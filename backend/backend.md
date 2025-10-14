# Backend Documentation

## 1. Mục đích

Backend của **FUNiX Passport** được xây dựng nhằm xử lý các yêu cầu liên quan đến việc lưu trữ, xác thực và quản lý dữ liệu học viên.  
Nó đóng vai trò là trung gian giữa **frontend (extension trên trình duyệt)** và **các hệ thống dữ liệu** của FUNiX.

---

## 2. Vai trò sử dụng

### Học viên (Student)

- Đăng nhập / xác thực người dùng.
- Gửi yêu cầu tra cứu khóa học.
- Lưu lại trạng thái học (video, bài quiz, …).

### Admin

- Theo dõi tiến độ học viên.
- Quản lý danh sách học viên, khóa học.
- Duyệt hoặc phản hồi yêu cầu hỗ trợ.

---

## 3. Chức năng chính

- API xác thực học viên (Login, Logout)
- API lấy danh sách khóa học, video
- API lưu trạng thái học tập
- API cho mentor quản lý dữ liệu người học
