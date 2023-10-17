# Cập nhật ảnh đại diện

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun.mhvn.vn/api/auth/change-avatar

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `image` | `fileUpload` | Ảnh tải lên tối đa 2Mb định dạng jpg, jpeg, png |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Cập nhật ảnh đại diện thành công",
    "data": {
        "avatar": "[LINK_IMAGE]"
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
    "message": "Vui lòng chọn hình ảnh",
    "errors": {
        "image": [
            "Vui lòng chọn hình ảnh"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
