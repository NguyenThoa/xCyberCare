# Danh mục Requirements — xCare (CyberCare v3)

> Điểm vào cấp hệ thống. Đọc file này **trước** khi gán mã REQ hoặc đặt prefix cho module mới.
> Dự án chưa chạy `/discover-system` — chưa có `_discovery/system_map.md`.

## Thuộc tính dự án

| Thuộc tính | Giá trị |
|---|---|
| Hệ thống | xCare — thủ tục Bảo hiểm xã hội · Jira project `CARE3` · Confluence space `CARE3` |
| Prefix TC ID | ❔ Chưa chốt — xác nhận với user trước lần sinh test case đầu tiên |
| Môi trường dùng chung? | ❔ Chưa hỏi |
| Năng lực kiểm thử của QA (gọi API · truy vấn CSDL · xem nhật ký) | ❔ Chưa hỏi |
| URL · tài khoản test | Lưu trong `.env` (đã `.gitignore`) — **không** ghi vào `docs/` |

## 1. Bảng danh mục module

| Module | Prefix | Nền tảng | Trạng thái recon | Mức phủ tài liệu | Tài liệu | REQ đã dùng | Mã kế tiếp | AMB treo | Story | Cập nhật |
|---|---|---|---|---|---|---|---|---|---|---|
| thu-tuc-607 | `TT607` | Web ⬜ | ⬜ Chưa khảo sát UI | Có đặc tả Confluence 143492085 (bản 14) | [analysis/analysis_CARE3-2755.md](thu-tuc-607/analysis/analysis_CARE3-2755.md) | REQ-TT607-01 → 86 (ticket CARE3-2755) | REQ-TT607-87 · AMB-TT607-43 · RISK-TT607-10 | 31 (🔴 11) | — | 06-10-2026 |

**Prefix đã chiếm:** `TT607` · `SYS` (dành riêng cho AMB/RISK cấp hệ thống)

## 2. Trạng thái REQ toàn hệ thống

| Module | Tổng REQ | Ghi chú |
|---|---|---|
| thu-tuc-607 | 86 | Sinh từ phân tích ticket, chưa kiểm chứng trên UI |

## 3. Ambiguity 🔴 High còn treo

| Module | Mã |
|---|---|
| thu-tuc-607 | AMB-TT607-13 · 17 · 19 · 20 · 32 · 33 · 34 · 35 · 36 · 37 · 42 |

## 4. Cấu trúc thư mục chuẩn

```
docs/requirements/
├── README.md                                   ← file này
├── _discovery/                                 ← chưa có
└── <module>/
    ├── REQUIREMENTS_<TÊN_MODULE>_SUMMARY.md    ← index module (chưa có cho thu-tuc-607)
    ├── web/ · mobile/ · api/
    ├── analysis/analysis_<TICKET-ID>.md
    └── impact/impact_<TICKET-ID>.md
```

## 5. Quy trình sử dụng

| Tình huống | Workflow | Ghi vào |
|---|---|---|
| Phân tích ticket mới | `/analyze-requirement-document` | `<module>/analysis/` |
| Recon UI module | `/generate-requirements-from-website` | `<module>/REQUIREMENTS_<TÊN_MODULE>_SUMMARY.md` + `web/` |
| Ticket đổi requirement đã có | `/update-requirements-from-ticket` | `<module>/impact/` |

## 6. Nhật ký danh mục

| Ngày | Thay đổi |
|---|---|
| 06-10-2026 | Khởi tạo danh mục. Thêm module `thu-tuc-607` (prefix `TT607`) từ ticket CARE3-2755 |
