# Zhihu MCP Directory Submission Checklist

<!-- release-status:start -->
## Recorded release status

- Local metadata: `0.1.3` with 13 tracked tools. Local metadata alone does not establish publication.
- Hosted production: `0.1.3` with 13 tools; recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Official MCP Registry: `0.1.3` (`active`); recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Registry evidence: [version-specific Registry record](https://registry.modelcontextprotocol.io/v0.1/servers/com.52choujiang%2Fzhihu-insights/versions/0.1.3).
- These are recorded observations, not a fresh live check. Public GitHub, npm, and other distribution channels require their own verification.
<!-- release-status:end -->

## Metadata

- Registry name: `com.52choujiang/zhihu-insights`
- Future registry name: `com.socialdatax/zhihu-insights`
- Endpoint: `https://mcp.socialdatax.com/zhihu/mcp`
- Auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Transport: hosted `streamable-http`; command/stdio fallback uses `mcp-remote`
- License: MIT for public documentation and configuration examples only
- Product: `SocialDataX` / `社媒数据助手`
- current 13 public tools are listed in `server-card.json`.

## Safety and publication checks

- No real API Key, private backend code, production configuration, internal sample, or account data is present.
- The hosted card must expose `zhihu_search_content`, `zhihu_get_content_detail_by_url`, `zhihu_get_content_comments_by_url`, `zhihu_get_user_info_by_profile_url`, `zhihu_submit_video_speech_text_by_video_url`, `zhihu_submit_video_speech_text_by_zvideo_id`, and `zhihu_get_video_speech_text_job`.
- Search and list calls pass the opaque `page_token` returned by the service for continuation.
- `examples/codex_config.toml` uses `bearer_token_env_var = "SOCIALDATAX_API_KEY"`.
- `examples/cursor_mcp.json` uses the remote URL and `${env:SOCIALDATAX_API_KEY}`.
- `mcp.json` and `examples/claude_desktop_config.json` are explicit `mcp-remote` fallbacks.
- Validate JSON and the official Registry file before submission; do not treat a hosted server card as a Registry publication.

## Required files

`README.md`, `LICENSE`, `server-card.json`, `mcp.json`, `glama.json`, all files under `examples/`, and `assets/logo.png`.

本地 `0.1.3` 候选新增 `zhihu_search_users`（用户搜索，支持 `page_token`）与 `zhihu_search_suggestions`（搜索联想，不分页）。尚未部署或发布 Registry，发布后需复验。
