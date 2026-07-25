# Tài liệu Backend – FUNiX Passport

## 1. Giới thiệu

Backend của hệ thống **FUNiX Passport** chịu trách nhiệm xử lý dữ liệu, xác thực người dùng, quản lý tài khoản và cung cấp dữ liệu cho Extension hoặc giao diện quản trị.

Backend đóng vai trò là cầu nối giữa người dùng, Extension, cơ sở dữ liệu và các tài nguyên như phụ đề hoặc tài liệu học tập.

---

## 2. Các vai trò trong hệ thống

### 2.1. User

User là người dùng thông thường của hệ thống.

Các chức năng:

- Đăng nhập.
- Đăng xuất.
- Xem nội dung được hệ thống cung cấp.
- Sử dụng Extension để lấy phụ đề hoặc tài liệu tương ứng với khóa học.

### 2.2. Translator

Translator là người có quyền tải lên và quản lý phụ đề hoặc tài liệu.

Các chức năng:

- Đăng nhập và đăng xuất.
- Tải phụ đề lên hệ thống.
- Tải tài liệu lên hệ thống.
- Xem danh sách nội dung đã tải lên.
- Tìm kiếm nội dung.
- Tải nội dung xuống.
- Xóa nội dung.
- Chỉnh sửa thông tin (metadata).
- Tải lại tệp khi cần cập nhật.

### 2.3. Admin

Admin là người quản trị hệ thống.

Các chức năng:

- Quản lý tài khoản người dùng.
- Tạo hoặc khóa tài khoản.
- Cấp quyền Translator.
- Thu hồi quyền Translator.
- Kiểm tra và quản lý dữ liệu trong hệ thống.

---

## 3. Quản lý phụ đề

Mỗi bản ghi phụ đề bao gồm các thông tin sau:

| Thuộc tính | Mô tả |
|------------|------|
| ID | Mã định danh của phụ đề |
| Translator | Người tải phụ đề lên |
| UploadedDate | Ngày tải lên |
| Name | Tên phụ đề |
| URL | Đường dẫn liên quan |
| VideoID | Mã video |
| CourseID | Mã khóa học |
| VI URL | Đường dẫn phụ đề tiếng Việt |
| EN URL | Đường dẫn phụ đề tiếng Anh |

Backend sử dụng `CourseID` và `VideoID` để xác định phụ đề tương ứng với video mà người dùng đang xem.

---

## 4. Quản lý tài liệu

Mỗi bản ghi tài liệu bao gồm:

| Thuộc tính | Mô tả |
|------------|------|
| ID | Mã định danh tài liệu |
| Translator | Người tải tài liệu lên |
| UploadedDate | Ngày tải lên |
| Name | Tên tài liệu |
| URL | Đường dẫn trang học |
| Document URL | Đường dẫn tệp tài liệu |

Backend sử dụng URL hoặc thông tin khóa học để tìm tài liệu phù hợp và trả kết quả cho Extension.

---

## 5. Luồng xử lý phụ đề

1. Người dùng mở video khóa học.
2. Extension lấy URL của trang hiện tại.
3. Extension phân tích URL để lấy `CourseID` và `VideoID`.
4. Extension gửi yêu cầu đến Backend.
5. Backend tìm phụ đề tương ứng trong cơ sở dữ liệu.
6. Backend trả về đường dẫn phụ đề.
7. Extension tự động hiển thị phụ đề cho người dùng.

---

## 6. Luồng xử lý tài liệu

1. Người dùng mở trang tài liệu.
2. Extension lấy URL của trang hiện tại.
3. Extension gửi yêu cầu đến Backend.
4. Backend tìm tài liệu phù hợp.
5. Backend trả về đường dẫn tải tài liệu.
6. Extension hiển thị thông tin trong cửa sổ Popup.

---

## 7. Các API dự kiến

### 7.1. Xác thực

```text
POST /api/auth/login
POST /api/auth/logout
```

### 7.2. Quản lý phụ đề

```text
GET    /api/subtitles
GET    /api/subtitles/:id
POST   /api/subtitles
PUT    /api/subtitles/:id
DELETE /api/subtitles/:id
```

### 7.3. Tìm phụ đề theo video

```text
GET /api/subtitles/search?courseId={courseId}&videoId={videoId}
```

### 7.4. Quản lý tài liệu

```text
GET    /api/documents
GET    /api/documents/:id
POST   /api/documents
PUT    /api/documents/:id
DELETE /api/documents/:id
```

### 7.5. Quản lý người dùng

```text
GET    /api/users
POST   /api/users
PUT    /api/users/:id
DELETE /api/users/:id
```

### 7.6. Quản lý quyền Translator

```text
PUT /api/users/:id/grant-translator
PUT /api/users/:id/revoke-translator
```

---

## 8. Yêu cầu bảo mật

- Mật khẩu người dùng phải được mã hóa trước khi lưu vào cơ sở dữ liệu.
- Chỉ người dùng đã xác thực mới được phép sử dụng các API yêu cầu đăng nhập.
- Token đăng nhập phải có thời gian hết hạn.
- Chỉ Admin mới được phép quản lý tài khoản và phân quyền Translator.
- Chỉ Translator hoặc Admin mới được thêm, sửa hoặc xóa phụ đề và tài liệu.
- Dữ liệu đầu vào phải được kiểm tra trước khi xử lý để tránh lỗi hoặc tấn công từ bên ngoài.

---

## 9. Yêu cầu hiệu năng

- Thời gian phản hồi khi tìm kiếm phụ đề hoặc tài liệu không quá **1 giây**.
- Các thao tác quản lý của Translator nên hoàn thành trong thời gian khoảng **0,5 giây** khi hệ thống hoạt động bình thường.
- Các trường như `CourseID`, `VideoID` và `URL` nên được đánh chỉ mục (Index) để tăng tốc độ tìm kiếm.

---

## 10. Cơ sở dữ liệu dự kiến

Hệ thống có thể sử dụng các bảng dữ liệu sau:

```text
users
subtitles
documents
```

Quan hệ giữa các bảng:

- Một Translator có thể tải lên nhiều phụ đề.
- Một Translator có thể tải lên nhiều tài liệu.
- Một khóa học có nhiều video.
- Mỗi video có thể có nhiều phụ đề với các ngôn ngữ khác nhau.

---

## 11. Kết luận

Backend của hệ thống FUNiX Passport chịu trách nhiệm quản lý người dùng, phân quyền, lưu trữ phụ đề, lưu trữ tài liệu và cung cấp dữ liệu cho Extension.

Việc phân chia quyền giữa **User**, **Translator** và **Admin** giúp hệ thống đảm bảo tính bảo mật, dễ quản lý và thuận tiện trong quá trình vận hành.