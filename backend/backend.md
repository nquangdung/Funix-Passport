# BACKEND
## 1. Backend có vai trò gì?
Backend đóng vai trò quan trọng trong việc vận hành một ứng dụng hoặc trang web, đảm nhiệm các chức năng "hậu trường" mà người dùng không nhìn thấy trực tiếp. Nó đóng vai trò như bộ não, xử lý các yêu cầu, logic và dữ liệu để mang đến trải nghiệm mượt mà cho người dùng.

### Mục đích chính của việc xây dựng backend:
- **Lưu trữ và quản lý dữ liệu:** Backend lưu trữ dữ liệu trong cơ sở dữ liệu, đảm bảo tính bảo mật và toàn vẹn. Nó cung cấp các API để truy cập và thao tác dữ liệu cho các thành phần khác của ứng dụng.
- **Xử lý logic:** Backend thực thi các quy tắc kinh doanh, logic ứng dụng và các thuật toán để đáp ứng các yêu cầu của người dùng. Ví dụ: khi bạn đăng nhập vào trang web, backend sẽ xác thực thông tin đăng nhập của bạn và cấp quyền truy cập phù hợp.
- **Kết nối với các dịch vụ bên ngoài:** Backend có thể kết nối với các dịch vụ bên ngoài như thanh toán trực tuyến, gửi email hoặc mạng xã hội để mở rộng chức năng của ứng dụng.
- **Quản lý người dùng:** Backend quản lý tài khoản người dùng, xác thực, phân quyền và các chức năng liên quan đến người dùng khác.
- **Đảm bảo bảo mật:** Backend triển khai các biện pháp bảo mật để bảo vệ dữ liệu và ứng dụng khỏi các truy cập trái phép, tấn công mạng và các mối đe dọa khác.
- **Tối ưu hóa hiệu suất:** Backend tối ưu hóa truy vấn cơ sở dữ liệu, sử dụng bộ nhớ cache và các kỹ thuật khác để đảm bảo ứng dụng hoạt động nhanh và mượt mà.

Ngoài ra, backend còn có thể bao gồm các chức năng khác như:
- **Xử lý hình ảnh và video:** Backend có thể xử lý hình ảnh và video, chẳng hạn như thay đổi kích thước, nén hoặc áp dụng các bộ lọc.
- **Gửi thông báo:** Backend có thể gửi email, tin nhắn SMS hoặc thông báo đẩy cho người dùng.
- **Tạo báo cáo:** Backend có thể tạo báo cáo và phân tích dữ liệu để cung cấp thông tin chi tiết về hiệu suất ứng dụng và hành vi của người dùng.

## 2. Các vai trò nào sẽ sử dụng Backend? Mỗi vai trò sẽ được sử dụng những thao tác/chức năng gì?
1. **Backend Developer (Lập trình viên Backend)**:
    - **Máy chủ**: Backend Developer đảm nhận trách nhiệm thực hiện mã nguồn cho các hoạt động mà trang web sẽ thực hiện từ phía máy chủ. Các nhiệm vụ bao gồm:
        - **Xác thực người dùng**: Đảm bảo chi tiết tài khoản của người dùng chính xác để họ được phép xem những gì họ muốn xem.
        - **Kiểm soát trình tự**: Đảm bảo các chương trình thực thi trên website được xử lý tốt và không có lỗi.
        - **Tối ưu hóa**: Đảm bảo tính năng của trang web hoạt động hiệu quả và chạy nhanh.
        - **Tự động thông báo**: Sử dụng mã nguồn để thông báo tại chỗ hoặc thông báo các tính năng, dịch vụ sẽ tiết kiệm thời gian và công sức⁵.

2. **Quản trị cơ sở dữ liệu (Database Administrator)**:
    - **Lưu trữ và truy xuất dữ liệu**: Quản trị cơ sở dữ liệu đảm bảo dữ liệu cần thiết cho trang web được lưu trữ và truy xuất một cách hiệu quả. Khi trình duyệt tạo một trang, nó lấy các giá trị cần thiết từ cơ sở dữ liệu, chẳng hạn như số lượng mặt hàng, giá cả, và hiển thị chúng cho người dùng⁵.

3. **Quản trị hệ thống (System Administrator)**:
    - **Bảo vệ hệ thống**: Backend Developer thay đổi các phần của trang web nhìn thấy ở Front End trong trình duyệt bằng các ngôn ngữ như CSS hoặc HTML để kiểm tra. Họ đảm bảo rằng các thay đổi này tồn tại cho đến khi trang được tải lại⁵.