# 🤖 automation-stack

> ⭐ Maturity: **L1 Growing** — 7 projects analyzed, comparison and best practices available.

Extracted best practices and deep analyses from the world's top automation & web scraping open-source projects.

## 📊 Leaderboard (by TEMC Score)

| Rank | Project | Stars | TEMC | Trend |
|------|---------|-------|------|-------|
| 1 | [Firecrawl](projects/firecrawl.md) | ~70k | **89** | 🚀 |
| 2 | [Playwright](projects/playwright.md) | 86k | **88** | 🚀 |
| 3 | [n8n](projects/n8n.md) | ~60k | **85** | ↑ |
| 4 | [Crawlee](projects/crawlee.md) | 17k | **81** | ↑ |
| 5 | [Scrapy](projects/scrapy.md) | 61k | **80** | → |
| 6 | [Puppeteer](projects/puppeteer.md) | 94k | **80** | → |
| 7 | [Selenium](projects/selenium.md) | 32k | **67** | ↓ |

## 📂 Repository Structure

```
automation-stack/
├── README.md              ← You are here
├── projects/              ← Individual project analyses (TEMC-scored)
│   ├── scrapy.md
│   ├── playwright.md
│   ├── puppeteer.md
│   ├── firecrawl.md
│   ├── crawlee.md
│   ├── n8n.md
│   └── selenium.md
├── best-practices/        ← Extracted patterns from multiple projects
│   ├── scraping-patterns.md
│   └── workflow-automation.md
├── code/                  ← Extracted code (coming in L2)
├── comparison.md          ← Side-by-side comparison table
└── SOURCES.md             ← All source projects with links
```

## 🎯 What This Repo Is

This is **not** a bookmark list. Each project is deeply analyzed with:
- **TEMC Score**: Technology (T), Ecosystem (E), Market (M), Combination potential (C)
- **Architecture analysis**: How the project is built and why
- **Extractable patterns**: What code/patterns can be reused
- **Comparison tables**: Side-by-side feature comparison
- **Best practices**: Patterns distilled from multiple projects

## 🔥 Quick Picks

- **Building an AI scraping pipeline?** → Start with [Firecrawl](projects/firecrawl.md)
- **Need browser automation/testing?** → Use [Playwright](projects/playwright.md)
- **Building workflow automation?** → Study [n8n](projects/n8n.md)
- **TypeScript web crawler?** → Check [Crawlee](projects/crawlee.md)
- **Python-heavy data pipeline?** → Go with [Scrapy](projects/scrapy.md)

## 📈 Scraping Patterns

See [best-practices/scraping-patterns.md](best-practices/scraping-patterns.md) for universal patterns including:
- Pipeline architecture
- Anti-bot strategies
- Content extraction for AI
- Retry with exponential backoff
- Concurrency control

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines. PRs welcome for:
- New project analyses (follow TEMC template)
- Best practice additions
- Code extractions

---

*Part of the [GitHub Open Source Knowledge Restructuring Project](https://github.com/bursh3347-collab). Powered by TEMC scoring methodology.*
