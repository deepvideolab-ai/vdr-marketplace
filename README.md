# VDR Plugins - Video Deep Research for Claude Code

Claude Code plugin marketplace for [Video Deep Research](https://videodeepresearch.com) MCP servers. Search and analyze millions of videos and ads using AI-powered deep research directly from Claude Code.

## Quick Start

### 1. Add the marketplace

```
/plugin marketplace add deepvideolab-ai/vdr-plugins
```

### 2. Install the plugin

```
/plugin install vdr-video-research@vdr-tools
```

### 3. Set your API token

Add to your shell profile (`~/.bashrc` or `~/.zshrc`):

```bash
export VDR_MCP_TOKEN='your-api-token-here'
```

### 4. Use it

Ask Claude Code to search videos:

```
Search for videos about electric vehicle marketing strategies
```

Or run the setup command to configure authentication:

```
/vdr-video-research:setup
```

Or use the skills directly:

```
/vdr-video-research:video-search Find videos about AI coding assistants
/vdr-video-research:ad-analysis What creative strategies are beauty brands using?
```

## OpenClaw Setup

If you use [OpenClaw](https://openclaw.org), follow these steps to use VDR video-research via mcporter.

### Prerequisites

- A VDR API token (do **not** paste it into chat)
- mcporter installed:
  ```bash
  npm i -g mcporter
  ```

### 1. Configure mcporter for OpenClaw

OpenClaw uses its own mcporter config at `~/.openclaw/workspace/config/mcporter.json`. Add the VDR server:

```bash
export VDR_MCP_TOKEN="YOUR_TOKEN"

mcporter config add vdr-video-research \
  --url "https://mcp.videodeepresearch.com/mcp" \
  --header "Authorization=Bearer $VDR_MCP_TOKEN" \
  --description "Video Deep Research MCP (HTTP, bearer auth)" \
  --persist "$HOME/.openclaw/workspace/config/mcporter.json"
```

If you previously had a broken entry with the same name, remove it first:

```bash
mcporter config remove vdr-video-research \
  --persist "$HOME/.openclaw/workspace/config/mcporter.json"
```

### 2. Verify the server

```bash
mcporter --config "$HOME/.openclaw/workspace/config/mcporter.json" \
  list vdr-video-research --schema

mcporter --config "$HOME/.openclaw/workspace/config/mcporter.json" \
  call vdr-video-research.health --output json
```

You should see `ok: true` and tools like `talk_to_1m` / `talk_to_ads`.

### 3. Install the skill

Download [`dist/vdr-mcporter.skill`](dist/vdr-mcporter.skill) from this repo and install it:

- **OpenClaw app** → Settings → Skills → Import / Install from file → select `vdr-mcporter.skill`
- Or copy manually:
  ```bash
  cp dist/vdr-mcporter.skill ~/.openclaw/workspace/dist/
  ```

### 4. Use it in OpenClaw

Say any of these in the OpenClaw TUI:

- "Use VDR video-search: electric vehicle marketing strategies"
- "Use VDR ad-analysis: What creative strategies are beauty brands using?"
- "Run VDR health check"

### Common gotchas

- **Works elsewhere but not in OpenClaw**: You configured a different mcporter.json. Fix by writing the VDR entry into `~/.openclaw/workspace/config/mcporter.json` (as above).
- **Don't use stdio mode**: A stdio `vdr-video-research` entry that runs mcporter will loop / "connection closed". Use HTTP to `https://mcp.videodeepresearch.com/mcp`.
- **Shell access in TUI**: Optional and gated by a one-time prompt per session. Not needed if mcporter config is correct.

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [vdr-video-research](plugins/vdr-video-research/) | Search and analyze 5M+ videos and ads with AI-powered deep research |

## Configuration

| Environment Variable | Required | Description |
|---------------------|----------|-------------|
| `VDR_MCP_TOKEN` | Yes | Bearer token for API authentication |
| `VDR_VIDEO_RESEARCH_URL` | No | Server URL override (defaults to `https://mcp.videodeepresearch.com`) |

## License

MIT
