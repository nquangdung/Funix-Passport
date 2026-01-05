![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image1.png)

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

1.  # Giới thiệu tổng quan về dự án

    1.  ## Tóm tắt dự án

-   **Hệ thống sẽ xây dựng:** Dự án tập trung phát triển hệ thống
    **FUNiX Passport**, một giải pháp công nghệ toàn diện bao gồm hai
    thành phần chính:

```{=html}
<!-- -->
```
-   **Backend:** Hệ thống quản trị tập trung giúp lưu trữ và quản lý các
    bản dịch thuật, phụ đề video và tài liệu học tập.

-   **Extension:** Một tiện ích mở rộng trên trình duyệt Chrome đóng vai
    trò là giao diện tương tác, giúp kết nối và hiển thị dữ liệu từ
    Backend đến người dùng cuối.

```{=html}
<!-- -->
```
-   **Mục đích xây dựng hệ thống:**

```{=html}
<!-- -->
```
-   **Hỗ trợ đắc lực cho sinh viên:** Hệ thống được thiết kế nhằm giúp
    học viên dễ dàng tiếp thu kiến thức từ các video bài giảng và tài
    liệu chuyên ngành bằng tiếng Việt.

-   **Giải quyết rào cản ngôn ngữ:** FUNiX Passport giải quyết bài toán
    khó khăn khi sinh viên phải đối mặt với các học liệu tiếng Anh phức
    tạp trên các nền tảng MOOC, giúp việc học tập trở nên hiệu quả và
    trực quan hơn thay vì chỉ dựa vào phụ đề tiếng Anh có sẵn.

```{=html}
<!-- -->
```
-   **Các mục tiêu xây dựng dự án:**

```{=html}
<!-- -->
```
-   **Xây dựng cơ sở dữ liệu tối ưu:** Thiết lập hệ quản trị dữ liệu
    chặt chẽ để quản lý danh mục môn học, liên kết video, và thông tin
    truy cập của người dùng.

-   **Tự động hóa quy trình hiển thị:** Phát triển cơ chế trích xuất URL
    và định danh video tự động để cung cấp bản dịch tương ứng cho sinh
    viên ngay tức thì.

-   **Đảm bảo tiêu chuẩn kỹ thuật cao:** Hệ thống phải đạt được tính bảo
    mật thông tin tuyệt đối, đồng thời tối ưu hóa hiệu suất với thời
    gian phản hồi cực nhanh (dưới 1 giây cho Extension và dưới 0.5 giây
    cho các thao tác quản trị).

-   **Thân thiện với người dùng:** Xây dựng giao diện đơn giản, tinh tế,
    đảm bảo người dùng không cần am hiểu sâu về công nghệ vẫn có thể sử
    dụng dễ dàng.

    1.  ## Phạm vi của dự án

```{=html}
<!-- -->
```
-   **Phạm vi về dịch vụ:**

```{=html}
<!-- -->
```
-   **Cung cấp giải pháp dịch thuật học thuật:** Hệ thống tập trung vào
    việc cung cấp phụ đề tiếng Việt cho các video bài giảng và các bản
    dịch tài liệu từ các nguồn tài liệu quốc tế.

-   **Quản lý dữ liệu tập trung (Backend):** Lưu trữ và quản lý Metadata
    của các bản dịch, bao gồm thông tin dịch giả, thời gian upload, URL
    nguồn, và các tệp tin phụ đề/tài liệu tương ứng.

-   **Tương tác thời gian thực (Extension):** Tiện ích mở rộng sẽ tự
    động nhận diện nội dung trên trang web học tập, truy vấn dữ liệu từ
    Backend và hiển thị bản dịch thông qua giao diện popup hoặc phụ đề
    chèn trực tiếp.

-   **Hệ thống phân quyền (User Management):** Dịch vụ bao gồm việc quản
    lý các nhóm người dùng khác nhau như User (Sinh viên), Translator
    (Dịch giả), và Admin (Quản trị viên) với các chức năng tương ứng.

```{=html}
<!-- -->
```
-   **Phạm vi về khách hàng:**

