[English](README.md) | [中文](README_CN.md)

# 🤖 automation-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/automation-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/automation-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/automation-stack?style=flat-square)

> ⭐ Maturity: **L1 Growing** — 7 top projects analyzed, horizontal comparison + best practices complete.

Extracted best practices, workflow patterns, and deep analysis from **7 high-star automation & web scraping tools** on GitHub. Each project is scored using our [TEMC methodology](#temc-scoring) (Technology × Ecosystem × Market × Combo).

## 📈 Trending Board (Updated: 2026-04-15)

| Rank | Project | Stars | TEMC | Trend |
|------|---------|-------|------|-------|
| 1 | n8n | 184k | 89 | 🚀 |
| 2 | Firecrawl | 109k | 89 | 🚀 |
| 3 | Puppeteer | 90k | 82 | → |
| 4 | Playwright | 86.5k | 90 | 🚀 |
| 5 | Scrapy | 61.3k | 74 | → |
| 6 | Selenium | 34k | 67 | ↓ |
| 7 | Crawlee | 22.8k | 83 | ↑ |

## 📋 What's Inside

### Projects Analyzed (7)

| Project | Stars | TEMC | Language | Category |
|---------|-------|------|----------|----------|
| [Playwright](projects/playwright.md) | 86.5k | **90** 🏆 | TypeScript | Cross-browser Automation |
| [Firecrawl](projects/firecrawl.md) | 109k | **89** 🏆 | TypeScript | AI-powered Web Scraping |
| [n8n](projects/n8n.md) | 184k | **89** 🏆 | TypeScript | Workflow Automation |
| [Crawlee](projects/crawlee.md) | 22.8k | **83** | TypeScript | Web Crawling Library |
| [Puppeteer](projects/puppeteer.md) | 90k | **82** | TypeScript | Chrome Automation |
| [Scrapy](projects/scrapy.md) | 61.3k | **74** | Python | Web Scraping Framework |
| [Selenium](projects/selenium.md) | 34k | **67** | Multi | Browser Automation (Legacy) |

### Comparison & Best Practices

- [📊 Automation Tools Comparison](comparison.md) — Full horizontal comparison
- [🕷️ Scraping Patterns](best-practices/scraping-patterns.md) — Anti-detection, retry, proxy rotation
- [⚙️ Workflow Automation](best-practices/workflow-automation.md) — Event-driven patterns, error handling

## 🎯 Quick Picks for Solo Developers

Based on a TypeScript + Next.js + Supabase + Vercel stack:

| Use Case | Pick | Why |
|----------|------|-----|
| AI Agent browser control | **Playwright** | TypeScript-native + @playwright/mcp |
| AI data extraction | **Firecrawl** | HTML→Markdown + LLM Extract API |
| Workflow automation | **n8n** | 400+ integrations + AI nodes + MCP |
| Production-grade scraping | **Crawlee** | TypeScript + Apache-2.0 |
| PDF/screenshot service | **Puppeteer** | Best Chrome-native capabilities |

## 🏗️ Repository Structure

```
automation-stack/
├── README.md              ← You are here
├── README_CN.md           ← 中文版
├── projects/              ← 7 project analyses (TEMC scored)
├── best-practices/        ← Cross-project patterns
├── code/                  ← Extracted code (coming in L2)
├── comparison.md          ← Horizontal comparison table
└── SOURCES.md             ← All source links + licenses
```

## <a id="temc-scoring"></a>📊 TEMC Scoring

**TEMC** = Technology × 0.25 + Ecosystem × 0.20 + Market × 0.30 + Combo × 0.25

- **T (Technology)**: Code quality, architecture, tech stack fit, docs
- **E (Ecosystem)**: Stars/forks, community activity, integrations, maintainer reputation
- **M (Market)**: Timing, competitive scarcity, trend alignment, commercializability
- **C (Combo)**: Stack compatibility, modularity, business combo potential, learning cost

## ⚔️ Solo Dev Verdict

**Playwright is the king of browser automation for TypeScript devs.** It's faster, more reliable, and better-typed than Puppeteer — and the `@playwright/mcp` integration makes it the default choice for AI agent browser control.

**Firecrawl is the scraping game-changer.** Instead of wrestling with selectors and pagination, you get clean Markdown from any URL — perfect for RAG pipelines and LLM data ingestion.

**n8n is your ops backbone.** Self-hostable, 400+ integrations, visual workflow builder. For a solo dev, n8n replaces the need for a dedicated ops engineer.

## 🔗 Related Stacks

- [code-base](https://github.com/bursh3347-collab/code-base) — Shared utility code
- [ai-agent-stack](https://github.com/bursh3347-collab/ai-agent-stack) — AI Agent frameworks
- [security-stack](https://github.com/bursh3347-collab/security-stack) — Security tools

---

*Powered by [TEMC scoring methodology](https://github.com/bursh3347-collab). Data updated 2026-04-15.*
