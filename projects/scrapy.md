# Scrapy

> The most battle-tested Python web crawling & scraping framework — 16 years of production-grade reliability.

| Metric | Data |
|--------|------|
| GitHub | [scrapy/scrapy](https://github.com/scrapy/scrapy) |
| Stars | 61,334 |
| Forks | 11,472 |
| License | BSD-3-Clause ✅ |
| Language | Python |
| Last Update | 2026-04-14 |
| Latest Version | v2.15.0 (2026-04-09) |
| Open Issues | 637 |
| Contributors | 500+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Twisted async engine, middleware pipeline, excellent extensibility. Mature but not cutting-edge. |
| E (Ecosystem) | 85 | 16-year ecosystem, massive plugin library (scrapy-splash, scrapy-playwright, scrapy-redis). 500+ contributors. |
| M (Market) | 72 | Mature market, Python-first. Less AI-native than newer tools. Stable demand but not growing fast. |
| C (Combination) | 70 | Python (not TS), but pipeline architecture patterns are universally reusable. Data extraction feeds AI pipelines. |
| **Total** | **77** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
scrapy/
├── scrapy/
│   ├── core/           # Engine, Scheduler, Downloader, Scraper
│   ├── http/           # Request/Response objects
│   ├── downloadermiddlewares/  # Retry, redirect, cookies, compression
│   ├── spidermiddlewares/      # Depth, HTTP error, referer
│   ├── pipelines/      # Item processing pipeline
│   ├── extensions/     # Stats, logging, throttle, memory debug
│   ├── utils/          # URL, decorators, iterators
│   └── settings/       # Configuration management
├── docs/               # Sphinx documentation
└── tests/              # Comprehensive test suite
```

**Architecture Pattern**: Event-driven pipeline with Twisted reactor

**Key Design**: Engine → Scheduler → Downloader → Spider → Item Pipeline — each stage is pluggable via middleware.

## Core Modules (5)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| Engine | Large | High | Orchestrates all components, Twisted reactor |
| Downloader | Medium | Medium | HTTP client with middleware chain |
| Spider | Medium | Low | User-defined extraction logic |
| Item Pipeline | Small | Low | Post-processing, storage, validation |
| Scheduler | Medium | Medium | Request queue with dedup (fingerprinting) |

## Extractable Patterns

1. **Pipeline Architecture** → `code-base/data-pipeline/pipeline-pattern/` ⭐通用代码候选
   - Pluggable middleware chain for request/response processing
   - Item pipeline for data validation → transformation → storage

2. **Request Fingerprinting** → Deduplication via URL + method + body hashing
   - Extractable as generic dedup strategy for any crawler

3. **Throttle & AutoThrottle** → Adaptive rate limiting based on server response time
   - Reusable pattern for any API client or scraper

4. **Retry Middleware** → Exponential backoff with configurable retry codes

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| Pipeline pattern | ✅ Yes | Simple copy → TS adapt | 2h |
| AutoThrottle | ✅ Yes | Needs adaptation | 3h |
| Request fingerprinting | ✅ Yes | Simple copy | 1h |
| Middleware chain | ✅ Yes | Needs TS rewrite | 4h |
| Twisted engine | ❌ No | Python-specific | N/A |

## Business Value

- **Pain Point**: Reliable large-scale web data extraction (Important)
- **Target Users**: Data engineers, ML teams, SEO companies
- **Competitors**: Crawlee ($0-paid via Apify), Firecrawl (API-first), Beautiful Soup (lightweight)
- **Commercialization**: Not directly SaaS-able; used as infrastructure for data products
- **Differentiation Window**: AI-powered extraction plugins (scrapy + LLM for structured data)

## Combination Potential

- **Product**: AI Data Pipeline SaaS — Scrapy extraction → LLM structuring → API delivery
- **Sell to**: Companies needing structured web data for AI training
- **Price**: $49-199/mo based on pages crawled

## Anti-fragility Assessment

- **Bus Factor**: 3+ core maintainers (wRAR, others) — Medium risk
- **Dependency Safety**: Twisted is stable but niche
- **CI/CD**: GitHub Actions, comprehensive test suite
- **License**: BSD-3-Clause ✅ fully commercial

## Why It Might NOT Be Worth Using

- Python-only, doesn't align with TS base stack
- Twisted async model is being superseded by asyncio
- For AI use cases, Firecrawl offers better LLM-ready output out of the box
- Overkill for simple scraping tasks
