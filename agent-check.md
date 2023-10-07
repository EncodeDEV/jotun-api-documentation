# Kiểm tra mã đại lý

API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md).

 Gửi request thông qua địa chỉ sau
 ```http
POST https://jotun..mhvn.vn/api/agent/check-code
```

Các tham số gửi lên

| Key | Type | Description |
| :--- | :--- | :--- |
| `code` | `string` | **Bắt buộc**. Chuỗi mã hóa hình ảnh |
| `device_id` | `string` | **Bắt buộc**. ID thiết bị |
| `action` | `string` | Hình thức xem thông tin, giá trị có thể là `scan`, `view` hoặc `input` tương ứng với quét mới, xem từ lịch sử hoặc nhập thủ công |
| `lat` | `string` | Tọa độ vị trí nếu có  |
| `lng` | `string` | Tọa độ vị trí nếu có  |
| `platform` | `string` | Loại hệ điều hành của thiết bị, giá trị có thể là `android`, `ios`  |
| `api_token` | `string` | Xác định tài khoản người dùng, giá trị là token trả về khi người dùng đăng nhập  |

### Kết quả trả về
