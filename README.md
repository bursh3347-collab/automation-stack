# 🔄 automation-stack

> ⭐ Maturity: **L1 Growing** — 7个TOP项目已分析，横向对比+最佳实践已完成

从GitHub全域自动化/爬虫/工作流高星项目中，拆解精华、提炼最佳实践、横向对比选型。

**TEMC评分体系** | **天工·代码猎手自动化产出** | **Apache-2.0**

---

## 📈 本分类飙升榜（最近更新：2026-04-15）

| 排名 | 项目 | 总Stars | TEMC | 趋势 |
|------|------|---------|------|------|
| 1 | n8n | 184k | 89 | 🚀 |
| 2 | Firecrawl | 109k | 89 | 🚀 |
| 3 | Puppeteer | 90k | 82 | → |
| 4 | Playwright | 86.5k | 90 | 🚀 |
| 5 | Scrapy | 61.3k | 74 | → |
| 6 | Selenium | 34k | 67 | ↓ |
| 7 | Crawlee | 22.8k | 83 | ↑ |

## 📂 仓库结构

```
automation-stack/
├── README.md              ← 你在这里
├── projects/              ← 7个高星项目的TEMC分析
│   ├── playwright.md      ← 🏆 TEMC 90 — TypeScript跨浏览器自动化
│   ├── firecrawl.md       ← 🏆 TEMC 89 — AI驱动Web数据采集
│   ├── n8n.md             ← 🏆 TEMC 89 — 工作流自动化平台
│   ├── crawlee.md         ← TEMC 83 — TypeScript原生爬虫库
│   ├── puppeteer.md       ← TEMC 82 — Chrome自动化
│   ├── scrapy.md          ← TEMC 74 — Python爬虫框架
│   └── selenium.md        ← TEMC 67 — Web自动化经典
├── best-practices/        ← 从多个项目中提炼的最佳实践
│   ├── scraping-patterns.md   ← 爬虫设计模式
│   └── workflow-automation.md ← 工作流自动化模式
├── code/                  ← 精华代码提取（待填充）
├── comparison.md          ← 7个项目横向对比表
└── SOURCES.md             ← 所有来源清单
```

## 🎯 天子快速选型

基于天子基准技术栈（TypeScript + Next.js + Supabase + Vercel）：

| 场景 | 首选 | 理由 |
|------|------|------|
| AI Agent浏览器操控 | **Playwright** | TypeScript原生 + @playwright/mcp |
| AI数据采集 | **Firecrawl** | HTML→Markdown + LLM Extract |
| 工作流自动化 | **n8n** | 400+集成 + AI节点 + MCP |
| 生产级爬虫 | **Crawlee** | TypeScript + Apache-2.0 |
| PDF/截图服务 | **Puppeteer** | Chrome原生能力最强 |

## 🔗 相关分类

- [code-base](https://github.com/bursh3347-collab/code-base) — 通用代码库
- [ai-agent-stack](https://github.com/bursh3347-collab/ai-agent-stack) — AI Agent分类

---

*由 [天工系统·代码猎手](https://github.com/bursh3347-collab) 自动化产出 | TEMC评分体系*
