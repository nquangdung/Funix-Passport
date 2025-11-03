# 🧩 Backend

## 🔹 Chức năng chính
- Có khả năng thao tác với **cơ sở dữ liệu**, với nhiệm vụ quản lý các **file dịch thuật**.
- **Dịch thuật viên (Translator)** có thể **upload** các file phụ đề tương ứng cho từng video trên các trang **MOOC**.
- Hệ thống có cơ sở dữ liệu chứa:
  - Danh sách các môn học
  - Link video
  - Số lượng truy cập từng video
- Giúp **Translator** và **Admin** có thể **quản lý dữ liệu dịch thuật** (phụ đề và tài liệu).

---

## 📤 Upload file phụ đề đã dịch (Translator)

1. Translator vào màn hình **Upload**.  
2. Nhập các thông tin cần thiết:
   - Tên Video  
   - URL Video  
   - Course ID  
   - Video ID  
3. Đính kèm file phụ đề đã dịch.  
4. Nhấn **Submit** → Hệ thống thực hiện **upload** và lưu dữ liệu vào **Database**.

---

## 📄 Upload file Document đã dịch (Translator)

Tương tự với upload phụ đề, nhưng Translator sẽ:
- Nhập **Tên bản dịch** và **URL của Document**.  
- Đính kèm file Document đã dịch.  
- Nhấn **Submit** để lưu vào Database.

---

## 📋 Xem danh sách các file dịch thuật đã được upload (Translator)

- Có **2 Dashboard**:
  1. Dashboard hiển thị **bản dịch phụ đề**.
  2. Dashboard hiển thị **bản dịch Document**.

---

## 📥 Tải xuống file đã dịch (Translator)

- Khi **click vào link** trên Dashboard, người dùng có thể tải xuống dữ liệu bản dịch (File phụ đề hoặc Document).

---

## 🔎 Tìm kiếm bản dịch theo bộ lọc (Translator)

Translator có thể tìm kiếm theo các tiêu chí sau:
- Tên bản dịch  
- URL  
- Người dịch  
- Course ID  
- Video ID

---

## 🗑️ Xóa file phụ đề hoặc Document (Translator)

- Sau khi tìm kiếm bản dịch, Translator có thể **xóa bản dịch** không còn cần thiết.

---

## ✏️ Chỉnh sửa thông tin bản dịch (Translator)

Sau khi tìm kiếm bản dịch, Translator có thể **chỉnh sửa** thông tin:
1. **Chỉnh sửa metadata** của file dịch.
2. **Re-upload (reup)** file dịch khác lên thay thế.

---

# 🛠️ Admin

## 👤 Quản lý người dùng
- **Xóa tài khoản** người dùng.
- **Thêm quyền** cho người dùng (chuyển **User → Translator**).
- **Xóa quyền** của người dùng (chuyển **Translator → User**).

---

# 🧩 Extension (Tiện ích mở rộng)

## 🔹 Mục đích
Tiện ích mở rộng có chức năng **giao tiếp với Backend** để:
- Lấy dữ liệu các bản dịch.
- Hiển thị bản dịch cho **sinh viên sử dụng**.

---

## ⚙️ Cơ chế hoạt động

1. Khi người dùng **truy cập trang web**, Extension sẽ:
   - Trích xuất **URL** của trang.
   - Lấy ra thông tin như `video_id`, `course_id`.

2. Extension gửi **request** lên Backend với dữ liệu tương ứng:
   - Nếu là trang MOOC → gửi `course_id` và `video_id` để tìm phụ đề.
   - Nếu là trang Document → gửi toàn bộ **URL** để tìm bản dịch Document.

3. **Backend** trả về bản dịch (nếu có).  
4. **Extension** hiển thị **popup** cho người dùng lựa chọn xem bản dịch.

---

# ✅ Duyệt bản dịch (Reviewer)

- Sau khi Translator đăng bản dịch lên, **Reviewers** có thể:
  - Xem lại bản dịch.
  - **Thông qua (approve)** sản phẩm dịch thuật trước khi công bố.

---
