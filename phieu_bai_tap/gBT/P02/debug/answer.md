# Danh sách 8 lỗi
Lỗi 1: Dòng 1 — `<form>` không có `action` và `method`, vi phạm best practices
Sửa: `<form action="#" method="POST">`

Lỗi 2: Dòng 2 — Input "Tên" không có `<label for="...">`, `id`, `name`, vi phạm accessibility
Sửa: `<label for="ten">Tên:</label> <input type="text" id="ten" name="ten" placeholder="Nguyễn Văn An" required>`

Lỗi 3: Dòng 4 — Input email không có `<label>`, `id`, `name`, `required`
Sửa: `<label for="email">Email:</label> <input type="email" id="email" name="email" placeholder="Email của bạn" required>`

Lỗi 4: Dòng 6–7 — Hai input password không có `<label>`, `id`, `name`, `required`
Sửa:
```
<label for="mat-khau">Mật khẩu:</label>
<input type="password" id="mat-khau" name="mat_khau" placeholder="Mật khẩu" required>

<label for="xac-nhan">Xác nhận mật khẩu:</label>
<input type="password" id="xac-nhan" name="xac_nhan_mat_khau" placeholder="Nhập lại mật khẩu" required>
```

Lỗi 5: Dòng 9 — Input phone dùng `type="text"` thay vì `type="tel"`, không có `label`, `id`, `name`, dùng `value` thay vì `placeholder`
Sửa: `<label for="dien-thoai">Phone:</label> <input type="tel" id="dien-thoai" name="dien_thoai" placeholder="0901234567" pattern="[0-9]{10}">`

Lỗi 6: Dòng 11–14 — `<select>` không có `<label>`, `id`, `name`, các `<option>` không có `value`
Sửa:
```
<label for="thanh-pho">Thành phố:</label>
<select id="thanh-pho" name="thanh_pho">
    <option value="hn">Hà Nội</option>
    <option value="hcm">TP.HCM</option>
</select>
```

Lỗi 7: Dòng 16–18 — `<label>` checkbox không liên kết với input nào (`for` + `id` bị thiếu), thiếu `<input type="checkbox">` và `required`
Sửa:
```
<input type="checkbox" id="dong-y" name="dong_y" required>
<label for="dong-y">Tôi đồng ý điều khoản</label>
```

Lỗi 8: Dòng 20 — Dùng `<input type="submit">` thay vì `<button type="submit">`, vi phạm best practices (button linh hoạt hơn, dễ style hơn)
Sửa: `<button type="submit">Gửi</button>`