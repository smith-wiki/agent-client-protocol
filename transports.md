# Stdio is ACP’s stable transport; HTTP and WebSocket remain a draft

ACP messages are UTF-8 JSON-RPC. Stable v1 recommends **stdio** whenever
possible; Streamable HTTP is explicitly still a draft, and custom transports
are permitted ([transports, L1–L8](https://agentclientprotocol.com/protocol/v1/transports)).

With stdio, the client launches the agent subprocess, writes messages to its
`stdin`, and reads messages from its `stdout`. Each request, notification, or
response occupies one line: `\n` delimits frames and embedded newlines are
forbidden. Only valid ACP messages may appear on `stdin` or `stdout`; the agent
may write UTF-8 logs to `stderr`, which the client may capture, forward, or
ignore ([transports, L10–L21](https://agentclientprotocol.com/protocol/v1/transports)).
This process ownership complements the protocol’s
[client/agent trust model](architecture.md).

The **Streamable HTTP & WebSocket Transport RFD is a proposal, not stable v1**.
It is intended to standardize remote bidirectional operation with Streamable
HTTP/SSE streams and WebSocket while preserving ACP’s JSON-RPC message format
and lifecycle. Until that RFD stabilizes, HTTP/WebSocket implementations are
custom transports rather than a portable ACP contract
([transport RFD](https://agentclientprotocol.com/rfds/streamable-http-websocket-transport)).
Custom transports must preserve JSON-RPC and ACP lifecycle requirements and
should document connection establishment and message exchange
([transports, L27–L34](https://agentclientprotocol.com/protocol/v1/transports)).
