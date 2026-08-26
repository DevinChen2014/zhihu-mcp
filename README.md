# Zhihu MCP

This public listing provides connection metadata and client examples for the hosted SocialDataX Zhihu MCP service. The implementation is privately hosted; this directory contains public connection materials only.

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/zhihu/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/zhihu-insights`
- Future registry name: `com.socialdatax/zhihu-insights`
- Current public capability version: `0.1.0`

## Scope

Use this service for public Zhihu hot-list, content search and detail, creator profiles, creator article lists, top-level comments, and comment replies. It does not provide account login, posting, editing, liking, commenting, following, or other account actions.

## Tools

| Tool | Purpose |
| --- | --- |
| `socialdatax_get_points_balance` | Query the current API Key account balance. |
| `zhihu_get_hot_list` | Read the current hot list. |
| `zhihu_search_content` | Search public answers, articles, and videos; use when a search term is available, and continue with `page_token`. |
| `zhihu_get_content_detail_by_url` | Read answer, article, or independent-video details from a URL. |
| `zhihu_get_user_info_by_profile_url` | Read a creator profile from a profile URL. |
| `zhihu_get_user_posted_articles_by_profile_url` | Read a creator's article list from a profile URL and continue with `page_token`. |
| `zhihu_get_content_comments_by_url` | Read first-level comments from a content URL and continue with `page_token`. |
| `zhihu_get_comment_replies_by_url` | Read replies from a content URL and first-level comment ID. |

When a content URL is already available, use the detail or comment tool instead of searching again. When a first-level comment ID is needed for replies, first use `zhihu_get_content_comments_by_url` and reuse the same content URL.

## Quick Start

Use the hosted endpoint directly when the client supports authenticated `streamable-http`:

```json
{
  "mcpServers": {
    "socialdatax-zhihu": {
      "type": "streamable_http",
      "url": "https://mcp.socialdatax.com/zhihu/mcp",
      "headers": {"Authorization": "Bearer <SOCIALDATAX_API_KEY>"}
    }
  }
}
```

For command/stdio-only clients, use `npx -y mcp-remote https://mcp.socialdatax.com/zhihu/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`. See the files in [examples](examples/).

Request or manage API access at <https://socialdatax.com/ai?from=github>. Never commit a real API Key.
