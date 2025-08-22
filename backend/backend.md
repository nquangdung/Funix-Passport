## Backend – Vai trò và mục đích

Backend là hệ thống API trung tâm để:
- Quản lý người dùng và phân quyền (User, Translator, Admin)
- Lưu trữ và quản lý metadata các bản dịch (Document, Video Subtitle)
- Xử lý upload/download file dịch thuật
- Cung cấp API cho Extension để tra cứu và trả về bản dịch nhanh chóng
- Đảm bảo bảo mật, xác thực và phân quyền khi truy cập dữ liệu

## Vai trò sử dụng Backend và chức năng

### Student (người dùng cuối, sử dụng qua Extension)
- Gửi yêu cầu tra cứu bản dịch theo URL/Course ID/Video ID
- Nhận và xem nội dung bản dịch (phụ đề/video, tài liệu)

### Translator (dịch thuật viên)
- Upload phụ đề đã dịch (nhập: Tên video, URL video, Course ID, Video ID; đính kèm file)
- Upload tài liệu đã dịch (nhập: Tên bản dịch, URL; đính kèm file)
- Quản lý bản dịch đã upload:
  - Xem danh sách (Dashboard riêng cho phụ đề và Document)
  - Tải xuống file đã dịch
  - Tìm kiếm theo bộ lọc: Tên, URL, Người dịch, Course ID, Video ID
  - Chỉnh sửa metadata, re-upload file dịch
  - Xóa bản dịch không cần thiết

### Admin (quản trị viên)
- Quản lý tài khoản người dùng
- Thêm quyền Translator cho User
- Thu hồi quyền (chuyển Translator về User)
- Xóa tài khoản người dùng

Ghi chú: Tất cả thao tác đều yêu cầu xác thực và được kiểm soát bởi phân quyền của hệ thống.

