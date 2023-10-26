# Hiển thị banner quảng cáo dạng popup

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/adv/single

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `type` | `string` | *Bắt buộc* Loại quảng cáo, giá trị hiện tại là image  |
| `pos` | `string` | *Bắt buộc* Vị trí hiển thị, giá trị hiện tại là popup  |

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
        "image": "[URL_IMAGE]",
        "url": "[URL_OPEN]"
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.image` Hình ảnh quảng cáo
- `data.url` Địa chỉ trang web mở khi click quảng cáo

_* Lưu ý: data có giá trị là mảng rỗng nghĩ là không hiển thị quảng cáo_

Dữ liệu gửi lên không hợp lệ
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Không xác định thiết bị (11070)",
    "errors": {
        "device_id": [
            "Không xác định thiết bị (11070)"
        ]
    },
    "status": "INVALID_FIELD",
    "status_code": 422
}
```
