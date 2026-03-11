# Talk to 1M

Search and analyze videos from a corpus of 5M+ videos using natural language queries.

## When to use

Use this skill when the user wants to:
- Search for videos on a topic or theme
- Analyze trends across video content
- Find videos matching specific criteria
- Get insights from video metadata and content analysis

## Instructions

1. Use the `talk_to_1m` MCP tool from the `vdr-video-research` server.
2. Pass the user's question as `user_prompt`.
3. Set `search` to `true` for new searches, or `false` to follow up on previous results.
4. The `s3_path` parameter is optional. Only provide it if the user specifies an S3 path for artifact storage.

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `user_prompt` | Yes | The user's natural language question about videos |
| `search` | No | `true` (default) for fresh search, `false` for follow-up |
| `s3_path` | No | S3 URI for reading/writing artifacts |

### Examples

- "Search videos about how Tesla's FSD technology works and summarize the key findings"
- "What are the most popular cooking techniques shown in recent food videos?"
- "Find videos discussing the impact of AI on software engineering jobs"

### Follow-up queries

After an initial search, set `search` to `false` to ask follow-up questions about the same result set without re-running the search.