```{=html}
<!-- -->
```
-   **Người dùng cuối (Students):** Đối tượng trọng tâm là sinh viên
    FUNiX đang theo học các chương trình trên nền tảng MOOC, những người
    có nhu cầu tiếp cận kiến thức bằng ngôn ngữ mẹ đẻ để tối ưu hóa việc
    tiếp thu.

-   **Đội ngũ dịch thuật (Translators):** Các cộng tác viên thực hiện
    việc chuyển ngữ và đóng góp nội dung cho hệ thống.

-   **Quản trị viên hệ thống (Admins):** Nhân sự phụ trách điều phối tài
    khoản và đảm bảo sự vận hành ổn định của cơ sở dữ liệu.

```{=html}
<!-- -->
```
-   **Phạm vi về nền tảng/hệ thống:**

```{=html}
<!-- -->
```
-   **Nền tảng người dùng:** Tiện ích mở rộng (Extension) được thiết kế
    để vận hành tối ưu và chủ yếu trên trình duyệt **Google Chrome**.

-   **Hệ thống máy chủ:** Thành phần Backend xử lý các yêu cầu thông qua
    API, đảm bảo tốc độ phản hồi nhanh và tính bảo mật dữ liệu cao bằng
    API Key hoặc Token.

-   **Môi trường ứng dụng:** Hệ thống hỗ trợ tích hợp trên các trang web
    giáo dục trực tuyến (MOOC) và các website tài liệu học thuật bất kỳ
    có trong danh mục quản lý của Backend.

2.  # Yêu cầu và đặc tả dự án

    1.  ## Yêu cầu chức năng

Hệ thống FUNiX Passport được thiết kế với các chức năng phân định rõ
ràng cho từng nhóm đối tượng người dùng nhằm đảm bảo quy trình quản lý
và cung cấp bản dịch diễn ra thông suốt.

A. Chức năng dành cho nhóm quản trị và dịch thuật (Backend)

  ---------------------------------------------------------------------------
  Actor        Tên chức năng         Mô tả hoạt động
  ------------ --------------------- ----------------------------------------
  User         Đăng nhập/Đăng xuất   Cho phép người dùng truy cập vào hệ
                                     thống để sử dụng các tính năng cơ bản
                                     hoặc thoát khỏi ứng dụng để đảm bảo an
                                     toàn tài khoản.

  Translator   Upload phụ đề Video   Translator nhập thông tin (Tên video,
                                     URL, Course ID, Video ID), đính kèm file
                                     phụ đề và gửi lên hệ thống để lưu trữ
                                     vào Database.

  Translator   Upload tài liệu       Tương tự video, Translator nhập Tên bản
               (Document)            dịch, URL tài liệu, đính kèm file
                                     Document đã dịch và lưu vào hệ thống.

  Translator   Quản lý Dashboard     Hiển thị danh sách các bản dịch phụ đề
                                     và tài liệu đã upload; cho phép xem
                                     thống kê và truy cập nhanh vào tệp tin.

  Translator   Tìm kiếm & Bộ lọc     Tìm kiếm bản dịch theo các tiêu chí:
                                     Tên, URL, Người dịch, Course ID hoặc
                                     Video ID.

  Translator   Chỉnh sửa bản dịch    Cho phép thay đổi các metadata (thông
                                     tin mô tả) hoặc tải lên file mới (Reup)
                                     để thay thế bản dịch cũ.

  Translator   Xóa bản dịch          Loại bỏ hoàn toàn các file phụ đề hoặc
                                     tài liệu khỏi hệ thống khi không còn cần
                                     thiết.

  Translator   Tải xuống file dịch   Cho phép dịch thuật viên tải về các file
                                     đã upload để kiểm tra hoặc lưu trữ cục
                                     bộ.

  Admin        Quản lý tài khoản     Thực hiện xóa tài khoản người dùng khỏi
                                     hệ thống khi có yêu cầu hoặc vi phạm
                                     chính sách.

  Admin        Phân quyền người dùng Cấp quyền (User thành Translator) hoặc
                                     thu hồi quyền (Translator về User) để
                                     quản lý đội ngũ nhân sự.

  Reviewer     Kiểm duyệt bản dịch   Kiểm tra nội dung dịch thuật từ
                                     Translator; phê duyệt để hiển thị công
                                     khai hoặc yêu cầu chỉnh sửa lại.
  ---------------------------------------------------------------------------

