# 🔄 Automation & Workflow Stack — 横向对比表

> 12个TOP项目全方位对比，帮你快速选型

## 综合评分排名

| 排名 | 项目 | ⭐ Stars | TEMC综合 | T技术 | E生态 | M市场 | C组合 | License |
|------|------|---------|---------|-------|-------|-------|-------|---------|
| 1 | **Playwright** | 86.5k | **90** | 92 | 90 | 88 | 90 | Apache-2.0 |
| 2 | **Firecrawl** | 109k | **89** | 88 | 90 | 92 | 85 | ⚠️ AGPL-3.0 |
| 3 | **n8n** | 184k | **89** | 88 | 95 | 90 | 82 | ⚠️ Fair-code |
| 4 | **Activepieces** | 21.7k | **85** | 85 | 80 | 88 | 85 | ✅ MIT |
| 5 | **Crawlee** | 22.8k | **83** | 85 | 75 | 82 | 88 | Apache-2.0 |
| 6 | **Temporal** | 19.6k | **82** | 92 | 82 | 85 | 70 | MIT |
| 7 | **Puppeteer** | 90k | **82** | 85 | 88 | 75 | 82 | Apache-2.0 |
| 8 | **Inngest** | 5.2k | **82** | 88 | 68 | 85 | 85 | BSL-like |
| 9 | **Windmill** | 16.2k | **82** | 90 | 75 | 82 | 78 | ⚠️ AGPL-3.0 |
| 10 | **Scrapy** | 61.3k | **74** | 78 | 85 | 65 | 70 | BSD-3 |
| 11 | **Selenium** | 34k | **67** | 75 | 82 | 60 | 55 | Apache-2.0 |
| 12 | **Huginn** | 49.1k | **63** | 65 | 85 | 58 | 50 | MIT |

## 按使用场景推荐

### 🤖 AI Agent 浏览器操控
**首选：Playwright** → auto-wait + @playwright/mcp = AI Agent直接操控浏览器

### 📊 AI/LLM 数据采集
**首选：Firecrawl** → HTML→Markdown + LLM Extract = AI-ready数据

### ⚙️ 工作流自动化（可嵌入SaaS）
**首选：Activepieces** → MIT license + 400+ MCP servers + AI Agent native

### ⚙️ 工作流自动化（自托管基建）
**首选：n8n** → 184k stars + 400+集成 + AI节点 + 可视化编排

### 🔧 高性能脚本→API/UI
**首选：Windmill** → Rust引擎13x Airflow + 多语言脚本 + 自动生成UI

### 📦 SaaS后台任务（Serverless）
**首选：Inngest** → 零基础设施 + Vercel原生 + TypeScript step functions

### 🏗️ 关键业务工作流（大规模）
**首选：Temporal** → 持久执行 + 自动重试 + 事件溯源 + 企业级

### 🕷️ 大规模结构化爬虫
**首选：Crawlee**（TypeScript项目）/ **Scrapy**（Python项目）

### 🧪 E2E测试
**首选：Playwright** → 跨浏览器 + auto-wait + trace viewer

## 技术栈对比

| 特性 | Activepieces | Windmill | Huginn | Temporal | Inngest |
|------|-------------|----------|--------|----------|---------|
| **语言** | TypeScript | Rust+Svelte | Ruby | Go | Go+TS SDK |
| **基栈匹配** | 🟢 高 | 🟡 中 | 🔴 低 | 🟡 中(SDK) | 🟢 高 |
| **AI/MCP** | ✅ 原生 | ⚠️ 部分 | ❌ | ❌ | ⚠️ 可集成 |
| **自托管** | ✅ Docker | ✅ Docker | ✅ Docker | ✅ (复杂) | ✅ (可选Cloud) |
| **Serverless** | ❌ | ❌ | ❌ | ❌ | ✅ 原生 |
| **持久执行** | ⚠️ 部分 | ✅ | ❌ | ✅ 完整 | ✅ Steps |
| **可视化** | ✅ 编排器 | ✅ UI生成 | ✅ 基础 | ❌ (Web UI) | ❌ (Dev Server) |
| **免费tier** | ✅ 自托管 | ✅ 自托管 | ✅ 自托管 | ❌ | ✅ 5k events/mo |

## License 风险矩阵

| 项目 | License | 商业闭源SaaS | 嵌入产品 | 风险等级 |
|------|---------|-------------|---------|----------|
| Playwright | Apache-2.0 | ✅ | ✅ | 🟢 低 |
| Puppeteer | Apache-2.0 | ✅ | ✅ | 🟢 低 |
| Crawlee | Apache-2.0 | ✅ | ✅ | 🟢 低 |
| Selenium | Apache-2.0 | ✅ | ✅ | 🟢 低 |
| Scrapy | BSD-3 | ✅ | ✅ | 🟢 低 |
| Temporal | MIT | ✅ | ✅ | 🟢 低 |
| Huginn | MIT | ✅ | ✅ | 🟢 低 |
| **Activepieces** | **MIT (core)** | **✅** | **✅** | **🟢 低** |
| Inngest | BSL-like | ⚠️ 限制 | ✅ SDK | 🟡 中 |
| n8n | Fair-code | ⚠️ 不可竞品 | ⚠️ | 🟡 中 |
| Windmill | AGPL-3.0 | ❌ 需商业许可 | ❌ | 🔴 高 |
| Firecrawl | AGPL-3.0 | ❌ 需商业许可 | ❌ | 🔴 高 |

## 天子选型建议（2026 Solo Dev SaaS）

1. **必装**：Playwright（测试+AI Agent浏览器操控）
2. **必装**：Inngest（SaaS后台任务，零基础设施，Vercel原生）
3. **强烈推荐**：Activepieces（可嵌入SaaS的自动化引擎，MIT）
4. **强烈推荐**：Crawlee（TypeScript原生+Apache-2.0=最佳爬虫选择）
5. **推荐**：n8n（自托管工作流自动化，一人公司基础设施）
6. **按需**：Firecrawl（AI数据采集API调用模式，规避AGPL）
7. **规模后**：Temporal（关键业务工作流，需要时再上）
8. **内部工具**：Windmill（高性能脚本平台，内部用AGPL无碍）
9. **参考**：Puppeteer（Chrome特定场景，如PDF生成SaaS）
10. **历史参考**：Huginn（Agent设计模式的鼻祖，概念学习）
11. **参考**：Scrapy（Python数据管道，架构模式可借鉴）
12. **跳过**：Selenium（已被Playwright全面替代）

---
*最后更新：2026-04-16 | TEMC评分体系 by 天工·内阁首辅*
