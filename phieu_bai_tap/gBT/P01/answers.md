# 📋 PHIẾU BÀI TẬP 01
# **HTML5 FUNDAMENTALS — Cấu trúc, Semantic, Tables & Links**

## PHẦN A — KIỂM TRA ĐỌC HIỂU
### Câu A1 (5đ) — HTTP & Browser
Đọc chương 01 (01_introduction_html_universe.md), trả lời:

1. DNS Lookup – Tìm địa chỉ của Shopee
    Trình duyệt gửi yêu cầu đến hệ thống DNS để hỏi:
    “Shopee nằm ở đâu?”
    DNS trả về một địa chỉ IP của server Shopee.
2. TCP Handshake – Thiết lập kết nối
    Sau khi biết địa chỉ IP, trình duyệt bắt đầu kết nối với server.
    Nếu bước này không thành công, trang web sẽ không thể tải.
3. TLS Handshake – Thiết lập bảo mật (HTTPS)
    Vì Shopee dùng HTTPS, nên trước khi gửi dữ liệu thật, trình duyệt và server cần tạo một kết nối an toàn.
    Hai bên trao đổi khóa mã hóa để đảm bảo an toan
4. Gửi HTTP Request – Yêu cầu trang
    Khi kết nối đã sẵn sàng, trình duyệt gửi yêu cầu:
    “Cho tôi trang chủ Shopee”
    Đây là một HTTP request, thường là dạng GET.
5. Server xử lý và trả về Response
    Server của Shopee nhận yêu cầu và xử lý:
    Xác định bạn truy cập trang chủ
    Chuẩn bị nội dung
6. Trình duyệt phân tích HTML
    Trình duyệt nhận HTML và bắt đầu đọc từng dòng.
    Trong quá trình đọc, nó phát hiện:
    file CSS
    file JavaScript
    hình ảnh
7. Gửi thêm request để tải tài nguyên
    Trình duyệt tiếp tục gửi nhiều request khác để tải:
    CSS (giao diện)
    JS (logic, tương tác)
    hình ảnh sản phẩm
    Trong ảnh DevTools có thể thấy rất nhiều thẻ script và tài nguyên được tải ở dây.
8. Render – Hiển thị trang
    Sau khi có đủ dữ liệu:
    HTML tạo cấu trúc
    CSS tạo giao diện
    JS thêm tương tác
    Trình duyệt bắt đầu vẽ trang lên màn hình.


### Câu A2 (5đ) — Semantic HTML

1. Dùng `<div class="header">` thay vì `<header>`
    Google đọc HTML như đọc sách — nó cần "mục lục" rõ ràng. Khi thấy **`<div class="header">`**, Google chỉ thấy một cái hộp vô danh. Khi thấy **`<header>`**, biết ngay đây là phần đầu trang(chứa logo, menu chính).

2. Dùng `<div class="menu">` thay vì `<nav>`
    Thẻ **`<nav>`** là tín hiệu quan trọng với Google: "Đây là khu vực 'điều hướng'" Nếu dùng **`<div>`**, Google không biết đây là menu hay chỉ là một đoạn text bình thường.

3. Dùng `<div class="title">` thay vì thẻ heading (`<h1>`, `<h2>`...)
    Tên sản phẩm **iPhone 16** là tiêu đề quan trọng nhất trong thẻ `<article>`. Google dùng thẻ `<h1>`–`<h6>` để hiểu cấu trúc nội dung và xếp hạng từ khóa. Bọc trong `<div>` thì Google coi nó như text bình thường.

4. Ảnh thiếu thuộc tính **`alt`**
    Google đọc **`alt`** để biết ảnh chứa nội dung gì → ảnh có thể xuất hiện trong Google Image Search. Đồng thời, khi ảnh bị lỗi không load được, **`alt`** hiển thị thay thế để user vẫn hiểu.

# Sửa lại:
```html
<header>
    <span class="logo">ShopTLU</span>
    <nav>
        <a href="/">Trang chủ</a>
        <a href="/products">Sản phẩm</a>
    </nav>
</header>

<main>
    <article class="product">
        <h1>iPhone 16 Pro</h1>
        <p class="price">25.990.000đ</p>
        <figure>
            <img src="iphone.jpg" alt="iPhone 16 Pro - màu titan tự nhiên">
        </figure>
    </article>
</main>

<footer>© 2026 ShopTLU</footer>
```

