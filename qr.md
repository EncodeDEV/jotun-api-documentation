# Kiểm tra và lấy thông tin mã QR khi quét

API chỉ gọi khi quét mã là mã QR, với mã vạch sử dụng [API này](barcode.md). Để giảm request tới hệ thống, chỉ gửi dữ liệu khi là nội dung URL, nếu nội dụng QR là văn bản thì hiển thị như hình phía dưới.

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun..mhvn.vn/api/code/qrcode

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | **Bắt buộc**. Nội dung mã QR |
| `action` | `string` | **Bắt buộc**. Cách thức lấy nội dung mã QR từ chức năng quét hoặc chức năng khác như Lịch sử, Danh sách mã đã kích hoạt (với tài khoản đăng nhập). Giá trị là `scan` hoặc `view` |
| `account_token` | `string` | Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ:

Trường hợp mã QR đã được đại lý kích hoạt:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "code": "[QR_CONTENT]",
        "qr": {
            "serial": "10000000003",
            "view": 1,
            "last_view": null,
            "actived_at": "06:55, 07/10/2023"
        },
        "product": {
            "name": "Sản phẩm mẫu 00001",
            "lot": null
        },
        "agent": {
            "id": "86jk4mOZ9D",
            "name": "Đại lý mẫu 0002",
            "address": null,
            "phone": "0707 88 7070",
            "fax": null,
            "hotline": null,
            "email": null,
            "website": null
        }
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.code` Nội dung mã QR
- `data.qr` Thông tin mã QR
- `data.product` Thông tin sản phẩm nếu có
- `data.agent` Thông tin đại lý kích hoạt

<details>
<summary>Màn hình hiển thị trường hợp này như sau</summary>
<img src="images/jotun_qr_1242x2688.png" width="300">
</details>

