1.  **Vai trò của BackEnd**

Backend trong dự án này đóng vai trò là bộ não và kho lưu trữ trung tâm
của toàn bộ hệ thống.

2.  **Mục đích xây dựng Backend**

-   **Quản lý tập trung toàn bộ dữ liệu dịch thuật:** Lưu trữ một cách
    có hệ thống các file phụ đề, file tài liệu đã dịch cùng với các
    thông tin liên quan (metadata).

-   **Cung cấp một giao diện làm việc cho Dịch thuật viên
    (Translator):** Tạo ra một môi trường để các dịch thuật viên có thể
    tải lên và quản lý các sản phẩm dịch thuật của mình.

-   **Đảm bảo chất lượng bản dịch:** Thông qua một quy trình kiểm duyệt
    (review), đảm bảo các bản dịch chính xác và chất lượng trước khi đến
    tay sinh viên.

-   **Quản lý người dùng và phân quyền:** Cho phép Quản trị viên (Admin)
    kiểm soát ai có thể truy cập và thực hiện các chức năng trong hệ
    thống.

-   **Cung cấp dữ liệu cho Extension:** Hoạt động như một API (Giao diện
    lập trình ứng dụng) để phía Extension có thể gửi yêu cầu và nhận về
    các bản dịch đã được phê duyệt, sau đó hiển thị cho sinh viên.

-   **Đảm bảo tính bảo mật và toàn vẹn dữ liệu:** Kiểm soát quyền truy
    cập thông qua token/API key, đảm bảo chỉ những người có thẩm quyền
    mới có thể thay đổi dữ liệu.

**3. Các vai trò sử dụng Backend và chức năng tương ứng**

Có 4 vai trò sẽ tương tác với Backend, mỗi vai trò có các chức năng
riêng biệt được định nghĩa rõ ràng:

**3.1 User (Người dùng bình thường)**

Người dùng thông thường chỉ có các quyền cơ bản nhất liên quan đến xác
thực tài khoản. Họ không có quyền truy cập vào các chức năng quản lý dữ
liệu.

-   **Đăng nhập:** Xác thực danh tính để vào hệ thống.

-   **Đăng xuất:** Kết thúc phiên làm việc.

**3.2 Translator (Dịch thuật viên)**

Đây là vai trò tạo ra nội dung cho hệ thống. Họ có quyền quản lý các bản
dịch mà mình tải lên.

-   **Upload phụ đề video:** Tải lên file phụ đề (.srt, .vtt, \...) kèm
    theo các thông tin như Tên video, URL, Course ID, và Video ID.

-   **Upload tài liệu dịch:** Tải lên file tài liệu (văn bản, pdf,\...)
    kèm Tên bản dịch và URL của tài liệu gốc.

-   **Xem danh sách và trạng thái bản dịch:** Truy cập Dashboard để xem
    danh sách các bản dịch đã upload và trạng thái của chúng (Chờ duyệt,
    Đã duyệt, Bị từ chối).

-   **Tải xuống bản dịch:** Tải về các file phụ đề hoặc tài liệu từ hệ
    thống.

-   **Tìm kiếm và lọc bản dịch:** Tìm kiếm các bản dịch dựa trên các
    tiêu chí như Tên, URL, Người dịch, Course ID, Video ID.

-   **Xóa bản dịch:** Xóa một file phụ đề hoặc tài liệu đã upload.

-   **Chỉnh sửa bản dịch:**

```{=html}
<!-- -->
```
-   Chỉnh sửa thông tin (metadata) của bản dịch.

-   Tải lại (Re-upload) một file dịch mới để thay thế file cũ (đặc biệt
    > khi bản dịch bị từ chối).

Sau khi upload, bản dịch sẽ ở trạng thái \"Chờ duyệt\" và cần được
Reviewer phê duyệt trước khi hiển thị cho người dùng cuối.

**3.3 Reviewer (Người duyệt)**

Vai trò này chịu trách nhiệm kiểm duyệt và đảm bảo chất lượng cho các
bản dịch.

-   **Xem danh sách bản dịch chờ duyệt:** Truy cập một Dashboard riêng
    để thấy các bản dịch đang cần được xem xét.

-   **Phê duyệt (Approve) bản dịch:** Nếu bản dịch đạt chất lượng,
    Reviewer sẽ phê duyệt để bản dịch được hiển thị cho User.

-   **Từ chối (Reject) bản dịch:** Nếu bản dịch có lỗi, Reviewer sẽ từ
    chối và có thể để lại ghi chú cho Translator sửa lại.

**3.4 Admin (Quản trị viên)**

Vai trò của Admin tập trung vào việc quản lý tài khoản người dùng và các
quyền hạn trong hệ thống.

-   **Xóa tài khoản người dùng:** Xóa một tài khoản bất kỳ (User,
    Translator, Reviewer) khỏi hệ thống.

-   **Cấp quyền Translator:** Nâng cấp một tài khoản từ vai trò User lên
    thành Translator.

-   **Hủy quyền Translator:** Giáng cấp một tài khoản từ vai trò
    Translator xuống thành User.

-   **Cấp quyền Reviewer:** Nâng cấp một tài khoản người dùng để trở
    thành Reviewer.

-   **Hủy quyền Reviewer:** Hủy bỏ vai trò Reviewer của một tài khoản.
