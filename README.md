# Eversince MCP server

Eversince is the media workspace for agents, where a user and their agents make content together. A connected agent works on the user's own footage, photos and recordings with a tool for each job, the user sees and changes the same work in the Eversince app, and everything stays in the workspace for the next session. This is the hosted Model Context Protocol server.

Common jobs are single calls: clips cut from a long recording, pauses and filler words removed, a crop that follows the person, captions timed to each word, carousels and thumbnails, dubbing in the speaker's own voice, AI generation, and posting to the user's social and ad accounts. `cut_clips`, for example, cuts many clips out of one recording in one call, with captions, a crop that follows the speaker and punch-ins when asked. Media is searchable down to moments inside recordings. A video is edited as a timeline and an image as a canvas, which stay changeable, which the user sees in the app before anything is rendered, and whose every edit returns its checks first. Everything made is kept in one searchable library and in projects, so a later session or another agent starts from the last work instead of from loose files.

Editing, searching and reading what is stored are free, and workspaces, projects, brand kits, saved graphics and public links are unlimited. Credits pay for AI generation and work on Eversince's servers; through the Eversince app on the user's computer or a Linux machine, the media work runs there at no charge.

| | |
|---|---|
| Server | `https://mcp.eversince.ai/mcp` |
| Transport | Streamable HTTP, stateless |
| Authentication | OAuth 2.1, discovered at `https://mcp.eversince.ai/.well-known/oauth-protected-resource`; or an API key on `Authorization: Bearer` |
| Capabilities | Tools, and two resources that show results as cards in clients that support MCP Apps |
| Documentation | https://docs.eversince.ai |
| Agent setup | https://eversince.ai/get-started.md |

Nothing has to be installed. A client connects to the address and the user signs in. Agents like ChatGPT, Claude, Muse, and Grok Bot take the address as a connector, and a coding agent or any client that accepts a URL adds it as an HTTP MCP server. An agent that can run commands sets itself up from https://eversince.ai/get-started.md. An agent that can do neither but can send HTTPS requests connects through a link the user opens, and receives an API key (https://docs.eversince.ai/connect).

```sh
claude mcp add --transport http eversince https://mcp.eversince.ai/mcp
codex mcp add eversince --url https://mcp.eversince.ai/mcp
```

```json
{ "mcpServers": { "eversince": { "type": "http", "url": "https://mcp.eversince.ai/mcp" } } }
```

## On the user's computer

The Eversince desktop app for Mac and Windows, and the app on a Linux machine an agent runs on (`npx eversince app install`), run the same server on that computer for the agents there. The media work the app can do runs on that computer at no charge, and the agent can use files on it without uploading them. `npm install -g eversince`, then `eversince init --agent <name>`, connects an agent through the app. Details: https://docs.eversince.ai/mcp-server.

## License

MIT for this README. The hosted server is subject to the [Eversince terms](https://eversince.ai/terms).
