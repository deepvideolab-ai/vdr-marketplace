# VDR Video Research Setup

Configure authentication for the VDR Video Research plugin.

## Steps

1. **Get your API token** from your VDR administrator or the DeepVideoLab.ai dashboard.

2. **Set the environment variable** in your shell profile (`~/.bashrc`, `~/.zshrc`, etc.):

```bash
export VDR_MCP_TOKEN='your-api-token-here'
```

3. **Reload your shell** or run `source ~/.bashrc` (or `~/.zshrc`).

4. **Verify the connection** by asking Claude Code to run the `health` tool:

```
Use the health tool from vdr-video-research to check the server status.
```

## Optional: Custom Server URL

By default, the plugin connects to the production server at `https://mcp.videodeepresearch.com`. To use a different server (e.g., for testing), set:

```bash
export VDR_VIDEO_RESEARCH_URL='https://your-custom-server.example.com'
```

## Troubleshooting

- **401 Unauthorized**: Check that `VDR_MCP_TOKEN` is set and the token is valid/not expired.
- **Connection refused**: Check that the server URL is correct and the server is running.
- **Timeout**: The video analysis tools can take 20-60 seconds. This is normal for large corpus searches.
