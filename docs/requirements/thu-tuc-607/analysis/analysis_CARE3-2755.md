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
| **Nguồn phân tích** | ① Mô tả ticket (chỉ chứa link Confluence) · ② Comment Jira: **0 comment** · ③ Confluence pageId `143492085` "Thủ tục 607 - theo phân tích mới", **phiên bản 14**, sửa lúc 06-10-2026 09:25 · ④ 6/25 ảnh đính kèm trang (xem mục 6) · ⑤ **Câu trả lời của người yêu cầu trong chat ngày 06-10-2026** (viết tắt `Chat 06-10`) |
| **Dải mã đã dùng** | `REQ-TT607-01` → `REQ-TT607-86` · `AMB-TT607-01` → `AMB-TT607-42` · `RISK-TT607-01` → `RISK-TT607-09` |
| **Mã kế tiếp** | `REQ-TT607-87` · `AMB-TT607-43` · `RISK-TT607-10` — KHÔNG đánh lại từ 01 |
| **Mức độ đầy đủ** | ⚠️ **Đủ một phần.** Có 11 AMB đã được trả lời. Còn **31 AMB treo**, trong đó **11 AMB 🔴**. Các nhóm REQ có cờ 🔴 ở mục 9 **chưa đủ** căn cứ để sinh test case |

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
| Chỉnh sửa hồ sơ sau khi Lưu tạm / Trình ký / Ký gửi | ✅ | Chat 06-10 (phần phụ lục HGĐ) |
| Sao chép hồ sơ 607 | ✅ | Chat 06-10 — **vị trí chức năng chưa rõ** (AMB-TT607-36) |
| Phân quyền theo đơn vị | ✅ | Chat 06-10 |
| **Thủ tục 612** | ❌ **Ngoài phạm vi** | Chat 06-10: *"không cần check thủ tục 612, chỉ xem những phần liên quan tới thủ tục 607 thôi"* |
| Popup tạo mới NTG (pageId 84123415) | ⚪ Chỉ kiểm việc mở popup / quay lại màn hình | Conf §2 dẫn link; nội dung trang này chưa đọc |
| Bên trong quy trình Trình ký | ⚪ Chỉ kiểm điểm vào / điểm ra | Conf: *"như hệ thống hiện tại"* |
| Nhập excel · nhóm "Chưa có phòng ban" · Mã NV | ❔ Không đề cập trong tài liệu | AMB-TT607-16 |
| "Các phần liên quan tới thủ tục 607" khác (danh sách, chi tiết, in…) | ❔ Không đề cập trong tài liệu | AMB-TT607-36 |

## 4. Acceptance Criteria — Phân Tích Chi Tiết

Cột **Nguồn**: `Conf §x · dòng y` = bảng trong trang Confluence 143492085 (bản 14). `Chat 06-10` = câu trả lời của người yêu cầu ngày 06-10-2026. `Mockup <tên ảnh>` = ảnh đính kèm trang Confluence.

### 4.1. Khung màn hình & phân quyền

| REQ ID | Yêu cầu (trích nguyên văn khi có) | Nguồn |
|---|---|---|
| REQ-TT607-01 | Header hiển thị "607 \| Cấp lại sổ BHXH do mất, hỏng" | Chat 06-10 (đè Conf §2 dòng 1 — xem AMB-TT607-01) |
| REQ-TT607-02 | Kỳ kê khai là trường bắt buộc | Conf §2 · "Kỳ kê khai \| Date Picker \*" |
| REQ-TT607-03 | Kỳ kê khai mặc định bằng tháng/năm tại thời điểm mở màn hình | Conf §2 · "Mặc định là tháng năm hiện tại" |
| REQ-TT607-04 | Kỳ kê khai cho phép chọn lại | Conf §2 · "cho phép chọn lại" |
| REQ-TT607-05 | Màn hình chia 2 phần: "Phần 1: Danh sách người tham gia trong hệ thống" · "Phần 2: Màn hình nhập thông tin gồm 3 Tab: TK1-TS, D01-TS, Giấy tờ đính kèm" | Conf §2 · dòng mô tả |
| REQ-TT607-06 | "Màn hình có scollbar ngang dọc khi kích thước bảng vượt quá màn hình" | Conf §2 · dòng mô tả |
| REQ-TT607-07 | "Tab TK1-TS mặc định hiển thị" | Conf §3 · dòng đầu |
| REQ-TT607-08 | "User của đơn vị chỉ được sử dụng các tính năng của chính đơn vị này." | Chat 06-10 · phạm vi áp dụng: AMB-TT607-33 |

