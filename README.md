# 🤖 automation-stack

> ⭐ Maturity: **L1 Growing** — 7 projects deeply analyzed with TEMC scoring, comparison table, and best practices.

Extracted best practices and deep analyses from the world's top automation & web scraping open-source projects.

## 📊 Leaderboard (by TEMC Score)

| Rank | Project | Stars | TEMC | Language | License | Trend |
|------|---------|-------|------|----------|---------|-------|
| 1 | [Firecrawl](projects/firecrawl.md) | 109k | **90** | TypeScript | AGPL-3.0 ⚠️ | 🚀 |
| 2 | [Playwright](projects/playwright.md) | 86k | **88** | TypeScript | Apache-2.0 ✅ | 🚀 |
| 3 | [n8n](projects/n8n.md) | 184k | **86** | TypeScript | Fair-code ⚠️ | 🚀 |
| 4 | [Crawlee](projects/crawlee.md) | 23k | **83** | TypeScript | Apache-2.0 ✅ | ↑ |
| 5 | [Puppeteer](projects/puppeteer.md) | 94k | **80** | TypeScript | Apache-2.0 ✅ | → |
| 6 | [Scrapy](projects/scrapy.md) | 61k | **77** | Python | BSD-3 ✅ | → |
| 7 | [Selenium](projects/selenium.md) | 34k | **67** | Java (multi) | Apache-2.0 ✅ | ↓ |

## 📂 Repository Structure

```
automation-stack/
├── README.md              ← You are here
├── projects/              ← Individual project analyses (TEMC-scored)
│   ├── firecrawl.md       (TEMC: 90)
│   ├── playwright.md      (TEMC: 88)
│   ├── n8n.md             (TEMC: 86)
│   ├── crawlee.md         (TEMC: 83)
│   ├── puppeteer.md       (TEMC: 80)
│   ├── scrapy.md          (TEMC: 77)
│   └── selenium.md        (TEMC: 67)
├── best-practices/        ← Extracted patterns from multiple projects
│   ├── scraping-patterns.md
│   └── workflow-automation.md
├── code/                  ← Extracted code snippets (coming in L2)
├── comparison.md          ← Side-by-side comparison of all 7 projects
├── SOURCES.md             ← All source projects with links & licenses
└── CONTRIBUTING.md        ← How to contribute
```

## 🎯 What This Repo Is

This is **not** a bookmark list. Each project is deeply analyzed with:

- **TEMC Score**: Technology (T) × Ecosystem (E) × Market (M) × Combination (C) weighted scoring
- **Architecture analysis**: Directory structure, core modules, design patterns
- **Extractable patterns**: What code/patterns can be reused in your own projects
- **Disassembly assessment**: Which modules can be extracted, difficulty, and time estimates
- **Business value**: Pain points, target users, competitive landscape, monetization potential
- **Anti-fragility**: Bus factor, license risks, dependency safety
- **Counter-arguments**: Why each project might NOT be worth using

## 🔥 Quick Decision Guide

| Your Need | Best Choice | Why |
|-----------|------------|-----|
| AI data extraction | **Firecrawl** | LLM-ready markdown output, MCP support |
| Browser testing & automation | **Playwright** | Cross-browser, TypeScript-native, auto-wait |
| Business workflow automation | **n8n** | Visual builder, 400+ integrations, AI-native |
| TypeScript web crawling | **Crawlee** | Built-in proxy rotation, Apache-2.0 |
| Python data pipeline | **Scrapy** | 16 years battle-tested, pipeline architecture |
| Chrome-specific automation | **Puppeteer** | Native CDP access, Google-backed |
| Enterprise legacy | **Selenium** | W3C standard, multi-language |

See [comparison.md](comparison.md) for the full feature comparison.

## 📈 Best Practices

- [Scraping Patterns](best-practices/scraping-patterns.md) — Pipeline architecture, anti-bot, AI extraction, retry patterns
- [Workflow Automation](best-practices/workflow-automation.md) — Node architecture, DAG execution, credential management

## 🔧 Universal Patterns Identified (→ code-base)

These cross-project patterns have been identified for extraction to the universal `code-base` repository:

| Pattern | Source Projects | Target |
|---------|----------------|--------|
| Pipeline architecture | Scrapy, Crawlee | `code-base/data-pipeline/` |
| Browser pool management | Crawlee | `code-base/browser-automation/` |
| Proxy rotation | Crawlee, Scrapy | `code-base/networking/` |
| HTML-to-Markdown for LLMs | Firecrawl | `code-base/ai-integration/` |
| MCP server pattern | Firecrawl, n8n | `code-base/ai-integration/` |
| Credential encryption | n8n | `code-base/auth/` |
| Auto-wait pattern | Playwright | `code-base/browser-automation/` |

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. PRs welcome for:
- New project analyses (follow TEMC template in any existing `.md`)
- Best practice additions
- Code extractions (L2 milestone)

## 📊 Scoring Methodology

**TEMC = T×0.25 + E×0.20 + M×0.30 + C×0.25**

| Dimension | Weight | What It Measures |
|-----------|--------|------------------|
| **T** (Technology) | 25% | Code quality, architecture, tech stack match, documentation |
| **E** (Ecosystem) | 20% | Stars/forks, community activity, maintainer reputation, integrations |
| **M** (Market) | 30% | Market timing, competitive scarcity, trend alignment, commercializability |
| **C** (Combination) | 25% | Tech stack compatibility, module extractability, commercial combo value, learning cost |

---

*Part of the [GitHub Open Source Knowledge Restructuring Project](https://github.com/bursh3347-collab). Powered by TEMC scoring methodology.*
