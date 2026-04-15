# Crawlee

> Apify's reliable TypeScript web crawling library — built-in proxy rotation, anti-blocking, and storage.

| Metric | Data |
|--------|------|
| GitHub | [apify/crawlee](https://github.com/apify/crawlee) |
| Stars | 22,797 |
| Forks | 1,314 |
| License | Apache-2.0 ✅ |
| Language | TypeScript |
| Last Update | 2026-04-13 |
| Contributors | 100+ |
| Built on | Playwright + Puppeteer + Cheerio |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 85 | Excellent TypeScript abstractions over Playwright/Puppeteer/Cheerio. Built-in proxy rotation, retry, storage. |
| E (Ecosystem) | 78 | Apify ecosystem, moderate community. Not as massive as Playwright/Scrapy but growing. |
| M (Market) | 82 | Growing demand for reliable AI data extraction. TypeScript-native fills a gap. |
| C (Combination) | 85 | TypeScript ✅, Apache-2.0 ✅, perfect license. Combines with Playwright + AI stack seamlessly. |
| **Total** | **83** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
crawlee/
├── packages/
│   ├── core/              # Base crawler, request queue, storage
│   ├── basic-crawler/     # HTTP-only crawler
│   ├── cheerio-crawler/   # Cheerio (HTML parsing) crawler
│   ├── playwright-crawler/ # Playwright-based crawler
│   ├── puppeteer-crawler/ # Puppeteer-based crawler
│   ├── jsdom-crawler/     # JSDOM-based crawler
│   ├── http-crawler/      # Raw HTTP crawler
│   ├── browser-pool/      # Browser instance management
│   ├── memory-storage/    # In-memory storage backend
│   └── utils/             # Shared utilities
└── test/                  # Integration tests
```

**Architecture Pattern**: Monorepo with pluggable crawler backends

**Key Design**: RequestQueue → Crawler (choose backend) → RequestHandler → Storage. Everything is pluggable.

## Core Modules (5)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| Core | Large | Medium | Base abstractions, request queue, router |
| Browser Pool | Medium | Low | Manages browser instances, rotation |
| Proxy Management | Small | Low | Proxy rotation, session management |
| Storage | Medium | Low | Key-value store, dataset, request queue |
| Crawler Variants | Medium | Low | Cheerio/Playwright/Puppeteer adapters |

## Extractable Patterns

1. **Browser Pool Pattern** → `code-base/browser-automation/browser-pool/` ⭐通用代码候选
   - Manages multiple browser instances with rotation
   - Handles crashes, restarts, memory limits

2. **Proxy Rotation** → `code-base/networking/proxy-rotation/` ⭐通用代码候选
   - Session-based proxy assignment
   - Automatic rotation on block detection

3. **Request Queue with Dedup** → Persistent request queue with fingerprinting
   - Handles retries, priorities, deduplication

4. **Pluggable Backend Pattern** → Same API, different backends (Cheerio vs Playwright)
   - Strategy pattern for choosing scraping method

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| Browser pool | ✅ Yes | Clean boundaries | 3h |
| Proxy rotation | ✅ Yes | Self-contained | 2h |
| Request queue | ✅ Yes | Needs storage adapter | 3h |
| Pluggable backend | ✅ Yes | Pattern extraction | 2h |
| Apify integration | ❌ No | Platform-specific | N/A |

## Business Value

- **Pain Point**: Reliable web scraping without getting blocked (Important)
- **Target Users**: Data companies, AI pipeline builders, market researchers
- **Competitors**: Scrapy (Python), Firecrawl (API-first), raw Playwright
- **Commercialization**: Foundation for scraping-as-a-service (via Apify cloud or self-hosted)
- **Differentiation Window**: TypeScript + Apache-2.0 + built-in anti-blocking = best base for TS scraping products

## Combination Potential

- **Product**: Scraping API SaaS — Crawlee + proxy pool + API layer = managed scraping service
- **Sell to**: Companies needing structured web data
- **Price**: Usage-based, $29-199/mo
- **Combo with Firecrawl**: Crawlee for custom complex scraping, Firecrawl for simple AI extraction
- **Combo with n8n**: Crawlee as custom node in n8n workflows

## Anti-fragility Assessment

- **Bus Factor**: Apify company (50+ employees) — Low risk ✅
- **Dependency Safety**: Well-managed, Dependabot active, TypeScript 6.0
- **CI/CD**: GitHub Actions, turbo build, vitest
- **License**: Apache-2.0 ✅ fully commercial

## Why It Might NOT Be Worth Using

- Smaller community than Scrapy or Playwright
- Tightly coupled with Apify platform for cloud features
- Overhead if you just need simple HTTP scraping (use fetch + cheerio)
- Browser pool is complex — simpler to use Playwright directly for small scale
- No built-in AI/LLM features (unlike Firecrawl)
