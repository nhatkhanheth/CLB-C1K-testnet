# Privacy Notes

CLB C1K là app quản lý dữ liệu nội bộ của câu lạc bộ, vì vậy dữ liệu triển khai thật có thể chứa thông tin nhạy cảm.

## Không Nên Public

- Tên thật hoặc số dư thật của thành viên.
- Lịch sử chi tiêu thật.
- Dữ liệu export báo cáo.
- Email đăng nhập Admin.
- Email xác nhận cấp 2.
- UID Firebase.
- Rules hoặc config trỏ thẳng tới project thật nếu không muốn public.

## Khuyến Nghị

- Dùng repo public cho source code đã scrub.
- Dùng bản private hoặc bản local cho cấu hình thật.
- Kiểm tra `index.html` trước khi upload.
- Không upload các file backup cá nhân như `index-old.html`, video screen recording, ảnh chụp màn hình có dữ liệu thật.