### 4.2. Panel danh sách người tham gia (NTG)

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-09 | "Cho phép tích chọn 1 hoặc nhiều người tham gia" | Conf §2 · P1 dòng 1 |
| REQ-TT607-10 | Mỗi dòng hiển thị "Họ và tên + (mã số bảo hiểm xã hội)" | Conf §2 · P1 dòng 2 |
| REQ-TT607-11 | Tìm kiếm gần đúng theo Họ và tên | Conf §2 · P1 dòng 2 · "cho phép nhập Họ và tên hoặc Mã số BHXH để tìm kiếm gần đúng" |
| REQ-TT607-12 | Tìm kiếm gần đúng theo Mã số BHXH | Conf §2 · P1 dòng 2 (cùng câu trên) |
| REQ-TT607-13 | Icon Thêm hiển thị tooltip "Thêm mới người tham gia" | Conf §2 · P1 icon 1 |
| REQ-TT607-14 | Bấm icon Thêm → "hiển thị pop-up thêm người tham gia ngay trên màn hình này" | Conf §2 · P1 icon 1 |
| REQ-TT607-15 | Icon Sửa "Mặc định disable" | Conf §2 · P1 icon 2 |
| REQ-TT607-16 | Icon Sửa có tooltip "Sửa thông tin người tham gia" | Conf §2 · P1 icon 2 |
| REQ-TT607-17 | Icon Sửa "Enable khi tích chọn 1 người tham gia" | Conf §2 · P1 icon 2 |
| REQ-TT607-18 | Bấm Sửa → màn hình chỉnh sửa NTG "load lên thông tin hiện tại của người tham gia" | Conf §2 · P1 icon 2 |
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
| REQ-TT607-27 | Mã số BHXH: "Trường hợp Mã số BHXH của người tham gia chưa có thì cho nhập" | Conf §3 · dòng 3 · trường hợp NTG đã có mã: AMB-TT607-40 |
| REQ-TT607-28 | Định dạng ngày sinh có đúng 3 giá trị: `dd/mm/yyyy` · `mm/yyyy` · `yyyy` | Conf §3 · dòng "Định dạng" |
| REQ-TT607-29 | Hình thức nhận kết quả có đúng 2 giá trị: "Nhận bản điện tử" · "Nhận bản giấy" | Conf §3 · dòng 12 |
| REQ-TT607-30 | Bỏ trống trường bắt buộc → tô đỏ, báo "\<Tên trường\> không được để trống". Áp cho: Định dạng · Ngày sinh · Giới tính · Quốc tịch · Dân tộc · Tỉnh/TP và Xã/phường (nơi ĐK khai sinh) · Tỉnh/TP, Xã/phường và Địa chỉ nơi nhận (nhận kết quả) | Conf §3 · dòng "Định dạng", 4, 5, 7, 8, 13.1, 13.3, 14.1, 14.3, 14.4 |
| REQ-TT607-31 | "Nội dung thay đổi yêu cầu" là trường bắt buộc | Conf §3 · dòng 15 · "Text Area \*" — câu thông báo lỗi: AMB-TT607-26 |
| REQ-TT607-32 | "Nội dung thay đổi yêu cầu" tối đa 1000 ký tự | Conf §3 · dòng 15 |
| REQ-TT607-33 | "Hồ sơ kèm theo" không bắt buộc, tối đa 1000 ký tự | Conf §3 · dòng 16 |
| REQ-TT607-34 | Email đúng định dạng `xxx@xxx.xxx`. Nhập sai → "Email không đúng định dạng" | Conf §3 · dòng 11 |
| REQ-TT607-35 | "Sai định dạng, người dùng vẫn ký → báo lỗi 'Email không đúng định dạng'" | Conf §3 · dòng 11 |
| REQ-TT607-36 | Cột Quận/huyện "chỉ hiển thị giao diện còn không có data" | Chat 06-10 · chi tiết: AMB-TT607-25 |
| REQ-TT607-37 | "Gửi kèm phụ lục thành viên hộ gia đình": "Mặc định không tích chọn" | Conf §3 · dòng 17 |
| REQ-TT607-38 | Checkbox phụ lục: "hệ thống tự động tích chọn nếu Người tham gia chưa có Mã số bHXH" | Conf §3 · dòng 17 |
| REQ-TT607-39 | "Khi tích đính kèm thành viên hộ gia đình thì Xem tờ khai phải hiển thị đúng thông tin của NTG đó" | Chat 06-10 |
| REQ-TT607-40 | "Nếu NTG không khai báo thành viên hộ gia đình mà ở màn tạo thủ tục có tích chọn đính kèm thì khi ký và gửi hiển thị thông báo lỗi" | Chat 06-10 · câu thông báo: AMB-TT607-34 |
| REQ-TT607-41 | Lưu tạm / Trình ký / Ký và gửi rồi **chỉnh sửa** hồ sơ → "vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" | Chat 06-10 · cách hiểu: AMB-TT607-35 |
| REQ-TT607-42 | Lưu tạm / Trình ký / Ký và gửi rồi **sao chép** hồ sơ → "vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" | Chat 06-10 · cách hiểu: AMB-TT607-35, AMB-TT607-36 |

### 4.4. Tab D01-TS

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-43 | Tờ khai D01-TS là **tùy chọn** | Chat 06-10 · "Tùy chọn" — quy tắc khi đã thêm dòng: AMB-TT607-32 |
| REQ-TT607-44 | "tại tờ khai TK1-TS người dùng tích chọn NTG nào thì ở tờ khai D01-TS chỉ được thêm NTG đó" | Conf §4 · dòng đầu |
| REQ-TT607-45 | Hiển thị nguyên văn: "Bảng kê thông tin (D01-TS) phục vụ các trường hợp đặc thù theo yêu cầu của cơ quan BHXH, đơn vị nhập thông tin trong bảng dưới đây để thực hiện kê khai bổ sung khi có yêu cầu cơ quan BHXH." | Conf §4 · dòng đầu |
| REQ-TT607-46 | Họ và tên: "Lấy thông tin từ NTG, không cho phép sửa" | Conf §4 · dòng 1 |
| REQ-TT607-47 | Cột Họ và tên và cột Mã số BHXH được cố định khi cuộn ngang | Conf §4 · dòng 1, 2 |
| REQ-TT607-48 | Mã số BHXH: "hệ thống tự động lấy từ người tham gia" | Conf §4 · dòng 2 |
| REQ-TT607-49 | Mã số BHXH: "Cho phép nhập lại thông tin Mã số BHXH" | Conf §4 · dòng 2 · đồng bộ với TK1: AMB-TT607-20 |
| REQ-TT607-50 | Độ dài tối đa: Họ và tên 100 · Mã số BHXH 10 · Tên, loại văn bản 100 · Số hiệu 50 · Cơ quan ban hành 255 · Trích yếu 500 · Trích lược nội dung cần thẩm định 1000 | Conf §4 · cột "Độ dài" dòng 1, 2, 3, 4, 7, 8, 9 |
| REQ-TT607-51 | Bỏ trống ô bắt buộc → "tô đỏ nếu chưa nhập". Áp cho: Tên, loại văn bản · Số hiệu · Ngày ban hành · Ngày hiệu lực · Cơ quan ban hành · Trích yếu · Trích lược nội dung cần thẩm định | Conf §4 · dòng 3 → 9 · áp khi nào: AMB-TT607-32 |
| REQ-TT607-52 | Ngày ban hành: "Định dạng dd/mm/yyyy" | Conf §4 · dòng 5 |
| REQ-TT607-53 | Ngày hiệu lực: định dạng `dd/mm/yyyy` | Conf §4 · dòng 6 · cột "Độ dài" |