B. Chức năng dành cho sinh viên (Extension)

  ------------------------------------------------------------------------
  Actor     Tên chức năng         Mô tả hoạt động
  --------- --------------------- ----------------------------------------
  Student   Tự động nhận diện URL Khi truy cập trang web, Extension trích
                                  xuất URL và ID để xác định xem trang đó
                                  có hỗ trợ bản dịch hay không.

  Student   Truy vấn bản dịch     Gửi yêu cầu (Request) lên Backend để tìm
                                  kiếm phụ đề hoặc tài liệu tương ứng với
                                  nội dung đang xem.

  Student   Hiển thị Popup lựa    Nếu có bản dịch, hệ thống hiển thị thông
            chọn                  báo hỏi người dùng có muốn sử dụng bản
                                  dịch tiếng Việt hay không.

  Student   Hiển thị bản dịch     Trình chiếu phụ đề tiếng Việt lên video
                                  hoặc hiển thị nội dung tài liệu dịch khi
                                  học viên đồng ý.

  Student   Bật/Tắt Extension     Cho phép người dùng chủ động kích hoạt
                                  hoặc tạm dừng hoạt động của tiện ích
                                  thông qua giao diện cài đặt.
  ------------------------------------------------------------------------

## Yêu cầu phi chức năng

### 2.2.1 Tính bảo mật

> Đây là yêu cầu hàng đầu để bảo vệ tài sản dữ liệu và quyền riêng tư
> của người dùng.

-   **An toàn dữ liệu:** Hệ thống phải đảm bảo tính bảo mật cao và dữ
    liệu được lưu trữ an toàn trong Database.

-   **Kiểm soát truy cập:** Việc truy cập hoặc chỉnh sửa dữ liệu tại
    Database bắt buộc phải có API Key hoặc Token hợp lệ.

-   **Phân quyền hệ thống:** Xác định rõ ràng các hạn chế về quyền sử
    dụng sản phẩm dựa trên vai trò (User, Translator, Admin) để ngăn
    chặn việc truy cập trái phép vào các chức năng quản trị.

-   **Mã hóa thông tin:** (Bổ sung) Sử dụng giao thức HTTPS/SSL để mã
    hóa dữ liệu truyền tải giữa Extension và Backend, đảm bảo các
    Metadata không bị đánh cắp trong quá trình Request.

### 2.2.2 Tính sẵn sàng và khả năng đáp ứng

> Đảm bảo sinh viên có thể học tập mọi lúc, mọi nơi mà không bị gián
> đoạn.

-   **Thời gian hoạt động:** Hệ thống cần đảm bảo khả năng làm việc liên
    tục 24/7 để phục vụ nhu cầu xem bài giảng của học viên bất kể khung
    giờ nào.

-   **Khả năng đáp ứng đa người dùng:** Hệ thống phải luôn sẵn sàng tiếp
    nhận và phản hồi yêu cầu từ nhiều học viên và dịch thuật viên tại
    các thời điểm khác nhau.

-   **Tính ổn định:** (Bổ sung) Hệ thống cần có cơ chế dự phòng (Backup)
    dữ liệu định kỳ để đảm bảo không mất mát thông tin khi có sự cố kỹ
    thuật bất ngờ.

### 2.2.3 Hiệu suất

> Yêu cầu về tốc độ xử lý là điểm nhấn quan trọng giúp tăng trải nghiệm
> người dùng.

-   **Tốc độ ổn định:** Hệ thống phải duy trì tốc độ vận hành ổn định
    trong mọi điều kiện truy cập.

-   **Thời gian phản hồi cho học viên:** Thời gian để hiển thị bản dịch
    kể từ khi học viên vào Website không được vượt quá **1 giây**.

-   **Tốc độ xử lý quản trị:** Thời gian để thực hiện các thao tác của
    Translator (như Submit file) cần đạt tốc độ trung bình không quá
    **0.5 giây** cho mỗi thao tác.

