---
name: project-test-env-safety
description: "Quy tắc an toàn môi trường test xCare — chỉ Ký và gửi khi đã xác nhận sandbox BHXH, ghi số hồ sơ khi ký lỗi, tài khoản nằm trong .env"
metadata:
  node_type: memory
  type: project
  originSessionId: d394fad8-24f3-48d5-ab04-1f07bb457b23
  modified: 2026-10-06T17:25:36.515Z
---

- Người dùng sẽ cấp tài khoản test; agent đã tạo `.env` (rỗng) và `.env.example` ở gốc repo với các biến XCARE_BASE_URL, XCARE_USER1_*/XCARE_USER2_* (2 đơn vị khác nhau để test phân quyền), XCARE_SIGN_*, XCARE_BHXH_SANDBOX_CONFIRMED (mặc định `no`). `.gitignore` mới tạo, chặn `.env`. 09-10-2026: người dùng đã điền URL, tài khoản 1, môi trường `dev`, XCARE_BHXH_SANDBOX_CONFIRMED=yes; tài khoản 2 và ký số còn trống. Chỉ đơn vị của tài khoản 1 ký được; không cần điền XCARE_SIGN_*. Có tài khoản đơn vị khác chỉ để đăng nhập XEM (XCARE_USER2_* đã điền 09-10, đơn vị khác tài khoản 1), dùng cho ca phân quyền, không ký bằng nó. Môi trường `dev` **dùng chung** với người khác nhưng được phép Ký và gửi (người dùng xác nhận 09-10) → chỉ Ký và gửi trên NTG/hồ sơ do QA tạo, không đụng dữ liệu người khác.
- Không bấm "Ký và gửi" khi XCARE_BHXH_SANDBOX_CONFIRMED khác `yes` — hồ sơ gửi cổng BHXH không thu hồi được.
- Khi ký số / gửi BHXH bị lỗi: ghi lại **số hồ sơ** vào báo cáo để người dùng tự kiểm tra (chỉ dẫn của người dùng 06-10-2026).

**Why:** Gửi nhầm lên cổng BHXH thật là hành động không đảo ngược được.
**How to apply:** Đọc `.env` trước khi chạy test UI; nếu trống thì hỏi người dùng. Liên quan [[project-care3-2755-thu-tuc-607]].
