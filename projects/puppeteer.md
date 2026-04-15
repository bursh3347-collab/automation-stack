# Puppeteer

> Google's original Chrome automation library — the tool that popularized headless browser scripting.

| Metric | Data |
|--------|------|
| GitHub | [puppeteer/puppeteer](https://github.com/puppeteer/puppeteer) |
| Stars | ~94,000 |
| Forks | ~9,000+ |
| License | Apache-2.0 ✅ |
| Language | TypeScript |
| Last Update | 2026-04-15 (today) |
| Contributors | 400+ |
| npm Weekly | 5M+ downloads |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 82 | Solid Chrome DevTools Protocol (CDP) implementation, TypeScript monorepo, clean API. Now supports Firefox. |
| E (Ecosystem) | 88 | Google-backed, massive npm adoption, Crawlee/Apify built on top. 94k stars. |
| M (Market) | 72 | Being overtaken by Playwright for new projects. Still dominant in Chrome-specific automation. |
| C (Combination) | 78 | TypeScript, Apache-2.0, but Playwright preferred for new work. Good for Chrome-specific tasks. |
| **Total** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
puppeteer/
├── packages/
│   ├── puppeteer/          # Main package (downloads Chrome)
│   ├── puppeteer-core/     # Core without browser download
│   ├── browsers/           # Browser download management
│   └── testserver/         # Test infrastructure
├── docker/                 # Docker configurations
├── docs/                   # API documentation
├── examples/               # Usage examples
└── test/                   # Test suite
```

**Architecture Pattern**: Monorepo (puppeteer/puppeteer-core split)

**Key Design**: CDP Connection → Browser/Page → Actions — direct Chrome DevTools Protocol mapping.

## Core Modules (4)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| puppeteer-core | Large | Medium | CDP protocol, browser control |
| Browser management | Medium | Low | Download, launch, connect |
| Page API | Large | Medium | Navigation, DOM, screenshots |
| Network interception | Medium | Low | Request/response modification |

## Extractable Patterns

1. **CDP Protocol Wrapper** → Direct Chrome DevTools Protocol access
   - Lower-level than Playwright, useful for custom automation

2. **Browser Download Management** → Automated browser binary management
   - `code-base/browser-automation/browser-manager/` ⭐通用代码候选

3. **PDF Generation** → Chrome's built-in PDF rendering
   - High-quality HTML-to-PDF conversion

4. **Network Interception** → Request/response modification patterns

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| PDF generation wrapper | ✅ Yes | Simple wrapper | 1h |
| Network interception | ✅ Yes | Pattern extraction | 2h |
| Browser management | ⚠️ Partial | Complex, Chrome-specific | 4h |
| CDP protocol | ❌ No | Core dependency | N/A |

## Business Value

- **Pain Point**: Chrome-specific automation and PDF generation (Important)
- **Target Users**: Developers needing Chrome automation, PDF services
- **Competitors**: Playwright (cross-browser), Selenium (multi-language)
- **Commercialization**: PDF-as-a-Service, screenshot service
- **Differentiation Window**: Narrowing — Playwright covers most use cases better

## Combination Potential

- **Product**: HTML-to-PDF SaaS — Puppeteer for high-fidelity PDF rendering
- **Sell to**: Companies needing invoice/report PDF generation
- **Price**: $19-49/mo per 10K PDFs
- **Alternative**: Use as Crawlee backend for reliable scraping

## Anti-fragility Assessment

- **Bus Factor**: Google team (5+ maintainers) — Low risk
- **Dependency Safety**: Chrome binary dependency, well-managed
- **CI/CD**: GitHub Actions, release-please automation
- **License**: Apache-2.0 ✅ fully commercial

## Why It Might NOT Be Worth Using

- Playwright is strictly better for new cross-browser projects
- Chrome-only by design (Firefox support is experimental)
- Google could shift focus to Chrome's built-in Testing Protocol
- Market share declining in favor of Playwright
- Stars are legacy — new projects overwhelmingly choose Playwright
