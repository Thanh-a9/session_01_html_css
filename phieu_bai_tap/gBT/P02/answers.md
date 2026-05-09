# 📋 PHIẾU BÀI TẬP 02
# **HTML5 FORMS & MEDIA — Biểu mẫu, Validation & Đa phương tiện**

## PHẦN A — KIỂM TRA ĐỌC HIỂU (25 điểm)

### Câu A1 (5đ) — Input Types

1. type="text" → Ô nhập văn bản 1 dòng → Không có validation mặc định → Dùng để nhập tên khách hàng, tên sản phẩm tìm kiếm  
2. type="email" → Ô nhập văn bản → Tự kiểm tra có định dạng email (phải có @) → Dùng cho đăng ký tài khoản / nhận email khuyến mãi  
3. type="password" → Ô nhập nhưng bị ẩn ký tự (••••) → Không validation mặc định → Dùng khi đăng nhập tài khoản  
4. type="number" → Ô nhập số, có nút tăng/giảm → Chỉ cho nhập số → Dùng để nhập số lượng sản phẩm
5. type="tel" → Ô nhập số điện thoại → Không validate chặt (tùy trình duyệt) → Dùng nhập số điện thoại giao hàng  
6. type="url" → Ô nhập link → Kiểm tra có dạng URL (http:// hoặc https://) → Dùng khi seller nhập link sản phẩm  
7. type="date" → Hiển thị lịch chọn ngày → Chỉ chọn ngày hợp lệ → Dùng chọn ngày giao hàng
8. type="checkbox" → Ô tick vuông (có thể chọn nhiều) → Không validation → Dùng chọn nhiều sở thích / nhiều sản phẩm  
9. type="radio" → Nút tròn (chỉ chọn 1 trong nhóm) → Không validation → Dùng chọn phương thức thanh toán (COD / Bank)  
10. type="file" → Nút upload file → Có thể giới hạn loại file (accept) → Dùng upload ảnh sản phẩm  

### Câu A2 (5đ) — Validation Attributes
```html
<!-- Trường hợp 1 -->
<input type="text" required value="">  
Kết quả: Không submit được  
    Thuộc tính required yêu cầu người dùng phải nhập dữ liệu. Vì giá trị đang rỗng nên trình duyệt sẽ chặn submit và hiển thị thông báo yêu cầu nhập.  

<!-- Trường hợp 2 -->
<input type="email" value="abc">        
Kết quả: Không submit được  
    type="email" tự động kiểm tra định dạng email. Giá trị "abc" không chứa ký tự @ nên không hợp lệ, trình duyệt sẽ báo lỗi.  

<!-- Trường hợp 3 -->
<input type="number" min="1" max="10" value="15"> 
Kết quả: Không submit được  
    Giá trị 15 vượt quá giới hạn max="10". Trình duyệt sẽ không cho submit và báo rằng giá trị phải nhỏ hơn hoặc bằng 10.  

<!-- Trường hợp 4 -->
<input type="text" pattern="[0-9]{10}" value="abc123"> 
Kết quả: Không submit được  
    pattern="[0-9]{10}" yêu cầu phải nhập đúng 10 chữ số. Giá trị "abc123" vừa chứa chữ cái vừa không đủ 10 ký tự số nên không khớp pattern.  

<!-- Trường hợp 5 -->
<input type="password" minlength="8" value="123">  
Kết quả: Không submit được  
    minlength="8" yêu cầu ít nhất 8 ký tự. Giá trị "123" chỉ có 3 ký tự nên bị từ chối.  
```
### Câu A3 (5đ) — Accessibility

1. Tại sao `<label for="email">` quan trọng cho screen reader?
    Screen reader không “nhìn thấy” giao diện, nó chỉ đọc nội dung HTML. Screen reader sẽ đọc: “Email, edit text” (người dùng biết đây là ô nhập email).  
    Nếu không có **label** cchỉ co **input**: Screen reader chỉ đọc: “edit text” (không biết phải nhập gì)  
    `<label>` giúp người dùng hiểu mục đích của input
2. Khi nào dùng `<fieldset>` + `<legend>`?
    Ví dụ:
```html
<fieldset>
    <legend>Thông tin giao hàng</legend>

    <label for="name">Tên:</label>
    <input type="text" id="name">

    <label for="phone">SĐT:</label>
    <input type="tel" id="phone">

    <label for="address">Địa chỉ:</label>
    <input type="text" id="address">
</fieldset>
```
    1.Screen reader sẽ đọc theo ngữ cảnh:
        “Thông tin giao hàng”-> rồi mới đọc từng field bên trong
    2.Nếu không có fieldset:
        Các input rời rạc, không có ngữ cảnh chung  
    fieldset + legend giúp tạo ngữ cảnh và cấu trúc logic hon

3. `aria-label` dùng khi nào?
    Dùng khi không có text hiển thị rõ ràng trên UI nhưng vẫn cần mô tả cho screen reader
```html
<button aria-label="Tìm kiếm">
    🔍
</button>
```
    Nếu không có aria-label:  
    Screen reader chỉ đọc: “button” → không biết chức năng   
4. Tại sao KHÔNG nên dùng `aria-label` khi đã có `<label>`?  
  Bị thừa, trùng thông tin, Làm code rối

### Câu A4 (5đ) — Media
1. Giải thích thuộc tính `loading="lazy"` trên thẻ `<img>`  
    **Lazy loading** nghĩa là trình duyệt sẽ trì hoãn tải ảnh cho đến khi ảnh đó sắp xuất hiện trong viewport (vùng nhìn thấy được của người dùng), thay vì tải toàn bộ ảnh ngay khi trang load.  
    **Ví dụ**: đang đọc một cuốn sách dày 500 trang, chỉ cần đọc 1 trang đang mở thôi thay viff đọc hết 500 trang ngay lúc mở sách.  
    **Cải thiệ**: Trang web mở nhanh hơn, tiết kiệm data cho người dùng điện thoại
    **Khi nào KHÔNG dùng?**: 
    Ảnh logo, ảnh đầu trang(người dùng thấy NGAY khi mở): lazy ở đây làm logo hiện ra chậm, trông rất xấu.  
2. Tại sao nên cung cấp nhiều `<source>` trong thẻ `<video>`?  
    Vì không có format video nào được hỗ trợ 100% trên tất cả trình duyệt. Trình duyệt sẽ đọc lần lượt từng `<source>`, dùng cái đầu tiên nó hiểu được.
Liệt kê ít nhất **3 format** video web phổ biến: **.mp4**, **.webm**, **.ogg** 

3. Thuộc tính `alt` trên `<img>` dùng để làm gì?
**alt** (alternative text) phục vụ 3 mục đích chính:
1. Accessibility: screen reader đọc cho người khiếm thị
2. SEO: giúp search engine hiểu nội dung ảnh
3. Fallback: hiển thị khi ảnh bị lỗi không load được

Viết `alt` tốt cho 3 trường hợp:
   - Ảnh sản phẩm iPhone 16
```html
<!-- mô tả đủ để người không thấy ảnh vẫn hiểu -->
<img src="iphone.jpg" alt="iPhone 16 màu đen, mặt trước với màn hình 6.1 inch" />
```
   - Ảnh trang trí (decorative)
```html
<!-- alt="" (để trống) báo cho screen reader biết "bỏ qua ảnh này" -->
<img src="duong-ke-trang-tri.png" alt="" />
```
   - Ảnh biểu đồ doanh thu Q1/2026
```html
<!-- tóm tắt nội dung chính của biểu đồ -->
<img
  src="bieu-do.png"
  alt="Biểu đồ doanh thu T1/2026: tháng 1 3.1 tỷ, tăng cao"
/>
```
### Câu A5 (5đ) — So sánh `<figure>` vs `<img>`
```html
<!-- Cách 1: đơn thuần = ảnh không có chú thích -->
Dùng khi: Ảnh chỉ để hỗ trợ nội dung xung quanh, không cần giải thích thêm. Nếu xóa ảnh đi, người đọc vẫn hiểu nội dung.
Ví dụ 1: 
<div class="tac-gia">
    <img src="avatar.jpg" alt="Ảnh tác giả Minh Tuấn">
    <p>Bài viết bởi <strong>Minh Tuấn</strong></p>
</div>
Ví dụ 2: 
<nav>
    <a href="/home">
        <img src="icon-home.png" alt="Trang chủ">
        Trang chủ
    </a>
</nav>

<!-- Cách 2: khung ảnh hoàn chỉnh gồm ảnh + chú thích đi kèm -->
Dùng khi: Ảnh mang nội dung độc lập, cần chú thích để người xem hiểu đầy đủ hơn. Nếu tách ảnh này ra khỏi trang, nó vẫn có nghĩa hoàn chỉnh.
Ví dụ 1:
<figure>
    <img
        src="iphone-16.jpg"
        alt="iPhone 16 Pro Max 256GB màu Titan Đen, mặt trước"
    >
    <figcaption>
        iPhone 16 Pro Max 256GB — Titan Đen
        <span class="gia">25.990.000đ</span>
    </figcaption>
</figure>
Ví dụ 2:
<article>
    <h1>Lũ lụt nghiêm trọng tại miền Trung</h1>
    <p>Theo thống kê mới nhất, có hơn 500 hộ dân bị ảnh hưởng...</p>
    <figure>
        <img
            src="lu-lut.jpg"
            alt="Người dân di chuyển bằng thuyền trên đường phố ngập lũ tại miền Trung"
        >
        <figcaption>
            Người dân miền Trung phải dùng thuyền di chuyển trong đợt lũ ngày 20/9/2024.
            Ảnh: VN
        </figcaption>
    </figure>
    <p>Chính quyền địa phương đã triển khai...</p>
</article>
```

## PHẦN B — THỰC HÀNH CODE

## PHẦN C — PHÂN TÍCH & SUY LUẬN (20 điểm)

### Câu C2 (10đ) — Thiết kế chiến lược Validation
1. Viết `pattern` regex cho CMND/CCCD và Số tài khoản
```
pattern="[0-9]{12}"
[0-9]: chỉ chấp nhận ký tự là chữ số 0 đến 9
{12}: đúng 12 ký tự.
```
**Số tài khoản — từ 10 đến 15 chữ số:**
```
pattern="[0-9]{10,15}"
[0-9]: chỉ chấp nhận là chữ số
{10,15}: độ dài từ 10 đến 15 ký tự.
```
2. Giải thích: HTML5 validation đủ an toàn cho ứng dụng ngân hàng chưa?
Người dùng có thể tắt hoàn toàn validation của HTML5.  
Chỉ cần thêm `novalidate` vào thẻ `<form>` là toàn bộ bị vô hiệu hóa.  
Dữ liệu gửi lên server không đi qua trình duyệt.  
Mọi validation phía trình duyệt đều vô nghĩa.  
3. 3 thứ HTML5 KHÔNG THỂ validate
1. So sánh 2 ô với nhau
Ví dụ: kiểm tra ô "Xác nhận PIN" có giống ô "PIN" không.
HTML không thể tham chiếu giá trị của ô khác. Bắt buộc dùng JS.
2. Kiểm tra dữ liệu đã tồn tại trên server chưa
Ví dụ: email này đã có tài khoản chưa, số CCCD này đã đăng ký chưa.
HTML không thể gọi lên server để hỏi. Cần JS gửi request kiểm tra (thường dùng fetch/ajax).
3. Validation theo điều kiện động
Ví dụ: nếu chọn "Chuyển khoản" thì ô số tài khoản mới bắt buộc; nếu chọn "COD" thì không cần.
HTML không thể bật/tắt `required` dựa trên lựa chọn của người dùng. Phải dùng JS lắng nghe sự kiện và thay đổi thuộc tính.
4. Nêu 2 rủi ro bảo mật nếu chỉ validate trên Frontend mà không validate Backend
**Rủi ro 1: Kẻ tấn công gửi dữ liệu độc hại trực tiếp lên server**
Dùng Postman hoặc curl, họ bỏ qua hoàn toàn form HTML và gửi bất kỳ dữ liệu nào lên server: số âm, chuỗi rỗng, mã SQL injection, script độc hại... Server không chặn lại, dữ liệu xấu đi thẳng vào cơ sở dữ liệu.
 
**Rủi ro 2: SQL Injection / tấn công dữ liệu**
Nếu backend không lọc dữ liệu đầu vào, kẻ tấn công gửi chuỗi như:
```
' OR 1=1 --
```
vào ô số tài khoản. Server nhận chuỗi này, ghép thẳng vào câu lệnh SQL → có thể đọc toàn bộ dữ liệu khách hàng hoặc xóa cơ sở dữ liệu. Frontend validation không ngăn được.