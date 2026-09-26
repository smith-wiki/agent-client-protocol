# ACP decouples AI coding agents from editors, the way LSP decoupled language servers

Without a shared protocol, every editor builds a custom integration for every
agent, and every agent implements editor-specific APIs. The ACP introduction
names three consequences
([source, L3–L6](https://agentclientprotocol.com/get-started/introduction)):

- **Integration overhead**: every new agent–editor pair needs custom work.
- **Limited compatibility**: an agent works with only a subset of editors.
- **Developer lock-in**: choosing an agent means accepting the interfaces it
  happens to ship with.

ACP's answer is the LSP move: an agent that implements ACP works with any
compatible editor, and an editor that supports ACP gets the whole ecosystem of
ACP agents, so both sides can evolve independently
([L8](https://agentclientprotocol.com/get-started/introduction)). The N×M
integration problem becomes N+M.

The protocol is editor-centric: it assumes the user lives in the editor and
reaches out to agents for specific tasks
([L12](https://agentclientprotocol.com/get-started/introduction)). Who owns
what is on [ACP is bidirectional](architecture.md); how the two sides are
connected is on [Stdio is ACP's stable transport](transports.md).
