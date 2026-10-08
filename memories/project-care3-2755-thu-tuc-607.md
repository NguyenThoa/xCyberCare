---
name: project-care3-2755-thu-tuc-607
description: "Ticket CARE3-2755 nâng cấp giao diện thủ tục 607 — module thu-tuc-607, prefix TT607, các quyết định đã chốt và việc còn treo (cập nhật 07-10-2026)"
metadata:
  node_type: memory
  type: project
  originSessionId: d394fad8-24f3-48d5-ab04-1f07bb457b23
  modified: 2026-10-06T17:25:31.068Z
---

Ticket CARE3-2755 "[xc100] [xCare] Nâng cấp giao diện thủ tục: 607" (Story, Ready for UAT). Đặc tả duy nhất là Confluence pageId 143492085 (đọc bản 14, sửa 06-10-2026 — trang vẫn đang được sửa). Ticket không có comment.

Bản phân tích đầy đủ: `docs/requirements/thu-tuc-607/analysis/analysis_CARE3-2755.md` (REQ-TT607-01→86, AMB-TT607-01→42, RISK-TT607-01→09; mã kế tiếp REQ-87/AMB-43/RISK-10). Danh mục: `docs/requirements/README.md`. Module do người dùng đặt tên `thu-tuc-607`; prefix `TT607` do agent đặt (người dùng có thể đổi).

Quyết định người dùng chốt trong chat 06-10-2026:
- Tên thủ tục: "607 Cấp lại sổ BHXH do mất, hỏng"
- Cột Quận/huyện chỉ hiển thị giao diện, không có data (đã bỏ cấp huyện)
- Mẫu tờ khai: TK1-TS theo QĐ 490/2023, D01-TS theo QĐ 595/2017
- 5 nút: Lưu tạm, Xem tờ khai, Trình ký, Ký và gửi, Trở lại
- Trở lại → Hủy bỏ/X ở lại màn 607; Đồng ý → về màn hình tạo hồ sơ mới
- Đính kèm: pdf/xml/jpg/xlsx, tối đa 06 file (gồm tờ khai), tổng 5MB
- Trình ký bị chặn khi còn lỗi, hiển thị thông báo lỗi
- D01-TS là tùy chọn
- User đơn vị chỉ dùng tính năng của chính đơn vị mình
- Phụ lục thành viên HGĐ: Xem tờ khai phải đúng thông tin NTG; sửa/sao chép sau khi lưu/ký vẫn hiện đúng dữ liệu đã lưu; NTG không khai TV HGĐ mà tích → Ký và gửi báo lỗi
- KHÔNG test thủ tục 612

**09-10-2026 (đã gộp, theo yêu cầu người dùng):** mục 7.1 tổ chức lại thành 3 bảng — ✅ 22 AMB đã trả lời · ⏳ 18 trả lời một phần · ❔ 2 chưa trả lời (35, 42) — nguồn `File 08-10` / `Chat 09-10`, giữ nguyên văn; câu hỏi lượt 2 B-1…B-22 có dòng `Trả lời:` để người dùng điền. Thêm REQ-TT607-87→106 (mục 4.7); mã kế tiếp REQ-107/AMB-43/RISK-10. Bản sao lưu trước khi gộp ở scratchpad phiên (không trong repo). Chốt mới đáng nhớ: Chỉnh sửa chỉ áp hồ sơ Lưu nháp; Thu hồi → Lưu nháp; Từ chối ký → chỉ Sao chép; giới hạn 5MB tính cả tờ khai; màn hình có thể không có Kỳ kê khai (người dùng đang kiểm).

**Còn treo:** 10 AMB 🔴 (13, 17, 19, 20, 32, 34, 35, 36, 37, 42) — chi tiết ở câu B-x trong mục 7.1. Đã chốt 09-10: prefix TC `CARE3_TT607_TC_001`, môi trường dev dùng chung, QA có quyền API/CSDL (xem [[project-test-env-safety]]). Chưa có test case, chưa có framework automation. Người dùng sẽ tự ra lệnh bước sinh TC (`/generate-testcases-manual-rbt` hoặc `/generate-testcases-from-requirements`).

**Why:** Giữ mạch phân tích giữa các phiên, tránh hỏi lại câu đã trả lời.
**How to apply:** Đọc file phân tích trước khi làm tiếp module này; kiểm tra Confluence có phiên bản mới hơn 14 không. Xem [[project-test-env-safety]], [[feedback-ask-dont-decide]].
