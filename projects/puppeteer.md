# Puppeteer

> Google Chrome DevTools团队出品的Chrome/Chromium自动化库

| 指标 | 数据 |
|------|------|
| GitHub | [puppeteer/puppeteer](https://github.com/puppeteer/puppeteer) |
| Stars | ~90,000 |
| Forks | ~9,000 |
| License | Apache-2.0 |
| 语言 | TypeScript |
| 最后更新 | 2026-04-15 |
| Contributors | 400+ |
| 创建时间 | 2017-08-16 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 85 | TypeScript，Chrome DevTools Protocol直接对接，PDF生成、截图、性能分析。但仅支持Chromium系浏览器 |
| E 生态 | 88 | 90k⭐，Google维护，npm周下载量3M+，Crawlee底层引擎之一 |
| M 市场 | 75 | 被Playwright在多浏览器场景超越，但Chrome-only场景仍是首选（PDF生成/截图服务） |
| C 组合 | 82 | TypeScript原生，与天子栈匹配。Chrome-only但覆盖95%+用户。Crawlee的Puppeteer crawler可直接用 |
| **综合** | **82** | T×0.25+E×0.20+M×0.30+C×0.25 = 21.25+17.6+22.5+20.5 |

## 核心价值

提供最原生的Chrome DevTools Protocol封装。PDF生成、截图、性能profiling等Chrome特有功能的首选。作为Playwright的前身，API设计影响了整个浏览器自动化领域。

## 架构亮点

```
puppeteer/
├── packages/
│   ├── puppeteer/           ← 主包（含Chromium下载）
│   ├── puppeteer-core/      ← 核心库（无浏览器捆绑）
│   └── browsers/            ← 浏览器管理
├── docker/                  ← Docker配置
├── docs/                    ← API文档
├── test/                    ← 测试
└── examples/                ← 示例
```

**架构模式**：单体+Monorepo，通过Chrome DevTools Protocol与浏览器通信

**核心设计**：
- **CDP直连**：Chrome DevTools Protocol原生支持，零抽象层损耗
- **Page/Frame/Worker模型**：清晰的浏览器抽象层次
- **Request Interception**：HTTP请求拦截与修改
- **Headless New**：Chrome原生headless模式（非旧版headless shell）

## 核心模块（4个）

1. **CDP通信层** — Chrome DevTools Protocol封装（大）
2. **Page/Frame API** — 页面操作抽象（大）
3. **浏览器管理** — 下载/启动/版本管理（中）
4. **PDF/截图** — 渲染输出（小）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| CDP通信模式 | ✅ | 需适配 | 3h |
| PDF生成服务 | ✅ | 简单复制 | 1h |
| 截图服务 | ✅ | 简单复制 | 1h |
| 浏览器版本管理 | ⚠️ | 复杂 | 4h |

⭐通用代码候选：PDF/截图生成服务（code-base/automation/pdf-screenshot/）

## 商业价值

- **痛点级别**：重要（PDF生成、截图SaaS、Chrome自动化是明确需求）
- **TAM**：PDF生成SaaS $1B+ / 截图API市场 $500M+
- **竞品**：Playwright（多浏览器）、CDP直连（更底层）
- **可商用度**：Apache-2.0完全可商用
- **差异化窗口**：PDF生成+截图=轻量SaaS，Puppeteer是最直接的实现路径

## 反证（为什么可能不值得用）

- Playwright已在多数场景替代Puppeteer（同团队，更强大）
- Chrome-only限制了跨浏览器兼容性测试场景
- Google可能降低维护优先级（Playwright由前Puppeteer团队创建）
- 社区新项目更倾向选Playwright而非Puppeteer

## 天子点评

PDF生成和截图SaaS的最短路径。但新项目直接上Playwright更全面，Puppeteer留给Chrome-only场景。
