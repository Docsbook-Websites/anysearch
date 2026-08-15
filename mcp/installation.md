---
title: MCP Server Installation — AnySearch
description: Connect AnySearch to any MCP client via Streamable HTTP, stdio proxy, or SSE proxy, with config examples for every major agent tool.
---

# MCP Server Installation

The AnySearch MCP Server natively supports Streamable HTTP transport (MCP spec 2025-03-26). SSE and stdio clients can connect via proxy. Choose the installation method that matches your client.

## Transport options

| Transport | Native support | Best for |
|---|---|---|
| Streamable HTTP | Yes | OpenCode, Claude Desktop (2025.6+), web-based clients |
| SSE | Via proxy | Cursor, Windsurf |
| stdio | Via proxy | Claude Desktop (legacy), VS Code Copilot, Cline |

## Streamable HTTP (recommended)

For clients that support Streamable HTTP transport natively — the simplest configuration.

```json
{
  "mcp": {
    "anysearch": {
      "type": "remote",
      "url": "https://api.anysearch.com/mcp",
      "headers": {
        "Authorization": "Bearer ${ANYSEARCH_API_KEY}"
      }
    }
  }
}
```

```json
{
  "mcpServers": {
    "anysearch": {
      "type": "streamable-http",
      "url": "https://api.anysearch.com/mcp",
      "headers": {
        "Authorization": "Bearer ${ANYSEARCH_API_KEY}"
      }
    }
  }
}
```

**Tip:** if you don't have an API key, omit the `headers` section. The server automatically uses anonymous access.

## Stdio proxy

For clients that only support stdio transport. Requires a proxy bridge — `mcp-remote` is recommended.

```json
{
  "mcpServers": {
    "anysearch": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://api.anysearch.com/mcp",
        "--header",
        "Authorization: Bearer ${ANYSEARCH_API_KEY}"
      ]
    }
  }
}
```

Alternatively, use `supergateway`:

```json
{
  "mcpServers": {
    "anysearch": {
      "command": "npx",
      "args": [
        "-y",
        "supergateway",
        "--streamableHttp",
        "https://api.anysearch.com/mcp",
        "--oauth2Bearer",
        "${ANYSEARCH_API_KEY}"
      ]
    }
  }
}
```

**Tip:** without an API key, omit `--header`/`Authorization: Bearer ...` (mcp-remote) or `--oauth2Bearer` and the key (supergateway).

## SSE proxy

For clients that only support SSE transport (Cursor, Windsurf). Start a local SSE proxy server first:

```bash
npx -y supergateway \
  --streamableHttp https://api.anysearch.com/mcp \
  --outputTransport sse \
  --port 8000 \
  --oauth2Bearer <your_api_key>
```

```json
{
  "mcpServers": {
    "anysearch": {
      "type": "sse",
      "url": "http://localhost:8000/sse"
    }
  }
}
```

**Note:** the SSE proxy must remain running while the agent is active — consider running it as a background service. Omit `--oauth2Bearer` if you don't have an API key.

## Client quick reference

| Client | Transport | Config file | Proxy required | Proxy tool |
|---|---|---|---|---|
| OpenCode | Streamable HTTP | `opencode.json` | No | — |
| Claude Desktop (2025.6+) | Streamable HTTP | `claude_desktop_config.json` | No | — |
| Claude Desktop (legacy) | stdio | `claude_desktop_config.json` | Yes | mcp-remote |
| Cursor | SSE | `.cursor/mcp.json` | Yes | supergateway |
| VS Code Copilot | stdio | `.vscode/mcp.json` | Yes | mcp-remote |
| Windsurf | SSE | `mcp_config.json` | Yes | supergateway |
| Cline | stdio | VS Code Settings | Yes | mcp-remote |

## Related

- [Skill Plugin](../skill/installation.md) — Alternative agent-native integration path
- [Authentication](../get-started/authentication.md) — Anonymous vs. API-key access
