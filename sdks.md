# ACP’s official SDKs cover five languages, while community ports broaden the runtime map

The official TypeScript package is `@agentclientprotocol/sdk`; it implements
both protocol sides, and its fluent `agent()`/`client()` APIs replace deprecated
connection classes ([TypeScript, L1–L13 and L15–L25](https://agentclientprotocol.com/libraries/typescript)).
Rust uses the `agent-client-protocol` crate and its `Agent` or `Client` traits
([Rust, L1–L22](https://agentclientprotocol.com/libraries/rust)). Python installs
`agent-client-protocol`, providing Pydantic models, async base classes, and
JSON-RPC plumbing ([Python, L1–L11](https://agentclientprotocol.com/libraries/python)).
Kotlin uses `com.agentclientprotocol:acp:0.1.0-SNAPSHOT`; only JVM is currently
supported, with other targets in progress
([Kotlin, L1–L24](https://agentclientprotocol.com/libraries/kotlin)). Java’s SDK
provides models, JSON-RPC plumbing, connection helpers, examples, and Spring AI
integrations, but its page gives no artifact coordinate
([Java, L1–L7](https://agentclientprotocol.com/libraries/java)).

The community catalog adds Cangjie `acp-cj`, C++ `acp-cpp`, Crystal `acp.cr`,
Dart `acp_dart`, three .NET libraries, Elixir
`raxol_agent_client_protocol`, and Emacs `acp.el`
([community, L1–L29](https://agentclientprotocol.com/libraries/community)). It
also lists six Go libraries, React `use-acp`, TypeScript `acp-ts-sdk`, three
Swift libraries, and a Vala SDK
([community, L31–L60](https://agentclientprotocol.com/libraries/community)).
These pages link official repositories under the `agentclientprotocol`
organization and community repositories under their respective owners, but do
not name individual maintainers. Nor do they call one SDK the schema’s reference
implementation: the strongest explicit statement is that Python **mirrors** the
official ACP schema ([Python, L1–L4](https://agentclientprotocol.com/libraries/python)).
