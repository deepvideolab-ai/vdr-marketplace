# Ad Analysis

Search and analyze ad videos for marketing insights, creative strategies, and competitive analysis.

## When to use

Use this skill when the user wants to:
- Find ad videos for specific products, brands, or industries
- Analyze advertising creative strategies
- Research competitor ad campaigns
- Understand marketing trends in video advertising

## Instructions

1. Use the `talk_to_ads` MCP tool from the `vdr-video-research` server.
2. Pass the user's question as `user_prompt`.
3. Set `search` to `true` for new searches, or `false` to follow up on previous results.
4. The `s3_path` parameter is optional. Only provide it if the user specifies an S3 path for artifact storage.

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `user_prompt` | Yes | The user's natural language question about ad videos |
| `search` | No | `true` (default) for fresh search, `false` for follow-up |
| `s3_path` | No | S3 URI for reading/writing artifacts |

### Examples

- "Find ad videos for skincare products targeting Gen Z audiences"
- "What creative strategies are beauty brands using in their recent video ads?"
- "Show me ads that use humor to sell fitness products"
- "Analyze competitor video ad strategies for the fitness industry"

### Follow-up queries

After an initial search, set `search` to `false` to ask follow-up questions about the same ad result set without re-running the search.
