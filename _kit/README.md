# _kit/ — Kit reference (dùng chung, không thuộc riêng project)

> **Mục đích:** Tách biệt **kiến thức áp dụng chung** (kit của Anh Tester + prompt templates) ra khỏi `docs/` (kiến thức riêng của xCyberCare).

Prefix `_` để folder này sort lên đầu trong file explorer, dễ tìm.

## Structure

```
_kit/
├── README.md                    ← file này
├── guides/                      ← 3 workflow guide từ kit v2
│   ├── AI_FULL_FLOW_AUTOMATION.md   (25KB) — flow end-to-end automation
│   ├── AI_FULL_FLOW_MANUAL.md       (28KB) — flow manual testing
│   └── SETUP_CLAUDE.md              (39KB) — setup Claude Code cho dự án QA
└── prompts/                     ← 32 prompt template (prompt_00..31)
    ├── README.md
    ├── prompt_00_discover_system.txt
    ├── prompt_01_generate_requirements.txt
    ├── ...
    └── prompt_31_generate_automation_api.txt
```

## Quan hệ với các folder khác

| Folder | Nội dung | Scope |
|---|---|---|
| `.claude/` | Rules + skills + commands + settings (auto-load bởi Claude Code) | Kit chung — Claude Code sử dụng |
| **`_kit/`** | Guides + prompts (con người tham chiếu / copy-paste) | Kit chung — dev/QA sử dụng |
| `docs/` | Requirements + testcases + conventions | **RIÊNG xCyberCare** |

Nguyên tắc: nếu 1 file **áp dụng được cho mọi dự án QA khác** → `_kit/` hoặc `.claude/`. Nếu file **chỉ có ý nghĩa cho xCyberCare** (nói tên hệ thống, module, prefix cụ thể) → `docs/`.

## Nguồn gốc

- `guides/` — từ `claude-testing-skills-main.zip` (Anh Tester kit v2, 2026-09).
- `prompts/` — từ `claude-testing-skills-main.zip` (kit v2, có 32 template — nhiều hơn kit v1).

## Khi mang sang dự án mới

Copy nguyên folder `_kit/` sang project khác dùng lại — không cần sửa gì (không hardcode xCyberCare).
