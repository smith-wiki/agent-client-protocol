# Agent Client Protocol (ACP)

A close study of the [Agent Client Protocol](https://agentclientprotocol.com/get-started/introduction):
an open protocol that standardizes communication between code editors
(clients) and AI coding agents.

## Where to start

- **Why and who:** [why-acp](why-acp.md) → [architecture](architecture.md) → [history](history.md)
- **The protocol, in call order:** [transports](transports.md) → [initialization](initialization.md) → [sessions](sessions.md) → [prompt-turn](prompt-turn.md)
- **What flows through a turn:** [content-blocks](content-blocks.md), [tool-calls-and-permissions](tool-calls-and-permissions.md), [client-filesystem-and-terminals](client-filesystem-and-terminals.md), [plans-modes-and-commands](plans-modes-and-commands.md)
- **Around the core:** [mcp-in-acp](mcp-in-acp.md), [extensibility](extensibility.md), [acp-v2](acp-v2.md)
- **Ecosystem and process:** [agents-and-clients](agents-and-clients.md), [agent-registry](agent-registry.md), [sdks](sdks.md), [governance](governance.md), [rfd-process](rfd-process.md)

## Questions and answers

1. **What is ACP and what problem does it solve?** It lets any ACP agent work
   in any ACP editor, replacing per-pair custom integrations, as LSP did for
   language servers. See [why-acp](why-acp.md).
2. **How do the editor and the agent talk?** Stable v1 specifies
   newline-delimited UTF-8 JSON-RPC over stdio with the agent as the editor's
   sub-process; Streamable HTTP and WebSocket are still a draft. See
   [transports](transports.md).
3. **What is the protocol's lifecycle?** `initialize` fixes one protocol version
   and exchanges capabilities ([initialization](initialization.md)); `session/new`
   creates a session, `session/load` replays one, `session/resume` reattaches
   ([sessions](sessions.md)); each `session/prompt` streams `session/update`
   notifications until one stop reason ([prompt-turn](prompt-turn.md)).
4. **Who controls what?** The client owns the user, permissions and the
   environment; the agent owns the conversation and calls back into the
   client's advertised capabilities. See [architecture](architecture.md).
5. **What can an agent ask of the editor?** Capability-gated file reads and
   writes (which see unsaved buffers) and terminals
   ([client-filesystem-and-terminals](client-filesystem-and-terminals.md));
   permission for tool calls and structured user input
   ([tool-calls-and-permissions](tool-calls-and-permissions.md)).
6. **How is content represented?** With MCP's `ContentBlock` variants; rich
   prompt inputs are gated by prompt capabilities. See
   [content-blocks](content-blocks.md).
7. **How do agents expose plans, modes, settings and commands?** As
   replace-the-whole-list `session/update`s and session methods; config options
   supersede the older modes. See
   [plans-modes-and-commands](plans-modes-and-commands.md).
8. **How does ACP relate to MCP?** ACP carries the editor–agent conversation;
   the client hands the agent MCP server configs for tools, and ACP reuses MCP
   types. An unstable RFD would tunnel MCP over ACP. See
   [mcp-in-acp](mcp-in-acp.md).
9. **How is ACP extended?** Through `_meta` fields and underscore-prefixed
   methods, advertised in capability `_meta`. See [extensibility](extensibility.md).
10. **What changes in ACP v2?** Prompt acceptance is separated from turn state,
    updates become replayable, client execution APIs are removed; v1 and v2
    coexist via per-connection version negotiation. v2 is still a draft. See
    [acp-v2](acp-v2.md).
11. **Who implements ACP?** Dozens of agents (some, like Claude Agent and
    Codex CLI, via adapters) and editors including Zed, JetBrains IDEs, Neovim,
    Emacs, VS Code and Visual Studio. See
    [agents-and-clients](agents-and-clients.md); agents are distributed through
    a curated [registry](agent-registry.md); official [SDKs](sdks.md) exist for
    TypeScript, Rust, Python, Kotlin and Java.
12. **Who maintains ACP and how does it change?** Zed and JetBrains govern it
    jointly under an interim maintainer hierarchy ([governance](governance.md));
    changes go through RFDs from Draft to Completed ([rfd-process](rfd-process.md)).
    Zed launched it with Gemini CLI in August 2025 ([history](history.md)).
13. *Open:* when will v2 stabilize? The migration guide gives no date.
14. *Open:* what exactly do the session-fork, proxy-chains and Streamable
    HTTP/WebSocket RFDs propose? Their reading copies were not available yet.
