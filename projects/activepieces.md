# Activepieces

> AI Agents & MCPs & AI Workflow Automation — the open-source Zapier/n8n alternative with 400+ MCP servers.

| Metric | Data |
|--------|------|
| GitHub | [activepieces/activepieces](https://github.com/activepieces/activepieces) |
| Stars | 21,728 |
| License | MIT (core) + Proprietary (EE) |
| Language | TypeScript |
| Last Updated | 2026-04-16 |
| Version | v0.81.3 |
| Package Manager | Bun |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technical | 85 | TypeScript monorepo (Turborepo). Bun runtime. React frontend. Fastify backend. AI SDK (Anthropic, OpenAI, Google, Replicate). MCP native. Tiptap editor. |
| E Ecosystem | 80 | 21.7k stars, growing fast. 400+ integrations/MCP servers. Active community. But smaller than n8n (184k stars). |
| M Market | 88 | Automation market booming. AI Agent + MCP positioning is 2026's hottest narrative. Zapier/Make.com are expensive → open-source demand is massive. |
| C Combination | 85 | TypeScript = perfect match. React + Radix UI + Tailwind. AI SDK integration. Self-hostable. Can be embedded into SaaS products. |
| **Composite** | **85.1** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Activepieces positions itself at the intersection of **workflow automation + AI Agents + MCP**:
- 400+ pre-built integrations (pieces)
- Native AI agent support with MCP servers
- Visual workflow builder
- Self-hostable (Docker)
- MIT license for core = commercial friendly

## Architecture Highlights

- **Monorepo**: Turborepo + Bun
- **Frontend**: React + Radix UI + TanStack Query + TipTap editor + XY Flow (visual builder)
- **Backend**: Fastify + TypeBox validation
- **AI**: Vercel AI SDK + multi-provider (Anthropic/OpenAI/Google/Replicate)
- **MCP**: `@modelcontextprotocol/sdk` + `@ai-sdk/mcp` native integration
- **Queue**: Bull (Redis-based job queue)
- **Database**: PostgreSQL (via TypeORM or direct)
- **Runtime**: Sandboxed engine for running user workflows

## Key Modules for Extraction

1. **Piece (integration) framework** — modular plugin system for adding integrations
2. **Visual workflow builder** — XY Flow-based drag-and-drop editor
3. **AI Agent execution** — MCP-native agent runtime
4. **Sandboxed execution engine** — secure user code execution
5. **Webhook handling** — event-driven trigger system

## Comparison with n8n

| Feature | Activepieces | n8n |
|---------|-------------|-----|
| License | MIT (core) | Fair-code (no competing SaaS) |
| AI/MCP | ✅ Native, 400+ MCP | ✅ AI nodes |
| Language | TypeScript | TypeScript |
| Stars | 21.7k | 184k |
| Self-host | ✅ Docker | ✅ Docker |
| Embed in SaaS | ✅ MIT allows | ⚠️ License restricts |

## Solo Dev Verdict

🟢 **Best open-source automation platform for embedding into your own SaaS**. The MIT license is the killer differentiator vs n8n. If you're building a SaaS product that needs workflow automation features (like a CRM with automated follow-ups, or a project management tool with triggers), Activepieces can be embedded directly. The MCP integration means your SaaS can offer AI agent capabilities out of the box. Main risk: smaller community than n8n.

---
*Analyzed: 2026-04-16 | TEMC scoring by 天工·内阁首辅*
