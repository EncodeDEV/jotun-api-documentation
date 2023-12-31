# Xác nhận mật khẩu

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/auth/confirm-password

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `password` | `string` | **Bắt buộc**. Mật khẩu của tài khoản đang đăng nhập |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mật khẩu chính xác",
    "status": "OK",
    "status_code": 200,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

Sau khi nhận được kết quả xác thực mật khẩu chính xác gọi [API Khóa tài khoản](user-block.md)
