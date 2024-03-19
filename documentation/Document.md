![](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image1.png)

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

**[Giới thiệu tổng quan về dự án](#giới-thiệu-tổng-quan-về-dự-án)
[4](\l)**

> [Tóm tắt dự án](#tóm-tắt-dự-án) [4](\l)
>
> [Phạm vi của dự án](#phạm-vi-của-dự-án) [4](\l)

**[Yêu cầu và đặc tả dự án](#yêu-cầu-và-đặc-tả-dự-án) [4](\l)**

> [Yêu cầu chức năng](#yêu-cầu-chức-năng) [4](\l)
>
> [Yêu cầu phi chức năng](#yêu-cầu-phi-chức-năng) [4](\l)
>
> [Tính bảo mật](#tính-bảo-mật) [5](\l)
>
> [Tính sẵn sàng và khả năng đáp
> ứng](#tính-sẵn-sàng-và-khả-năng-đáp-ứng) [5](\l)
>
> [Hiệu suất](#hiệu-suất) [5](\l)
>
> [Đặc tả phần mềm](#đặc-tả-phần-mềm) [5](\l)

**[Kiến trúc và thiết kế phần mềm](#_heading=h.wx6yez1weppj) [5](\l)**

> [Kiến trúc phần mềm](#kiến-trúc-phần-mềm) [5](\l)
>
> [Usecase](#usecase) [6](\l)
>
> [Usecase của User](#usecase-của-user) [7](\l)
>
> [Usecase của Translator](#usecase-của-translator) [8](\l)
>
> [Usecase của Admin](#usecase-của-admin) [8](\l)
>
> [Usecase của Student](#usecase-của-student) [8](\l)
>
> [Sơ đồ use case tổng quát của hệ
> thống](#sơ-đồ-use-case-tổng-quát-của-hệ-thống) [8](\l)
>
> [Class Diagram](#class-diagram) [9](\l)
>
> [Senquence Diagram](#_heading=h.s5lpyvciae7u) [10](\l)
>
> [Activity Diagram](#activity-diagram) [10](#activity-diagram)

Tài liệu đặc tả

# Giới thiệu tổng quan về dự án

## Tóm tắt dự án

> **Hệ thống sẽ xây dựng:** Hệ thống cung cấp bản dịch Tiếng Việt cho
> các tài liệu/ video của khoá học.
>
> **Mục đích xây dựng hệ thống:** Hỗ trợ học viên Funix xem được tài
> liệu/ video bài giảng ở Tiếng Việt.
>
> **Giải quyết bài toán:**

-   Nguồn học liệu đa phần từ các khoá học trên các trang web MOOC ở
    ngôn ngữ Tiếng Anh

-   Nhiều học viên còn hạn chế về khả năng tiếng anh

> **Các mục tiêu:**

-   Xây dựng cơ sở dữ liệu lưu trữ thông tin các bản dịch

-   Website quản lý cho các translators thao tác để cung cấp bản dịch

-   Xây dựng extension để học viên có thể thêm vào Google Chrome phục vụ
    việc học tập

    1.  ## Phạm vi của dự án

> **Phạm vi về dịch vụ:**

-   Dịch vụ dịch thuật tài liệu/ video bài giảng sang Tiếng Việt

> **Phạm vị khách hàng:**

-   Học viên theo học tại Funix (\~30.000 học viên update 9/1/2024)

> **Phạm vi về nền tảng**/ **hệ** **thống:**

-   Website để translators cung cấp, quản lý nguồn bản dịch/ phụ đề

-   Extension hiển thị các bản dịch/ phụ đề tiếng việt cho học viên

# Yêu cầu và đặc tả dự án

## Yêu cầu chức năng

### Backend

> **Chức năng cho translators**

-   Chức năng upload/ download các bản dịch (file phụ đề/ docs)

-   Xem danh sách các bản dịch hiện có

-   Tìm kiếm các bản dịch theo các thuộc tính

-   Chỉnh sửa nội dung bản dịch

-   Xoá bản dịch

> **Chức năng cho admin**

-   Chuyển đổi vai trò user -- translator

-   Xoá tài khoản

### Extension

-   Chức năng bật/ tắt bản dịch tự động

## Yêu cầu phi chức năng

### Tính bảo mật 

-   Phải có tính bảo mật cao, dữ liệu được lưu trữ ở Database an toàn.
    Đồng thời bạn cũng cần các API Key hay Token mới có thể truy cập và
    chỉnh sửa dữ liệu ở Database.

### Tính sẵn sàng và khả năng đáp ứng

-   Làm việc 24/7, đáp ứng yêu cầu user và translator truy cập mọi thời
    gian khác nhau.

-   Extension được xây dựng để sử dụng chủ yếu trên trình duyệt Chrome
    của desktop.

-   Tự động hiển thị pop-up đề xuất bản dịch đối với các tài liệu/ bài
    giảng có sẵn.

### Hiệu suất

-   Có tốc độ ổn định, thời gian để hiển thị bản dịch tính từ khi học
    viên vào Website không được quá **1s**.

-   Thời gian để submit và thực hiện các thao tác của Translator cũng
    cần phải có tốc độ xử lý nhanh, trung bình mỗi thao tác không được
    quá** 0.5s**.

## Đặc tả phần mềm

-   Cơ sở dữ liệu được sử dụng là MySQL

-   Ngôn ngữ lập trình là Java

# Kiến trúc và thiết kế phần mềm

## Kiến trúc phần mềm

Kiến trúc phần mềm được sử dụng là Client -- Server, trong đó

Extension là "client software" trích xuất url các tài liệu, bài giảng
gửi request bản dịch đến sever.

Backend là "sever software" lưu trữ cơ sở dữ liệu với các bản dịch, truy
vấn cơ sở dữ liệu để gửi kết quả đến các client, cho phép translator
thao tác với cơ sở dữ liệu (thêm/ xửa/ xoá bản dịch).

## Usecase

### Usecase của User

![](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image2.png){width="6.727777777777778in"
height="2.1527777777777777in"}

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

### Usecase của Translator

![A diagram of a person with text Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image3.png){width="5.882341426071741in"
height="4.728094925634296in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Upload                                                |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator thêm các bản dịch mới vào cơ sở dữ liệu    |
|              | của hệ thống                                          |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống                  |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ menu trang web quản lý, chọn chức năng upload  |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị lựa chọn upload phụ đề video/   |
|              | bản dịch document.                                    |
|              |                                                       |
|              | 3\. Translator chọn loại file.                        |
|              |                                                       |
|              | 4\. Hệ thống hiển thị form upload tương ứng           |
|              |                                                       |
|              | 5\. Người dùng nhập metadata cho bản dịch             |
|              |                                                       |
|              | 6\. Người dùng upload file bản dịch                   |
|              |                                                       |
|              | 7\. Nếu các trường thông tin là đầy đủ và hợp lệ, cập |
|              | nhật thông tin vào hệ thống                           |
+--------------+-------------------------------------------------------+
| **Luồng      | 7b. Nếu các trường thông tin còn sai sót, file không  |
| phụ**        | hợp lệ,... hiển thị thông báo cho translator chỉnh    |
|              | sửa                                                   |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Xem danh sách                                         |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator xem danh sách các bản dịch có sẵn trong cơ |
|              | sở dữ liệu của hệ thống                               |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống                  |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ menu trang web quản lý, chọn chức năng xem     |
| chính**      | danh sách                                             |
|              |                                                       |
|              | 2\. Hệ thống hiển thị lựa chọn danh sách phụ đề       |
|              | video/ bản dịch document                              |
|              |                                                       |
|              | 3\. Lựa chọn loại bản dịch                            |
|              |                                                       |
|              | 4\. Hiển thị danh sách tương ứng                      |
+--------------+-------------------------------------------------------+
| **Luồng      | Không                                                 |
| phụ**        |                                                       |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Download                                              |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tải bản dịch từ cơ sở dữ liệu của hệ thống |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống, đang ở màn hình |
| kiện**       | danh sách bản dịch                                    |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ danh sách bản dịch, translator click vào link  |
| chính**      | download                                              |
|              |                                                       |
|              | 2\. Hệ thống hiển thị màn hình chọn nơi lưu file,     |
|              | loại file muốn lưu                                    |
|              |                                                       |
|              | 3\. Người dùng lựa chọn và bấm tải file               |
|              |                                                       |
|              | 4\. Hệ thống hiển thị thông báo đã tải thành công     |
+--------------+-------------------------------------------------------+
| **Luồng      | 4b. Nếu gặp lỗi khi tải về (trùng tên file, hết ổ),   |
| phụ**        | hiển thị thông báo cho translator                     |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Tìm kiếm bản dịch                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tìm kiếm các bản dịch theo các thuộc tính  |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống, đang ở màn hình |
| kiện**       | danh sách bản dịch                                    |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ màn hình danh sách bản dịch, translator click  |
| chính**      | vào biểu tượng filter                                 |
|              |                                                       |
|              | 2\. Hệ thống hiển thị các ô nhập các thuộc tính: Tên  |
|              | bản dịch, Url, Người dịch, Course ID, Video ID.       |
|              |                                                       |
|              | 3\. Translator nhập các thuộc tính theo ý muốn và     |
|              | click "Lọc"                                           |
|              |                                                       |
|              | 4\. Hệ thống tìm kiếm cơ sở dữ liệu và hiển thị danh  |
|              | sách các bản dịch khớp với yêu cầu.                   |
+--------------+-------------------------------------------------------+
| **Luồng      | # 4b. Nếu không thấy bản ghi nào hợp lệ,              |
| phụ**        |  thông báo cho translator {#b.-nếu-không-thấy-bản-ghi |
|              | -nào-hợp-lệ-thông-báo-cho-translator .list-paragraph} |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Chỉnh sửa bản dịch                                    |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator chỉnh sửa bản dịch có sẵn trong cơ sở dữ   |
|              | liệu của hệ thống                                     |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống, đang ở màn hình |
| kiện**       | danh sách bản dịch                                    |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ màn hình danh sách bản dịch, người dùng click  |
| chính**      | link "edit" của bản dịch muốn sửa.                    |
|              |                                                       |
|              | 2\. Hệ thống hiển thị form thông tin của bản dịch     |
|              | hiện tại                                              |
|              |                                                       |
|              | 3\. Translator chỉnh sửa các trưởng thông tin         |
|              | metadata muốn sửa                                     |
|              |                                                       |
|              | 4\. Translator bấm lưu                                |
|              |                                                       |
|              | 5\. Nếu các trường thông tin là đầy đủ và hợp lệ, cập |
|              | nhật thông tin vào hệ thống                           |
+--------------+-------------------------------------------------------+
| **Luồng      | # 3b. Translator chọn reup file dịch                  |
| phụ**        |  {#b.-translator-chọn-reup-file-dịch .list-paragraph} |
|              |                                                       |
|              | 4b. Hệ thống hiển thị pop-up để translator chọn file  |
|              | mới                                                   |
|              |                                                       |
|              | 5b. Translator chọn file thay thế và click upload     |
|              |                                                       |
|              | 6b. Quay lại bước 4 luồng chính                       |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Xoá bản dịch                                          |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator xoá các bản dịch khỏi cơ sở dữ liệu của hệ |
|              | thống                                                 |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống, đang ở màn hình |
| kiện**       | danh sách bản dịch                                    |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Từ màn hình danh sách bản dịch, translator click  |
| chính**      | vào link "delete" cạnh bản dịch muốn xoá              |
|              |                                                       |
|              | 2\. Hệ thống hiển thị cảnh báo "bạn chắc chắn muốn    |
|              | xoá?"                                                 |
|              |                                                       |
|              | 3\. Translator chọn "Đồng ý"                          |
|              |                                                       |
|              | 4\. Hệ thống xoá bản dịch khỏi cơ sở dữ liệu và thông |
|              | báo xoá thành công                                    |
+--------------+-------------------------------------------------------+
| **Luồng      | # 3b. Translator                                      |
| phụ**        |  chọn "Huỷ" {#b.-translator-chọn-huỷ .list-paragraph} |
|              |                                                       |
|              | 4b. Hệ thống quay lại hiển thị danh sách bản dịch     |
+--------------+-------------------------------------------------------+

### Usecase của Admin

![A diagram of a foreign language Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image4.png){width="4.550007655293088in"
height="2.6047003499562553in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Xoá tài khoản                                         |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin xoá các tài khoản khỏi hệ thống                 |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập thành công vào hệ thống, ở màn     |
| kiện**       | hình danh sách tài khoản                              |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin chọn link "delete" cạnh tài khoản muốn xoá  |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị cảnh báo "bạn chắc chắn muốn    |
|              | xoá?"                                                 |
|              |                                                       |
|              | 3\. Admin chọn "Đồng ý"                               |
|              |                                                       |
|              | 4\. Hệ thống xoá tài khoản khỏi cơ sở dữ liệu và      |
|              | thông báo xoá thành công                              |
+--------------+-------------------------------------------------------+
| **Luồng      | # 3b.                                                 |
| phụ**        | Admin chọn "Huỷ" {#b.-admin-chọn-huỷ .list-paragraph} |
|              |                                                       |
|              | 4b. Hệ thống quay lại hiển thị danh sách tài khoản    |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Đổi vai trò translator -- user                        |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin thực hiện thêm hoặc bớt quyền cho tài khoản     |
|              | (giữa user -- translator)                             |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập thành công vào hệ thống, ở màn     |
| kiện**       | hình danh sách tài khoản                              |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin chọn link "role" cạnh tài khoản muốn xoá    |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị lựa chọn vai trò translator/    |
|              | user.                                                 |
|              |                                                       |
|              | 3\. Admin chọn vai trò mới cho tài khoản và ấn "lưu"  |
|              |                                                       |
|              | 4\. Hệ thống cập nhật thông tin vào cơ sở dữ liệu     |
+--------------+-------------------------------------------------------+
| **Luồng      | # 3b. Ad                                              |
| phụ**        | min chọn "huỷ" {#b.-admin-chọn-huỷ-1 .list-paragraph} |
|              |                                                       |
|              | 4b. Hệ thống quay lại hiển thị danh sách tài khoản    |
+--------------+-------------------------------------------------------+

### Usecase của Student

![A black and white image of a circle with a arrow pointing to the
center Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image5.png){width="5.125in"
height="2.5in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Bật bản dịch                                          |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Student thực hiện áp dụng bản dịch/ phụ đề đối với    |
|              | tài liệu/ bàig giảng                                  |
+--------------+-------------------------------------------------------+
| **Điều       | Student đã cài đặt và kích hoạt extension FUNiX       |
| kiện**       | Passport                                              |
|              |                                                       |
|              | Student mở các video, tài liệu của khoá học có sẵn    |
|              | trong cơ sở dữ liệu của hệ thống                      |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Hệ thống tìm kiếm bản dịch trong yêu cầu nhận     |
| chính**      | được từ Extension                                     |
|              |                                                       |
|              | 2\. Nếu thấy, hệ thống hiển thị pop-up hỏi student có |
|              | muốn áp dụng bản dịch không.                          |
|              |                                                       |
|              | 3\. Student chọn "Phụ đề"                             |
|              |                                                       |
|              | 4\. Hệ thống áp dụng bản dịch/ phụ đề lên tài liệu/   |
|              | video                                                 |
+--------------+-------------------------------------------------------+
| **Luồng      | # 3b. Student chọn "Keep org                          |
| phụ**        | inal" {#b.-student-chọn-keep-orginal .list-paragraph} |
|              |                                                       |
|              | 4b. Thoát pop-up, hiển thị tài liệu/ video nguyên bản |
+--------------+-------------------------------------------------------+

### Use case của Reviewer

![A diagram of a person with text Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image6.png){width="3.6805555555555554in"
height="3.7777777777777777in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Kiểm tra bản dịch                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Reviewer kiểm tra xem các Translator đã dịch video    |
|              | đúng chưa, nếu đúng rồi thì mới hiển thị ra cho User. |
+--------------+-------------------------------------------------------+
| **Điều       | Reviewer đã đăng nhập vào hệ thống, mở danh sách bản  |
| kiện**       | dịch                                                  |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Reviewer click vào bản dịch muốn kiểm tra         |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị nội dung bản dịch               |
|              |                                                       |
|              | 3\. Reviewer click xác nhận bản dịch đã đúng          |
|              |                                                       |
|              | 4\. Hệ thống cập nhật trạng thái bản dịch là          |
|              | "checked"                                             |
+--------------+-------------------------------------------------------+
| **Luồng      | 3b. Reviewer xác nhận bản dịch sai sót                |
| phụ**        |                                                       |
|              | 4b. Hệ thống cập nhật trạng thái của bản dịch là      |
|              | "update neeeded" -- cần translator cập nhật lại.      |
+--------------+-------------------------------------------------------+

## Sơ đồ use case tổng quát của hệ thống

![A diagram of a person\'s connection Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image7.png){width="6.727777777777778in"
height="5.231944444444444in"}

**Hình 2 Sơ đồ use case tổng quát**

## Class Diagram

![A diagram of a language Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image8.png){width="6.727777777777778in"
height="5.711805555555555in"}

[]{#_heading=h.s5lpyvciae7u .anchor}**Hình 3: Class Diagram**

## Sequence Diagram

Sequence Diagram cho hoạt động kiểm tra và hiển thị bản dịch của
Extension

**Cơ chế hoạt động:**

> 1\. Khi truy cập vào một trang web bất kỳ, Extension sẽ trích xuất ra
> url của trang web đó. Từ đó sẽ lấy ra được các thông tin như video_id
> hay course_id. 

2\. Extension gửi request lên Backend với các dữ liệu tưng ứng đã trích
xuất được:

\- Nếu đó là trang web thuộc các nguồn MOOC: gửi
lên **course_id** và **video_id** để tìm phụ đề.

\- Còn lại sẽ là tìm dịch Document: gửi lên toàn bộ url để tìm bản dịch
do Document đó.

3\. Backend sẽ trả về bản dịch với thông tin tương ứng (nếu có).

> 4\. Sau khi nhận dữ liệu trả về từ Backend, nêu như có bản dịch thì
> Extension sẽ hiển thị popup cho người dùng để lựa chọn xem có muốn
> dịch không.

![A diagram of a diagram Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image9.png){width="5.836170166229222in"
height="4.5030314960629925in"}

**Hình: Sequence Diagram cho hoạt động kiểm tra và hiển thị bản dịch của
Extension**

## Activity Diagram

Vẽ Activity Diagram cho thao tác bật mở Extension của học viên

![A diagram of a flowchart Description automatically
generated](vertopal_674e5db98bdb42b1a7ee012d17062b7f/media/image10.png){width="6.077543744531933in"
height="3.7777777777777777in"}

**Hình: Ativity Diagram cho thao tác mở Extension của học viên**