### 4.5. Tab Giấy tờ đính kèm

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-54 | Click vào khu vực tải tệp để chọn tệp | Conf §5 · dòng 1 |
| REQ-TT607-55 | Kéo-thả tệp trực tiếp vào khung | Conf §5 · dòng 1 |
| REQ-TT607-56 | Hiển thị nguyên văn: "Định dạng cho phép: pdf, xml, jpg, xlsx. Tối đa 06 file (gồm tờ khai). Tổng dung lượng tối đa 5MB" | Conf §5 · dòng 2 · Chat 06-10 xác nhận |
| REQ-TT607-57 | Icon minh hoạ thay đổi theo phần mở rộng tệp (PDF, XLSX, JPG, XML) | Conf §5 · dòng 3 |
| REQ-TT607-58 | Tên tệp hiển thị "theo tên gốc của file khi upload" | Conf §5 · dòng 4 |
| REQ-TT607-59 | Dung lượng từng tệp tính bằng MB, "làm tròn 2 chữ số thập phân" | Conf §5 · dòng 5 |
| REQ-TT607-60 | Xem: "xem trước nội dung file đã tải (preview), không tải file về máy" | Conf §5 · dòng 6 |
| REQ-TT607-61 | Tải xuống: "tải file đã đính kèm về máy tính cá nhân" | Conf §5 · dòng 7 |
| REQ-TT607-62 | Bấm Xóa → popup "Xác nhận" với nội dung "Bạn có chắc chắn muốn xóa tài liệu này?" | Conf §5 · dòng 8 · Mockup `image2026-9-8_17-19-44.png` |
| REQ-TT607-63 | Popup xóa → Xác nhận: "Xóa file đính kèm, tính lại tổng dung lượng" | Conf §5 · dòng 8 |
| REQ-TT607-64 | Popup xóa → Hủy bỏ: "Tắt popup" | Conf §5 · dòng 8 |
| REQ-TT607-65 | Tổng dung lượng "Cập nhật lại mỗi khi thêm/xóa file. Căn phải, nằm dưới file cuối cùng" | Conf §5 · dòng 9 |
| REQ-TT607-66 | Tổng dung lượng vượt quá 5MB → "Tổng dung lượng các tệp không được vượt quá 05 MB." | Conf §5.1 · dòng 1 |
| REQ-TT607-67 | Tệp sai định dạng → "Vui lòng chọn tệp có định dạng JPG, XLSX, PDF, XML." | Conf §5.1 · dòng 2 |
| REQ-TT607-68 | Quá 6 tệp → "Số lượng tệp đính kèm không được vượt quá 06 tệp." | Conf §5.1 · dòng 3 · Conf §5.2 · cách đếm: AMB-TT607-17 |
| REQ-TT607-69 | Danh sách "hiển thị theo thứ tự tải lên (không cho kéo-thả sắp xếp lại)" | Conf §5.2 |

### 4.6. Nút thao tác & điều hướng