### Câu A3 (5đ) — Block vs Inline
```html
┌─────────────────────────────────────────────┐  ← Trình duyệt
│                                             │
│ ┌─────────────────────────────────────────┐ │
│ │ Hộp 1                                   │ │  ← **<div>** BLOCK
│ └─────────────────────────────────────────┘ │
│                                             │
│ [Text A] [Text B]                           │  ← **<span>** INLINE
│                                             │
│ ┌─────────────────────────────────────────┐ │
│ │ Hộp 2                                   │ │  ← **<div>** BLOCK
│ └─────────────────────────────────────────┘ │
│                                             │
│ [Text C] [Text D]                           │  ← **<span>+<strong>** INLINE
│                                             │
│ ┌─────────────────────────────────────────┐ │
│ │ Hộp 3                                   │ │  ← **<div>** BLOCK
│ └─────────────────────────────────────────┘ │
│                                             │
└─────────────────────────────────────────────┘
```
**`<div>`** là Block → chiếm trọn 1 dòng, xuống dòng tự động  
Dù không **`<br>`**, trình duyệt vẫn tự đẩy **Hộp 1, Hộp 2, Hộp 3** xuống từng dòng riêng. Vì **`<div>`** là block element — nó "giành cả con đường", không ai chen vào được.  
**`<span>`** và **`<strong>`** là **Inline** → nằm cạnh nhau trên 1 dòng  
**Text A** và **Text B** tuy là 2 thẻ riêng biệt, nhưng vì đều là **inline** nên chúng không xuống dòng. Tương tự với **Text C** và **Text D**.

### Câu A4 (5đ) — Table

1. Ví dụ bảng HTML giống như một tờ báo cáo Excel. Tờ báo cáo đó có 3 phần rõ ràng: phần tiêu đề cột ở trên cùng, phần dữ liệu ở giữa, và phần tổng kết ở dưới cùng. Ba thẻ này chính là ba phần đó.  
**`<thead>`** — Phần đầu bảng (tiêu đề cột)  
    Chứa hàng tiêu đề mô tả ý nghĩa của từng cột. Trình duyệt tự động in đậm và căn giữa chữ bên trong. Khi in bảng dài nhiều trang, **`<thead>`** sẽ được lặp lại ở đầu mỗi trang tự động(**`<tbody>`** thì không).  
**`<tbody>`** — Phần thân bảng (dữ liệu chính)  
    Chứa toàn bộ hàng dữ liệu thực tế. Đây là nơi chiếm nhiều dòng nhất. Nếu có 100 sản phẩm thì cả 100 hàng **<tr>** đều nằm trong **`<tbody>`**. JavaScript thường chỉ thao tác vào **`<tbody>`** khi thêm/xóa dữ liệu động.  
**`<tfoot>`** — Phần cuối bảng (tổng kết)  
    Chứa hàng tổng hợp, tổng cộng, hoặc ghi chú cuối bảng. Dù viết **`<tfoot>`** trước **`<tbody>`** trong code, trình duyệt vẫn hiển thị nó ở dưới cùng.
2. Tại sao KHÔNG NÊN dùng table để tạo layout trang web?  
    1. **Sai về ngữ nghĩa:** **`<table>`** là "dữ liệu dạng bảng". Khi dùng nó để tạo layout (đặt sidebar, chia cột header/content). Google đọc HTML và nghĩ "trang này chứa bảng dữ liệu" — trong khi thực ra đó chỉ là khung bố cục.  
    2. **Không responsive, vỡ giao diện** trên mobile: **`<table>`** có kích thước cố định theo nội dung bên trong. Khi màn hình thu nhỏ (điện thoại), bảng không tự co lại mà tràn ra ngoài màn hình hoặc bị ép lại xấu xí.  
    3. **Code phức tạp, khó bảo trì**: Layout bằng **`<table>`** đòi hỏi lồng nhiều **`<tr>`**, **`<td>`**, **`colspan`**, **`rowspan`** chỉ để chia cột — không liên quan gì đến dữ liệu.   

## PHẦN B — THỰC HÀNH CODE (60 điểm)

### Bài B4 (15đ) — Phân tích trang web thật

1. 3 thẻ html
    `<header>`
     Vị trí: `<header class="shopee-top shopee-top--sticky">`
    `<section>` : `<section class="G9LJcQ" tabindex="-1"></section>`
    `<form>` : `<form role="search" autocomplete="off" class="shopee-searchbar">`
    2 thẻ không đúng:
    Dùng `<div>` thay cho `<nav>`: `<div class="navbar-wrapper container-wrapper"></div>`
    Dùng `<div>` thay cho `<button>`: `<div role="button" class="stardust-popover__target">`

2. KHÔNG thấy thẻ `<table>`, Không xác định được table.
3. form:
    `<form role="search" autocomplete="off" class="shopee-searchbar">`
    Action: Không thấy
    Method: Không khai báo
    input type: Không ghi rõ type
```html
<input 
  class="shopee-searchbar-input__input"
  maxlength="128"
  placeholder="Shopee bao ship 0Đ - Đăng ký ngay!"
  autocomplete="off"
  aria-autocomplete="list"
  role="combobox"
>
```
