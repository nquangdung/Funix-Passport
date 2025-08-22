# FUNiX Passport
- Tên dự án: Hệ thống quản lý và phân phối bản dịch FUNiX Passport
- Mã sinh viên: HUYNVFX61609

## Mục đích repo
Repo này dùng để phát triển extension xem bản dịch và backend quản lý cho dự án FUNiX Passport, phục vụ môn học SWE102.

## Các branch chính

### master
- Branch chính chứa code ổn định
- Lịch sử commit đã được rollback về bản ổn định

### bug/clear_console_log 
- Đã xóa toàn bộ console.log trong file udemy-subtitle.js
- Đảm bảo không ảnh hưởng UI/UX người dùng

### feat/auto_enable_subtitle
- Sửa hàm pageLoad() để tự động hiển thị phụ đề
- Cập nhật logic: 
  ```javascript
  function pageLoad(code) {
    startObserver();
    if (code === 200) {
      start(1, false);
    }
  }
  ```

### document
- Thêm thư mục documentation/ chứa:
  - Các sơ đồ hệ thống (Usecase, Class, Activity, Sequence)
  - File tài liệu Document.MD (chuyển đổi từ .docx)
  - Ảnh minh họa trong documentation/diagram

### backend
- Thêm tài liệu đặc tả backend:
  - Vai trò và mục đích của backend
  - Danh sách chức năng theo từng vai trò (Student, Translator, Admin)
  - Cấu trúc API và database