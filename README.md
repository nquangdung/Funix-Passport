# FUNiX Passport - FX18096 Assignment 02 

## Thông Tin Sinh Viên
| Tiêu chí | Thông tin chi tiết |
| :--- | :--- |
| **Họ và tên học viên** | Nguyễn Ngọc Minh |
| **Mã sinh viên** | FX18096 |
| **Môn học** | SWE102x_03-A_VN Nhập môn kỹ thuật phần mềm |
| **Email học viên** | minhnnfx18096@funix.edu.vn |

---

## Mục Đích Của Repository
- Repository này được thiết lập nhằm mục đích quản lý, phát triển và lưu trữ toàn bộ mã nguồn cũng như tài liệu phân tích hệ thống thuộc bài toán Assignment 02 - SWE. 

- Mục tiêu cốt lõi:
1. Xử lý lỗi hệ thống liên quan đến luồng hiển thị phụ đề dịch thuật trên nền tảng học trực tuyến như Udemy, Coursera,..
2. Nâng cấp tính năng tự động kích hoạt phụ đề dựa trên trạng thái tải trang của Extension.
3. Tổ chức và lưu trữ hệ thống tài liệu đặc tả, sơ đồ thiết kế UML cho cả hai thành phần độc lập: Frontend Extension và Hệ thống quản lý Backend.


## Cấu Trúc Các Nhánh (Branch Workflow) Trong Dự Án
- Dự án được triển khai theo quy trình Git Workflow. Mã nguồn và tài liệu được phân tách độc lập thành 5 nhánh riêng biệt trước khi tích hợp vào nhánh chính (master):

| Tên Nhánh (Branch) | Vai Trò Hệ Thống | Nội Dung Lưu Trữ & Thay Đổi |
| :--- | :--- | :--- |
| **`1. master`** | Nhánh chính của dự án, chứa mã nguồn phiên bản ổn định nhất (Production-ready) | Chứa mã nguồn ổn định cuối cùng, file `README.md` tổng quan và là nơi tiếp nhận kết quả gộp nhánh (Merge) từ tất cả các nhánh tính năng, tài liệu bên dưới. |
| **`2. bug/clear_console_log`** | Sửa lỗi hệ thống (Bug fix) | iến hành rà soát và loại bỏ hoàn toàn các câu lệnh `console.log` dùng để debug trong file script chạy ngầm `script/subtitle/udemy-subtitle.js`. Thao tác này giúp tối ưu hóa hiệu năng và tránh rò rỉ thông tin log hệ thống ra trình duyệt của người dùng. |
| **`3. feat/auto_enable_subtitle`** | Nhánh phát triển tính năng mới (Feature development) | Chỉnh sửa cấu trúc logic của hàm điều hướng `pageLoad(code)` trong file `udemy-subtitle.js`. Chuyển đổi cơ chế từ "Hiển thị popup hỏi người dùng" sang "Tự động kích hoạt hiển thị phụ đề" ngay khi mã trạng thái phản hồi từ hệ thống tải thành công (`code === 200`).. |
| **`4. document`** | Nhánh lưu trữ tài liệu thiết kế hệ thống | Thư mục `documentation/diagram/` chứa các tệp sơ đồ phân tích dạng ảnh `.png` bao gồm: Sơ đồ Ca sử dụng (Use Case), Sơ đồ Lớp (Class), Sơ đồ Hoạt động (Activity) và Sơ đồ Trình tự (Sequence Diagram). Và File đặc tả hệ thống dạng Word (`.docx`) và phiên bản chuyển đổi định dạng tĩnh Markdown (`Document.md`) hiển thị trực tiếp trên giao diện GitLab..  |
| **`backend`** | Nhánh lưu trữ tài liệu đặc tả kiến trúc phía máy chủ (Backend System). | File `backend/backend.md` mô tả chi tiết về mục đích, vai trò của hệ thống quản lý phụ đề tập trung, danh sách các đối tượng tương tác (Học viên, Translator, Reviewer, Admin) cùng bảng đặc tả chức năng, phân quyền sử dụng hệ thống API. |