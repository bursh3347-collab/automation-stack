# Playwright

> Microsoft's cross-browser automation framework — the modern standard for browser testing and scraping.

| Metric | Data |
|--------|------|
| GitHub | [microsoft/playwright](https://github.com/microsoft/playwright) |
| Stars | ~86,500 |
| Forks | ~4,500 |
| License | Apache-2.0 ✅ |
| Language | TypeScript |
| Last Update | 2026-04-15 (today) |
| Contributors | 500+ |
| npm Weekly | 10M+ downloads |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 92 | Cross-browser (Chromium/Firefox/WebKit), codegen, trace viewer, auto-wait, TypeScript-native. Best-in-class API design. |
| E (Ecosystem) | 90 | Microsoft-backed, massive enterprise adoption, VS Code integration, Playwright Test runner. .claude directory = AI-friendly. |
| M (Market) | 85 | Dominant in E2E testing, growing in AI agent browser control and scraping. |
| C (Combination) | 88 | TypeScript-native, Apache-2.0, perfect match for AI agent browser automation. Direct integration with AI stack. |
| **Total** | **88** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
playwright/
├── packages/
│   ├── playwright-core/    # Core browser automation protocol
│   ├── playwright/         # Main package with browser downloads
│   ├── playwright-test/    # Test runner framework
│   ├── trace-viewer/       # Debugging trace UI
│   └── html-reporter/      # Test report generation
├── browser_patches/        # Custom browser patches for automation
├── docs/                   # Documentation
├── tests/                  # Comprehensive test suite
└── utils/                  # Build and development utilities
```

**Architecture Pattern**: Monorepo with clean package boundaries

**Key Design**: Browser Protocol Layer → Page/Context API → Actions/Assertions — each layer abstracts the one below.

## Core Modules (5)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| playwright-core | Large | Medium | CDP/BiDi protocol, browser connection |
| Page API | Large | Medium | Navigation, selectors, actions, screenshots |
| Auto-wait | Small | Low | Intelligent element waiting, no flaky tests |
| Codegen | Medium | Low | Record user actions → generate test code |
| Trace Viewer | Medium | Low | Visual debugging with snapshots |

## Extractable Patterns

1. **Auto-wait Pattern** → `code-base/browser-automation/auto-wait/` ⭐通用代码候选
   - Intelligent waiting for elements to be actionable
   - Eliminates explicit sleep/wait calls

2. **Browser Context Isolation** → Each test gets fresh context (cookies, storage)
   - Reusable pattern for parallel scraping sessions

3. **Selector Engine** → CSS, XPath, text, role, test-id selectors
   - Unified selector strategy applicable to any browser tool

4. **Screenshot/PDF Generation** → Full-page, element, viewport screenshots
   - Extractable as standalone screenshot service

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| Auto-wait pattern | ✅ Yes | Concept extraction | 1h |
| Context isolation | ✅ Yes | Pattern documentation | 1h |
| Screenshot service | ✅ Yes | Simple wrapper | 2h |
| Codegen approach | ⚠️ Partial | Complex, needs adaptation | 8h |
| Browser patches | ❌ No | Microsoft-specific | N/A |

## Business Value

- **Pain Point**: Reliable cross-browser testing + AI browser automation (Critical)
- **Target Users**: QA teams, AI agent developers, scraping companies
- **Competitors**: Puppeteer (Chrome-only), Selenium (verbose), Cypress (testing-only)
- **Commercialization**: Foundation for browser-based AI agents, testing SaaS
- **Differentiation Window**: AI agent browser control (Playwright + LLM = autonomous web agent)

## Combination Potential

- **Product**: AI Browser Agent SaaS — Playwright + LLM for autonomous web tasks
- **Sell to**: Companies needing web automation (data entry, monitoring, testing)
- **Price**: $29-99/mo per agent
- **Combo with Firecrawl**: Playwright handles JS-heavy pages, Firecrawl handles static + API

## Anti-fragility Assessment

- **Bus Factor**: Microsoft team (10+ active maintainers) — Low risk ✅
- **Dependency Safety**: Self-contained, custom browser binaries
- **CI/CD**: Comprehensive GitHub Actions, cross-platform testing
- **License**: Apache-2.0 ✅ fully commercial

## Why It Might NOT Be Worth Using

- Heavy resource usage (downloads browsers ~500MB+)
- Overkill for simple HTTP scraping (use Cheerio/Firecrawl instead)
- Microsoft could deprioritize (unlikely given adoption)
- Learning curve for advanced features (network interception, browser contexts)