-   **Tương thích trình duyệt:** Extension được xây dựng để hoạt động
    tối ưu và mượt mà nhất trên trình duyệt Google Chrome.

-   **Khả năng chịu tải:** (Bổ sung) Backend cần có khả năng xử lý ít
    nhất 500 yêu cầu đồng thời (Concurrent requests) mà không làm tăng
    độ trễ (Latency) vượt mức quy định.

    1.  ## Đặc tả phần mềm

# Dựa trên cấu trúc của hệ thống FUNiX Passport, các đặc tả phần mềm cần thiết bao gồm: {#dựa-trên-cấu-trúc-của-hệ-thống-funix-passport-các-đặc-tả-phần-mềm-cần-thiết-bao-gồm .list-paragraph}

**2.3.1 Nền tảng và Môi trường vận hành**

-   **Trình duyệt mục tiêu:** Tiện ích mở rộng (Extension) được đặc tả
    để chạy chủ yếu trên nền tảng trình duyệt Google Chrome.

-   **Hệ điều hành:** Hệ thống cần tương thích với các hệ điều hành phổ
    biến có hỗ trợ trình duyệt Chrome như Windows, macOS và Linux.

-   **Cơ sở dữ liệu (Database):** Backend sử dụng hệ quản trị cơ sở dữ
    liệu để lưu trữ và quản lý Metadata cho các bản dịch video và tài
    liệu.

**2.3.2 Đặc tả dữ liệu (Metadata Specification)**

Hệ thống yêu cầu các cấu trúc dữ liệu cụ thể cho từng loại bản dịch để
đảm bảo tính nhất quán:

-   **Bản dịch Video:** Phải chứa các trường thông tin bắt buộc như ID
    (tự động), Translator (tự động), UploadedDate (tự động), Name, URL,
    Video ID, Course ID, và đường dẫn tệp (VI Subtitle URL).

-   **Bản dịch Document:** Phải chứa các trường như ID, Translator,
    UploadedDate, Name, URL và Document URL.

**2.3.3 Giao tiếp và Bảo mật hệ thống**

-   **Cơ chế giao tiếp:** Extension sử dụng phương thức gửi yêu cầu
    (Request) lên Backend kèm theo các tham số trích xuất được (như
    video_id hoặc course_id) để truy vấn dữ liệu.

-   **Xác thực và Ủy quyền:** Hệ thống đặc tả việc sử dụng API Key hoặc
    Token như một điều kiện bắt buộc để truy cập và chỉnh sửa dữ liệu
    trong Database.

**2.3.4 Đặc tả bổ sung (Đề xuất)**

Để tăng tính ổn định và khả năng mở rộng, thầy đề xuất thêm các đặc tả
sau:

-   **Định dạng dữ liệu API:** Sử dụng định dạng **JSON** cho mọi phản
    hồi từ Backend về Extension để đảm bảo tốc độ truyền tải nhanh và dễ
    phân tích dữ liệu.

-   **Lưu trữ cục bộ (Local Storage):** Extension sử dụng Chrome Storage
    API để lưu trữ các trạng thái cài đặt (Bật/Tắt) của người dùng ngay
    trên trình duyệt.

-   **Xử lý tệp tin:** Hệ thống cần đặc tả các định dạng tệp phụ đề hỗ
    trợ (ví dụ: .srt, .vtt) và định dạng tài liệu (ví dụ: .pdf, .docx)
    để Translator có thể upload chính xác.

3.  # Kiến trúc và thiết kế phần mềm

    1.  ## Kiến trúc phần mềm

**3.1.1 Lựa chọn kiến trúc: Client-Server Architecture (Mô hình Khách -
Chủ)**

Dựa trên các yêu cầu và đặc điểm của dự án, em đề xuất sử dụng kiến trúc
**Client-Server** (cụ thể là mô hình Web Service thông qua RESTful API)
cho hệ thống FUNiX Passport.

Trong mô hình này:

-   **Client (Phía khách):** Chính là tiện ích mở rộng (**Extension**)
    chạy trên trình duyệt Chrome của sinh viên.

