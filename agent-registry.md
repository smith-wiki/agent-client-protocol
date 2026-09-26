# The ACP Registry turns curated manifests into installable agent metadata for every client

The registry is a curated distribution channel for ACP-compatible agents that
support authentication, not merely a directory
([registry, L1–L5](https://agentclientprotocol.com/get-started/registry)). Clients
fetch one aggregate containing agent metadata and automatic-installation details:

```text
https://cdn.agentclientprotocol.com/registry/v1/latest/registry.json
```

([registry, L173–L181](https://agentclientprotocol.com/get-started/registry))

An agent contributes `<id>/agent.json`; its ID is lowercase with hyphens
allowed, `icon.svg` is optional, and listing changes arrive through pull
requests ([registry, L183–L197](https://agentclientprotocol.com/get-started/registry)).
The registry RFD defines `distribution` as any combination of three independent
strategies: `binary`, `npx`, and `uvx`. Binary archives are keyed by
`<os>-<arch>` and must cover Darwin, Linux, and Windows; `npx` installs Node
packages and `uvx` installs Python packages
([registry RFD, L21–L36](https://agentclientprotocol.com/rfds/acp-agent-registry)).
Icons must be 16×16 monochrome SVGs using `currentColor`
([registry RFD, L37–L44](https://agentclientprotocol.com/rfds/acp-agent-registry)).

The proposal’s CI validates schema compliance, unique slugs, icons, distribution
URLs, binary OS coverage, and authentication during an ACP handshake, then
publishes versioned and `latest` aggregates
([registry RFD, L65–L76](https://agentclientprotocol.com/rfds/acp-agent-registry)).
Its February 2026 revision removed `schema_version`, `homepage`, `capabilities`,
and `auth`, added `icon`, and established the three distribution types
([registry RFD, L86–L100](https://agentclientprotocol.com/rfds/acp-agent-registry)).
Thus the RFD records the design history, while the registry page documents the
operational endpoint and submission flow.
