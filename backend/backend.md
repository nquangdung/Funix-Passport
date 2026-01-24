# FUNiX Passport - Tài liệu Backend

## Tổng quan

Tài liệu này mô tả kiến trúc backend, mục đích, vai trò và các tính năng của hệ thống FUNiX Passport. Backend đóng vai trò là máy chủ API trung tâm quản lý dữ liệu bản dịch và cung cấp dịch vụ truy xuất phụ đề/tài liệu cho Chrome Extension.

---

## 1. Mục đích

Backend cung cấp:

- **Quản lý dữ liệu**: Lưu trữ và quản lý các bản dịch tiếng Việt (phụ đề và tài liệu) cho các khóa học MOOC
- **Dịch vụ API**: Các endpoint RESTful để Chrome Extension yêu cầu bản dịch
- **Xác thực**: Xác thực dựa trên Token/API Key cho các thao tác của Translator và Admin
- **Kiểm soát truy cập theo vai trò (RBAC)**: Áp dụng quyền hạn dựa trên vai trò người dùng

---

## 2. Kiến trúc

### 2.1. Công nghệ sử dụng

| Thành phần | Công nghệ |
|------------|-----------|
| Dịch vụ Backend | Firebase Cloud Functions |
| Cơ sở dữ liệu | Firebase Firestore |
| Lưu trữ file | Firebase Storage |
| Endpoint API | `https://funix-subtitle.firebaseapp.com` |

### 2.2. Sơ đồ kiến trúc

```
┌─────────────────────────────────────────────────────────────────┐
│                        CLIENTS                                   │
├─────────────────────┬───────────────────────────────────────────┤
│  Chrome Extension   │           Web Portal                       │
│  (Học viên)         │   (Translator / Admin / Reviewer)          │
└─────────┬───────────┴───────────────────┬───────────────────────┘
          │                               │
          │  GET /get                     │  POST /upload
          │  (course_id, video_id)        │  PUT /update
          │                               │  DELETE /delete
          ▼                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                    TẦNG BACKEND API                              │
│              (Firebase Cloud Functions)                          │
├─────────────────────────────────────────────────────────────────┤
│  • Xác thực & Phân quyền (Token/API Key)                        │
│  • Kiểm tra Request                                              │
│  • Xử lý nghiệp vụ                                               │
│  • Định dạng Response                                            │
└─────────────────────────────────────────────────────────────────┘
          │                               │
          ▼                               ▼
┌─────────────────────┐     ┌─────────────────────────────────────┐
│   Firebase Storage  │     │       Firebase Firestore             │
│   (File phụ đề)     │     │       (Metadata)                     │
│   • File .srt       │     │       • Bản ghi phụ đề               │
│   • File .vtt       │     │       • Bản ghi tài liệu             │
│   • Tài liệu        │     │       • Tài khoản người dùng         │
└─────────────────────┘     └─────────────────────────────────────┘
```

### 2.3. Luồng dữ liệu

1. **Extension → Backend**: Extension trích xuất `course_id` và `video_id` từ trang MOOC, gửi request đến backend
2. **Backend → Database**: Backend truy vấn Firestore để tìm bản ghi bản dịch phù hợp
3. **Backend → Storage**: Nếu tìm thấy, lấy URL file từ Firebase Storage
4. **Backend → Extension**: Trả về metadata + URL file cho Extension để hiển thị

---

## 3. Vai trò người dùng

### 3.1. Tổng quan vai trò

| Vai trò | Mô tả | Quyền hạn Backend |
|---------|-------|-------------------|
| **User** | Người dùng đã xác thực cơ bản | Đăng nhập, Đăng xuất |
| **Translator** | Người đóng góp bản dịch | Upload, Sửa, Xóa bản dịch của mình |
| **Admin** | Quản trị viên hệ thống | Quản lý người dùng, Cấp/Thu hồi quyền |
| **Reviewer** | Kiểm duyệt viên | Duyệt, Phê duyệt/Từ chối bản dịch |
| **Student** | Người dùng Extension | Chỉ đọc các bản dịch đã được phê duyệt |