-   **Server (Phía chủ):** Là hệ thống **Backend** chịu trách nhiệm xử
    lý logic nghiệp vụ và quản lý cơ sở dữ liệu tập trung.

**3.1.2 Lý do lựa chọn kiến trúc**

Việc lựa chọn kiến trúc Client-Server thay vì các kiến trúc khác (như
Monolithic hay Peer-to-Peer) dựa trên các lý do thực tế sau:

-   **Tách biệt trách nhiệm (Separation of Concerns):** Hệ thống có hai
    thành phần hoạt động trên các môi trường hoàn toàn khác nhau:
    Extension chạy trên trình duyệt và Backend chạy trên máy chủ. Kiến
    trúc này giúp đội ngũ phát triển có thể nâng cấp giao diện Extension
    mà không làm ảnh hưởng đến cấu trúc dữ liệu bên dưới của Backend.

-   **Tối ưu hóa hiệu suất (Performance Optimization):** Đề bài yêu cầu
    thời gian hiển thị bản dịch dưới **1 giây**. Bằng cách sử dụng
    Client-Server, Extension (Client) chỉ đảm nhận việc hiển thị và
    trích xuất URL nhẹ nhàng, trong khi các truy vấn dữ liệu phức tạp
    được đẩy về Server có cấu hình mạnh xử lý, đảm bảo tốc độ phản hồi
    nhanh nhất.

-   **Tăng cường tính bảo mật:** Dự án yêu cầu bảo mật dữ liệu cao và sử
    dụng API Key/Token. Kiến trúc Client-Server cho phép thiết lập một
    \"trạm gác\" bảo mật tập trung tại Backend. Toàn bộ dữ liệu nhạy cảm
    được lưu trữ an toàn trong Database phía sau Server, chỉ những
    Request có Token hợp lệ từ Client mới được phép truy xuất.

-   **Khả năng mở rộng (Scalability):** Hệ thống phục vụ nhiều đối tượng
    từ Student, Translator đến Admin. Mô hình này cho phép Server phục
    vụ hàng ngàn Client (Extension) cùng lúc. Khi lượng sinh viên tăng
    lên, chúng ta chỉ cần nâng cấp tài nguyên cho Server mà không cần
    yêu cầu sinh viên phải thay đổi thiết bị hay cài đặt phức tạp.

-   **Phù hợp với đặc thù Extension:** Extension về bản chất là một ứng
    dụng nhỏ cần kết nối từ xa để lấy dữ liệu. Client-Server là kiến
    trúc tiêu chuẩn và hiệu quả nhất để các tiện ích trình duyệt giao
    tiếp với cơ sở dữ liệu bên ngoài.

    1.  ## Usecase

**3.2.0 Danh sách Use Case cho các Actor**

Dưới đây là các chức năng cụ thể được bóc tách từ yêu cầu dự án:

-   **Actor: User**

    -   Đăng nhập hệ thống.

    -   Đăng xuất hệ thống.

-   **Actor: Translator (Dịch thuật viên)**

    -   Upload file phụ đề video (bao gồm: Nhập Metadata và Đính kèm
        file).

    -   Upload file Document (bao gồm: Nhập Metadata và Đính kèm file).

    -   Xem Dashboard (Bản dịch phụ đề và tài liệu).

    -   Tải xuống file dịch.

    -   Tìm kiếm bản dịch theo bộ lọc.

    -   Xóa bản dịch.

    -   Chỉnh sửa Metadata của file dịch.

    -   Reup (Tải lên lại) file dịch khác.

-   **Actor: Admin (Quản trị viên)**

    -   Xóa tài khoản người dùng.

    -   Thêm quyền Translator cho User.

    -   Xóa quyền Translator của người dùng.

-   **Actor: Student (Học viên - Người dùng Extension)**

    -   Bật/Tắt Extension qua giao diện cài đặt.

    -   Lựa chọn dịch nội dung (qua Popup).

-   **Actor: Reviewer (Người kiểm duyệt - Actor nâng cao)**

    -   Phê duyệt bản dịch.

    -   Yêu cầu chỉnh sửa bản dịch.

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image2.png){width="6.727777777777778in"
height="1.9444444444444444in"}

