# Khôi phục mật khẩu

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

## Bước 1: Kiểm tra số điện thoại

Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/auth/check-phone

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `cc_phone` | `string` | **Bắt buộc**. Mã điện thoại quốc gia hợp lệ |
| `phone` | `string` | **Bắt buộc**. Số điện thoại, tối đa 14 ký tự |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ, số điện thoại đã tồn tại:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Số điện thoại hợp lệ",
    "data": {
        "user_id": "1aLxX2AON5"
    },
    "status": "OK",
    "status_code": 200,
    "captcha": {
        "required": false,
        "data": null
    }
}
```
- `data.user_id` ID tài khoản có số điện thoại kiểm tra, dùng để gửi ở bước nhập mật khẩu mới

Kết quả số điện thoại chưa tồn tại
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Số điện thoại chưa tồn tại trên hệ thống",
    "status": "NOT_FOUND",
    "status_code": 404,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

## Bước 2: Xác thực OTP
Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/verify-otp

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```
Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `user_id` | `string` | **Bắt buộc**. ID tài khoản lấy được ở Bước 1 |
| `otp` | `string` | **Bắt buộc**. Mã OTP được nhập bởi người dùng |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mã xác thực chính xác",
    "data": {
        "user_id": "1aLxX2AON5",
        "otp": {
            "refresh_after": 90
        }
    },
    "status": "OK",
    "status_code": 200,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

Kết quả với dữ liệu không hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mã OTP không chính xác",
    "data": {
        "user_id": "359pJrp0DW",
        "otp": {
            "refresh_after": 90
        }
    },
    "errors": {
        "otp": [
            "Mã OTP không chính xác"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```

## Bước 3: Nhập mật khẩu mới

Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/reset-password

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `user_id` | `string` | **Bắt buộc**. ID tài khoản lấy được ở Bước 1 |
| `password` | `string` | **Bắt buộc**. Mật khẩu đăng nhập, tối thiểu 8 ký tự, chứ ít nhất một: ký tự viết hoa, viết thường, chữ số, chữ cái và ký tự đặc biệt |
| `password_confirmation` | `string` | **Bắt buộc**. Mật khẩu đăng nhập nhập lại |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Khôi phục mật khẩu thành công",
    "status": "OK",
    "status_code": 200,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

Kết quả lỗi dữ liệu hoặc lỗi cập nhật
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mật khẩu cần ít nhất 8 ký tự (11017)",
    "errors": {
        "password": [
            "Mật khẩu cần ít nhất 8 ký tự (11017)",
            "Mật khẩu không khớp (11018)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422,
    "captcha": {
        "required": false,
        "data": null
    }
}
```

Sau khi khôi phục mật khẩu thành công mở màn hình Đăng nhập tài khoản.
