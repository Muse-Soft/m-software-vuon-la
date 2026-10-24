# DESIGN.md — Landing page cửa hàng cây cảnh Vườn Lá

Nguồn: yêu cầu web MSR-26, Epic TEC-205, task Thiết kế TEC-206.
Phạm vi: CHỈ 1 landing page giới thiệu cửa hàng cây cảnh Vườn Lá. Không làm trang con, không làm backend.

## 1. Nguyên tắc bố cục (OPERATIONS.md §16.1 — visual-first)

- Ảnh lớn làm nội dung chính, chữ ít, nhiều khoảng trắng. Ngành cây cảnh có chuẩn thẩm mỹ mạnh nên ưu tiên bố cục ảnh lớn + khoảng trắng, không nhồi chữ.
- Một màn hình chỉ có MỘT điểm nhấn thị giác: hoặc một ảnh lớn, hoặc một tiêu đề lớn — không đặt hai điểm nhấn cạnh nhau.
- Thứ tự đọc từ trên xuống dưới đúng thứ tự các section ở §5. Không đảo thứ tự.

## 2. Bảng màu — mã hex kèm vai trò (bắt buộc, §16.2)

| Mã hex | Vai trò — dùng ở đâu, không dùng ở đâu |
|---|---|
| `#F4F7F0` | Nền chính toàn trang. Mọi section nền sáng đều dùng màu này. |
| `#FFFFFF` | Nền thẻ (card cây, card chăm sóc, card workshop), nền ô nhập form. Không dùng làm nền toàn trang. |
| `#DCE7D3` | Nền phụ — section xen kẽ (dùng cho section Hướng dẫn chăm sóc và section Bảng giá mẫu) để tách nhịp với nền chính. |
| `#22301F` | Chữ chính: tiêu đề, tên cây, giá, tiêu đề section. Không dùng cho chữ phụ. |
| `#4A5A44` | Chữ phụ: mô tả ngắn, ghi chú, chú thích ảnh, chữ trong footer. |
| `#5B8C5A` | Nhấn chính: nút bấm chính, liên kết, giá nổi bật, viền thẻ đang chọn, tiêu đề nhỏ (eyebrow) trên tiêu đề section. |
| `#3E6B42` | Nhấn đậm — chỉ dùng cho trạng thái hover/active của nút chính và cho tiêu đề hero trên ảnh sáng. Không dùng làm nền diện rộng. |
| `#A8C3A0` | Kẻ mảnh / đường phân cách giữa các khối, viền ô nhập ở trạng thái thường. Không dùng làm chữ. |

Quy tắc tương phản: chữ `#22301F` và `#4A5A44` chỉ đặt trên nền `#F4F7F0`, `#FFFFFF` hoặc `#DCE7D3`. Không đặt chữ xanh lá lên nền xanh lá.

## 3. Font chữ (cụ thể, có subset tiếng Việt)

- Tiêu đề: **Playfair Display** (serif), dùng cho: tên thương hiệu, tiêu đề hero, tiêu đề mọi section, tên cây trong card. Cỡ: hero 56px desktop / 36px mobile; tiêu đề section 36px desktop / 28px mobile; tên cây 20px. Trọng lượng 700 cho tiêu đề, 600 cho tên cây.
- Nội dung: **Be Vietnam Pro** (sans-serif), dùng cho: mô tả, giá, nhãn nút, nhãn form, chú thích, footer. Cỡ: nội dung chính 16px, chú thích 14px, nhãn nhỏ 13px in hoa giãn cách 0.12em. Trọng lượng 400 cho nội dung, 600 cho nút và nhãn.
- Tải qua Google Fonts với subset tiếng Việt (`subset=vietnamese` hoặc css2 có unicode-range tiếng Việt). Nếu font tải lỗi, fallback: tiêu đề → Georgia, serif; nội dung → system-ui, sans-serif. Không dùng thêm font thứ ba.

## 4. Phong cách tham chiếu — MỘT phong cách duy nhất

**Tropical Minimalism** (tối giản nhiệt đới): nền sáng gần trắng pha xanh nhạt, nhiều khoảng trắng, cây xanh làm điểm nhấn duy nhất, ánh sáng tự nhiên, không họa tiết rườm rà, không icon stock phẳng, không khung viền đậm.
- Cách nhận biết khi làm đúng: nhìn trang 3 giây phải thấy ngay cây xanh và khoảng trống, không thấy màu chói, không thấy khối chữ dày.
- Cấm: gradient sặc sỡ, nền tối diện rộng, ảnh minh họa hoạt hình, icon trang trí không mang thông tin.

## 5. Cấu trúc trang — thứ tự section bắt buộc

1. **Header (dính trên cùng):** logo chữ "Vườn Lá" (Playfair Display) + menu neo tới các section + nút "Đặt lịch". Chiều cao 64px, nền `#F4F7F0`, vị trí sticky.
2. **Hero — ảnh lớn toàn màn hình:** ảnh góc cửa hàng đầy cây xanh dưới ánh sáng tự nhiên, tỉ lệ 16:9, full-bleed (tràn hết chiều ngang). Tiêu đề: "Cây xanh cho tổ ấm của bạn". Mô tả 1 câu: từ chậu cây để bàn nhỏ xinh đến cây nội thất dáng lớn cho phòng khách và văn phòng. Nút chính "Xem bộ sưu tập" + nút phụ "Đặt lịch tư vấn".
3. **Bộ sưu tập cây theo không gian:** 3 nhóm, mỗi nhóm 1 hàng thẻ, mỗi thẻ gồm ảnh + tên cây + giá mẫu:
   - Cây để bàn (ảnh 4:5)
   - Cây ban công (ảnh 4:5)
   - Cây nội thất (ảnh 4:5)
   Mỗi thẻ ghi rõ "(ảnh mẫu)" dưới ảnh và giá ghi rõ "Giá mẫu".
