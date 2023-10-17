# Lấy thông tin hiển thị, giao diện

_API cần gửi các tham số bắt buộc [Xem tại đây](README.md) và cần xác thực bằng token, token có thể tạo ở API token đã được cung cấp [Xem tại đây](token-access.md)._

Sau khi lấy được dữ liệu lần đầu cần Cache lại để ứng dụng có thể sử dụng trong trường hợp Offline

 Gửi request thông qua địa chỉ sau
 ```http
GET https://jotun.mhvn.vn/api/config/layout

Accept: application/json
Authorization: Bearer eyJ0eXAiOiJKV-pmnw....8Dbv_l03p5WK2zHh8
Content-Type: application/json
```

Các tham số gửi lên ngoài tham số bắt buộc:

| Key | Type | Description |
| :--- | :--- | :--- |
| `s` | `string` | Tên giao diện cần lấy thông tin |

Tham số `s` có thể gửi một giá trị hoặc nhiều giá trị mỗi giá trị cách nhau bằng dấu phẩy `,`

Tham số `s` gồm các giá trị sau:
- `all`: Lấy tất cả thông tin
- `scan`: Màn hình quét mã
- `register`: Màn hình đăng ký bao gồm `Kiểm tra mã đại lý` và `Nhập thông tin tài khoản`
- `otp`: Màn hình nhập mã OTP
- `login`: Màn hình đăng nhập
- `qr`: Màn hình hiển thị thông tin mã QR
- `barcode`: Màn hình hiển thị thông tin mã vạch
- `report`: Màn hình báo lỗi
- `history`: Màn hình lịch sử quét
- `actived_codes`: Màn hình danh sách mã đã kích hoạt
- `account`: Màn hình thông tin tài khoản
- `account_update`: Màn hình cập nhật thông tin tài khoản
- `change_pwd`: Màn hình cập nhật mật khẩu

### Kết quả trả về
Kết quả nếu tham số `s` trống hoặc không có hoặc không nằm trong danh sách qui định:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "hotline": {
        "label": "HOTLINE:",
        "number": "1800 1511"
    },
    "popup": {
        "ok": {
            "btn": "Okey"
        },
        "warning": {
            "btn": "Okey"
        },
        "confirm": {
            "btn_confirm": "Chắc chắn",
            "btn_cancel": "Hủy"
        }
    },
    "layout": []
}
```

Kết quả nếu tham số `s` gửi một giá trị hợp lệ, ví dụ _s=scan_:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "hotline": {
        ...
    },
    "popup": {
        ...
    },
    "layout": {
        "text": {
            "guide": "Hướng camera về phía mã QR hoặc mã vạch"
        },
        "button": {
            "account": "ĐẠI LÝ",
            "account_auth": "TÀI KHOẢN",
            "history": "LỊCH SỬ"
        },
        "modal": {
            "title": "Hướng dẫn quét mã vạch",
            "contents": [
                "Hướng Camera về phía mã và chờ cho đến khi lấy nét hình ảnh.",
                "Không đưa camera quá gần. Nếu không lấy nét được, hãy di chuyển camera đến gần hoặc ra xa mã.",
                "Nếu không đủ ánh sáng, hãy bật đèn flash bằng nút bật đèn giữa màn hình"
            ],
            "button": {
                "close": "ĐÃ HIỂU"
            },
            "links": {
                "tos": {
                    "title": "Điều khoản sử dụng",
                    "action": "web_view",
                    "url": "[LINK_WEBVIEW]"
                },
                "pp": {
                    "title": "Chính sách bảo mật",
                    "action": "web_view",
                    "url": "[LINK_WEBVIEW]"
                }
            }
        }
    }
}
```

Kết quả nếu tham số `s` gửi nhiều giá trị hợp lệ, ví dụ _s=register,otp_:
 ```http
STATUS: 200 OK
Content-Type: application/json
```
```javascript
{
    "hotline": {
        ...
    },
    "popup": {
        ...
    },
    "layout": {
        "register": {
            "input": {
                "agent": {
                    "label": null,
                    "placeholder": "Mã đại lý"
                },
                "name": {
                    "label": null,
                    "placeholder": "Tên hiển thị"
                },
                "phone": {
                    "label": null,
                    "placeholder": "Số điện thoại"
                },
                "username": {
                    "label": null,
                    "placeholder": "Tên đăng nhập"
                },
                "email": {
                    "label": null,
                    "placeholder": "Email"
                },
                "password": {
                    "label": null,
                    "placeholder": "Mật khẩu"
                },
                "password_confirmtion": {
                    "label": null,
                    "placeholder": "Mật khẩu"
                }
            },
            "button": {
                "submit": "ĐĂNG KÝ"
            },
            "text": {
                "login": "Đăng nhập",
                "login_hint": "Đã có tài khoản?",
                "tos_hint": "Bằng việc click Đăng ký bạn đã đồng ý với",
                "guide_s1": "Nhập mã đại lý được Jotun cung cấp",
                "guide_s3": "Xác thực số điện thoại để hoàn thành đăng ký"
            },
            "links": {
                "tos": {
                    "title": "Điều khoản sử dụng",
                    "action": "web_view",
                    "url": "[LINK_WEBVIEW]"
                }
            }
        },
        "otp": {
            "text": {
                "guide": "Nhập mã xác thực nhận được",
                "resend": {
                    "hint": "Không nhận được mã?",
                    "send": "Gửi lại",
                    "wait": "Gửi lại sau 60s",
                    "limit_hint": "Bạn đã yêu cầu mã 3 lần",
                    "limit": "Vui lòng thử lại sau 24 giờ"
                }
            }
        }
    }
}
```
