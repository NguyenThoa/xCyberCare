# prompts/ — Copy-paste prompt templates

32 prompt template từ Claude Testing Kit v2 (bộ `claude-testing-skills-main`).

**Cách dùng:** mở file → copy nội dung → thay `[...]` bằng data thật → paste vào Claude Code.

## Danh sách (theo thứ tự workflow QA)

### Discover / Requirements (0-1, 20-21, 29-30)
- `prompt_00_discover_system.txt` — explore app, discover modules
- `prompt_01_generate_requirements.txt` — từ website UI
- `prompt_20_analyze_requirement_document.txt` — phân tích Jira/.docx
- `prompt_21_update_requirements_from_ticket.txt` — update REQ theo ticket
- `prompt_29_generate_requirements_from_api.txt` — từ Swagger/OpenAPI
- `prompt_30_generate_requirements_from_mobile.txt` — từ app mobile

### Test cases (2, 22, 15, 13, 12)
- `prompt_02_generate_test_cases.txt` — FULL RBT 6 bước
- `prompt_22_generate_testcases_quick.txt` — QUICK mode
- `prompt_15_generate_checklist.txt` — sinh checklist test
- `prompt_13_generate_traceability_matrix.txt` — matrix REQ↔TC↔Bug
- `prompt_12_review_testcases.txt` — review TC theo checklist

### Test data / API mock (7, 14)
- `prompt_07_generate_test_data.txt`
- `prompt_14_generate_api_mocks.txt`

### Automation framework (3, 6)
- `prompt_03_create_framework_{playwright,selenium,appium}.txt`
- `prompt_06_review_automation_code.txt`

### Automation script (4, 5, 9, 26, 31)
- `prompt_04_generate_script_{playwright,selenium}.txt`
- `prompt_05_convert_manual_to_automation.txt`
- `prompt_09_generate_api_tests.txt`
- `prompt_26_generate_automation_mobile_flow.txt`
- `prompt_31_generate_automation_api.txt`

### Execute / Run / Heal (16, 17, 18, 23)
- `prompt_16_execute_test_cases.txt` — chạy manual TC
- `prompt_17_run_and_fix_tests.txt` — chạy + auto fix
- `prompt_18_heal_locators.txt` — sửa locator hỏng
- `prompt_23_retest_fixed_bugs.txt`

### Bug / Report (10, 11, 24)
- `prompt_10_create_bug_report.txt`
- `prompt_11_analyze_test_report.txt`
- `prompt_24_generate_test_summary_report.txt`

### Impact analysis (19, 27) — rất hữu ích cho project đã có nhiều TC
- `prompt_19_update_automation_from_impact.txt`
- `prompt_27_update_testcases_from_impact.txt`

### Meta (8, 25, 28)
- `prompt_08_analyze_flaky_tests.txt`
- `prompt_25_generate_master_test_plan.txt`
- `prompt_28_generate_user_guide.txt`

## Nguồn

`claude-testing-skills-main.zip` (CyberTech kit v2, 2026-09).
