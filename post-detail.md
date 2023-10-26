# Lấy nội dung bài viết

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/post/view

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | *Bắt buộc* ID của bài viết, lấy được ở [API lấy danh sách bài viêt](posts.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy dữ liệu thành công",
    "data": {
        "title": "Giảm giá 50% dịp Halloween 2023",
        "content": "[HTML_CONTENT]",
        "updated_at": "18:17, 26/10/2023"
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.title` Tiêu đề bài viết
- `data.content` Nội dung bài viết, nội dung có định dạng HTML
- `data.updated_at` Thời gian cập nhật bài viết

Dữ liệu gửi lên không hợp lệ
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Nội dung không tồn tại",
    "errors": {
        "id": [
            "Nội dung không tồn tại"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
