# Lấy thông tin tài khoản đang đăng nhập

API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md).

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun..mhvn.vn/api/auth/check

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
    "message": "Lấy dữ liệu thành công",
    "status": "OK",
    "status_code": 200,
    "data": {
        "user": {
            "name": "Tai khoan test 0004",
            "username": "daily4",
            "avt": null | "[LINK_IMAGE]",
            "phone": "+84987888555",
            "phone_verified": false,
            "email": null,
            "email_verified": false,
            "registered_at": "22:30, 30/09/2023",
            "last_login_at": "05:29, 07/10/2023"
        },
        "agent": {
            "code": "DMA0002",
            "name": "Đại lý mẫu 0002",
            "address": null,
            "phone": "0707 88 7070",
            "description": ""
        }
    }
}
```

- `data.user` Thông tin tài khoản
- `data.agent` Thông tin đại lý

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

# Hình ảnh màn hình hiển thị
![](images/jotun_user_1242x2688.png){: width="50%"}
