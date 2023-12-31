# Khóa tài khoản

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/block

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `password` | `string` | **Bắt buộc**. Mật khẩu của tài khoản đang đăng nhập |
| `reason` | `string` | **Bắt buộc**. Lý do khóa tài khoản |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Khóa tài khoản thành công",
    "status": "OK",
    "status_code": 200
}
```

Sau khi khóa tài khoản thành công tài khoản sẽ được tự động đăng xuất. Quay lại màn hình quét.
