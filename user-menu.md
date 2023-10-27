# Lấy thông tin Menu tài khoản đăng nhập

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/auth/menu

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |

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
            "title": "Lịch sử kích hoạt mã",
            "action": "open_app_fn",
            "url": "list_actived_codes",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        },
        {
            "title": "Lịch sử quét",
            "action": "open_app_fn",
            "url": "list_scanned_histories",
            "text-color": "#ffffff",
            "bg-color": "#0e133a"
        },
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

Account Token không đúng:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Vui lòng đăng nhập để tiếp tục",
    "status": "UNAUTHORIZED",
    "status_code": 401
}
```
