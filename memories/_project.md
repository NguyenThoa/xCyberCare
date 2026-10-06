# Tổng quan dự án xCyberCare

> Cập nhật: 07-10-2026

| Mục | Nội dung |
|---|---|
| Hệ thống | xCare / CyberCare v3 — hệ thống làm thủ tục Bảo hiểm xã hội |
| Jira / Confluence | Project `CARE3` trên jira.cybertech.vn · space `CARE3` trên conf.cybertech.vn — đọc qua MCP `jira-cybertech` |
| Stack test dự kiến | Playwright + TypeScript (chưa dựng framework) |
| Bộ kit | `.claude/` (21 skill, 39 command, 6 rules — Claude Code tự nạp) · `_kit/` (guides + 32 prompt cho người đọc) |
| Quy tắc dự án | `CLAUDE.md` ở gốc repo |

## Module đang làm

| Module | Prefix | Ticket | Trạng thái |
|---|---|---|---|
| `thu-tuc-607` | `TT607` | CARE3-2755 | Đã phân tích (86 REQ). Chờ trả lời 11 AMB 🔴, chưa sinh test case |

## Chưa chốt

- Prefix TC ID
- Môi trường test có dùng chung không
- QA có quyền gọi API / truy vấn CSDL không
- `.env` chưa điền URL và tài khoản

## Vị trí trên luồng làm việc

`Phân tích ticket ✅` → trả lời AMB 🔴 → sinh test case → `/review-testcases` → dựng framework (chặng 0) → sinh script (chặng 1) …

Chi tiết từng mục: xem [MEMORY.md](MEMORY.md).
