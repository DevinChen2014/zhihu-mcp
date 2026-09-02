# Zhihu MCP Directory Submission Checklist

## Metadata

- Registry name: `com.52choujiang/zhihu-insights`
- Future registry name: `com.socialdatax/zhihu-insights`
- Version: `0.1.2`
- Endpoint: `https://mcp.socialdatax.com/zhihu/mcp`
- Auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Transport: hosted `streamable-http`; command/stdio fallback uses `mcp-remote`
- License: MIT for public documentation and configuration examples only
- Product: `SocialDataX` / `社媒数据助手`
- current 11 public tools are listed in `server-card.json`.

## Safety and publication checks

- No real API Key, private backend code, production configuration, internal sample, or account data is present.
- `server-card.json` and `registry/zhihu/server.json` use public capability version `0.1.2` and the same endpoint.
- The hosted server card is live at `0.1.2` with 11 tools. The official Registry latest remains `0.1.0` until publication; verify the public repository sync and Registry publication as separate steps.
- The hosted card must expose `zhihu_search_content`, `zhihu_get_content_detail_by_url`, `zhihu_get_content_comments_by_url`, `zhihu_get_user_info_by_profile_url`, `zhihu_submit_video_speech_text_by_video_url`, `zhihu_submit_video_speech_text_by_zvideo_id`, and `zhihu_get_video_speech_text_job`.
- Search and list calls pass the opaque `page_token` returned by the service for continuation.
- `examples/codex_config.toml` uses `bearer_token_env_var = "SOCIALDATAX_API_KEY"`.
- `examples/cursor_mcp.json` uses the remote URL and `${env:SOCIALDATAX_API_KEY}`.
- `mcp.json` and `examples/claude_desktop_config.json` are explicit `mcp-remote` fallbacks.
- Validate JSON and the official Registry file before submission; do not treat a hosted server card as a Registry publication.

## Required files

`README.md`, `LICENSE`, `server-card.json`, `mcp.json`, `glama.json`, all files under `examples/`, and `assets/logo.png`.
