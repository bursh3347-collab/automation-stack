# n8n

> Fair-code workflow automation platform — the open alternative to Zapier.

| Metric | Data |
|--------|------|
| GitHub | [n8n-io/n8n](https://github.com/n8n-io/n8n) |
| Stars | ~60,000 |
| Forks | ~12,000 |
| License | Sustainable Use License (fair-code) |
| Language | TypeScript |
| Last Update | 2026-04 (very active) |
| Contributors | 400+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 88 | Visual workflow builder, 400+ integrations, code nodes (JS/Python), AI agent nodes. Self-hostable. TypeScript monorepo. |
| E Ecosystem | 88 | ~60k stars, 400+ community nodes. Growing AI workflow community. Active Discord. Enterprise adoption rising. |
| M Market | 85 | Workflow automation booming with AI. Zapier/Make alternative with self-host option. AI agent orchestration emerging use case. |
| C Combo | 82 | TypeScript but complex monorepo. Architecture patterns valuable. AI workflow nodes = agent orchestration reference. |
| **Overall** | **85** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 85.6 |

## ⚠️ License Note
**Sustainable Use License** (fair-code, not OSI-approved open source). Free to use and self-host. Cannot offer n8n as a competing service. OK for internal automation and learning.

## Core Value
Visual workflow automation with code flexibility. 400+ integrations out of the box. Self-hostable alternative to Zapier/Make. Emerging as AI agent orchestration platform with built-in LLM nodes.

## Architecture Highlights
- **Visual Workflow Editor**: Drag-and-drop node-based workflow builder
- **Node System**: Trigger nodes + Action nodes + Function nodes + AI nodes
- **Credential Management**: Encrypted credential storage with OAuth support
- **Execution Engine**: Queue-based with retry, error handling, sub-workflows
- **AI Agent Framework**: Built-in agent nodes with memory, tools, and chain-of-thought
- **Webhook System**: HTTP triggers for external event-driven automation

## Key Modules
1. **Workflow Engine** (Large) — Execution, queuing, error handling, sub-workflows
2. **Node Ecosystem** (Large) — 400+ integration nodes, custom node SDK
3. **AI Agent Nodes** (Medium) — LLM chains, agents, memory, tools integration
4. **Editor UI** (Large) — Vue.js visual workflow builder
5. **Credential System** (Medium) — Encrypted storage, OAuth flows, sharing

## Extractable Patterns
- **⭐ Universal Code Candidate: Webhook Trigger Pattern** → code-base/api/webhook-handler/
- **⭐ Universal Code Candidate: Credential Encryption Pattern** → code-base/auth/credential-vault/
- Node-based workflow execution engine design
- Visual workflow builder architecture
- AI agent orchestration with tool nodes

## Why This Matters
- Reference architecture for workflow automation SaaS
- AI agent nodes = competitor intelligence for agent frameworks
- Integration patterns for 400+ services