| REQ ID | Yêu cầu | Nguồn |
|---|---|---|
| REQ-TT607-70 | Có 5 nút: Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi · Trở lại | Chat 06-10 · nhãn và tab hiển thị: AMB-TT607-39 |
| REQ-TT607-71 | Lưu tạm: "Cho phép lưu kể cả khi chưa validate hết các ô nhập thông tin" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-72 | Lưu tạm → "chuyển sang màn hình danh sách thủ tục trạng thái Lưu nháp" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-73 | Lưu tạm: "khi lưu không cập nhật thông tin thay đổi vào NTG" | Conf §3/§4 · Thao tác 1 |
| REQ-TT607-74 | Khi bấm Lưu tạm / Trình ký / Ký và gửi: "Tô đỏ các ô có lỗi và hiển thị lỗi khi hover vào ô input, lỗi hiển thị dạng tooltip" | Conf §3/§4 · Thao tác 1, 3, 4 |
| REQ-TT607-75 | Khi bấm Lưu tạm / Trình ký / Ký và gửi: "Tô đỏ các ô bắt buộc nhập nhưng đang bị bỏ trống" | Conf §3/§4 · Thao tác 1, 3, 4 |
| REQ-TT607-76 | Xem tờ khai ở tab TK1-TS → popup preview mẫu TK1-TS (QĐ 490/QĐ-BHXH ngày 28-03-2023) | Conf §3 · Thao tác 2 · Mockup `image2026-9-21_14-41-18.png` · Chat 06-10 |
| REQ-TT607-77 | Xem tờ khai ở tab D01-TS → popup preview mẫu D01-TS (QĐ 595/QĐ-BHXH ngày 14-04-2017) | Conf §4 · Thao tác 2 · Mockup `image2026-9-21_14-41-42.png` · Chat 06-10 |
| REQ-TT607-78 | Trình ký "thực hiện quy trình Trình ký như hệ thống hiện tại" | Conf §3/§4 · Thao tác 3 |
| REQ-TT607-79 | Còn lỗi thì Trình ký bị chặn, "hiển thị rõ thông báo lỗi" | Chat 06-10 · câu thông báo: AMB-TT607-31 |
| REQ-TT607-80 | Ký và gửi: "Khi còn lỗi không cho phép Ký và gửi BH" | Conf §3/§4 · Thao tác 4 |
| REQ-TT607-81 | Ký và gửi: "Khi ký và gửi BH thực hiện cập nhật thông tin NLĐ theo hồ sơ đã ký gửi" | Conf §3/§4 · Thao tác 4 |
| REQ-TT607-82 | Trở lại khi "người dùng đã nhập thông tin người tham gia" → popup "Thông báo", nội dung "Bạn có chắc muốn trở lại danh sách?" | Conf §3/§4 · Thao tác 5 · Mockup `image2026-9-21_14-45-9.png` · điều kiện: AMB-TT607-37 |
| REQ-TT607-83 | Popup Trở lại → bấm Hủy bỏ **hoặc** X → đóng popup, vẫn ở màn hình thủ tục 607 vừa tạo | Chat 06-10 |
| REQ-TT607-84 | Popup Trở lại → Đồng ý → không lưu thông tin, quay về màn hình **Tạo hồ sơ mới** | Chat 06-10 · Conf §3/§4 Thao tác 5 |
| REQ-TT607-85 | Bấm Back của trình duyệt → hiện thông báo như REQ-TT607-82 | Conf §3/§4 · Thao tác 5 · khả thi: AMB-TT607-42 |
| REQ-TT607-86 | Đóng cửa sổ → hiện thông báo | Conf §3/§4 · Thao tác 5 · khả thi: AMB-TT607-42 |

**Tổng: 86 REQ** (4.1: 8 · 4.2: 14 · 4.3: 20 · 4.4: 11 · 4.5: 16 · 4.6: 17).

> **Quy mô tài liệu:** có ≥ 25 REQ, nhưng chỉ có **1 ticket**. Cấu trúc tách theo quy tắc của workflow là "mỗi ticket 1 file con", nên với 1 ticket thì tách ra cũng chỉ được index + 1 file con trùng nội dung. Vì vậy tôi giữ **1 file**.

## 4b. Đối Chiếu Chéo Nguồn

| Hạng mục | Ticket | Comment Jira | Confluence (bản 14) | Mockup / preview | Chat 06-10 | Kết luận |
|---|---|---|---|---|---|---|
| Tên thủ tục | — | — | "Cấp lại sổ BHXH không thay đổi thông tin" | TK1: giống Conf · D01/Đính kèm/preview: "…do mất, hỏng" | "607 Cấp lại sổ BHXH do mất, hỏng" | ✅ Theo Chat → AMB-TT607-01 đóng |
| Cấp địa chỉ | — | — | Chỉ Tỉnh + Xã (thiếu 13.2/14.2) | TK1 có cột Quận/huyện · preview TK1-TS có ô Huyện | Cột Quận/huyện chỉ hiển thị, không có data | ✅ Theo Chat → AMB-TT607-02 đóng · chi tiết còn mở AMB-TT607-25 |
| Mẫu tờ khai | — | — | Không ghi số văn bản | TK1-TS QĐ 490/2023 · D01-TS QĐ 595/2017 | "đúng rồi" | ✅ AMB-TT607-03 đóng |
| Bộ nút | — | — | Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi BH · Trở lại | D01: Hủy bỏ · Xem tờ khai · Lưu và đóng · Trình ký · Ký và gửi | Lưu tạm · Xem tờ khai · Trình ký · Ký và gửi · Trở lại | ✅ Theo Chat · nhãn "Ký và gửi" hay "Ký và gửi BH" còn mở AMB-TT607-39 |
| Trở lại → Đồng ý | — | — | Vừa "quay về màn hình danh sách" vừa "chuyển về màn hình Tạo hồ sơ mới" | Popup: "Bạn có chắc muốn trở lại danh sách?" | Về màn hình tạo hồ sơ mới | ✅ Theo Chat · câu chữ popup lệch đích đến → AMB-TT607-37 |
| Giới hạn dung lượng | — | — | 5MB | Preview: "Dung lượng file còn lại: 6.0MB" | 5MB | ✅ 5MB · nút "+ Thêm đính kèm" trong preview còn mở AMB-TT607-30 |
| Trình ký khi còn lỗi | — | — | Chỉ ghi "Tô đỏ" | TK1: nút Trình ký đang disable | Có chặn, hiển thị rõ thông báo lỗi | ✅ AMB-TT607-07 đóng · câu thông báo còn mở AMB-TT607-31 |
| D01 bắt buộc? | — | — | Các ô đánh dấu \* | — | Tùy chọn | ✅ AMB-TT607-08 đóng · còn mở AMB-TT607-32 |
| Kỳ kê khai | — | — | Date Picker | 2 dropdown tháng / năm | — | ⚠️ Xung đột → AMB-TT607-14 |
| Cột "Trạng thái (3.2)" | — | — | Không có | TK1 có ("Đã kiểm tra") | — | ⚠️ AMB-TT607-12 |
| Đánh số cột | — | — | 13.x / 14.x | TK1: 12.x / 13.x · D01: hai cột cùng số 4.5, không có 4.3 | — | ⚠️ AMB-TT607-38 |
| Dòng hướng dẫn trong dropzone | — | — | "Chọn tệp hoặc kéo và thả tệp vào đây" | "Kéo thả tệp vào đây hoặc chọn tệp từ máy tính" | — | ⚠️ AMB-TT607-38 |
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
| BR-5 | Tích phụ lục mà NTG không có thành viên HGĐ → chặn ở bước Ký và gửi | 40 |
| BR-6 | Đính kèm: ≤ 6 tệp (gồm tờ khai) · tổng ≤ 5MB · chỉ pdf/xml/jpg/xlsx | 66, 67, 68 |
| BR-7 | Người dùng chỉ thao tác trong phạm vi đơn vị của mình | 08 |
| BR-8 | Hồ sơ đã lưu/ký, khi mở chỉnh sửa hoặc sao chép, hiển thị đúng dữ liệu tại thời điểm đã lưu/ký | 41, 42 |

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

