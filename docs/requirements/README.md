# Danh mục Requirements — xCare (CyberCare v3)

> Điểm vào cấp hệ thống. Đọc file này **trước** khi gán mã REQ hoặc đặt prefix cho module mới.
> Dự án chưa chạy `/discover-system` — chưa có `_discovery/system_map.md`.

## Thuộc tính dự án

| Thuộc tính | Giá trị |
|---|---|
| Hệ thống | xCare — thủ tục Bảo hiểm xã hội · Jira project `CARE3` · Confluence space `CARE3` |
| Prefix TC ID | ✅ `CARE3_<MODULE>_TC_<3 số>` — VD `CARE3_TT607_TC_001` (người dùng chốt 09-10). Dùng cố định cho mọi module, KHÔNG đổi giữa chừng |
| Môi trường dùng chung? | ✅ **Có** — môi trường `dev` dùng chung nhưng **được phép Ký và gửi** (Chat 09-10). Bật quy tắc: chỉ dùng dữ liệu do QA tạo (tên truy vết được), dọn dữ liệu test sau khi chạy, không thao tác phá huỷ trên dữ liệu người khác |
| Năng lực kiểm thử của QA (gọi API · truy vấn CSDL · xem nhật ký) | ✅ CSDL **Oracle**, truy cập bằng Navicat Premium, **chỉ đọc** (không sửa / xóa gì) · API: chỉ bắt request trên trình duyệt (không có Swagger / Postman) · **không xem được** log hệ thống (Chat 09-10). Trang chủ xCare có khung "Nhật ký hoạt động" — chưa rõ có tính là nhật ký không (B-41) |
| URL · tài khoản test | Lưu trong `.env` (đã `.gitignore`) — **không** ghi vào `docs/` |

## 1. Bảng danh mục module

| Module | Prefix | Nền tảng | Trạng thái recon | Mức phủ tài liệu | Tài liệu | REQ đã dùng | Mã kế tiếp | AMB treo | Story | Cập nhật |
|---|---|---|---|---|---|---|---|---|---|---|
| thu-tuc-607 | `TT607` | Web ⬜ | ⬜ Chưa khảo sát UI | Có đặc tả Confluence 143492085 (bản 14) | [analysis/analysis_CARE3-2755.md](thu-tuc-607/analysis/analysis_CARE3-2755.md) | REQ-TT607-01 → 106 (ticket CARE3-2755) | REQ-TT607-107 · AMB-TT607-43 · RISK-TT607-10 | 20 (🔴 10) | — | 09-10-2026 |

**Prefix đã chiếm:** `TT607` · `SYS` (dành riêng cho AMB/RISK cấp hệ thống)

## 2. Trạng thái REQ toàn hệ thống

| Module | Tổng REQ | Ghi chú |
|---|---|---|
| thu-tuc-607 | 106 | Sinh từ phân tích ticket + câu trả lời AMB (08 → 09-10), chưa kiểm chứng trên UI |

## 3. Ambiguity 🔴 High còn treo

| Module | Mã |
|---|---|
| thu-tuc-607 | AMB-TT607-13 · 17 · 19 · 20 · 32 · 34 · 35 · 36 · 37 · 42 (câu hỏi lượt 2: B-1 → B-21) |

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
| 09-10-2026 | `thu-tuc-607`: thêm REQ-TT607-87 → 106 từ câu trả lời AMB; AMB treo 31 → 20 (🔴 11 → 10, đóng AMB-TT607-33) |
| 09-10-2026 | Thuộc tính dự án: môi trường `dev` dùng chung nhưng được Ký và gửi · QA có quyền gọi API / truy vấn CSDL |
| 09-10-2026 | Chốt năng lực kiểm thử (B-22): Oracle chỉ đọc qua Navicat · API qua request trình duyệt · không xem log |
| 09-10-2026 | Chốt prefix TC ID `CARE3_<MODULE>_TC_<3 số>` (VD `CARE3_TT607_TC_001`) |
