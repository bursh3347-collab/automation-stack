# Puppeteer

> JavaScript API for Chrome and Firefox.

| Metric | Data |
|--------|------|
| GitHub | [puppeteer/puppeteer](https://github.com/puppeteer/puppeteer) |
| Stars | 94,118 |
| Forks | 9,419 |
| License | Apache-2.0 |
| Language | TypeScript |
| Last Update | 2026-04-15 |
| Contributors | 400+ |
| Open Issues | 298 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 85 | Chrome DevTools Protocol direct access. Mature, battle-tested. Good TypeScript support but less elegant API than Playwright. |
| E Ecosystem | 88 | 94k stars (highest in category). Google-backed. Massive npm ecosystem of plugins and wrappers. |
| M Market | 72 | Being gradually replaced by Playwright for new projects. Still dominant in existing codebases. |
| C Combo | 82 | TypeScript native. Good for Chrome-specific automation. Pairs with scraping pipelines. |
| **Overall** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 80.15 |

## Core Value
The original modern browser automation library from Google. Direct Chrome DevTools Protocol access gives maximum Chrome control. Simpler API than Selenium, massive ecosystem.

## Architecture Highlights
- **CDP Direct Access**: Raw Chrome DevTools Protocol for maximum browser control
- **Page Model**: Clean abstraction over browser tabs/pages
- **Screenshot/PDF Generation**: Built-in rendering to images and PDFs
- **Request Interception**: Network-level control for scraping and testing
- **Firefox Support**: Added via WebDriver BiDi protocol

## Key Modules
1. **Browser/Page Management** (Large) — Launch, connect, page lifecycle
2. **DOM Interaction** (Medium) — Selectors, clicks, typing, file uploads
3. **Network Control** (Medium) — Interception, caching, authentication
4. **Rendering** (Small) — Screenshots, PDFs, accessibility snapshots
5. **DevTools Protocol** (Small) — Raw CDP access for advanced use cases

## Extractable Patterns
- Screenshot/PDF generation service pattern
- CDP protocol wrapper for advanced browser control
- Cookie/session management patterns

## Puppeteer vs Playwright
| | Puppeteer | Playwright |
|---|-----------|------------|
| Multi-browser | Chrome + Firefox | Chrome + Firefox + WebKit |
| Auto-wait | Manual | Built-in |
| Parallel | Manual | Built-in fixtures |
| API Design | Good | Better (locators) |
| Trace Viewer | No | Yes |
| **Verdict** | Legacy leader | Modern choice |