4. **Hướng dẫn chăm sóc theo từng loại cây:** nền phụ `#DCE7D3`. 3–4 card, mỗi card: tên loại cây, ánh sáng cần thiết, tần suất tưới, 1 lưu ý ngắn. Ảnh minh họa 1:1 cho mỗi card. Nội dung chăm sóc là hướng dẫn chung, không ghi số liệu đo lường bịa đặt.
5. **Góc workshop trồng và thay chậu:** ảnh lớn 3:2 + lịch workshop dạng danh sách (ngày, chủ đề, số chỗ — tất cả ghi "Lịch mẫu" nếu chưa có lịch thật). Nút "Đăng ký workshop" cuộn xuống form.
6. **Bảng giá mẫu:** nền phụ `#DCE7D3`. Bảng 3 cột: loại cây/dịch vụ, mô tả ngắn, giá mẫu. Dòng chú thích bắt buộc ngay dưới bảng: "Giá trên trang chỉ là giá mẫu, chưa phải giá bán thật."
7. **Form đặt lịch tư vấn / đặt cây (CHỈ giao diện):** các trường: họ tên, số điện thoại, loại cây quan tâm, ngày muốn tư vấn, ghi chú (tùy chọn). Form CHỈ chạy phía trước (frontend-only): bấm gửi chỉ hiện thông báo "Bản demo — form chưa gửi dữ liệu thật." Không hứa hẹn cửa hàng sẽ liên hệ.
8. **Footer:** tên Vườn Lá, địa chỉ [CẦN BỔ SUNG], điện thoại [CẦN BỔ SUNG], giờ mở cửa [CẦN BỔ SUNG], dòng "Ảnh và giá trên trang là mẫu minh họa."

## 6. Quy tắc hình ảnh

- Tông ảnh bắt buộc: xanh lá tươi mát + ánh sáng tự nhiên, nền sáng, không ảnh tối, không ảnh lọc màu vàng đậm hay lạnh xanh dương.
- Ảnh mẫu chất lượng cao, đồng tông ngay từ bản đầu: dùng ảnh mẫu Unsplash chủ đề cây xanh trong nhà / cửa hàng cây, mỗi ảnh ghi chú "(ảnh mẫu)" trong caption hoặc alt text, khai báo là ảnh mẫu trong footer.
- Tỉ lệ khung (không đổi tùy ý):
  - Hero: 16:9 full-bleed.
  - Thẻ bộ sưu tập: 4:5.
  - Card chăm sóc: 1:1.
  - Workshop: 3:2.
  - Ảnh trong bảng giá: không dùng ảnh, chỉ chữ và số.
- Trên mobile mọi lưới ảnh về 1 cột, ảnh giữ đúng tỉ lệ, không cắt mất chủ thể chính (cây phải còn nguyên trong khung).

## 7. Bố cục và responsive

- Chiều rộng nội dung tối đa 1120px, căn giữa, lề hai bên tối thiểu 20px.
- Khoảng cách giữa các section: 80px desktop, 56px mobile. Khoảng trắng là một phần của thiết kế, không lấp đầy bằng chữ hay ảnh thêm.
- Breakpoint duy nhất: 768px. Dưới 768px: header thu gọn (logo + nút Đặt lịch), hero 36px, mọi lưới về 1 cột, bảng giá cuộn ngang trong khung (không vỡ layout).
- Nút chính: nền `#5B8C5A`, chữ trắng `#FFFFFF`, bo góc 8px, padding 12px 24px, hover chuyển `#3E6B42`. Nút phụ: viền 1px `#5B8C5A`, chữ `#3E6B42`, nền trong suốt.

## 8. Dữ liệu thật và tính trung thực — bắt buộc

- Địa chỉ, điện thoại, giờ mở cửa, lịch workshop thật, giá bán thật: chưa biết → ghi đúng `[CẦN BỔ SUNG]` hoặc "Giá mẫu" / "Lịch mẫu". TUYỆT ĐỐI không bịa số điện thoại, địa chỉ, giá thật.
- Ảnh: tất cả là ảnh mẫu cho tới khi khách cung cấp ảnh thật, phải ghi rõ "(ảnh mẫu)".
- Form: chỉ giao diện, có thông báo demo, không hứa hẹn liên hệ.
- Không dùng tên người thật, đánh giá khách hàng thật hay số liệu bán hàng nếu chưa được cung cấp — nếu cần khối nhận xét thì để trống chờ bổ sung, không tự viết lời khen giả.

## 9. Đối chiếu Acceptance Criteria TEC-206

- [x] Bảng màu hex kèm vai trò từng màu (§2: 8 màu, màu chốt #F4F7F0 / #22301F / #5B8C5A + màu phụ).
- [x] Font tiêu đề + nội dung cụ thể, subset tiếng Việt (§3: Playfair Display + Be Vietnam Pro).
- [x] MỘT phong cách tham chiếu có tên (§4: Tropical Minimalism).
- [x] Quy tắc hình ảnh: ảnh lớn làm nội dung chính, tỉ lệ khung từng khối (§6).
- [x] Bố cục ảnh lớn + khoảng trắng visual-first (§1, §7).
- [x] Đủ khối nội dung: hero, bộ sưu tập theo không gian, chăm sóc, workshop, bảng giá mẫu, form giao diện (§5).
- [x] Dữ liệu thật chưa biết → [CẦN BỔ SUNG], form frontend-only có thông báo demo (§8).
