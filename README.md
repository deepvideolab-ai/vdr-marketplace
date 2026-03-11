# VDR Plugins - Video Deep Research

Plugin marketplace for [Video Deep Research](https://videodeepresearch.com) MCP servers. Search and analyze millions of videos and ads using AI-powered deep research.

## Claude Desktop / Cowork (OAuth — recommended)

1. Open **Settings > Connectors** in the Claude Desktop or Cowork app.
2. Click **Add custom connector**.
3. Enter the server URL: `https://mcp.videodeepresearch.com/mcp`
4. Complete the OAuth sign-in flow when prompted.
5. The VDR tools will appear automatically after authorization.

No API keys or environment variables needed — Claude handles OAuth automatically.

For the test environment, use: `https://mcp-test.videodeepresearch.com/mcp`

## Claude Code CLI (API key)

### 1. Add the marketplace

```
claude plugin marketplace add deepvideolab-ai/vdr-marketplace
```

### 2. Install the plugin

```
claude plugin install vdr-video-research@vdr-plugin
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

Or use the skills directly:

```
/vdr-video-research:talk-to-1M Find videos about AI coding assistants
/vdr-video-research:talk-to-ads What creative strategies are beauty brands using?
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

- "Use VDR talk-to-1M: electric vehicle marketing strategies"
- "Use VDR talk-to-ads: What creative strategies are beauty brands using?"
- "Run VDR health check"

### Common gotchas

- **Works elsewhere but not in OpenClaw**: You configured a different mcporter.json. Fix by writing the VDR entry into `~/.openclaw/workspace/config/mcporter.json` (as above).
- **Don't use stdio mode**: A stdio `vdr-video-research` entry that runs mcporter will loop / "connection closed". Use HTTP to `https://mcp.videodeepresearch.com/mcp`.
- **Shell access in TUI**: Optional and gated by a one-time prompt per session. Not needed if mcporter config is correct.

## Using the Test Site

To point any client at the **test** environment instead of production, replace the server URL with `https://mcp-test.videodeepresearch.com/mcp`.

### Claude Desktop / Cowork (OAuth)

1. Open **Settings > Connectors**.
2. Add (or edit) the custom connector and enter: `https://mcp-test.videodeepresearch.com/mcp`
3. Complete the OAuth sign-in flow.

### Claude Code CLI (API key)

Set both environment variables before launching Claude Code:

```bash
export VDR_VIDEO_RESEARCH_URL='https://mcp-test.videodeepresearch.com'
export VDR_MCP_TOKEN='your-test-api-token'
```

Then install (or reinstall) the plugin as usual:

```
claude plugin install vdr-video-research@vdr-plugin
```

### OpenClaw (mcporter)

Configure mcporter with the test URL:

```bash
export VDR_MCP_TOKEN="YOUR_TEST_TOKEN"

mcporter config add vdr-video-research \
  --url "https://mcp-test.videodeepresearch.com/mcp" \
  --header "Authorization=Bearer $VDR_MCP_TOKEN" \
  --description "Video Deep Research MCP – TEST" \
  --persist "$HOME/.openclaw/workspace/config/mcporter.json"
```

### Switching back to production

Unset the URL override (or remove it from your shell profile) so the default production URL is used:

```bash
unset VDR_VIDEO_RESEARCH_URL
```

For OpenClaw, re-run the `mcporter config add` command with the production URL (`https://mcp.videodeepresearch.com/mcp`).

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [vdr-video-research](plugins/vdr-video-research/) | Search and analyze 5M+ videos and ads with AI-powered deep research |

## Configuration

| Environment Variable | Required | Description |
|---------------------|----------|-------------|
| `VDR_MCP_TOKEN` | CLI only | Bearer token for API key authentication (not needed for OAuth) |
| `VDR_VIDEO_RESEARCH_URL` | No | Server URL override (defaults to `https://mcp.videodeepresearch.com`) |

## License

MIT
