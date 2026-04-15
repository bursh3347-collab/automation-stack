# Selenium

> The W3C standard for browser automation — 22 years of industry dominance, multi-language support.

| Metric | Data |
|--------|------|
| GitHub | [SeleniumHQ/selenium](https://github.com/SeleniumHQ/selenium) |
| Stars | 34,082 |
| Forks | 8,674 |
| License | Apache-2.0 ✅ |
| Languages | Java, Python, JavaScript, Ruby, C#, Rust |
| Last Update | 2026-04-15 (today) |
| Contributors | 800+ |
| Architecture | Bazel monorepo |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 75 | W3C WebDriver standard, multi-language, robust. But verbose API, heavy setup, slower than modern alternatives. |
| E (Ecosystem) | 82 | Industry standard, W3C spec, massive enterprise adoption. 800+ contributors over 22 years. |
| M (Market) | 60 | Mature/stable but being replaced by Playwright/Puppeteer for new projects. Legacy enterprise demand remains. |
| C (Combination) | 55 | Java-first architecture doesn't align with TS stack. Heavy setup. Better alternatives exist for一人公司. |
| **Total** | **67** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
selenium/
├── java/              # Java bindings (primary)
├── py/                # Python bindings
├── javascript/        # JavaScript/Node.js bindings
├── rb/                # Ruby bindings
├── dotnet/            # C# bindings
├── rust/              # Selenium Manager (browser driver management)
├── common/            # Shared resources, WebDriver protocol
├── cpp/               # IE Driver (legacy)
├── third_party/       # Third-party dependencies
└── scripts/           # Build and CI scripts
```

**Architecture Pattern**: Multi-language monorepo with Bazel build system

**Key Design**: Client → WebDriver Protocol (W3C) → Browser Driver → Browser. Standard-based approach.

## Core Modules (4)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| WebDriver Protocol | Large | High | W3C standard implementation |
| Language Bindings | Large | Low | Java/Python/JS/Ruby/C# clients |
| Selenium Manager | Medium | Low | Rust-based browser driver management |
| Grid | Large | Medium | Distributed test execution |

## Extractable Patterns

1. **Selenium Manager (Rust)** → Automatic browser driver discovery and management
   - Smart detection of installed browsers
   - Automatic driver version matching

2. **Grid Architecture** → Distributed browser execution
   - Hub → Node pattern for scaling browser automation
   - Relevant for large-scale scraping infrastructure

3. **W3C WebDriver Protocol** → Standard browser control protocol
   - Reference implementation for custom automation tools

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| Grid architecture | ⚠️ Partial | Complex, Java-specific | 8h+ |
| Selenium Manager | ⚠️ Partial | Rust, standalone tool | 4h |
| WebDriver protocol | ❌ No | Use Playwright instead | N/A |
| Language bindings | ❌ No | Better alternatives exist | N/A |

## Business Value

- **Pain Point**: Cross-browser, cross-language test automation (Important for enterprises)
- **Target Users**: Enterprise QA teams, testing consultancies
- **Competitors**: Playwright (modern), Cypress (developer-friendly), Puppeteer (Chrome)
- **Commercialization**: Not directly — it's infrastructure, not a product
- **Differentiation Window**: None for一人公司. Legacy enterprises will keep using it.

## Combination Potential

- **Limited for天子**: Java-first, heavy setup, doesn't match TS stack
- **Educational Value**: Understanding WebDriver protocol helps when building automation tools
- **Grid Pattern**: Distributed execution concept applicable to any scraping infrastructure

## Anti-fragility Assessment

- **Bus Factor**: SeleniumHQ organization (10+ core maintainers) — Low risk ✅
- **Dependency Safety**: W3C standard = extremely stable
- **CI/CD**: Bazel build, comprehensive multi-platform testing
- **License**: Apache-2.0 ✅ fully commercial

## Why It Might NOT Be Worth Using

- Verbose API compared to Playwright/Puppeteer
- Heavy setup (Java, driver management, Grid)
- Java-first doesn't align with TypeScript stack
- Playwright is strictly better for new TypeScript projects
- Slow to adopt modern features (auto-wait, trace viewer)
- Legacy reputation — new developers prefer modern alternatives
- Grid complexity is overkill for一人公司 scale
