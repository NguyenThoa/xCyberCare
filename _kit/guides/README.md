# Kit Guides — Reference từ Claude Testing Kit v2

3 file guide gốc từ bộ `claude-testing-skills-main.zip` (Anh Tester kit, phiên bản mới). Copy vào đây để tham chiếu workflow chuẩn, **KHÔNG override** các convention riêng của xCyberCare.

## Files

| File | Nội dung |
|---|---|
| [AI_FULL_FLOW_AUTOMATION.md](AI_FULL_FLOW_AUTOMATION.md) | Flow end-to-end AI-assisted automation: từ discover system → requirements → TC → auto → execute → report |
| [AI_FULL_FLOW_MANUAL.md](AI_FULL_FLOW_MANUAL.md) | Flow manual testing đầy đủ, dùng AI-RBT + execute + report |
| [SETUP_CLAUDE.md](SETUP_CLAUDE.md) | Setup Claude Code cho dự án QA từ đầu |

## Khi nào dùng

- Cần workflow chuẩn cho task chưa quen → mở guide tương ứng để tham chiếu.
- Setup dự án khác dùng kit này → đọc `SETUP_CLAUDE.md`.
- Onboarding người mới vào team QA sử dụng Claude Code → gửi họ đọc 3 file này.

## Quan hệ với xCyberCare

- xCyberCare có convention riêng (JUnit 5, format v2/v3, prefix TC ID, docs/requirements per-module) — nếu guide xung đột thì **theo convention xCyberCare**.
- xCyberCare CLAUDE.md ở root project override một số điểm của kit gốc — tham chiếu file đó trước.

## Nguồn gốc

Zip: `claude-testing-skills-main.zip` (Anh Tester, 2026-09).
