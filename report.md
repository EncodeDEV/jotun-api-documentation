# Báo cáo mã QR sai thông tin

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/code/report

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | **Bắt buộc** ID của mã cần báo lỗi, được trả về từ [API lấy thông tin mã QR](qr.md) |
| `account_token` | `string` | Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `fullname` | `string` | Tên người báo lỗi, tối thiểu 3 ký tự, tối đa 50 ký tự |
| `phone` | `string` | **Bắt buộc nếu không có _account_token_ hoặc _account_token_ hết hạn**. Số điện thoại người báo lỗi, tối thiểu 9 ký tự, tối đa 20 ký tự |
| `shop_info` | `string` | Thông tin nơi bán hoặc nới kiểm tra mã, tối đa 150 ký tự |
| `description` | `string` | **Bắt buộc** Mô tả chi tiết lỗi, sai |
| `images` | `array` | Ảnh chụp sản phẩm, là một mảng tập tin upload, tối đa 3 ảnh, mỗi ảnh tối đa 2Mb định dạng jpg, jpeg, png |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Gửi báo lỗi thành công. Cảm ơn bạn, chúng tôi sẽ sớm kiểm tra lại thông tin",
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
    "message": "Vui lòng nhập số điện thoại",
    "errors": {
        "phone": [
            "Vui lòng nhập số điện thoại"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422,
    "captcha": {
        "required": false,
        "data": null
    }
}
