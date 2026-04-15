# Scrapy

> Python高性能异步Web爬虫框架，16年历史的行业标杆

| 指标 | 数据 |
|------|------|
| GitHub | [scrapy/scrapy](https://github.com/scrapy/scrapy) |
| Stars | 61,334 |
| Forks | 11,472 |
| License | BSD-3-Clause |
| 语言 | Python |
| 最后更新 | 2026-04-15 |
| Contributors | 500+ |
| Open Issues | 637 |
| 创建时间 | 2010-02-22 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 78 | Twisted异步引擎成熟稳定，中间件/Pipeline架构优秀，Spider协议清晰。但Python-only，不支持JS渲染 |
| E 生态 | 85 | 61k⭐+11k forks，16年历史，Scrapy Cloud/Splash/Portia生态完整，PyPI下载量巨大 |
| M 市场 | 65 | 成熟稳定市场，增长平缓。AI时代被Firecrawl/Crawlee等新框架分流，但传统爬虫需求仍在 |
| C 组合 | 70 | Python（非天子主栈TypeScript），但数据Pipeline场景有用。可通过API调用集成 |
| **综合** | **74** | T×0.25+E×0.20+M×0.30+C×0.25 = 19.5+17+19.5+17.5 |

## 核心价值

解决大规模结构化Web数据抓取问题。通过异步引擎+中间件+Pipeline架构，实现高性能、可扩展的爬虫系统。16年积累的稳定性和社区生态是最大资产。

## 架构亮点

```
scrapy/
├── scrapy/           ← 核心框架
│   ├── spiders/      ← Spider基类
│   ├── downloadermiddlewares/  ← 下载中间件
│   ├── spidermiddlewares/     ← Spider中间件
│   ├── pipelines/    ← 数据处理Pipeline
│   ├── core/         ← 引擎核心（Twisted事件循环）
│   ├── http/         ← HTTP请求/响应
│   └── settings/     ← 配置系统
├── docs/             ← ReadTheDocs文档
├── tests/            ← 完整测试套件
└── pyproject.toml    ← 现代Python打包
```

**架构模式**：Engine → Scheduler → Downloader → Spider → Pipeline（管道式处理）

**核心设计**：
- **Twisted异步引擎**：单线程非阻塞IO，高并发低资源
- **中间件链**：请求/响应双向拦截，灵活扩展（代理、UA、重试、限速）
- **Item Pipeline**：数据清洗→验证→存储的标准化流水线
- **Signal系统**：引擎事件广播，松耦合扩展

## 核心模块（5个）

1. **Engine核心** — 调度引擎，协调所有组件（大）
2. **Downloader + 中间件** — HTTP下载+代理/UA/限速（大）
3. **Spider框架** — 解析逻辑+CSS/XPath选择器（中）
4. **Item Pipeline** — 数据处理流水线（小）
5. **Feed Exporters** — JSON/CSV/XML导出（小）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| 中间件架构模式 | ✅ | 需适配(TypeScript重写) | 4h |
| Pipeline数据处理模式 | ✅ | 需适配 | 3h |
| 限速/去重策略 | ✅ | 简单复制思路 | 2h |
| Feed导出器 | ⚠️ | 需重写 | 3h |

⭐通用代码候选：中间件链模式（code-base/patterns/middleware-chain/）

## 商业价值

- **痛点级别**：重要（大规模数据采集是AI训练/RAG的刚需）
- **TAM**：Web Scraping市场$2.4B (2026)
- **竞品**：Firecrawl（AI原生）、Crawlee（TypeScript原生）、Beautiful Soup（轻量级）
- **可商用度**：BSD许可完全可商用，但Python限制了天子的直接使用
- **差异化窗口**：Scrapy在AI时代的差异化在于成熟的中间件生态和Scrapy Cloud托管

## 反证（为什么可能不值得用）

- Python-only，与天子TypeScript基准栈不匹配
- 不支持JavaScript渲染（需Splash/Playwright额外集成）
- 架构成熟但创新停滞，社区活力不如新项目
- 对AI/LLM场景无原生支持（需手动集成）
