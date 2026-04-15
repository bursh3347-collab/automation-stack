# 🔄 Automation & Scraping Stack — 横向对比表

> 7个TOP项目全方位对比，帮你快速选型

## 综合评分排名

| 排名 | 项目 | ⭐ Stars | TEMC综合 | T技术 | E生态 | M市场 | C组合 | License |
|------|------|---------|---------|-------|-------|-------|-------|---------|
| 1 | **Playwright** | 86.5k | **90** | 92 | 90 | 88 | 90 | Apache-2.0 |
| 2 | **Firecrawl** | 109k | **89** | 88 | 90 | 92 | 85 | ⚠️ AGPL-3.0 |
| 3 | **n8n** | 184k | **89** | 88 | 95 | 90 | 82 | ⚠️ Fair-code |
| 4 | **Crawlee** | 22.8k | **83** | 85 | 75 | 82 | 88 | Apache-2.0 |
| 5 | **Puppeteer** | 90k | **82** | 85 | 88 | 75 | 82 | Apache-2.0 |
| 6 | **Scrapy** | 61.3k | **74** | 78 | 85 | 65 | 70 | BSD-3 |
| 7 | **Selenium** | 34k | **67** | 75 | 82 | 60 | 55 | Apache-2.0 |

## 按使用场景推荐

### 🤖 AI Agent 浏览器操控
**首选：Playwright** → auto-wait + @playwright/mcp = AI Agent直接操控浏览器
备选：Puppeteer（Chrome-only场景）

### 📊 AI/LLM 数据采集
**首选：Firecrawl** → HTML→Markdown + LLM Extract = AI-ready数据
备选：Crawlee（需要Apache-2.0许可时）

### 🕷️ 大规模结构化爬虫
**首选：Crawlee**（TypeScript项目）/ **Scrapy**（Python项目）
备选：Firecrawl（API模式调用）

### ⚙️ 工作流自动化
**首选：n8n** → 400+集成 + AI节点 + 可视化编排
备选：自研webhook + Playwright（轻量场景）

### 🧪 E2E测试
**首选：Playwright** → 跨浏览器 + auto-wait + trace viewer
备选：Cypress（前端专用）

### 📄 PDF生成/截图服务
**首选：Puppeteer** → Chrome原生PDF/截图能力最强
备选：Playwright

## 技术栈对比

| 特性 | Playwright | Firecrawl | n8n | Crawlee | Puppeteer | Scrapy | Selenium |
|------|-----------|-----------|-----|---------|-----------|--------|----------|
| **语言** | TypeScript | TypeScript | TypeScript | TypeScript | TypeScript | Python | Java(多语言) |
| **JS渲染** | ✅ 多浏览器 | ✅ 内置 | ⚠️ 需集成 | ✅ 多引擎 | ✅ Chrome | ❌ 需Splash | ✅ WebDriver |
| **Auto-wait** | ✅ | N/A | N/A | ⚠️ 部分 | ❌ | N/A | ❌ |
| **MCP支持** | ✅ 官方 | ✅ 官方 | ✅ 双向 | ❌ | ❌ | ❌ | ❌ |
| **代理轮换** | ⚠️ 手动 | ✅ 内置 | ⚠️ 需节点 | ✅ 自动 | ⚠️ 手动 | ✅ 中间件 | ⚠️ 手动 |
| **分布式** | ❌ | ✅ API | ✅ Worker | ✅ Apify Cloud | ❌ | ✅ Scrapy Cloud | ✅ Grid |
| **AI集成** | ⚠️ MCP | ✅ 原生 | ✅ AI节点 | ❌ | ❌ | ❌ | ❌ |
| **自托管** | N/A | ✅ Docker | ✅ Docker | ✅ Docker | N/A | ✅ | ✅ Grid |

## License 风险矩阵

| 项目 | License | 商业闭源SaaS | 内部使用 | 修改后分发 | 风险等级 |
|------|---------|-------------|---------|-----------|----------|
| Playwright | Apache-2.0 | ✅ | ✅ | ✅ | 🟢 低 |
| Puppeteer | Apache-2.0 | ✅ | ✅ | ✅ | 🟢 低 |
| Crawlee | Apache-2.0 | ✅ | ✅ | ✅ | 🟢 低 |
| Selenium | Apache-2.0 | ✅ | ✅ | ✅ | 🟢 低 |
| Scrapy | BSD-3 | ✅ | ✅ | ✅ | 🟢 低 |
| n8n | Fair-code | ⚠️ 不可竞品 | ✅ | ⚠️ 限制 | 🟡 中 |
| Firecrawl | AGPL-3.0 | ❌ 需商业许可 | ⚠️ 衍生需开源 | ❌ 必须开源 | 🔴 高 |

## 天子选型建议

基于天子基准技术栈（TypeScript + Next.js + Supabase + Vercel）：

1. **必装**：Playwright（测试+AI Agent浏览器操控）
2. **强烈推荐**：Crawlee（TypeScript原生+Apache-2.0=最佳爬虫选择）
3. **推荐**：n8n（自托管工作流自动化，一人公司基础设施）
4. **按需**：Firecrawl（AI数据采集API调用模式，规避AGPL）
5. **了解**：Puppeteer（Chrome特定场景，如PDF生成SaaS）
6. **参考**：Scrapy（Python数据管道，架构模式可借鉴）
7. **跳过**：Selenium（已被Playwright全面替代）

---
*最后更新：2026-04-15 | TEMC评分体系 by 天工·代码猎手*
