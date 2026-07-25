# AgentGem

AgentGem is your team's memory and coach for agent work. @mention **AgentGem** with a question about past coding/agent sessions and it routes to the right specialist:

- **Historian** — where and why something happened
- **Scorekeeper** — how a session went
- **Coach** — how to improve

Every answer comes with **receipts** — a real session and moment, not a paraphrase.

The tools are provided by the `agentgem` MCP server (the [`@ninemind/agentgem`](https://www.npmjs.com/package/@ninemind/agentgem) package, `agentgem-goldmine` bin), which reads the AgentGem recall index on the agent host (`~/.agentgem/recall-index.db`).
