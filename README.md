# Eversince MCP Server

A hosted **Model Context Protocol (MCP)** server that exposes the Eversince creative agent — image, video, audio, and motion graphics generation — to any MCP-compatible client.

- **Transport**: Streamable HTTP
- **MCP SDK**: `@modelcontextprotocol/sdk` (server-side)
- **Server URL**: `https://mcp.eversince.ai/mcp`

## What this is

This is an MCP server implementation. It speaks JSON-RPC 2.0 over HTTP per the MCP specification and exposes a set of MCP tools that let MCP clients (Claude Desktop, Cursor, Cline, Windsurf, claude.ai, Zed) drive the Eversince creative agent.

The server is hosted by Eversince. There is nothing to install or run locally — connect any MCP client to the URL above.

## MCP capabilities

| Capability | Supported |
|---|---|
| `tools` | Yes |
| `resources` | Yes |
| `prompts` | No |
| `sampling` | No |
| `roots` | No |

Tools are discovered via the standard MCP `tools/list` method. The current set is returned live by the server, with full input schemas.

Resources are discovered via `resources/list` — the server exposes the agent-facing skill playbook, API reference, and advanced patterns documents at `eversince://skill`, `eversince://reference/api`, and `eversince://reference/patterns`.

## Authentication

The server implements **OAuth 2.1** authorization per the MCP authorization specification, with discovery via [RFC 9728 Protected Resource Metadata](https://datatracker.ietf.org/doc/rfc9728/) at `https://mcp.eversince.ai/.well-known/oauth-protected-resource`.

Two credential types are accepted on the `Authorization: Bearer <token>` header:

1. **OAuth 2.1 access token** — Issued via the standard MCP OAuth flow. MCP clients (Claude Desktop, Cursor, claude.ai) discover the authorization server automatically.
2. **API key** — Static `es_live_*` key for programmatic clients. Create at https://eversince.ai/app/settings.

On 401, the server returns a `WWW-Authenticate: Bearer` header so MCP clients can complete OAuth discovery.

## Connect

Most MCP clients accept the server URL directly via their MCP settings. For clients that only support local stdio servers, use a remote bridge such as [`mcp-remote`](https://github.com/geelen/mcp-remote).

```json
{
  "mcpServers": {
    "eversince": {
      "url": "https://mcp.eversince.ai/mcp"
    }
  }
}
```

## Links

| | |
|---|---|
| Production endpoint | `https://mcp.eversince.ai/mcp` |
| OAuth metadata | `https://mcp.eversince.ai/.well-known/oauth-protected-resource` |
| Documentation | https://docs.eversince.ai |
| Account & API keys | https://eversince.ai/app/settings |

## License

MIT for this README. The hosted MCP server is subject to the [Eversince Terms of Service](https://eversince.ai/terms).