#### ✅ Đã trả lời (Chat 06-10-2026)

| Mã | Câu hỏi | Trả lời | REQ liên quan |
|---|---|---|---|
| AMB-TT607-01 | Tên thủ tục 607 | "607 Cấp lại sổ BHXH do mất, hỏng" | 01 |
| AMB-TT607-02 | Địa chỉ 2 cấp hay 3 cấp | "Quận/Huyện đã bỏ nên chỉ hiển thị giao diện còn không có data" | 36 |
| AMB-TT607-03 | Mẫu tờ khai đích | QĐ 490/2023 (TK1-TS) và QĐ 595/2017 (D01-TS) — "đúng rồi" | 76, 77 |
| AMB-TT607-04 | Bộ nút của D01 | Lưu tạm, Xem tờ khai, Trình ký, Ký và gửi, Trở lại | 70 |
| AMB-TT607-05 | Đích của Trở lại → Đồng ý | Hủy bỏ / X → ở lại · Đồng ý → màn hình tạo hồ sơ mới | 83, 84 |
| AMB-TT607-06 | 5MB hay 6MB | 5MB (nhắc lại câu định dạng cho phép) | 56, 66 |
| AMB-TT607-07 | Trình ký có chặn khi còn lỗi | "có, hiển thị rõ thông báo lỗi" | 79 |
| AMB-TT607-08 | D01-TS bắt buộc hay tùy chọn | "Tùy chọn" | 43 |
| AMB-TT607-09 | Phân quyền | "User của đơn vị chỉ được sử dụng các tính năng của chính đơn vị này." *(trả lời một phần, còn AMB-TT607-33)* | 08 |
| AMB-TT607-10 | Phụ lục thành viên hộ gia đình | Xem tờ khai đúng thông tin · sửa/sao chép giữ đúng dữ liệu đã lưu · chặn khi Ký gửi nếu NTG không khai báo *(trả lời một phần, còn AMB-TT607-34, 35)* | 39–42 |
| AMB-TT607-11 | Có regression thủ tục 612 không | Không — chỉ phần liên quan 607 | — |

#### ❔ Còn treo

