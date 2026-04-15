# Selenium

> Web自动化的行业标准，W3C WebDriver协议的参考实现

| 指标 | 数据 |
|------|------|
| GitHub | [SeleniumHQ/selenium](https://github.com/SeleniumHQ/selenium) |
| Stars | 34,082 |
| Forks | 8,674 |
| License | Apache-2.0 |
| 语言 | Java (多语言：Java/Python/C#/Ruby/JavaScript/Rust) |
| 最后更新 | 2026-04-15 |
| Contributors | 800+ |
| Open Issues | 190 |
| 创建时间 | 2013-01-14（GitHub迁移，实际始于2004） |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 75 | W3C标准实现，多语言+多浏览器。但架构老旧（WebDriver协议开销大），不支持auto-wait，flaky tests常见 |
| E 生态 | 82 | 34k⭐+800+贡献者+22年历史。Selenium Grid分布式执行。企业级采用率极高（不看Stars看实际使用） |
| M 市场 | 60 | 被Playwright/Cypress等现代框架替代中。新项目很少选Selenium。但企业遗留系统迁移慢 |
| C 组合 | 55 | Java为主（非天子栈），JavaScript绑定存在但体验差。架构不适合AI Agent集成 |
| **综合** | **67** | T×0.25+E×0.20+M×0.30+C×0.25 = 18.75+16.4+18+13.75 |

## 核心价值

作为W3C WebDriver标准的参考实现，Selenium是浏览器自动化的「基础设施层」。Selenium Grid支持分布式测试。22年积累的企业采用率和多语言支持是最大资产。

## 架构亮点

```
selenium/
├── java/            ← Java绑定（核心）
├── py/              ← Python绑定
├── dotnet/          ← C#绑定
├── rb/              ← Ruby绑定
├── javascript/      ← JavaScript绑定
├── rust/            ← Rust组件（Selenium Manager）
├── cpp/             ← IE Driver（遗留）
├── common/          ← 共享资源
└── BUILD.bazel      ← Bazel构建系统
```

**架构模式**：Monorepo，Bazel构建，W3C WebDriver协议

**核心设计**：
- **W3C WebDriver标准**：浏览器厂商原生支持的标准协议
- **Selenium Grid**：分布式测试执行（Hub-Node架构）
- **Selenium Manager**：自动下载浏览器驱动（Rust编写）
- **多语言绑定**：统一的跨语言API设计

## 核心模块（4个）

1. **WebDriver Protocol** — W3C标准协议实现（大）
2. **Selenium Grid** — 分布式执行引擎（大）
3. **Selenium Manager** — 浏览器/驱动管理（Rust）（中）
4. **多语言绑定** — Java/Python/C#/Ruby/JS/Rust（巨大）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| Grid分布式模式 | ✅ | 架构参考 | 2h |
| WebDriver协议理解 | ✅ | 学习参考 | 1h |
| 浏览器管理(Rust) | ⚠️ | 复杂 | 8h |
| 多语言绑定设计 | ✅ | 架构参考 | 1h |

⭐通用代码候选：分布式执行Grid模式（code-base/patterns/distributed-grid/）

## 商业价值

- **痛点级别**：舒适（企业遗留系统需要Selenium Grid，但新项目不选）
- **TAM**：测试自动化$40B+（但Selenium份额在下降）
- **竞品**：Playwright（现代化替代）、Cypress（前端测试）、TestCafe
- **可商用度**：Apache-2.0完全可商用
- **差异化窗口**：Selenium Grid的分布式能力仍有参考价值

## 反证（为什么可能不值得用）

- 架构老旧，WebDriver协议额外通信开销
- 不支持auto-wait，flaky tests是最大痛点
- 新项目几乎不选Selenium（Playwright已成事实标准）
- Java为主，与天子TypeScript栈匹配度极低
- 学习ROI低：花时间学Selenium不如直接学Playwright

## 天子点评

历史遗产，学习ROI极低。把时间花在Playwright上，回报高100倍。
