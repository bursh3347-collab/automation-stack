# Crawlee

> Apify出品的TypeScript原生Web爬虫开发库，可靠+可扩展+生产级

| 指标 | 数据 |
|------|------|
| GitHub | [apify/crawlee](https://github.com/apify/crawlee) |
| Stars | 22,796 |
| Forks | 1,314 |
| License | Apache-2.0 |
| 语言 | TypeScript |
| 最后更新 | 2026-04-15 |
| Contributors | 150+ |
| Open Issues | 174 |
| 创建时间 | 2016-08-26 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 85 | TypeScript原生，支持Playwright/Puppeteer/Cheerio/JSDOM/HTTP多引擎。自动代理轮换、请求队列、自动缩放、数据存储 |
| E 生态 | 75 | 22.8k⭐，Apify公司维护（$200M+融资），Docker/云部署支持，但社区规模小于Scrapy |
| M 市场 | 82 | AI数据Pipeline需求增长，TypeScript生态缺少生产级爬虫库。Crawlee填补空白 |
| C 组合 | 88 | TypeScript原生=天子基准栈完美匹配。Apache-2.0完全可商用。可直接嵌入Next.js项目 |
| **综合** | **83** | T×0.25+E×0.20+M×0.30+C×0.25 = 21.25+15+24.6+22 |

## 核心价值

解决TypeScript生态缺少生产级爬虫库的问题。不同于Scrapy(Python-only)和Puppeteer(仅浏览器控制)，Crawlee提供完整的爬虫生命周期管理：URL发现→去重→请求队列→并发控制→数据存储→代理轮换。

## 架构亮点

```
crawlee/
├── packages/
│   ├── crawlee/              ← 主包（统一入口）
│   ├── core/                 ← 核心引擎
│   ├── basic-crawler/        ← 基础HTTP爬虫
│   ├── cheerio-crawler/      ← Cheerio解析爬虫
│   ├── jsdom-crawler/        ← JSDOM爬虫
│   ├── playwright-crawler/   ← Playwright浏览器爬虫
│   ├── puppeteer-crawler/    ← Puppeteer浏览器爬虫
│   ├── http-crawler/         ← 纯HTTP爬虫
│   ├── browser-pool/         ← 浏览器实例池管理
│   ├── proxy-rotation/       ← 代理轮换
│   └── utils/                ← 工具集
├── docs/                     ← 文档
├── test/                     ← 测试
└── website/                  ← 文档网站
```

**架构模式**：Monorepo（Yarn + Lerna + Turborepo），插件式多引擎

**核心设计**：
- **多引擎统一接口**：Playwright/Puppeteer/Cheerio/JSDOM/HTTP共享相同的Router+Handler API
- **RequestQueue**：分布式请求队列，自动去重+优先级
- **AutoscaledPool**：根据系统资源自动调节并发数
- **ProxyRotation**：智能代理轮换+健康检查
- **SessionPool**：会话管理+Cookie持久化

## 核心模块（5个）

1. **Core Engine** — 爬虫基类+路由+生命周期管理（大）
2. **Browser Pool** — 浏览器实例池化管理（中）
3. **Request Queue** — 请求队列+去重+优先级（中）
4. **Proxy Rotation** — 代理管理+轮换+健康检查（小）
5. **Storage** — 数据集+Key-Value存储+请求队列持久化（中）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| 多引擎统一接口模式 | ✅ | 架构参考 | 2h |
| Browser Pool | ✅ | 需适配 | 3h |
| Request Queue | ✅ | 简单复制 | 2h |
| Proxy Rotation | ✅ | 简单复制 | 1h |
| AutoscaledPool | ✅ | 需适配 | 2h |

⭐通用代码候选：请求队列+去重（code-base/automation/request-queue/）
⭐通用代码候选：代理轮换（code-base/automation/proxy-rotation/）
⭐通用代码候选：浏览器实例池（code-base/automation/browser-pool/）

## 商业价值

- **痛点级别**：重要（TypeScript开发者需要可靠的爬虫库）
- **TAM**：Web Scraping市场$2.4B (2026) + AI Data Pipeline市场
- **竞品**：Scrapy（Python）、Firecrawl（AI原生但AGPL）、Colly（Go）
- **可商用度**：✅ Apache-2.0完全可商用=天子最佳选择
- **差异化窗口**：TypeScript + Apache-2.0 + 多引擎=唯一同时满足三条件的生产级爬虫库

## 反证（为什么可能不值得用）

- Stars远低于竞品（22k vs Scrapy 61k vs Playwright 86k）
- Apify公司可能将核心功能限制在Apify Cloud平台
- 文档质量不如Playwright/Scrapy
- 社区贡献者数量有限，Bus Factor风险

## 天子点评

TypeScript+Apache-2.0+生产级 = 天子自建爬虫的唯一选择。Stars低但Apify公司维护，稳定可靠，直接用。
