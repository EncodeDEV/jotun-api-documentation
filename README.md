# JOTUN Mobile App API Documentation by VietCheck

## API xác thực quyền truy cập bằng key đã được cung cấp:

- [Lấy token xác thực quyền truy cập](token-access.md)

Các API cần sau cần có token được lấy từ API xác thực trên để có thể truy cập

## Danh sách các API liên quan tới tài khoản đăng nhập:

- [Kiểm tra mã đại lý](agent-check.md)
- [Đăng ký tài khoản đại lý](register.md)
- [Đăng nhập tài khoản đại lý bằng username](login.md)
- [Đăng nhập tài khoản đại lý bằng số điện thoại](login-phone.md)
- [Cập nhật xác thực số điện thoại](phone-verify-update.md)
- [Kiểm tra trạng thái đăng nhập](check-login-status.md)
- [Lấy thông tin tài khoản](user.md)
- [Cập nhật thông tin tài khoản](update-user.md)
   - Xác thực mật khẩu trước khi cập nhật tài khoản
- [Cập nhật ảnh đại diện](change-avatar.md)
- [Lấy danh sách mã đã kích hoạt](https://github.com)
- [Lấy thông tin chi tiết mã](code-detail.md)

Danh sách các API quét mã:

- [Lấy thông tin mã QR](https://github.com)
- [Lấy thông tin mã vạch](https://github.com)
- [Gửi báo sai thông tin](https://github.com)

## Danh sách các API khác:

- Lấy thông tin hiển thị Menu tài khoản
- Trạng thái ứng dụng: Bắt buộc hoặc khuyến nghị cập nhật, thông báo bảo trì

## Response Status, Status Code

## HTTP Status có thể trả về

API trả về một số https status code sau:

| Status Code | Status | Description
| :--- | :--- | :--- | 
| 200 | `OK` | Xử lý yêu cầu thành công |
| 401 | `UNAUTHORIZED` | Yêu cầu chưa được xác thực |
| 400 | `BAD REQUEST` | Yêu cầu không thể xử lý |
| 403 | `REQUEST DENIED` | Không có quyền truy cập |
| 404 | `NOT FOUND` | Không tìm thấy dữ liệu |
| 422 | `INVALID FIELD` | Có dữ liệu gửi lên không cho phép |
| 500 | `INTERNAL SERVER ERROR` | Lỗi hệ thống hoặc máy chủ |
