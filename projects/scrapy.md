# Scrapy

> Fast high-level web crawling & scraping framework for Python.

| Metric | Data |
|--------|------|
| GitHub | [scrapy/scrapy](https://github.com/scrapy/scrapy) |
| Stars | 61,333 |
| Forks | 11,472 |
| License | BSD-3-Clause |
| Language | Python |
| Last Update | 2026-04-15 |
| Contributors | 500+ |
| Open Issues | 637 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 88 | Battle-tested since 2010. Async Twisted engine, middleware pipeline, robust item pipeline. Excellent extensibility via middleware/extensions/signals. |
| E Ecosystem | 92 | 61k+ stars, massive community, Scrapy Cloud (Zyte), 500+ contributors. De facto Python scraping standard. |
| M Market | 75 | Mature market, well-established. Not trending upward but steady demand. Python-only limits cross-language adoption. |
| C Combo | 70 | Python-only (not TypeScript). But patterns (middleware pipeline, item processing) are universally applicable. Data pipeline integration excellent. |
| **Overall** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 80.15 |

## Core Value
The gold standard for Python web scraping. Solves large-scale data extraction with built-in rate limiting, retry logic, proxy rotation support, and structured data pipelines.

## Architecture Highlights
- **Engine-Spider-Pipeline Architecture**: Clean separation of crawl logic (Spiders), processing (Item Pipelines), and infrastructure (Engine/Scheduler/Downloader)
- **Middleware System**: Request/Response middleware chain for proxies, user-agents, cookies, retries
- **Signals Framework**: Event-driven hooks for monitoring, stats, custom behaviors
- **Async Twisted Core**: Non-blocking I/O for high concurrency
- **Selector API**: CSS + XPath unified selector interface

## Key Modules
1. **Spider Framework** (Large) — Base spider classes, CrawlSpider with rules, XMLFeedSpider, SitemapSpider
2. **Item Pipeline** (Medium) — Data validation, cleaning, deduplication, storage adapters
3. **Downloader Middleware** (Medium) — Proxy rotation, user-agent rotation, retry policies, cookies
4. **Feed Exporters** (Small) — JSON, CSV, XML, custom format output
5. **Extensions** (Small) — Stats collection, logging, throttling, memory management

## Extractable Patterns
- **⭐ Universal Code Candidate: Middleware Pipeline Pattern** → code-base/patterns/middleware-chain/
- **⭐ Universal Code Candidate: Retry with Exponential Backoff** → code-base/error-handling/retry/
- Spider-Pipeline separation pattern for any ETL workflow
- Rate limiting / politeness engine design

## Competitors
| | Scrapy | Crawlee | Playwright | BeautifulSoup |
|---|--------|---------|------------|---------------|
| Language | Python | JS/TS/Python | Multi | Python |
| JS Rendering | Via Splash | Built-in | Built-in | No |
| Scale | Excellent | Good | Medium | Small |
| Learning Curve | Medium | Low | Low | Very Low |
| Anti-bot | Plugins | Built-in | Stealth mode | None |
