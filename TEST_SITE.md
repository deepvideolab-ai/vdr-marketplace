# Using the Test Site

To point any client at the **test** environment instead of production, replace the server URL with `https://mcp-test.videodeepresearch.com/mcp`.

## Claude Desktop / Cowork (OAuth)

1. Open **Settings > Connectors**.
2. Add (or edit) the custom connector and enter: `https://mcp-test.videodeepresearch.com/mcp`
3. Complete the OAuth sign-in flow.

## Claude Code CLI (API key)

Set both environment variables before launching Claude Code:

```bash
export VDR_VIDEO_RESEARCH_URL='https://mcp-test.videodeepresearch.com'
export VDR_MCP_TOKEN='your-test-api-token'
```

Then install (or reinstall) the plugin as usual:

```
claude plugin install vdr-video-research@vdr-plugin
```

## OpenClaw (mcporter)

Configure mcporter with the test URL:

```bash
export VDR_MCP_TOKEN="YOUR_TEST_TOKEN"

mcporter config add vdr-video-research \
  --url "https://mcp-test.videodeepresearch.com/mcp" \
  --header "Authorization=Bearer $VDR_MCP_TOKEN" \
  --description "Video Deep Research MCP – TEST" \
  --persist "$HOME/.openclaw/workspace/config/mcporter.json"
```

## Switching back to production

Unset the URL override (or remove it from your shell profile) so the default production URL is used:

```bash
unset VDR_VIDEO_RESEARCH_URL
```

For OpenClaw, re-run the `mcporter config add` command with the production URL (`https://mcp.videodeepresearch.com/mcp`).
