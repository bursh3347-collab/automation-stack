# Workflow Automation Best Practices

> Patterns extracted from n8n (184k⭐), Crawlee (23k⭐), and Scrapy (61k⭐) pipeline architectures.

## 1. Node/Plugin Architecture (from n8n)

The most powerful pattern for extensible automation:

```typescript
// Pattern: Self-describing automation node
interface AutomationNode {
  name: string;
  description: string;
  inputs: NodeInput[];        // What this node accepts
  outputs: NodeOutput[];      // What this node produces
  credentials?: Credential[]; // Required auth
  execute(input: any): Promise<any>;
}

// Each node is:
// 1. Self-contained (no external dependencies)
// 2. Declarative (inputs/outputs/credentials declared upfront)
// 3. Composable (chain nodes into workflows)
```

**From n8n**: Every integration is a node. 400+ nodes follow the same pattern. This makes it trivial to add new integrations.

## 2. DAG Execution Engine (from n8n)

```
[Trigger] → [Node A] → [Branch]
                          ├── [Node B] → [Node D] → [Output]
                          └── [Node C] → [Output]
```

Key principles:
- **Topological sort**: Execute nodes in dependency order
- **Parallel branches**: Independent paths execute concurrently
- **Error propagation**: Errors bubble up with context
- **Retry per node**: Each node has its own retry policy

## 3. Credential Management (from n8n)

```typescript
// Pattern: Encrypted credential storage
interface CredentialStore {
  // Store encrypted, retrieve decrypted
  save(name: string, data: Record<string, string>): Promise<void>;
  get(name: string): Promise<Record<string, string>>;
  // AES-256-CBC encryption at rest
  // Decrypt only at execution time
  // Never log credential values
}
```

**Critical rule**: Credentials are encrypted at rest, decrypted only during node execution, never logged or exposed in error messages.

## 4. Trigger Patterns (from n8n + general)

| Trigger Type | Pattern | Use Case |
|-------------|---------|----------|
| **Webhook** | HTTP POST → start workflow | External event (Stripe, GitHub) |
| **Schedule** | Cron expression → start | Daily reports, periodic checks |
| **Polling** | Check source every N minutes | APIs without webhooks |
| **Event** | Message queue → start | Real-time processing |
| **Manual** | User click → start | Testing, one-off tasks |

## 5. Error Handling Strategies

```typescript
// Pattern: Multi-level error handling
class WorkflowExecutor {
  async executeNode(node: Node, input: any) {
    try {
      return await node.execute(input);
    } catch (error) {
      // Level 1: Node-level retry
      if (node.retryPolicy && attempt < node.maxRetries) {
        return await this.retryNode(node, input, attempt + 1);
      }
      // Level 2: Error output path
      if (node.errorOutput) {
        return await this.executeNode(node.errorOutput, { error, input });
      }
      // Level 3: Workflow-level error handler
      return await this.handleWorkflowError(error, node);
    }
  }
}
```

## 6. Idempotency (Critical for Automation)

```typescript
// Pattern: Every automation step should be idempotent
// Running it twice produces the same result

// ❌ Bad: Creates duplicate entries
await db.insert({ name: 'John', email: 'john@example.com' });

// ✅ Good: Upsert with unique key
await db.upsert(
  { email: 'john@example.com' },
  { name: 'John', email: 'john@example.com' }
);
```

**Why**: Automation workflows WILL fail mid-execution. When you retry, you don't want duplicate records, double charges, or repeated notifications.

## 7. Observability (from n8n + production patterns)

```typescript
// Pattern: Every workflow execution should be traceable
interface ExecutionLog {
  workflowId: string;
  executionId: string;  // Unique per run
  startedAt: Date;
  completedAt: Date;
  status: 'success' | 'error' | 'timeout';
  nodes: {
    nodeId: string;
    input: any;         // Sanitized (no credentials)
    output: any;
    duration: number;
    error?: string;
  }[];
}
```

## Summary: Automation Architecture Principles

1. **Everything is a node** — Self-contained, composable units
2. **Fail gracefully** — Multi-level error handling + retries
3. **Be idempotent** — Safe to retry any step
4. **Encrypt credentials** — At rest and in transit
5. **Log everything** — But sanitize sensitive data
6. **Design for retry** — Assume any step can fail
7. **Separate triggers from logic** — Many triggers, same workflow
