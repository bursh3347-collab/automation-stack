# Firecrawl

> AI-powered web scraping — turn any website into LLM-ready markdown or structured data.

| Metric | Data |
|--------|------|
| GitHub | [mendableai/firecrawl](https://github.com/mendableai/firecrawl) |
| Stars | ~70,000 |
| Forks | ~7,000 |
| License | AGPL-3.0 |
| Language | TypeScript |
| Last Update | 2026-04 (active) |
| Contributors | 200+ |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T Tech | 88 | LLM-optimized output (markdown/structured). JavaScript rendering, anti-bot handling. TypeScript + Python SDKs. Cloud API + self-host. |
| E Ecosystem | 85 | ~70k stars, rapid growth. MCP integration. Strong AI/LLM community adoption. Mendable (YC) backed. |
| M Market | 90 | Perfect timing — every AI app needs web data. LLM-ready scraping is the hottest niche. API-first model = SaaS revenue. |
| C Combo | 90 | TypeScript native. Direct RAG/Agent pipeline integration. Pairs with Supabase vector store. MCP server available. |
| **Overall** | **89** | T×0.25 + E×0.20 + M×0.30 + C×0.25 = 88.5 |

## ⚠️ License Warning
**AGPL-3.0** — Derivative works must be open-sourced. Self-hosting OK for internal use. Building a competing SaaS on top requires careful legal review. Use the paid API for commercial projects, or reference patterns for TypeScript rewrites.

## Core Value
Bridge between raw web and AI. Converts any webpage into clean markdown or structured JSON that LLMs can directly consume. Handles JavaScript rendering, anti-bot, and content extraction automatically.

## Architecture Highlights
- **Scrape → Clean → Structure Pipeline**: Raw HTML → content extraction → markdown/JSON output
- **JavaScript Rendering**: Playwright-based for dynamic content
- **Anti-Bot Layer**: Proxy rotation, browser fingerprinting, CAPTCHA handling
- **MCP Server**: Direct integration with AI agents as a tool
- **Batch & Crawl Modes**: Single page, site crawl, or batch URL processing
- **LLM Extraction**: Use LLM to extract structured data from pages with schema definition

## Key Modules
1. **Content Extractor** (Large) — HTML to clean markdown/text conversion
2. **Crawler Engine** (Large) — Site-wide crawling with depth/scope controls
3. **JS Renderer** (Medium) — Playwright-based dynamic content rendering
4. **API Layer** (Medium) — REST API with rate limiting, webhooks, async jobs
5. **MCP Server** (Small) — Model Context Protocol integration for AI agents

## Extractable Patterns
- **⭐ Universal Code Candidate: HTML-to-Markdown Pipeline** → code-base/ai-integration/web-to-llm/
- **⭐ Universal Code Candidate: Batch URL Processing Queue** → code-base/api/job-queue/
- LLM-based structured data extraction pattern
- MCP tool server implementation pattern

## Why #1 Priority for Tianzi
- Direct integration with RAG pipelines and AI agents
- TypeScript native = perfect stack match
- MCP server = plug into any Agent framework
- Revenue model reference: API pricing tiers
