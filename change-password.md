# Đổi mật khẩu

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/change-password

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `current_password` | `string` | **Bắt buộc** Mật khẩu hiện tại của tài khoản |
| `password` | `string` | **Bắt buộc** Mật khẩu đăng nhập, tối thiểu 8 ký tự, chứ ít nhất một: ký tự viết hoa, viết thường, chữ số, chữ cái và ký tự đặc biệt |
| `password_confirmation` | `string` | **Bắt buộc**. Mật khẩu đăng nhập nhập lại |

### Kết quả trả về
Kết quả dữ liệu hợp lệ tài khoản sẽ được đăng nhập luôn:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Cập nhật mật khẩu thành công",
    "status": "OK",
    "status_code": 200,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

Dữ liệu không hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Có trường dữ liệu không hợp lệ, vui lòng kiểm tra lại",
    "errors": {
        "current_password": [
            "Mật khẩu hiện tại không chính xác"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422,
    "captcha": {
        "required": false,
        "data": null
    }
}
