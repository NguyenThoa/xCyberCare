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

**09-10-2026 (gộp lần 3, theo yêu cầu người dùng):** 10 AMB (13, 14, 15, 20, 23, 24, 26, 29, 31, 34) chuyển sang ✅ → 32 đã trả lời · 8 một phần · 2 chưa trả lời. Chốt mới: 607 KHÔNG có Kỳ kê khai (REQ-02/03/04 chờ người dùng bảo chuyển Deprecated — REQ chưa sửa); Xem tờ khai báo lỗi thì không mở preview, Lưu tạm không validate; tờ khai không hiện thành dòng đính kèm nhưng cộng vào tổng dung lượng; lỗi phụ lục HGĐ dạng Toast; chuyển cùng NTG 2 lần tạo 2 dòng; hiệu năng 50/100 NTG chỉ cần không treo/lỗi (QA tự đo). Bản sao lưu ở scratchpad phiên.

**09-10-2026 (gộp lần 4):** 8 AMB (18, 19, 28, 32, 35, 37, 38, 42) sang ✅ → 40 đã trả lời · 2 một phần (17 chờ BA, 36) · 0 chưa trả lời; khảo sát web xong (xem [[reference-xcare-dev-site]]). Chốt mới: Back / đóng tab không có popup (REQ-85/86 chờ xác nhận Deprecated, câu B-25); D01-TS chỉ thêm NTG đã có ở TK1-TS; Sao chép điền sẵn form ở màn Tạo hồ sơ (chưa lưu); mọi trường TK1-TS giữ dữ liệu tại lúc lưu/ký; Oracle chỉ đọc, API qua request trình duyệt, không xem log. REQ-02/03/04 và 85/86 đã Deprecated (09-10, người dùng xác nhận).

**(Cũ, trước gộp lần 4) Còn treo:** 6 AMB 🔴 (17, 32, 35, 36, 37, 42) · câu mới B-3b, B-5b, B-7, B-16 · B-10 là việc kiểm môi trường dev (hồ sơ 607 giao diện cũ) · B-18→B-22 chưa trả lời. Đã chốt 09-10: prefix TC `CARE3_TT607_TC_001`, môi trường dev dùng chung, QA có quyền API/CSDL (xem [[project-test-env-safety]]). Chưa có test case, chưa có framework automation. Người dùng sẽ tự ra lệnh bước sinh TC (`/generate-testcases-manual-rbt` hoặc `/generate-testcases-from-requirements`).

**Why:** Giữ mạch phân tích giữa các phiên, tránh hỏi lại câu đã trả lời.
**How to apply:** Đọc file phân tích trước khi làm tiếp module này; kiểm tra Confluence có phiên bản mới hơn 14 không. Xem [[project-test-env-safety]], [[feedback-ask-dont-decide]].
