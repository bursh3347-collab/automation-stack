# Inngest

> The leading workflow orchestration platform — run stateful step functions and AI workflows on serverless.

| Metric | Data |
|--------|------|
| GitHub | [inngest/inngest](https://github.com/inngest/inngest) |
| Stars | 5,213 |
| License | Server Source License (BSL-like) |
| Language | Go (server) + TypeScript SDK |
| Last Updated | 2026-04-16 |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Technical | 88 | Elegant event-driven architecture. Serverless-native (works with Vercel/Netlify/Cloudflare). TypeScript SDK with step functions. Built-in retry, debounce, rate limiting. |
| E Ecosystem | 68 | 5.2k stars — smallest in this comparison. But growing fast. Inngest Cloud has strong adoption. Used by Documenso, Resend, and others. |
| M Market | 85 | Background job + event-driven workflow market is underserved. Inngest fills the gap between simple queues and full Temporal. Perfect for serverless environments. |
| C Combination | 85 | **Excellent base stack fit**: TypeScript SDK, works with Next.js + Vercel natively. Event-driven = perfect for SaaS (user actions → background workflows). Zero infrastructure for solo dev (Inngest Cloud free tier). |
| **Composite** | **82.3** | T×0.25 + E×0.20 + M×0.25 + C×0.25 |

## Core Value

Inngest is **Temporal for serverless** — durable execution without the infrastructure:
- Event-driven: send events, Inngest runs the right functions
- Step functions: break complex workflows into reliable steps
- Automatic retry with backoff
- Concurrency control + rate limiting + debouncing
- Works on Vercel, Netlify, Cloudflare Workers, AWS Lambda
- **Zero infrastructure**: no Redis, no queues, no workers to manage

## Architecture Highlights

- **Server**: Go-based event processing engine
- **SDK**: TypeScript-first (also Python, Go)
- **Execution model**: Event → Function → Steps (each step is individually retryable)
- **Deployment**: SDK runs inside YOUR app (Next.js API route), Inngest Cloud orchestrates
- **Local dev**: `inngest dev` for local testing with UI

## TypeScript SDK Example

```typescript
import { inngest } from './client';

export const processOrder = inngest.createFunction(
  { id: 'process-order', retries: 3 },
  { event: 'order/created' },
  async ({ event, step }) => {
    const validated = await step.run('validate', () =>
      validateOrder(event.data.orderId)
    );
    await step.run('charge', () =>
      chargePayment(event.data.orderId)
    );
    await step.run('fulfill', () =>
      fulfillOrder(event.data.orderId)
    );
    await step.run('notify', () =>
      sendConfirmation(event.data.orderId)
    );
  }
);
```

## Inngest vs Temporal vs BullMQ

| Feature | Inngest | Temporal | BullMQ |
|---------|---------|----------|--------|
| Infrastructure | Zero (Cloud) | Heavy (server+DB) | Redis |
| TypeScript SDK | ✅ Excellent | ✅ Good | ✅ Good |
| Serverless | ✅ Native | ❌ Needs server | ❌ Needs Redis |
| Durable execution | ✅ Steps | ✅ Full | ❌ |
| Free tier | ✅ 5k events/mo | ❌ | ✅ (self-host) |
| Learning curve | Low | High | Low |
| Best for | SaaS background jobs | Mission-critical workflows | Simple queues |

## Solo Dev Verdict

🟢🟢 **THE background job solution for solo dev SaaS in 2026**. Inngest eliminates the need to set up Redis, manage workers, or run Temporal infrastructure. Just add the SDK to your Next.js app, deploy to Vercel, and you have durable event-driven workflows. **Used by Documenso** (analyzed in fullstack-saas-stack) for their signing workflows. Free tier (5k events/month) is enough for early-stage SaaS. Upgrade when you have revenue. This is a must-have in the solo dev SaaS toolkit alongside Supabase + Vercel.

---
*Analyzed: 2026-04-16 | TEMC scoring by 天工·内阁首辅*
