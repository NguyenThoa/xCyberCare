# 📋 Phân Tích Requirement: CARE3-2755
## [xc100] [xCare] Nâng cấp giao diện thủ tục: 607 — Cấp lại sổ BHXH do mất, hỏng

## 1. Tổng Quan Ticket

| Thuộc tính | Giá trị |
|---|---|
| **Ticket** | [CARE3-2755](https://jira.cybertech.vn/browse/CARE3-2755) |
| **Type / Priority** | Story · Medium |
| **Status** | Ready for UAT |
| **Reporter / Assignee** | Bùi Thị Lan Em / Vũ Văn Tiến |
| **Tạo / Cập nhật** | 01-07-2026 14:30 / 02-10-2026 16:44 |
| **Sprint · Fix Version · Epic cha** | Không có trong dữ liệu ticket đã đọc |
| **Module** | `thu-tuc-607` · prefix `TT607` |
| **Nguồn phân tích** | ① Mô tả ticket (chỉ chứa link Confluence) · ② Comment Jira: **0 comment** · ③ Confluence pageId `143492085` "Thủ tục 607 - theo phân tích mới", **phiên bản 14**, sửa lúc 06-10-2026 09:25 · ④ 6/25 ảnh đính kèm trang (xem mục 6) · ⑤ **Câu trả lời của người yêu cầu trong chat ngày 06-10-2026** (viết tắt `Chat 06-10`) · ⑥ Câu trả lời người yêu cầu viết thẳng vào file này ngày 08-10-2026 (`File 08-10`) · ⑦ Câu trả lời trong chat ngày 09-10-2026 (`Chat 09-10`) |
| **Dải mã đã dùng** | `REQ-TT607-01` → `REQ-TT607-106` · `AMB-TT607-01` → `AMB-TT607-42` · `RISK-TT607-01` → `RISK-TT607-09` |
| **Mã kế tiếp** | `REQ-TT607-107` · `AMB-TT607-43` · `RISK-TT607-10` — KHÔNG đánh lại từ 01 |
| **Mức độ đầy đủ** | ⚠️ **Đủ một phần.** 22 AMB đã trả lời · 18 AMB trả lời một phần · 2 AMB chưa trả lời. Trong 20 AMB còn mở có **10 AMB 🔴** (13, 17, 19, 20, 32, 34, 35, 36, 37, 42). Câu còn hỏi: B-1 → B-21 ở mục 7.1. Các nhóm REQ có cờ 🔴 ở mục 9 **chưa đủ** căn cứ để sinh test case |

> Các mã tạm `R-01…R-46` và `Q1…Q32` của bản phân tích nháp trước **không còn dùng nữa**. Mã chính thức bắt đầu từ bản này.
>
> Thứ tự ưu tiên khi các nguồn mâu thuẫn: `Chat 06-10` (quyết định mới nhất, có ngày) > Confluence > mockup. Mọi chỗ đã áp thứ tự này đều được ghi lại ở mục 4b và mục 7.1.

## 2. User Story

Ticket **không có** User Story theo dạng "As a… I want… So that…", và cũng không có AC dạng liệt kê. Trích nguyên văn những gì ticket có:

- Summary: *"[xc100] [xCare] Nâng cấp giao diện thủ tục: 607"*
- Description: chỉ chứa link `https://conf.cybertech.vn/pages/viewpage.action?pageId=143492085`
- AC (do người yêu cầu cung cấp trong prompt): *"Làm đúng như phân tích, phần nào chưa clear thì hỏi tôi chứ không được tự ý quyết định"*

→ Vì vậy **AC thực tế = nội dung trang Confluence + các câu trả lời trong chat**.

## 3. Phạm Vi Áp Dụng (Scope)

| Hạng mục | Trong phạm vi | Nguồn |
|---|---|---|
| Màn hình tạo thủ tục 607 (header, Kỳ kê khai, panel NTG) | ✅ | Conf §1–2 |
| Tab TK1-TS | ✅ | Conf §3 |
| Tab D01-TS (tùy chọn) | ✅ | Conf §4 · Chat 06-10 |
| Tab Giấy tờ đính kèm | ✅ | Conf §5 |
| 5 nút: Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi · Trở lại | ✅ | Chat 06-10 |
| Preview tờ khai TK1-TS (QĐ 490/2023) và D01-TS (QĐ 595/2017) | ✅ | Chat 06-10 |
| Chỉnh sửa hồ sơ — **chỉ hồ sơ Lưu nháp** | ✅ | Chat 06-10 · Chat 09-10 (AMB-TT607-19: Trình ký / Gửi thành công không có Chỉnh sửa) |
| Sao chép hồ sơ 607 — tích checkbox hồ sơ ở danh sách thủ tục thì hiện nút | ✅ | Chat 06-10 · File 08-10 (AMB-TT607-36) |
| Thu hồi · Từ chối ký hồ sơ đã Trình ký | ✅ | File 08-10 · Chat 09-10 (AMB-TT607-19) |
| Hồ sơ 607 tạo trên giao diện cũ | ✅ | File 08-10 (AMB-TT607-22) · dữ liệu test: B-10 |
| Hiệu năng lưới NTG (50 / 100 NTG) | ✅ | File 08-10 (AMB-TT607-24) · ngưỡng đạt: B-12 |
| Phân quyền theo đơn vị | ✅ | Chat 06-10 |
| **Thủ tục 612** | ❌ **Ngoài phạm vi** | Chat 06-10: *"không cần check thủ tục 612, chỉ xem những phần liên quan tới thủ tục 607 thôi"* |
| Popup tạo mới NTG (pageId 84123415) | ⚪ Chỉ kiểm việc mở popup / quay lại màn hình | Conf §2 dẫn link; nội dung trang này chưa đọc |
| Bên trong quy trình Trình ký | ⚪ Chỉ kiểm điểm vào / điểm ra | Conf: *"như hệ thống hiện tại"* |
| Nhập excel · nhóm "Chưa có phòng ban" · Mã NV · thanh icon dọc | ❌ **Ngoài phạm vi** | File 08-10 (AMB-TT607-16): *"không test phần này … Nên bỏ qua chức năng này"* |
| "Các phần liên quan tới thủ tục 607" khác (danh sách, chi tiết, in…) | ✅ "Test hết những phần liên quan tới thủ tục 607" — **danh sách màn hình chưa chốt** | File 08-10 (AMB-TT607-36) · B-18 |

## 4. Acceptance Criteria — Phân Tích Chi Tiết

Cột **Nguồn**: `Conf §x · dòng y` = bảng trong trang Confluence 143492085 (bản 14). `Chat 06-10` = câu trả lời của người yêu cầu ngày 06-10-2026. `Mockup <tên ảnh>` = ảnh đính kèm trang Confluence.

### 4.1. Khung màn hình & phân quyền

| REQ ID | Yêu cầu (trích nguyên văn khi có) | Nguồn |
|---|---|---|
| REQ-TT607-01 | Header hiển thị "607 \| Cấp lại sổ BHXH do mất, hỏng" | Chat 06-10 (đè Conf §2 dòng 1 — xem AMB-TT607-01) |
| REQ-TT607-02 | Kỳ kê khai là trường bắt buộc | Conf §2 · "Kỳ kê khai \| Date Picker \*" · ⏳ Có Kỳ kê khai hay không: B-2 |
| REQ-TT607-03 | Kỳ kê khai mặc định bằng tháng/năm tại thời điểm mở màn hình | Conf §2 · "Mặc định là tháng năm hiện tại" · ⏳ B-2 |
| REQ-TT607-04 | Kỳ kê khai cho phép chọn lại | Conf §2 · "cho phép chọn lại" · File 08-10 (AMB-TT607-14): "cho phép chọn lại tháng/năm trước và sau đó" · ⏳ giới hạn & có Kỳ kê khai không: B-2 |
| REQ-TT607-05 | Màn hình chia 2 phần: "Phần 1: Danh sách người tham gia trong hệ thống" · "Phần 2: Màn hình nhập thông tin gồm 3 Tab: TK1-TS, D01-TS, Giấy tờ đính kèm" | Conf §2 · dòng mô tả |
| REQ-TT607-06 | "Màn hình có scollbar ngang dọc khi kích thước bảng vượt quá màn hình" | Conf §2 · dòng mô tả |
| REQ-TT607-07 | "Tab TK1-TS mặc định hiển thị" | Conf §3 · dòng đầu |
| REQ-TT607-08 | "User của đơn vị chỉ được sử dụng các tính năng của chính đơn vị này." | Chat 06-10 · phạm vi áp dụng: AMB-TT607-33 · ✅ File 08-10 (AMB-TT607-33): không có phân vai; user đơn vị nào chỉ thấy dữ liệu đơn vị đó |

### 4.2. Panel danh sách người tham gia (NTG)

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-09 | "Cho phép tích chọn 1 hoặc nhiều người tham gia" | Conf §2 · P1 dòng 1 |
| REQ-TT607-10 | Mỗi dòng hiển thị "Họ và tên + (mã số bảo hiểm xã hội)" | Conf §2 · P1 dòng 2 |
| REQ-TT607-11 | Tìm kiếm gần đúng theo Họ và tên | Conf §2 · P1 dòng 2 · "cho phép nhập Họ và tên hoặc Mã số BHXH để tìm kiếm gần đúng" · ✅ File 08-10 (AMB-TT607-29): không phân biệt hoa/thường; "phải có dấu tiếng Việt mới tìm kiếm đúng được" · ⏳ B-14 |
| REQ-TT607-12 | Tìm kiếm gần đúng theo Mã số BHXH | Conf §2 · P1 dòng 2 (cùng câu trên) · ⏳ Tìm theo một phần mã: B-14 |
| REQ-TT607-13 | Icon Thêm hiển thị tooltip "Thêm mới người tham gia" | Conf §2 · P1 icon 1 |
| REQ-TT607-14 | Bấm icon Thêm → "hiển thị pop-up thêm người tham gia ngay trên màn hình này" | Conf §2 · P1 icon 1 |
| REQ-TT607-15 | Icon Sửa "Mặc định disable" | Conf §2 · P1 icon 2 |
| REQ-TT607-16 | Icon Sửa có tooltip "Sửa thông tin người tham gia" | Conf §2 · P1 icon 2 |
| REQ-TT607-17 | Icon Sửa "Enable khi tích chọn 1 người tham gia" | Conf §2 · P1 icon 2 |
| REQ-TT607-18 | Bấm Sửa → màn hình chỉnh sửa NTG "load lên thông tin hiện tại của người tham gia" | Conf §2 · P1 icon 2 · ⏳ Quay lại màn hình thủ tục có tự lấy dữ liệu mới: B-11 (File 08-10, AMB-TT607-23) |
| REQ-TT607-19 | Icon ⋮ trên từng dòng "chỉ áp dụng cho người tham gia tương ứng" → chuyển NTG đó sang bảng bên phải | Conf §2 · P1 icon 3 |
| REQ-TT607-20 | Icon ⋮ trên đầu bảng "áp dụng với các người tham gia được tích chọn" → chuyển các NTG đó sang bảng bên phải | Conf §2 · P1 icon 3 |
| REQ-TT607-21 | Bấm nút thu gọn → "đóng lại mục người tham gia, chỉ hiển thị phần 2: nội dung thủ tục toàn màn hình", nút đổi sang icon mở rộng | Conf §2 · P1 nút |
| REQ-TT607-22 | "Click vào icon lần nữa để mở rộng người tham gia" | Conf §2 · P1 nút |

### 4.3. Tab TK1-TS

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-23 | Cột STT và cột Họ và tên được cố định: "khi có scollbar ngang di chuyển không làm ảnh hưởng vị trí của cột này" | Conf §3 · dòng 1, 2 |
| REQ-TT607-24 | Họ và tên lấy từ NTG, "không cho sửa" | Conf §3 · dòng 2 |
| REQ-TT607-25 | Các trường sau lấy giá trị từ thông tin NTG: Mã số BHXH · Định dạng · Ngày sinh · Giới tính · Quốc tịch · Dân tộc · Mã số hộ gia đình · Số điện thoại · Email · Hình thức nhận kết quả · Tỉnh/TP và Xã/phường (Nơi đăng ký giấy khai sinh) · Tỉnh/TP, Xã/phường và Địa chỉ nơi nhận (Địa chỉ nhận kết quả) | Conf §3 · dòng 3 → 14.4 |
| REQ-TT607-26 | Các trường sau cho phép sửa: Định dạng · Ngày sinh · Giới tính · Quốc tịch · Dân tộc · Mã số hộ gia đình · Số điện thoại · Email · Hình thức nhận kết quả ("cho phép chọn lại") · 2 cặp Tỉnh/TP – Xã/phường · Địa chỉ nơi nhận | Conf §3 · dòng "Định dạng" → 14.4 |
| REQ-TT607-27 | Mã số BHXH: "Trường hợp Mã số BHXH của người tham gia chưa có thì cho nhập" | Conf §3 · dòng 3 · trường hợp NTG đã có mã: AMB-TT607-40 · 🔁 **Sửa 09-10** (File 08-10, AMB-TT607-40): NTG **đã có** Mã số BHXH thì ô vẫn **cho chỉnh sửa** |
| REQ-TT607-28 | Định dạng ngày sinh có đúng 3 giá trị: `dd/mm/yyyy` · `mm/yyyy` · `yyyy` | Conf §3 · dòng "Định dạng" |
| REQ-TT607-29 | Hình thức nhận kết quả có đúng 2 giá trị: "Nhận bản điện tử" · "Nhận bản giấy" | Conf §3 · dòng 12 · ✅ AMB-TT607-27 "theo conf": Hình thức nhận kết quả **không bắt buộc** |
| REQ-TT607-30 | Bỏ trống trường bắt buộc → tô đỏ, báo "\<Tên trường\> không được để trống". Áp cho: Định dạng · Ngày sinh · Giới tính · Quốc tịch · Dân tộc · Tỉnh/TP và Xã/phường (nơi ĐK khai sinh) · Tỉnh/TP, Xã/phường và Địa chỉ nơi nhận (nhận kết quả) | Conf §3 · dòng "Định dạng", 4, 5, 7, 8, 13.1, 13.3, 14.1, 14.3, 14.4 · ✅ AMB-TT607-27: Địa chỉ nhận kết quả **luôn** bắt buộc · ✅ AMB-TT607-15 (File 08-10, Chat 09-10): ô bỏ trống **bị tô đỏ**, báo lỗi khi bấm **Xem tờ khai** / Trình ký / Ký và gửi · ⏳ Xem tờ khai có bị chặn, Lưu tạm có tô đỏ: B-4 |
| REQ-TT607-31 | "Nội dung thay đổi yêu cầu" là trường bắt buộc | Conf §3 · dòng 15 · "Text Area \*" — câu thông báo lỗi: AMB-TT607-26 · ⏳ B-13 |
| REQ-TT607-32 | "Nội dung thay đổi yêu cầu" tối đa 1000 ký tự | Conf §3 · dòng 15 |
| REQ-TT607-33 | "Hồ sơ kèm theo" không bắt buộc, tối đa 1000 ký tự | Conf §3 · dòng 16 |
| REQ-TT607-34 | Email đúng định dạng `xxx@xxx.xxx`. Nhập sai → "Email không đúng định dạng" | Conf §3 · dòng 11 |
| REQ-TT607-35 | "Sai định dạng, người dùng vẫn ký → báo lỗi 'Email không đúng định dạng'" | Conf §3 · dòng 11 |
| REQ-TT607-36 | Cột Quận/huyện "chỉ hiển thị giao diện còn không có data" | Chat 06-10 · chi tiết: AMB-TT607-25 · ✅ File 08-10 (AMB-TT607-25): áp cho **cả hai** nhóm địa chỉ · cột vẫn mở nhưng danh sách rỗng · preview / file gửi đi ô Huyện để trống |
| REQ-TT607-37 | "Gửi kèm phụ lục thành viên hộ gia đình": "Mặc định không tích chọn" | Conf §3 · dòng 17 |
| REQ-TT607-38 | Checkbox phụ lục: "hệ thống tự động tích chọn nếu Người tham gia chưa có Mã số bHXH" | Conf §3 · dòng 17 |
| REQ-TT607-39 | "Khi tích đính kèm thành viên hộ gia đình thì Xem tờ khai phải hiển thị đúng thông tin của NTG đó" | Chat 06-10 |
| REQ-TT607-40 | "Nếu NTG không khai báo thành viên hộ gia đình mà ở màn tạo thủ tục có tích chọn đính kèm thì khi ký và gửi hiển thị thông báo lỗi" | Chat 06-10 · câu thông báo: AMB-TT607-34 · ✅ File 08-10 (AMB-TT607-34): câu lỗi khi Ký và gửi: tiêu đề "Lỗi", nội dung "TK1TS dòng 1: Đã chọn gửi kèm phụ lục thành viên hộ gia đình nhưng danh sách thành viên đang trống" · Trình ký / Lưu tạm / Xem tờ khai **không bị chặn** · ⏳ popup hay toast: B-17 |
| REQ-TT607-41 | Lưu tạm / Trình ký / Ký và gửi rồi **chỉnh sửa** hồ sơ → "vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" | Chat 06-10 · cách hiểu: AMB-TT607-35 · 🔁 **Thu hẹp 09-10** (Chat 09-10, AMB-TT607-19): Chỉnh sửa **chỉ áp cho hồ sơ Lưu nháp**; hồ sơ Trình ký / Gửi thành công không có nút Chỉnh sửa · File 08-10 (AMB-TT607-21): sao chép / chỉnh sửa / xem hồ sơ Lưu nháp hiển thị đúng dữ liệu lúc bấm Lưu tạm |
| REQ-TT607-42 | Lưu tạm / Trình ký / Ký và gửi rồi **sao chép** hồ sơ → "vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" | Chat 06-10 · cách hiểu: AMB-TT607-35, AMB-TT607-36 · File 08-10 (AMB-TT607-19, 21): Sao chép có ở hồ sơ Lưu nháp, Trình ký, Gửi thành công, Từ chối ký |

### 4.4. Tab D01-TS

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-43 | Tờ khai D01-TS là **tùy chọn** | Chat 06-10 · "Tùy chọn" — quy tắc khi đã thêm dòng: AMB-TT607-32 |
| REQ-TT607-44 | "tại tờ khai TK1-TS người dùng tích chọn NTG nào thì ở tờ khai D01-TS chỉ được thêm NTG đó" | Conf §4 · dòng đầu · ⚠️ File 08-10 (AMB-TT607-32) ghi "chọn NTG bất kỳ" — **có thể mâu thuẫn**, chờ B-16 |
| REQ-TT607-45 | Hiển thị nguyên văn: "Bảng kê thông tin (D01-TS) phục vụ các trường hợp đặc thù theo yêu cầu của cơ quan BHXH, đơn vị nhập thông tin trong bảng dưới đây để thực hiện kê khai bổ sung khi có yêu cầu cơ quan BHXH." | Conf §4 · dòng đầu |
| REQ-TT607-46 | Họ và tên: "Lấy thông tin từ NTG, không cho phép sửa" | Conf §4 · dòng 1 |
| REQ-TT607-47 | Cột Họ và tên và cột Mã số BHXH được cố định khi cuộn ngang | Conf §4 · dòng 1, 2 |
| REQ-TT607-48 | Mã số BHXH: "hệ thống tự động lấy từ người tham gia" | Conf §4 · dòng 2 |
| REQ-TT607-49 | Mã số BHXH: "Cho phép nhập lại thông tin Mã số BHXH" | Conf §4 · dòng 2 · đồng bộ với TK1: AMB-TT607-20 · ✅ File 08-10 (AMB-TT607-20): **không đồng bộ** với TK1 — nhập ở tờ khai nào thì xem tờ khai đó hiện đúng giá trị đã nhập (REQ-TT607-97) |
| REQ-TT607-50 | Độ dài tối đa: Họ và tên 100 · Mã số BHXH 10 · Tên, loại văn bản 100 · Số hiệu 50 · Cơ quan ban hành 255 · Trích yếu 500 · Trích lược nội dung cần thẩm định 1000 | Conf §4 · cột "Độ dài" dòng 1, 2, 3, 4, 7, 8, 9 |
| REQ-TT607-51 | Bỏ trống ô bắt buộc → "tô đỏ nếu chưa nhập". Áp cho: Tên, loại văn bản · Số hiệu · Ngày ban hành · Ngày hiệu lực · Cơ quan ban hành · Trích yếu · Trích lược nội dung cần thẩm định | Conf §4 · dòng 3 → 9 · áp khi nào: AMB-TT607-32 · ✅ File 08-10 (AMB-TT607-32): **đã thêm** dòng D01 thì các ô \* thành bắt buộc (REQ-TT607-104) |
| REQ-TT607-52 | Ngày ban hành: "Định dạng dd/mm/yyyy" | Conf §4 · dòng 5 |
| REQ-TT607-53 | Ngày hiệu lực: định dạng `dd/mm/yyyy` | Conf §4 · dòng 6 · cột "Độ dài" · ✅ File 08-10 (AMB-TT607-28): **không** kiểm Ngày hiệu lực ≥ Ngày ban hành · nhập ngày sai "Không hiển thị kết quả nhập" · ⏳ câu lỗi: B-3 |

### 4.5. Tab Giấy tờ đính kèm

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-54 | Click vào khu vực tải tệp để chọn tệp | Conf §5 · dòng 1 |
| REQ-TT607-55 | Kéo-thả tệp trực tiếp vào khung | Conf §5 · dòng 1 |
| REQ-TT607-56 | Hiển thị nguyên văn: "Định dạng cho phép: pdf, xml, jpg, xlsx. Tối đa 06 file (gồm tờ khai). Tổng dung lượng tối đa 5MB" | Conf §5 · dòng 2 · Chat 06-10 xác nhận · Cách đếm: REQ-TT607-90 |
| REQ-TT607-57 | Icon minh hoạ thay đổi theo phần mở rộng tệp (PDF, XLSX, JPG, XML) | Conf §5 · dòng 3 |
| REQ-TT607-58 | Tên tệp hiển thị "theo tên gốc của file khi upload" | Conf §5 · dòng 4 |
| REQ-TT607-59 | Dung lượng từng tệp tính bằng MB, "làm tròn 2 chữ số thập phân" | Conf §5 · dòng 5 |
| REQ-TT607-60 | Xem: "xem trước nội dung file đã tải (preview), không tải file về máy" | Conf §5 · dòng 6 |
| REQ-TT607-61 | Tải xuống: "tải file đã đính kèm về máy tính cá nhân" | Conf §5 · dòng 7 |
| REQ-TT607-62 | Bấm Xóa → popup "Xác nhận" với nội dung "Bạn có chắc chắn muốn xóa tài liệu này?" | Conf §5 · dòng 8 · Mockup `image2026-9-8_17-19-44.png` |
| REQ-TT607-63 | Popup xóa → Xác nhận: "Xóa file đính kèm, tính lại tổng dung lượng" | Conf §5 · dòng 8 |
| REQ-TT607-64 | Popup xóa → Hủy bỏ: "Tắt popup" | Conf §5 · dòng 8 |
| REQ-TT607-65 | Tổng dung lượng "Cập nhật lại mỗi khi thêm/xóa file. Căn phải, nằm dưới file cuối cùng" | Conf §5 · dòng 9 |
| REQ-TT607-66 | Tổng dung lượng vượt quá 5MB → "Tổng dung lượng các tệp không được vượt quá 05 MB." | Conf §5.1 · dòng 1 · ✅ Chat 09-10 (AMB-TT607-17): 5MB **tính tổng hết, gồm cả tờ khai** · tiêu đề "Thông báo" |
| REQ-TT607-67 | Tệp sai định dạng → "Vui lòng chọn tệp có định dạng JPG, XLSX, PDF, XML." | Conf §5.1 · dòng 2 |
| REQ-TT607-68 | Quá 6 tệp → "Số lượng tệp đính kèm không được vượt quá 06 tệp." | Conf §5.1 · dòng 3 · Conf §5.2 · cách đếm: AMB-TT607-17 · ⚠️ Chat 09-10 trả lời câu lỗi vượt số tệp bằng câu của dung lượng — chờ B-5 |
| REQ-TT607-69 | Danh sách "hiển thị theo thứ tự tải lên (không cho kéo-thả sắp xếp lại)" | Conf §5.2 |

### 4.6. Nút thao tác & điều hướng

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-70 | Có 5 nút: Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi · Trở lại | Chat 06-10 · nhãn và tab hiển thị: AMB-TT607-39 · ✅ File 08-10 (AMB-TT607-39): nhãn "Ký và gửi" · bộ 5 nút hiện ở **tất cả các tab** |
| REQ-TT607-71 | Lưu tạm: "Cho phép lưu kể cả khi chưa validate hết các ô nhập thông tin" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-72 | Lưu tạm → "chuyển sang màn hình danh sách thủ tục trạng thái Lưu nháp" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-73 | Lưu tạm: "khi lưu không cập nhật thông tin thay đổi vào NTG" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-74 | Khi bấm Lưu tạm / Trình ký / Ký và gửi: "Tô đỏ các ô có lỗi và hiển thị lỗi khi hover vào ô input, lỗi hiển thị dạng tooltip" | Conf §3/§4 · Thao tác 1, 3, 4 · ⏳ Tooltip còn không khi đã có toast (REQ-TT607-103): B-15 |
| REQ-TT607-75 | Khi bấm Lưu tạm / Trình ký / Ký và gửi: "Tô đỏ các ô bắt buộc nhập nhưng đang bị bỏ trống" | Conf §3/§4 · Thao tác 1, 3, 4 · ⏳ Lưu tạm có tô đỏ: B-4 |
| REQ-TT607-76 | Xem tờ khai ở tab TK1-TS → popup preview mẫu TK1-TS (QĐ 490/QĐ-BHXH ngày 28-03-2023) | Conf §3 · Thao tác 2 · Mockup `image2026-9-21_14-41-18.png` · Chat 06-10 |
| REQ-TT607-77 | Xem tờ khai ở tab D01-TS → popup preview mẫu D01-TS (QĐ 595/QĐ-BHXH ngày 14-04-2017) | Conf §4 · Thao tác 2 · Mockup `image2026-9-21_14-41-42.png` · Chat 06-10 |
| REQ-TT607-78 | Trình ký "thực hiện quy trình Trình ký như hệ thống hiện tại" | Conf §3/§4 · Thao tác 3 |
| REQ-TT607-79 | Còn lỗi thì Trình ký bị chặn, "hiển thị rõ thông báo lỗi" | Chat 06-10 · câu thông báo: AMB-TT607-31 · ✅ File 08-10 (AMB-TT607-31): thông báo dạng **toast** (REQ-TT607-103) |
| REQ-TT607-80 | Ký và gửi: "Khi còn lỗi không cho phép Ký và gửi BH" | Conf §3/§4 · Thao tác 4 |
| REQ-TT607-81 | Ký và gửi: "Khi ký và gửi BH thực hiện cập nhật thông tin NLĐ theo hồ sơ đã ký gửi" | Conf §3/§4 · Thao tác 4 · ✅ File 08-10 (AMB-TT607-20): "NLĐ là người tham gia (NTG)" · ⏳ có cập nhật NTG theo tờ khai: B-9 |
| REQ-TT607-82 | Trở lại khi "người dùng đã nhập thông tin người tham gia" → popup "Thông báo", nội dung "Bạn có chắc muốn trở lại danh sách?" | Conf §3/§4 · Thao tác 5 · Mockup `image2026-9-21_14-45-9.png` · điều kiện: AMB-TT607-37 · ⏳ Điều kiện hiện popup & câu chữ "danh sách": B-19 |
| REQ-TT607-83 | Popup Trở lại → bấm Hủy bỏ **hoặc** X → đóng popup, vẫn ở màn hình thủ tục 607 vừa tạo | Chat 06-10 |
| REQ-TT607-84 | Popup Trở lại → Đồng ý → không lưu thông tin, quay về màn hình **Tạo hồ sơ mới** | Chat 06-10 · Conf §3/§4 Thao tác 5 · ✅ File 08-10 (AMB-TT607-37): "Bấm đồng ý thì quay trở về màn tạo thủ tục mới" |
| REQ-TT607-85 | Bấm Back của trình duyệt → hiện thông báo như REQ-TT607-82 | Conf §3/§4 · Thao tác 5 · khả thi: AMB-TT607-42 · ⏳ B-21 |
| REQ-TT607-86 | Đóng cửa sổ → hiện thông báo | Conf §3/§4 · Thao tác 5 · khả thi: AMB-TT607-42 · ⏳ B-21 |

### 4.7. Yêu cầu bổ sung từ câu trả lời AMB (08 → 09-10-2026)

Câu chữ trích nguyên văn câu trả lời của người yêu cầu. Ô có ⏳ còn chờ câu hỏi B-x ở mục 7.1.

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-87 | Lưới TK1-TS **không được có** cột "Trạng thái (3.2)" (mockup TK1 có). Nếu có → bug | AMB-TT607-12 · File 08-10 · Chat 09-10 |
| REQ-TT607-88 | Preview TK1-TS: ô **có trên lưới** lấy giá trị trên lưới; ô **không có trên lưới** lấy từ thông tin NTG, phải kiểm lấy đúng từ NTG. Ánh xạ: [06] CCCD = CCCD/ĐDCN/HC · [10] Họ và tên cha/mẹ/giám hộ = Người giám hộ · [13] Mã số BHXH = màn hình thông tin NTG · [14] Họ và tên (chữ in hoa) = Họ và tên · [14.2] Giới tính · [14.3] Ngày sinh · [14.4] Nơi đăng ký khai sinh = **chỉ** "Nơi cấp giấy khai sinh" (bắt buộc, không lấy nguồn khác) · [14.5] CCCD/ĐDCN/HC · [15] Mức tiền đóng = Mức đóng ở **tab "Thông tin tham gia BHXH"** của màn hình NTG · [16] Phương thức đóng · [17] Nơi KCB ban đầu = Tỉnh thành KCBBĐ và Bệnh viện KCBBĐ | AMB-TT607-13, 30 · File 08-10 · Chat 09-10 · ⏳ B-1, B-1b, B-1c |
| REQ-TT607-89 | Ngày sinh: định dạng `yyyy` thì nhập đủ ngày/tháng **không hiển thị** · ngày không tồn tại **không nhập được** · ngày tương lai nhập **bình thường** · nhập sai "nhập vào thì ko hiển thị gì, vẫn tô đỏ ô input và khi ký báo lỗi" | AMB-TT607-15 · File 08-10 · Chat 09-10 · ⏳ câu lỗi: B-3 |
| REQ-TT607-90 | Số tệp được tải lên: chỉ khai TK1-TS → tối đa **5 tệp**; khai TK1-TS và D01-TS → tối đa **4 tệp**. Tổng dung lượng ≤ 5MB **tính cả tờ khai** | AMB-TT607-17 · File 08-10 · Chat 09-10 · ⏳ câu lỗi: B-5 · thêm D01 sau khi đã đủ tệp: chờ BA |
| REQ-TT607-91 | **Không** giới hạn dung lượng từng tệp (chỉ giới hạn tổng). Tệp 0 byte và tệp trùng tên **đều nhận** | AMB-TT607-18 · File 08-10 |
| REQ-TT607-92 | Tệp xml và xlsx không xem trước được → nút **Xem bị ẩn** | AMB-TT607-18 · File 08-10 · Chat 09-10 |
| REQ-TT607-93 | Trình ký: phải điền đủ thông tin bắt buộc, thiếu thì báo lỗi đúng trường. Thành công → về **màn hình danh sách thủ tục**, trạng thái **"Trình ký"**, **không** sinh số hồ sơ. Tích checkbox hồ sơ: Sao chép · Thu hồi · Từ chối ký · Ký và gửi; **không** có Chỉnh sửa | AMB-TT607-19 · File 08-10 · Chat 09-10 · ⏳ B-6 |
| REQ-TT607-94 | Ký và gửi: phải điền đủ thông tin bắt buộc, thiếu thì báo lỗi đúng trường. Thành công → về màn hình danh sách thủ tục, trạng thái **"Gửi thành công"**, **có** sinh số hồ sơ (ghi lại số hồ sơ vào báo cáo). Tích checkbox hồ sơ: chỉ **Sao chép** | AMB-TT607-19 · File 08-10 · Chat 09-10 |
| REQ-TT607-95 | Thu hồi hồ sơ Trình ký → trạng thái **Lưu nháp**, hồ sơ hoạt động đúng như hồ sơ Lưu nháp | AMB-TT607-19 · Chat 09-10 · ⏳ popup / lý do: B-7 · thao tác của Lưu nháp: B-8 |
| REQ-TT607-96 | Từ chối ký → trạng thái **"Từ chối ký"**, hồ sơ chỉ **Sao chép** được | AMB-TT607-19 · Chat 09-10 · ⏳ B-7 |
| REQ-TT607-97 | Mã số BHXH ở TK1-TS và D01-TS **không đồng bộ**: "Nhập ở tờ khai nào thì khi view hiển thị đúng tờ khai đã nhập đó" | AMB-TT607-20 · File 08-10 |
| REQ-TT607-98 | Khi gửi, thông tin NTG trên tờ khai khác danh sách NTG → hiện thông báo "Xác nhận" với nội dung *"thông tin NTG trên tờ khai khác với thông tin trong danh sách NTG. Bấm "Xác nhận" để tiếp tục Ký và Gửi BHXH."* · Bấm Hủy bỏ: "Tắt popup, không thực hiện trình ký, tờ khai giữ nguyên" | AMB-TT607-20 · File 08-10 · ⏳ nút nào kích hoạt, câu chữ, trường so sánh: B-9 |
| REQ-TT607-99 | Hồ sơ 607 tạo trên giao diện cũ mở bằng **giao diện mới**; dữ liệu Huyện cũ được đổi sang thông tin mới nhất hiện tại | AMB-TT607-22 · File 08-10 · ⏳ dữ liệu test: B-10 |
| REQ-TT607-100 | Bỏ NTG khỏi lưới bằng icon **Thùng rác** ở cột Họ và tên (2). Thêm 2 NTG cùng lúc không báo lỗi | AMB-TT607-24 · File 08-10 · ⏳ chuyển trùng NTG: B-12 |
| REQ-TT607-101 | Kiểm hiệu năng lưới với khoảng **50 và 100 NTG** | AMB-TT607-24 · File 08-10 · ⏳ ngưỡng đạt: B-12 |
| REQ-TT607-102 | Popup Xem tờ khai **không có** dòng "Dung lượng file còn lại" và nút "+ Thêm đính kèm". Chỉ hiển thị các tờ khai, đúng mẫu, đúng thông tin. Có nút **Tải xuống** — file tải xuống phải hiển thị đúng | AMB-TT607-30 · File 08-10 |
| REQ-TT607-103 | Lỗi khi Trình ký / Ký và gửi hiển thị dạng **toast góc phải trên cùng**, đủ thời gian đọc rồi biến mất; lỗi trường nào hiện đúng thông tin lỗi trường đó và **trỏ tới đúng tab** bị lỗi | AMB-TT607-31 · File 08-10 · ⏳ nhiều tab cùng lỗi, tooltip: B-15 |
| REQ-TT607-104 | D01-TS: **đã thêm** dòng thì các ô \* bắt buộc. Thêm dòng: "chọn NTG bất kỳ bằng cách click vào checkbox rồi chọn option bất kỳ được hiển thị". Xóa dòng: icon **Thùng rác** cột Họ và tên (2). **Không chặn** thêm nhiều NTG cùng lúc và nhiều dòng | AMB-TT607-32 · File 08-10 · ⏳ menu/option, quan hệ với REQ-44: B-16 |
| REQ-TT607-105 | Đổi Tỉnh/TP thì Xã/phường **bị xóa**. Danh mục Tỉnh/Xã theo danh mục **mới nhất hiện tại** | AMB-TT607-41 · File 08-10 |
| REQ-TT607-106 | Dòng hướng dẫn trong dropzone: "Kéo thả tệp vào đây hoặc chọn tệp từ máy tính" | AMB-TT607-38 · File 08-10 |

**Tổng: 106 REQ** (4.1: 8 · 4.2: 14 · 4.3: 20 · 4.4: 11 · 4.5: 16 · 4.6: 17 · 4.7: 20).

> **Quy mô tài liệu:** có ≥ 25 REQ, nhưng chỉ có **1 ticket**. Cấu trúc tách theo quy tắc của workflow là "mỗi ticket 1 file con", nên với 1 ticket thì tách ra cũng chỉ được index + 1 file con trùng nội dung. Vì vậy tôi giữ **1 file**.

## 4b. Đối Chiếu Chéo Nguồn

| Hạng mục | Ticket | Comment Jira | Confluence (bản 14) | Mockup / preview | Chat 06-10 | Kết luận |
|---|---|---|---|---|---|---|
| Tên thủ tục | — | — | "Cấp lại sổ BHXH không thay đổi thông tin" | TK1: giống Conf · D01/Đính kèm/preview: "…do mất, hỏng" | "607 Cấp lại sổ BHXH do mất, hỏng" | ✅ Theo Chat → AMB-TT607-01 đóng |
| Cấp địa chỉ | — | — | Chỉ Tỉnh + Xã (thiếu 13.2/14.2) | TK1 có cột Quận/huyện · preview TK1-TS có ô Huyện | Cột Quận/huyện chỉ hiển thị, không có data | ✅ Theo Chat → AMB-TT607-02 đóng · chi tiết còn mở AMB-TT607-25 |
| Mẫu tờ khai | — | — | Không ghi số văn bản | TK1-TS QĐ 490/2023 · D01-TS QĐ 595/2017 | "đúng rồi" | ✅ AMB-TT607-03 đóng |
| Bộ nút | — | — | Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi BH · Trở lại | D01: Hủy bỏ · Xem tờ khai · Lưu và đóng · Trình ký · Ký và gửi | Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi · Trở lại | ✅ Theo Chat · AMB-TT607-39 đóng (File 08-10): nhãn "Ký và gửi", 5 nút ở tất cả các tab |
| Trở lại → Đồng ý | — | — | Vừa "quay về màn hình danh sách" vừa "chuyển về màn hình Tạo hồ sơ mới" | Popup: "Bạn có chắc muốn trở lại danh sách?" | Về màn hình tạo hồ sơ mới | ✅ Theo Chat · câu chữ popup lệch đích đến → AMB-TT607-37 · B-19 |
| Giới hạn dung lượng | — | — | 5MB | Preview: "Dung lượng file còn lại: 6.0MB" | 5MB | ✅ 5MB, tính cả tờ khai (Chat 09-10) · AMB-TT607-30 đóng: preview không có "Dung lượng file còn lại" và "+ Thêm đính kèm" |
| Trình ký khi còn lỗi | — | — | Chỉ ghi "Tô đỏ" | TK1: nút Trình ký đang disable | Có chặn, hiển thị rõ thông báo lỗi | ✅ AMB-TT607-07 đóng · dạng toast (File 08-10, REQ-TT607-103) · còn B-15 |
| D01 bắt buộc? | — | — | Các ô đánh dấu \* | — | Tùy chọn | ✅ AMB-TT607-08 đóng · đã thêm dòng thì ô \* bắt buộc (REQ-TT607-104) · còn B-16 |
| Kỳ kê khai | — | — | Date Picker | 2 dropdown tháng / năm | File 08-10: Date Picker · Chat 09-10: cần kiểm tra lại có Kỳ kê khai không | ⏳ Theo File 08-10 là Date Picker · có tồn tại không: B-2 |
| Cột "Trạng thái (3.2)" | — | — | Không có | TK1 có ("Đã kiểm tra") | Chat 09-10: màn hình không được có cột này | ✅ AMB-TT607-12 đóng → REQ-TT607-87 |
| Đánh số cột | — | — | 13.x / 14.x | TK1: 12.x / 13.x · D01: hai cột cùng số 4.5, không có 4.3 | — | ⚠️ AMB-TT607-38 · B-20 |
| Dòng hướng dẫn trong dropzone | — | — | "Chọn tệp hoặc kéo và thả tệp vào đây" | "Kéo thả tệp vào đây hoặc chọn tệp từ máy tính" | File 08-10: theo mockup | ✅ Theo mockup → REQ-TT607-106 |
| Thủ tục 612 | — | — | Ghi chú ở dòng 15 | — | Ngoài phạm vi | ✅ AMB-TT607-11 đóng |

## 5. Phụ Thuộc (Dependencies)

### 5.1. Màn hình Tạo mới người tham gia (Confluence pageId 84123415)
Trang được dẫn link từ Conf §2, **chưa đọc** nội dung. Phạm vi của ticket này: mở popup Thêm, mở màn hình Sửa (REQ-TT607-14, 18) và quay lại thủ tục (AMB-TT607-23).

### 5.2. Quy trình Trình ký hiện tại
Conf chỉ ghi "như hệ thống hiện tại" và không đặc tả lại. Trạng thái hồ sơ sau khi Trình ký chưa rõ → AMB-TT607-19.

### 5.3. Ký số & cổng tiếp nhận BHXH
Nút Ký và gửi phụ thuộc chứng thư số và cổng BHXH. Khi lỗi xảy ra, người yêu cầu chỉ dẫn: *"Lúc ý hãy note lại số hồ sơ để tôi kiểm tra"* (Chat 06-10) → RISK-TT607-02.

### 5.4. Dữ liệu hồ sơ NTG / NLĐ
Dữ liệu tờ khai lấy từ hồ sơ NTG (REQ-TT607-25). Ký và gửi ghi ngược vào NLĐ (REQ-TT607-81). Thông tin thành viên hộ gia đình của NTG là điều kiện của REQ-TT607-40.

### 5.5. Business Rules tổng hợp

| # | Rule | REQ |
|---|---|---|
| BR-1 | Mức chặn khi còn lỗi: Lưu tạm **cho lưu** · Trình ký **chặn** · Ký và gửi **chặn** | 71, 79, 80 |
| BR-2 | Chỉ Ký và gửi mới ghi ngược vào NLĐ; Lưu tạm thì không | 73, 81 |
| BR-3 | D01-TS là tùy chọn và chỉ được thêm NTG đã tích chọn ở TK1-TS | 43, 44 |
| BR-4 | NTG chưa có Mã số BHXH → ô mã cho nhập **và** checkbox phụ lục tự được tích | 27, 38 |
| BR-5 | Tích phụ lục mà NTG không có thành viên HGĐ → chặn **chỉ** ở bước Ký và gửi; Trình ký / Lưu tạm / Xem tờ khai không chặn | 40 |
| BR-6 | Đính kèm: ≤ 6 tệp gồm tờ khai (chỉ TK1 → 5 tệp tải lên · TK1 + D01 → 4 tệp) · tổng ≤ 5MB **tính cả tờ khai** · chỉ pdf/xml/jpg/xlsx · không giới hạn từng tệp | 66, 67, 68, 90, 91 |
| BR-7 | Người dùng chỉ thao tác trong phạm vi đơn vị của mình | 08 |
| BR-8 | Hồ sơ đã lưu/ký, khi mở chỉnh sửa (chỉ Lưu nháp) hoặc sao chép, hiển thị đúng dữ liệu tại thời điểm đã lưu/ký | 41, 42 |
| BR-9 | Thao tác theo trạng thái: **Lưu nháp** → Chỉnh sửa, Sao chép (còn lại: B-8) · **Trình ký** → Sao chép, Thu hồi, Từ chối ký, Ký và gửi · **Gửi thành công** → chỉ Sao chép · **Từ chối ký** → chỉ Sao chép | 93–96 |

## 6. Phân Tích Mockup/Screenshot

Đã xem **6/25** ảnh đính kèm. 19 ảnh còn lại là icon nhỏ (< 2KB) hoặc ảnh ngày 08-09-2026 không được nhúng vào nội dung trang bản 14 → **chưa xem**.

### 6.1. `image2026-9-9_8-44-41.png` — Màn hình chính, tab TK1-TS
- Header ghi "607 | Cấp lại sổ BHXH không thay đổi thông tin" — **lệch** với tên đã chốt (REQ-TT607-01).
- Kỳ kê khai là **2 dropdown** (12 / 2024), góc phải có nhãn "Mẫu: TK1-TS".
- Lưới có header 2 tầng. Có thêm cột **Trạng thái (3.2)** (AMB-TT607-12) và cột **Quận/huyện (12.2, 13.2)**.
- Nút: Lưu tạm · Xem tờ khai · **Trình ký (đang disable)** · Ký và gửi BH · Trở lại.

### 6.2. `image2026-9-18_10-34-23.png` — Tab D01-TS
- Header "…do mất, hỏng". Có dòng text hướng dẫn, nhãn "Mẫu: D01-TS".
- Cột Họ tên và Mã số BHXH có nền xám (khoá). Ô Ngày hiệu lực **tô đỏ**, ảnh không giải thích lý do.
- Header nhóm: "Thông tin văn bản" (4.x) và "Nội dung văn bản" (5.x). Hai cột cùng số **4.5**, không có 4.3.
- Bộ nút **khác** đặc tả: Hủy bỏ · Xem tờ khai · Lưu và đóng · Trình ký · Ký và gửi → đã chốt theo Chat.

### 6.3. `image2026-9-18_10-27-16.png` — Tab Giấy tờ đính kèm
- Dropzone có nút "Chọn tệp" và dòng định dạng cho phép. Bảng "Tài liệu đã đính kèm" gồm STT · Tên tệp · Dung lượng · Thao tác. Khi chưa có tệp, bảng hiện "Chưa có tài liệu đính kèm" và "Tổng dung lượng: 0 MB".
- Panel trái **khác** 6.1: có ô "Tìm kiếm" placeholder "Điền thông tin…", nhóm "CHƯA CÓ PHÒNG BAN", dòng "Mã NV". Có thêm nút "Nhập excel" và thanh icon dọc → AMB-TT607-16.
- Bộ nút hiện cả ở tab này (đặc tả không ghi) → AMB-TT607-39.

### 6.4. `image2026-9-21_14-45-9.png` — Popup Trở lại
Tiêu đề "Thông báo", nội dung "Bạn có chắc muốn trở lại danh sách?", có nút Hủy bỏ · Đồng ý · X.

### 6.5. `image2026-9-8_17-19-44.png` — Popup Xóa tệp
Tiêu đề "Xác nhận", nội dung "Bạn có chắc chắn muốn xóa tài liệu này?", có nút Hủy bỏ · Xác nhận · X.

### 6.6. `image2026-9-21_14-41-18.png` / `…14-41-42.png` — Popup Xem tờ khai
- Bên trái: danh sách tờ khai (TK1-TS, D01-TS); cột STT của **cả hai dòng đều là "1"**. Bên phải: ảnh mẫu. Có nút Tải xuống và X.
- Mẫu TK1-TS (QĐ 490) có các trường **không có trên lưới nhập**: [06] CCCD/ĐDCN/Hộ chiếu, [10] Họ tên cha/mẹ/giám hộ, mục II [13]–[17] → AMB-TT607-13.
- Popup D01 hiển thị "Dung lượng file còn lại: 6.0MB" và "+ Thêm đính kèm" → AMB-TT607-30.

## 7. Các Điểm Mơ Hồ & Rủi Ro

### 7.1. Điểm Mơ Hồ (Ambiguities)

> Nguồn trả lời: `Chat 06-10` · `File 08-10` = câu trả lời người yêu cầu viết thẳng vào file này (08-10-2026) · `Chat 09-10`. Câu trả lời ghi **nguyên văn**.
> Tổng: **22 AMB đã trả lời** · **18 AMB trả lời một phần** · **2 AMB chưa trả lời**. Câu còn hỏi đánh mã `B-x`, chi tiết ở "🔁 Lượt hỏi 2".

#### ✅ Đã trả lời

| Mã | Câu hỏi | Trả lời | Nguồn | REQ liên quan |
|---|---|---|---|---|
| AMB-TT607-01 | Tên thủ tục 607 | "607 Cấp lại sổ BHXH do mất, hỏng" | Chat 06-10 | 01 |
| AMB-TT607-02 | Địa chỉ 2 cấp hay 3 cấp | "Quận/Huyện đã bỏ nên chỉ hiển thị giao diện còn không có data" | Chat 06-10 | 36 |
| AMB-TT607-03 | Mẫu tờ khai đích | QĐ 490/2023 (TK1-TS) và QĐ 595/2017 (D01-TS) — "đúng rồi" | Chat 06-10 | 76, 77 |
| AMB-TT607-04 | Bộ nút của D01 | Lưu tạm, Xem tờ khai, Trình ký, Ký và gửi, Trở lại | Chat 06-10 | 70 |
| AMB-TT607-05 | Đích của Trở lại → Đồng ý | Hủy bỏ / X → ở lại · Đồng ý → màn hình tạo hồ sơ mới | Chat 06-10 | 83, 84 |
| AMB-TT607-06 | 5MB hay 6MB | 5MB (nhắc lại câu định dạng cho phép) | Chat 06-10 | 56, 66 |
| AMB-TT607-07 | Trình ký có chặn khi còn lỗi | "có, hiển thị rõ thông báo lỗi" | Chat 06-10 | 79 |
| AMB-TT607-08 | D01-TS bắt buộc hay tùy chọn | "Tùy chọn" | Chat 06-10 | 43 |
| AMB-TT607-09 | Phân quyền | "User của đơn vị chỉ được sử dụng các tính năng của chính đơn vị này." *(chi tiết ở AMB-TT607-33)* | Chat 06-10 | 08 |
| AMB-TT607-10 | Phụ lục thành viên hộ gia đình | Xem tờ khai đúng thông tin · sửa/sao chép giữ đúng dữ liệu đã lưu · chặn khi Ký gửi nếu NTG không khai báo *(chi tiết ở AMB-TT607-34, 35)* | Chat 06-10 | 39–42 |
| AMB-TT607-11 | Có regression thủ tục 612 không | Không — chỉ phần liên quan 607 | Chat 06-10 | — |
| AMB-TT607-12 | Cột "Trạng thái (3.2)" (mockup TK1) có trong phạm vi không? | "bỏ cột trạng thái cho tôi" → làm rõ: **(b) Màn hình không được có cột này, nếu có thì là bug** | File 08-10 · Chat 09-10 | 87 |
| AMB-TT607-16 | Nút "Nhập excel", nhóm "Chưa có phòng ban", dòng Mã NV, thanh icon dọc có trong phạm vi không? | "không test phần này do thủ tục này không cần chức năng này nên ko có data để import. Nên bỏ qua chức năng này" | File 08-10 | Mục 3 |
| AMB-TT607-21 | Mở lại hồ sơ Lưu nháp có giữ dữ liệu lỗi và tệp đính kèm không? | "Khi sao chép/chỉnh sửa/ View hồ sơ lưu nháp thì phải được hiển thị đúng thông tin dữ liệu như lúc bấm Lưu tạm" | File 08-10 | 41, 42 |
| AMB-TT607-22 | Hồ sơ 607 tạo trên giao diện cũ mở bằng giao diện nào? Dữ liệu cấp Huyện cũ? | "Hiển thị giao diện mới, Dữ liệu Huyện cũ được đổi hết sang thông tin mới nhất hiện tại" *(dữ liệu test: B-10)* | File 08-10 | 99 |
| AMB-TT607-25 | Cột Quận/huyện "không có data" áp cho nhóm nào? Khoá hay mở? Preview để trống? | "1. Đúng … áp cho **cả hai** nhóm địa chỉ (Nơi ĐK khai sinh và Địa chỉ nhận kết quả) · 2. Cột này vẫn mở nhưng danh sách rỗng · 3. Đúng. Trên preview / file gửi đi, ô Huyện để trống" | File 08-10 | 36 |
| AMB-TT607-27 | Hình thức nhận kết quả có bắt buộc không? Chọn "Nhận bản điện tử" thì Địa chỉ nhận kết quả còn bắt buộc không? | "theo conf" → Hình thức nhận kết quả **không** bắt buộc (Conf không có \*) · Địa chỉ nhận kết quả **luôn** bắt buộc | File 08-10 | 29, 30 |
| AMB-TT607-30 | Popup Xem tờ khai có "Dung lượng file còn lại" và "+ Thêm đính kèm" không? | "Không có dòng này và nút + thêm đính kèm như mockup. Nó là tài liệu cũ rồi. Khi xem tờ khai chỉ hiển thị thông tin các tờ khai, kiểm tra nó hiển thị đúng mẫu, đúng thông tin đã nhập ở phần tạo thủ tục, phần nào ko có sẽ lấy từ thông tin người tham gia. Có nút tải xuống hãy check cả file tải xuống luôn xem có hiển thị đúng không." | File 08-10 | 88, 102 |
| AMB-TT607-33 | Trong cùng đơn vị có phân vai không? Dữ liệu theo đơn vị? | "Không có phân vai, user của đơn vị nào hiển thị đũng dữ liệu của đơn vị đó và không thấy dữ liệu của nhau" | File 08-10 | 08 |
| AMB-TT607-39 | Nhãn "Ký và gửi" hay "Ký và gửi BH"? 5 nút có ở tab Giấy tờ đính kèm không? | "Nhãn Ký và gửi. Nppk 5 nít hiện ở tất cả các tab" (= bộ 5 nút hiện ở tất cả các tab) | File 08-10 | 70 |
| AMB-TT607-40 | NTG đã có Mã số BHXH thì ô Mã số BHXH ở TK1 bị khoá không? | "Vẫn cho chỉnh sửa" | File 08-10 | 27 |
| AMB-TT607-41 | Đổi Tỉnh thì Xã có bị xoá không? Danh mục Tỉnh/Xã lấy từ đâu? | "Đổi tỉnh thì xã có bị xóa. danh mục tỉnh/xã lấy theo danh mục mới nhất hiện tại" | File 08-10 | 105 |

#### ⏳ Đã trả lời một phần

| Mã | Câu hỏi | Đã trả lời (nguyên văn) | Nguồn | Còn hỏi | Mức |
|---|---|---|---|---|---|
| AMB-TT607-13 | Mẫu TK1-TS có các ô không có trên lưới nhập ([06], [10], mục II [13]–[17]) — preview lấy từ đâu? | "Lấy từ thông tin người tham gia · [06] CCCD = CCCD/ĐDCN/HC trong màn hình thông tin người tham gia · [10] Họ và tên cha/mẹ/giám hộ = Người giám hộ … · [13] Mã số BHXH = *(bỏ trống)* · [14] Họ và tên (viết chữ in hoa) = Họ và tên … · [14.2] Giới tính = Giới tính … · [14.3] Ngày, tháng, năm sinh = Ngày sinh … · [14.4] Nơi đăng ký khai sinh = Nơi cấp giấy khai sinh / Nguyên quán / Hộ khẩu thường trú, tạm trú … · [14.5] Số CCCD/ĐDCN/Hộ chiếu = CCCD/ĐDCN/HC … · [15] Mức tiền đóng = Mức đóng trong màn hình thông tin tham gia BHXH · [16] Phương thức đóng = Phương thức đóng … · [17] Nơi đăng ký khám, chữa bệnh ban đầu = Tỉnh thành KCBBĐ và Bệnh viện KCBBĐ …" (File 08-10)<br>Chat 09-10: [13] "lấy từ màn hình thông tin người tham gia" · ô có trên lưới thì lấy theo lưới, không có mới lấy từ NTG: "đúng . Nhưng cũng cần check xem đã lấy đúng từ thông tin NTG chưa. Và có cho sửa thông tin này" · [14.4]: "lấy từ nơi cấp giấy khai sinh. Trường này là bắt buộc nên không thể trồng được. Nếu ko có thông tin cũng không lấy từ nguồn khác" · [15]: "cùng màn hình người tham gia nhưng ở tab thông tin tham gia BHXH" | File 08-10 · Chat 09-10 | B-1 · B-1b · B-1c | 🔴 |
| AMB-TT607-14 | Kỳ kê khai: Date Picker hay 2 dropdown? Chọn được khoảng nào? | "Date Picker, mặc định là tháng năm hiện tại, cho phép chọn lại tháng/năm trước và sau đó." (File 08-10)<br>Chat 09-10: "tôi cần kiểm tra lại xem có kỳ kê khai không" | File 08-10 · Chat 09-10 | B-2 | 🟡 |
| AMB-TT607-15 | Ngày sinh validate thế nào theo từng "Định dạng"? Thông báo lỗi? | "Không hiển thị với nhập đủ ngày/tháng khi chọn định dạng yyyy. Không nhập được ngày không tồn tại. Ngày trong tương lai nhập được bình thường. Bỏ trống Không chọn tô đỏ và khi xem tờ khai/trình ký/ký và gửi báo lỗi "\<Tên trường\> không được để trống"" (File 08-10)<br>Chat 09-10: nhập sai "nghĩa là nhập vào thì ko hiển thị gì, vẫn tô đỏ ô input và khi ký báo lỗi" · bỏ trống: chọn **(a) ô bị tô đỏ, và báo lỗi khi bấm Xem tờ khai, Trình ký, Ký và gửi** | File 08-10 · Chat 09-10 | B-3 · B-4 | 🟡 |
| AMB-TT607-17 | "Tối đa 06 file (gồm tờ khai)" đếm thế nào? Tờ khai có tính vào 5MB không? | "1. Nếu có khai báo tờ khai TK1-TS thì được tải tối đa 5 tệp <=5MB · 2. Nếu có khai báo tờ khai TK1-TS và D01-TS thì được tải tối đa 4 tệp <=5MB" (File 08-10)<br>Chat 09-10: 5MB "tính tổng hết" · lỗi vượt số tệp: "Thông báo / Tổng dung lượng các tệp không được vượt quá 05 MB." · đã tải 5 tệp rồi mới thêm D01: "tôi cần confirm lại BA" | File 08-10 · Chat 09-10 | B-5 · ý 3 chờ BA | 🔴 |
| AMB-TT607-18 | Đuôi `.jpeg`/`.xls`/viết hoa? Giới hạn từng tệp? Tệp 0 byte, trùng tên? Xem trước xml/xlsx? | "1. … -> Confirm lại sau · 2. Không giới hạn dung lượng từng tệp · 3. Tệp 0 byte, tệp trùng tên đều nhận · 4. … không xem được xml và xlsx" (File 08-10)<br>Chat 09-10: bấm Xem xml/xlsx → "nút bị ẩn" | File 08-10 · Chat 09-10 | ý 1 chờ xác nhận | 🟡 |
| AMB-TT607-19 | Sau Trình ký / Ký và gửi hồ sơ ở trạng thái gì? Còn sửa / xóa / sao chép được không? | "1. Khi click Trình ký thì phải điền đầy đủ thông tin bắt buộc, nếu không điền hết thì thông báo lỗi đúng trường, Click trình ký thành công thì trở về màn hình danh sách thủ tục, và TRẠNG THÁI hiển thị trình ký, không sinh số hồ sơ, khi click vào checkbox thủ tục vừa trình ký thì có thể sao chép/thu hồi/từ chối ký/ký và gửi. · 2. Khi click Ký và gửi thì phải điền đầy đủ thông tin bắt buộc, nếu không điền hết thì thông báo lỗi đúng trường, Click ký và gửi thành công thì trở về màn hình danh sách thủ tục, và TRẠNG THÁI hiển thị Gửi thành công, có sinh số hồ sơ và lưu lại số hồ sơ cho tôi, khi click vào checkbox thủ tục vừa ký và gửi thì có thể sao chép." (File 08-10)<br>Chat 09-10: nhãn trạng thái "Trình ký" · "trình ký và ký chỉ sao chép không có nút chỉnh sửa. Chỉnh sửa chỉ áp dụng cho hồ sơ lưu nháp" · "có cần test. khi thu hồi thì trạng thái trình ký > Lưu nháp, và hoạt động đúng với hồ sơ lưu nháp. Từ chối ký thì trạng thái trở thành Từ chối ký và hồ sơ đó chỉ sao chép được" | File 08-10 · Chat 09-10 | B-6 · B-7 · B-8 | 🔴 |
| AMB-TT607-20 | Mã số BHXH ở D01 khác TK1 thì dùng giá trị nào? Hai tab đồng bộ không? "NLĐ" có phải NTG không? | "Nhập ở tờ khai nào thì khi view hiển thị đúng tờ khai đã nhập đó. NLĐ là người tham gia (NTG). Thông tin sẽ được lấy từ NTG đó. Khi gửi đi cần check có thông tin nào khác với thông tin NTG thì hiển thị thông báo: Xác nhận với nội dung thông tin NTG trên tờ khai khác với thông tin trong danh sách NTG. Bấm "Xác nhận" để tiếp tục Ký và Gửi BHXH. Bấm Hủy bỏ: Tắt popup, không thực hiện trình ký, tờ khai giữ nguyên." | File 08-10 | B-9 | 🔴 |
| AMB-TT607-23 | Sửa NTG xong có quay lại màn hình thủ tục không? Dữ liệu nhập dở có mất không? Lưới có tự lấy dữ liệu mới không? | "Sửa NTG xong quay lại màn hình thủ tục phải load lại data hoặc xóa NTG vừa sửa đi và thêm lại sẽ lấy dữ liệu mới nhất đã sửa" | File 08-10 | B-11 | 🟡 |
| AMB-TT607-24 | Bỏ NTG khỏi lưới thế nào? Chuyển 1 NTG hai lần có trùng dòng không? Tối đa bao nhiêu NTG? | "1. Bỏ 1 NTG khỏi lười bằng cách click vào icon 'Thùng rác' ngay cột Họ và tên (2) · 2. Có thêm 1 lúc 2 NTG được không hiển thị lỗi · 3. … Check performance cho tôi khoảng 50 or 100 NTG" | File 08-10 | B-12 | 🟡 |
| AMB-TT607-26 | Validation Số điện thoại, Mã số hộ gia đình, Mã số BHXH, độ dài Địa chỉ nơi nhận? Câu lỗi bỏ trống "Nội dung thay đổi yêu cầu"? | "Check đúng theo tài liệu phân tích, phần nào ko có độ dài ko cần check" | File 08-10 | B-13 | 🟡 |
| AMB-TT607-28 | D01: Ngày hiệu lực ≥ Ngày ban hành? Ngày sai định dạng báo gì? Cơ quan ban hành có điền sẵn tên đơn vị? | "1. … -> không check · 2. … -> Không hiển thị kết quả nhập · 3. Tôi cần confirm lại BA" | File 08-10 | ý 3 chờ BA · ý 2 xem B-3 | 🟡 |
| AMB-TT607-29 | Tìm kiếm gần đúng có bỏ qua dấu và hoa/thường không? Tìm theo một phần mã BHXH? | "Tìm kiếm "gần đúng" phải có dấu tiếng Việt mới tìm kiếm đúng được và tìm kiếm chữ hoa/thường đều được, không phân biệt." | File 08-10 | B-14 | 🟢 |
| AMB-TT607-31 | Trình ký bị chặn vì còn lỗi: thông báo dạng gì, câu chữ gì? | "Hiển thị dạng thông báo góc phải (Toast) trên cùng khoảng thời gian đủ để đọc lỗi rồi biến mất. Lỗi ở trường nào thì hiển thị đúng thông tin lỗi trường đó và trỏ tới đúng tab bị lỗi" | File 08-10 | B-15 | 🟡 |
| AMB-TT607-32 | D01: đã thêm dòng thì ô \* bắt buộc? Thêm / xóa dòng thế nào? Một NTG nhiều dòng? | "1. … -> Đúng · 2. -> Thêm bằng thao tác chọn NTG bất kỳ bằng cách click vào checkbox rồi chọn option bất kỳ được hiển thị · -> Xóa bằng icon 'Thùng rác' cột Họ và tên (2) · 3. … -> Hiện tại không chặn có thể thêm nhiều NTG cùng lúc và nhiều dòng được" | File 08-10 | B-16 | 🔴 |
| AMB-TT607-34 | Tích phụ lục mà NTG không có TV HGĐ: câu lỗi khi Ký và gửi? Trình ký / Lưu tạm có bị chặn? | "1. … câu thông báo lỗi khi Ký và gửi là: Lỗi / TK1TS dòng 1: Đã chọn gửi kèm phụ lục thành viên hộ gia đình nhưng danh sách thành viên đang trống · 2. Trình ký/lưu tạm/xem tờ khai không bị chặn khi tích phụ lục mà NTG không có thành viên HGĐ." | File 08-10 | B-17 (popup hay toast) | 🔴 |
| AMB-TT607-36 | Sao chép nằm ở đâu, bản sao trạng thái gì? "Các phần liên quan tới 607" gồm màn hình nào? | "Test hết những phần liên quan tới thủ tục 607. Chức năng sao chép khi user click vào checkbox của thủ tục cần sao chép sẽ hiển thị button đó." | File 08-10 | B-18 | 🔴 |
| AMB-TT607-37 | Điều kiện hiện popup Trở lại? Chưa nhập gì thì về đâu? Câu chữ popup lệch đích đến? | "Bấm hủy bỏ thì giữ nguyên màn hình tạo thủ tục đang được tạo · Bấm đồng ý thì quay trở về màn tạo thủ tục mới" | File 08-10 | B-19 | 🔴 |
| AMB-TT607-38 | Số thứ tự cột và câu hướng dẫn dropzone theo bản nào? | Dropzone: "Kéo thả tệp vào đây hoặc chọn tệp từ máy tính" | File 08-10 | B-20 (số thứ tự cột) | 🟢 |

#### ❔ Chưa trả lời

| Mã | Câu hỏi | Trạng thái | Mức |
|---|---|---|---|
| AMB-TT607-35 | "Vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" có nghĩa là hồ sơ **giữ ảnh chụp dữ liệu** tại lúc lưu/ký — tức sau đó sửa hồ sơ NTG (VD đổi thành viên HGĐ) thì hồ sơ vẫn hiện dữ liệu cũ? Quy tắc này chỉ áp cho phụ lục HGĐ hay cho **mọi** trường của TK1-TS? | "tôi cần confirm lại sau" (File 08-10) | 🔴 |
| AMB-TT607-42 | Đóng tab/cửa sổ chỉ hiện được hộp thoại mặc định của trình duyệt — chấp nhận được không? Nút Back có hiện popup của ứng dụng không? | "Tôi chưa hiểu phần này, hãy giải thích cho tôi nút đó nút nào" (File 08-10) → đã giải thích ở B-21 | 🔴 |

#### 🔁 Lượt hỏi 2 (09-10-2026)

> Viết câu trả lời vào dòng `Trả lời:` ngay dưới mỗi câu. Câu trả lời đã nhận ở Chat 09-10 đã được chuyển vào 2 bảng trên.

**Phát sinh từ câu trả lời mới**

**B-1 (AMB-TT607-13 ý 2).** Câu "Và có cho sửa thông tin này" nghĩa là gì?
- (a) Các ô đó **sửa được trên lưới TK1**, và preview phải hiện giá trị đã sửa.
- (b) Sửa được **ngay trong popup Xem tờ khai**.
- (c) Ý khác.

Trả lời:

**B-1b (AMB-TT607-13, đính chính).** Lần trước tôi hỏi nhầm: lưới TK1 theo Conf **không có** cột CCCD (REQ-TT607-25). Vậy [06] và [14.5] CCCD chỉ lấy từ NTG, không sửa được trên lưới, đúng không? Nếu màn hình thực tế có cột CCCD thì tôi sẽ ghi nhận khi recon.

Trả lời:

**B-1c (AMB-TT607-13 ý 3).** Lưới TK1 **có** cặp Tỉnh/TP – Xã/phường "Nơi đăng ký giấy khai sinh", sửa được (REQ-TT607-26). Ô [14.4] trên preview lấy:
- (a) giá trị **trên lưới** (mặc định lấy từ "Nơi cấp giấy khai sinh" của NTG, người dùng sửa thì theo giá trị đã sửa), hay
- (b) **luôn** lấy "Nơi cấp giấy khai sinh" của NTG, bỏ qua giá trị sửa trên lưới?

Trả lời:

**B-2 (AMB-TT607-14).** Bạn đang kiểm tra màn hình có Kỳ kê khai không. Nếu **có**: chọn được lùi/tiến xa nhất bao nhiêu tháng, hay không giới hạn? Nếu **không có**: tôi đổi REQ-TT607-02, 03, 04 sang 🔴 Deprecated.

Trả lời:

**B-3 (AMB-TT607-15 ý 1 · AMB-TT607-28 ý 2).** Nhập ngày sai (sai định dạng / ngày không tồn tại) thì khi ký báo lỗi với **câu chữ** gì? Có phải "\<Tên trường\> không được để trống" không? Áp cho cả Trình ký và Xem tờ khai không, hay chỉ Ký và gửi? Ngày ở D01 (Ngày ban hành, Ngày hiệu lực) có xử lý giống vậy không?

Trả lời:

**B-4 (AMB-TT607-15 ý 3, 4 — chưa được trả lời).**
1. Bấm **Xem tờ khai** khi còn trống trường bắt buộc: báo lỗi **và không mở** preview, hay báo lỗi nhưng **vẫn mở** preview?
2. Bấm **Lưu tạm** khi còn trống trường bắt buộc: có tô đỏ không? (REQ-TT607-75 theo Conf đang ghi là có, và Lưu tạm vẫn lưu được.)

Trả lời:

**B-5 (AMB-TT607-17 ý 1, 2).**
1. "Tính tổng hết": tờ khai TK1-TS / D01-TS có hiện thành **dòng** trong bảng "Tài liệu đã đính kèm" và được cộng vào dòng "Tổng dung lượng" không? Mỗi tờ khai nặng khoảng bao nhiêu?
2. Bạn trả lời câu báo lỗi **số tệp** bằng câu của **dung lượng**. Vậy khi vượt **số tệp** (tệp thứ 6 khi chỉ có TK1, tệp thứ 5 khi có TK1 + D01), câu báo lỗi là:
   - (a) "Số lượng tệp đính kèm không được vượt quá 06 tệp." (REQ-TT607-68), hay
   - (b) "Tổng dung lượng các tệp không được vượt quá 05 MB." (như bạn ghi)?
3. Tiêu đề "Thông báo" áp cho cả 3 lỗi đính kèm (dung lượng, định dạng, số tệp) đúng không?

Trả lời:

**B-6 (AMB-TT607-19 ý 2).** Ở File 08-10 bạn ghi: hồ sơ Trình ký tích checkbox thì có **Sao chép / Thu hồi / Từ chối ký / Ký và gửi**. Chat 09-10 ghi "Trình ký … chỉ sao chép". Tôi hiểu là hồ sơ Trình ký vẫn có đủ 4 nút trên, chỉ là **không có nút Chỉnh sửa**. Đúng không?

Trả lời:

**B-7 (AMB-TT607-19 ý 3).** Bấm Thu hồi / Từ chối ký có **popup xác nhận** hoặc **ô nhập lý do** không? Nếu có thì câu chữ là gì?

Trả lời:

**B-8 (AMB-TT607-19 ý 4 — chưa được trả lời).** Hồ sơ **Lưu nháp** tích checkbox thì có những thao tác nào (Chỉnh sửa, Sao chép, Xóa, Trình ký, Ký và gửi…)?

Trả lời:

**Đã hỏi ở lượt 1, chưa được trả lời**

**B-9 (AMB-TT607-20).**
1. Popup "thông tin NTG trên tờ khai khác với danh sách NTG" hiện khi bấm **Ký và gửi**, **Trình ký**, hay cả hai? (Câu "Hủy bỏ: không thực hiện trình ký" làm tôi chưa chắc.)
2. Tiêu đề và nội dung có đúng nguyên văn: tiêu đề "Xác nhận", nội dung "Thông tin NTG trên tờ khai khác với thông tin trong danh sách NTG. Bấm "Xác nhận" để tiếp tục Ký và Gửi BHXH.", 2 nút Xác nhận / Hủy bỏ?
3. Những trường nào được so sánh? Mã số BHXH nhập ở D01 có tính không?
4. Bấm Xác nhận và gửi thành công thì hồ sơ NTG bị **cập nhật theo tờ khai** (REQ-TT607-81) đúng không?

Trả lời:

**B-10 (AMB-TT607-22).** Môi trường test có sẵn hồ sơ 607 tạo bằng **giao diện cũ** không? Không có thì các TC này ghi BLOCKED.

Trả lời:

**B-11 (AMB-TT607-23).** Sửa NTG xong quay lại: **kỳ vọng** là lưới **tự** lấy dữ liệu mới, còn "xóa NTG rồi thêm lại" chỉ là cách làm vòng? Dữ liệu đang nhập dở của **các NTG khác** trên lưới có bị mất không?

Trả lời:

**B-12 (AMB-TT607-24).**
1. Chuyển **cùng một NTG** sang lưới 2 lần có tạo **2 dòng trùng** không?
2. Kiểm hiệu năng 50 / 100 NTG: ngưỡng đạt là gì (thời gian chuyển / lưu ≤ bao nhiêu giây, hay chỉ cần không treo, không lỗi)?

Trả lời:

**B-13 (AMB-TT607-26).** Bỏ trống "Nội dung thay đổi yêu cầu" thì báo "Nội dung thay đổi yêu cầu không được để trống" đúng không?

Trả lời:

**B-14 (AMB-TT607-29).**
1. Gõ **không dấu** ("nguyen") thì **không** tìm ra "Nguyễn", đúng không?
2. Gõ **một phần** Mã số BHXH (ví dụ 4 số giữa) có tìm ra không?

Trả lời:

**B-15 (AMB-TT607-31).**
1. Lỗi nằm ở **nhiều tab** cùng lúc thì nhảy tới tab nào? Toast hiện một lỗi hay tất cả?
2. Tooltip khi hover vào ô lỗi (REQ-TT607-74) còn không, hay toast thay hẳn tooltip?

Trả lời:

**B-16 (AMB-TT607-32).**
1. "Chọn option bất kỳ được hiển thị": là menu nào, có những option gì (ví dụ icon ⋮ → "Thêm vào D01-TS")?
2. Bạn ghi "chọn **NTG bất kỳ**", nhưng REQ-TT607-44 (Conf) ghi D01 **chỉ được thêm NTG đã tích ở TK1-TS**. Còn giữ REQ-TT607-44 không?

Trả lời:

**B-17 (AMB-TT607-34).** Lỗi "TK1TS dòng 1: Đã chọn gửi kèm phụ lục…" hiện dạng **popup** tiêu đề "Lỗi", hay **toast** góc phải như AMB-TT607-31?

Trả lời:

**B-18 (AMB-TT607-36).**
1. "Test hết những phần liên quan tới 607" gồm những màn hình nào? (Gợi ý để bạn gạch bớt / thêm: danh sách thủ tục · chi tiết hồ sơ · in · tra cứu kết quả · thu hồi · từ chối ký · …)
2. Bản sao chép có trạng thái gì (Lưu nháp?) và mở ra ở màn hình nào?

Trả lời:

**B-19 (AMB-TT607-37).**
1. Thế nào là "đã nhập thông tin NTG" để popup Trở lại hiện (đã chuyển ≥ 1 NTG sang lưới? chỉ đổi Kỳ kê khai?)?
2. **Chưa** nhập gì mà bấm Trở lại thì về đâu?
3. Popup ghi "trở lại **danh sách**" nhưng Đồng ý lại về màn **tạo thủ tục mới** — câu chữ này đúng hay là bug?

Trả lời:

**B-20 (AMB-TT607-38).** Số thứ tự cột theo bản nào: Conf (13.x / 14.x), mockup TK1 (12.x / 13.x)? Mockup D01 có 2 cột cùng số 4.5, không có 4.3 — đúng là gì?

Trả lời:

**B-21 (AMB-TT607-42).** Giải thích: có **hai hành động của trình duyệt**, không phải nút trên màn hình xCare:
- **Nút Back của trình duyệt** — mũi tên ← góc trên bên trái cạnh thanh địa chỉ, hoặc Alt + ←. REQ-TT607-85 yêu cầu hiện popup **của xCare** "Bạn có chắc muốn trở lại danh sách?". Làm được.
- **Đóng tab / cửa sổ** — dấu X trên tab, hoặc Ctrl + W. Trình duyệt chỉ cho hiện hộp thoại **mặc định của Chrome** (kiểu "Rời khỏi trang web? Các thay đổi có thể không được lưu", nút Rời khỏi / Hủy). Ứng dụng **không đổi được** câu chữ hay giao diện hộp thoại này (REQ-TT607-86).

Câu hỏi:
1. Đóng tab: chỉ cần hiện hộp thoại mặc định của Chrome là đạt?
2. Nút Back: phải hiện đúng popup của xCare như REQ-TT607-85?

Trả lời:

**Câu chung của dự án (phát sinh 09-10)**

**B-22 (năng lực kiểm thử — `docs/requirements/README.md`).** Bạn xác nhận QA "có quyền" gọi API / truy vấn CSDL. Để viết TC Vòng 3 (Technical):
1. CSDL loại gì (SQL Server, PostgreSQL, Oracle…)? Truy cập bằng công cụ gì?
2. Quyền **chỉ đọc** hay được **ghi / xoá** (VD dọn dữ liệu test)?
3. Gọi API bằng cách nào: có tài liệu API (Swagger / Postman) không, hay chỉ bắt request trên trình duyệt?
4. Có xem được **nhật ký hoạt động** (log hệ thống / lịch sử thao tác hồ sơ) không?

Trả lời:

**Bạn ghi sẽ xác nhận sau (giữ treo):** AMB-TT607-17 ý 3 (đã tải 5 tệp rồi thêm D01 — chờ BA) · AMB-TT607-18 ý 1 (`.jpeg`, `.xls`, đuôi viết hoa) · AMB-TT607-28 ý 3 (Cơ quan ban hành có tự điền tên đơn vị — chờ BA) · AMB-TT607-35 (giữ ảnh chụp dữ liệu tại lúc lưu/ký).

### 7.2. Rủi Ro Kiểm Thử

| Mã | Rủi ro | Mô tả | Mitigation |
|---|---|---|---|
| RISK-TT607-01 | Tài liệu chưa ổn định | Ticket đã ở trạng thái Ready for UAT, nhưng Confluence vẫn được sửa (bản 14 lúc 06-10-2026 09:25). Mockup lệch đặc tả ở nhiều điểm | Ghi số phiên bản Confluence vào TC; khi trang đổi phiên bản thì chạy `/update-requirements-from-ticket` |
| RISK-TT607-02 | Ký số & gửi cổng BHXH | Hồ sơ gửi đi không thu hồi được. Lỗi ký số / cổng chưa có luồng xử lý được đặc tả | Chỉ dùng tài khoản test do người yêu cầu cấp. Khi ký/gửi lỗi: **ghi lại số hồ sơ** vào execution report để người yêu cầu kiểm tra (Chat 06-10) |
| RISK-TT607-03 | Dữ liệu NTG đa dạng | Cần đủ loại NTG: có / chưa có mã BHXH · **có / không** khai báo thành viên HGĐ · email sai · thiếu trường bắt buộc · đủ nhiều NTG để thử cuộn | Tạo bộ NTG riêng, tên truy vết được (`auto_607_<timestamp>`) |
| RISK-TT607-04 | Ghi ngược hồ sơ NLĐ | Ký và gửi làm thay đổi hồ sơ NLĐ, có thể ảnh hưởng dữ liệu của người khác nếu môi trường dùng chung | Môi trường `dev` **dùng chung**, được phép Ký và gửi (Chat 09-10) → chỉ dùng NTG do QA tạo, tên truy vết được; không Ký và gửi trên NTG của người khác |
| RISK-TT607-05 | Kiểm tra "dữ liệu không đổi sau khi lưu" (REQ-41/42) | Muốn chứng minh hồ sơ giữ dữ liệu cũ thì phải **sửa hồ sơ NTG sau khi lưu** rồi mở lại hồ sơ — nếu không sửa, phép thử không chứng minh được gì | Thiết kế TC theo 4 bước trạng thái sạch (skill 4.3.2) sau khi AMB-TT607-35 được trả lời |
| RISK-TT607-06 | Bộ tệp mẫu | Cần tệp đúng 5MB, 5MB + 1 byte, đuôi lạ, 0 byte, tên tiếng Việt, tên dài | Sinh sẵn bằng `/generate-test-data` |
| RISK-TT607-07 | Hộp thoại khi đóng tab / Back | Hộp thoại của trình duyệt khác nhau theo trình duyệt, khó tự động hoá | Đánh dấu manual; chỉ assert có hay không có hộp thoại (skill 4.3.6) |
| RISK-TT607-08 | Phân quyền theo đơn vị | Cần ≥ 2 tài khoản thuộc 2 đơn vị khác nhau | Chỉ đơn vị của tài khoản 1 ký được. Có tài khoản đơn vị khác để **đăng nhập xem dữ liệu** (không ký được) — người dùng điền vào `XCARE_USER2_*` trong `.env` (Chat 09-10). Ca phân quyền chỉ kiểm phía xem, không ký bằng tài khoản 2 |
| RISK-TT607-09 | Hồ sơ 607 cũ | Hồ sơ tạo trên giao diện cũ phải mở bằng giao diện mới, dữ liệu Huyện cũ được đổi (REQ-TT607-99) — có thể không mở được | Cần dữ liệu hồ sơ cũ trên môi trường test (B-10); không có thì TC ghi BLOCKED |

## 8. Ma Trận Trạng Thái

| Trạng thái hiện tại | Hành động | Trạng thái sau | Nguồn |
|---|---|---|---|
| (Mới) | Lưu tạm | **Lưu nháp** | REQ-TT607-72 |
| (Mới) / Lưu nháp | Trình ký | **Trình ký** (không sinh số hồ sơ) | REQ-TT607-93 |
| (Mới) / Lưu nháp / Trình ký | Ký và gửi | **Gửi thành công** (sinh số hồ sơ) | REQ-TT607-94 |
| Trình ký | Thu hồi | **Lưu nháp** | REQ-TT607-95 |
| Trình ký | Từ chối ký | **Từ chối ký** | REQ-TT607-96 |
| Lưu nháp | Chỉnh sửa | Hiển thị đúng dữ liệu lúc Lưu tạm | REQ-TT607-41 · AMB-TT607-35 |
| Lưu nháp / Trình ký / Gửi thành công / Từ chối ký | Sao chép | Hiển thị đúng dữ liệu đã lưu/ký · trạng thái bản sao: ❔ B-18 | REQ-TT607-42 · AMB-TT607-35 |
| Ký gửi lỗi (ký số / cổng BHXH) | — | ❔ Không đề cập — ghi lại số hồ sơ | RISK-TT607-02 |

## 9. Tóm Tắt Acceptance Criteria (Checklist)

Nhóm có cờ 🔴 = còn AMB 🔴 treo, **chưa đủ** căn cứ sinh test case.

- [ ] **Khung màn hình & phân quyền** — REQ 01–08 · 🟡 B-2 (có Kỳ kê khai không)
- [ ] **Panel NTG** — REQ 09–22, 100, 101 · 🟡 B-11, B-12, B-14
- [ ] **TK1-TS: lấy dữ liệu từ NTG & quyền sửa** — REQ 23–27, 87 · ✅
- [ ] **TK1-TS: validation** — REQ 28–36, 89, 105 · 🟡 B-3, B-4, B-13
- [ ] **TK1-TS: phụ lục hộ gia đình** — REQ 37–40 · 🔴 AMB-34 (chỉ còn B-17: popup hay toast)
- [ ] **Giữ đúng dữ liệu khi sửa / sao chép** — REQ 41–42 · 🔴 AMB-35, 36 (B-18)
- [ ] **D01-TS** — REQ 43–53, 97, 104 · 🔴 AMB-32 (B-16) · 🟡 AMB-28 (B-3, chờ BA)
- [ ] **Giấy tờ đính kèm** — REQ 54–69, 90–92, 106 · 🔴 AMB-17 (B-5, chờ BA) · 🟡 AMB-18 ý 1
- [ ] **Lưu tạm & tô lỗi** — REQ 70–75, 103 · 🟡 B-4, B-15
- [ ] **Xem tờ khai** — REQ 76–77, 88, 102 · 🔴 AMB-13 (B-1, B-1b, B-1c)
- [ ] **Trình ký / Ký và gửi / Thu hồi / Từ chối ký** — REQ 78–81, 93–99 · 🔴 AMB-19 (B-6, B-7, B-8), AMB-20 (B-9) · 🟡 B-10
- [ ] **Trở lại & rời trang** — REQ 82–86 · 🔴 AMB-37 (B-19), AMB-42 (B-21)

## 10. Khuyến Nghị Cho Kiểm Thử

1. **Trả lời câu B-1 → B-21 và chốt 10 AMB 🔴 còn mở** (13, 17, 19, 20, 32, 34, 35, 36, 37, 42 — xem 7.1) trước khi sinh test case cho các nhóm có cờ 🔴. Các nhóm còn lại có thể làm trước.
2. **Recon UI thật trước khi viết TC.** Mockup lệch đặc tả nhiều chỗ, nên phải lấy câu chữ, nhãn nút và trạng thái cột từ màn hình thật (cần URL và tài khoản trong `.env`).
3. Ưu tiên kiểm **BR-1** (mức chặn của 3 nút khi còn lỗi) và **BR-2** (chỉ Ký và gửi mới ghi ngược vào NLĐ) — đây là hai rule có tác động dữ liệu lớn nhất.
4. Đối chiếu preview TK1-TS / D01-TS với **từng ô** của mẫu QĐ 490 / QĐ 595, đặc biệt ô Huyện (phải để trống) và các ô không có trên lưới nhập.
5. Kiểm REQ-41/42 bằng phép thử có thay đổi dữ liệu thật ở hồ sơ NTG sau khi lưu (RISK-TT607-05).
6. Ca biên đính kèm: tổng 5MB (gồm tờ khai) đúng biên và + 1 byte · chỉ TK1: tệp tải lên thứ 5 và thứ 6 · TK1 + D01: tệp thứ 4 và thứ 5 — câu báo lỗi chờ B-5.
7. Phân quyền: 2 tài khoản thuộc 2 đơn vị, kiểm chéo không thấy NTG / hồ sơ của nhau.
8. Ký và gửi chỉ chạy trên môi trường đã được xác nhận là test. Mọi lần lỗi phải ghi số hồ sơ.
9. Tách các ca hộp thoại trình duyệt (Back / đóng tab) thành manual.
10. Ngoài phạm vi: thủ tục 612, nội dung bên trong quy trình Trình ký, form tạo NTG, Nhập excel / nhóm "Chưa có phòng ban" / Mã NV (AMB-TT607-16).
11. Hiệu năng: lưới với 50 và 100 NTG (REQ-TT607-101) — ngưỡng đạt chờ B-12.

---

## Nhật ký phân tích

| Ngày | Nội dung |
|---|---|
| 06-10-2026 | Bản nháp đầu (mã tạm R-xx / Q-xx), lưu ở `docs/requirements/thu-tuc/` |
| 06-10-2026 | Nhận câu trả lời Chat 06-10 → đóng AMB-01…11. Cấp mã chính thức REQ-TT607-01→86 · AMB-TT607-01→42 · RISK-TT607-01→09. Chuyển file sang module `thu-tuc-607` |
| 09-10-2026 | Mốc git trước khi sửa: `40e1f21` (file đã có thay đổi chưa commit: câu trả lời người yêu cầu viết vào ngày 08-10 — bản sao lưu đầy đủ trước lần sửa này nằm ngoài repo). Nhận trả lời `File 08-10` và `Chat 09-10`. Mục 7.1 tổ chức lại: 22 AMB đã trả lời (thêm 12, 16, 21, 22, 25, 27, 30, 33, 39, 40, 41) · 18 trả lời một phần · 2 chưa trả lời (35, 42); câu trả lời giữ nguyên văn. Thêm câu hỏi lượt 2 B-1 → B-21. Thêm REQ-TT607-87 → 106 (mục 4.7). Sửa REQ-TT607-27 (Mã số BHXH luôn cho sửa) và thu hẹp REQ-TT607-41 (Chỉnh sửa chỉ áp cho Lưu nháp). Ghi chú câu trả lời vào REQ 02–04, 08, 11, 12, 18, 29–31, 36, 40, 42, 44, 49, 51, 53, 56, 66, 68, 70, 74, 75, 79, 81, 82, 84–86. Cập nhật mục 3, 4b, BR (5, 6, 8, thêm BR-9), mục 8, 9, 10, RISK-09 |
