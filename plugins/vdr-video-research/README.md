# VDR Video Research Plugin

Search and analyze 5M+ videos and ads with AI-powered deep research.

## Claude Desktop / Cowork (OAuth — recommended)

1. Open **Settings > Connectors** in the Claude Desktop or Cowork app.
2. Click **Add custom connector**.
3. Enter the server URL: `https://mcp.videodeepresearch.com/mcp`
4. Complete the OAuth sign-in flow when prompted.
5. The VDR tools will appear automatically after authorization.

No environment variables or tokens needed — Claude handles OAuth automatically.

For the test environment, use: `https://mcp-test.videodeepresearch.com/mcp`

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

- **talk-to-1M** - Search the video corpus using `talk_to_1m`
- **talk-to-ads** - Analyze ad videos using `talk_to_ads`

## Claude Code CLI Setup (API key)

1. Set your API token:

```bash
export VDR_MCP_TOKEN='your-api-token-here'
```

2. Install the plugin:

```
claude plugin install vdr-video-research@vdr-plugin
```

Or run the setup command after installation:

```
/vdr-video-research:setup
```

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `VDR_MCP_TOKEN` | CLI only | Bearer token for API key authentication (not needed for OAuth) |
| `VDR_VIDEO_RESEARCH_URL` | No | Server URL override (defaults to `https://mcp.videodeepresearch.com`) |
