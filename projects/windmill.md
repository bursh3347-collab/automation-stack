# Windmill

> Open-source developer platform to turn scripts into webhooks, workflows and UIs. Fastest workflow engine (13x vs Airflow).

| Metric | Data |
|--------|------|
| GitHub | [windmill-labs/windmill](https://github.com/windmill-labs/windmill) |
| Stars | 16,245 |
| License | AGPLv3 (EE features proprietary) |
| Language | Rust (backend) + Svelte (frontend) + TypeScript/Python/Go (scripts) |
| Last Updated | 2026-04-16 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technical | 90 | Rust backend = blazing fast (13x Airflow). Multi-language script support (TS/Python/Go/Bash/SQL/GraphQL). PostgreSQL-native. Auto-generated UIs from scripts. |
| E Ecosystem | 75 | 16.2k stars. Niche but passionate community. Windmill Hub for shared scripts. Less mainstream than n8n/Activepieces. |
| M Market | 82 | Internal tool + workflow automation market is huge. Alternative to Retool (no-code) + Temporal (workflow engine). Developer-first positioning. |
| C Combination | 78 | Svelte frontend doesn't match base stack. But TypeScript script support is excellent. Self-hostable. Docker compose ready. |
| **Composite** | **82.0** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Windmill is a **developer-first** platform that bridges the gap between scripts and production:
- Write a script (TS/Python/Go) → instantly get a webhook, scheduled job, or UI
- Auto-generate forms and dashboards from function signatures
- Built-in approval flows, error handling, retries
- 13x faster than Apache Airflow (Rust backend)

## Architecture Highlights

- **Backend**: Rust (extremely fast, compiled binary)
- **Frontend**: Svelte + Tailwind
- **Database**: PostgreSQL (stores everything — scripts, schedules, results, audit logs)
- **Workers**: Distributed execution with language-specific runtimes
- **Script Languages**: TypeScript, Python, Go, Bash, SQL, GraphQL, PowerShell
- **MCP**: `.mcp.json` present — MCP-aware
- **AI**: `.agents` and `.claude` directories — AI coding agent support

## Key Modules for Extraction

1. **Script-to-API pattern** — auto-generate REST endpoints from function signatures
2. **Auto-generated UI** — derive forms from TypeScript/Python types
3. **Approval flows** — human-in-the-loop workflow patterns
4. **Distributed worker architecture** — Rust-based job execution
5. **Audit logging** — compliance-ready execution tracking

## Solo Dev Verdict

🟡 **Excellent for internal tools and data pipelines, but not for customer-facing SaaS**. If you need to build internal dashboards, cron jobs, data pipelines, or script-based automation, Windmill is superior to n8n/Activepieces in raw performance. The Rust backend means it can handle heavy workloads. **Caveat**: AGPL license limits commercial use. Svelte frontend is a mismatch with base stack. Best used as infrastructure, not as a product to embed.

---
*Analyzed: 2026-04-16 | TEMC scoring by 天工·内阁首辅*
