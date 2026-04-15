# Firecrawl

> The AI-native web scraping engine — turns any URL into LLM-ready markdown with a single API call.

| Metric | Data |
|--------|------|
| GitHub | [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) |
| Stars | 109,388 |
| Forks | 7,005 |
| License | AGPL-3.0 ⚠️ |
| Language | TypeScript |
| Last Update | 2026-04-15 (today) |
| Created | 2024-04-15 (exactly 2 years ago) |
| Topics | ai, crawler, llm, markdown, web-scraping |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 90 | AI-first design, HTML→Markdown conversion, structured extraction, multiple SDKs (Python/JS/Go/Rust). MCP server support. |
| E (Ecosystem) | 88 | 109k stars in 2 years = explosive growth. AI community adoption. LangChain/LlamaIndex integrations. |
| M (Market) | 92 | Perfect timing — every AI app needs web data. LLM-ready output is THE differentiator. MCP support = Agent ecosystem. |
| C (Combination) | 90 | TypeScript, MCP support, direct integration with AI agent stack. Perfect for天子's AI pipeline. |
| **Total** | **90** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Architecture Analysis

```
firecrawl/
├── apps/
│   ├── api/              # Main API server (TypeScript)
│   │   ├── native/       # Native Rust performance module
│   │   └── src/          # Core scraping logic
│   └── js-sdk/           # JavaScript SDK
├── sdks/                 # Multi-language SDKs
│   ├── python/
│   ├── go/
│   └── rust/
└── docs/                 # Documentation
```

**Architecture Pattern**: API-first with native Rust performance layer

**Key Design**: URL Input → Browser Rendering → Content Extraction → Markdown/Structured Output — optimized for LLM consumption.

## Core Modules (5)

| Module | Size | Coupling | Description |
|--------|------|----------|-------------|
| Scraping Engine | Large | High | Browser rendering + content extraction |
| Markdown Converter | Medium | Low | HTML → clean Markdown for LLMs |
| Structured Extraction | Medium | Medium | LLM-powered schema-based extraction |
| Crawl Orchestrator | Large | Medium | Multi-page crawling, sitemap discovery |
| MCP Server | Small | Low | Model Context Protocol integration |

## Extractable Patterns

1. **HTML-to-Markdown for LLMs** → `code-base/ai-integration/html-to-markdown/` ⭐通用代码候选
   - Clean markdown output optimized for token efficiency
   - Removes nav, ads, boilerplate

2. **Structured Extraction Pattern** → LLM + JSON schema = structured data from any page
   - Reusable for any "unstructured → structured" AI pipeline

3. **MCP Server Pattern** → Model Context Protocol server implementation
   - `code-base/ai-integration/mcp-server/` ⭐通用代码候选

4. **Crawl Orchestration** → Sitemap discovery, depth control, rate limiting

## Disassembly Assessment

| Module | Extractable? | Difficulty | Time |
|--------|-------------|------------|------|
| HTML-to-Markdown | ⚠️ AGPL | Need clean-room rewrite | 6h |
| Structured extraction | ⚠️ AGPL | Concept replicable | 4h |
| MCP server pattern | ⚠️ AGPL | Pattern study, own impl | 3h |
| Crawl orchestrator | ⚠️ AGPL | Complex, reference only | 8h |

**⚠️ License Warning**: AGPL-3.0 means derivative works must be open-sourced. For commercial use, either:
1. Use the hosted API (paid)
2. Study patterns and clean-room rewrite in TypeScript
3. Keep self-hosted deployment fully open-source

## Business Value

- **Pain Point**: Every AI app needs clean web data (Critical)
- **Target Users**: AI developers, RAG pipeline builders, data teams
- **Competitors**: Crawlee (library), Apify (platform), Jina Reader (API)
- **Commercialization**: Already commercial (API pricing: $0→$500+/mo)
- **Differentiation Window**: MCP integration makes it the default for AI agents

## Combination Potential

- **Product**: AI Data Pipeline — Firecrawl extraction → RAG pipeline → SaaS
- **Sell to**: Companies building AI-powered products needing web data
- **Price**: Usage-based, $29-199/mo
- **Combo with Playwright**: Firecrawl for content extraction, Playwright for interactive automation
- **Combo with n8n**: Firecrawl as data source in n8n workflow automation

## Anti-fragility Assessment

- **Bus Factor**: Mendable/Firecrawl team (10+ contributors) — Medium risk
- **Dependency Safety**: Rust native module for performance
- **CI/CD**: Active GitHub Actions
- **License**: AGPL-3.0 ⚠️ copyleft — commercial use requires caution

## Why It Might NOT Be Worth Using

- AGPL-3.0 license severely limits commercial derivative works
- Hosted API pricing can get expensive at scale
- 2 years old — longevity not yet proven
- Depends on LLM APIs for structured extraction (cost adds up)
- Competitors like Jina Reader offer similar functionality
- Self-hosted requires significant infrastructure
