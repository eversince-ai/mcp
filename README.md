# Eversince MCP server

Eversince is the media workspace for agents. Agents search and understand media, down to moments inside recordings, edit video and stills in persistent documents, inspect and render the result, and continue from the same editable state when the user comes back with revisions. Beyond cuts: multicam, keyframes, grading with LUTs and masks, cutouts, audio cleanup and ducking, dubbing in the speaker's own voice, motion graphics, and, through the desktop app, export to Premiere Pro, DaVinci Resolve or Final Cut Pro. This is the hosted Model Context Protocol server.

| | |
|---|---|
| Server | `https://mcp.eversince.ai/mcp` |
| Transport | Streamable HTTP, stateless |
| Authentication | OAuth 2.1, discovered at `https://mcp.eversince.ai/.well-known/oauth-protected-resource`; or an API key on `Authorization: Bearer` |
| Capabilities | tools |
| Documentation | https://docs.eversince.ai |

Nothing is installed or run. A client connects to the address and the user signs in. Agents like ChatGPT, Claude, Muse, and Grok Bot take the address as a connector. Claude Code, Codex, Cursor, VS Code and any client that accepts a URL add it as an HTTP MCP server. An agent that can run commands sets itself up from https://eversince.ai/skill.md. An agent that can do neither connects by a link the user opens and receives an API key (https://docs.eversince.ai/connect).

```sh
claude mcp add --transport http eversince https://mcp.eversince.ai/mcp
codex mcp add eversince --url https://mcp.eversince.ai/mcp
```

```json
{ "mcpServers": { "eversince": { "url": "https://mcp.eversince.ai/mcp" } } }
```

## On the user's computer

The Eversince desktop app, for Mac and Windows, runs the same server on the computer it is installed on, for the agents there, and works on files where they are. `npm install -g eversince` then `eversince init --agent <name>` connects an agent through the app. Details: https://docs.eversince.ai/mcp-server.

## License

MIT for this README. The hosted server is subject to the [Eversince terms](https://eversince.ai/terms).
