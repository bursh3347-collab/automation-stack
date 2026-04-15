# Selenium

> Browser automation framework — the original web testing standard.

| Metric | Data |
|--------|------|
| GitHub | [SeleniumHQ/selenium](https://github.com/SeleniumHQ/selenium) |
| Stars | ~32,000 |
| Forks | ~8,500 |
| License | Apache-2.0 |
| Language | Java (multi-language bindings) |
| Last Update | 2026-04 (active) |
| Contributors | 800+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 72 | Mature but showing age. WebDriver standard (W3C). Multi-language. Grid for distributed testing. Selenium 4 with CDP support. |
| E Ecosystem | 82 | 32k stars, 800+ contributors. W3C standard. Massive enterprise adoption. Every testing framework integrates with it. |
| M Market | 65 | Being replaced by Playwright for new projects. Still dominant in enterprise legacy. Market share declining. |
| C Combo | 55 | Java-primary (not TypeScript). WebDriver protocol useful but Playwright is better match for Tianzi's stack. |
| **Overall** | **67** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 67.15 |

## Core Value
The original browser automation standard. W3C WebDriver protocol creator. Multi-language support (Java, Python, C#, Ruby, JavaScript). Selenium Grid for distributed testing at scale.

## Architecture Highlights
- **WebDriver Protocol**: W3C standard for browser automation (adopted by all browsers)
- **Selenium Grid**: Distributed test execution across machines/browsers
- **Multi-Language Bindings**: Java, Python, C#, Ruby, JavaScript
- **Selenium 4**: BiDi protocol support, relative locators, Chrome DevTools access
- **Selenium IDE**: Record-and-playback browser extension

## Key Modules
1. **WebDriver Core** (Large) — Browser communication protocol implementation
2. **Selenium Grid** (Large) — Distributed execution hub with node management
3. **Language Bindings** (Medium) — Multi-language client libraries
4. **Selenium IDE** (Medium) — Browser extension for recording tests
5. **Selenium Manager** (Small) — Automatic browser/driver management

## Extractable Patterns
- Distributed execution grid pattern (for any distributed task system)
- W3C WebDriver protocol knowledge
- Browser compatibility testing patterns

## Verdict
Legacy leader. Learn from its architecture (especially Grid), but use Playwright for new projects. TEMC 67 = record but don't prioritize for extraction.
