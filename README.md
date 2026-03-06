# Webflow Site Companion

A companion project for building and managing your Webflow site with AI — powered by the [official Webflow MCP server](https://github.com/webflow/mcp-server).

Works with both [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Claude Cowork](https://docs.anthropic.com/en/docs/claude-cowork).

## What This Does

This project connects Claude to your Webflow site so you can manage it conversationally:

- **Site management** — List sites, manage pages, update SEO settings
- **CMS operations** — Create collections, add fields, manage items
- **Design** — Build elements, apply styles, work with components and variables (via the Designer API)
- **Assets** — Upload and organize files
- **Brand-consistent copy** — Built-in brand voice guidelines so Claude writes in your voice

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) or [Claude Cowork](https://docs.anthropic.com/en/docs/claude-cowork)
- Node.js 22.3.0+
- A Webflow account with at least one site

## Getting Started

1. **Clone the repo**

   ```sh
   git clone https://github.com/rachelwolan/webflow-site.git
   cd webflow-site
   ```

2. **Open with Claude Code**

   ```sh
   claude
   ```

   On first use, a browser window will open to authorize Webflow access via OAuth. Grant access to the sites you want to manage.

3. **Start building**

   Ask Claude to list your sites, update CMS content, manage pages, or write copy — it has full access to the Webflow Data API and Designer API.

### Using with Claude Cowork

Open this project in Claude Cowork. The MCP server configuration in `.claude/mcp.json` is picked up automatically.

## Project Structure

```
.claude/mcp.json          # Webflow + Figma MCP server config
CLAUDE.md                 # Safety rules, capabilities, and brand voice reference
brand/
  voice-and-tone.md       # Core voice attributes and tone shifts by context
  writing-by-surface.md   # How to write for each surface (marketing, docs, blog, etc.)
  vocabulary.md           # Preferred terms, words to avoid, capitalization rules
```

## MCP Server Capabilities

The [Webflow MCP server](https://github.com/webflow/mcp-server) exposes tools for both the **Data API** and **Designer API**.

### Data API

- List and manage sites
- CMS collections — create, read, update fields and items
- Pages — list, get metadata, update SEO settings
- Assets — upload and manage
- Custom scripts on pages

### Designer API

Requires the MCP Bridge App running in the Webflow Designer.

- Create and modify elements on the canvas
- Apply styles and design variables
- Build components
- Work with breakpoints for responsive design

## Safety Guardrails

`CLAUDE.md` includes safety rules that Claude follows automatically:

- **Never publishes** without explicit confirmation
- **Never deletes** CMS items or collections without confirmation
- **Always reads before writing** — fetches current state before making changes
- **Respects rate limits** — 60 requests/minute, 1 publish/minute

## Brand Voice

The `brand/` directory contains guidelines that Claude follows when writing copy for your site:

| File | What it covers |
|------|---------------|
| `voice-and-tone.md` | Core voice attributes, dos/don'ts, tone shifts by context |
| `writing-by-surface.md` | How to write for marketing, enterprise, docs, blog, customer stories, pricing, and AI features |
| `vocabulary.md` | Preferred terms, words to avoid, capitalization, number formatting |

You can customize these files to match your own brand.

## Troubleshooting

**OAuth not working?** Reset auth and try again:

```sh
rm -rf ~/.mcp-auth
```

**Designer API tools not available?** Make sure the MCP Bridge App is running in the Webflow Designer.

## Resources

- [Webflow MCP Server Docs](https://developers.webflow.com/mcp/reference/overview)
- [Webflow Data API Reference](https://developers.webflow.com/data/v2.0.0/reference/rest-introduction)
- [MCP Server Source](https://github.com/webflow/mcp-server)

## License

ISC
