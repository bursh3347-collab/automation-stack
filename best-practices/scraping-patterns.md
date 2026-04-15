# Web Scraping Architecture Patterns

> Best practices extracted from Scrapy, Firecrawl, Crawlee, and Playwright.

## Pattern 1: Pipeline Architecture (from Scrapy)

Separate your scraping into distinct stages:

```
URL Queue → Fetcher → Parser → Cleaner → Storage
    ↑                                    |
    └────────── New URLs ←──────────────┘
```

**Why it works**: Each stage can be scaled, tested, and modified independently.

**Implementation tips**:
- Use a persistent queue (Redis, PostgreSQL) for URLs — survives crashes
- Deduplicate URLs before adding to queue (hash-based fingerprinting)
- Process items through a pipeline of transformers (validate → clean → enrich → store)

## Pattern 2: Anti-Bot Strategy Stack (from Crawlee + Firecrawl)

Layer multiple anti-detection strategies:

1. **Proxy Rotation**: Rotate IPs per request or per session
2. **User-Agent Rotation**: Realistic browser UA strings, rotate per session
3. **Request Fingerprint Randomization**: Headers order, TLS fingerprint, accept-language
4. **Session Management**: Maintain cookies across related requests, rotate sessions periodically
5. **Rate Limiting**: Respect robots.txt, add random delays (1-5s), honor 429 responses
6. **Browser Fingerprinting**: For Playwright/Puppeteer — stealth plugins, realistic viewport/fonts

## Pattern 3: Content Extraction Pipeline (from Firecrawl)

For AI-ready output:

```
Raw HTML → Readability → Clean HTML → Markdown → Structured JSON
```

1. **Readability**: Remove navigation, ads, sidebars (use Mozilla Readability)
2. **Clean HTML**: Strip scripts, styles, tracking elements
3. **Markdown Conversion**: Preserve headings, lists, tables, links, code blocks
4. **Structured Extraction**: Use LLM with JSON schema to extract specific data

## Pattern 4: Retry with Exponential Backoff (Universal)

```typescript
async function fetchWithRetry(url: string, maxRetries = 3): Promise<Response> {
  for (let i = 0; i < maxRetries; i++) {
    try {
      const response = await fetch(url);
      if (response.status === 429) {
        const delay = Math.pow(2, i) * 1000 + Math.random() * 1000;
        await sleep(delay);
        continue;
      }
      return response;
    } catch (error) {
      if (i === maxRetries - 1) throw error;
      await sleep(Math.pow(2, i) * 1000);
    }
  }
  throw new Error('Max retries exceeded');
}
```

## Pattern 5: Parallel Crawling with Concurrency Control (from Crawlee)

```typescript
class AutoscaledPool {
  private concurrency: number;
  private maxConcurrency: number;
  private runningTasks: number = 0;
  
  async run(tasks: AsyncIterable<() => Promise<void>>) {
    // Scale concurrency based on:
    // - CPU usage (reduce if > 80%)
    // - Memory usage (reduce if > 80%)
    // - Error rate (reduce if > 10%)
    // - Success rate (increase if > 95%)
  }
}
```

## Pattern 6: JavaScript Rendering Decision Tree

```
Need JS rendering?
├── No (static HTML) → Use HTTP client (fastest, cheapest)
│   └── Tools: Cheerio, BeautifulSoup, node-html-parser
├── Yes (SPA/dynamic content)
│   ├── Simple rendering → Headless browser (Playwright)
│   └── Complex interaction → Full browser with stealth (Playwright + stealth)
└── Unsure → Try HTTP first, fall back to browser
```

## Anti-Patterns to Avoid

1. **No rate limiting** — You'll get IP banned and potentially face legal issues
2. **Ignoring robots.txt** — Legal risk and ethical concerns
3. **Storing raw HTML** — Wastes storage; extract and clean immediately
4. **Single point of failure** — No retry logic, no proxy fallback
5. **Synchronous scraping** — Always use async/concurrent approaches
