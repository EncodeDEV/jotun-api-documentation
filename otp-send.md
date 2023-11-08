# Gửi mã OTP thông qua SMS

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

Một số điện thoại chỉ có thể yêu cầu gửi OTP tối đa 1 ngày 3 lần, mỗi lần cách nhau 90 giây.

Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/resend-otp

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc nếu không cung cấp số điện thoại** Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `cc_phone` | `string` | **Bắt buộc nếu không cung cấp account_token** Mã quốc gia số điện thoại |
| `phone` | `string` | **Bắt buộc nếu không cung cấp account_token** Số điện thoại |

_account_token_ sẽ được ưu tiên kiểm tra và dùng trước nếu cung cấp cả 3 tham số

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Gửi mã OTP thành công",
    "data": {
        "otp": {
            "refresh_after": 90,
            "status": 'wait',
        }
    },
    "status": "OK",
    "status_code": 200,
    "captcha": []
}
```

- `data.otp.refresh_after` Thời gian chờ để có thể yêu cầu gửi lại lần tiếp
- `data.otp.status` Trạng thái có đang chờ gửi lại tiếp hay không 

Yêu cầu gửi quá nhanh:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Vui lòng yêu cầu gửi lại OTP sau 68 giây",
    "errors": {
        "limit": [
            "Đang trong thời gian chờ để có thể gửi lại mã OTP"
        ]
    },
    "data": {
        "otp": {
            "refresh_after": 68,
            "status": 'wait',
        }
    },
    "status": "INVALID_FIELD",
    "status_code": 422,
    "captcha": []
}
```

Vượt quá giới hạn trong ngày:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Bạn đã yêu cầu gửi OTP 3 lần hôm nay. Vui lòng yêu cầu gửi lại OTP vào ngày mai",
    "errors": {
        "limit": [
            "Vượt quá giới hạn gửi OTP trong một ngày"
        ]
    },
    "data": {
        "otp": {
            "refresh_after": 90,
            "status": 'limit',
        }
    },
    "status": "INVALID_FIELD",
    "status_code": 422,
    "captcha": []
}
```
