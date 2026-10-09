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
| `thu-tuc-607` | `TT607` | CARE3-2755 | Đã phân tích (106 REQ, cập nhật 09-10). 2 AMB còn mở (17 🔴 chờ BA, 36 🟡), 40 đã trả lời (gộp lần 4 ngày 09-10); còn câu B-31 ý 3, B-32, B-33→38, B-40, B-41 trong mục 7.1. Chưa sinh test case |

## Chưa chốt

- Đã chốt 09-10: prefix TC ID `CARE3_<MODULE>_TC_<3 số>` (VD `CARE3_TT607_TC_001`, người dùng chọn — không dùng XCARE) · môi trường `dev` **dùng chung** nhưng được Ký và gửi (→ chỉ dùng dữ liệu QA tự tạo, dọn sau khi chạy) · QA "có quyền" gọi API / truy vấn CSDL (chi tiết loại CSDL, chỉ đọc hay ghi: chưa hỏi). Ghi ở `docs/requirements/README.md`
- `.env` (09-10): đã có URL, tài khoản 1, môi trường `dev`, sandbox = yes · ký số không cần điền (chỉ đơn vị tài khoản 1 ký được) · tài khoản 2 (đơn vị khác, chỉ để xem) đã điền 09-10 → `.env` đủ

## Vị trí trên luồng làm việc

`Phân tích ticket ✅` → trả lời AMB 🔴 → sinh test case → `/review-testcases` → dựng framework (chặng 0) → sinh script (chặng 1) …

Chi tiết từng mục: xem [MEMORY.md](MEMORY.md).