| Mã | Câu hỏi | Nguy cơ | Mức | Assumption tạm |
|---|---|---|---|---|
| AMB-TT607-12 | Cột "Trạng thái (3.2)" dưới Mã số BHXH (mockup TK1 hiện "Đã kiểm tra") có trong phạm vi không? Giá trị lấy từ đâu? | Bỏ sót hoặc báo bug sai | 🟡 | Không test cho đến khi có trả lời |
| AMB-TT607-13 | Mẫu TK1-TS có [06] CCCD, [10] Họ tên cha/mẹ/giám hộ, mục II [13]–[17] (mức tiền đóng, phương thức đóng, nơi KCB…). Lưới nhập không có các trường này → preview và file gửi BHXH điền gì vào các ô đó, lấy từ đâu? | Tờ khai gửi đi thiếu thông tin | 🔴 | Chỉ đối chiếu preview với các trường có trên lưới |
| AMB-TT607-14 | Kỳ kê khai là Date Picker (Conf) hay 2 dropdown tháng/năm (mockup)? Được chọn khoảng nào (tháng quá khứ, tương lai)? | Thiếu ca biên | 🟡 | Theo UI thực tế khi recon |
| AMB-TT607-15 | Ngày sinh validate thế nào theo từng "Định dạng"? (VD: chọn `yyyy` mà nhập đủ ngày/tháng; ngày sinh ở tương lai; ngày không tồn tại.) Thông báo lỗi là gì? | Không viết được TC negative | 🟡 | Chỉ test bỏ trống |
| AMB-TT607-16 | Nút "Nhập excel", nhóm "Chưa có phòng ban", dòng Mã NV, thanh icon dọc (chỉ có trên mockup Giấy tờ đính kèm) có trong phạm vi không? | Phạm vi test sai | 🟡 | Ngoài phạm vi |
| AMB-TT607-17 | "Tối đa 06 file (gồm tờ khai)": TK1-TS và D01-TS có được tính vào 6 tệp không? Khi không dùng D01 thì người dùng được tải mấy tệp (4 hay 5)? Tờ khai có tính vào giới hạn 5MB không? | Sai ca biên 4/5/6 tệp | 🔴 | Không chạy ca biên cho đến khi có trả lời |
| AMB-TT607-18 | Có nhận đuôi `.jpeg`, `.xls`, đuôi viết hoa (`.PDF`) không? Có giới hạn dung lượng từng tệp không? Tệp 0 byte, tệp trùng tên xử lý ra sao? Xem trước tệp xml/xlsx hiển thị thế nào? | Thiếu ca biên | 🟡 | Chỉ nhận đúng 4 đuôi viết thường |
| AMB-TT607-19 | Sau Trình ký và sau Ký và gửi, hồ sơ chuyển sang trạng thái gì? Ở mỗi trạng thái còn sửa / xóa / sao chép được không? | Không kiểm được trạng thái | 🔴 | — |
| AMB-TT607-20 | Mã số BHXH ở D01 (cho nhập lại) khác TK1 thì giá trị nào được dùng? Hai tab có đồng bộ với nhau không? "NLĐ" ở REQ-81 có phải chính là NTG không? | Dữ liệu gửi đi không nhất quán | 🔴 | — |
| AMB-TT607-21 | Mở lại hồ sơ Lưu nháp: dữ liệu đang lỗi và tệp đính kèm có được giữ nguyên không? | Thiếu TC sửa nháp | 🟡 | Giữ nguyên tất cả |
| AMB-TT607-22 | Hồ sơ 607 tạo trên giao diện cũ (đang nháp hoặc đã gửi) mở bằng giao diện nào? Dữ liệu cấp Huyện cũ xử lý ra sao? | Hồ sơ cũ bị lỗi khi mở | 🟡 | — |
| AMB-TT607-23 | Sửa NTG xong có quay lại màn hình thủ tục không? Dữ liệu đang nhập dở có bị mất không? Lưới có tự lấy dữ liệu NTG mới không? | Mất dữ liệu đang nhập | 🟡 | — |
| AMB-TT607-24 | Bỏ một NTG khỏi lưới bên phải bằng cách nào? Chuyển 1 NTG hai lần có bị trùng dòng không? Một hồ sơ được tối đa bao nhiêu NTG? | Thiếu ca negative | 🟡 | — |
| AMB-TT607-25 | Cột Quận/huyện "không có data": áp cho **cả hai** nhóm địa chỉ (Nơi ĐK khai sinh và Địa chỉ nhận kết quả) đúng không? Cột này bị khoá (không cho chọn) hay vẫn mở nhưng danh sách rỗng? Trên preview / file gửi đi, ô Huyện để trống? | Assert sai trạng thái cột | 🟡 | Hiển thị cột, ô trống, không thao tác được |
| AMB-TT607-26 | Validation của Số điện thoại, Mã số hộ gia đình, Mã số BHXH (đúng 10 chữ số?), độ dài Địa chỉ nơi nhận? Câu thông báo lỗi khi bỏ trống "Nội dung thay đổi yêu cầu"? | Không viết được TC biên | 🟡 | Dùng câu chung "\<Tên trường\> không được để trống" |
| AMB-TT607-27 | Hình thức nhận kết quả có bắt buộc không (Conf không có dấu \*)? Chọn "Nhận bản điện tử" thì Địa chỉ nhận kết quả còn bắt buộc không? | Chặn hoặc cho qua sai | 🟡 | Theo Conf: địa chỉ luôn bắt buộc |
| AMB-TT607-28 | D01: Ngày hiệu lực có phải ≥ Ngày ban hành không? Nhập ngày sai định dạng / ngày không tồn tại thì báo gì? "Cơ quan ban hành — Nhập tên doanh nghiệp": có điền sẵn tên đơn vị không? | Thiếu TC validation | 🟡 | — |
| AMB-TT607-29 | Tìm kiếm "gần đúng" có bỏ qua dấu tiếng Việt và hoa/thường không? Tìm được theo một phần của mã BHXH không? | Kỳ vọng mơ hồ | 🟢 | Chứa chuỗi, không phân biệt hoa/thường |
| AMB-TT607-30 | Popup Xem tờ khai có dòng "Dung lượng file còn lại" và nút "+ Thêm đính kèm" (mockup) không? Nếu có thì hoạt động thế nào? | Bug giả hoặc bỏ sót | 🟢 | Không test |
| AMB-TT607-31 | Khi Trình ký bị chặn vì còn lỗi, thông báo hiển thị dạng gì (popup / toast / chỉ tooltip trên ô) và câu chữ là gì? | Không assert được | 🟡 | Chỉ kiểm hồ sơ không được trình ký và ô lỗi bị tô đỏ |
| AMB-TT607-32 | D01 tùy chọn: khi người dùng **đã thêm** một dòng D01 thì các ô \* trở thành bắt buộc đúng không? Thêm / xóa dòng D01 bằng thao tác nào? Một NTG được nhiều dòng D01 không? | Chặn ký gửi sai | 🔴 | — |
| AMB-TT607-33 | Trong **cùng** một đơn vị có phân vai không (ai được Trình ký, ai được Ký và gửi)? User thuộc nhiều đơn vị thì chuyển đơn vị thế nào? "Chỉ dùng tính năng của đơn vị mình" có nghĩa là panel NTG và danh sách hồ sơ chỉ hiện dữ liệu của đơn vị đó? | Thiếu test phân quyền | 🔴 | Kiểm 2 user thuộc 2 đơn vị khác nhau không thấy dữ liệu của nhau |
| AMB-TT607-34 | Tích phụ lục mà NTG không có thành viên HGĐ: câu thông báo lỗi khi Ký và gửi là gì? Trình ký có bị chặn tương tự không? Lưu tạm có cho qua không? | Không assert được | 🔴 | Chỉ chặn ở Ký và gửi; Lưu tạm vẫn cho |
| AMB-TT607-35 | "Vẫn hiển thị đúng thông tin đã Lưu hoặc ký trước đó" có nghĩa là hồ sơ **giữ ảnh chụp dữ liệu** tại lúc lưu/ký — tức sau đó sửa hồ sơ NTG (VD đổi thành viên HGĐ) thì hồ sơ vẫn hiện dữ liệu cũ? Quy tắc này chỉ áp cho phụ lục HGĐ hay cho **mọi** trường của TK1-TS? | Kỳ vọng ngược nhau tuỳ cách hiểu | 🔴 | — |
| AMB-TT607-36 | Chức năng "sao chép" hồ sơ nằm ở đâu (màn hình danh sách thủ tục?), bản sao có trạng thái gì? Ngoài tạo / sửa / sao chép, "các phần liên quan tới thủ tục 607" còn gồm màn hình nào (danh sách, chi tiết, in, tra cứu kết quả)? | Phạm vi test thiếu | 🔴 | Chỉ test tạo, sửa, sao chép |
| AMB-TT607-37 | Thế nào là "đã nhập thông tin người tham gia" để hiện popup Trở lại (đã chuyển NTG sang lưới? chỉ đổi Kỳ kê khai?)? Khi **chưa** nhập gì thì bấm Trở lại về đâu — "màn hình danh sách" (Conf) hay "tạo hồ sơ mới"? Popup ghi "trở lại **danh sách**" nhưng đích đến là "tạo hồ sơ mới" — câu chữ có cần sửa không? | Assert sai điều hướng | 🔴 | — |
| AMB-TT607-38 | Số thứ tự cột và câu hướng dẫn trong dropzone đúng là bản nào? Conf ghi 13.x/14.x, mockup TK1 ghi 12.x/13.x; mockup D01 có hai cột cùng số 4.5, không có 4.3; dropzone Conf: "Chọn tệp hoặc kéo và thả tệp vào đây", mockup: "Kéo thả tệp vào đây hoặc chọn tệp từ máy tính" | Bug UI bị bỏ qua hoặc báo sai | 🟢 | Theo Conf |
| AMB-TT607-39 | Nhãn nút là "Ký và gửi" hay "Ký và gửi BH"? Bộ 5 nút có hiển thị ở tab Giấy tờ đính kèm không (mockup có, Conf không ghi)? | Assert nhãn sai | 🟢 | "Ký và gửi", hiện ở cả 3 tab |
| AMB-TT607-40 | NTG **đã có** Mã số BHXH thì ô Mã số BHXH ở TK1 bị khoá đúng không? | Thiếu ca negative | 🟡 | Khoá |
| AMB-TT607-41 | Dropdown Xã/phường phụ thuộc Tỉnh/TP: đổi Tỉnh thì Xã có bị xoá không? Danh mục Tỉnh/Xã lấy từ nguồn nào (danh mục sau sáp nhập 2025)? | Lỗi dữ liệu địa chỉ | 🟡 | Đổi Tỉnh thì Xã bị xoá |
| AMB-TT607-42 | **Đóng tab/cửa sổ:** trình duyệt **không cho phép** hiện popup tùy biến của ứng dụng, chỉ hiện được hộp thoại mặc định của trình duyệt (câu chữ do trình duyệt quyết định). Chấp nhận hộp thoại mặc định có được không? Nút Back của trình duyệt có hiện popup của ứng dụng (REQ-82) không? | Bug không sửa được / assert sai | 🔴 | REQ-86 chỉ kiểm **có** hộp thoại, không assert câu chữ |

