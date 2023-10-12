# Đăng xuất tài khoản đại lý

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/logout

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ, sau khi đăng xuất thành công quay lại màn hình quét mã:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Đăng xuất thành công",
    "status": "OK",
    "status_code": 200
}
```

Token không đúng:
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
