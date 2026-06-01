# Firebase Setup

Tài liệu này mô tả cách cấu hình Firebase cho CLB C1K mà không đưa thông tin riêng tư lên GitHub.

## 1. Tạo Firebase Project

1. Mở Firebase Console.
2. Tạo project mới hoặc dùng project hiện có.
3. Thêm Web App.
4. Copy Firebase config vào `index.html`.

Chỉ thay ở bản bạn dùng thật. Không commit bản có thông tin thật lên repo public.

## 2. Bật Authentication

Vào `Authentication` → `Sign-in method`, bật:

- `Email/Password`
- `Anonymous`

`Email/Password` dùng cho Admin và mật khẩu cấp 2. `Anonymous` dùng cho chế độ Viewer đọc dữ liệu.

## 3. Tạo 2 User Auth

Tạo 2 user khác email:

```text
admin@example.com      -> mật khẩu Admin cấp 1
security@example.com   -> mật khẩu cấp 2
```

User cấp 2 chỉ dùng để xác nhận thao tác nhạy cảm. Không cấp quyền ghi database cho user này.

## 4. Cấu Hình Realtime Database

Trong Realtime Database, tạo node:

```json
{
  "admins": {
    "UID_CUA_ADMIN_CAP_1": true
  }
}
```

Chỉ thêm UID của user Admin cấp 1.

Không thêm UID của user cấp 2 vào `/admins`.

## 5. Rules Gợi Ý

```json
{
  "rules": {
    ".read": "auth != null",
    "admins": {
      ".read": false,
      ".write": false
    },
    "clb_c1k": {
      ".read": "auth != null",
      ".write": "auth != null && root.child('admins').child(auth.uid).val() === true"
    },
    "clb_c1k_snapshots": {
      ".read": "auth != null",
      ".write": "auth != null && root.child('admins').child(auth.uid).val() === true"
    }
  }
}
```

## 6. Authorized Domains

Nếu deploy lên GitHub Pages, vào:

```text
Authentication -> Settings -> Authorized domains
```

Thêm domain GitHub Pages, ví dụ:

```text
your-user.github.io
```

## 7. Checklist Trước Khi Public

- `ADMIN_AUTH_EMAIL` vẫn là placeholder hoặc email demo.
- `LEVEL2_AUTH_EMAIL` vẫn là placeholder hoặc email demo.
- Firebase config không phải project riêng tư thật.
- Không có UID thật trong file.
- Không có dữ liệu club thật trong repo.