### 7.2. Rủi Ro Kiểm Thử

| Mã | Rủi ro | Mô tả | Mitigation |
|---|---|---|---|
| RISK-TT607-01 | Tài liệu chưa ổn định | Ticket đã ở trạng thái Ready for UAT, nhưng Confluence vẫn được sửa (bản 14 lúc 06-10-2026 09:25). Mockup lệch đặc tả ở nhiều điểm | Ghi số phiên bản Confluence vào TC; khi trang đổi phiên bản thì chạy `/update-requirements-from-ticket` |
| RISK-TT607-02 | Ký số & gửi cổng BHXH | Hồ sơ gửi đi không thu hồi được. Lỗi ký số / cổng chưa có luồng xử lý được đặc tả | Chỉ dùng tài khoản test do người yêu cầu cấp. Khi ký/gửi lỗi: **ghi lại số hồ sơ** vào execution report để người yêu cầu kiểm tra (Chat 06-10) |
| RISK-TT607-03 | Dữ liệu NTG đa dạng | Cần đủ loại NTG: có / chưa có mã BHXH · **có / không** khai báo thành viên HGĐ · email sai · thiếu trường bắt buộc · đủ nhiều NTG để thử cuộn | Tạo bộ NTG riêng, tên truy vết được (`auto_607_<timestamp>`) |
| RISK-TT607-04 | Ghi ngược hồ sơ NLĐ | Ký và gửi làm thay đổi hồ sơ NLĐ, có thể ảnh hưởng dữ liệu của người khác nếu môi trường dùng chung | Chỉ dùng NTG do QA tạo; hỏi môi trường có dùng chung không (mục 10) |
| RISK-TT607-05 | Kiểm tra "dữ liệu không đổi sau khi lưu" (REQ-41/42) | Muốn chứng minh hồ sơ giữ dữ liệu cũ thì phải **sửa hồ sơ NTG sau khi lưu** rồi mở lại hồ sơ — nếu không sửa, phép thử không chứng minh được gì | Thiết kế TC theo 4 bước trạng thái sạch (skill 4.3.2) sau khi AMB-TT607-35 được trả lời |
| RISK-TT607-06 | Bộ tệp mẫu | Cần tệp đúng 5MB, 5MB + 1 byte, đuôi lạ, 0 byte, tên tiếng Việt, tên dài | Sinh sẵn bằng `/generate-test-data` |
| RISK-TT607-07 | Hộp thoại khi đóng tab / Back | Hộp thoại của trình duyệt khác nhau theo trình duyệt, khó tự động hoá | Đánh dấu manual; chỉ assert có hay không có hộp thoại (skill 4.3.6) |
| RISK-TT607-08 | Phân quyền theo đơn vị | Cần ≥ 2 tài khoản thuộc 2 đơn vị khác nhau | Xin thêm tài khoản đơn vị thứ hai (đã có chỗ khai trong `.env`) |
| RISK-TT607-09 | Hồ sơ 607 cũ | Hồ sơ tạo trên giao diện cũ có thể không mở được trên giao diện mới | Cần dữ liệu hồ sơ cũ trên môi trường UAT |

