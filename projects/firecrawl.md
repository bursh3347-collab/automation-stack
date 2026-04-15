# Firecrawl

> AI驱动的Web数据抓取引擎，将网页转换为LLM-ready的Markdown/结构化数据

| 指标 | 数据 |
|------|------|
| GitHub | [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) |
| Stars | 109,401 |
| Forks | 7,006 |
| License | AGPL-3.0 |
| 语言 | TypeScript |
| 最后更新 | 2026-04-15 |
| Contributors | 200+ |
| 创建时间 | 2024-04-15 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 88 | TypeScript+Rust混合，HTML→Markdown转换、结构化数据提取（LLM Extract）、JavaScript渲染、反爬绕过。自托管Docker支持 |
| E 生态 | 90 | 109k⭐（2年内从0→109k=火箭增长），MCP server官方支持，9种语言SDK，Mendable公司维护 |
| M 市场 | 92 | AI/LLM数据Pipeline刚需。RAG、Agent、训练数据采集的首选工具。时机窗口完美 |
| C 组合 | 85 | TypeScript原生，MCP集成，REST API。⚠️但AGPL-3.0限制商业闭源使用（需购买商业许可或自托管） |
| **综合** | **89** | T×0.25+E×0.20+M×0.30+C×0.25 = 22+18+27.6+21.25 |

## 核心价值

解决AI/LLM应用的Web数据获取问题。不是传统爬虫，而是"Web→AI-ready Data"的转换引擎。核心差异化：HTML→clean Markdown + 结构化数据提取 + 反爬绕过。

## 架构亮点

```
firecrawl/
├── apps/
│   ├── api/              ← 主API服务（TypeScript）
│   ├── rust-sdk/         ← Rust性能模块
│   ├── python-sdk/       ← Python SDK
│   ├── js-sdk/           ← JavaScript SDK
│   └── go-sdk/           ← Go SDK
├── examples/             ← 使用示例
├── docker-compose.yaml   ← 自托管配置
└── SELF_HOST.md          ← 自托管文档
```

**架构模式**：API服务+多SDK+Docker自托管

**核心设计**：
- **Scrape→Map→Crawl三模式**：单页抓取/站点地图/深度爬取
- **LLM Extract**：用LLM从页面提取结构化数据（JSON Schema定义）
- **Markdown转换**：智能清洗HTML→干净Markdown（去导航/广告/噪音）
- **反爬绕过**：代理轮换+浏览器指纹+Cloudflare bypass
- **MCP Server**：AI Agent直接调用Web抓取能力

## 核心模块（5个）

1. **HTML→Markdown引擎** — 核心转换逻辑，去噪+格式化（大）
2. **LLM Extract** — 结构化数据提取（中）
3. **Crawl引擎** — 深度爬取+URL发现+并发控制（大）
4. **反爬系统** — 代理管理+指纹+bypass（中）
5. **API层** — REST API+认证+速率限制（中）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| HTML→Markdown转换 | ✅ | 需适配(AGPL注意) | 3h |
| LLM Extract模式 | ✅ | 简单参考思路 | 2h |
| 反爬策略 | ✅ | 需适配 | 3h |
| MCP Server模式 | ✅ | 简单参考 | 2h |

⭐通用代码候选：HTML→Markdown清洗（code-base/data-extraction/html-to-markdown/）
⭐通用代码候选：MCP Server集成模式（code-base/ai-integration/mcp-server/）

## 商业价值

- **痛点级别**：致命（AI应用=数据密集，Web是最大数据源）
- **TAM**：Web Data Extraction $5B+ / AI Data Pipeline $10B+
- **竞品**：Crawlee（Apache-2.0）、Jina Reader（开源）、Apify（PaaS）
- **可商用度**：⚠️ AGPL-3.0=衍生作品必须开源。商业使用需购买许可或纯API调用
- **差异化窗口**：LLM Extract + MCP = AI Agent原生数据获取层

## 反证（为什么可能不值得用）

- **AGPL-3.0是最大风险**：任何基于Firecrawl的衍生作品必须开源，限制商业闭源SaaS
- 109k⭐中大量是AI hype驱动，实际生产使用率待验证
- 自托管资源消耗较大（需浏览器实例+代理池）
- Mendable公司商业模式（Cloud API）可能限制开源版功能
