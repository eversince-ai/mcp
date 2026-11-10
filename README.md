# Eversince MCP server

Eversince is the media workspace for agents. Agents find, edit, design, generate and render images, video and audio with the user: clips cut from long recordings, pauses and filler words removed, vertical crops that follow the person, captions timed to each word, carousels and thumbnails, generated images, video, voice and music, and dubbing in the speaker's own voice. Media is searchable down to moments inside recordings. Every piece stays an editable timeline or canvas that the user sees and changes in the Eversince app before anything is rendered, and the next session continues from the same state. Through the desktop app, edits export to Premiere Pro, DaVinci Resolve or Final Cut Pro. This is the hosted Model Context Protocol server.

| | |
|---|---|
| Server | `https://mcp.eversince.ai/mcp` |
| Transport | Streamable HTTP, stateless |
| Authentication | OAuth 2.1, discovered at `https://mcp.eversince.ai/.well-known/oauth-protected-resource`; or an API key on `Authorization: Bearer` |
| Capabilities | tools |
| Documentation | https://docs.eversince.ai |

Nothing is installed or run. A client connects to the address and the user signs in. Agents like ChatGPT, Claude, Muse, and Grok Bot take the address as a connector. Claude Code, Codex, Cursor, VS Code and any client that accepts a URL add it as an HTTP MCP server. An agent that can run commands sets itself up from https://eversince.ai/get-started.md. An agent that can do neither and can send HTTPS requests connects by a link the user opens and receives an API key (https://docs.eversince.ai/connect).

```sh
claude mcp add --transport http eversince https://mcp.eversince.ai/mcp
codex mcp add eversince --url https://mcp.eversince.ai/mcp
```

```json
{ "mcpServers": { "eversince": { "type": "http", "url": "https://mcp.eversince.ai/mcp" } } }
```

## On the user's computer

The Eversince desktop app, for Mac and Windows, runs the same server on the computer it is installed on, for the agents there, and works on files where they are. `npm install -g eversince` then `eversince init --agent <name>` connects an agent through the app. Details: https://docs.eversince.ai/mcp-server.

## License

MIT for this README. The hosted server is subject to the [Eversince terms](https://eversince.ai/terms).
