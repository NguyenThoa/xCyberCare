---
name: reference-xcare-dev-site
description: "Bản đồ site dev-care.xcyber.vn (route, đăng nhập SSO, trạng thái hồ sơ) và lưu ý DOM cho locator — khảo sát 09-10-2026"
metadata:
  node_type: memory
  type: reference
---

- URL gốc lấy từ `.env`; chưa đăng nhập thì chuyển sang SSO `stg-accounts.xcyber.vn` (Keycloak, realm cyberid). Agent **không nhập mật khẩu** (không phải máy cục bộ) → người dùng tự đăng nhập trong cửa sổ Playwright rồi agent khảo sát tiếp. Phiên đăng nhập có thể mất khi đóng cửa sổ.
- Route đã thấy: `/procedures` (danh sách, tab Hệ thống mới / Hệ thống cũ) · `/create-new-profile` (chọn thủ tục; 607 nằm trong **Lĩnh vực số thẻ**) · `/create-profile?procedureCode=607` (form). Nhấn đúp dòng hồ sơ mở bảng "Kết quả tiếp nhận và xử lý hồ sơ".
- Trạng thái hồ sơ trên danh sách: Lưu Nháp · Trình ký · Gửi thành công, BHXH đang xử lý · Ký lỗi · BHXH từ chối (mã lỗi cổng dạng `CE047`).
- Gói dịch vụ tài khoản test (CARE-B-1Y-T100) **hết hạn 13-10-2026** — hỏi người dùng đã gia hạn chưa trước khi lên lịch chạy Ký và gửi.
- Lưu ý locator (chỉ ghi nhận khi recon, chưa viết code): nút "+" tạo mới và nút ⋮ của NTG **không có accessible name**; role name của tab/menu bị lẫn tên icon ("right awesome-address-card LĨNH VỰC SỐ THẺ"); ô Tìm kiếm ở màn tạo mới không lọc cây theo chữ gõ. Khi viết Page Object phải tìm thuộc tính ổn định hơn (inspect DOM, đề nghị dev thêm `data-testid`) — không dùng toạ độ. Chưa gặp id động hay lỗi chạy song song vì chưa chạy script nào.

**Why:** Tránh khảo sát lại từ đầu và tránh đoán route / trạng thái. **How to apply:** Xác minh lại trên màn hình thật trước khi đưa vào locator (luật "không đoán locator"). Liên quan [[project-care3-2755-thu-tuc-607]], [[project-test-env-safety]].
