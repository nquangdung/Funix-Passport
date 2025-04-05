### Backend này có vai trò gì, mục đích xây dựng là gì?

Backend trong dự án này có vai trò là trung tâm xử lý dữ liệu và giao tiếp giữa các thành phần của hệ thống. Mục đích xây dựng backend bao gồm:

- **Quản lý dữ liệu dịch thuật**: Lưu trữ và xử lý các file dịch thuật (phụ đề và tài liệu), metadata liên quan, và thông tin người dùng.
- **Cung cấp API**: Đảm bảo giao tiếp giữa frontend (bao gồm extension và giao diện quản lý) và cơ sở dữ liệu.
- **Xử lý nghiệp vụ**: Thực hiện các thao tác như xác thực người dùng, quản lý quyền truy cập, và xử lý các yêu cầu từ dịch thuật viên, quản trị viên, và sinh viên.
- **Đảm bảo bảo mật và hiệu suất**: Bảo vệ dữ liệu nhạy cảm, ngăn chặn các lỗ hổng bảo mật, và tối ưu hóa hiệu suất xử lý.

---

### Các vai trò nào sẽ sử dụng Backend? Mỗi vai trò sẽ được sử dụng những thao tác/chức năng gì?

#### 1. **Translator (Dịch thuật viên)**

- **Upload file dịch**: Gửi file phụ đề hoặc tài liệu đã dịch lên hệ thống.
- **Chỉnh sửa/xóa bản dịch**: Thực hiện các thao tác chỉnh sửa hoặc xóa các bản dịch đã upload.
- **Xem danh sách bản dịch**: Lấy danh sách các bản dịch đã thực hiện.
- **Tìm kiếm và lọc bản dịch**: Tìm kiếm và lọc danh sách bản dịch theo tiêu chí.

#### 2. **Admin (Quản trị viên)**

- **Quản lý tài khoản người dùng**: Thêm, xóa, hoặc chỉnh sửa quyền của người dùng (ví dụ: chuyển User thành Translator hoặc ngược lại).
- **Quản lý dữ liệu hệ thống**: Xóa hoặc chỉnh sửa các bản dịch trong hệ thống.
- **Theo dõi hoạt động**: Kiểm tra và giám sát các hoạt động của dịch thuật viên và sinh viên.

#### 3. **Student (Sinh viên)**

- **Xem tài liệu dịch**: Truy cập và tải xuống các tài liệu hoặc phụ đề đã được dịch.
- **Bật/tắt extension**: Tương tác với extension để hiển thị bản dịch trên các nền tảng học trực tuyến.

#### 4. **Reviewer (Người kiểm duyệt)**

- **Duyệt bài dịch**: Xem xét và phê duyệt hoặc từ chối các bài dịch do Translator gửi lên.
- **Gửi phản hồi**: Đưa ra nhận xét hoặc yêu cầu chỉnh sửa cho các bài dịch.

#### 5. **User (Người dùng thông thường)**

- **Đăng ký/đăng nhập**: Tạo tài khoản và đăng nhập vào hệ thống.
- **Xem thông tin cá nhân**: Quản lý thông tin tài khoản cá nhân.
