# n8n

> The open-source workflow automation platform with native AI — 400+ integrations, visual builder, self-hostable.

| Metric | Data |
|--------|------|
| GitHub | [n8n-io/n8n](https://github.com/n8n-io/n8n) |
| Stars | 184,154 |
| Forks | 56,818 |
| License | Sustainable Use License (fair-code) ⚠️ |
| Language | TypeScript |
| Last Update | 2026-04-15 (today) |
| Version | v2.17.0 |
| Topics | ai, automation, mcp, workflow, low-code |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 88 | TypeScript monorepo (turbo/pnpm), AI-native nodes, MCP client+server, 400+ integrations. Production-grade. |
| E (Ecosystem) | 92 | 184k stars = top 50 GitHub globally. 56k forks. Enterprise adoption. Active Discord community. |
| M (Market) | 85 | Workflow automation market booming with AI. Competes with Zapier/Make but open-source + AI-native. |
| C (Combination) | 82 | TypeScript ✅, MCP ✅, but fair-code license limits commercial redistribution. Best as infrastructure, not product base. |
| **Total** | **86** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
n8n-monorepo/
├── packages/
│   ├── cli/              # n8n CLI + main server
│   ├── core/             # Core execution engine
│   ├── workflow/          # Workflow data structures
│   ├── nodes-base/       # 400+ built-in integrations
│   ├── nodes-langchain/  # AI/LangChain nodes
│   ├── editor-ui/        # Vue.js visual editor
│   ├── design-system/    # UI component library
│   ├── @n8n/task-runner/  # Isolated code execution
│   └── @n8n/computer-use/ # Computer use capability
├── scripts/              # Build/deploy scripts
└── docker/               # Docker configurations
```

**Architecture Pattern**: Monorepo with turbo build, pnpm workspaces

**Key Design**: Visual Editor → Workflow Engine → Node Execution → Credential Management. Each node is a self-contained integration.

## Core Modules (5)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| Workflow Engine | Large | High | Execution, branching, error handling |
| Node System | Large | Low | 400+ self-contained integration nodes |
| Editor UI | Large | Medium | Vue.js visual workflow builder |
| AI Nodes | Medium | Medium | LangChain, MCP client/server |
| Credential Manager | Medium | Medium | Encrypted credential storage |

## Extractable Patterns

1. **Node Plugin Architecture** → `code-base/workflow/plugin-system/` ⭐通用代码候选
   - Self-contained integration pattern: input → process → output
   - Each node declares its properties, credentials, execution logic

2. **Visual Workflow Pattern** → Graph-based execution with branching
   - DAG execution engine reusable for any pipeline system

3. **Credential Encryption** → AES-256 encrypted credential storage
   - `code-base/auth/credential-encryption/` ⭐通用代码候选

4. **MCP Integration** → Both client and server MCP support
   - Pattern for making any app MCP-compatible

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| Node plugin pattern | ✅ Yes | Concept extraction | 2h |
| DAG execution engine | ⚠️ Partial | Complex, study pattern | 6h |
| Credential encryption | ✅ Yes | Simple adaptation | 2h |
| MCP client/server | ⚠️ License | Fair-code limits | 4h |
| Visual editor | ❌ No | Too coupled, Vue.js | N/A |

**⚠️ License Warning**: Sustainable Use License (fair-code) — you can self-host and modify, but cannot compete with n8n commercially. Fine for internal use or as infrastructure.

## Business Value

- **Pain Point**: Connecting AI with business workflows (Critical for一人公司)
- **Target Users**: Solo founders, small teams, enterprises
- **Competitors**: Zapier ($29+/mo), Make ($9+/mo), Activepieces (open-source)
- **Commercialization**: Use as backend infrastructure for automation SaaS
- **Differentiation Window**: AI-native workflows — most automation tools bolt AI on; n8n is AI-native

## Combination Potential

- **Product**: AI Automation Agency — n8n workflows + custom AI nodes = client solutions
- **Sell to**: SMBs needing AI-powered business automation
- **Price**: $99-499/mo per automation suite
- **Combo with Firecrawl**: n8n workflow triggers Firecrawl for data → AI processing → action
- **Combo with Playwright**: n8n orchestrates browser automation tasks

## Anti-fragility Assessment

- **Bus Factor**: n8n GmbH company (50+ employees) — Low risk ✅
- **Dependency Safety**: Self-contained, well-managed monorepo
- **CI/CD**: Turbo build, comprehensive CI, Docker support
- **License**: Sustainable Use License ⚠️ — can't compete with n8n

## Why It Might NOT Be Worth Using

- Fair-code license prevents building a competing automation platform
- Resource-heavy for self-hosting (Node.js + database + Redis)
- 184k stars means EVERYONE knows about it — hard to differentiate
- Complex codebase — contributing or extending requires deep knowledge
- Visual editor creates vendor lock-in for workflow definitions
