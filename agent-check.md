# Kiểm tra mã đại lý

API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md).

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/agent/check-code
```

Các tham số gửi lên

| Key | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | **Bắt buộc**. Mã đại lý |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
 ```http
HTTP STATUS: 200 OK
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

Dữ liệu không hợp lệ:
 ```http
HTTP STATUS: 200 OK
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
