# ⚙️ Workflow Automation 最佳实践

> 从n8n和自动化项目中提炼的工作流设计模式

## 1. 节点化架构（来自 n8n）

**问题**：需要灵活组合不同服务/API的自动化流程

**最佳实践**：
```typescript
// 统一的节点接口
interface WorkflowNode {
  execute(input: NodeInput): Promise<NodeOutput>;
  trigger?(webhook: WebhookData): Promise<NodeOutput>; // 触发器节点
  
  // 元数据
  name: string;
  description: string;
  inputs: ParameterSchema[];
  outputs: ParameterSchema[];
  credentials?: CredentialSchema[]; // 需要的凭证
}

// 工作流定义
interface Workflow {
  nodes: WorkflowNode[];
  connections: Connection[]; // 节点间数据流
  settings: WorkflowSettings;
}
```

**关键设计**：每个节点独立、可复用、可测试。节点间通过数据流连接。

**来源**：n8n `packages/workflow/` + `packages/nodes-base/`

## 2. Webhook触发器模式（来自 n8n）

**最佳实践**：
```typescript
// 通用Webhook处理器
class WebhookHandler {
  async handleIncoming(req: Request): Promise<void> {
    // 1. 验证签名（HMAC/API Key）
    this.verifySignature(req);
    
    // 2. 解析payload
    const payload = this.parsePayload(req);
    
    // 3. 匹配工作流
    const workflow = this.findWorkflow(req.path);
    
    // 4. 触发执行
    await this.executeWorkflow(workflow, payload);
    
    // 5. 返回响应（同步/异步可选）
  }
}
```

**来源**：n8n `packages/cli/` webhook处理

## 3. 凭证安全管理（来自 n8n）

**最佳实践**：
- API密钥加密存储（AES-256 + 环境变量密钥）
- OAuth token自动刷新
- 凭证与工作流分离（引用而非内嵌）
- 最小权限原则

**来源**：n8n Credential管理系统

## 4. 错误处理与重试（通用）

**最佳实践**：
```typescript
class RetryHandler {
  async executeWithRetry<T>(
    fn: () => Promise<T>,
    options: { maxRetries: number; backoff: 'exponential' | 'linear' }
  ): Promise<T> {
    for (let i = 0; i <= options.maxRetries; i++) {
      try {
        return await fn();
      } catch (error) {
        if (i === options.maxRetries) throw error;
        const delay = options.backoff === 'exponential' 
          ? Math.pow(2, i) * 1000 
          : i * 1000;
        await new Promise(r => setTimeout(r, delay));
      }
    }
    throw new Error('Unreachable');
  }
}
```

## 5. 一人公司自动化优先级

基于n8n + 天子时间约束（每天4小时），推荐自动化优先级：

| 优先级 | 自动化类型 | ROI | 推荐工具 |
|--------|-----------|-----|----------|
| P0 | 数据采集→AI处理 | 🔥 极高 | Firecrawl + n8n |
| P0 | 监控告警 | 🔥 极高 | n8n webhook |
| P1 | 内容发布流水线 | 📈 高 | n8n + API |
| P1 | 客户通知 | 📈 高 | n8n + Email/Slack |
| P2 | 报表生成 | 📊 中 | n8n + Playwright截图 |
| P3 | 竞品监控 | 📊 中 | Crawlee + n8n |

---
*提炼自 n8n/Playwright/Firecrawl 的生产实践，面向一人公司场景优化*
