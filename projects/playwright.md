# Playwright

> Framework for Web Testing and Automation — test Chromium, Firefox and WebKit with a single API.

| Metric | Data |
|--------|------|
| GitHub | [microsoft/playwright](https://github.com/microsoft/playwright) |
| Stars | 86,505 |
| Forks | 5,505 |
| License | Apache-2.0 |
| Language | TypeScript |
| Last Update | 2026-04-15 |
| Contributors | 500+ |
| Open Issues | 626 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 92 | Auto-wait, network interception, multi-browser, codegen, trace viewer. TypeScript-first with Python/Java/C# bindings. Production-grade from Microsoft. |
| E Ecosystem | 90 | 86k stars, Microsoft-backed, rapid growth. Strong VS Code integration. Active community and enterprise adoption. |
| M Market | 85 | Replacing Selenium as testing standard. Growing automation use cases beyond testing. |
| C Combo | 88 | TypeScript native = perfect stack match. Headless browser for AI scraping, testing, automation. Direct integration with Next.js testing. |
| **Overall** | **88** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 88.0 |

## Core Value
The modern standard for browser automation. Single API across Chromium, Firefox, WebKit. Auto-waiting eliminates flaky tests. Network interception enables API mocking.

## Architecture Highlights
- **Browser Context Isolation**: Each test gets fresh browser context (cookies, storage, permissions)
- **Auto-Wait Engine**: Automatically waits for elements to be actionable before performing actions
- **Network Interception Layer**: Mock APIs, modify requests/responses, record HAR files
- **Codegen Tool**: Record user interactions → generate test code automatically
- **Trace Viewer**: Time-travel debugging with DOM snapshots, network logs, console output
- **Multi-language Bindings**: TypeScript/JavaScript, Python, Java, C# — all from single codebase

## Key Modules
1. **Browser Engine Abstraction** (Large) — Unified API across Chromium/Firefox/WebKit via CDP/proprietary protocols
2. **Page & Locator API** (Large) — Element selection, actions, assertions with auto-waiting
3. **Network Layer** (Medium) — Request interception, response mocking, HAR recording
4. **Test Runner** (Medium) — Parallel execution, fixtures, annotations, HTML reporter
5. **Codegen & Trace** (Small) — Recording, playback, time-travel debugging

## Extractable Patterns
- **⭐ Universal Code Candidate: Browser Automation Wrapper** → code-base/automation/browser/
- **⭐ Universal Code Candidate: Network Interception Pattern** → code-base/testing/api-mocking/
- Auto-wait pattern for robust UI automation
- Browser context isolation for parallel testing
- Page Object Model implementation

## Why This Matters for Tianzi
- **Direct stack match**: TypeScript native, integrates with Next.js testing
- **AI scraping backbone**: Headless browser for LLM-ready data extraction (pairs with Firecrawl)
- **SaaS testing**: E2E testing for any Micro SaaS product
