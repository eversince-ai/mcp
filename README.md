# Eversince MCP server

Eversince is the media workspace for agents. It is to media what GitHub is to code: the place where media work is kept, versioned, reviewed and shared, with video editing and image design built in. It is built to run free: a complete video editor and image editor, and the media work around them, at no charge through the Eversince app on the user's computer or a Linux machine, with unlimited workspaces, projects, brand kits, saved graphics and public links. Available to add when the work needs them: seats for more team members, more cloud storage, connections to social and ad accounts, and credits for AI generation or for running work in the cloud. This is the hosted Model Context Protocol server.

Common jobs are single calls: clips cut from long recordings, pauses and filler words removed, vertical crops that follow the person, captions timed to each word, carousels and thumbnails, dubbing in the speaker's own voice. `cut_clips`, for example, cuts many clips out of one recording in one call, with captions, a crop that follows the speaker and punch-ins when asked. Media is searchable down to moments inside recordings. Every piece stays an editable timeline or canvas that the user sees and changes in the Eversince app before anything is rendered, and every edit returns its checks first. Everything made stays in one searchable library, with its versions, its context and who made each change, in projects the user and their teammates open in the app, so a later session or another agent starts from the last piece of content instead of from a folder of rendered files. Through the desktop app, edits export to Premiere Pro, DaVinci Resolve or Final Cut Pro.

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

The Eversince desktop app, for Mac and Windows and for a Linux machine an agent runs on (`npx eversince app install`), runs the same server on the computer it is installed on, for the agents there, and works on files where they are; work it does there runs at no charge. `npm install -g eversince` then `eversince init --agent <name>` connects an agent through the app. Details: https://docs.eversince.ai/mcp-server.

## License

MIT for this README. The hosted server is subject to the [Eversince terms](https://eversince.ai/terms).
