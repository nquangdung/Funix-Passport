![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image1.png)

Tài liệu đặc tả yêu cầu

> ***FUNiX Passport***

Revision History

  ----------------- ------------- --------------------------- -----------------
  **Date**          **Version**   **Description**             **Author**

  \<04/13/07\>      \<1.0\>       SRS 1.0                     Group-1

  \<04/15/07\>      \<2.0\>       SRS 2.0                     Group-1

  \<04/15/07\>      \<3.0\>       SRS 3.0                     Group-1

  \<04/16/07\>      \<4.0\>       SRS 4.0                     Group-1
  ----------------- ------------- --------------------------- -----------------

Bảng thuật ngữ

Cung cấp tổng quan về bất kỳ định nghĩa nào mà người đọc nên hiểu trước
khi đọc tiếp.

  ----------- -----------------------------------------------------------
  Cấu hình    Nó có nghĩa là một sản phẩm có sẵn / Được chọn từ một danh
              mục có thể được tùy chỉnh.

  FAQ         Frequently Asked Questions

  CRM         Customer Relationship Management

  RAID 5      Redundant Array of Inexpensive Disk/Drives
  ----------- -----------------------------------------------------------

Table of Contents

[1. Giới thiệu tổng quan về dự án
[4](#giới-thiệu-tổng-quan-về-dự-án)](\l)

[1.1 Tóm tắt dự án [4](#tóm-tắt-dự-án)](\l)

[1.2 Phạm vi của dự án [4](#phạm-vi-của-dự-án)](\l)

[2. Yêu cầu và đặc tả dự án [5](#yêu-cầu-và-đặc-tả-dự-án)](\l)

[2.1 Yêu cầu chức năng [5](#yêu-cầu-chức-năng)](\l)

[2.2 Yêu cầu phi chức năng [7](#yêu-cầu-phi-chức-năng)](\l)

[2.2.1 Tính bảo mật [7](#tính-bảo-mật)](\l)

[2.2.2 Tính sẵn sàng và khả năng đáp ứng
[8](#tính-sẵn-sàng-và-khả-năng-đáp-ứng)](\l)

[2.2.3 Hiệu suất [8](#hiệu-suất)](\l)

[2.3 Đặc tả phần mềm [8](#đặc-tả-phần-mềm)](\l)

[3. Kiến trúc và thiết kế phần mềm
[10](#kiến-trúc-và-thiết-kế-phần-mềm)](\l)

[3.1 Kiến trúc phần mềm [10](#kiến-trúc-phần-mềm)](\l)

[3.2 Usecase [11](#usecase)](\l)

[3.2.1 Usecase của User [11](#usecase-của-user)](\l)

[3.2.2 Usecase của Translator [12](#usecase-của-translator)](\l)

[3.2.3 Usecase của Reviewer [15](#usecase-của-reviewer)](\l)

[3.2.4 Usecase của Admin [16](#usecase-của-admin)](\l)

[3.2.5 Usecase của Student [17](#usecase-của-student)](\l)

[3.3 Sơ đồ use case tổng quát của hệ thống
[18](#sơ-đồ-use-case-tổng-quát-của-hệ-thống)](\l)

[3.4 Class Diagram [19](#class-diagram)](\l)

[3.5 Sequence Diagram [19](#sequence-diagram)](\l)

[3.6 Activity Diagram [20](#activity-diagram)](\l)

Tài liệu đặc tả

1.  # Giới thiệu tổng quan về dự án

    1.  ## Tóm tắt dự án

> \- Hệ thống xây dựng là một hệ thống dịch thuật gồm 2 phần chính:một
> **Backend** mạnh mẽ để quản lý, lưu trữ dữ liệu dịch thuật (phụ đề
> video, tài liệu) và một **Tiện ích mở rộng (Extension)** trên trình
> duyệt Chrome để cung cấp các bản dịch này cho sinh viên một cách liền
> mạch.
>
> \- Mục đích chính của hệ thống là phá bỏ rào cản ngôn ngữ cho sinh
> viên FUNiX khi tiếp cận các khóa học trên nền tảng MOOC vốn chủ yếu sử
> dụng Tiếng Anh.
>
> \- Hệ thống giải quyết bài toán sinh viên gặp khó khăn trong việc học
> và nắm bắt kiến thức do chỉ có phụ đề/tài liệu gốc bằng Tiếng Anh.
> Bằng cách cung cấp bản dịch Tiếng Việt chất lượng, hệ thống giúp nâng
> cao trải nghiệm và hiệu quả học tập.
>
> \- Bằng cách cung cấp bản dịch Tiếng Việt chất lượng thông qua một quy
> trình kiểm duyệt chặt chẽ, hệ thống giúp nâng cao trải nghiệm và hiệu
> quả học tập.

\- Các mục tiêu của dự án:

> **+ Mục tiêu 1:** Xây dựng một Backend hoàn chỉnh cho phép các Dịch
> thuật viên (Translator) , Người duyệt(Reviewer) và Quản trị viên
> (Admin) quản lý hiệu quả kho dữ liệu và quy trình dịch thuật.
>
> **+ Mục tiêu 2:** Phát triển một Extension cho trình duyệt Chrome, có
> khả năng tự động nhận diện trang web và cung cấp bản dịch đã được phê
> duyệt cho sinh viên.
>
> **+ Mục tiêu 3:** Đảm bảo hệ thống có hiệu năng cao, bảo mật và ổn
> định, mang lại trải nghiệm mượt mà cho tất cả người dùng.
>
> **+ Mục tiêu 4:** Thiết kế giao diện người dùng (cho cả trang quản lý
> và Extension) đơn giản, trực quan, dễ sử dụng ngay cả với người không
> có nhiều kiến thức về công nghệ.

## Phạm vi của dự án

**- Phạm vi về dịch vụ:**

\+ Trong phạm vi:

-   Cung cấp nền tảng để lưu trữ, quản lý (thêm, sửa, xóa, tìm kiếm) các
    > tệp dịch thuật (phụ đề .srt, .vtt\... và tài liệu .pdf, .docx\...)
    > do con người dịch.

-   Thực hiện quy trình kiểm duyệt để đảm bảo chất lượng bản dịch trước
    > khi công khai.

-   Cung cấp bản dịch cho người dùng cuối (sinh viên) thông qua
    > Extension.

-   Quản lý phân quyền người dùng (Admin, Translator, Reviewer, User).

\+ Ngoài phạm vi:

-   Hệ thống không tự động dịch thuật bằng máy (như Google Translate).

-   Hệ thống không phải là một công cụ chỉnh sửa phụ đề/văn bản trực
    > tuyến.

**- Phạm vi về khách hàng:**

\+ Sinh viên FUNiX: Người dùng cuối, sử dụng Extension để xem các bản
dịch.

\+ Dịch thuật viên (Translator): Người dùng nội bộ, chịu trách nhiệm
upload và quản lý các bản dịch.

\+ Reviewer (Người duyệt): Người dùng nội bộ, chịu trách nhiệm kiểm tra
và phê duyệt chất lượng bản dịch.

\+ Quản trị viên (Admin): Người dùng nội bộ, chịu trách nhiệm quản lý
tài khoản người dùng.

**- Phạm vi về nền tảng/hệ thống**:

\+ Backend: Hoạt động như một Web API để Extension và trang quản trị có
thể giao tiếp.

\+ Trang quản lý (cho Admin, Translator): Giao diện web, truy cập qua
trình duyệt.

\+ Extension: Hoạt động trên trình duyệt Google Chrome.

2.  # Yêu cầu và đặc tả dự án

    1.  ## Yêu cầu chức năng

**A. Chức năng cho Quản trị viên (Admin)**

\- FN-ADMIN-01: Quản lý tài khoản người dùng

\+ Admin có thể xem danh sách tất cả người dùng trong hệ thống.

\+ Admin có quyền xóa một tài khoản người dùng bất kỳ (User hoặc
Translator).

\+ Admin có quyền thêm quyền cho một User, chuyển họ thành Translator
hoặc Reviewer.

\+ Admin có quyền xóa quyền của một Translator hoặc Reviewer., chuyển họ
thành User.

**B. Chức năng cho Dịch thuật viên (Translator)**

\- FN-TRN-01: Xác thực người dùng

\+ Translator có thể đăng nhập và đăng xuất khỏi hệ thống trên trang
quản lý.

\- FN-TRN-02 & FN-TRN-03: Gửi bản dịch (Phụ đề và Tài liệu)

\+ Upload: Upload tệp dịch và thông tin kèm theo để gửi duyệt. Trạng
thái ban đầu của bản dịch là \"Chờ duyệt\".

\+ Chỉnh sửa & Xóa: Có thể sửa hoặc xóa các bản dịch chưa được duyệt
hoặc bị từ chối.

\- FN-TRN-04: Xem và tìm kiếm bản dịch

\+ Xem danh sách các bản dịch đã upload trên 2 dashboard riêng biệt: một
cho phụ đề và một cho tài liệu.

\+ Tải xuống tệp gốc của một bản dịch bất kỳ.

\+ Tìm kiếm/lọc các bản dịch theo: Tên bản dịch, URL, Người dịch, Course
ID, Video ID.

**C. Chức năng cho Sinh viên (thông qua Extension)**

\- FN-US-01: Tự động phát hiện và truy vấn

\+ Khi người dùng truy cập một trang web, Extension tự động trích xuất
URL (và các ID như course_id, video_id nếu có).

\+ Extension gửi yêu cầu chứa thông tin đã trích xuất lên Backend để tìm
bản dịch tương ứng.

\- FN-US-02: Hiển thị thông báo và bản dịch

\+ Nếu Backend trả về kết quả có bản dịch với trạng thái "Đã duyệt",
Extension sẽ hiển thị một popup thông báo và hỏi người dùng có muốn xem
bản dịch không.

\+ Nếu người dùng đồng ý, Extension sẽ hiển thị phụ đề Tiếng Việt trên
trình phát video hoặc cung cấp quyền truy cập vào tài liệu đã dịch.

\- FN-US-03: Cài đặt Extension

\+ Người dùng có thể bật/tắt toàn bộ chức năng của Extension thông qua
một giao diện cài đặt đơn giản (như hình ảnh đã cung cấp).

![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image2.png){width="6.721527777777778in"
height="2.625in"}

**D. Chức năng cho Reviewer**

\- FN-REV-01: Quản lý hàng đợi duyệt

\+ Reviewer có thể xem một danh sách các bản dịch đang có trạng thái
\"Chờ duyệt\".

\- FN-REV-02: Đánh giá bản dịch

\+ Reviewer có thể tải tệp dịch về để kiểm tra nội dung và so sánh với
tài liệu gốc.

\- FN-REV-03: Phê duyệt hoặc Từ chối

\+ Phê duyệt: Nếu bản dịch đạt chất lượng, Reviewer thay đổi trạng thái
thành \"Đã duyệt\".

\+ Từ chối: Nếu bản dịch có lỗi, Reviewer thay đổi trạng thái thành \"Bị
từ chối\" và phải cung cấp lý do/phản hồi cho Translator.

## Yêu cầu phi chức năng

### 2.2.1 Tính bảo mật

**- Xác thực và Phân quyền:**

\+ Mọi yêu cầu truy cập tài nguyên cần quản lý (upload, sửa, xóa) lên
Backend phải được xác thực thông qua API Key hoặc Access Token .

\+ Hệ thống phải thực thi cơ chế phân quyền nghiêm ngặt: Translator
không thể thực hiện chức năng của Admin và ngược lại.

**- An toàn dữ liệu:**

\+ Dữ liệu nhạy cảm (như mật khẩu người dùng) phải được mã hóa một chiều
(hashing) trước khi lưu vào Database.

\+ Hệ thống cần có cơ chế chống lại các hình thức tấn công phổ biến như
SQL Injection, Cross-Site Scripting (XSS).

**- Quyền riêng tư:**

\+ Hệ thống chỉ thu thập những thông tin cần thiết cho hoạt động (URL,
Course ID, Video ID) và không theo dõi các hoạt động khác của người
dùng.

### 2.2.2 Tính sẵn sàng và khả năng đáp ứng

\- Hệ thống phải có khả năng hoạt động 24/7 để sinh viên có thể học tập
bất cứ lúc nào.

\- Backend phải luôn sẵn sàng nhận yêu cầu từ Extension và trang quản
lý.

\- Cần có cơ chế sao lưu (backup) cơ sở dữ liệu định kỳ để phòng trường
hợp xảy ra sự cố.

\- Mục tiêu thời gian hoạt động (uptime) của hệ thống phải đạt tối thiểu
99.5%.

### 2.2.3 Hiệu suất

\- **Tốc độ hiển thị bản dịch (cho Sinh viên)**: Thời gian từ khi sinh
viên truy cập trang web cho đến khi Extension hiển thị thông báo có bản
dịch không được vượt quá 1 giây.

\- **Tốc độ xử lý tác vụ (cho Translator)**: Thời gian xử lý các thao
tác trên trang quản lý (upload, submit, tìm kiếm, xóa) phải nhanh, trung
bình mỗi thao tác không được quá 0.5 giây.

\- **Khả năng chịu tải**: Backend phải có khả năng xử lý đồng thời nhiều
yêu cầu từ các Extension của nhiều sinh viên cùng lúc mà không bị treo
hoặc giảm hiệu suất đáng kể.

3.  ## Đặc tả phần mềm

    **- Kiến trúc hệ thống:**

    \+ Backend: Một ứng dụng web phía máy chủ, cung cấp các RESTful API
    để giao tiếp với các thành phần khác.

    \+ Database: Hệ thống cơ sở dữ liệu (có thể là SQL như PostgreSQL
    hoặc NoSQL như MongoDB) để lưu trữ thông tin người dùng và metadata
    của các bản dịch.

    \+ File Storage: Một giải pháp lưu trữ tệp (có thể là lưu trên cùng
    máy chủ hoặc sử dụng dịch vụ cloud storage như Amazon S3, Google
    Cloud Storage) để chứa các tệp phụ đề và tài liệu.

    \+ Extension: Một tiện ích mở rộng cho trình duyệt Google Chrome
    được phát triển bằng HTML, CSS, và JavaScript.

    \+ Giao diện quản lý: Một ứng dụng web (có thể là Single Page
    Application - SPA) được xây dựng bằng các framework hiện đại (ví dụ:
    React, Vue, Angular) để cung cấp giao diện cho Admin và Translator.

    **- Đặc tả Metadata trong Database:**

    **+** Bảng Translation:

    ID: UUID, Primary Key, Tự động tạo.

    TranslatorID: UUID, Foreign Key đến bảng Users.

    Name: String

    SourceURL: String

    UploadedDate: Timestamp, Tự động tạo.

    Status: Enum (\'Pending\', \'Approved\', \'Rejected\') - Trạng thái

    \+ Bảng VideoTranslations kế thừa Translation:

    VideoID: String.

    CourseID: String.

    ViSubtitleURL: String (Đường dẫn tới tệp phụ đề .srt, .vtt\...).

    EnSubtitleURL: String (Optional).

    \+ Bảng DocumentTranslations kế thừa Translation:

    DocumentURL: String (Đường dẫn tới tệp tài liệu đã dịch).

    \+ Bảng Users:

    ID: UUID, Primary Key.

    Username: String, Unique.

    PasswordHash: String.

    Role: Enum (\'User\', \'Translator\', \'Reviewer\', \'Admin\').

    \+ Bảng ReviewComments:

    ID: UUID, Primary Key.

    TranslationID: UUID, Foreign Key đến bảng dịch thuật.

    ReviewerID: UUID, Foreign Key đến bảng Users.

    Comment: Text - Nội dung phản hồi, lý do từ chối.

    CreatedAt: Timestamp.

```{=html}
<!-- -->
```
3.  # Kiến trúc và thiết kế phần mềm

    1.  ## Kiến trúc phần mềm

\- Dựa trên các yêu cầu của dự án, kiến trúc phần mềm được lựa chọn là
**Microservices**. Đây là một dạng cụ thể và nâng cao của mô hình
Client-Server, phù hợp nhất với các yêu cầu về tính linh hoạt, khả năng
mở rộng và bảo trì của hệ thống.

\- Lý do lựa chọn kiến trúc Microservices:

**+ Tính độc lập và linh hoạt:**

-   Hệ thống bao gồm các thành phần có chức năng riêng biệt: quản lý
    > người dùng, quản lý bản dịch, và phục vụ truy vấn cho extension.
    > Kiến trúc Microservices cho phép tách các chức năng này thành các
    > dịch vụ độc lập (ví dụ: UserService, TranslationService).

-   Mỗi dịch vụ có thể được phát triển, triển khai, và nâng cấp độc lập
    > mà không ảnh hưởng đến các dịch vụ khác. Điều này giúp các nhóm
    > phát triển (Backend, Frontend, Extension) có thể làm việc song
    > song, đẩy nhanh tiến độ dự án.

**+ Khả năng mở rộng :**

-   Dự kiến lượng truy cập từ Extension của sinh viên sẽ rất lớn và tập
    > trung vào dịch vụ truy vấn bản dịch. Với Microservices, chúng ta
    > có thể mở rộng (scale-up) chỉ riêng dịch vụ này để đáp ứng tải cao
    > mà không cần phải mở rộng toàn bộ hệ thống, giúp tối ưu hóa chi
    > phí tài nguyên.

**+ Tính ổn định và khả năng phục hồi** :

-   Nếu một dịch vụ gặp lỗi (ví dụ: dịch vụ quản lý của Translator tạm
    > thời bị sập), nó sẽ không làm ảnh hưởng đến các dịch vụ cốt lõi
    > khác. Sinh viên vẫn có thể truy vấn và xem bản dịch một cách bình
    > thường. Điều này tăng cường đáng kể tính sẵn sàng của hệ thống.

**+ Tự do về công nghệ :**

-   Mỗi microservice có thể được xây dựng bằng công nghệ phù hợp nhất
    > cho chức năng của nó. Ví dụ, UserService có thể dùng Node.js để xử
    > lý I/O hiệu quả, trong khi một dịch vụ phân tích dữ liệu truy cập
    > trong tương lai có thể được viết bằng Python.

==\>Microservices giải quyết được các vấn đề về sự phụ thuộc chặt chẽ,
khó mở rộng và khó bảo trì khi dự án phát triển lớn hơn.

1.  ## Usecase

    1.  ### Usecase của User

\- Usecase 1:

+--------------+-------------------------------------------------------+
| **Use Case   | Đăng nhập                                             |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | User có thể đăng nhập tài khoản vào hệ thống và sử    |
|              | dụng các chức năng trong đó.                          |
+--------------+-------------------------------------------------------+
| **Điều       | User chưa đăng nhập vào hệ thống                      |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. User truy cập vào trang web quản lý. Nhấn vào mục |
| chính**      | "Login\"                                              |
|              |                                                       |
|              | 2\. Hệ thống hiển thị Form Login.                     |
|              |                                                       |
|              | 3\. User nhập vào các thông tin đăng nhập.            |
|              |                                                       |
|              | 4\. Nếu thông tin đăng nhập đúng, cập nhật thông tin  |
|              | vào hệ thống.                                         |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 4, nếu thông tin đăng nhập sai sẽ hiển thị     |
| phụ**        | thông báo cho người dùng.                             |
+--------------+-------------------------------------------------------+

\- Usecase 2:

+--------------+-------------------------------------------------------+
| **Use Case   | Đăng xuất                                             |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | User kết thúc phiên làm việc và thoát khỏi hệ thống.  |
+--------------+-------------------------------------------------------+
| **Điều       | User đã đăng nhập vào hệ thống.                       |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. User nhấn vào nút \"Logout\".                     |
| chính**      |                                                       |
|              | 2\. Hệ thống hủy phiên làm việc hiện tại.             |
|              |                                                       |
|              | 3\. Hệ thống chuyển hướng người dùng về trang đăng    |
|              | nhập.                                                 |
+--------------+-------------------------------------------------------+
| **Luồng      | Không có.                                             |
| phụ**        |                                                       |
+--------------+-------------------------------------------------------+

### Usecase của Translator

\- Usecase 1:

+--------------+-------------------------------------------------------+
| **Use Case   | Upload bản dịch                                       |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tải lên hệ thống một tệp bản dịch mới, có  |
|              | thể là phụ đề cho video hoặc tài liệu dịch, kèm theo  |
|              | các thông tin mô tả cần thiết.                        |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống.                 |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator nhấn vào nút \"Upload\" trên thanh     |
| chính**      | điều hướng hoặc dashboard.                            |
|              |                                                       |
|              | 2\. Hệ thống hiển thị giao diện upload, yêu cầu       |
|              | Translator chọn loại bản dịch: \"Phụ đề Video\" hoặc  |
|              | \"Tài liệu\".                                         |
|              |                                                       |
|              | 3\. Nếu Translator chọn \"Phụ đề Video\":             |
|              |                                                       |
|              | a\. Hệ thống hiển thị form nhập liệu gồm các trường:  |
|              | Tên Video, URL Video, Course ID, và Video ID.         |
|              |                                                       |
|              | b\. Translator điền đầy đủ thông tin vào các trường.  |
|              |                                                       |
|              | 4\. Nếu Translator chọn \"Tài liệu\":                 |
|              |                                                       |
|              | a\. Hệ thống hiển thị form nhập liệu gồm các trường:  |
|              | Tên bản dịch và URL của tài liệu gốc.                 |
|              |                                                       |
|              | b\. Translator điền đầy đủ thông tin vào các trường.  |
|              |                                                       |
|              | 5\. Translator nhấn nút \"Chọn tệp\" và chọn tệp phụ  |
|              | đề hoặc tài liệu tương ứng từ máy tính.               |
|              |                                                       |
|              | 6\. Tên tệp đã chọn được hiển thị trên giao diện.     |
|              |                                                       |
|              | 7\. Translator nhấn nút \"Submit\" để bắt đầu quá     |
|              | trình tải lên.                                        |
|              |                                                       |
|              | 8\. Hệ thống kiểm tra tính hợp lệ của tất cả các      |
|              | thông tin đã nhập và định dạng tệp.                   |
|              |                                                       |
|              | 9\. Hệ thống lưu tệp vào File Storage, đồng thời tạo  |
|              | một bản ghi metadata mới trong Database.              |
|              |                                                       |
|              | 10\. Hệ thống hiển thị thông báo \"Đã gửi bản dịch để |
|              | chờ duyệt thành công\" và chuyển hướng người dùng về  |
|              | trang dashboard, nơi bản dịch mới vừa tải lên xuất    |
|              | hiện ở đầu danh sách với trạng thái chờ duyệt.        |
+--------------+-------------------------------------------------------+
| **Luồng      | \- Tại bước 8: Nếu bất kỳ trường thông tin bắt buộc   |
| phụ**        | nào bị bỏ trống hoặc có định dạng không hợp lệ, hệ    |
|              | thống sẽ hiển thị thông báo lỗi ngay tại trường đó và |
|              | không cho phép submit.                                |
|              |                                                       |
|              | \- Tại bước 8: Nếu định dạng tệp không được hỗ trợ    |
|              | (ví dụ: .exe), hệ thống sẽ hiển thị lỗi \"Định dạng   |
|              | tệp không hợp lệ\".\<br\>                             |
|              |                                                       |
|              | \- Tại bước 9: Nếu có lỗi xảy ra ở phía máy chủ (lỗi  |
|              | kết nối database, lỗi lưu tệp), hệ thống sẽ hiển thị  |
|              | thông báo \"Đã có lỗi xảy ra, vui lòng thử lại.\"     |
+--------------+-------------------------------------------------------+

\- Usecase 2:

+--------------+-------------------------------------------------------+
| **Use Case   | Nhập Metadata bản dịch                                |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator nhập các thông tin mô tả cho bản dịch như  |
|              | Tên, URL, Course ID, Video ID.                        |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đang trong luồng \"Upload bản dịch\" hoặc  |
| kiện**       | \"Chỉnh sửa thông tin\".                              |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Hệ thống hiển thị form với các trường thông tin:  |
| chính**      | Tên bản dịch, URL gốc, Course ID, Video ID (nếu là    |
|              | phụ đề).                                              |
|              |                                                       |
|              | 2\. Translator điền thông tin vào các trường.         |
|              |                                                       |
|              | 3\. Hệ thống kiểm tra tính hợp lệ của dữ liệu ngay    |
|              | khi người dùng nhập.                                  |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu dữ liệu nhập vào không hợp lệ (ví dụ: định dạng   |
| phụ**        | URL sai), hệ thống sẽ hiển thị thông báo lỗi bên dưới |
|              | trường nhập liệu tương ứng.                           |
+--------------+-------------------------------------------------------+

\- Usecase 3:

+--------------+-------------------------------------------------------+
| **Use Case   | Chọn tệp tải lên                                      |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator chọn một tệp bản dịch từ máy tính cá nhân  |
|              | để tải lên hệ thống.                                  |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đang trong luồng \"Upload bản dịch\" hoặc  |
| kiện**       | \"Thay thế tệp dịch\".                                |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator nhấn vào nút \"Chọn tệp\" hoặc khu vực |
| chính**      | tải tệp.                                              |
|              |                                                       |
|              | 2\. Hệ thống hiển thị cửa sổ chọn tệp của hệ điều     |
|              | hành.                                                 |
|              |                                                       |
|              | 3\. Translator điều hướng, chọn một tệp và nhấn       |
|              | \"Open\" hoặc \"Select\".                             |
|              |                                                       |
|              | 4\. Hệ thống ghi nhận tên tệp đã chọn và hiển thị     |
|              | trên giao diện.                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu Translator đóng cửa sổ chọn tệp mà không chọn tệp |
| phụ**        | nào, hệ thống quay lại trạng thái trước đó.           |
+--------------+-------------------------------------------------------+

\- Usecase 4:

+--------------+-------------------------------------------------------+
| **Use Case   | Tìm kiếm bản dịch                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tìm kiếm các bản dịch đã có trên hệ thống  |
|              | dựa trên các bộ lọc.                                  |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập và đang ở trang dashboard.    |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator nhập từ khóa và/hoặc chọn các giá trị  |
| chính**      | từ bộ lọc (Tên bản dịch, Url, Người dịch, Course ID,  |
|              | Video ID).                                            |
|              |                                                       |
|              | 2\. Translator nhấn nút \"Tìm kiếm\".                 |
|              |                                                       |
|              | 3\. Hệ thống truy vấn và trả về danh sách các bản     |
|              | dịch phù hợp.                                         |
|              |                                                       |
|              | 4\. Hệ thống hiển thị kết quả cho Translator.         |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu không có bản dịch nào khớp với tiêu chí tìm kiếm, |
| phụ**        | hệ thống hiển thị thông báo \"Không tìm thấy kết quả  |
|              | phù hợp\".                                            |
+--------------+-------------------------------------------------------+

\- Usecase 5:

+--------------+-------------------------------------------------------+
| **Use Case   | Chỉnh sửa thông tin bản dịch                          |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator cập nhật lại các thông tin mô tả           |
|              | (metadata) cho một bản dịch đã tồn tại trên hệ thống. |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống.                 |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Trên trang dashboard, Translator sử dụng chức     |
| chính**      | năng tìm kiếm/lọc để xác định bản dịch cần chỉnh sửa. |
|              |                                                       |
|              | 2\. Translator nhấn vào nút \"Sửa\" hoặc biểu tượng   |
|              | chỉnh sửa tương ứng với bản dịch đó.                  |
|              |                                                       |
|              | 3\. Hệ thống hiển thị một form (biểu mẫu) với các     |
|              | trường thông tin được điền sẵn dữ liệu hiện tại của   |
|              | bản dịch (Tên, URL, Course ID, v.v.).                 |
|              |                                                       |
|              | 4\. Translator thay đổi thông tin trong các trường    |
|              | mong muốn.                                            |
|              |                                                       |
|              | 5\. Hệ thống kiểm tra tính hợp lệ của dữ liệu mới     |
|              | được nhập.                                            |
|              |                                                       |
|              | 6\. Sau khi hoàn tất chỉnh sửa, Translator nhấn nút   |
|              | \"Lưu thay đổi\".                                     |
|              |                                                       |
|              | 7\. Hệ thống cập nhật bản ghi tương ứng trong         |
|              | Database với thông tin mới.                           |
|              |                                                       |
|              | 8\. Hệ thống hiển thị thông báo \"Cập nhật thành      |
|              | công\" và làm mới lại danh sách bản dịch.             |
+--------------+-------------------------------------------------------+
| **Luồng      | \- Tại bước 5: Nếu dữ liệu nhập vào không hợp lệ, hệ  |
| phụ**        | thống sẽ hiển thị lỗi ngay tại trường đó và không cho |
|              | phép lưu.                                             |
|              |                                                       |
|              | \- Tại bất kỳ lúc nào: Nếu Translator nhấn nút        |
|              | \"Hủy\" hoặc đóng form, mọi thay đổi sẽ không được    |
|              | lưu và hệ thống quay trở lại trang dashboard.         |
+--------------+-------------------------------------------------------+

\- Usecase 6:

+--------------+-------------------------------------------------------+
| **Use Case   | Thay thế tệp dịch                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tải lên một tệp tin mới để thay thế cho    |
|              | tệp tin của một bản dịch đã có, mà không làm thay đổi |
|              | các thông tin metadata.                               |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập và đã xác định được bản dịch  |
| kiện**       | cần thay thế tệp.                                     |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Trên trang dashboard, Translator tìm bản dịch cần |
| chính**      | thay thế tệp.                                         |
|              |                                                       |
|              | 2\. Translator nhấn vào nút \"Thay thế tệp\" (hoặc    |
|              | Re-upload).                                           |
|              |                                                       |
|              | 3\. Hệ thống hiển thị một cửa sổ yêu cầu chọn tệp     |
|              | mới.                                                  |
|              |                                                       |
|              | 4\. Translator chọn một tệp mới từ máy tính của mình. |
|              |                                                       |
|              | 5\. Hệ thống kiểm tra định dạng của tệp mới.          |
|              |                                                       |
|              | 6\. Translator nhấn nút \"Xác nhận\" để bắt đầu thay  |
|              | thế.                                                  |
|              |                                                       |
|              | 7\. Hệ thống tiến hành xóa tệp cũ khỏi File Storage,  |
|              | tải lên tệp mới, và cập nhật lại đường dẫn tệp trong  |
|              | bản ghi ở Database.                                   |
|              |                                                       |
|              | 8\. Hệ thống hiển thị thông báo \"Thay thế tệp thành  |
|              | công\".                                               |
+--------------+-------------------------------------------------------+
| **Luồng      | \- Tại bước 5: Nếu định dạng tệp mới không hợp lệ, hệ |
| phụ**        | thống hiển thị lỗi và hủy thao tác.                   |
|              |                                                       |
|              | \- Tại bước 7: Nếu quá trình tải tệp mới lên thất     |
|              | bại, hệ thống sẽ giữ lại tệp cũ và thông báo lỗi cho  |
|              | người dùng.                                           |
+--------------+-------------------------------------------------------+

### Usecase của Reviewer

\- Usecase 1:

+--------------+-------------------------------------------------------+
| **Use Case   | Xem danh sách bản dịch chờ duyệt                      |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Reviewer truy cập để xem tất cả các bản dịch đang ở   |
|              | trạng thái \"Chờ duyệt\".                             |
+--------------+-------------------------------------------------------+
| **Điều       | Reviewer đã đăng nhập.                                |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Reviewer chọn mục \"Duyệt bản dịch\" từ menu.     |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị danh sách các bản dịch có trạng |
|              | thái \"Pending\".                                     |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu không có bản dịch nào cần duyệt, hệ thống hiển    |
| phụ**        | thị thông báo.                                        |
+--------------+-------------------------------------------------------+

\- Usecase 2 :

+--------------+-------------------------------------------------------+
| **Use Case   | Phê duyệt bản dịch                                    |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Reviewer phê duyệt một bản dịch đạt chất lượng.       |
+--------------+-------------------------------------------------------+
| **Điều       | Reviewer đang xem danh sách chờ duyệt.                |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Reviewer chọn một bản dịch để kiểm tra.           |
| chính**      |                                                       |
|              | 2\. Sau khi xác định bản dịch đạt yêu cầu, Reviewer   |
|              | nhấn nút \"Phê duyệt\".                               |
|              |                                                       |
|              | 3\. Hệ thống yêu cầu xác nhận.                        |
|              |                                                       |
|              | 4\. Hệ thống cập nhật trạng thái bản dịch thành       |
|              | \"Approved\" và thông báo thành công.                 |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu Reviewer hủy xác nhận, thao tác bị hủy bỏ.        |
| phụ**        |                                                       |
+--------------+-------------------------------------------------------+

\- Usecase 3:

+--------------+-------------------------------------------------------+
| **Use Case   | Từ chối bản dịch                                      |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Reviewer từ chối một bản dịch không đạt chất lượng và |
|              | cung cấp phản hồi.                                    |
+--------------+-------------------------------------------------------+
| **Điều       | Reviewer đang xem danh sách chờ duyệt.                |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Reviewer chọn một bản dịch và nhận thấy có lỗi.   |
| chính**      |                                                       |
|              | 2\. Reviewer nhấn nút \"Từ chối\".                    |
|              |                                                       |
|              | 3\. Hệ thống hiển thị form yêu cầu nhập lý do/phản    |
|              | hồi.                                                  |
|              |                                                       |
|              | 4\. Reviewer nhập phản hồi và xác nhận.               |
|              |                                                       |
|              | 5\. Hệ thống cập nhật trạng thái thành \"Rejected\",  |
|              | lưu lại phản hồi và thông báo thành công.             |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu không nhập lý do (nếu bắt buộc), hệ thống sẽ báo  |
| phụ**        | lỗi.                                                  |
+--------------+-------------------------------------------------------+

### Usecase của Admin

\- Usecase 1:

+--------------+-------------------------------------------------------+
| **Use Case   | Xem danh sách người dùng                              |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin xem danh sách tất cả các tài khoản trong hệ     |
|              | thống cùng với vai trò của họ.                        |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập.                                   |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin truy cập trang \"Quản lý người dùng\" từ    |
| chính**      | menu.                                                 |
|              |                                                       |
|              | 2\. Hệ thống truy vấn và hiển thị danh sách tất cả    |
|              | người dùng, bao gồm tên đăng nhập và vai trò (User,   |
|              | Translator, Admin).                                   |
+--------------+-------------------------------------------------------+
| **Luồng      | Không có.                                             |
| phụ**        |                                                       |
+--------------+-------------------------------------------------------+

\- Usecase 2:

+--------------+-------------------------------------------------------+
| **Use Case   | Thay đổi vai trò người dùng                           |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin thay đổi vai trò của một người dùng, ví dụ:     |
|              | chuyển một User thành Translator hoặc ngược lại.      |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập vào hệ thống.                      |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin truy cập vào mục \"Quản lý người dùng\" từ  |
| chính**      | menu.                                                 |
|              |                                                       |
|              | 2\. Hệ thống hiển thị danh sách tất cả người dùng và  |
|              | vai trò hiện tại của họ.                              |
|              |                                                       |
|              | 3\. Admin sử dụng công cụ tìm kiếm để tìm tài khoản   |
|              | người dùng cần thay đổi vai trò.                      |
|              |                                                       |
|              | 4\. Admin nhấn vào nút \"Thay đổi vai trò\" bên cạnh  |
|              | tài khoản người dùng đó.                              |
|              |                                                       |
|              | 5\. Hệ thống hiển thị một danh sách hoặc hộp thoại    |
|              | cho phép chọn vai trò mới (User hoặc Translator).     |
|              |                                                       |
|              | 6\. Admin chọn vai trò mới và nhấn \"Lưu\" hoặc \"Xác |
|              | nhận\".                                               |
|              |                                                       |
|              | 7\. Hệ thống cập nhật vai trò của người dùng trong    |
|              | Database.                                             |
|              |                                                       |
|              | 8\. Hệ thống hiển thị thông báo \"Thay đổi vai trò    |
|              | thành công\" và cập nhật lại thông tin trên danh      |
|              | sách.                                                 |
+--------------+-------------------------------------------------------+
| **Luồng      | \- Ràng buộc: Admin không thể thay đổi vai trò của    |
| phụ**        | chính tài khoản của mình để tránh tự khóa quyền.      |
+--------------+-------------------------------------------------------+

\- Usecase 3:

+--------------+-------------------------------------------------------+
| **Use Case   | Xóa tài khoản người dùng                              |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin xóa vĩnh viễn một tài khoản người dùng khỏi hệ  |
|              | thống.                                                |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập.                                   |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin truy cập mục \"Quản lý người dùng\".        |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị danh sách tất cả người dùng.    |
|              |                                                       |
|              | 3\. Admin tìm tài khoản người dùng cần xóa.           |
|              |                                                       |
|              | 4\. Admin nhấn vào nút \"Xóa\" bên cạnh tài khoản đó. |
|              |                                                       |
|              | 5\. Hệ thống hiển thị một hộp thoại cảnh báo, yêu cầu |
|              | xác nhận hành động xóa. Ví dụ: \"Bạn có chắc chắn     |
|              | muốn xóa vĩnh viễn tài khoản \[username\]? Hành động  |
|              | này không thể hoàn tác.\"                             |
|              |                                                       |
|              | 6\. Admin nhấn nút \"Xác nhận xóa\".                  |
|              |                                                       |
|              | 7\. Hệ thống xóa bản ghi của người dùng đó khỏi       |
|              | Database.                                             |
|              |                                                       |
|              | 8\. Hệ thống hiển thị thông báo \"Đã xóa tài khoản    |
|              | thành công\" và làm mới lại danh sách.                |
+--------------+-------------------------------------------------------+
| **Luồng      | \- Tại bước 6: Nếu Admin nhấn \"Hủy\", hành động xóa  |
| phụ**        | sẽ bị hủy bỏ.                                         |
|              |                                                       |
|              | \- Ràng buộc: Admin không thể xóa tài khoản của chính |
|              | mình.                                                 |
+--------------+-------------------------------------------------------+

### Usecase của Student

\- Usecase 1:

+--------------+-------------------------------------------------------+
| **Use Case   | Xem bản dịch                                          |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Khi truy cập một trang web học liệu, Student nhận     |
|              | được thông báo và xem bản dịch Tiếng Việt nếu có.     |
+--------------+-------------------------------------------------------+
| **Điều       | Student đã cài đặt và bật Extension.                  |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Student truy cập một trang web (ví dụ: trang      |
| chính**      | video trên Udemy).                                    |
|              |                                                       |
|              | 2\. Extension tự động trích xuất URL và các ID liên   |
|              | quan.                                                 |
|              |                                                       |
|              | 3\. Extension gửi yêu cầu lên Backend.                |
|              |                                                       |
|              | 4\. Nếu Backend tìm thấy bản dịch và bản dịch có      |
|              | trạng thái 'Approved', Extension hiển thị popup hỏi   |
|              | Student có muốn xem không.                            |
|              |                                                       |
|              | 5\. Nếu Student đồng ý, Extension sẽ hiển thị bản     |
|              | dịch (chèn phụ đề vào video).                         |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 4, nếu Backend không tìm thấy bản dịch,        |
| phụ**        | Extension không thực hiện hành động nào.              |
+--------------+-------------------------------------------------------+

\- Usecase 2:

+--------------+-------------------------------------------------------+
| **Use Case   | Bật/Tắt Extension                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Student bật hoặc tắt chức năng tự động tìm kiếm và    |
|              | hiển thị bản dịch của Extension.                      |
+--------------+-------------------------------------------------------+
| **Điều       | Student đã cài đặt Extension.                         |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Student nhấp vào biểu tượng của Extension trên    |
| chính**      | thanh công cụ trình duyệt.                            |
|              |                                                       |
|              | 2\. Hệ thống hiển thị một popup với một công tắc      |
|              | (toggle switch).                                      |
|              |                                                       |
|              | 3\. Student nhấp vào công tắc để chuyển trạng thái từ |
|              | Bật sang Tắt hoặc ngược lại.                          |
|              |                                                       |
|              | 4\. Extension lưu trạng thái mới và áp dụng cho tất   |
|              | cả các lần truy cập trang web sau đó.                 |
+--------------+-------------------------------------------------------+
| **Luồng      | Không có.                                             |
| phụ**        |                                                       |
+--------------+-------------------------------------------------------+

## Sơ đồ use case tổng quát của hệ thống

![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image3.png){width="5.94375in"
height="5.195833333333334in"}

**Hình 2 Sơ đồ use case tổng quát**

## Class Diagram

**Hình 3: Class
Diagram**![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image4.png){width="6.71875in"
height="5.65in"}

## Sequence Diagram

![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image5.png){width="6.726388888888889in"
height="4.758333333333334in"}

## Activity Diagram

![](vertopal_b8399742dc5b4f11b83d413e4b885254/media/image6.png){width="4.902777777777778in"
height="8.91388888888889in"}
