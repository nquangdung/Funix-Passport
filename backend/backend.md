# FUNiX Passport
FUNiX đang cần xây dựng một hệ thống giúp sinh viên xem được các tài liệu Tiếng Việt, bao gồm cả phụ đề cho video và trang tài liệu. Mục tiêu của hệ thống là giúp học viên nắm bắt kiến thức từ videodễ dàng hơn bằng cách cung cấp các bản dịch tiếng Việt thay vì chỉ có phụ đề Tiếng Anh.

- Backend trong yêu cầu của bạn có vai trò quản lý các hoạt động liên quan đến dữ liệu dịch thuật và phụ đề. Mục đích chính của việc xây dựng Backend là cung cấp cho các dịch thuật viên (Translator) 
và quản trị viên (Admin) một giao diện để tải lên, quản lý và tìm kiếm các file dịch thuật (phụ đề hoặc tài liệu dịch).

Có 3 vai trò chính trong hệ thống:

1. Người dùng (User): Đây là vai trò của người dùng bình thường. Người dùng có thể đăng nhập và đăng xuất khỏi ứng dụng.

2. Dịch thuật viên (Translator): Đây là vai trò của các dịch thuật viên. Translator có thể thực hiện các thao tác sau trên ứng dụng:
+ Upload file phụ đề đã dịch tiếng Việt cho video.
+ Upload file tài liệu đã dịch tiếng Việt.
+ Xem danh sách các file dịch thuật đã được upload (Dashboard).
+ Tải xuống file đã dịch (phụ đề hoặc tài liệu).
+ Tìm kiếm các bản dịch theo bộ lọc (tên, URL, người dịch, Course ID, Video ID).
+ Xóa các file phụ đề hoặc tài liệu.
+ Chỉnh sửa thông tin các file dịch (metadata) và có thể re-upload file dịch khác.

3. Quản trị viên (Admin): Đây là vai trò của các quản trị viên. Admin có thể thực hiện các thao tác như sau:
+ Xóa tài khoản một người dùng.
+ Thêm quyền cho một người dùng (chuyển User thành Translator).
+ Xóa quyền của một người dùng (chuyển Translator thành User).

Backend sẽ cung cấp cơ sở dữ liệu để lưu trữ các thông tin metadata cho mỗi bản dịch dành cho video hoặc tài liệu. Các thông tin metadata bao gồm: ID, Tên Translator, Ngày upload, Tên bản dịch, URL (video hoặc tài liệu), Video ID (nếu là bản dịch cho video), Course ID, Đường dẫn đến file phụ đề tiếng Việt, và tùy chọn, đường dẫn đến file phụ đề tiếng Anh (nếu có). Đối với bản dịch của tài liệu, sẽ có trường Document URL thay vì Video ID.

Backend cần đảm bảo các vai trò (User, Translator, Admin) có quyền truy cập và sử dụng các chức năng tương ứng của mình dựa trên yêu cầu trên
