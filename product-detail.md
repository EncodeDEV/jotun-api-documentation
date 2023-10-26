# Lấy thông tin chi tiết sản phẩm

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/product/view

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | *Bắt buộc* ID của sản phẩm, lấy được ở [API lấy danh sách sản phẩm](products.md) |

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
        "name": "Sản phẩm mẫu 00002",
        "images": [
            "[URL_IMAGE]",
            "[URL_IMAGE]",
            ...
            "[URL_IMAGE]",
        ],
        "units": "5L, 10L",
        "category": "Sơn nội thất",
        "attributes": [
            "Lorem ipsum dolor sit amet",
            "Lorem ipsum dolor sit amet",
            ....
        ],
        "description": "[HTML_CONTENT]",
        "updated_at": "18:33, 26/10/2023"
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.name` Tên sản phẩm
- `data.images` Hình ảnh sản pẩm
- `data.category` Danh mục sản phẩm
- `data.units` Giá trị đóng gói sản phẩm
- `data.attributes` Đặc tính nổi bật
- `data.description` Mô tả chi tiết
- `data.updated_at` Thời gian cập nhật bài viết

Dữ liệu gửi lên không hợp lệ
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Thông tin sản phẩm không tồn tại",
    "errors": {
        "id": [
            "Thông tin sản phẩm không tồn tại"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
