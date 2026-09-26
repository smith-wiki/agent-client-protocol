# Agent Client Protocol (ACP)

A close study of the [Agent Client Protocol](https://agentclientprotocol.com/get-started/introduction):
an open protocol that standardizes communication between code editors
(clients) and AI coding agents.

Start with [why ACP exists](why-acp.md), then [how agents are connected](transports.md).

## Questions and answers

1. **What is ACP and what problem does it solve?** It lets any ACP agent work
   in any ACP editor, replacing per-pair custom integrations, as LSP did for
   language servers. See [why-acp.md](why-acp.md).
2. **How do the editor and the agent talk?** A local agent runs as a
   sub-process of the editor and speaks JSON-RPC over stdio; remote agents over
   HTTP or WebSocket are still a work in progress. See
   [transports.md](transports.md).
3. *Open:* what is the protocol's lifecycle (initialization, capabilities,
   sessions, prompt turns)?
4. *Open:* what can an agent ask of the editor (files, terminals, permissions)?
5. *Open:* how does ACP relate to MCP?
6. *Open:* who maintains ACP, and which agents and editors implement it?
