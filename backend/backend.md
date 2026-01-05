1\. Vai trò và mục đích xây dựng

Vai trò: Hệ thống Backend đóng vai trò là trung tâm quản lý dữ liệu và
điều phối các hoạt động của Extension. Nó đảm bảo việc lưu trữ và xử lý
các thông tin phức tạp mà trình duyệt không thể xử lý đơn lẻ.

Mục đích: \* Lưu trữ cài đặt của người dùng (như tùy chọn tự động hiển
thị phụ đề) một cách bền vững trên cơ sở dữ liệu.

Cung cấp các API để Extension có thể truy xuất bản dịch và dữ liệu phụ
đề từ máy chủ một cách nhanh chóng.

Đảm bảo tính bảo mật và đồng bộ hóa dữ liệu khi người dùng sử dụng
Extension trên nhiều thiết bị khác nhau.

2\. Các vai trò sử dụng Backend và Chức năng

A. Người dùng cuối (End User - Học viên)

Vai trò: Sử dụng Extension để hỗ trợ việc học tập qua video.

Thao tác/Chức năng:

Đồng bộ hóa cài đặt: Tự động lưu và tải các cấu hình cá nhân (ngôn ngữ,
kích thước phụ đề, chế độ hiển thị).

Truy xuất phụ đề: Gửi yêu cầu lên Backend để nhận dữ liệu phụ đề tương
ứng với video đang xem.

B. Quản trị viên (Administrator)

Vai trò: Quản lý nội dung và giám sát hoạt động của toàn bộ hệ thống.

Thao tác/Chức năng:

Quản lý dữ liệu phụ đề: Cập nhật, sửa đổi hoặc thêm mới các bản dịch phụ
đề vào cơ sở dữ liệu.

Giám sát hệ thống: Theo dõi hiệu suất của Backend và quản lý quyền truy
cập của người dùng.

Cấu hình hệ thống: Điều chỉnh các thông số kỹ thuật của máy chủ để đảm
bảo tính ổn định.
