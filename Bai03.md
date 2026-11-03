

# Phần 1. Phân tích

Mở DevTools: `Cmd + Option + I`

Chọn Inspect → Elements → Computed.

Sơ đồ CSS Box Model (giả định):

    +-------------------------+
    | Margin: 0px             |
    |  +-------------------+  |
    |  | Border: 1px       |  |
    |  |  +-------------+  |  |
    |  |  | Padding: 0px|  |  |
    |  |  | Content     |  |  |
    |  |  +-------------+  |  |
    |  +-------------------+  |
    +-------------------------+

Nguyên nhân: Thiếu khoảng cách hoặc CSS
định vị sai khiến hai khung chồng lên nhau.

# Phần 2. Triển khai

Đề xuất sửa trong tab Styles:

```css
.driver-info {
    position: static;
    margin-bottom: 20px;
    padding: 15px;
    border: 1px solid #ccc;
    box-sizing: border-box;
}

.station-list {
    position: static;
    margin-top: 10px;
    padding: 15px;
}
```

Chỉ chỉnh CSS trong DevTools, không sửa file gốc.

# Phần 3. Kiểm thử

Nếu Margin không có tác dụng:

- Kiểm tra `position: absolute/fixed`.
- Kiểm tra `!important` ghi đè CSS.
- Kiểm tra `transform`, `float`, `display`.
- Xem Styles và Computed để tìm quy tắc
  CSS đang có hiệu lực.

Kết luận: Điều chỉnh Position, Margin,
Padding giúp tránh chồng lấn giao diện.