### 3.2. Ma trận quyền hạn theo vai trò

| Hành động | User | Translator | Reviewer | Admin |
|-----------|:----:|:----------:|:--------:|:-----:|
| Đăng nhập/Đăng xuất | Có | Có | Có | Có |
| Xem Dashboard | - | Có | Có | Có |
| Upload Phụ đề/Tài liệu | - | Có | - | - |
| Sửa bản dịch của mình | - | Có | - | - |
| Xóa bản dịch của mình | - | Có | - | - |
| Xem danh sách chờ duyệt | - | - | Có | Có |
| Phê duyệt/Từ chối bản dịch | - | - | Có | Có |
| Quản lý người dùng | - | - | - | Có |
| Cấp/Thu hồi quyền Translator | - | - | - | Có |

---

## 4. Các API Endpoint

### 4.1. Endpoint công khai (Extension)

#### Lấy phụ đề
```
POST /get
```

**Request Body:**
```json
{
  "cid": "course_id",
  "lid": "video_id"
}
```

**Response (Thành công):**
```json
{
  "code": 200,
  "data": {
    "vi": "https://storage.firebase.com/.../subtitle_vi.srt",
    "en": "https://storage.firebase.com/.../subtitle_en.srt"
  }
}
```

**Response (Không tìm thấy):**
```json
{
  "code": 404,
  "message": "Không tìm thấy bản dịch"
}
```

### 4.2. Endpoint được bảo vệ (Translator/Admin)

Tất cả các endpoint được bảo vệ yêu cầu header `Authorization: Bearer <token>`.

#### Upload phụ đề
```
POST /subtitle/upload
```

**Request Body:**
```json
{
  "name": "Tên video",
  "url": "https://mooc-platform.com/video/123",
  "courseId": "course_id",
  "videoId": "video_id",
  "file": "<file_mã_hóa_base64>"
}
```

#### Upload tài liệu
```
POST /document/upload
```

**Request Body:**
```json
{
  "name": "Tên tài liệu",
  "url": "https://mooc-platform.com/doc/123",
  "file": "<file_mã_hóa_base64>"
}
```

#### Cập nhật Metadata
```
PUT /translation/:id
```

#### Xóa bản dịch
```
DELETE /translation/:id
```

#### Tìm kiếm/Lọc bản dịch
```
GET /translations?name=&url=&translator=&courseId=&videoId=
```

### 4.3. Endpoint Admin

#### Danh sách người dùng
```
GET /admin/users
```

#### Cấp quyền Translator
```
POST /admin/users/:id/grant-translator
```

#### Thu hồi quyền Translator
```
POST /admin/users/:id/revoke-translator
```

#### Xóa người dùng
```
DELETE /admin/users/:id
```

### 4.4. Endpoint Reviewer

#### Danh sách bản dịch chờ duyệt
```
GET /reviews/pending
```

#### Phê duyệt bản dịch
```
POST /reviews/:id/approve
```

#### Từ chối bản dịch
```
POST /reviews/:id/reject
```

**Request Body (Từ chối):**
```json
{
  "comment": "Lý do từ chối"
}
```

---

## 5. Mô hình dữ liệu

### 5.1. Bản ghi phụ đề (Subtitle)

| Trường | Kiểu | Mô tả |
|--------|------|-------|
| `id` | String | ID duy nhất tự động tạo |
| `name` | String | Tên video/khóa học |
| `url` | String | URL video gốc |
| `courseId` | String | Mã định danh khóa học MOOC |
| `videoId` | String | Mã định danh video |
| `viSubtitleUrl` | String | URL file phụ đề tiếng Việt |
| `translator` | String | ID người upload |
| `uploadedDate` | Timestamp | Thời gian upload |
| `reviewer` | String | ID người duyệt |
| `reviewedDate` | Timestamp | Thời gian duyệt |
| `reviewStatus` | Enum | `PENDING`, `APPROVED`, `REJECTED` |
| `reviewComment` | String | Nhận xét (nếu từ chối) |

### 5.2. Bản ghi tài liệu (Document)

