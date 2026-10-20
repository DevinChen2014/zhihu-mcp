# Zhihu MCP

LobeHub 用户请使用 [LobeHub setup / 接入说明](LOBEHUB.md)，包含专属官网入口、认证和来源配置。

This public listing provides connection metadata and client examples for the hosted SocialDataX Zhihu MCP service. The implementation is privately hosted; this directory contains public connection materials only.

<!-- release-status:start -->
## Recorded release status

- Local metadata: `0.1.3` with 13 tracked tools. Local metadata alone does not establish publication.
- Hosted production: `0.1.3` with 13 tools; recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Official MCP Registry: `0.1.3` (`active`); recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Registry evidence: [version-specific Registry record](https://registry.modelcontextprotocol.io/v0.1/servers/com.52choujiang%2Fzhihu-insights/versions/0.1.3).
- These are recorded observations, not a fresh live check. Public GitHub, npm, and other distribution channels require their own verification.
<!-- release-status:end -->

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/zhihu/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/zhihu-insights`
- Future registry name: `com.socialdatax/zhihu-insights`

## Scope

Use this service for public Zhihu hot-list, content search and detail, creator profiles, creator article lists, top-level comments, comment replies, and speech-to-text for independent videos and video answers. Plain answers without video are not processable transcript inputs. It does not provide account login, posting, editing, liking, commenting, following, or other account actions.

## Tools

| Tool | Purpose |
| --- | --- |
| `zhihu_search_users` | Search users by keyword; supports opaque `page_token` continuation. |
| `zhihu_search_suggestions` | Get search-box suggestions for a keyword; no pagination. |
| `socialdatax_get_points_balance` | Query the current API Key account's SocialDataX points balance / 积分余额、剩余积分或点数. |
| `zhihu_get_hot_list` | Read the current hot list. |
| `zhihu_search_content` | Search public answers, articles, and videos; use when a search term is available, and continue with `page_token`. |
| `zhihu_get_content_detail_by_url` | Read answer, article, or independent-video details from a URL. |
| `zhihu_get_user_info_by_profile_url` | Read a creator profile from a profile URL. |
| `zhihu_get_user_posted_articles_by_profile_url` | Read a creator's article list from a profile URL and continue with `page_token`. |
| `zhihu_get_content_comments_by_url` | Read first-level comments from a content URL and continue with `page_token`. |
| `zhihu_get_comment_replies_by_url` | Read replies from a content URL and first-level comment ID. |
| `zhihu_submit_video_speech_text_by_video_url` | Submit speech-to-text from an independent `/zvideo/{zvideo_id}` page or a video-answer page URL. |
| `zhihu_submit_video_speech_text_by_zvideo_id` | Submit an independent-video speech-to-text job from a numeric `zvideo_id`. |
| `zhihu_get_video_speech_text_job` | Continue querying the same independent-video or video-answer speech-to-text job ID until terminal. |

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

本地 `0.1.3` 候选新增 `zhihu_search_users`（用户搜索，支持 `page_token`）与 `zhihu_search_suggestions`（搜索联想，不分页）。尚未部署或发布 Registry，发布后需复验。

用户搜索结果还包含累计赞同数 `received_upvote_count`、回答数 `answer_count`、文章数 `article_count`、平台创作总数 `creation_count` 和最近创作时间 `last_creation_time`（秒级 Unix 时间戳）；不可用时为 null。创作总数不通过回答数与文章数相加计算。

搜索建议返回 `text`、`label` 和 `icon_url`；后两项不可用时为 null。`label` 保留平台标记，不承诺完整分类枚举；`icon_url` 用于建议展示。

## Gemini CLI extension

Install this service from its public GitHub repository:

```sh
gemini extensions install https://github.com/DevinChen2014/zhihu-mcp
```

When prompted, enter your own `SOCIALDATAX_API_KEY`. Get a key from [SocialDataX](https://socialdatax.com/ai?from=github); business tool calls consume SocialDataX credits. The extension connects directly to the existing hosted MCP endpoint and does not include the private service implementation.

Verify the connection with `gemini mcp list`. To change the saved key, run:

```sh
gemini extensions config socialdatax-zhihu
```
