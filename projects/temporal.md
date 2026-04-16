# Temporal

> Durable execution platform — build invincible applications that never fail.

| Metric | Data |
|--------|------|
| GitHub | [temporalio/temporal](https://github.com/temporalio/temporal) |
| Stars | 19,631 |
| License | MIT |
| Language | Go (server) + TypeScript/Python/Java/Go SDKs |
| Last Updated | 2026-04-16 |
| Funding | $100M+ raised (Series B) |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technical | 92 | Best-in-class durable execution. Automatic retries, timeouts, heartbeats. Event sourcing architecture. Multi-language SDKs. Production-proven at Uber/Netflix/Snap scale. |
| E Ecosystem | 82 | 19.6k stars. Strong enterprise adoption (Uber, Netflix, Snap, Stripe). TypeScript SDK excellent. Temporal Cloud available. |
| M Market | 85 | Workflow orchestration market growing fast. Temporal = gold standard for durable execution. AI agent workflows increasingly need this reliability. |
| C Combination | 70 | Go server = operational overhead for solo dev. TypeScript SDK is great for writing workflows. But running Temporal server requires infrastructure (Cassandra/MySQL/Postgres + ElasticSearch). Temporal Cloud solves this ($200+/mo). |
| **Composite** | **82.4** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Temporal solves the hardest problem in distributed systems: **what happens when things fail?**
- Workflows survive server crashes, network failures, and process restarts
- Automatic retry with exponential backoff
- Long-running workflows (days/weeks/months)
- Built-in saga pattern for distributed transactions
- Event sourcing = full audit trail of every execution

## Architecture Highlights

- **Server**: Go, gRPC-based, horizontally scalable
- **Persistence**: Cassandra, MySQL, or PostgreSQL
- **Search**: Elasticsearch for workflow visibility
- **SDKs**: TypeScript, Python, Java, Go, .NET, PHP
- **Workflow model**: Deterministic execution + activities (side effects)
- **AI-ready**: `.claude` and `.cursor` directories = actively using AI coding agents

## Key Patterns for Extraction

1. **Durable execution** — workflow-as-code that survives failures
2. **Activity pattern** — separating business logic (deterministic) from side effects (non-deterministic)
3. **Saga pattern** — distributed transaction compensation
4. **Signal/Query** — external interaction with running workflows
5. **Child workflows** — workflow composition and decomposition

## TypeScript SDK Example

```typescript
// A workflow that processes an order with automatic retry
async function orderWorkflow(orderId: string) {
  await validateOrder(orderId);       // Activity: retries on failure
  await chargePayment(orderId);       // Activity: retries on failure
  await fulfillOrder(orderId);        // Activity: retries on failure
  await sendConfirmation(orderId);    // Activity: retries on failure
}
```

## Solo Dev Verdict

🟡 **Overkill for MVP, essential at scale**. For a solo dev building an MVP, Temporal's operational overhead (server + persistence + search) is too much. Use Inngest or simple queue-based patterns instead. **BUT**: once your SaaS hits production with critical workflows (payments, data pipelines, multi-step AI agents), Temporal becomes necessary. Plan to migrate to Temporal when you have paying customers. The TypeScript SDK is excellent. Study the durable execution pattern NOW — it's the foundation of reliable AI agent systems.

---
*Analyzed: 2026-04-16 | TEMC scoring by 天工·内阁首辅*
