# Kiểm tra trạng thái đăng nhập

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/auth/check

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Tài khoản đang đăng nhập",
    "data": {
        "avatar": "[LINK_IMAGE]",
        "phone": {
            "verified": false,
            "need_verify": false
        }
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.avatar` link ảnh đại diện
- `data.phone.verified` trạng thái xác thực số điện thoại
- `data.phone.need_verify` có cần xác thực số điện thoại hay không

Token không đúng:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Không đăng nhập tài khoản",
    "status": "UNAUTHORIZED",
    "status_code": 401
}
```
