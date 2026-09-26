# ACP v1 content blocks reuse MCP’s typed envelope, with capabilities governing rich prompt inputs.

ACP v1 uses MCP’s `ContentBlock` structure so agents can forward MCP tool output without transformation. The same blocks carry user input in `session/prompt`, streamed model output in `session/update`, and tool-call progress or results ([ACP Content, lines 1–8](https://agentclientprotocol.com/protocol/v1/content)). See [prompt turns](prompt-turn.md) for the lifecycle that transports these payloads.

The stable variants are:

- `type: "text"` with required `text` and optional `annotations`; agents **MUST** support it in prompts ([ACP Content, lines 9–24](https://agentclientprotocol.com/protocol/v1/content)).
- `type: "image"` with required base64 `data` and `mimeType`, plus optional `uri` and `annotations`; prompt use requires the `image` capability ([ACP Content, lines 25–49](https://agentclientprotocol.com/protocol/v1/content)).
- `type: "audio"` with required base64 `data` and `mimeType`, plus optional `annotations`; prompt use requires the `audio` capability ([ACP Content, lines 50–70](https://agentclientprotocol.com/protocol/v1/content)).
- `type: "resource_link"` with required `uri` and `name`, plus optional `mimeType`, `title`, `description`, `size`, and `annotations`. Its section specifies no separate prompt capability ([ACP Content, lines 86–119](https://agentclientprotocol.com/protocol/v1/content)).
- `type: "resource"` with required `resource` containing embedded resource contents and optional `annotations`; prompt use requires `embeddedContext` ([ACP Content, lines 71–85](https://agentclientprotocol.com/protocol/v1/content)).

A compact image block is:

```json
{"type":"image","data":"iVBORw0…","mimeType":"image/png","uri":"file:///diagram.png"}
```

Its encoded bytes, media type, and optional source URI correspond directly to the image fields above ([ACP Content, lines 25–49](https://agentclientprotocol.com/protocol/v1/content)).
