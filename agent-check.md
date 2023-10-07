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

### Dữ liệu mẫu
Mã đại lý:
```
DMA0001
```
