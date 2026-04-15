# Crawlee

> A web scraping and browser automation library for Node.js to build reliable crawlers.

| Metric | Data |
|--------|------|
| GitHub | [apify/crawlee](https://github.com/apify/crawlee) |
| Stars | ~17,000 |
| Forks | ~700 |
| License | Apache-2.0 |
| Language | TypeScript |
| Last Update | 2026-04 (active) |
| Contributors | 100+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Unified API for HTTP + browser crawling. Built-in anti-blocking, proxy rotation, session management. TypeScript-first. |
| E Ecosystem | 75 | 17k stars. Apify (established company) backed. Smaller community than Scrapy/Playwright but growing. |
| M Market | 78 | Good positioning as "reliable crawling" solution. Competes with Scrapy in Python world. TypeScript advantage for Node.js devs. |
| C Combo | 85 | TypeScript native. Clean API design. Apache-2.0 = fully commercial. Pairs well with Playwright for rendering. |
| **Overall** | **81** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 80.9 |

## Core Value
Reliable web crawling with built-in anti-blocking. Unified API that works for both simple HTTP requests and full browser rendering. Think "Scrapy but for TypeScript" with modern anti-bot built in.

## Architecture Highlights
- **Unified Crawler Interface**: Same API for HttpCrawler, CheerioCrawler, PlaywrightCrawler, PuppeteerCrawler
- **AutoscaledPool**: Automatic concurrency management based on system resources
- **Session Management**: Automatic session rotation to avoid blocks
- **Request Queue**: Persistent queue with deduplication and retry
- **Storage Abstraction**: Dataset (results) + KeyValueStore (state) + RequestQueue (URLs)

## Key Modules
1. **Crawler Classes** (Large) — HTTP, Cheerio, Playwright, Puppeteer crawlers with unified API
2. **Anti-Blocking** (Medium) — Proxy rotation, session management, fingerprinting
3. **Storage System** (Medium) — Dataset, KeyValueStore, RequestQueue with local/cloud backends
4. **AutoscaledPool** (Small) — Concurrency management and resource optimization
5. **Router** (Small) — URL pattern matching for different page handlers

## Extractable Patterns
- **⭐ Universal Code Candidate: Request Queue with Dedup** → code-base/patterns/request-queue/
- AutoscaledPool concurrency pattern
- Unified crawler interface design (adapter pattern)
- Session rotation strategy