| Trường | Kiểu | Mô tả |
|--------|------|-------|
| `id` | String | ID duy nhất tự động tạo |
| `name` | String | Tên tài liệu |
| `url` | String | URL tài liệu gốc |
| `documentUrl` | String | URL file tài liệu đã dịch |
| `translator` | String | ID người upload |
| `uploadedDate` | Timestamp | Thời gian upload |
| `reviewer` | String | ID người duyệt |
| `reviewedDate` | Timestamp | Thời gian duyệt |
| `reviewStatus` | Enum | `PENDING`, `APPROVED`, `REJECTED` |
| `reviewComment` | String | Nhận xét (nếu từ chối) |

### 5.3. Bản ghi người dùng (User)

| Trường | Kiểu | Mô tả |
|--------|------|-------|
| `id` | String | ID duy nhất tự động tạo |
| `email` | String | Email người dùng |
| `displayName` | String | Tên hiển thị |
| `role` | Enum | `USER`, `TRANSLATOR`, `REVIEWER`, `ADMIN` |
| `createdAt` | Timestamp | Thời gian tạo tài khoản |

---

## 6. Các nền tảng MOOC được hỗ trợ

Backend lưu trữ bản dịch cho các nền tảng sau:

| Nền tảng | Định dạng Course ID | Định dạng Video ID |
|----------|---------------------|-------------------|
| Udemy | Dựa trên domain | Lecture ID |
| Coursera | Course slug | Video ID |
| edX | Course ID | Block ID |
| Udacity | Course ID | Lesson/Video ID |
| YouTube | - | Video ID |
| Vimeo | - | Video ID |
| AWS Academy | Course ID | Module ID |
| Applied Digital Skills | - | Lesson ID |
| Google Edu | - | Lesson ID |

---

## 7. Bảo mật

### 7.1. Xác thực
- Firebase Authentication để quản lý người dùng
- JWT token để xác thực API
- Xử lý hết hạn và làm mới token

### 7.2. Phân quyền
- Kiểm soát truy cập theo vai trò (RBAC)
- Kiểm tra quyền ở mức endpoint
- Xác thực quyền sở hữu tài nguyên (translator chỉ có thể sửa bản upload của mình)

### 7.3. Bảo vệ dữ liệu
- HTTPS cho tất cả giao tiếp API
- Firebase Security Rules để kiểm soát truy cập database
- Kiểm tra và làm sạch dữ liệu đầu vào

---

## 8. Yêu cầu hiệu suất

| Chỉ số | Mục tiêu |
|--------|----------|
| Thời gian phản hồi tra cứu phụ đề | <= 1 giây |
| Thao tác Upload/CRUD | <= 0.5 giây |
| Độ khả dụng API | 99.9% uptime |

---

## 9. Tham chiếu mã nguồn

Chrome Extension giao tiếp với backend thông qua các file chính sau:

| File | Mục đích |
|------|----------|
| `script/lib/requestData.js` | Helper gửi request API để lấy phụ đề |
| `script/background/ajax.js` | Background script xử lý AJAX request |
| `script/subtitle/*.js` | Xử lý phụ đề theo từng nền tảng |

### 9.1. Ví dụ gửi API Request

```javascript
// Từ script/lib/requestData.js
class RequestData {
  static async requestSubtitleData(cid, id, parseSubtitle) {
    let request = {
      content: 'POST Request',
      requestUrl: 'https://funix-subtitle.firebaseapp.com/get',
      requestBody: {
        cid: cid,
        lid: id,
      },
    };
    // ... xử lý response và trả về phụ đề đã parse
  }
}
```

---

## 10. Cải tiến trong tương lai

- [ ] Triển khai lớp cache cho các phụ đề truy cập thường xuyên
- [ ] Thêm hỗ trợ cho nhiều nền tảng MOOC hơn
- [ ] Triển khai upload hàng loạt cho translator
- [ ] Thêm dashboard phân tích để theo dõi sử dụng
- [ ] Triển khai webhook thông báo khi trạng thái duyệt thay đổi
