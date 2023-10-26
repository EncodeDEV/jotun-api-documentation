# Lấy danh sách bài viết

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/post/list

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `page` | `integer` | Trang dữ liệu cần lấy |
| `per` | `integer` | Số bản ghi dữ liệu trên một trang, mặc định là 10 |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "current_page": 1,
        "per": 10,
        "total_items": 2,
        "items": [
            {
                "id": "eJMpdeaZO5",
                "title": "Giảm giá 50% dịp Halloween 2023",
                "featured_image": "[URL_IMAGE]",
                "action": "app_view"
            },
            {
                "id": "KLJarozPyR",
                "title": "Chương trình khuyến mãi dịp Back Friday 2023",
                "featured_image": "[URL_IMAGE]",
                "action": "app_view"
            }
        ]
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.current_page` Trang dữ liệu hiện tại
- `data.per` Số bản ghi dữ liệu của một trang
- `data.total_items` Số bản ghi thực tế của trang hiện tại
- `data.items` Dữ liệu của từng bản ghi
- `data.items.*.id` ID của bài viết, sử dụng để lấy chi tiết nội dung bài viết ở [API lấy nội dung bài viêt](post-detail.md)
- `data.items.*.title` Tiêu đề bài viết
- `data.items.*.featured_image` Ảnh bài viết
- `data.items.*.action` Hiển thị nội dung bằng giao diện ứng dụng hay bằng web view, giá trị là _app_view_ hoặc _web_view_

Không có dữ liệu
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "current_page": 1,
        "per": 10,
        "total_items": 0,
        "items": []
    },
    "status": "OK",
    "status_code": 200
}
```

Dữ liệu gửi lên không hợp lệ
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Không xác định thiết bị (11070)",
    "errors": {
        "device_id": [
            "Không xác định thiết bị (11070)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
