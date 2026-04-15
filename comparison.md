# Automation & Web Scraping Tools — Comparison

> Last updated: 2026-04-15

## Overview Matrix

| Project | Stars | Language | License | Type | TEMC | Best For |
|---------|-------|----------|---------|------|------|----------|
| **Puppeteer** | 94k | TypeScript | Apache-2.0 | Browser Automation | 80 | Chrome-specific automation |
| **Playwright** | 86k | TypeScript | Apache-2.0 | Browser Automation | **88** | Modern cross-browser testing & automation |
| **Firecrawl** | ~70k | TypeScript | AGPL-3.0 | AI Web Scraping | **89** | LLM-ready web data extraction |
| **Scrapy** | 61k | Python | BSD-3 | Web Scraping | 80 | Large-scale Python scraping |
| **n8n** | ~60k | TypeScript | Fair-code | Workflow Automation | **85** | Visual workflow & AI agent orchestration |
| **Selenium** | 32k | Java | Apache-2.0 | Browser Automation | 67 | Legacy enterprise testing |
| **Crawlee** | 17k | TypeScript | Apache-2.0 | Web Scraping | 81 | Reliable TypeScript crawling |

## Category Breakdown

### 🌐 Browser Automation
| | Playwright | Puppeteer | Selenium |
|---|-----------|-----------|----------|
| Multi-browser | ✅ Chrome+FF+WebKit | ⚠️ Chrome+FF | ✅ All browsers |
| Auto-wait | ✅ Built-in | ❌ Manual | ❌ Manual |
| TypeScript | ✅ Native | ✅ Native | ⚠️ Bindings |
| Trace/Debug | ✅ Trace Viewer | ❌ | ❌ |
| Distributed | ⚠️ Via sharding | ❌ | ✅ Grid |
| **Verdict** | 🏆 **Modern choice** | Good for Chrome | Legacy |

### 🕷️ Web Scraping
| | Firecrawl | Crawlee | Scrapy |
|---|-----------|---------|--------|
| Language | TypeScript | TypeScript | Python |
| AI-Ready Output | ✅ Markdown/JSON | ❌ | ❌ |
| Anti-Bot | ✅ Built-in | ✅ Built-in | ⚠️ Plugins |
| JS Rendering | ✅ Playwright | ✅ Playwright/Puppeteer | ⚠️ Splash |
| MCP Integration | ✅ | ❌ | ❌ |
| Scale | Cloud API | Self-host | Self-host |
| **Verdict** | 🏆 **For AI pipelines** | Best TS crawler | Best Python crawler |

### ⚡ Workflow Automation
n8n stands alone in this category as the open-source workflow automation platform. Competes with Zapier, Make, and Temporal in different segments.

## Recommendation for Tianzi (TypeScript + Next.js + AI)

1. **Firecrawl** (TEMC 89) — #1 pick. AI-native scraping, TypeScript, MCP integration. Use API for production, reference code for patterns.
2. **Playwright** (TEMC 88) — #2 pick. Browser automation backbone. Testing + scraping. Perfect stack match.
3. **n8n** (TEMC 85) — #3 pick. Workflow automation reference. AI agent orchestration patterns.
4. **Crawlee** (TEMC 81) — Good alternative to Firecrawl for self-hosted TypeScript scraping.
5. **Scrapy/Puppeteer** (TEMC 80) — Learn patterns, but not primary tools for TypeScript stack.
6. **Selenium** (TEMC 67) — Legacy. Skip unless working with enterprise Java.