### Usecase của User

**Use Case mẫu:**

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image3.png){width="6.727777777777778in"
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

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image4.png){width="3.9930555555555554in"
height="0.8541666666666666in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Upload file phụ đề                                    |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tải lên file phụ đề tiếng Việt kèm theo    |
|              | các thông tin định danh video                         |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã đăng nhập vào hệ thống và có quyền dịch |
| kiện**       | thuật                                                 |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator truy cập màn hình Upload phụ đề.       |
| chính**      |                                                       |
|              | 2\. Hệ thống hiển thị form nhập thông tin.            |
|              |                                                       |
|              | 3\. Translator nhập Metadata: Tên Video, URL, Course  |
|              | ID, Video ID.                                         |
|              |                                                       |
|              | 4\. Translator đính kèm file phụ đề đã dịch.          |
|              |                                                       |
|              | 5\. Translator nhấn Submit; hệ thống lưu dữ liệu vào  |
|              | Database.                                             |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 3 hoặc 4, nếu thiếu thông tin bắt buộc hoặc    |
| phụ**        | định dạng file không đúng, hệ thống hiển thị thông    |
|              | báo lỗi và yêu cầu nhập lại.                          |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Tìm kiếm bản dịch và lọc                              |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Translator tìm lại các bản dịch đã tải lên thông qua  |
|              | các tiêu chí lọc                                      |
+--------------+-------------------------------------------------------+
| **Điều       | Hệ thống đã có dữ liệu bản dịch trong Database        |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator truy cập Dashboard.                    |
| chính**      |                                                       |
|              | 2\. Translator nhập từ khóa vào bộ lọc: Tên, URL,     |
|              | Người dịch, Course ID hoặc Video ID.                  |
|              |                                                       |
|              | 3\. Hệ thống truy xuất và hiển thị danh sách kết quả  |
|              | tương ứng.                                            |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu không tìm thấy kết quả, hệ thống hiển thị thông   |
| phụ**        | báo \"Không tìm thấy bản dịch phù hợp\"               |
+--------------+-------------------------------------------------------+

+--------------+-------------------------------------------------------+
| **Use Case   | Chỉnh sửa và Reup                                     |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Thay đổi thông tin mô tả hoặc thay thế tệp dịch cũ    |
|              | bằng tệp mới                                          |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã tìm thấy bản dịch cần sửa thông qua bộ  |
| kiện**       | lọc                                                   |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Translator chọn bản dịch cần sửa và nhấn          |
| chính**      | \"Edit\".                                             |
|              |                                                       |
|              | 2\. Translator lựa chọn: Chỉnh sửa Metadata (tên,     |
|              | id\...) hoặc chọn \"Reup\" để chọn tệp mới.           |
|              |                                                       |
|              | 3\. Hệ thống cập nhật thông tin mới vào Database.     |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu quá trình upload tệp mới thất bại, hệ thống giữ   |
| phụ**        | nguyên phiên bản cũ và báo lỗi.                       |
+--------------+-------------------------------------------------------+

### Usecase của Admin

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image5.png){width="3.888888888888889in"
height="0.8541666666666666in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Phân quyền người dùng                                 |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin thay đổi vai trò của người dùng từ User thành   |
|              | Translator hoặc ngược lại để quản lý đội ngũ dịch     |
|              | thuật.                                                |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập vào hệ thống quản trị (Backend).   |
| kiện**       |                                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin truy cập vào danh sách người dùng.          |
| chính**      |                                                       |
|              | 2\. Admin tìm kiếm và chọn tài khoản cần thay đổi     |
|              | quyền.                                                |
|              |                                                       |
|              | 3\. Admin nhấn chọn \"Thêm quyền\" hoặc \"Xóa quyền\" |
|              | Translator.                                           |
|              |                                                       |
|              | 4\. Hệ thống cập nhật vai trò mới vào Database và     |
|              | hiển thị thông báo thành công.                        |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 2, nếu không tìm thấy người dùng, hệ thống     |
| phụ**        | hiển thị thông báo \"Người dùng không tồn tại\".      |
+--------------+-------------------------------------------------------+

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image6.png){width="3.888888888888889in"
height="0.8541666666666666in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Xóa tài khoản người dùng                              |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Admin thực hiện xóa vĩnh viễn tài khoản của một người |
|              | dùng ra khỏi hệ thống.                                |
+--------------+-------------------------------------------------------+
| **Điều       | Admin đã đăng nhập và người dùng cần xóa phải đang    |
| kiện**       | tồn tại trong hệ thống.                               |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Admin truy cập vào danh sách tài khoản.           |
| chính**      |                                                       |
|              | 2\. Admin chọn tài khoản muốn xóa.                    |
|              |                                                       |
|              | 3\. Hệ thống hiển thị cảnh báo xác nhận xóa.          |
|              |                                                       |
|              | 4\. Admin xác nhận; hệ thống xóa dữ liệu tài khoản    |
|              | trong Database.                                       |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 4, nếu Admin chọn \"Hủy\", hệ thống sẽ quay    |
| phụ**        | lại danh sách và không thực hiện lệnh xóa.            |
+--------------+-------------------------------------------------------+

### Usecase của Student

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image7.png){width="3.9166666666666665in"
height="0.8541666666666666in"}

