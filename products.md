# Lấy danh sách sản phẩm

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/product/list

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `page` | `integer` | Trang dữ liệu cần lấy, không sử dụng phân trang không cần gửi |
| `per` | `integer` | Số bản ghi dữ liệu trên một trang, mặc định là 10, không sử dụng phân trang không cần gửi |

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
                "id": "YDPMAxQdN2",
                "name": "Sản phẩm mẫu 00002",
                "featured_image": "[URL_IMAGE]",
                "category": "Sơn nội thất",
                "units": "5L, 10L",
                "action": "app_view",
                "url": ""
            },
            {
                "id": "6z3kpg8Z2E",
                "name": "Sản phẩm mẫu 00001",
                "featured_image": "[URL_IMAGE]",
                "category": "Sơn ngoại thất",
                "units": "5L, 10L",
                "action": "app_view",
                "url": ""
            }
        ]
    },
    "status": "OK",
    "status_code": 200
}": 200
}
```

- `data.current_page` Trang dữ liệu hiện tại
- `data.per` Số bản ghi dữ liệu của một trang
- `data.total_items` Số bản ghi thực tế của trang hiện tại
- `data.items` Dữ liệu của từng bản ghi
- `data.items.*.id` ID của sản phẩm, sử dụng để lấy chi tiết nội dung sản phẩm ở [API lấy nội dung sản phẩm](product-detail.md)
- `data.items.*.name` Tên sản phẩm
- `data.items.*.featured_image` Ảnh sản phẩm
- `data.items.*.category` Danh mục sản phẩm
- `data.items.*.units` Giá trị đóng gói sản phẩm
- `data.items.*.action` Hiển thị nội dung bằng giao diện ứng dụng hay bằng web view, giá trị là _app_view_ hoặc _web_view_
- `data.items.*.url` Địa chỉ để mở trong web view khi action có giá trị là _web_view_

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
