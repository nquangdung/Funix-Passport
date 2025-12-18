![](media/image1.png)

Tài liệu đặc tả yêu cầu

> **_FUNiX Passport_**

Revision History

---

**Date** **Version** **Description** **Author**

\<03/12/25\> \<1.0\> SRS 1.0 DucNVFX14814

---

Bảng thuật ngữ

Cung cấp tổng quan về bất kỳ định nghĩa nào mà người đọc nên hiểu trước
khi đọc tiếp.

---

Cấu hình Nó có nghĩa là một sản phẩm có sẵn / Được chọn từ một danh
mục có thể được tùy chỉnh.

FAQ Frequently Asked Questions

CRM Customer Relationship Management

RAID 5 Redundant Array of Inexpensive Disk/Drives

---

Table of Contents

[1. Giới thiệu tổng quan về dự án
[4](#giới-thiệu-tổng-quan-về-dự-án)](#giới-thiệu-tổng-quan-về-dự-án)

[1.1 Tóm tắt dự án [4](#tóm-tắt-dự-án)](#tóm-tắt-dự-án)

[1.2 Phạm vi của dự án [4](#phạm-vi-của-dự-án)](#phạm-vi-của-dự-án)

[2. Yêu cầu và đặc tả dự án
[5](#yêu-cầu-và-đặc-tả-dự-án)](#yêu-cầu-và-đặc-tả-dự-án)

[2.1 Yêu cầu chức năng [5](#yêu-cầu-chức-năng)](#yêu-cầu-chức-năng)

[2.2 Yêu cầu phi chức năng
[6](#yêu-cầu-phi-chức-năng)](#yêu-cầu-phi-chức-năng)

[2.2.1. Tính bảo mật [6](#tính-bảo-mật)](#tính-bảo-mật)

[2.2.2. Tính sẵn sàng và khả năng đáp ứng
[6](#tính-sẵn-sàng-và-khả-năng-đáp-ứng)](#tính-sẵn-sàng-và-khả-năng-đáp-ứng)

[2.2.3. Hiệu suất [6](#hiệu-suất)](#hiệu-suất)

[2.2.4. Giao diện người dùng
[6](#giao-diện-người-dùng)](#giao-diện-người-dùng)

[2.3 Đặc tả phần mềm [6](#đặc-tả-phần-mềm)](#đặc-tả-phần-mềm)

[3. Kiến trúc và thiết kế phần mềm
[7](#kiến-trúc-và-thiết-kế-phần-mềm)](#kiến-trúc-và-thiết-kế-phần-mềm)

[3.1 Kiến trúc phần mềm [7](#kiến-trúc-phần-mềm)](#kiến-trúc-phần-mềm)

[3.2 Usecase [8](#usecase)](#usecase)

[3.2.1 Usecase của User [9](#usecase-của-user)](#usecase-của-user)

[3.2.2 Usecase của Translator
[11](#usecase-của-translator)](#usecase-của-translator)

[3.2.3 Usecase của Admin [14](#usecase-của-admin)](#usecase-của-admin)

[3.2.4 Usecase của Reviewer
[15](#usecase-của-reviewer)](#usecase-của-reviewer)

[3.3 Sơ đồ use case tổng quát của hệ thống
[16](#sơ-đồ-use-case-tổng-quát-của-hệ-thống)](#sơ-đồ-use-case-tổng-quát-của-hệ-thống)

[3.4 Class Diagram [17](#class-diagram)](#class-diagram)

[3.5 Sequence Diagram [18](#sequence-diagram)](#sequence-diagram)

[3.6 Activity Diagram [19](#activity-diagram)](#activity-diagram)

Tài liệu đặc tả

1.  # Giới thiệu tổng quan về dự án

    1.  ## Tóm tắt dự án

```{=html}
<!-- -->
```

1.  Hệ thống xây dựng: hệ thống quản lý và hiển thị bản dịch phụ đề và
    tài liệu tiếng Việt cho các video học tập và tài liệu trên nền tảng
    MOOC của FUNiX

2.  Mục đích: hỗ trợ sinh viên tiếp cận kiến thức dễ dàng hơn bằng tiếng
    Việt thay vì phải xem phụ đề tiếng Anh

3.  Bài toán giải quyết:

- Cung cấp bản dịch trực tiếp qua Extension trên trình duyệt Chrome

- Quản lý hiệu quả các bản dịch phụ đề và tài liệu

4.  Mục tiêu:

- Xây dựng backend quản lý dữ liệu dịch thuật và người dùng

- Phát triển Extension Chrome giao tiếp với backend để hiển thị bản
  dịch

- Đảm bảo bảo mật, hiệu năng và trải nghiệm người dùng tốt

  1.  ## Phạm vi của dự án

5.  Phạm vi về dịch vụ

- Quản lý upload, chỉnh sửa, xóa các bản dịch phụ đề và tài liệu

- Cung cấp API phục vụ Extension lấy dữ liệu bản dịch

6.  Phạm vi về khách hàng

- Người dùng (User)

- Dịch thuật viên (Translator)

- Quản trị viên (Admin)

- Người đánh giá bản dịch(Reviewer)

7.  Phạm vi về nền tảng/hệ thống

- Backend server và database lưu trữ dữ liệu

- Extension Chrome chạy trên trình duyệt Chrome

2.  # Yêu cầu và đặc tả dự án

    1.  ## Yêu cầu chức năng

- User: đăng nhập, đăng xuất

- Translator:

```{=html}
<!-- -->
```

- Upload file phụ đề đã dịch

- Upload file Document đã dịch

- Xem Dashboard danh sách bản dịch phụ đề và Document

- Tải xuống file đã dịch

- Tìm kiếm bản dịch theo bộ lọc

- Xóa bản dịch

- Chỉnh sửa metadata hoặc thay thế file dịch

```{=html}
<!-- -->
```

- Admin: quản lý tài khoản người dùng (xóa tài khoản, cấp quyền hoặc
  thu hồi quyền Translator)

- Reviewer: quản lý bản dịch chờ duyệt, theo dõi lịch sử duyệt bản
  dịch

- Extension:

```{=html}
<!-- -->
```

- Tự động trích xuất thông tin

- Gửi request lấy bản dịch phù hợp từ backend

- Hiển thị popup cho người dùng lựa chọn xem bản dịch

- Hiển thị bản dịch khi người dùng đồng ý

- Cho phép bật/tắt extension

  1.  ## Yêu cầu phi chức năng

  ```{=html}
  <!-- -->
  ```

  1.  ### Tính bảo mật

```{=html}
<!-- -->
```

- Sử dụng API Key hoặc Token để xác thực truy cập và chỉnh sửa dữ liệu

- Bảo vệ dữ liệu trong database khỏi truy cập trái phép

- Tuân thủ chính sách bảo mật dữ liệu cá nhân

  1.  ### Tính sẵn sàng và khả năng đáp ứng

```{=html}
<!-- -->
```

- Hệ thống hoạt động 24/7, luôn sẵn sàng phục vụ người dùng

- Đảm bảo khả năng xử lý đồng thời nhiều yêu cầu từ người dùng

  1.  ### Hiệu suất

```{=html}
<!-- -->
```

- Thời gian hiển thị bản dịch trên Extension không quá 1 giây kể từ
  khi truy cập trang web

- Thời gian xử lý thao tác của Translator (upload, chỉnh sửa, xóa)
  không quá 0.5 giây

  1.  ### Giao diện người dùng

```{=html}
<!-- -->
```

- Giao diện dễ hiểu, thân thiện, không yêu cầu kiến thức công nghệ cao

- Extension tương thích tốt với trình duyệt Chrome

  1.  ## Đặc tả phần mềm

```{=html}
<!-- -->
```

- Cơ sở dữ liệu lưu trữ các bảng: Users, Roles, SubtitleTranslations,
  DocumentTranslations, Courses, Videos

- API backend RESTful hỗ trợ các chức năng CRUD, xác thực, phân quyền

- Lưu trữ file dịch trên server hoặc dịch vụ lưu trữ đám mây, đường
  dẫn file lưu trong database

- Extension sử dụng Chrome Extension API, giao tiếp qua HTTPS

- Hệ thống có logging và xử lý lỗi

3.  # Kiến trúc và thiết kế phần mềm

    1.  ## Kiến trúc phần mềm

- Kiến trúc lựa chọn: Kiến trúc Client-Server với REST API

- Lý do:

  - Phân tách rõ ràng giữa backend và frontend, dễ bảo trì và mở
    rộng

  - REST API giúp tích hợp dễ dàng với Extension và các client khác

  - Đáp ứng yêu cầu bảo mật và hiệu năng

  - Phù hợp với mô hình đa người dùng và quản lý phân quyền

  1.  ## Usecase

```{=html}
<!-- -->
```

- Actors: User, Translator, Admin, Reviewer

- Use Case chính

---

Use Case Actor Mô tả

---

Đăng nhập All Người dùng đăng nhập vào hệ
thống

Đăng xuất All Người dùng đăng xuất khỏi hệ
thống

Hiển thị bản dịch qua User Extension lấy và hiển thị bản
Extension dịch

Bật/tắt Extension User Người dùng bật hoặc tắt
Extension

Upload file phụ đề Translator Upload file phụ đề, nhập
metadata

Upload file Document Translator Upload file Document, nhập
metadata

Xem danh sách bản dịch Translator Xem danh sách các bản dịch

Tải xuống file dịch Translator Tải file đã upload

Tìm kiếm bản dịch Translator Tìm kiếm theo bộ lọc

Xóa bản dịch Translator Xóa bản dịch

Chỉnh sửa metadata & Reup Translator Chỉnh sửa thông tin hoặc thay
file thế file

Quản lý tài khoản Admin Thêm/xóa tài khoản

Quản lý phân quyền Admin Cấp/thu hồi quyền

Quản lý bản dịch chờ duyệt Reviewer Phê duyệt hoặc từ chối bản dịch

Theo dõi lịch sử duyệt bản Reviewer Theo dõi lịch sử duyệt bản dịch
dịch

---

### Usecase của User

- Usecase Đăng nhập:

+-----------+----------------------------------------------------------+
| **Use | Đăng nhập |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | User có thể đăng nhập tài khoản vào hệ thống và sử dụng |
| | các chức năng trong đó |
+-----------+----------------------------------------------------------+
| **Điều | User chưa đăng nhập vào hệ thống |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. User truy cập vào trang web quản lý, nhấn vào mục |
| chính** | "Login\" |
| | |
| | 2\. Hệ thống hiển thị Form Login |
| | |
| | 3\. User nhập vào các thông tin đăng nhập |
| | |
| | 4\. Nếu thông tin đăng nhập đúng, cập nhật thông tin vào |
| | hệ thống |
+-----------+----------------------------------------------------------+
| **Luồng | Ở bước 4, nếu thông tin đăng nhập sai sẽ hiển thị thông |
| phụ** | báo cho người dùng |
+-----------+----------------------------------------------------------+

- Usecase Đăng xuất:

+-----------+----------------------------------------------------------+
| **Use | Đăng xuất |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | User có thể đăng xuất khỏi hệ thống để kết thúc phiên |
| | làm việc |
+-----------+----------------------------------------------------------+
| **Điều | User chưa đăng nhập vào hệ thống |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. User nhấn nút "Logout" trên giao diện |
| chính** | |
| | 2\. Hệ thống hủy phiên làm việc |
| | |
| | 3\. Hệ thống chuyển hướng User về trang đăng nhập hoặc |
| | trang chủ |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu đăng xuất không thành công, hiển thị thông báo lỗi |
| phụ** | |
+-----------+----------------------------------------------------------+

- Usecase Hiển thị bản dịch qua Extension:

+-----------+----------------------------------------------------------+
| **Use | Hiển thị bản dịch qua Extension |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | User dùng Extension để xem bản dịch phụ đề hoặc tài liệu |
| | khi truy cập trang web thuộc các nguồn MOOC |
+-----------+----------------------------------------------------------+
| **Điều | User đã cài đặt và bật Extension |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. User truy cập trang web thuộc các nguồn MOOC |
| chính** | |
| | 2\. Extension tự động lấy URL, Course ID, Video ID |
| | |
| | 3\. Gửi yêu cầu đến backend lấy bản dịch |
| | |
| | 4\. Hiển thị popup hỏi User có muốn xem bản dịch không |
| | |
| | 5\. Nếu đồng ý, hiển thị bản dịch trên giao diện |
| | Extension |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu không tìm thấy bản dịch hoặc backend lỗi, hiển thị |
| phụ** | thông báo không có bản dịch |
+-----------+----------------------------------------------------------+

- Usecase Bật hoặc tắt Extension Chrome:

+-----------+----------------------------------------------------------+
| **Use | Bật hoặc tắt Extension Chrome |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | User có thể bật hoặc tắt Extension để quyết định có sử |
| | dụng bản dịch hay không |
+-----------+----------------------------------------------------------+
| **Điều | User đã cài đặt Extension |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. User nhấn vào biểu tượng Extension trên trình duyệt |
| chính** | |
| | 2\. Extension hiển thị popup với tùy chọn bật/tắt |
| | |
| | 3\. User chọn bật hoặc tắt |
| | |
| | 4\. Extension lưu trạng thái lựa chọn |
| | |
| | 5\. Khi bật, Extension hoạt động lấy bản dịch và hiển |
| | thị. Khi tắt, Extension không hoạt động |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu trạng thái lưu không thành công, hiển thị thông báo |
| phụ** | lỗi |
+-----------+----------------------------------------------------------+

### Usecase của Translator

- Usecase Upload phụ đề tiếng Việt:

+-----------+----------------------------------------------------------+
| **Use | Upload phụ đề tiếng Việt |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể upload file phụ đề tiếng Việt cho |
| | video học tập |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có quyền upload phụ đề |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập trang upload phụ đề |
| chính** | |
| | 2\. Nhập metadata: tên video, URL, Course ID, Video ID |
| | |
| | 3\. Chọn file phụ đề tiếng Việt từ máy tính |
| | |
| | 4\. Nhấn nút "Upload" |
| | |
| | 5\. Hệ thống lưu file và thông tin metadata vào database |
| | |
| | 6\. Hiển thị thông báo upload thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Ở bước 4, nếu file không đúng định dạng hoặc thiếu thông |
| phụ** | tin, hệ thống hiển thị lỗi và yêu cầu sửa |
+-----------+----------------------------------------------------------+

- Usecase Upload file Document tiếng Việt:

+-----------+----------------------------------------------------------+
| **Use | Upload file Document tiếng Việt |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể upload file Document tiếng Việt đã |
| | dịch |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có quyền upload Document |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập trang upload Document |
| chính** | |
| | 2\. Nhập metadata: tên Document, URL, Course ID, |
| | Document ID |
| | |
| | 3\. Chọn file Document tiếng Việt từ máy tính |
| | |
| | 4\. Nhấn nút "Upload" |
| | |
| | 5\. Hệ thống lưu file và thông tin metadata vào database |
| | |
| | 6\. Hiển thị thông báo upload thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Ở bước 4, nếu file không đúng định dạng hoặc thiếu thông |
| phụ** | tin, hệ thống hiển thị lỗi và yêu cầu sửa |
+-----------+----------------------------------------------------------+

- Usecase Xem danh sách bản dịch:

+-----------+----------------------------------------------------------+
| **Use | Xem danh sách bản dịch |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể xem danh sách các bản dịch phụ đề và |
| | tài liệu đã upload |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập trang Dashboard |
| chính** | |
| | 2\. Hệ thống hiển thị danh sách bản dịch (phụ đề và |
| | Document) của Translator |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu không có bản dịch nào, hiển thị thông báo "Chưa có |
| phụ** | bản dịch nào" |
+-----------+----------------------------------------------------------+

- Usecase Tải xuống file dịch:

+-----------+----------------------------------------------------------+
| **Use | Tải xuống file dịch |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể tải file phụ đề hoặc Document đã |
| | upload về máy tính |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có bản dịch trong danh sách |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập danh sách bản dịch |
| chính** | |
| | 2\. Chọn bản dịch cần tải xuống |
| | |
| | 3\. Nhấn nút "Download" |
| | |
| | 4\. Hệ thống tải file về máy tính |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu file không còn tồn tại hoặc lỗi khi tải, hiển thị |
| phụ** | thông báo lỗi |
+-----------+----------------------------------------------------------+

- Usecase Tìm kiếm bản dịch:

+-----------+----------------------------------------------------------+
| **Use | Tìm kiếm bản dịch |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể tìm kiếm các bản dịch theo nhiều tiêu |
| | chí khác nhau |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có quyền upload Document |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập trang danh sách bản dịch |
| chính** | |
| | 2\. Nhập tiêu chí tìm kiếm: tên bản dịch, URL, người |
| | dịch, Course ID, Video ID,... |
| | |
| | 3\. Nhấn nút "Tìm kiếm" |
| | |
| | 4\. Hệ thống trả về danh sách bản dịch thỏa mãn điều |
| | kiện |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu không có kết quả, hệ thống hiển thị thông báo "Không |
| phụ** | tìm thấy bản dịch phù hợp" |
+-----------+----------------------------------------------------------+

- Usecase Chỉnh sửa metadata hoặc thay thế file dịch:

+-----------+----------------------------------------------------------+
| **Use | Chỉnh sửa metadata hoặc thay thế file dịch |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể chỉnh sửa thông tin liên quan đến bản |
| | dịch hoặc thay thế file dịch đã upload trước đó |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có quyền chỉnh sửa bản dịch |
| kiện** | của mình |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập danh sách bản dịch đã upload |
| chính** | |
| | 2\. Chọn bản dịch cần chỉnh sửa |
| | |
| | 3\. Hệ thống hiển thị form chỉnh sửa thông tin |
| | (metadata) và upload file mới |
| | |
| | 4\. Translator chỉnh sửa thông tin hoặc chọn file mới để |
| | thay thế |
| | |
| | 5\. Nhấn nút "Lưu" |
| | |
| | 6\. Hệ thống kiểm tra dữ liệu hợp lệ, lưu thay đổi vào |
| | database và cập nhật file mới nếu có |
| | |
| | 7\. Hiển thị thông báo cập nhật thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu dữ liệu nhập không hợp lệ hoặc file không đúng định |
| phụ** | dạng, hệ thống hiển thị lỗi và yêu cầu sửa lại |
+-----------+----------------------------------------------------------+

- Usecase Xóa bản dịch:

+-----------+----------------------------------------------------------+
| **Use | Xóa bản dịch |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Translator có thể xóa bản dịch phụ đề hoặc Document đã |
| | upload |
+-----------+----------------------------------------------------------+
| **Điều | Translator đã đăng nhập và có quyền xóa bản dịch |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Translator truy cập danh sách bản dịch |
| chính** | |
| | 2\. Chọn bản dịch cần xóa |
| | |
| | 3\. Nhấn nút "Xóa" |
| | |
| | 4\. Hệ thống yêu cầu xác nhận xóa |
| | |
| | 5\. Nếu xác nhận, hệ thống xóa bản dịch khỏi database và |
| | file lưu trữ |
| | |
| | 6\. Hiển thị thông báo xóa thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu thao tác xóa không thành công do lỗi hệ thống, hiển |
| phụ** | thị thông báo lỗi |
+-----------+----------------------------------------------------------+

### Usecase của Admin

- Usecase Quản lý tài khoản người dùng:

+-----------+----------------------------------------------------------+
| **Use | Quản lý tài khoản người dùng |
| Case | |
| Name** | |
+-----------+----------------------------------------------------------+
| **Mô tả** | Admin có thể thêm, xóa tài khoản người dùng |
+-----------+----------------------------------------------------------+
| **Điều | Admin đã đăng nhập và có quyền quản lý tài khoản |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Admin truy cập trang quản lý người dùng |
| chính** | |
| | 2\. Xem danh sách người dùng |
| | |
| | 3\. Chọn người dùng cần chỉnh sửa |
| | |
| | 4\. Thực hiện thay đổi quyền hoặc xóa tài khoản |
| | |
| | 5\. Hệ thống cập nhật dữ liệu |
| | |
| | 6\. Hiển thị thông báo thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu thao tác không thành công do lỗi hệ thống, hiển thị |
| phụ** | thông báo lỗi |
+-----------+----------------------------------------------------------+

- Usecase Cấp hoặc thu hồi quyền cho người dùng:

+-----------+----------------------------------------------------------+
| **Use | Cấp hoặc thu hồi quyền cho người dùng |
| Case | |
| Name** | |
+===========+==========================================================+
| **Mô tả** | Translator có thể xóa bản dịch phụ đề hoặc Document đã |
| | upload |
+-----------+----------------------------------------------------------+
| **Điều | Admin đã đăng nhập và có quyền quản lý phân quyền |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Admin truy cập trang quản lý người dùng |
| chính** | |
| | 2\. Tìm kiếm người dùng cần thay đổi quyền |
| | |
| | 3\. Chọn người dùng và chọn cấp hoặc thu hồi quyền |
| | Translator |
| | |
| | 4\. Hệ thống cập nhật quyền trong database |
| | |
| | 5\. Hiển thị thông báo thành công |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu thao tác không thành công do lỗi hệ thống, hiển thị |
| phụ** | thông báo lỗi |
+-----------+----------------------------------------------------------+

### Usecase của Reviewer

- Usecase Quản lý bản dịch chờ duyệt:

+-----------+----------------------------------------------------------+
| **Use | Quản lý bản dịch chờ duyệt |
| Case | |
| Name** | |
+===========+==========================================================+
| **Mô tả** | Reviewer quyết định phê duyệt bản dịch để hiển thị cho |
| | User hoặc từ chối để Translator chỉnh sửa lại |
+-----------+----------------------------------------------------------+
| **Điều | Reviewer đã đăng nhập |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Reviewer truy cập danh sách các bản dịch chờ duyệt |
| chính** | |
| | 2\. Reviewer xem chi tiết bản dịch |
| | |
| | 3\. Reviewer chọn "Phê duyệt" hoặc "Từ chối" bản dịch |
| | |
| | 4\. Nếu phê duyệt, trạng thái bản dịch được cập nhật |
| | thành "Đã duyệt". Nếu từ chối, Reviewer nhập lý do và hệ |
| | thống gửi thông báo yêu cầu chỉnh sửa cho Translator |
| | |
| | 5\. Hiển thị thông báo thành công về hành động đã thực |
| | hiện |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu thao tác không thành công do lỗi hệ thống, hiển thị |
| phụ** | thông báo lỗi |
+-----------+----------------------------------------------------------+

- Usecase Theo dõi lịch sử duyệt bản dịch:

+-----------+----------------------------------------------------------+
| **Use | Theo dõi lịch sử duyệt bản dịch |
| Case | |
| Name** | |
+===========+==========================================================+
| **Mô tả** | Reviewer có thể xem lại lịch sử các bản dịch đã duyệt |
| | hoặc từ chối, cùng với ghi chú và thời gian |
+-----------+----------------------------------------------------------+
| **Điều | Reviewer đã đăng nhập |
| kiện** | |
+-----------+----------------------------------------------------------+
| **Luồng | 1\. Reviewer truy cập trang lịch sử duyệt bản dịch |
| chính** | |
| | 2\. Hệ thống hiển thị danh sách các bản dịch đã xử lý |
| | với trạng thái và ghi chú |
+-----------+----------------------------------------------------------+
| **Luồng | Nếu không có bản ghi lịch sử, hiển thị thông báo "Không |
| phụ** | có lịch sử duyệt bản dịch" |
+-----------+----------------------------------------------------------+

## Sơ đồ use case tổng quát của hệ thống

![A diagram of a diagram AI-generated content may be
incorrect.](media/image2.png){width="6.383886701662292in" height="6.467226596675416in"}

Hình 1: Usecase tổng quát

**\
**

## Class Diagram

![A screenshot of a computer AI-generated content may be
incorrect.](media/image3.png){width="7.470470253718285in" height="7.508298337707786in"}

Hình 2: Class diagram

**\
**

## Sequence Diagram

![A diagram of a project AI-generated content may be
incorrect.](media/image4.png){width="6.727777777777778in" height="2.865972222222222in"}

Hình 3: Sequence Diagram cho hoạt động hiển thị bản dịch của Extension

## Activity Diagram

![A diagram of a work flow AI-generated content may be
incorrect.](media/image5.png){width="5.450472440944882in" height="5.40880249343832in"}

Hình 4: Activity Diagram cho thao tác bật mở Extension