+--------------+-------------------------------------------------------+
| **Use Case   | Lựa chọn dịch nội dung                                |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Học viên đồng ý hoặc từ chối xem bản dịch tiếng Việt  |
|              | khi Extension phát hiện có dữ liệu                    |
+--------------+-------------------------------------------------------+
| **Điều       | Extension đang ở trạng thái Bật và Backend đã trả về  |
| kiện**       | kết quả tìm thấy bản dịch                             |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Extension hiển thị Popup hỏi người dùng có muốn   |
| chính**      | dịch không.                                           |
|              |                                                       |
|              | 2\. Người dùng nhấn chọn \"Dịch\" (Phụ đề).           |
|              |                                                       |
|              | 3\. Extension hiển thị bản dịch tiếng Việt tương ứng  |
|              | trên màn hình.                                        |
+--------------+-------------------------------------------------------+
| **Luồng      | Ở bước 2, nếu người dùng chọn \"Keep Original\",      |
| phụ**        | Extension sẽ đóng Popup và giữ nguyên nội dung gốc.   |
+--------------+-------------------------------------------------------+

5.  **Usecase của reviewer**

+--------------+-------------------------------------------------------+
| **Use Case   | Phê duyệt bản dịch                                    |
| Name**       |                                                       |
+--------------+-------------------------------------------------------+
| **Mô tả**    | Reviewer kiểm tra chất lượng bản dịch trước khi cho   |
|              | phép hiển thị cho Student.                            |
+--------------+-------------------------------------------------------+
| **Điều       | Translator đã upload bản dịch ở trạng thái \"Chờ      |
| kiện**       | duyệt\".                                              |
+--------------+-------------------------------------------------------+
| **Luồng      | 1\. Reviewer mở danh sách các tệp đang chờ kiểm tra.  |
| chính**      |                                                       |
|              | 2\. Reviewer xem nội dung và nhấn \"Approve\"         |
|              | (Duyệt).                                              |
|              |                                                       |
|              | 3\. Hệ thống thay đổi trạng thái bản dịch thành       |
|              | \"Công khai\" để Student có thể thấy.                 |
+--------------+-------------------------------------------------------+
| **Luồng      | Nếu dịch sai, Reviewer chọn \"Reject\" và gửi kèm lý  |
| phụ**        | do yêu cầu sửa đổi                                    |
+--------------+-------------------------------------------------------+

## Sơ đồ use case tổng quát của hệ thống

**Usecase tổng quát mẫu:**

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image8.png){width="6.368055555555555in"
height="9.284722222222221in"}

## Class Diagram

![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image9.png){width="6.727777777777778in"
height="5.004166666666666in"}

3.  ## Sequence Diagram

4.  ## Activity Diagram

```{=html}
<!-- -->
```
4.  ![](vertopal_c48769ec538849a0a6fabc09b685c6b7/media/image10.png){width="3.8916666666666666in"
    height="9.425in"}
