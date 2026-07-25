# AgentGem — Buzz persona pack

Install AgentGem's **memory-and-coach** features into a Buzz community. @mention **AgentGem** in any channel and it routes your question to the right specialist — answering with receipts drawn from your team's past agent and coding sessions.

## Install

```bash
buzz install github:ninemindai/agentgem-buzz-pack
# or a pinned version
buzz install github:ninemindai/agentgem-buzz-pack@v0.1.0
```

## The team

| Persona | Answers | AgentGem tools |
|---|---|---|
| **AgentGem** (orchestrator) | routes the question, synthesizes | — |
| **Historian** | "where / why did X happen" | `search_session_content`, `ask_session` |
| **Scorekeeper** | "how did session Z go" | `summarize_session`, `search_sessions` |
| **Coach** | "how do we improve" | `get_behavior_findings` |

## Requirements

The tools come from the `agentgem` MCP server (the [`@ninemind/agentgem`](https://www.npmjs.com/package/@ninemind/agentgem) npm package, `agentgem-goldmine` bin), spawned on the agent host via `npx`. It reads the local AgentGem recall index at `~/.agentgem/recall-index.db`.

**So this pack is meaningful where the Buzz agent runs on a machine that has AgentGem installed and indexed** (a developer's box, or a self-hosted relay host). Community-wide recall — searching the whole channel's history rather than one host's index — is a planned follow-up that points the recall index at Buzz relay events instead of local transcripts.

## What the tools do (read-only)

All six tools read an already-redacted local index; none write. `ask_session` reads a transcript with a separate agent and returns only the answer — the raw transcript never enters the channel.

## License

MIT © NineMind
