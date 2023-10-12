# Kiểm tra mã đại lý

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/agent/check-code

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | **Bắt buộc**. Mã đại lý |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mã đại lý hợp lệ",
    "data": {
        "id": "0BJkQpxngY",
        "name": "Đại lý mẫu 001"
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.id` ID của đại lý sử dụng để đăng ký tài khoản
- `data.name` tên đại lý

Dữ liệu không hợp lệ:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Mã đại lý không đúng (10004)",
    "errors": {
        "code": [
            "Mã đại lý không đúng (10004)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```

### Dữ liệu mẫu
Mã đại lý:
```
DMA0001
```
# Hình ảnh màn hình hiển thị
<img src="images/jotun_register_s1_1242x2688.png" width="360"/>
