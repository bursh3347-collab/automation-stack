# Web Scraping Best Practices

> Universal patterns extracted from Scrapy (61k⭐), Crawlee (23k⭐), Firecrawl (109k⭐), and Playwright (86k⭐).

## 1. Pipeline Architecture (from Scrapy)

Every scraping system should follow a pipeline pattern:

```
URL Input → Request Queue → Downloader → Parser → Item Pipeline → Storage
              ↑                                          |
              └── Retry/Failed ──────────────────────────┘
```

**Why**: Separation of concerns makes each stage independently testable, replaceable, and scalable.

**From Scrapy**: Middleware chains at download and spider levels allow injecting cross-cutting concerns (logging, rate limiting, proxy rotation) without modifying core logic.

## 2. Anti-Bot Strategies (from Crawlee + Scrapy)

### Browser Fingerprint Rotation
- Rotate User-Agent strings (real browser profiles, not random strings)
- Randomize viewport size, timezone, language headers
- Use stealth plugins (playwright-extra-stealth / puppeteer-extra-stealth)

### Request Patterns
- **Random delays**: 1-5 seconds between requests (not fixed intervals)
- **Session management**: Maintain cookies per crawl session
- **Referer chain**: Build realistic referer headers
- **Accept headers**: Match real browser Accept/Accept-Language/Accept-Encoding

### Proxy Strategy (from Crawlee)
```typescript
// Pattern: Session-based proxy assignment
// Each session gets ONE proxy, rotated on block
const proxyConfig = {
  useApifyProxy: true,
  proxyUrls: ['http://proxy1:8080', 'http://proxy2:8080'],
  newUrlFunction: (sessionId) => selectProxy(sessionId)
};
```

**Key insight from Crawlee**: Assign one proxy per session (not per request). Rotating per-request triggers anti-bot systems faster.

## 3. Content Extraction for AI (from Firecrawl)

### HTML → Markdown Conversion
The #1 pattern for feeding web data to LLMs:

1. **Remove noise**: Navigation, footers, ads, scripts, styles
2. **Preserve structure**: Headings, lists, tables, code blocks
3. **Clean formatting**: Normalize whitespace, fix encoding
4. **Output markdown**: Token-efficient format for LLMs

```typescript
// Pattern: Extract main content
function extractMainContent(html: string): string {
  // 1. Use readability algorithm (Mozilla Readability)
  // 2. Convert to markdown (turndown)
  // 3. Clean up excess whitespace
  // 4. Trim to token budget
}
```

### Structured Extraction with LLMs
```typescript
// Pattern: Schema-guided extraction
const schema = z.object({
  title: z.string(),
  price: z.number(),
  features: z.array(z.string())
});

// Send markdown + schema to LLM → get structured JSON
```

## 4. Retry with Exponential Backoff (from Scrapy + Crawlee)

```typescript
// Universal retry pattern
async function fetchWithRetry(
  url: string,
  maxRetries: number = 3,
  baseDelay: number = 1000
): Promise<Response> {
  for (let i = 0; i < maxRetries; i++) {
    try {
      const response = await fetch(url);
      if (response.status === 429) {
        // Rate limited — wait longer
        await sleep(baseDelay * Math.pow(2, i) * (1 + Math.random()));
        continue;
      }
      if (response.ok) return response;
    } catch (error) {
      if (i === maxRetries - 1) throw error;
      await sleep(baseDelay * Math.pow(2, i));
    }
  }
  throw new Error(`Failed after ${maxRetries} retries`);
}
```

**Scrapy's insight**: Add jitter (randomness) to backoff to prevent thundering herd.
**Crawlee's insight**: Track blocked responses and rotate proxy before retrying.

## 5. Concurrency Control (from Scrapy + Crawlee)

```typescript
// Pattern: Adaptive concurrency
class AdaptiveConcurrency {
  private currentConcurrency: number;
  private targetSuccessRate: number = 0.95;

  adjustConcurrency(successRate: number) {
    if (successRate > this.targetSuccessRate) {
      // Increase concurrency (things are going well)
      this.currentConcurrency = Math.min(
        this.currentConcurrency * 1.1,
        this.maxConcurrency
      );
    } else {
      // Decrease concurrency (too many failures)
      this.currentConcurrency = Math.max(
        this.currentConcurrency * 0.5,
        this.minConcurrency
      );
    }
  }
}
```

**From Scrapy AutoThrottle**: Measure server response time, automatically adjust request rate.

## 6. Request Deduplication (from Scrapy)

```typescript
// Pattern: URL fingerprinting for dedup
function requestFingerprint(url: string, method: string, body?: string): string {
  const normalized = new URL(url);
  // Sort query parameters for consistency
  normalized.searchParams.sort();
  const canonical = `${method}:${normalized.toString()}:${body || ''}`;
  return crypto.createHash('sha256').update(canonical).digest('hex');
}
```

## 7. Sitemap-First Discovery (from Crawlee + Firecrawl)

```typescript
// Pattern: Always check sitemap before crawling
async function discoverUrls(domain: string): Promise<string[]> {
  // 1. Check robots.txt for sitemap location
  // 2. Parse sitemap.xml (including sitemap index)
  // 3. Fall back to link-based crawling if no sitemap
  // This is 10-100x faster than crawling link-by-link
}
```

## Summary: When to Use What

| Pattern | Best Source | Apply When |
|---------|------------|------------|
| Pipeline architecture | Scrapy | Building any data extraction system |
| Anti-bot strategies | Crawlee | Scraping sites with protection |
| AI content extraction | Firecrawl | Feeding data to LLMs |
| Browser automation | Playwright | JS-heavy sites, SPAs |
| Retry + backoff | Universal | Any HTTP client |
| Adaptive concurrency | Scrapy | High-volume scraping |
| Request dedup | Scrapy | Large-scale crawling |
| Sitemap discovery | Crawlee | Starting a new crawl |
