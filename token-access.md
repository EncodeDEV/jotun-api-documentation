# Lấy token xác thực quyền truy cập Api

Gửi request thông qua địa chỉ sau

 ```http
POST https://jotun.mhvn.vn/oauth/token

Accept: application/json
Content-Type: application/json
```

Các tham số gửi lên

| Key | Type | Description |
| :--- | :--- | :--- |
| `grant_type` | `string` | **Bắt buộc**. Giá trị luôn là `client_credentials` |
| `client_id` | `string` | **Bắt buộc**. id truy cập được cung cấp trước |
| `client_secret` | `string` | **Bắt buộc**. key truy cập được cung cấp trước |
| `scope` | `string` | Cung cấp giới hạn truy cập nội dung cho phép, mặc định là `*` là tất cả |

### Kết quả trả về
Kết quả trả về dưới dạng JSON chứa thông tin token truy cập, ví dụ như sau

```javascript
{
    "token_type": "Bearer",
    "expires_in": 5183996,
    "access_token": "eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8"
}
```

- `token_type` là loại token, mặc định là _Bearer_
- `expires_in` thời gian hiệu lực của token, mặc định 1 năm
- `access_token` key xác thực quyền truy cập, lưu lại để sử dụng các API khác

Có thể gửi token xác thực thông quan Request Header `Authorization`:
```
`Authorization` : `Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8`
```
