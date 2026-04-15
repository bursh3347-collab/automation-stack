[English](README.md) | [中文](README_CN.md)

# 🤖 automation-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/automation-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/automation-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/automation-stack?style=flat-square)

> ⭐ 成熟度: **L1 成长期** — 7个TOP项目已分析，横向对比+最佳实践已完成

从GitHub全域 **7个高星自动化/爬虫/工作流项目** 中拆解精华、提炼最佳实践、横向对比选型。每个项目使用 [TEMC评分体系](#temc评分) 量化评估。

## 📈 飙升榜（更新：2026-04-15）

| 排名 | 项目 | 总Stars | TEMC | 趋势 |
|------|------|---------|------|------|
| 1 | n8n | 184k | 89 | 🚀 |
| 2 | Firecrawl | 109k | 89 | 🚀 |
| 3 | Puppeteer | 90k | 82 | → |
| 4 | Playwright | 86.5k | 90 | 🚀 |
| 5 | Scrapy | 61.3k | 74 | → |
| 6 | Selenium | 34k | 67 | ↓ |
| 7 | Crawlee | 22.8k | 83 | ↑ |

## 📋 仓库内容

### 已分析项目 (7)

| 项目 | Stars | TEMC | 语言 | 类别 |
|------|-------|------|------|------|
| [Playwright](projects/playwright.md) | 86.5k | **90** 🏆 | TypeScript | 跨浏览器自动化 |
| [Firecrawl](projects/firecrawl.md) | 109k | **89** 🏆 | TypeScript | AI驱动Web数据采集 |
| [n8n](projects/n8n.md) | 184k | **89** 🏆 | TypeScript | 工作流自动化平台 |
| [Crawlee](projects/crawlee.md) | 22.8k | **83** | TypeScript | TypeScript原生爬虫库 |
| [Puppeteer](projects/puppeteer.md) | 90k | **82** | TypeScript | Chrome自动化 |
| [Scrapy](projects/scrapy.md) | 61.3k | **74** | Python | Python爬虫框架 |
| [Selenium](projects/selenium.md) | 34k | **67** | Multi | Web自动化经典 |

### 对比与最佳实践

- [📊 自动化工具横向对比](comparison.md) — 全面横向对比
- [🕷️ 爬虫设计模式](best-practices/scraping-patterns.md) — 反检测、重试、代理轮换
- [⚙️ 工作流自动化](best-practices/workflow-automation.md) — 事件驱动模式、错误处理

## 🎯 天子快速选型

基于天子基准技术栈（TypeScript + Next.js + Supabase + Vercel）：

| 场景 | 首选 | 理由 |
|------|------|------|
| AI Agent浏览器操控 | **Playwright** | TypeScript原生 + @playwright/mcp |
| AI数据采集 | **Firecrawl** | HTML→Markdown + LLM Extract |
| 工作流自动化 | **n8n** | 400+集成 + AI节点 + MCP |
| 生产级爬虫 | **Crawlee** | TypeScript + Apache-2.0 |
| PDF/截图服务 | **Puppeteer** | Chrome原生能力最强 |

## 🏗️ 仓库结构

```
automation-stack/
├── README.md              ← 英文版
├── README_CN.md           ← 你在这里
├── projects/              ← 7个项目TEMC分析
├── best-practices/        ← 跨项目最佳实践
├── code/                  ← 精华代码提取（L2阶段）
├── comparison.md          ← 横向对比表
└── SOURCES.md             ← 所有来源清单
```

## <a id="temc评分"></a>📊 TEMC评分体系

**综合评分** = T×0.25 + E×0.20 + M×0.30 + C×0.25

- **T（技术分）**: 代码质量、架构设计、技术栈匹配度、文档质量
- **E（生态分）**: Stars/Forks、社区活跃度、生态集成度、维护者信誉
- **M（时机分）**: 市场时机、竞品稀缺度、趋势匹配度、可商用性
- **C（组合分）**: 技术栈兼容性、模块可拆解性、商业组合价值、学习成本

## ⚔️ 天子点评

**Playwright是TypeScript开发者浏览器自动化的王者。** 比Puppeteer更快、更可靠、类型更完善——`@playwright/mcp`集成使其成为AI Agent浏览器控制的默认选择。

**Firecrawl是爬虫领域的颠覆者。** 不再纠结选择器和分页，任何URL直接返回干净Markdown——完美适配RAG管道和LLM数据摄取。

**n8n是你的运维中枢。** 可自托管、400+集成、可视化工作流构建器。对独立开发者来说，n8n替代了专职运维工程师的需求。

## 🔗 相关分类

- [code-base](https://github.com/bursh3347-collab/code-base) — 通用代码库
- [ai-agent-stack](https://github.com/bursh3347-collab/ai-agent-stack) — AI Agent分类
- [security-stack](https://github.com/bursh3347-collab/security-stack) — 安全工具分类

---

*由 [天工系统·代码猎手](https://github.com/bursh3347-collab) 自动化产出 | TEMC评分体系 | 更新于 2026-04-15*
