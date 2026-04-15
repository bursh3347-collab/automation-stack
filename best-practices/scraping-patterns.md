# 🕷️ Web Scraping 最佳实践

> 从7个TOP项目中提炼的爬虫设计模式和反模式

## 1. 请求队列模式（来自 Crawlee）

**问题**：大规模爬虫需要管理URL发现、去重、重试、优先级

**最佳实践**：
```typescript
// 统一的请求队列接口
interface RequestQueue {
  addRequest(url: string, options?: { priority?: number }): Promise<void>;
  fetchNextRequest(): Promise<Request | null>;
  markRequestHandled(request: Request): Promise<void>;
  reclaimRequest(request: Request): Promise<void>; // 失败重试
}
```

**关键设计**：
- 去重通过URL指纹（normalize后hash）
- 优先级队列（BFS vs DFS可配置）
- 失败请求自动回收（指数退避重试）
- 持久化存储（断点续爬）

**来源**：Crawlee `packages/core/` RequestQueue实现

## 2. 中间件链模式（来自 Scrapy）

**问题**：需要在请求/响应生命周期中灵活插入处理逻辑

**最佳实践**：
```typescript
// 中间件接口
interface Middleware {
  processRequest?(request: Request): Promise<Request | null>;
  processResponse?(response: Response): Promise<Response | null>;
  processError?(error: Error): Promise<void>;
  priority: number; // 执行顺序
}

// 中间件管道
class MiddlewarePipeline {
  private middlewares: Middleware[] = [];
  
  async processRequest(req: Request): Promise<Request | null> {
    let current = req;
    for (const mw of this.middlewares.sort((a,b) => a.priority - b.priority)) {
      const result = await mw.processRequest?.(current);
      if (!result) return null; // 中间件可以终止请求
      current = result;
    }
    return current;
  }
}
```

**典型中间件**：代理轮换、UA随机化、限速、Cookie管理、重试

**来源**：Scrapy `downloadermiddlewares/` 架构

## 3. 多引擎统一接口（来自 Crawlee）

**问题**：不同页面需要不同渲染引擎（静态HTML用HTTP，动态页用浏览器）

**最佳实践**：
```typescript
// 统一的爬虫处理器接口
interface CrawlerHandler {
  requestHandler(context: CrawlingContext): Promise<void>;
}

// 根据需求选择引擎
const crawler = new PlaywrightCrawler({...}); // JS渲染页面
const crawler = new CheerioCrawler({...});    // 静态HTML
const crawler = new HttpCrawler({...});        // API调用
// 所有引擎共享相同的 requestHandler API
```

**关键**：Handler代码不需要关心底层引擎，可以无缝切换

**来源**：Crawlee多引擎架构

## 4. HTML→AI-ready数据转换（来自 Firecrawl）

**问题**：LLM/RAG需要干净的文本数据，HTML噪音太多

**最佳实践**：
1. 移除导航栏、侧边栏、页脚、广告
2. 保留语义结构（标题层级、列表、表格）
3. 转换为Markdown（LLM最友好的格式）
4. 可选：用LLM提取结构化数据（JSON Schema定义）

**来源**：Firecrawl HTML→Markdown引擎

## 5. 代理轮换+健康检查（来自 Crawlee + Scrapy）

**最佳实践**：
```typescript
class ProxyRotator {
  private proxies: Proxy[] = [];
  private healthMap: Map<string, ProxyHealth> = new Map();
  
  getProxy(): Proxy {
    // 优先选择健康度高的代理
    return this.proxies
      .filter(p => this.healthMap.get(p.url)?.isHealthy)
      .sort((a, b) => this.getScore(b) - this.getScore(a))[0];
  }
  
  reportResult(proxy: Proxy, success: boolean) {
    // 更新健康度
    const health = this.healthMap.get(proxy.url)!;
    health.successRate = (health.successRate * 0.9) + (success ? 0.1 : 0);
    if (health.successRate < 0.3) health.isHealthy = false;
  }
}
```

**来源**：Crawlee `proxy-rotation/` + Scrapy中间件

## 反模式（避免）

| 反模式 | 问题 | 正确做法 |
|--------|------|----------|
| 硬编码sleep等待 | 不可靠+浪费时间 | 用auto-wait或元素检测 |
| 不做去重 | 重复爬取浪费资源 | URL指纹去重 |
| 单一UA | 容易被封 | UA池随机轮换 |
| 无限速 | 被IP封禁 | 自适应限速 |
| 不处理失败 | 数据丢失 | 指数退避重试 |
| 全用浏览器 | 资源浪费 | 静态页用HTTP/Cheerio |

---
*提炼自 Scrapy/Playwright/Firecrawl/Crawlee 四大项目的生产实践*
