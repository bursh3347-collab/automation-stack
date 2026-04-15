# 🗺️ Automation Stack 技术趋势路线图

> 最近更新：2026-04-15

## 🟢 当前主流

| 方向 | 代表项目 | 状态 |
|------|---------|------|
| AI驱动Web数据采集 | Firecrawl, Crawlee | 快速增长 |
| 浏览器自动化 | Playwright | 事实标准 |
| 低代码工作流自动化 | n8n, Zapier | 成熟市场 |
| Chrome DevTools自动化 | Puppeteer | 稳定 |

## 🚀 崛起方向

- **MCP集成自动化**：AI Agent通过MCP协议直接调用浏览器/爬虫能力（@playwright/mcp, n8n MCP节点）
- **AI原生数据管道**：HTML→Markdown→LLM结构化提取（Firecrawl模式成为标准）
- **无代码Agent工作流**：n8n AI节点+LLM Chain/Agent/Memory让非开发者构建AI工作流
- **Rust性能层**：Crawlee/Firecrawl底层引入Rust模块提升性能

## 📉 衰退方向

- **Selenium**：被Playwright全面替代，仅企业遗留系统使用
- **纯HTTP爬虫**：JavaScript渲染页面越来越多，纯HTTP请求覆盖率下降
- **手动触发自动化**：向事件驱动+AI自主触发演进

## 🔮 6-12月预测

1. Playwright MCP server成为AI Agent浏览器交互的事实标准
2. n8n AI工作流功能追平/超越Zapier AI
3. Firecrawl式"Web→LLM-ready"成为每个AI应用的标配能力
4. 反爬技术升级（Cloudflare Turnstile v3），爬虫框架需持续进化
5. 自动化工具向Agent化演进——从"按规则执行"到"按目标自主规划"

## 🏢 对一人公司的影响

- **核心工具链**：Playwright(浏览器) + Crawlee(爬虫) + n8n(工作流) = 一人公司自动化三件套
- **商业机会**：基于这三个工具构建垂直自动化SaaS（数据采集API、自动化代理、AI工作流模板）
- **技能投资**：TypeScript + Playwright + n8n是最高ROI的自动化技能组合
- **时间杠杆**：n8n工作流自动化可替代1-2人的手动运营工作

---

*由天工系统·代码猎手生成 | 2026-04-15*
