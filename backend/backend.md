# FUNiX Passport — Backend

## 1. Vai trò và mục đích xây dựng

Backend của FUNiX Passport là tầng máy chủ chịu trách nhiệm quản lý
**bản dịch tiếng Việt cho phụ đề và tài liệu** của các khoá học MOOC
(Udemy, Coursera, Udacity, Sololearn, …) mà học viên FUNiX đang theo
học. Trong khi Chrome Extension chỉ là phần "tiêu thụ" — lấy bản dịch
về và chèn vào trang video — toàn bộ vòng đời nội dung (tạo, kiểm
duyệt, cập nhật, công bố, lưu trữ) đều xảy ra trên Backend.

Mục đích xây dựng Backend, theo thứ tự ưu tiên:

1. **Là nguồn sự thật duy nhất (single source of truth)** cho bản dịch
   phụ đề / tài liệu, để mọi học viên dùng cùng một phiên bản và mọi
   cập nhật được phản ánh ngay lập tức trên Extension.
2. **Tách quyền theo vai trò:** không phải ai cũng được upload, sửa,
   duyệt hoặc xoá bản dịch — luồng kiểm duyệt phải có nhiều cấp.
3. **Cung cấp API công khai cho Extension** (`/get`, `/list`,
   `/translation/{id}`) với độ trễ thấp, cache friendly, không yêu cầu
   học viên đăng nhập.
4. **Cung cấp giao diện quản trị nội bộ** cho đội dịch và đội điều
   phối, kèm log thao tác để truy vết.
5. **Lưu trữ metadata phụ trợ** (tác giả bản dịch, lịch sử chỉnh sửa,
   trạng thái duyệt, đánh giá chất lượng) phục vụ chấm công và báo
   cáo chất lượng.

## 2. Các vai trò sử dụng Backend

Các vai trò dưới đây thừa kế theo thiết kế đã trình bày trong Class
Diagram của Assignment 01 (xem `documentation/diagram/class-diagram.png`).

| Vai trò | Mô tả ngắn | Quan hệ thừa kế |
|----|----|----|
| **Student** (External actor) | Người dùng cuối, học viên FUNiX. Chỉ tương tác với Backend gián tiếp qua Chrome Extension. | — |
| **User** | Người có tài khoản trên hệ thống quản trị. Lớp cơ sở của các vai trò nội bộ. | — |
| **Translator** | Người dịch nội dung, là người tạo bản dịch mới hoặc cập nhật bản dịch hiện có. | `Translator → User` |
| **Reviewer** *(bổ sung từ A1 — Nâng cao)* | Người duyệt bản dịch trước khi công bố. | `Reviewer → User` |
| **Admin** | Người điều phối hệ thống. Có toàn quyền trên Translator/Reviewer/User và metadata. | `Admin → Reviewer → Translator → User` |

## 3. Quyền và thao tác theo từng vai trò

### 3.1 Student (qua Extension)

| Endpoint / thao tác | Mô tả |
|----|----|
| `POST /get` *(public)* | Trả về metadata và URL bản dịch theo `{cid, lid}` (course id + lesson id) — Extension dùng để hiển thị phụ đề trên trang video. |
| `GET /translation/{id}.vtt` *(public)* | Trả về file phụ đề định dạng WebVTT đã được duyệt (chỉ phục vụ bản dịch có trạng thái `approved`). |
| `GET /document/{id}` *(public)* | Trả về bản dịch tài liệu kèm theo (nếu có). |

Học viên **không cần đăng nhập** vào Backend, **không có** quyền tạo,
sửa, xoá, hoặc nhìn thấy bản dịch ở trạng thái `pending` /
`rejected`.

### 3.2 Translator

Đăng nhập bằng tài khoản User. Phạm vi truy cập giới hạn ở các bản
dịch do chính mình tạo hoặc được Admin phân công.

