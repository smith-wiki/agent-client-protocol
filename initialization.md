# Initialization fixes one protocol version and advertises every optional surface

Before any session, the client calls `initialize` with its latest integer `protocolVersion`, `clientCapabilities`, and preferably `clientInfo`; the agent returns the selected version, `agentCapabilities`, optional `authMethods`, and preferably `agentInfo` ([initialization, L1–L21](https://agentclientprotocol.com/protocol/v1/initialization)).

```json
{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":1,"clientCapabilities":{"fs":{"readTextFile":true,"writeTextFile":true},"terminal":true},"clientInfo":{"name":"editor","title":"Editor","version":"1.0"}}}
```

If the agent supports the requested major version it echoes it; otherwise it returns its latest supported version. A client that cannot speak that version should close the connection and tell the user ([initialization, L23–L39](https://agentclientprotocol.com/protocol/v1/initialization)). Omitted capabilities mean **unsupported** ([initialization, L41–L53](https://agentclientprotocol.com/protocol/v1/initialization)).

Client groups are `auth.terminal`, `fs.readTextFile`, `fs.writeTextFile`, `terminal`, `elicitation` (`form`/`url`), and boolean session-config support ([initialization, L54–L107](https://agentclientprotocol.com/protocol/v1/initialization)). Agent groups are `loadSession`, `promptCapabilities` (`image`, `audio`, `embeddedContext`), `mcpCapabilities` (`http`, deprecated `sse`), `auth.logout`, and `sessionCapabilities` (`list`, `fork`, `resume`, `close`, `delete`, `additionalDirectories`); text and resource links plus `session/new`, `session/prompt`, `session/cancel`, and `session/update` are baseline ([initialization, L108–L196](https://agentclientprotocol.com/protocol/v1/initialization)). `clientInfo`/`agentInfo` contain `name`, optional human-readable `title`, and `version` ([initialization, L198–L219](https://agentclientprotocol.com/protocol/v1/initialization)).

Each `authMethods` entry has an `id`. Agent-driven methods use `authenticate { methodId }`; terminal methods instead launch an interactive process. Stable v1 `logout` is callable only when `agentCapabilities.auth.logout` is `{}` ([authentication, L6–L16 and L30–L60](https://agentclientprotocol.com/protocol/v1/authentication)).