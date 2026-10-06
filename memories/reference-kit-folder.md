---
name: reference-kit-folder
description: "_kit/ là tài liệu cho người đọc (guides + 32 prompt), không phải skill; link nội bộ trong guides bị hỏng; dòng 21 guides/README cố ý để nguyên"
metadata:
  node_type: memory
  type: reference
  originSessionId: d394fad8-24f3-48d5-ab04-1f07bb457b23
  modified: 2026-10-06T17:25:46.417Z
---

- Skill/command/rules của bộ kit nằm ở `.claude/` (21 skill, 39 command, 6 rules) — Claude Code tự nạp. `_kit/` chỉ gồm `guides/` (AI_FULL_FLOW_AUTOMATION.md, AI_FULL_FLOW_MANUAL.md, SETUP_CLAUDE.md) và `prompts/` (prompt_00…31) để người copy-paste.
- 07-10-2026: đổi "Partner Hub" (tên dự án cũ) → "xCyberCare" trong `_kit/README.md` và `_kit/guides/README.md`. Dòng 21 của `_kit/guides/README.md` vẫn ghi convention cũ (JUnit 5, format v2/v3) — người dùng bảo "tạm thời cứ để lại"; chỉ sửa khi đã chốt convention xCyberCare.
- Link trong `_kit/guides/*.md` hỏng (`prompts/…`, `.claude/rules/…` tương đối từ guides/; `plans/`, `scripts/` không tồn tại). Đã đề nghị sửa, người dùng chưa trả lời.
- Theo AI_FULL_FLOW_AUTOMATION, automation chỉ bắt đầu khi có bộ TC đã `/review-testcases`; xCyberCare chưa tới đó (xem [[project-care3-2755-thu-tuc-607]]). Stack dự kiến: Playwright + TypeScript.
