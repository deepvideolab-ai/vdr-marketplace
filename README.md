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
