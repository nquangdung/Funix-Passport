# FUNiX Passport Assignment - SWE

**Họ tên:** Lê Vân Phong  
**Mã sinh viên:** FX28249  

---

##  Tên dự án
**SWE Assignment - FUNiX Passport Extension**

---

##  Mục đích của Repo
Repository này được tạo ra nhằm phục vụ **Assignment môn Software Engineering (SWE)** thuộc chương trình FUNiX.  
Mục tiêu chính của repo là quản lý mã nguồn của **Extension FUNiX Passport** — một tiện ích hỗ trợ dịch phụ đề và tài liệu học tập từ các nền tảng MOOC như **Udemy** hoặc **Coursera**.  

Repo bao gồm **nhiều branch** phục vụ cho từng nhiệm vụ hoặc giai đoạn phát triển khác nhau (được mô tả chi tiết bên dưới).

---

## Danh sách các Branch và mô tả chi tiết

### 1. `document`
Branch này được sử dụng để **thêm các tài liệu liên quan đến đặc tả và sơ đồ của dự án**, bao gồm:
- **Diagram** thể hiện kiến trúc hệ thống và luồng dữ liệu.  
- **Tài liệu mô tả yêu cầu (SRS)**, quy trình hoạt động, và phân tích chức năng của hệ thống.

 Mục tiêu: giúp người đọc và nhóm phát triển nắm bắt rõ cấu trúc tổng thể và mục tiêu thiết kế.

---

### 2.  `backend`
Branch này chứa **các yêu cầu và đặc tả chức năng của hệ thống Backend**, bao gồm:
- Quản lý cơ sở dữ liệu các file dịch thuật.
- Mô tả chức năng upload, xem danh sách, tải xuống, chỉnh sửa, xóa file phụ đề và tài liệu.
- Vai trò của người dịch (*Translator*) và quản trị viên (*Admin*).

Mục tiêu: xây dựng nền tảng backend có thể tương tác với Extension để hiển thị bản dịch cho người dùng.

---

### 3.  `bug/clear_console_log`
Branch này được tạo ra nhằm **xóa toàn bộ các lệnh `console.log`** không cần thiết trong file:
 Mục tiêu: tối ưu và làm sạch mã nguồn, tránh hiển thị thông tin debug ra console của trình duyệt khi Extension chạy.

---

### 4.  `feat/auto_enable_subtitle`
Branch này bổ sung **tính năng dịch tự động** cho Extension.  
Cụ thể, khi người dùng truy cập vào video có phụ đề, Extension sẽ:
- Tự động bật tính năng dịch mà không cần phải thao tác thủ công.  
- Tối ưu hóa trải nghiệm người dùng, giảm số bước cần thực hiện khi xem nội dung học tập.

 Mục tiêu: nâng cao tính tiện dụng và tự động hóa của Extension FUNiX Passport.

---

##  Cấu trúc tổng quan của dự án
