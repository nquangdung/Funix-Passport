Backend sẽ thực hiện các thao tác với cơ sở dữ liệu với nhiệm vụ là quản lý về các file dịch thuật. Ngoài ra, Backend phải được thiết kế để các dịch thuật viên có thể upload lên các file phụ đề tương ứng cho từng video trên các trang MOOC hoặc upload các tài liệu đã được dịch. Giúp các dịch thuật viên và quản trị viên có thể quản lý được các dữ liệu về dịch thuật, phụ đề. Đồng thời cũng có cơ sở dữ liệu chứa danh sách các môn, link video, sô lượng truy cập từng video, …

1. Sẽ có 3 vai trò chính như sau:

User: Người dùng bình thường, chỉ có thể đăng nhập và đăng xuất khỏi ứng dụng.

Translator: Các dịch thuật viên, có thể thực hiện các thao tác sau trên ứng dụng:

- Upload file phụ đề đã dịch tiếng Việt:

  - Translator sẽ vào màn hình upload, sau đó cần nhập các thông tin cần thiết như: Tên Video, URL Video, Course ID, Video ID.

  - Sau đó Translator sẽ đính kèm thêm file phụ đề đã được dịch.

  - Nhấn submit và ứng dụng thực hiện công đoạn upload, lưu dữ liệu vào Database.

- Upload file Document đã dịch tiếng Việt:

  - Tương tự với upload phụ đề, nhưng Translator sẽ cần nhập Tên bản dịch và URL của Document.

  - Translator sẽ đính kèm file Document đã dịch.

  * Xem danh sách các file dịch thuật đã được upload: sẽ có hai Dashboard, 01 Dashboard hiển thị các bản dịch phụ đề và Dashboard còn lại sẽ hiển thị bản dịch Document.

- Tải xuống file đã dịch: khi click vào link trên Dashboard thì có thể tải xuống dữ liệu của bản dịch (File phụ đề hoặc file Document).

- Tìm kiếm các bản dịch theo bộ lọc:

  - Translator có thể tìm kiếm các bản dịch theo những bộ lọc tính sau: Tên bản dịch, Url, Người dịch, Course ID, Video ID.

- Xóa các file phụ đề hoặc document:

  - Sau khi tìm kiếm bản dịch, Translator có thể lựa chọn để xóa bản dịch đó đi.

- Chỉnh sửa thông tin:

  - Sau khi tìm kiếm bản dịch, Translator có thể lựa chọn để chỉnh sửa lại thông tin của bản dịch đó. Sẽ có 2 loại chỉnh sửa như sau: Chỉnh sửa các metadata của file dịch và Reup file dịch khác lên thay thế.

Reviewer: Các reviewer sẽ xem các bản dịch của Translator và quyết định sẽ đăng bản dịch nào lên cho User xem.

Admin: Các quản trị viên, nhiệm vụ chính là quản lý tài khoản người dùng. Admin có thể thực hiện các thao tác như sau:

- Xóa tài khoản một người dùng.

- Thêm quyền cho một người dùng (chuyển User thành Translator).

- Xóa quyền cho một người dùng (chuyển Translator cho User).

2. Ngoài ra, Backend cũng sẽ có một Database và bạn sẽ cần lưu trữ các Metadata sau cho mỗi bản dịch thuật (Phụ đề hoặc Document). Các Metadata này sẽ gồm cả dữ liệu mà Translator nhập vào lẫn các dữ liệu do Backend tự tạo.

Với bản dịch dành cho Video, Database sẽ lưu các dữ liệu như sau:

    + ID (tự động tạo): ID của bản dịch
    + Translator (tự động tạo): Tên của dịch thuật viên đã upload
    + UploadedDate (tự động tạo): Thời gian mà bản dịch này được upload
    + Name: Tên của bản dịch
    + URL: Link website (có thể là link website tài liệu hoặc là link video)
    + Video ID: Id của video đó
    + Course ID: Nguồn video
    + VI Subtitle URL: Đường dẫn đến file phụ đề tiếng Việt
    + En Subtitle URL (Optional): Đường dẫn đến file phụ đề tiếng Anh

Ngược lại, nếu như đó là bản dịch cho Document thì sẽ có các trường như sau

    + ID (tự động tạo): ID của bản dịch
    + Translator (tự động tạo): Tên của dịch thuật viên đã upload.
    + UploadedDate (tự động tạo): Thời gian mà bản dịch này được upload.
    + Name: Tên của bản dịch.
    + URL: Link website (có thể là link website tài liệu hoặc là link video).
    + Document URL: Đường dẫn đến file Document đã được dịch.
