# mcp-backlink-checker

<!-- mirror-seo:start -->

**MCP server for a backlink checker: does a page link to your domain, dofollow or nofollow, anchor text and robots guards.** Backlink checks from Claude or Cursor: dofollow or nofollow, anchor text, HTTP status and robots guards.

Works with Claude Desktop, Claude Code, Cursor and any Model Context Protocol client. Runs on your own machine: this one has no hosted endpoint, so install it from the bundle or from source.

## Install

**Claude Desktop, one click.** Download `backlink-checker.mcpb` from the [latest release](https://github.com/theluckystrike/mcp-servers/releases/latest) and double-click it.

**From source.** The mirror is self-contained: every `@theluckystrike/*` dependency is vendored, so a fresh clone builds with no extra setup.

```sh
git clone https://github.com/theluckystrike/mcp-backlink-checker.git
cd mcp-backlink-checker
npm install && npm run build
```

Then point your client at the built entry point:

```json
{
  "mcpServers": {
    "backlink-checker": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-backlink-checker/dist/index.js"]
    }
  }
}
```

> `@theluckystrike/mcp-backlink-checker` is **not published on npm yet**, so an `npx -y @theluckystrike/mcp-backlink-checker` command will fail. The three paths above are the working ones and each is exercised by CI.

![backlink-checker demo](https://raw.githubusercontent.com/theluckystrike/mcp-servers/main/assets/demo-backlink-checker.gif)

Read-only mirror of [mcp-servers/servers/backlink-checker](https://github.com/theluckystrike/mcp-servers/tree/main/servers/backlink-checker). See [MIRROR.md](MIRROR.md).

<!-- mirror-seo:end -->

**In the [official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.theluckystrike%2Fbacklink-checker/versions/latest)** (`io.github.theluckystrike/backlink-checker`).
Backlink checking for solopreneurs and small studios: does a page link to
your domain, dofollow or nofollow, with anchor text, HTTP status and robots
guards, read directly from your MCP client — Claude Desktop, Cursor, or any
MCP host. All checks run on demand, nothing stored.

## Tools

- `"link_check"` — check one page: does it link to your domain, dofollow or nofollow, with anchor text and HTTP status.
- `"link_audit"` (Pro) — audit a batch of pages in one call, one verdict row per page.
- `"robots_guard_check"` — read a page's robots rules before you touch it, so audits stay polite.

## The one rule that decides everything else

Nothing is stored. Every call fetches the page live, parses the anchor,
applies the robots guards, and reports — so a verdict is always about the
page as it is now, never as it was.

## Free vs Pro

The free tier is full single-page checking: `link_check` and
`robots_guard_check`, watermark-free, no per-day limits. Pro (an
`MCP_LICENSE_KEY`, activate with `license_activate`) adds batch
`link_audit`. Run `license_status` to see the current tier.

## Quick start

```json
{
  "mcpServers": {
    "backlink-checker": { "command": "npx", "args": ["-y", "@theluckystrike/mcp-backlink-checker"] }
  }
}
```

## Buy

Single-server Pro is $19, or get all 46 servers with one lifetime key for
$39 — see [mcp.zovo.one/buy/backlink-checker](https://mcp.zovo.one/buy/backlink-checker).

## Use these docs as an MCP server

Any MCP client (Claude, Cursor, Windsurf, VS Code) can read this repository's documentation directly via GitMCP — no install:

- Docs MCP URL: https://gitmcp.io/theluckystrike/mcp-backlink-checker
