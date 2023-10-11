# Lấy thông tin mã QR đã kích hoạt

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun..mhvn.vn/api/code/actived-code-detail

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `id` | `string` | **Bắt buộc**. ID của mã lấy được từ API khác ví dụ API lấy danh sách mã đã kích hoạt [Xem tại đây](list-codes.md) |

### Kết quả trả về
Kết quả với dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "id": "KVqRPklj3G",
        "serial": "10000000001",
        "view": 3,
        "scan": 2,
        "last_view_at": "08:45, 03/10/2023",
        "actived_at": "14:32, 10/10/2023",
        "p_url": "[URL]",
        "image": "[LINK_IMAGE]",
        "status": "actived"
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.id` ID của mã đang xem
- `data.serial` Serial của mã đã kích hoạt
- `data.last_view_at` Thời gian truy cập lần cuối
- `data.actived_at` Ngày kích hoạt mã
- `data.view` Lượt truy cập thông tin mã
- `data.scan` Lượt quét mã
- `data.report_count` Lượt báo sai thông tin của mã
- `data.status` Trạng thái hệ thống của mã: _actived_ là đã kích hoạt, _blocked_ là đang khóa, _trashed_ là đã xóa
- `data.p_url` Nội dung được mã hóa của mã QR
- `data.image` Hình ảnh mã QR

Account Token không đúng:
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

Tham số không chính xác
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```
{
    "message": "Mã không chính xác",
    "errors": {
        "id": [
            "Mã không chính xác"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
