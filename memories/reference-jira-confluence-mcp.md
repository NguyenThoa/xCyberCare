---
name: reference-jira-confluence-mcp
description: Đọc Jira/Confluence của Cybertech qua MCP jira-cybertech (repo không có scripts/integrations)
metadata:
  node_type: memory
  type: reference
  originSessionId: d394fad8-24f3-48d5-ab04-1f07bb457b23
  modified: 2026-10-06T17:25:40.768Z
---

- Jira: https://jira.cybertech.vn (project CARE3) · Confluence: https://conf.cybertech.vn (space CARE3 "CyberCare v3").
- Truy cập bằng MCP server `jira-cybertech` (các tool `jira_get_issue`, `confluence_get_page`, `confluence_download_attachment`…). Lệnh `/fetch-jira-requirements` nhắc tới `scripts/integrations/jira/jira_fetcher.js` nhưng thư mục đó **không tồn tại** trong repo.
- `confluence_get_attachments` trả kết quả quá lớn; danh sách attachment đã có sẵn trong metadata của `confluence_get_page`. Xem ảnh bằng `confluence_download_attachment` theo id.
- Người dùng muốn được hỏi trước khi dùng MCP này (lần đầu đã từ chối, sau đó chọn "Dùng MCP jira-cybertech" — chỉ đọc, không ghi lên Jira/Confluence).
