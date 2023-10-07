# Cập nhật trạng thái xác thực số điện thoại

Sau khi xác thực số điện thoại bằng Firebase trên ứng dụng thành công có thể gọi API này để cập nhật trạng thái xác thực.

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/auth/verify-phone

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) hoặc đăng ký mới [Xem tại đây](register.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Xác thực số điện thoại thành công",
    "status": "OK",
    "status_code": 200
}
```

Đã xác thực từ trước:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Tài khoản đã xác thực số điện thoại",
    "errors": {
        "account": [
            "Số điên thoại của tài khoản này đã được xác thực trước đó"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```

# Hình ảnh màn hình hiển thị
<img src="images/jotun_register_otp_1242x2688.png" width="360"/>
