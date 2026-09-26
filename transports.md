# Local agents speak JSON-RPC over stdio; remote agents are still in progress

The introduction describes two deployment shapes
([source, L12–L18](https://agentclientprotocol.com/get-started/introduction)):

| Shape  | Where the agent runs                         | Transport              | Status |
|--------|----------------------------------------------|------------------------|--------|
| Local  | sub-process of the code editor               | JSON-RPC over stdio    | the main case |
| Remote | cloud or separate infrastructure             | HTTP or WebSocket      | "work in progress" |

So in the local case the editor (the *client*) owns the agent's process: it
launches the agent and talks to it over the agent's stdin/stdout, as editors
do with LSP servers. For remote agents the maintainers say they are still
working with agentic platforms on the requirements of cloud-hosted deployments
([L16–L18](https://agentclientprotocol.com/get-started/introduction)).

Why this decoupling matters: [ACP decouples AI coding agents from editors, the
way LSP decoupled language servers](why-acp.md).
