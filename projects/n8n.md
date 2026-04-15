# n8n

> 开源AI原生工作流自动化平台，400+集成+可视化编排+自托管

| 指标 | 数据 |
|------|------|
| GitHub | [n8n-io/n8n](https://github.com/n8n-io/n8n) |
| Stars | 184,163 |
| Forks | 56,819 |
| License | Sustainable Use License (Fair-code) |
| 语言 | TypeScript |
| 最后更新 | 2026-04-15 |
| Contributors | 700+ |
| Open Issues | 1,463 |
| 创建时间 | 2019-06-22 |

## TEMC评分

| 维度 | 分数 | 理由 |
|------|------|------|
| T 技术 | 88 | TypeScript monorepo，可视化编排+代码混合，AI节点（LLM/Agent/Memory/Vector Store），MCP client+server双向支持 |
| E 生态 | 95 | 184k⭐（自动化领域全球第一），400+集成，社区模板丰富，n8n Cloud商业运营 |
| M 市场 | 90 | AI+自动化=2026最热赛道。替代Zapier/Make的开源方案。一人公司必备基础设施 |
| C 组合 | 82 | TypeScript原生，可嵌入webhook触发。但系统复杂（pnpm monorepo 30+packages），集成成本高 |
| **综合** | **89** | T×0.25+E×0.20+M×0.30+C×0.25 = 22+19+27+20.5 |

## 核心价值

解决业务流程自动化问题。从简单的Webhook→处理→输出，到复杂的AI Agent工作流，n8n是开源自动化的事实标准。AI节点让非开发者也能构建AI工作流。

## 架构亮点

```
n8n/
├── packages/
│   ├── cli/              ← CLI入口+服务器
│   ├── core/             ← 工作流引擎核心
│   ├── workflow/          ← 工作流定义+执行
│   ├── nodes-base/       ← 400+内置节点
│   ├── editor-ui/        ← Vue.js可视化编辑器
│   ├── @n8n/ai-workflow-* ← AI工作流模块
│   └── @n8n/chat/        ← 聊天UI组件
├── docker/               ← Docker部署
├── scripts/              ← 构建脚本
└── turbo.json            ← Turborepo配置
```

**架构模式**：Monorepo（pnpm + Turborepo），30+packages

**核心设计**：
- **节点化架构**：每个集成=一个节点，统一接口（execute/trigger/webhook）
- **可视化+代码**：拖拽编排+Code节点（JS/Python）
- **AI Agent节点**：LLM Chain/Agent/Memory/VectorStore/Tool原生支持
- **MCP双向**：既是MCP client（调用外部工具），也是MCP server（暴露工作流为工具）
- **Credential管理**：统一的API密钥/OAuth管理

## 核心模块（5个）

1. **Workflow Engine** — 工作流解析+执行引擎（大）
2. **Node系统** — 400+集成节点+统一接口（巨大）
3. **Editor UI** — Vue.js可视化编辑器（大）
4. **AI Agent模块** — LLM/Agent/Memory/Tool（中）
5. **Credential管理** — API密钥+OAuth+加密存储（中）

## 可拆解评估

| 模块 | 可独立抽取 | 难度 | 预估时间 |
|------|-----------|------|----------|
| Webhook触发模式 | ✅ | 简单参考 | 1h |
| Credential加密存储 | ✅ | 需适配 | 3h |
| AI Agent工作流模式 | ✅ | 需适配 | 4h |
| Node统一接口设计 | ✅ | 架构参考 | 2h |

⭐通用代码候选：Credential加密管理（code-base/auth/credential-vault/）
⭐通用代码候选：Webhook触发器模式（code-base/automation/webhook-trigger/）

## 商业价值

- **痛点级别**：致命（一人公司=必须自动化，n8n是最佳开源选择）
- **TAM**：工作流自动化$20B+ / iPaaS $10B+
- **竞品**：Zapier（$1.4B估值）、Make.com、Pipedream、Activepieces
- **可商用度**：⚠️ Sustainable Use License不是传统开源。自用OK，但不能作为竞品SaaS销售
- **差异化窗口**：AI节点+MCP=下一代自动化平台。但n8n Cloud竞争激烈

## 反证（为什么可能不值得用）

- **Fair-code许可**：不是MIT/Apache，限制竞品使用场景
- 系统极其复杂（30+packages），学习曲线陡峭
- 自托管资源消耗大（Node.js+数据库+Redis+Worker）
- n8n Cloud版本功能更完整，开源版可能被功能限制
- 184k⭐中包含大量非活跃star（hype效应）

## 天子点评

一人公司自动化终极武器，AI节点+MCP让工作流即产品。Fair-code许可限制竞品但自用完全OK，直接部署开干。