| Quyền | Mô tả |
|----|----|
| Tạo bản dịch mới | Upload phụ đề (.vtt / .srt) hoặc tài liệu (.docx / .md), nhập metadata bắt buộc (course, lesson, ngôn ngữ nguồn, ngôn ngữ đích). |
| Cập nhật bản dịch của mình | Reup file mới, sửa metadata khi bản dịch ở trạng thái `pending` hoặc `rejected`. |
| Xem trạng thái và phản hồi của Reviewer | Đọc `reviewNote` đính kèm bản dịch để biết lý do bị từ chối. |
| Gửi yêu cầu duyệt lại | Sau khi sửa, chuyển bản dịch về trạng thái `pending` để Reviewer xem xét lại. |

Translator **không được**: duyệt/từ chối bản dịch, xoá bản dịch của
người khác, đụng vào tài khoản người dùng khác.

### 3.3 Reviewer *(vai trò bổ sung từ A1 — Nâng cao)*

Reviewer là cầu nối giữa Translator và bản dịch công bố. Reviewer kế
thừa toàn bộ quyền của Translator (bản thân cũng có thể dịch), và bổ
sung quyền kiểm duyệt:

| Quyền | Mô tả |
|----|----|
| Duyệt bản dịch | Chuyển trạng thái bản dịch từ `pending` → `approved`. Bản `approved` mới được Extension trả về. |
| Từ chối bản dịch | Chuyển trạng thái sang `rejected`, kèm `reviewNote` mô tả lý do để Translator chỉnh sửa. |
| Xem mọi bản dịch ở mọi trạng thái | Truy cập toàn bộ pipeline (pending / approved / rejected) để chọn việc duyệt. |
| Re-open bản dịch đã `approved` | Khi phát hiện sai sót sau công bố, đưa về `pending` để Translator sửa lại. |

Reviewer **không được**: xoá vĩnh viễn bản dịch, sửa lịch sử kiểm duyệt
của Reviewer khác, quản lý vai trò người dùng.

### 3.4 Admin

Admin có toàn quyền hệ thống. Trong mô hình kế thừa
`Admin → Reviewer → Translator → User`, Admin nhận mọi quyền của các
vai trò bên dưới, cộng thêm:

| Quyền | Mô tả |
|----|----|
| Quản lý người dùng | Tạo / khoá / mở khoá tài khoản User; cấp / thu hồi vai trò Translator hoặc Reviewer. |
| Xoá bản dịch vĩnh viễn | Hard delete khỏi cơ sở dữ liệu (dùng khi có yêu cầu pháp lý / vi phạm bản quyền). |
| Quản lý danh sách khoá học | CRUD trên catalog course / lesson / ngôn ngữ hỗ trợ. |
| Cấu hình hệ thống | Quản lý audio engine, kích thước cache, rate-limit cho endpoint public, key API ngoài. |
| Xem log thao tác | Audit log mọi hành động của Translator / Reviewer / Admin khác. |
| Phân công công việc | Gán Translator / Reviewer cụ thể cho từng lesson hoặc course. |

## 4. Ràng buộc kiểm duyệt và an toàn

- Bản dịch chỉ được Extension trả về khi ở trạng thái `approved`.
- Mỗi lần chuyển trạng thái đều ghi log: `{userId, fromStatus, toStatus, timestamp, reviewNote}`.
- Translator không thể tự duyệt bản dịch của chính mình (kể cả khi
  cùng tài khoản có thêm vai trò Reviewer cho bản dịch khác).
- Mọi endpoint quản trị bắt buộc xác thực bằng token; endpoint public
  cho Extension chỉ dùng phương thức `POST /get` với rate-limit theo IP.

## 5. Liên kết tham chiếu

- Use Case Diagram tổng quát: `documentation/diagram/use-case-overall.png`
- Class Diagram chi tiết các lớp Role / Translation / DAO: `documentation/diagram/class-diagram.png`
- Sequence Diagram cho luồng Extension lấy bản dịch: `documentation/diagram/sequence-diagram.png`
- Activity Diagram cho luồng học viên bật / tắt Extension: `documentation/diagram/activity-diagram.png`
- Tài liệu SRS đầy đủ: `documentation/Document.MD` (hoặc bản `.docx` gốc trong cùng thư mục)
