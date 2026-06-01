# CLB C1K

Ứng dụng web tĩnh để quản lý quỹ, công nợ, chi tiêu buổi chơi và bảng xếp hạng thành viên cho một câu lạc bộ nhỏ.

![CLB C1K logo](./logo.svg)

## Điểm Chính

- Theo dõi số dư từng thành viên, quỹ Team và quỹ Birthday.
- Ghi chi tiêu theo buổi, chia đều, cùng số tiền hoặc trừ quỹ.
- Quản lý nạp tiền, trả nợ, trừ tiền và lịch sử giao dịch.
- Copy nội dung Messenger cho từng giao dịch hoặc tổng hợp theo tháng.
- Tạo lịch tennis theo tháng để copy nhanh.
- BXH chi tiêu/tham gia theo snapshot tháng trước và bảng công nợ hiện tại.
- Đăng nhập Admin bằng Firebase Authentication.
- Mật khẩu cấp 2 dùng một Firebase Auth user riêng để xác nhận thao tác nhạy cảm.
- Hỗ trợ giao diện mobile/PWA, chạy trực tiếp bằng file HTML hoặc GitHub Pages.

## Cấu Trúc

```text
.
├── index.html
├── logo.svg
├── README.md
├── SECURITY.md
├── CHANGELOG.md
├── LICENSE
├── .gitignore
└── docs
    ├── FIREBASE_SETUP.md
    └── PRIVACY.md
```

## Chạy Local

Vì app là static HTML, có thể mở trực tiếp:

```text
index.html
```

Hoặc chạy bằng server local nếu trình duyệt chặn một số tính năng:

```bash
python -m http.server 8080
```

Sau đó mở:

```text
http://localhost:8080
```

## Cấu Hình Firebase

File `index.html` trong repo public đang dùng placeholder, không chứa thông tin riêng tư. Trước khi dùng thật, thay các giá trị trong phần `cfg` và email Auth:

```js
const cfg = {
  apiKey: "YOUR_FIREBASE_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.REGION.firebasedatabase.app",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.firebasestorage.app",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_FIREBASE_APP_ID"
};

const ADMIN_AUTH_EMAIL = "admin@example.com";
const LEVEL2_AUTH_EMAIL = "security@example.com";
```

Xem hướng dẫn chi tiết trong [docs/FIREBASE_SETUP.md](./docs/FIREBASE_SETUP.md).

## Bảo Mật

Không commit các thông tin sau lên GitHub:

- Email Admin thật.
- Email cấp 2 thật.
- UID Firebase thật.
- Mật khẩu, PIN, dữ liệu export, dữ liệu club thật.
- File backup HTML cá nhân có chứa Firebase config thật.

Repo này chỉ nên chứa bản public đã scrub thông tin nhạy cảm.

## Deploy Lên GitHub Pages

1. Tạo repo mới trên GitHub.
2. Upload toàn bộ nội dung trong thư mục này.
3. Vào `Settings` → `Pages`.
4. Chọn branch `main`, folder `/root`.
5. Chờ GitHub Pages build xong và mở URL được cấp.

Nếu dùng Firebase Authentication với GitHub Pages, nhớ thêm domain GitHub Pages vào `Authentication` → `Settings` → `Authorized domains`.

## License

MIT. Xem [LICENSE](./LICENSE).
