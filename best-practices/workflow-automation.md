# Workflow Automation Best Practices

> Patterns extracted from n8n, Temporal, and modern automation platforms.

## Pattern 1: Event-Driven Workflow Architecture (from n8n)

```
Trigger → Process → Decision → Action → Callback
   ↑                                      |
   └──────── Error Handler ←──────────────┘
```

**Trigger types**:
- **Webhook**: HTTP POST triggers workflow (most flexible)
- **Schedule**: Cron-based recurring execution
- **Polling**: Check external service periodically
- **Event**: Message queue / pub-sub events

## Pattern 2: Idempotent Workflow Steps

Every step should be safely re-runnable:

```typescript
async function processOrder(orderId: string) {
  // Check if already processed (idempotency key)
  const existing = await db.getProcessingResult(orderId);
  if (existing) return existing;
  
  // Process
  const result = await doWork(orderId);
  
  // Store result with idempotency key
  await db.saveProcessingResult(orderId, result);
  return result;
}
```

## Pattern 3: Error Handling Strategy

```
Step fails?
├── Transient error (network, rate limit) → Retry with backoff (max 3)
├── Data error (invalid input) → Skip + log + notify
├── System error (service down) → Pause workflow + alert
└── Unknown error → Retry once → if fails → human review queue
```

## Pattern 4: Credential Management (from n8n)

- **Encrypt at rest**: AES-256 for stored credentials
- **Encrypt in transit**: TLS for all API calls
- **Scope access**: Credentials tied to specific workflows/users
- **Rotate regularly**: Automated rotation for API keys
- **Never log**: Redact credentials in all logs

## Pattern 5: Webhook Security

```typescript
function verifyWebhook(req: Request, secret: string): boolean {
  const signature = req.headers['x-signature'];
  const computed = crypto
    .createHmac('sha256', secret)
    .update(req.body)
    .digest('hex');
  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(computed)
  );
}
```

## Pattern 6: AI Agent Workflow Integration (from n8n AI nodes)

Modern workflow automation increasingly integrates AI agents:

1. **LLM Decision Node**: Use AI to make routing decisions in workflows
2. **Tool Calling**: Workflow steps as tools available to AI agents
3. **Memory Integration**: Persist conversation context across workflow runs
4. **Human-in-the-Loop**: AI processes → human review → AI continues

## Automation Anti-Patterns

1. **No error handling** — Silent failures corrupt data
2. **Tight coupling** — Steps directly call each other instead of using events
3. **No observability** — Can't debug failed workflows
4. **Hardcoded credentials** — Security nightmare
5. **No rate limiting** — Overwhelm downstream services
6. **No idempotency** — Duplicate processing on retries
