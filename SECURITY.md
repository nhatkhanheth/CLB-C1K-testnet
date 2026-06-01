# Security Policy

## Supported Version

Repo public này chỉ đại diện cho bản static HTML hiện tại.

## Reporting

Nếu phát hiện lỗi bảo mật, hãy mở issue với mô tả ngắn gọn, không đưa dữ liệu riêng tư hoặc credential thật vào issue.

## Public Repository Rules

Không commit:

- Mật khẩu.
- PIN.
- Email Admin thật.
- UID Firebase thật.
- Firebase config riêng tư nếu không muốn public.
- File export dữ liệu thật.

## Firebase Hardening

- Chỉ UID Admin cấp 1 được thêm vào `/admins`.
- User cấp 2 không được thêm vào `/admins`.
- Bật `Email/Password` và `Anonymous` trong Firebase Auth.
- Giới hạn write bằng Realtime Database Rules.
- Thêm đúng Authorized Domain khi deploy.
