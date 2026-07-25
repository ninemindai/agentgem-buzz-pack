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
| **ReportCard** | "score my steering / give me a report card" | `gemit` skill (runs the CLI) ⚠️ |

## Requirements

The tools come from the `agentgem` MCP server (the [`@ninemind/agentgem`](https://www.npmjs.com/package/@ninemind/agentgem) npm package, `agentgem-goldmine` bin), spawned on the agent host via `npx`. It reads the local AgentGem recall index at `~/.agentgem/recall-index.db`.

**So this pack is meaningful where the Buzz agent runs on a machine that has AgentGem installed and indexed** (a developer's box, or a self-hosted relay host). Community-wide recall — searching the whole channel's history rather than one host's index — is a planned follow-up that points the recall index at Buzz relay events instead of local transcripts.

## Capabilities & security

**Historian, Scorekeeper, and Coach are read-only.** Their six goldmine tools read an already-redacted local index; none write. `ask_session` reads a transcript with a separate agent and returns only the answer — the raw transcript never enters the channel.

**ReportCard can execute a command — scoped to that one persona.** The `gemit` report card is a CLI (`npx … gemit`), not a read-only tool, so ReportCard is granted Buzz's shell MCP (`buzz-dev-mcp`) via its own `mcp_servers` front matter. That is a **broad capability** (a shell can run anything), deliberately isolated to ReportCard and absent from the other three personas. Only add this pack to a community where you're comfortable with that persona running commands on the agent host.

- ReportCard runs `gemit` for the score and only runs `gemit --share` (which publishes an unlisted, redacted card) when someone explicitly asks — it never passes `--yes` on your behalf.
- **Cleaner future path:** expose `gemit` as a proper read-only-style MCP tool in the `agentgem-goldmine` server (a `run_gemit` tool). That would drop the shell requirement entirely — tracked as a follow-up in the AgentGem repo.

## License

MIT © NineMind
