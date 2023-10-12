# Kiểm tra và lấy thông tin mã vạch khi quét

API chỉ gọi khi quét mã là mã vạch, với mã QR sử dụng [API này](qr.md).

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/code/barcode

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | **Bắt buộc**. Nội dung mã vạch |
| `action` | `string` | **Bắt buộc**. Cách thức lấy nội dung mã QR từ chức năng quét hoặc chức năng khác như Lịch sử, Danh sách mã đã kích hoạt (với tài khoản đăng nhập). Giá trị là `scan` hoặc `view` |
| `account_token` | `string` | Token xác thực tài khoản đăng nhập nhận được khi đăng nhập [Xem tại đây](login.md) |

### Kết quả trả về
Kết quả dữ liệu hợp lệ, mã vạch được hỗ trợ:

Trường hợp mã vạch có thông tin sản phẩm:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "code": {
            "code": "8936144810330",
            "country": "Việt Nam"
        },
        "enterprise": {
            "name": "Công ty TNHH OLIC Việt Nam",
            "address": "Tầng 11, tòa nhà Zen Tower , số 12 Khuất Duy Tiến, Thanh Xuân Trung, Quận Thanh Xuân, TP. Hà Nội",
            "phone": null,
            "hotline": null,
            "fax": null,
            "email": null,
            "website": null,
            "view_more": "[URL_WEB_VIEW]"
        },
        "product": {
            "name": "Huyết Thanh Truyền Trắng – Serum 7Day Olic",
            "image": "[URL_IMAGE]"
        }
    },
    "status": "OK",
    "status_code": 200
}
```

- `data.code` Thông tin mã vạch
- `data.enterprise` Thông tin doanh nghiệp sở hữu
- `data.product` Thông tin sản phẩm nếu có

<details>
<summary>Màn hình hiển thị trường hợp này như sau</summary>
<img src="images/jotun_barcode_1242x2688.png" width="300">
</details>

Trường hợp mã vạch chưa thông tin sản phẩm:
```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "message": "Lấy thông tin thành công",
    "data": {
        "code": {
            "code": "8936188550070",
            "country": "Việt Nam"
        },
        "enterprise": {
            "name": "CHI NHÁNH MINH VŨ - CÔNG TY TNHH ĐỊNH BÍCH",
            "address": "Xóm 4, Xã Xuân Châu, Huyện Thọ Xuân, Tỉnh Thanh Hóa",
            "phone": null,
            "hotline": null,
            "fax": null,
            "email": null,
            "website": null,
            "view_more": "[URL_WEB_VIEW]"
        },
        "product": {
            "name": null,
            "image": null
        }
    },
    "status": "OK",
    "status_code": 200
}
```

<details>
<summary>Màn hình hiển thị trường hợp này như sau</summary>
<img src="images/jotun_barcode_no_product_1242x2688.png" width="300">
</details>

### Dữ liệu mẫu
Mã vạch
```
8936144810330, 8936188550070
```
