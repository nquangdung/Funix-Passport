# Tài liệu Hệ thống Backend - FUNiX Passport

## 1. Vai trò và Mục đích xây dựng Backend
* **Mục đích:** Hệ thống Backend được xây dựng nhằm mục đích quản lý tập trung dữ liệu phụ đề, quản lý các bản dịch ngôn ngữ (Việt - Anh) cho tài liệu học tập của học viên FUNiX. Đồng thời lưu trữ cấu hình hệ thống, lịch sử cập nhật và hỗ trợ tính năng dịch thuật đồng bộ theo thời gian thực trên các nền tảng học trực tuyến như Udemy, YouTube, Coursera.

* **Vai trò cốt lõi:**
*   **- Xác thực và Bảo mật:** Tiếp nhận request từ các Client (Extension, Dashboard), thực hiện giải mã và xác thực mã quyền hạn truy cập thông qua cơ chế JSON Web Token (JWT).
*   **- Tách biệt và Quản lý lưu trữ:** Trực tiếp quản lý việc lưu trữ Metadata (thông tin bản dịch, người dùng, lịch sử) vào hệ thống cơ sở dữ liệu (MySQL/PostgreSQL) với các ràng buộc về tính toàn vẹn dữ liệu, đồng thời quản lý đường dẫn URL trỏ tới các tệp tin phụ đề/tài liệu vật lý được lưu trữ tại Cloud Storage (AWS S3).
*   **- Kiểm soát chất lượng nội dung:** Xây dựng một quy trình khép kín, chuẩn hóa từ giai đoạn biên dịch đến xuất bản, giúp giải quyết triệt để bài toán kiểm soát chất lượng kiến thức trước khi đến tay người học thông qua bước duyệt trung gian của Reviewer.
*   **- Tối ưu hóa hiệu năng phản hồi:** Đáp ứng các ràng buộc khắt khe về mặt thời gian phản hồi (thời gian phản hồi API lấy bản dịch cho Extension dưới 1 giây và các thao tác xử lý nghiệp vụ khác dưới 0.5 giây).
*   **- Đảm bảo tính độc lập và khả năng mở rộng:** Áp dụng kiến trúc phân lớp (Layered Architecture - 4 Tier) nhằm tách biệt hoàn toàn Logic nghiệp vụ khỏi giao diện hiển thị. Điều này giúp hệ thống dễ dàng bảo trì, nâng cấp tính năng hoặc thêm mới các đối tượng sử dụng (như việc bổ sung thêm Reviewer và các lớp ReviewerDAO tương ứng) mà không làm ảnh hưởng đến cấu trúc hiện tại.

## 2. Các Đối Tượng Sử Dụng Và Thao Tác Chức Năng

Hệ thống Backend cung cấp các cổng API riêng biệt, được phân quyền chặt chẽ theo từng vai trò (Role) cụ thể:

### 2.1 Học viên (Thông qua Chrome Extension)
Là đối tượng tiêu thụ nội dung cuối cùng, tương tác với Backend một cách tự động thông qua Extension chạy trên trình duyệt (Coursera, Udemy).
*   **Gửi yêu cầu tìm kiếm bản dịch (`GET /api/v1/translations/search`):** Tự động gửi các tham số định danh như `url` (đối với tài liệu) hoặc `course_id` và `video_id` (đối với video bài học) lên Backend để tìm kiếm dữ liệu tương ứng.
*   **Nhận dữ liệu hiển thị:** Tiếp nhận Response Body dạng JSON chứa URL của tệp phụ đề Việt/Anh hoặc tệp tài liệu để Extension nhúng trực tiếp vào giao diện bài học (thẻ `<track>` cho video hoặc lớp Overlay cho Document).
*   *Ràng buộc nghiệp vụ:* Học viên chỉ có thể tìm thấy và sử dụng các bản dịch có trạng thái dữ liệu chính thức là `PUBLISHED`.

### 2.2 Người dịch (Translator)
Là đối tượng đóng góp và xây dựng nội dung phụ đề, tài liệu học tập cho hệ thống.
*   **Đăng nhập hệ thống:** Xác thực tài khoản thông qua hệ thống để nhận chuỗi mã JWT Token duy trì phiên làm việc.
*   **Upload bản dịch mới (`POST /api/v1/translator/upload`):** Gửi các file vật lý (.srt, .vtt, .pdf, .docx) dưới dạng `multipart/form-data` kèm theo chuỗi JSON chứa thông tin metadata như name, course_id, video_id.
*   **Quản lý bản dịch cá nhân:** Thực hiện các tác vụ chỉnh sửa thông tin hoặc xóa các bản dịch do chính mình sở hữu thông qua lớp truy vấn dữ liệu chuyên biệt (`TranslationDAO`).
*   *Ràng buộc nghiệp vụ:* Các bản dịch sau khi upload thành công sẽ tự động gán trạng thái ban đầu là `PENDING` (Chờ duyệt).

### 2.3. Người kiểm duyệt (Reviewer)
Là các chuyên gia hoặc giảng viên chịu trách nhiệm thẩm định, đánh giá chất lượng nội dung trước khi xuất bản công khai.
*   **Xem danh sách chờ duyệt (`GET /api/v1/reviewer/translations/pending`):** Sử dụng Dashboard riêng hiển thị danh sách các bản dịch mới upload đang ở trạng thái `PENDING`.
*   **Kiểm tra và đối chiếu:** Tải file về để đối chiếu với video gốc, xem nội dung hoặc kiểm tra thông tin metadata.
*   **Phê duyệt bản dịch (Approve):** Gọi API cập nhật trạng thái dữ liệu sang `PUBLISHED`. Lúc này, hệ thống sẽ tự động lưu vết mã người duyệt (`Reviewer_ID`) và thời gian phê duyệt (`Review_Date`) để Extension có thể tìm thấy dữ liệu.
*   **Từ chối và phản hồi (Reject):** Chuyển trạng thái bản dịch sang `REJECTED`, đồng thời nhập ghi chú lý do từ chối cụ thể (`Review_Note`) để gửi yêu cầu sửa đổi cho Translator.

### 2.4. Quản trị viên (Admin)
Là đối tượng có quyền hạn cao nhất, chịu trách nhiệm quản trị nhân sự và vận hành hệ thống.
*   **Quản lý người dùng (`PATCH /api/v1/admin/users/{user_id}/role`):** Sử dụng lớp chuyên biệt `AdminDAO` để thực hiện thay đổi quyền hạn hoặc cập nhật vai trò của các tài khoản trong hệ thống (ví dụ: cấp quyền giữa User thông thường và Translator).
*   *Ràng buộc nghiệp vụ:* Chỉ có những tài khoản có quyền Admin (xác thực qua Token) mới có thể gọi API này để đảm bảo an toàn hệ thống.