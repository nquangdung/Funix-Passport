# FUNiX Passport — Assignment 02 SWE

> Repo này là sản phẩm nộp cho **Assignment 02 — Quản lý mã nguồn phần
> mềm FUNiX Passport** của môn **SWE102x — Nhập môn kỹ thuật phần
> mềm** trên FUNiX. Fork từ
> [`anhndfx00424/funix-passport-assignment-swe`](https://gitlab.com/anhndfx00424/funix-passport-assignment-swe).

## Thông tin sinh viên

| | |
|----|----|
| **Họ tên** | Nguyễn Nam Anh |
| **Mã sinh viên** | anhnnfx06447 |
| **Email** | anhnnfx06447@funix.edu.vn |
| **Môn học** | SWE102x_03-A_VN — Nhập môn kỹ thuật phần mềm |
| **Assignment** | 02 — Quản lý mã nguồn phần mềm FUNiX Passport |

## Mục đích của repo

Repo phục vụ hai mục đích, tương ứng với hai loại bài tập:

1. **Thực hành Git/GitLab:** revert commit, branch theo loại thay đổi
   (`bug/…`, `feat/…`), push lên remote, merge nhiều nhánh vào master,
   xử lý conflict, tạo Merge Request.
2. **Nâng cấp FUNiX Passport:** sửa lỗi extension hiển thị phụ đề trên
   Udemy, dọn các log debug khỏi production, và thay đổi UX để phụ đề
   tự hiển thị thay vì hỏi người dùng.

## Danh sách nhánh và nội dung thay đổi

| # | Branch | Mục đích | Thay đổi chính |
|----|----|----|----|
| 1 | `master` | Nhánh chính, đã rollback bug và là điểm hợp nhất các nhánh khác | Revert commit `9b1904d Fix Udemy bug` về trạng thái `e605880 Format file` để Extension khởi tạo lại `$(document).ready` và hiển thị popup phụ đề trên Udemy. |
| 2 | `bug/clear_console_log` | Sửa lỗi mỹ thuật — xoá `console.log` debug khỏi production | Xoá toàn bộ 9 dòng `console.log("N-udemy-subtitle")` trong `script/subtitle/udemy-subtitle.js`. |
| 3 | `feat/auto_enable_subtitle` | Cải tiến UX — tự bật phụ đề thay vì hỏi | Sửa hàm `pageLoad()` trong `script/subtitle/udemy-subtitle.js`: bỏ `Notifycation.confirmSubtitle`, tự gọi `start(mode, res.float)` với `mode=1` (tiếng Việt) nếu `arraySubType` có hỗ trợ. |
| 4 | `document` | Đặt tài liệu thiết kế vào repo | Thêm `documentation/` chứa file `.docx` của SRS (Assignment 01), bản Markdown `Document.MD` để GitLab render, và thư mục `diagram/` chứa 4 sơ đồ UML (Use Case, Class, Activity, Sequence). |
| 5 | `backend` | Mô tả vai trò và quyền của Backend | Thêm `backend/backend.md` mô tả mục đích Backend, các vai trò sử dụng (Student qua Extension; User / Translator / Reviewer / Admin) và quyền hạn từng vai trò. |
| 6 | `master` (hiện tại) | README + merge tất cả | File README này, sau đó merge `bug/clear_console_log`, `feat/auto_enable_subtitle`, `document`, `backend` vào master. |

## Cách kiểm thử trên Chrome

```bash
# 1. Clone repo về máy
git clone https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe.git
cd anhnnfx06447-assignment-02-swe

# 2. Chrome → chrome://extensions
#    Bật "Developer mode" ở góc phải trên
#    Nhấn "Load unpacked" → chọn thư mục repo vừa clone
```

Sau khi load, mở một bài học bất kỳ trên Udemy (đã có bản dịch FUNiX):
phụ đề tiếng Việt sẽ tự hiển thị (sau khi đã merge `feat/auto_enable_subtitle`).

## Cấu trúc thư mục

```
.
├── README.md                              ← (file này)
├── manifest.json                          ← Chrome Extension manifest v2
├── icon/                                  ← Icon Extension
├── popup/                                 ← Popup khi click vào icon
├── page/                                  ← Trang Admin / Manual / Changelog
├── style/                                 ← Stylesheet
├── script/                                ← Logic chính của Extension
│   └── subtitle/
│       └── udemy-subtitle.js              ← Trọng tâm sửa của Y/c 01, 02, 03
├── documentation/                         ← (branch document) Tài liệu thiết kế
│   ├── Document.MD                          (SRS dạng Markdown)
│   ├── SWE102x-Assignment01-ThietKeFUNiXPassport.docx
│   └── diagram/                             (Use Case / Class / Activity / Sequence)
└── backend/                               ← (branch backend) Mô tả Backend
    └── backend.md
```

## Liên kết

- **Forked Repo (repo cá nhân):** https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe
- **Original Repo (do FUNiX cung cấp):** https://gitlab.com/anhndfx00424/funix-passport-assignment-swe
- **Branches:**
  - master — https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe/-/tree/master
  - bug/clear_console_log — https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe/-/tree/bug/clear_console_log
  - feat/auto_enable_subtitle — https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe/-/tree/feat/auto_enable_subtitle
  - document — https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe/-/tree/document
  - backend — https://gitlab.com/anhnnfx06447/anhnnfx06447-assignment-02-swe/-/tree/backend
