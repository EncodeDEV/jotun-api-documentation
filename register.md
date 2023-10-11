# Đăng ký tài khoản mới

Trước khi thực hiện bước đăng ký cần lấy thông tin đại lý bằng [API kiểm tra thông tin đại lý](agent-check.md)

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/auth/register

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | **Bắt buộc**. Tên hiển thị, tối đa 50 ký tự |
| `username` | `string` | **Bắt buộc**. Tên đăng nhập, chỉ chấp nhận chữ cái không dấu, chữ số, dấu gạch dưới, tối đa 30 ký tự |
| `cc_phone` | `string` | **Bắt buộc**. Mã điện thoại quốc gia hợp lệ |
| `phone` | `string` | **Bắt buộc**. Số điện thoại, tối đa 14 ký tự |
| `email` | `string` | Địa chỉ email hợp lệ, tối đa 50 ký tự |
| `password` | `string` | **Bắt buộc**. Mật khẩu đăng nhập, tối thiểu 8 ký tự, chứ ít nhất một: ký tự viết hoa, viết thường, chữ số, chữ cái và ký tự đặc biệt |
| `password_confirmation` | `string` | **Bắt buộc**. Mật khẩu đăng nhập nhập lại |
| `agent_id` | `string` | **Bắt buộc**. ID đại lý lấy được từ [API Kiểm tra thông tin đại lý](agent-check.md) |
| `account_code` | `string` | Mã xác thực tài khoản được cung cấp bởi quản lý hệ thống (xem mục Dư liệu mẫu phía dưới) |
| `account_token` | `string` | Token (nếu có) tài khoản đang đăng nhập, nếu token hợp lệ sẽ cần thoát tài khoản trước khi đăng ký mới |

### Kết quả trả về
Kết quả dữ liệu hợp lệ tài khoản sẽ được đăng nhập luôn:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Đăng ký tài khoản thành công",
    "data": {
        "token": "vs7zv3shXZfo....g61kamFRg41dfd398",
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

Dữ liệu không hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Có trường dữ liệu không hợp lệ. Vui lòng kiểm tra lại",
    "errors": {
        "username": [
            "Tên đăng nhập đã được sử dụng (11014)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```

## Dữ liệu mẫu
Mã đăng ký tài khoản
```
DMAC0001, DMAC0002, DMAC0003, DMAC0004
```
