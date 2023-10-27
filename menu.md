# Lấy thông tin hiển thị menu

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/config/menu

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "data": [
        {
            "title": "Liên hệ hỗ trợ",
            "action": "web_view",
            "url": "[URL]",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        },
        {
            "title": "Giới thiệu & Hướng dẫn",
            "action": "web_view",
            "url": "[URL]",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        },
        {
            "title": "Điều khoản sử dụng",
            "action": "web_view",
            "url": "[URL]",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        },
        {
            "title": "Chính sách bảo mật",
            "action": "web_view",
            "url": "[URL]",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        }
    ],
    "status": "OK",
    "status_code": 200
}
```

- `title` text hiển thị từng mục
- `action` hành động khi mở. _web_view_ là mở url trong webview, _open_app_fn_ là mở một màn hình chức năng trong ứng dụng
- `url` Màn hình hoặc URL mở khi click
- `text-color` Màu chữ
- `bg-color` Màu nền

Account Token không đúng:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Thiếu dữ liệu cần thiết (11067)",
    "errors": {
        "platform": [
            "Thiếu dữ liệu cần thiết (11067)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
