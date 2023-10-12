# Đăng nhập tài khoản bằng số điện thoại

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/auth/login-phone

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `cc_phone` | `string` | **Bắt buộc**. Mã điện thoại quốc gia hợp lệ |
| `phone` | `string` | **Bắt buộc**. Số điện thoại, tối đa 14 ký tự |
| `password` | `string` | **Bắt buộc**. Mật khẩu đăng nhập, tối thiểu 8 ký tự, chứ ít nhất một: ký tự viết hoa, viết thường, chữ số, chữ cái và ký tự đặc biệt |
| `account_token` | `string` | Token (nếu có) tài khoản đang đăng nhập, nếu token hợp lệ sẽ cần thoát tài khoản trước khi đăng đăng nhập |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
Trường hợp 1:
```javascript
{
    "message": "Đăng nhập thành công",
    "data": {
        "token": "KXYu3q92xdiphRtkIeySHF1Zd6MPfCZhKlEBuGXl32060d1b",
        "phone": {
            "verified": false,
            "need_verify": true
        },
        "avatar": "[LINK_IMAGE]"
    },
    "status": "OK",
    "status_code": 200
}
```
- `data.token` mã xác thực tài khoản đại lý đang đăng nhập
- `data.avatar` link ảnh đại diện
- `data.phone.verified` trạng thái xác thực số điện thoại
- `data.phone.need_verify` có cần xác thực số điện thoại hay không

Trường hợp 2:
```javascript
{
    "message": "Tài khoản của bạn hiện chưa được xác thực bởi JOTUN. Vui lòng liên hệ HOTLINE để được hướng dẫn",
    "status": "REQUEST_DENIED",
    "status_code": 403
}
```

Dữ liệu không hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Số điện thoại hoặc mật khẩu không chính xác",
    "errors": {
        "phone": "Số điện thoại hoặc mật khẩu không chính xác"
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
