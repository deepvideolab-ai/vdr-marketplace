# VideoClaw

Query the video database to find, count, and analyze video records by various criteria.

## When to use

Use this skill when the user wants to:
- Look up a specific video by its document ID, creator ID, or URL
- Count videos by platform (e.g. TikTok, YouTube, Instagram)
- Count videos by a specific creator
- Find videos longer than a certain duration
- Run flexible queries against the video database
- Get raw video metadata or statistics

## Instructions

1. Use the `videoclaw` MCP tool from the `vdr-video-research` server.
2. Choose the appropriate `action` based on what the user needs.
3. Provide the required parameters for the chosen action.

### Actions

| Action | Required Params | Description |
|--------|----------------|-------------|
| `search_by_id` | `id` | Find a video by its document ID |
| `search_by_creator_id` | `creator_id` | Find videos by a creator's ID |
| `search_by_url` | `url` | Find a video by its URL |
| `search_by_duration` | `min_duration` | Find videos longer than N seconds |
| `count_by_uid_prefix` | `uid_prefix` | Count videos by platform prefix (e.g. `tiktok_`, `youtube_`) |
| `count_by_creator_id` | `creator_id` | Count videos by a creator |
| `search` | `query_json` | Flexible search with a JSON query body |
| `count` | `query_json` | Count results for a flexible JSON query |

### Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `action` | Yes | One of the action names above |
| `id` | For search_by_id | Document ID |
| `creator_id` | For search/count_by_creator_id | Creator identifier |
| `url` | For search_by_url | Video URL |
| `min_duration` | For search_by_duration | Minimum duration in seconds |
| `before_date` | No | Upper date bound (exclusive), for search_by_duration |
| `after_date` | No | Lower date bound (inclusive), for search_by_duration |
| `date_field` | No | Date field to filter on (default: `release_time`) |
| `uid_prefix` | For count_by_uid_prefix | UID prefix string (e.g. `tiktok_`) |
| `query_json` | For search/count | Raw JSON query string |
| `max_results` | No | Max results for search_by_duration (default: 100, max: 10000) |
| `size` | No | Result size for search action (default: 10, max: 10000) |
| `source_fields` | No | List of fields to return for search action |
| `index` | No | Video index to query (default: `video_deep_research`) |

### Examples

- "How many TikTok videos do we have?" → action: `count_by_uid_prefix`, uid_prefix: `tiktok_`
- "Find the video with ID abc123" → action: `search_by_id`, id: `abc123`
- "How many videos does creator X have?" → action: `count_by_creator_id`, creator_id: `X`
- "Find videos longer than 10 minutes" → action: `search_by_duration`, min_duration: `600`
- "Look up this video URL" → action: `search_by_url`, url: `https://...`
