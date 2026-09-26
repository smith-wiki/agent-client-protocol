# ACP v2 makes turns observable and replayable while deliberately breaking v1

ACP v2 has a stable baseline schema, but the protocol as a whole remains draft; `schema.unstable.json` features are separate opt-in experiments. Gate both independently. ([migration, L9–L13](https://agentclientprotocol.com/protocol/v2/migration))

| Change from v1 | v2 effect |
|---|---|
| Negotiation | Send `{"protocolVersion":2}` in `initialize`; a v1-only agent returns `1`. Each connection selects one surface, so retain both. ([migration, L15–L19](https://agentclientprotocol.com/protocol/v2/migration)) |
| Initialization/auth | Both roles use required `info` plus `capabilities`; markers are objects. Auth becomes `auth/login`/`auth/logout`. ([migration, L28–L38](https://agentclientprotocol.com/protocol/v2/migration)) ([migration, L47–L59](https://agentclientprotocol.com/protocol/v2/migration)) |
| Prompt lifecycle | `session/prompt` acknowledges insertion with `messageId`; `state_update` reports `running`, `requires_action`, then `idle` with `stopReason`. ([migration, L62–L93](https://agentclientprotocol.com/protocol/v2/migration)) |
| Messages | Every update/chunk has `messageId`; full `user_message`, `agent_message`, and `agent_thought` upserts replace or clear content; chunks append. ([migration, L104–L124](https://agentclientprotocol.com/protocol/v2/migration)) |
| Tools/permissions | `tool_call_update` creates or patches; status adds `cancelled`; `tool_call_content_chunk` appends. `session/request_permission` separates required `title` from optional typed `subject`. ([migration, L125–L147](https://agentclientprotocol.com/protocol/v2/migration)) ([migration, L165–L175](https://agentclientprotocol.com/protocol/v2/migration)) |
| Sessions/replay | `capabilities.session` requires `session/new`, `session/list`, `session/resume`, `session/close`, `session/prompt`, `session/cancel`, and `session/update`; `replayFrom:{"type":"start"}` replaces `session/load`. ([migration, L186–L201](https://agentclientprotocol.com/protocol/v2/migration)) |
| Diffs/terminals | File operations (`add`/`delete`/`modify`/`move`/`copy`) replace `oldText`/`newText`; agent-owned `terminal_update` snapshots and base64 `terminal_output_chunk`s are display-only. ([migration, L148–L162](https://agentclientprotocol.com/protocol/v2/migration)) |
| Client tools | Client `fs/*` and execution `terminal/*` disappear; provide client-side tools through `mcpServers`. ([migration, L209–L219](https://agentclientprotocol.com/protocol/v2/migration)) |
| Plans/modes | `plan_update` is a `planId`-keyed tagged union (stable `items` variant); dedicated modes become categorized config options. ([migration, L180–L207](https://agentclientprotocol.com/protocol/v2/migration)) |
| Extensibility | Enums and tagged unions accept unknown future variants; custom variants start `_`. ([migration, L3–L7](https://agentclientprotocol.com/protocol/v2/migration)) |

Net-new state, replay, correction, multiple plans, and byte-faithful display follow from these changes. See [prompt-turn.md](prompt-turn.md) for turn flow and [client-filesystem-and-terminals.md](client-filesystem-and-terminals.md) for terminal ownership.