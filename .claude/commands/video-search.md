# /video-search

Search and analyze videos from a 5M+ video library using AI-powered deep research.

## Important

- If you need to check whether `VDR_MCP_TOKEN` is set, use `env | grep VDR_MCP_TOKEN` instead of `echo $VDR_MCP_TOKEN`. The `echo` approach does not work reliably in this environment.

## Prerequisites

Before calling any tools, check if the `talk_to_1m` tool is available. If it is not available, the plugin is not installed. Guide the user to install it:

1. Add the marketplace: `claude plugin marketplace add deepvideolab-ai/vdr-plugins`
2. Install the plugin: `claude plugin install vdr-video-research@vdr-tools`
3. Restart Claude Code to load the plugin

Then check if `VDR_MCP_TOKEN` is set using `env | grep VDR_MCP_TOKEN`. If not set, tell the user to set it:

```
export VDR_MCP_TOKEN=<your-token>
```

Only proceed with the search after both the plugin and token are confirmed.

## How It Works

1. Call the `talk_to_1m` tool directly with the user's query and `search: true`
2. Analyze results for key findings, patterns, and trends
3. Present a structured summary with evidence from video content
4. For follow-up questions, call `talk_to_1m` again with `search: false`

## Tools

| Tool | Purpose |
|------|---------|
| `talk_to_1m` | Search and analyze general video content |
| `talk_to_ads` | Search and analyze advertising/commercial video content |
| `deep_research` | In-depth multi-step research across video library |
| `direct_ask` | Direct questions without search context |

## Usage

/video-search $ARGUMENTS

## Examples

/video-search latest trends in electric vehicles
/video-search fashion trends in 2026 spring collections
/video-search competitor ad strategies for fitness apps

## Install

Part of the [VDR Video Research](https://github.com/deepvideolab-ai/vdr-plugins) plugin:

```
/plugin marketplace add deepvideolab-ai/vdr-plugins
/plugin install vdr-video-research@vdr-tools
```
