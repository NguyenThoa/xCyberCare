---
name: feedback-ask-dont-decide
description: "Chỗ nào chưa rõ thì hỏi lại người dùng, tuyệt đối không tự quyết nghiệp vụ; trả lời đã cho thì ghi đúng nguyên văn"
metadata:
  node_type: memory
  type: feedback
  originSessionId: d394fad8-24f3-48d5-ab04-1f07bb457b23
  modified: 2026-10-06T17:25:20.314Z
---

Mọi điểm mơ hồ / mâu thuẫn trong requirement phải đưa thành câu hỏi cho người dùng, không tự chọn đáp án. Người dùng nhắc lại nhiều lần: "phần nào chưa clear thì hỏi tôi chứ không được tự ý quyết định", "Nếu còn thắc mắc gì hãy hỏi lại tôi".

**Why:** Người dùng là người chốt nghiệp vụ; agent tự quyết thì tài liệu phân tích/test case mất giá trị.

**How to apply:** Liệt kê câu hỏi theo mã (AMB-…) để người dùng trả lời inline; ghi câu trả lời kèm nguồn "Chat <ngày>". Khi người dùng bảo "tạm để lại" một chỗ sai đã báo, giữ nguyên, không tự sửa. Xem [[project-care3-2755-thu-tuc-607]].

Cách người dùng trả lời (quan sát 08–09-10-2026):
- Người dùng hay **viết câu trả lời thẳng vào file phân tích** và muốn câu hỏi được **lưu vào file** để trả lời sau, không chỉ hỏi trong chat. Mỗi câu kèm dòng `Trả lời:` trống; câu có phương án thì đánh (a)/(b) để họ chỉ ghi chữ cái.
- Câu trả lời viết vào file chỉ được **gộp vào bảng AMB và sửa REQ khi người dùng bảo** ("chuyển cho tôi"); trước khi gộp phải sao lưu bản gốc ra scratchpad.
- Câu trả lời ngắn / lệch câu hỏi (VD trả lời câu số tệp bằng câu dung lượng) → hỏi lại, không tự đoán ý.

Kiểm tra trạng thái thật trước khi báo: 09-10 agent báo ".env chưa có URL / tài khoản" dựa vào bộ nhớ cũ, người dùng đã điền từ trước và phải nhắc "tôi đã trả lời rồi". **Why:** bộ nhớ chỉ đúng tại lúc ghi. **How to apply:** trước khi nói "chưa có / chưa chốt", mở file đích (`.env` — chỉ kiểm có/trống, không in giá trị — `docs/requirements/README.md`, file phân tích) rồi mới báo.
