# Debug HTML 
**Danh sách lỗi**

Lỗi 1: Dòng 1 — `<!DOCTYPE>` thiếu từ khóa `html` — Sửa thành `<!DOCTYPE html>`

Lỗi 2: Dòng 2 — `<html>` thiếu thuộc tính `lang` — Sửa thành `<html lang="vi">`

Lỗi 3: Dòng 4 — `<title>Trang web` không có thẻ đóng `</title>` — Thêm `</title>` vào cuối

Lỗi 4: Dòng 5 — `<meta charset="utf8">` sai giá trị, phải là `"UTF-8"` — Sửa thành `<meta charset="UTF-8">`

Lỗi 5: Dòng 5 — `<meta>` đặt sau `<title>`, nhưng quy chuẩn yêu cầu `<meta charset>` phải đứng đầu tiên trong `<head>` — Đưa `<meta charset>` lên trước `<title>`

Lỗi 6: Dòng 8 — `<h1>Welcome to ShopTLU<h1>` thẻ đóng thiếu dấu `/` — Sửa thành `</h1>`

Lỗi 7: Dòng 8 — `<h1>` đặt ngoài `<header>`, vi phạm cấu trúc semantic — Chuyển `<h1>` vào bên trong `<header>`

Lỗi 8: Dòng 11 — `<a href="home">Trang chủ<a>` thẻ đóng thiếu dấu `/` — Sửa thành `</a>`

Lỗi 9: Dòng 11 — `href="home"` và `href="products"` không phải đường dẫn hợp lệ — Sửa thành `href="index.html"` và `href="products.html"`

Lỗi 10: Dòng 18 — `<h3>` xuất hiện ngay sau `<h1>`, nhảy cấp heading — Theo quy tắc accessibility, phải dùng `<h2>` thay vì `<h3>`

Lỗi 11: Dòng 19 — `<img src=iphone.jpg>` giá trị `src` không có dấu nháy kép, thiếu thuộc tính `alt` — Sửa thành `<img src="iphone.jpg" alt="iPhone 16 Pro">`

Lỗi 12: Dòng 21 — `<p>Giá: <b>25.990.000đ</p></b>` lồng thẻ sai thứ tự, `</b>` phải đóng trước `</p>` — Sửa thành `<p>Giá: <b>25.990.000đ</b></p>`

Lỗi 13: Dòng 21 — Dùng `<b>` thay vì `<strong>` — `<b>` chỉ in đậm thuần túy, `<strong>` mới có ý nghĩa semantic "quan trọng" — Sửa thành `<strong>`

Lỗi 14: Dòng 26-27 — `<table>` dùng `<td>` cho hàng tiêu đề thay vì `<th>`, không có `<thead>`/`<tbody>` — Thêm `<thead>`, `<tbody>` và đổi `<td>` tiêu đề thành `<th>`

Lỗi 15: Dòng 37 — Có 2 thẻ `<main>` trong 1 trang, HTML5 chỉ cho phép duy nhất 1 `<main>` — Đổi `<main>` thứ 2 thành `<aside>` và đưa vào bên trong `<main>` thứ nhất

Lỗi 16: Dòng 43 — `<p>Copyright 2026` thiếu thẻ đóng `</p>` — Thêm `</p>` vào cuối