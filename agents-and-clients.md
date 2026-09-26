# ACP already connects dozens of agents to editors, sometimes through explicit adapters

The agent catalog currently names AgentPool, Augment Code, AutoDev, Blackbox AI,
Claw Orchestrator, Cline, Code Assistant, Construct, crow-cli, Cursor, Docker’s
cagent, fast-agent, Factory Droid, fount, Gemini CLI, GitHub Copilot, Goose,
Hermes Agent, Junie, Kaagum, Kimi CLI, Kiro CLI, localharness, Minion Code,
Mistral Vibe, OpenClaw, OpenCode, OpenHands, Poolside, Qoder CLI, Qwen Code,
Raxol, siGit Code, Stakpak, stdio Bus, and VT Code
([agents, L1–L40](https://agentclientprotocol.com/get-started/agents)). Four
entries explicitly identify adapters rather than native implementations: Bub via
`bub-acp-server`, Claude Agent via Zed’s SDK adapter, Codex CLI via ACP’s
adapter, and Pi via `pi-acp` ([agents, L5–L9 and L32](https://agentclientprotocol.com/get-started/agents)).
The catalog does **not** explicitly label every unqualified entry “native,” so
absence of “via” is not proof of implementation architecture.

Editor support is similarly varied. Emacs uses `agent-shell.el`; JetBrains is
listed directly; and Neovim uses CodeCompanion, `agentic.nvim`, `avante.nvim`,
or `hermes.nvim` ([clients, L1–L13](https://agentclientprotocol.com/get-started/clients)).
Obsidian has four listed plugins, while Open Knowledge has built-in ACP threads
and registry installation ([clients, L14–L20](https://agentclientprotocol.com/get-started/clients)).
Pulsar, Qt Creator, Sublime Text, Unity, Visual Studio, and Visual Studio Code
use packages or extensions; Zed is also listed as a client
([clients, L20–L33](https://agentclientprotocol.com/get-started/clients)). This is
the concrete ecosystem enabled by ACP’s [N+M integration model](why-acp.md).
