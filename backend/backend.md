## Mục đích và vai trò của Backend
Backend trong dự án này chính là cầu nối giữa Database và Client (extension Chrome của người dùng). Mục tiêu chính của việc xây dựng Backend là để:

- Xử lý và kiểm soát các truy vấn dữ liệu từ và đến Database.
- Xử lý logic của ứng dụng, bao gồm quản lý quyền truy cập và các thao tác trên dữ liệu.
- Cung cấp API để extension Chrome có thể giao tiếp và tương tác với dữ liệu.
- Các vai trò sử dụng Backend
- Có 4 vai trò sẽ sử dụng Backend, bao gồm các thao tác/chức năng dưới đây:

  - User: Sử dụng Backend để đăng nhập và đăng xuất khỏi ứng dụng và xem phụ đề. Backend cung cấp API để User có thể truy cập và xem dữ liệu phụ đề từ Database.

  - Reviewer: Sử dụng Backend để phê duyệt các bài dịch của Translator. Backend cung cấp API để Reviewer có thể truy cập và phê duyệt các bài dịch.

  - Translator: Sử dụng Backend để thực hiện các thao tác sau:
    - Upload file phụ đề hoặc Document đã dịch.
    - Xem danh sách các file dịch thuật đã được upload.
    - Tải xuống file đã dịch.
    - Tìm kiếm các bản dịch theo bộ lọc.
    - Xóa các file phụ đề hoặc document.
    - Chỉnh sửa thông tin.

  - Admin: Sử dụng Backend để quản lý tài khoản người dùng, bao gồm xóa tài khoản, thêm quyền, và xóa quyền cho người dùng. Backend cung cấp các API để Admin có thể thực hiện những thao tác này.