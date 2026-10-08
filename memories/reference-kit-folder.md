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
- 08-10-2026: đã sửa 89 link tương đối trong `_kit/guides/AI_FULL_FLOW_*.md` (thêm `../` cho `prompts/`, `../../` cho `.claude/` và `CLAUDE.md`) theo yêu cầu người dùng. Nếu sau này chuyển guides ra gốc repo / chép đè bộ kit gốc thì các link này lại phải bỏ tiền tố.
- 08-10-2026: đổi chữ "Anh Tester" → "CyberTech" trong `_kit/` (7 chỗ). Người dùng chốt GIỮ NGUYÊN mọi URL/tên miền/đường dẫn `anhtester` và trích dẫn tác giả bài viết trong `.claude/skills/skills-rbt-manual-testing/references/automation_criteria.md` dòng 3.
- Còn 5 link trỏ tới `plans/` và `scripts/` — hai thư mục không có trong repo (CLAUDE.md cũng nhắc tới). Người dùng chưa chọn: cấp thư mục từ bộ kit gốc / bỏ link / để nguyên.
- Theo AI_FULL_FLOW_AUTOMATION, automation chỉ bắt đầu khi có bộ TC đã `/review-testcases`; xCyberCare chưa tới đó (xem [[project-care3-2755-thu-tuc-607]]). Stack dự kiến: Playwright + TypeScript.
