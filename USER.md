# OpenClaw Personal AI Employee Configuration

## Available Skills

### ai-image-generation
- **Description**: Generate and edit images on RunComfy via the `runcomfy` CLI
- **Models**: FLUX 2 (Klein, Pro, Dev, Flash, Turbo, Max), Google Nano Banana 2/Pro, OpenAI GPT Image 2, ByteDance Seedream, Alibaba Qwen, Wan
- **Triggers**: "generate image", "make a picture", "text to image", "AI image", "image to image", "i2i", or explicit image creation requests
- **Capabilities**: Text-to-image (t2i) and image-to-image / edit (i2i) endpoints
- **Scope**: Project-level (`.claude/skills/ai-image-generation/` and `skills/ai-image-generation/`)

## Available MCP Tools

### mcp-server-time
- **Provider**: Stdio transport via `uvx mcp-server-time`
- **Tools**:
  - `get_current_time`: Returns current time for a timezone
  - `convert_time`: Converts time between timezones
- **Configuration**: `mcp.servers.time` in OpenClaw config
- **Scope**: Gateway-level (available to all agents)
- **Status**: Connected and operational as of 2026-06-17

## Scheduled Jobs

When scheduled jobs run, they have access to:
- All skills listed above
- All MCP tools (time zone handling via mcp-server-time)
- The agent model: `google/gemini-3.1-flash-lite-preview`

## Notes

- MCP server initialized via systemd PATH at `/home/waqarjanas/.local/bin`
- Image generation requires `runcomfy` CLI
- Timezone operations use real-time data from mcp-server-time (not training data)
