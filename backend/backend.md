\# Tài liệu Backend - Dự án FUNiX Passport



\## 1. Vai trò và Mục đích xây dựng

Backend đóng vai trò là "bộ não" trung tâm của hệ thống FUNiX Passport, có nhiệm vụ quản lý, lưu trữ và xử lý toàn bộ dữ liệu để phục vụ cho các hoạt động của Extension.



\* \*\*Mục đích xây dựng:\*\*

&nbsp;   \* \*\*Quản lý tập trung:\*\* Lưu trữ dữ liệu về người dùng, các bản dịch phụ đề video và tài liệu học tập.

&nbsp;   \* \*\*Cung cấp API:\*\* Phục vụ các yêu cầu từ phía Client (Extension) như xác thực người dùng, tìm kiếm và hiển thị bản dịch tương ứng với URL trang web (Udemy, Coursera...).

&nbsp;   \* \*\*Đảm bảo tính nhất quán:\*\* Giúp đồng bộ hóa dữ liệu giữa các bộ phận: Admin (quản trị), Translator (người dịch) và Student (người dùng cuối).



\## 2. Các vai trò và Chức năng trên Backend

Dựa trên yêu cầu hệ thống, có 3 nhóm người dùng chính tương tác với Backend:



\### A. Quản trị viên (Admin)

Đây là nhóm có quyền hạn cao nhất để vận hành hệ thống.

\* \*\*Quản lý tài khoản:\*\* Xem danh sách, tạo mới, chỉnh sửa hoặc xóa các tài khoản trong hệ thống.

\* \*\*Phân quyền hệ thống:\*\* Cấp quyền hoặc thu hồi quyền \*\*Translator\*\* cho người dùng (User).

\* \*\*Quản trị dữ liệu:\*\* Kiểm soát các bản dịch đã được tải lên hệ thống.



\### B. Người dịch thuật (Translator)

Nhóm đóng góp nội dung cho hệ thống.

\* \*\*Quản lý bản dịch:\*\* Thêm mới các bản dịch cho Video hoặc Tài liệu (Document).

\* \*\*Cập nhật dữ liệu:\*\* Chỉnh sửa hoặc xóa các bản dịch do mình quản lý để đảm bảo chất lượng nội dung.



\### C. Sinh viên / Người dùng (Student / User)

Nhóm sử dụng dịch vụ thông qua Extension.

\* \*\*Xác thực:\*\* Đăng nhập để sử dụng các tính năng cá nhân hóa.

\* \*\*Truy vấn dữ liệu:\*\* Gửi URL trang web đang xem để Backend tìm kiếm và trả về bản dịch phù hợp.

\* \*\*Xem nội dung:\*\* Hiển thị bản dịch phụ đề hoặc tài liệu đã được hệ thống phê duyệt.