## 8. Ma Trận Trạng Thái

| Trạng thái hiện tại | Hành động | Trạng thái sau | Nguồn |
|---|---|---|---|
| (Mới) | Lưu tạm | **Lưu nháp** | REQ-TT607-72 |
| (Mới) / Lưu nháp | Trình ký | ❔ Không đề cập trong tài liệu | AMB-TT607-19 |
| (Mới) / Lưu nháp / ? | Ký và gửi | ❔ Không đề cập trong tài liệu | AMB-TT607-19 |
| Lưu nháp / đã trình ký / đã ký gửi | Chỉnh sửa / Sao chép | Hiển thị đúng dữ liệu đã lưu/ký | REQ-TT607-41, 42 · AMB-TT607-35, 36 |
| Ký gửi lỗi (ký số / cổng BHXH) | — | ❔ Không đề cập — ghi lại số hồ sơ | RISK-TT607-02 |

## 9. Tóm Tắt Acceptance Criteria (Checklist)

Nhóm có cờ 🔴 = còn AMB 🔴 treo, **chưa đủ** căn cứ sinh test case.

- [ ] **Khung màn hình & phân quyền** — REQ 01–08 · 🔴 AMB-33
- [ ] **Panel NTG** — REQ 09–22 · 🟡 AMB-23, 24, 29
- [ ] **TK1-TS: lấy dữ liệu từ NTG & quyền sửa** — REQ 23–27 · 🟡 AMB-40
- [ ] **TK1-TS: validation** — REQ 28–36 · 🟡 AMB-15, 25, 26, 27, 41
- [ ] **TK1-TS: phụ lục hộ gia đình** — REQ 37–40 · 🔴 AMB-34
- [ ] **Giữ đúng dữ liệu khi sửa / sao chép** — REQ 41–42 · 🔴 AMB-35, 36
- [ ] **D01-TS** — REQ 43–53 · 🔴 AMB-20, 32 · 🟡 AMB-28
- [ ] **Giấy tờ đính kèm** — REQ 54–69 · 🔴 AMB-17 · 🟡 AMB-18
- [ ] **Lưu tạm & tô lỗi** — REQ 70–75 · 🟢 AMB-39
- [ ] **Xem tờ khai** — REQ 76–77 · 🔴 AMB-13
- [ ] **Trình ký / Ký và gửi** — REQ 78–81 · 🔴 AMB-19 · 🟡 AMB-31
- [ ] **Trở lại & rời trang** — REQ 82–86 · 🔴 AMB-37, 42

## 10. Khuyến Nghị Cho Kiểm Thử

1. **Chốt 11 AMB 🔴** (13, 17, 19, 20, 32, 33, 34, 35, 36, 37, 42 — xem 7.1) trước khi sinh test case cho các nhóm có cờ 🔴. Các nhóm còn lại có thể làm trước.
2. **Recon UI thật trước khi viết TC.** Mockup lệch đặc tả nhiều chỗ, nên phải lấy câu chữ, nhãn nút và trạng thái cột từ màn hình thật (cần URL và tài khoản trong `.env`).
3. Ưu tiên kiểm **BR-1** (mức chặn của 3 nút khi còn lỗi) và **BR-2** (chỉ Ký và gửi mới ghi ngược vào NLĐ) — đây là hai rule có tác động dữ liệu lớn nhất.
4. Đối chiếu preview TK1-TS / D01-TS với **từng ô** của mẫu QĐ 490 / QĐ 595, đặc biệt ô Huyện (phải để trống) và các ô không có trên lưới nhập.
5. Kiểm REQ-41/42 bằng phép thử có thay đổi dữ liệu thật ở hồ sơ NTG sau khi lưu (RISK-TT607-05).
6. Ca biên đính kèm: 5MB đúng biên, 5MB + 1 byte, tệp thứ 6 và thứ 7 — chờ AMB-TT607-17 chốt cách đếm.
7. Phân quyền: 2 tài khoản thuộc 2 đơn vị, kiểm chéo không thấy NTG / hồ sơ của nhau.
8. Ký và gửi chỉ chạy trên môi trường đã được xác nhận là test. Mọi lần lỗi phải ghi số hồ sơ.
9. Tách các ca hộp thoại trình duyệt (Back / đóng tab) thành manual.
10. Ngoài phạm vi: thủ tục 612, nội dung bên trong quy trình Trình ký, form tạo NTG.

---

## Nhật ký phân tích

| Ngày | Nội dung |
|---|---|
| 06-10-2026 | Bản nháp đầu (mã tạm R-xx / Q-xx), lưu ở `docs/requirements/thu-tuc/` |
| 06-10-2026 | Nhận câu trả lời Chat 06-10 → đóng AMB-01…11. Cấp mã chính thức REQ-TT607-01→86 · AMB-TT607-01→42 · RISK-TT607-01→09. Chuyển file sang module `thu-tuc-607` |
