# VDR Video Research Plugin

Claude Code plugin for the Video Deep Research MCP server. Search and analyze 5M+ videos and ads with AI-powered deep research.

## Tools

| Tool | Description |
|------|-------------|
| `talk_to_1m` | Search and analyze regular videos using natural language |
| `talk_to_ads` | Search and analyze ad videos for marketing insights |
| `direct_ask` | Analyze specific videos by their platform IDs |
| `deep_research` | Full async analysis pipeline (submit job, poll for results) |
| `deep_research_status` | Poll for deep_research job completion |
| `health` | Server health check |

## Skills

- **video-search** - Search the video corpus using `talk_to_1m`
- **ad-analysis** - Analyze ad videos using `talk_to_ads`

## Setup

1. Set your API token:

```bash
export VDR_MCP_TOKEN='your-api-token-here'
```

2. Install the plugin:

```
/plugin install vdr-video-research@vdr-tools
```

Or run the setup command after installation:

```
/vdr-video-research:setup
```

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `VDR_MCP_TOKEN` | Yes | Bearer token for API authentication |
| `VDR_VIDEO_RESEARCH_URL` | No | Server URL override (defaults to `https://mcp.videodeepresearch.com`) |
