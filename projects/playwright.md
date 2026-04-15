# Playwright

> 微软出品的跨浏览器自动化框架，E2E测试+浏览器自动化的现代标准

| 指标 | 数据 |
|------|------|
| GitHub | [microsoft/playwright](https://github.com/microsoft/playwright) |
| Stars | ~86,500 |
| Forks | ~4,500 |
| License | Apache-2.0 |
| 语言 | TypeScript |
| 最后更新 | 2026-04-15 |
| Contributors | 500+ |
| 创建时间 | 2020-01-23 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 92 | TypeScript原生，auto-wait消除flaky tests，多浏览器(Chromium/Firefox/WebKit)，codegen代码生成，trace viewer调试，browser patches确保一致性 |
| E 生态 | 90 | 86k⭐，Microsoft维护，VS Code插件，Playwright Test runner，@playwright/mcp官方MCP server |
| M 市场 | 88 | AI Agent浏览器自动化最热赛道，测试+RPA+数据采集三合一。MCP server让AI Agent直接操控浏览器 |
| C 组合 | 90 | TypeScript原生=天子基准栈完美匹配。可直接用于AI Agent的Web交互层、数据采集、E2E测试 |
| **综合** | **90** | T×0.25+E×0.20+M×0.30+C×0.25 = 23+18+26.4+22.5 |

## 核心价值

解决跨浏览器Web自动化的可靠性问题。auto-wait机制、network interception、多浏览器一致性是核心差异化。在AI Agent时代，Playwright是浏览器操控的事实标准。

## 架构亮点

```
playwright/
├── packages/
│   ├── playwright/           ← 主包（用户安装）
│   ├── playwright-core/      ← 核心引擎（无浏览器捆绑）
│   ├── playwright-test/      ← 测试运行器
│   ├── trace-viewer/         ← 调试追踪UI
│   └── playwright-ct-*/      ← 组件测试适配器
├── browser_patches/          ← Chromium/Firefox/WebKit补丁
├── docs/                     ← 官方文档
├── tests/                    ← 海量测试
└── examples/                 ← 示例代码
```

**架构模式**：Client-Server（Browser Process ↔ Playwright Server ↔ User Script）

**核心设计**：
- **Browser Patches**：直接修补浏览器源码确保API一致性
- **Auto-wait**：自动等待元素可操作，消灭flaky tests
- **Network Interception**：拦截/修改HTTP请求
- **Trace Viewer**：时间旅行式调试（截图+DOM快照+网络日志）
- **Codegen**：录制浏览器操作自动生成代码

## 核心模块（5个）

1. **playwright-core引擎** — 浏览器通信协议+API封装（大）
2. **Auto-wait系统** — 智能等待+重试机制（中）
3. **Network拦截层** — 请求拦截/模拟/录制（中）
4. **Codegen/录制** — 操作录制→代码生成（中）
5. **Trace Viewer** — 调试追踪工具（大）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| Auto-wait模式 | ✅ | 简单参考 | 1h |
| Network拦截模式 | ✅ | 需适配 | 2h |
| Page Object模式 | ✅ | 简单复制 | 1h |
| 浏览器上下文隔离 | ✅ | 需适配 | 2h |

⭐通用代码候选：浏览器自动化Page Object模式（code-base/automation/page-object/）
⭐通用代码候选：Auto-wait重试模式（code-base/patterns/auto-wait/）

## 商业价值

- **痛点级别**：致命（AI Agent必须能操控浏览器，E2E测试是开发刚需）
- **TAM**：测试自动化$40B+ / RPA $14B+ / AI Agent工具市场$10B+
- **竞品**：Puppeteer（Chrome-only）、Selenium（老旧）、Cypress（测试专用）
- **可商用度**：Apache-2.0完全可商用，Microsoft长期维护有保障
- **差异化窗口**：@playwright/mcp让AI Agent直接用Playwright=最大机会

## 反证（为什么可能不值得用）

- 微软项目=可能随战略调整被低优先级化
- Browser patches维护成本极高，小团队无法fork维护
- 对于简单爬虫场景过于重量级（Cheerio/HTTP更轻量）
- MCP server生态仍在早期，稳定性待验证

## 天子点评

TypeScript原生+Apache-2.0+@playwright/mcp = AI Agent浏览器操控的唯一最优解，天子必学必用，零替代品。
