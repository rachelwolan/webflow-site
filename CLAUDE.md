# Webflow Site Companion

## Project Overview
Companion project for building in Webflow, powered by the [official Webflow MCP server](https://github.com/webflow/mcp-server). Works in both Claude Code and Claude Cowork.

## Setup
- **MCP Server**: Remote Webflow MCP via OAuth (configured in `.claude/mcp.json`)
- **Auth**: OAuth - browser prompt on first use, authorizes site access
- **Node.js**: Requires 22.3.0+
- To reset auth: `rm -rf ~/.mcp-auth`

## MCP Server Capabilities
The Webflow MCP server exposes tools for both the **Data API** and **Designer API**:

### Data API Tools
- List and manage sites
- CMS collections: create, read, update fields and items
- Pages: list, get metadata, update SEO settings
- Assets: upload and manage
- Custom scripts on pages

### Designer API Tools (requires MCP Bridge App in Designer)
- Create and modify elements on the canvas
- Apply styles and design variables
- Build components
- Work with breakpoints for responsive design

## Safety Rules (CRITICAL)

### Never do without explicit user confirmation:
- **Publish the site** - this pushes changes live to production
- **Delete CMS items or collections** - data loss is permanent
- **Bulk updates to CMS items** - always preview what will change first
- **Modify page SEO settings in bulk** - can affect search rankings
- **Update static page content** - changes go to staging but affect the site

### Rate Limits
- **60 requests/minute** for general API calls
- **1 publish/minute** for site publishes
- For batch operations, space requests and process sequentially

### Best Practices
- Always **read before write** - fetch current state before updating anything
- **Log what you're about to change** before doing it
- When working with CMS items, list them first to confirm IDs and current field values
- The `pages_update_static_content` tool only works for secondary locales, not the default locale

## Brand Voice

When writing or editing any copy for this Webflow site, follow the brand guidelines in `brand/`:

- **`brand/voice-and-tone.md`** — Core voice attributes, dos/don'ts, tone shifts by context
- **`brand/writing-by-surface.md`** — How to write for each surface (marketing, enterprise, docs, blog, customer stories, pricing, AI features)
- **`brand/vocabulary.md`** — Preferred terms, words to avoid, capitalization, number formatting

**Quick reference**: Webflow's voice is a knowledgeable, warm mentor. Confident but not arrogant. Empowering but not hand-holding. Substance over hype. Lead with outcomes, not features. Respect the reader's intelligence.

## API Reference
- MCP server docs: https://developers.webflow.com/mcp/reference/overview
- Data API docs: https://developers.webflow.com/data/v2.0.0/reference/rest-introduction
- MCP server source: https://github.com/webflow/mcp-server
