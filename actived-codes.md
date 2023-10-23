# Lấy danh sách mã QR đã kích hoạt

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/code/actived-codes-by-agent

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `account_token` | `string` | **Bắt buộc**. Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |
| `page` | `integer` | Trang dữ liệu cần lấy |
| `per` | `integer` | Số bản ghi dữ liệu trên một trang |
| `d` | `integer` | Ngày kích hoạt |
| `m` | `integer` | Tháng kích hoạt |
| `y` | `integer` | Năm kích hoạt |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "current_page": 1,
        "per": 15,
        "total_items": 1,
        "items": [
            {
                "id": "KVqRPklj3G",
                "serial": "10000000001",
                "p_url": "[URL]",
                "actived_at": "14:32, 10/10/2023",
                "view": 3,
                "report_count": 13,
                "status": "actived"
            }
        ]
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.current_page` Trang dữ liệu hiện tại
- `data.per` Số bản ghi dữ liệu của một trang
- `data.total_items` Số bản ghi thực tế của trang hiện tại
- `data.items` Dữ liệu của từng bản ghi
- `data.items.*.id` ID của mã đã kích hoạt
- `data.items.*.serial` Serial của mã đã kích hoạt
- `data.items.*.p_url` Nội dung được mã hóa của mã QR
- `data.items.*.actived_at` Ngày kích hoạt mã
- `data.items.*.view` Lượt truy cập thông tin mã
- `data.items.*.report_count` Lượt báo sai thông tin của mã
- `data.items.*.status` Trạng thái hệ thống của mã: _actived_ là đã kích hoạt, _blocked_ là đang khóa, _trashed_ là đã xóa

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
