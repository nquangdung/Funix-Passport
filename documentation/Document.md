**FUNiX**

![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image1.png){width="2.3333333333333335in"
height="2.3333333333333335in"}

**SWE102x_03-A:**

**Nhập môn kỹthuật phần mềm**

**Assignment 1: Thiết kếFUNiX Passport**

Nguyễn Đặng Kim Ngân - FX10631

**FUNiX**

**Revision History**

  -----------------------------------------------------------------------
  **Date**          **Version**       **Description**   **Author**
  ----------------- ----------------- ----------------- -----------------
  \<04/13/07\>      \<1.0\>           SRS 1.0           Group-1

  \<04/15/07\>      \<2.0\>           SRS 2.0           Group-1

  \<04/15/07\>      \<3.0\>           SRS 3.0           Group-1
  -----------------------------------------------------------------------

**Bảng thuật ngữ**

> Cung cấp tổng quan vềbất kỳđịnh nghĩa nào mà người đọc nên hiểu trước
> khi đọc tiếp.

+-----------------------------------+-----------------------------------+
| > Cấu hình                        | > Nó có nghĩa là một sản phẩm có  |
|                                   | > sẵn / Được chọn từmột danh mục  |
|                                   | > có thểđược tùy chỉnh.           |
+===================================+===================================+
| > FAQ                             | > Frequently Asked Questions      |
+-----------------------------------+-----------------------------------+
| > CRM                             | > Customer Relationship           |
|                                   | > Management                      |
+-----------------------------------+-----------------------------------+
| > RAID 5                          | > Redundant Array of Inexpensive  |
|                                   | > Disk/Drives                     |
+-----------------------------------+-----------------------------------+
| > CSDL                            | > Cơ sởdữliệu                     |
+-----------------------------------+-----------------------------------+

**Table of Contents**

+-----------------------------------+-----------------------------------+
| > Nguyễn Đặng Kim Ngân - FX10631\ | > 1\                              |
| > Table of Contents\              | > 3\                              |
| > 1. Giới thiệu tổng quan vềdựán\ | > 5\                              |
| > 1.1 Tóm tắt dựán FUNiX          | > 5\                              |
| > Passport:\                      | > 6\                              |
| > 1.2 Phạm vi của dựán\           | > 7\                              |
| > 2. Yêu cầu và đặc tảdựán\       | > 7\                              |
| > 2.1 ĐỊNH NGHĨA YÊU CẦU DỰÁN:\   | > 7\                              |
| > 2.2 Yêu cầu chức năng\          | > 7\                              |
| > 2.3 Yêu cầu phi chức năng\      | > 8\                              |
| > ■2.2.1 Tính bảo mật\            | > 8\                              |
| > ■2.2.2 Tính sẵn sàng và khảnăng | > 8\                              |
| > đáp ứng ■2.2.3 Hiệu suất\       | > 9\                              |
| > 2.4 Đặc tảphần mềm              | > 9\                              |
| >                                 | > 9\                              |
| > ●\                              | > 9\                              |
| > 3. Kiến trúc và thiết kếphần    | > 11\                             |
| > mềm\                            | > 11\                             |
| > 3.1 Kiến trúc phần mềm\         | > 13\                             |
| > 3.2 Usecase:\                   | > 17\                             |
| > 3.2.1 Usecase của User\         | > 18\                             |
| > 3.2.2 Usecase của Translator\   | > 20\                             |
| > 3.2.3 Usecase của Admin\        | > 21\                             |
| > 3.2.4 Usecase của Student\      | > 22\                             |
| > 3.3 Sơ đồuse case tổng quát của | > 23                              |
| > hệthống 3.4 Class Diagram\      |                                   |
| > 3.5 Sequence Diagram\           |                                   |
| > 3.6 Activity Diagram            |                                   |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

Tài liệu đặc tả

+-----------------------+-----------------------+-----------------------+
| 1.1                   | **1.**                | > **[Giới thiệu tổng  |
|                       |                       | > quan                |
|                       |                       | >                     |
|                       |                       | vềdựán]{.underline}** |
+=======================+=======================+=======================+
|                       | > Tóm tắt dựán FUNiX  |                       |
|                       | > Passport:           |                       |
+-----------------------+-----------------------+-----------------------+

> Tóm tắt lại các thông tin cơ bản vềdựán:
>
> ● Hệthống sẽxây dựng là gì?
>
> Chúng ta sẽxây dựng hệthống tên FUNiX Passport đểhỗtrợdịch tài liệu
> chữhoặc video từtiếng Anh sang tiếng Việt của FUNiX dành riêng riêng
> học viên theo học.
>
> ● Mục đích xây dựng hệthống là gì? Hệthống giúp giải quyết cho bài
> toán gì?
>
> Hệthống được xây dựng với các mục đích sau:
>
> \- Hỗtrợhọc viên tiếp cận học liệu dễhiểu hơn, chuẩn xác hơn.
>
> \- Vì đa sốcác trang web đều sửdụng ứng dụng dịch ngôn ngữtheo dạng
> bềmặt, việc dịch tay và chỉnh sửa đểphù hợp với chủđềcông nghệthông
> tin sẽgiúp tính chính xác của học liệu đối với chuyên ngành.
>
> ● Các mục tiêu đểxây dựng dựán là gì?
>
> Đểxây dựng dựán, ta cần hoàn thành những mục tiêu:
>
> \- Xây dựng mô hình dựán gồm 2 phần là phần Backend và Extension:\
> - Backend: là nơi thực hiện các thao tác với CSDL, với nhiệm vụlà quản
> lý vềcác file dịch thuật. Ngoài ra, Backend phải được thiết kếđểcác
> dịch thuật viên đăng tải phụ đềtương ứng với học liệu đó. Backend cần
> giúp các dịch thuật viên và quản trịviên quản lý file dịch thuật, đồng
> thời, cần lưu trữđầy đủthông tin môn - url học liệu - file dịch thuật.
>
> \- Extension: Là một tiện ích mởrộng, giao tiếp với Backend, thực hiện
> nạp những thông tin cần thiết đểhiển thịbản dịch tương ứng cho phía
> học viên sửdụng.

+-----------------------------------+-----------------------------------+
| \-                                | > Xây dựng giao diện sửdụng thân  |
|                                   | > thiện, dễhiểu với người dùng.   |
|                                   | > Cung cấp các bản dịch chính     |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> xác trong thời gian nhanh chóng.\
> 1.2 Phạm vi của dựán
>
> Giải thích phạm vi của dựán: định nghĩa: là một phần kếhoạch dựán liên
> quan. Chúng ta sẽxác định các mục tiêu dựán cụthể, các công việc,
> nhiệm vụ, chi phí và thời hạn. Tài liệu phạm vi của dựán tuyên bốphạm
> vi hoặc các điều khoản tham chiếu, giải thích các ranh giới của dựán
> thiết lập trách nhiệm cho từng thành viên trong nhóm và các quy trình
> xác minh cũng như phê duyệt công việc đã hoàn thành.

+-----------------------------------+-----------------------------------+
| ●                                 | > Phạm vi vềdịch vụ               |
|                                   | >                                 |
| > \-\                             | > Cung cấp một nền tảng lưu       |
| > -                               | > trữMetadata các file phụđềcủa   |
|                                   | > các học liệu tiếng Anh. Thao    |
| ●                                 | > tác, tìm kiếm, chỉnh sửa, quản  |
|                                   | > lí thông tin các file dịch      |
| > \-\                             | > phụđề.                          |
| > -\                              | >                                 |
| > -                               | > Phạm vi vềkhách hàng:           |
|                                   | >                                 |
| ●                                 | > Học viên FUNiX.                 |
|                                   | >                                 |
| > \-\                             | > Các dịch thuật viên\            |
| > -                               | > Các quản trịviên.               |
|                                   | >                                 |
|                                   | > Phạm vi vềnền tảng/hệthống      |
|                                   | >                                 |
|                                   | > Các trang công nghệthông tin    |
|                                   | > trên internet, những video, học |
|                                   | > liệu MOOC. Hoạt động như một    |
|                                   | > tiện ích mởrộng trên các phần   |
|                                   | > mềm internet: Bing, Chrome, ... |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

+-------------+-------------+-------------+-------------+-------------+
| 2.1         | > \-        | **2.**      |             | > **Yêu cầu |
|             |             |             |             | > và đặc    |
|             |             |             |             | > tảdựán**  |
+=============+=============+=============+=============+=============+
|             |             | > ĐỊNH      |             |             |
|             |             | > NGHĨA YÊU |             |             |
|             |             | > CẦU DỰÁN: |             |             |
+-------------+-------------+-------------+-------------+-------------+
|             |             | > Là những  |             |             |
|             |             | > vấn đềcần |             |             |
|             |             | > xửlý      |             |             |
|             |             | > trong     |             |             |
|             |             | > bài.      |             |             |
|             |             | > Chỉnói    |             |             |
|             |             | > vềvấn đề, |             |             |
|             |             | > không     |             |             |
|             |             | > đềcập tới |             |             |
|             |             | > tới giải  |             |             |
|             |             | > pháp.     |             |             |
+-------------+-------------+-------------+-------------+-------------+
|             | > \-        | > Những vai |             |             |
|             |             | > trò của   |             |             |
|             |             | > đặc tảyêu |             |             |
|             |             | > cầu dựán: |             |             |
+-------------+-------------+-------------+-------------+-------------+
|             |             | \-          | > Giúp      |             |
|             |             |             | > người làm |             |
|             |             |             | > hình dung |             |
|             |             |             | > rõ ràng   |             |
|             |             |             | > được mục  |             |
|             |             |             | > đích      |             |
|             |             |             | > dựán,     |             |
|             |             |             | > từđó xây  |             |
|             |             |             | > dựng      |             |
|             |             |             | > hệthống   |             |
+-------------+-------------+-------------+-------------+-------------+

> chuẩn xác, đầy đủcác chức năng.
>
> \- Tránh gặp phải trường hợp hiểu sai ý nhau.
>
> \- Giúp cho việc bảo trì và nâng cao các chức năng trong hệthống 1
> cách dễdàng và nhanh chóng .
>
> \- Giúp các tester hiểu được hệthống rõ ràng -\> xây dựng những kịch
> bản xác thực, chi tiết, thực tếhơn.
>
> 2.2 Yêu cầu chức năng
>
> Dựa vào các yêu cầu ởphần \"Yêu cầu dựán\", bạn sẽlọc xem khi xây dựng
> thì hệthống sẽgồm có những chức năng nào, những chức năng đó sẽhoạt
> động như thếnào và đưa vào tài liệu theo Template đã có.
>
> \- Hỗtrợđăng tải và lưu trữcác file dịch thuật + thông tin của file
> (phụthuộc vào dạng bài gốc là video MOOC hay bài viết) như link bài
> gốc, tên người dịch, ngày đăng tải, tên bản dịch, v.v

+-----------------------------------+-----------------------------------+
| > \-\                             | > Cho phép quản trịviên quản lý   |
| > -\                              | > file dịch thuật, chỉnh sửa,     |
| > -\                              | > xóa, thay đổi thông tin.        |
| > 2.3                             | >                                 |
|                                   | > Cho phép quản trịviên quản lý   |
|                                   | > danh sách người dùng: thêm      |
|                                   | > quyền, xóa quyền, xóa tài       |
|                                   | > khoản.                          |
|                                   | >                                 |
|                                   | > Hỗtrợngười dùng cung cấp file   |
|                                   | > dịch tương ứng khi họtruy cập   |
|                                   | > vào học liệu nước ngoài.        |
|                                   | >                                 |
|                                   | > Yêu cầu phi chức năng           |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> Ởphần \"Yêu cầu dựán\" đã đưa ra cho bạn rất nhiều yêu cầu cho
> hệthống. Bạn sẽcần lọc rađâu là yêu cầu dạng phi chức năng đểviết vào
> tài liệu (theo như mẫu đã có ởTemplate). Ngoài ra, bạn có thểbổsung
> thêm một sốyêu cầu phi chức năng mà bạn nghĩ sẽcần thiết cho dựán này.
>
> *■*2.2.1 Tính bảo mật
>
> Xác định các yêu cầu liên quan đến vấn đềbảo mật hoặc quyền riêng tư
> dẫn đến hạn chếquyền truy cập hoặc sửdụng sản phẩm. Có thểlà bảo mật
> vật lý, dữliệu hoặc phần mềm. Các yêu cầu bảo mật thường bắt nguồn
> từcác quy tắc kinh doanh, vì vậy hãy xác định mọi chính sách hoặc quy
> định vềbảo mật hoặc quyền riêng tư mà sản phẩm phải tuân theo.

+-----------------------------------+-----------------------------------+
| > \-\                             | > Yêu cầu tính bảo mật cao.       |
| > -\                              | >                                 |
| > -                               | > Không rò rỉcác file dịch thuật  |
|                                   | > ra ngoài.                       |
|                                   | >                                 |
|                                   | > Cần lớp bảo mật trước khi được  |
|                                   | > phép chỉnh sửa hay thêm bớt     |
|                                   | > dữliệu trong database.          |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> *■*2.2.2 Tính sẵn sàng và khảnăng đáp ứng
>
> Nêu vềsựsẵn sàng của hệthống như khảnăng làm việc 24/7, luôn đáp ứng
> yêu cầu người đọc và tác giảcó thểxem và cập nhật bài với các thời
> gian khác nhau
>
> \- Đáp ứng bản dịch đầy đủ, chính xác trong thời gian ngắn.
>
> \- Khảnăng làm việc 24/7. Luôn luôn sẵn sàng cho user xem bản dịch và
> cho translator, admin làm việc với bản dịch.
>
> \- Extension được xây dựng đểsửdụng chủyếu trên trình duyệt Chrome
> *■*2.2.3 Hiệu suất
>
> Nêu các yêu cầu hiệu suất cụthểcho các hoạt động hệthống khác nhau.
> Nếu các yêu cầu chức năng hoặc tính năng khác nhau có yêu cầu vềhiệu
> suất khác nhau, nên chỉđịnh các mục tiêu hiệu suất đó ngay cạnh các
> yêu cầu chức năng tương ứng chứkhông gộp lại trong phần này.
>
> \- Có tốc độổn định, thời gian đểhiển thịbản dịch tính từkhi học viên
> vào website không được quá 1s.
>
> \- Thời gian đểsubmit và thực hiện các thao tác của Translator cần
> phải có tốc độxửlí nhanh. Trung bình mỗi thao tác không quá 0.5s.
>
> 2.4 Đặc tảphần mềm
>
> Sau khi đã xác định được hết các yêu cầu cho dựán. Bạn cũng cần xác
> định đâu là đặc tảphần mềm trong dựán hiện tại và viết vào tài liệu.
>
> Ngoài ra, bạn có thểbổsung thêm một sốđặc tảkhác mà bạn nghĩ sẽcần
> thiết cho dựán này.
>
> \- Vấn đềbảo mật dữliệu: Yêu cầu API Key hoặc Token đểtruy cập dữliệu.
>
> \- Hệthống được vận hành và được sửdụng chủyếu trên Chrome trong dạng
> 1 Extension.

●

+-----------------------+-----------------------+-----------------------+
| > 3.1\                | **3.**                | > **Kiến trúc và      |
| > 3.1.1\              |                       | > thiết kếphần mềm**  |
| > -\                  |                       |                       |
| > -                   |                       |                       |
+=======================+=======================+=======================+
|                       | > Kiến trúc phần mềm\ |                       |
|                       | > Định nghĩa kiến     |                       |
|                       | > trúc phần mềm:\     |                       |
|                       | > Là cấp bậc cao nhất |                       |
|                       | > của giai đoạn thiết |                       |
|                       | > kế\                 |                       |
|                       | > Từnhững ý tưởng rời |                       |
|                       | > rạc, kiến trúc phần |                       |
|                       | > mềm sẽgiúp ta       |                       |
|                       | > tổchức và sắp xếp   |                       |
|                       | > logic đểchuẩn bị    |                       |
+-----------------------+-----------------------+-----------------------+

> bắt tay thực hiện.
>
> \- Một khi đã quyết định kiến trúc thì không thểthay đổi trong bất kì
> trường hợp nào.- Kiến trúc phần mềm chia nhỏhệthống và ý tưởng lớn hơn
> thành các hệthống tập trung nhỏ hơn.
>
> \- Lợi ích của việc xây dựng 1 kiến trúc tốt: Tiết kiệm thời gian hoàn
> thành sản phẩm, chi phí bảo trì dựán.
>
> \- Buy & Build: Phân tách dựán ra thành các phần riêng biệt, từđó xem
> xét đã có bản sản phẩm hoàn chỉnh được rao bán trên thịtrường hay
> chưa. Nếu có thì ta bỏphí để mua bản có sẵn đó, vừa tiết kiệm được
> nhân lực cũng như thời gian, tiền bạc xây dựng dựán.
>
> \- Các mẫu kiến trúc phần mềm thông dụng:\
> - Pipe and Filter: -
>
> Dựa vào các nội dung của yêu cầu dựán phía trên, bạn hãy chọn lựa kiến
> trúc phần mềm phùhợp với dựán này. Sau đó, bạn cần viết ra lý do hợp
> lý đểbạn chọn kiến trúc này thay vì các kiến trúc khác.

+-----------------------+-----------------------+-----------------------+
| > Mô hình cấu trúc    |                       |                       |
| > tổng quát           |                       |                       |
+=======================+=======================+=======================+
| > Client-Server       | > \- Dựa vào cách     |                       |
|                       | > hoạt động của phần  |                       |
|                       | > mềm: người dùng     |                       |
|                       | > truy cập vào trang  |                       |
|                       | > web học liệu, sau   |                       |
|                       | > đó extension lấy ID |                       |
|                       | > của các thành phần, |                       |
|                       | > gửi về\             |                       |
|                       | > backend và chờfile  |                       |
|                       | > phụđề/document      |                       |
|                       | > tương ứng.          |                       |
|                       | >                     |                       |
|                       | > \- Dựa vào sốlượng: |                       |
|                       | > 1 backend (server)  |                       |
|                       | > chịu trách nhiệm và |                       |
|                       | > xửlý yêu cầu của    |                       |
|                       | > nhiều máy học viên  |                       |
|                       | > (client)            |                       |
+-----------------------+-----------------------+-----------------------+
| > Mô hình cấu trúc    |                       |                       |
| > chức năng           |                       |                       |
+-----------------------+-----------------------+-----------------------+
| > Tìm kiếm file       | > Pipe-Filter         | > \- Dựa vào cách     |
|                       |                       | > hoạt động: Sau khi  |
|                       |                       | > nhập 1 loạt ký      |
|                       |                       | > tựchứa thông tin    |
|                       |                       | > của file cần tìm    |
|                       |                       | > kiếm, hệthống       |
|                       |                       | > sẽtiến hành phân    |
|                       |                       | > tách thông tin theo |
|                       |                       | > từng lớp, từđó chọn |
|                       |                       | > ra những kết quảcó  |
|                       |                       | > độtrùng khớp nhiều  |
|                       |                       | > nhất tới thấp nhất. |
+-----------------------+-----------------------+-----------------------+

+-----------------------------------+-----------------------------------+
| > 3.2\                            | > Usecase:\                       |
| > 3.2.1                           | > Usecase của User                |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image2.png){width="5.979166666666667in"
> height="5.406944444444444in"}

+-----------------------------------+-----------------------------------+
| **Use Case Name**                 | > Đăng nhập                       |
+===================================+===================================+
| > **Mô tả**                       | > User có thểđăng nhập tài khoản  |
|                                   | > vào hệthống và sửdụng các chức  |
|                                   | > năng trong đó.                  |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > User chưa đăng nhập vào hệthống |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. User truy cập vào trang web |
|                                   | > quản lý. Nhấn vào mục "Login\"  |
|                                   | > 2. Hệthống hiển thịForm Login.  |
|                                   | >                                 |
|                                   | > 3\. User nhập vào các thông tin |
|                                   | > đăng nhập.                      |
|                                   | >                                 |
|                                   | > 4\. Nếu thông tin đăng nhập     |
|                                   | > đúng, cập nhật thông tin vào    |
|                                   | > hệthống.                        |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước 4, nếu thông tin đăng     |
|                                   | > nhập sai sẽhiển thịthông báo    |
|                                   | > cho người dùng.                 |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Đăng xuất                       |
+===================================+===================================+
| > **Mô tả**                       | > User sau khi sửdụng hệthống     |
|                                   | > xong có thểđăng xuất tài khoản  |
|                                   | > đểtránh bịkẻlợi dụng.           |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > User đã đăng nhập vào hệthống   |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. User tìm kiếm mục "Log out" |
|                                   | > trên hệthống.                   |
|                                   | >                                 |
|                                   | > 2\. User nhấp vào Logout và     |
|                                   | > confirm đăng xuất.              |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước 2, hệthống sẽhiển         |
|                                   | > thịpop-up form đểxác định đăng  |
|                                   | > xuất.                           |
+-----------------------------------+-----------------------------------+

> 3.2.2 Usecase của Translator
>
> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image3.png){width="6.729166666666667in"
> height="5.781944444444444in"}

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Upload file phụđề               |
+===================================+===================================+
| > **Mô tả**                       | > Sau khi thực hiện dịch xong tài |
|                                   | > liệu (video MOOC hoặc trang     |
|                                   | > web), Translator tiến hành đăng |
|                                   | > tải file dịch thuật lên         |
|                                   | > hệthống.                        |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
|                                   | >                                 |
|                                   | > \- Học liệu gốc chưa có file    |
|                                   | > dịch                            |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Nhấn vào mục "Đăng tải      |
|                                   | > file".                          |
|                                   | >                                 |
|                                   | > 3\. Translator tải file         |
|                                   | > phụđề/document lên              |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
|                                   | > 4\. Translator hoàn thành các   |
|                                   | > thông tin cần thiết của file.   |
|                                   | > 5. Translator nhấn "Submit".    |
|                                   | > Thao tác hoàn thành.            |
+===================================+===================================+
| > **Luồng phụ**                   | > Ởbước thứ3, hệthống thực hiện   |
|                                   | > kiểm tra định dạng, kích        |
|                                   | > cỡfile.Ởbước thứ5, hệthống kiểm |
|                                   | > tra các thông tin đã đúng định  |
|                                   | > dạng, cúpháp.                   |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Tải file phụđề                  |
+===================================+===================================+
| > **Mô tả**                       | > Sau khi tìm thấy file cần tải,  |
|                                   | > translator nhấp nút tải.        |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
|                                   | >                                 |
|                                   | > \- File dịch đã tồn tại         |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Translator mởbảng           |
|                                   | > dashboard, và chọn file muốn    |
|                                   | > tải. 3. Nhấp vào nút tải đểtiến |
|                                   | > hành tải file.                  |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   |                                   |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Tải xuống file đã dịch          |
+===================================+===================================+
| > **Mô tả**                       | > Sau khi thực hiện dịch xong tài |
|                                   | > liệu (video MOOC hoặc trang     |
|                                   | > web), Translator tiến hành đăng |
|                                   | > tải file dịch thuật lên         |
|                                   | > hệthống.                        |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
|                                   | >                                 |
|                                   | > \- Học liệu gốc chưa có file    |
|                                   | > dịch                            |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Nhấn vào mục "Đăng tải      |
|                                   | > file".                          |
|                                   | >                                 |
|                                   | > 3\. Translator tải file         |
|                                   | > phụđề/document lên\             |
|                                   | > 4. Translator hoàn thành các    |
|                                   | > thông tin cần thiết của file.   |
|                                   | > 5. Translator nhấn "Submit".    |
|                                   | > Thao tác hoàn thành.            |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước thứ3, hệthống thực hiện   |
|                                   | > kiểm tra định dạng, kích        |
|                                   | > cỡfile.Ởbước thứ5, hệthống kiểm |
|                                   | > tra các thông tin đã đúng định  |
|                                   | > dạng, cúpháp.                   |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Xem danh sách các file đã được  |
|                                   | > upload                          |
+===================================+===================================+
| > **Mô tả**                       | > Backend sẽcung cấp 2 Dashboard, |
|                                   | > 1 bảng hiển thịcác bản dịch     |
|                                   | > phụđềvà 1 bảng hiển thịbản dịch |
|                                   | > Document.                       |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Translator xem 2 dashboard, |
|                                   | > 1 bảng lưu trữfile phụđề, 1     |
|                                   | > bảng lưu trữfile document.      |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   |                                   |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Tìm kiếm các bản dịch theo      |
|                                   | > bộlọc                           |
+===================================+===================================+
| > **Mô tả**                       | > Translator có thểtìm kiếm các   |
|                                   | > bản dịch theo những bộlọc sau:  |
|                                   | > Tên bản dịch, Url, Người dịch,  |
|                                   | > Course ID, Video ID.            |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Nhấn vào mục Tìm kiếm\      |
|                                   | > 3. Translator tìm nhập thẳng    |
|                                   | > vào thanh tìm kiếm hoặc chọn    |
|                                   | > theo bộlọc có sẵn.              |
|                                   | >                                 |
|                                   | > 4\. Translator xem những kết    |
|                                   | > quảtìm kiếm trảvề               |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Máy chủthực hiện tìm kiếm theo  |
|                                   | > thông tin đã được cung cấp và   |
|                                   | > trảlại những kết quảtìm kiếm    |
|                                   | > trùng khớp                      |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Xóa các file dịch thuật         |
+===================================+===================================+
| > **Mô tả**                       | > Sau khi tới file cần xóa,       |
|                                   | > translator thực hiện xóa file.  |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền. \`        |
|                                   | >                                 |
|                                   | > \- Học liệu gốc đã có file dịch |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 1.5. Translator thực hiện tìm   |
|                                   | > kiếm file cần xóa.              |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
|                                   | > 2\. Translator nhấp vào dòng    |
|                                   | > file cần xóa trong dashboard    |
|                                   | > hoặc trong mục tìm kiếm.        |
|                                   | >                                 |
|                                   | > 3\. Translator nhấn Xác nhận    |
|                                   | > xóa file.                       |
+===================================+===================================+
| > **Luồng phụ**                   | > Ởbước thứ2, hệthống hiện 1      |
|                                   | > pop-up form xác nhận xóa file.  |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Chỉnh sửa thông tin file        |
+===================================+===================================+
| > **Mô tả**                       | > Translator mởfile cần chỉnh sửa |
|                                   | > và tiến hành cập nhật thông     |
|                                   | > tin/file dịch thuật theo ý      |
|                                   | > muốn.                           |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Translator đã đăng nhập tài  |
|                                   | > khoản được cấp quyền.           |
|                                   | >                                 |
|                                   | > \- File học liệu đã tồn tại, đã |
|                                   | > có file phụđềđính kèm.          |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Translator truy cập vào     |
|                                   | > trang web quản lý, nhập         |
|                                   | > password đểtruy cập vào         |
|                                   | > dashboard lưu file.             |
|                                   | >                                 |
|                                   | > 2\. Translator nhấn vào mục     |
|                                   | > đểxem các bảng file hoặc thực   |
|                                   | > hiện tìm kiếm file mong muốn.   |
|                                   | >                                 |
|                                   | > 3\. Translator nhấp vào ô Edit  |
|                                   | > và tiến hành cập nhật thông tin |
|                                   | > file.                           |
|                                   | >                                 |
|                                   | > 4\. Sau khi hoàn thành,         |
|                                   | > translator thực hiện, xác nhận  |
|                                   | > cập nhật thông tin.             |
|                                   | >                                 |
|                                   | > 4.5. Translator nhập lại những  |
|                                   | > thông tin cập nhật sai định     |
|                                   | > dạng, cúpháp. (nếu có)\         |
|                                   | > 5. Translator kiểm tra lại      |
|                                   | > thông tin sau khi đã cập nhật.  |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước thứ2, hệthống thực hiện   |
|                                   | > kiểm tra định dạng, kích        |
|                                   | > cỡfile.Ởbước thứ4, hệthống kiểm |
|                                   | > tra định dạng, cú pháp và gửi   |
|                                   | > cảnh báo vềform chỉnh sửa.      |
|                                   | >                                 |
|                                   | > Ởbước 5, hệthống thực hiện cập  |
|                                   | > nhật thông tin và trảvềthông    |
|                                   | > tinđã cập nhật cho người dùng.  |
+-----------------------------------+-----------------------------------+

> 3.2.3 Usecase của Admin
>
> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image4.png){width="6.729166666666667in"
> height="3.2597222222222224in"}

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Chỉnh sửa quyền của người dùng  |
+===================================+===================================+
| > **Mô tả**                       | > Admin vào Dashboard lưu trữdanh |
|                                   | > sách người dùng và thực hiện    |
|                                   | > chỉnh sửa quyền. Có thểthêm     |
|                                   | > hoặc xóa quyền.                 |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Admin đã được cấp quyền      |
|                                   | > chỉnh sửa.                      |
|                                   | >                                 |
|                                   | > \- Những người dùng bịquản lý   |
|                                   | > là translator và user.          |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Admin truy cập vào trang    |
|                                   | > web quản lý, nhập password      |
|                                   | > đểtruy cập vào dashboard lưu    |
|                                   | > thông tin người dùng.           |
|                                   | >                                 |
|                                   | > 2\. Admin chọn Translator đểxóa |
|                                   | > quyền xuống User. HOẶC, chọn    |
|                                   | > User đểthêm quyền Translator.   |
|                                   | >                                 |
|                                   | > 3\. Admin xác nhận và quay      |
|                                   | > trởlại màn hình chính.          |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước 1, dashboard hiện danh    |
|                                   | > sách tất cảngười dùng nhưng     |
|                                   | > chỉhiện thịnút cập nhật ởcác    |
|                                   | > người dùng có vai trò là        |
|                                   | > Translator hoặc User.           |
|                                   | >                                 |
|                                   | > Ởbước 3, hệthống thực hiện cập  |
|                                   | > nhật thông tin và trảvềthông    |
|                                   | > tinđã cập nhật cho người dùng.  |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Xóa tài khoản người dùng.       |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Mô tả**                       | > Admin thực hiện xóa vĩnh viễn   |
|                                   | > tài khoản của người dùng        |
+===================================+===================================+
| > **Điều kiện**                   | > \- Admin đã được cấp quyền      |
|                                   | > chỉnh sửa.                      |
|                                   | >                                 |
|                                   | > \- Những người dùng bịquản lý   |
|                                   | > là translator và user.          |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Admin mởdanh sách lưu       |
|                                   | > trữngười dùng.                  |
|                                   | >                                 |
|                                   | > 2\. Admin chọn Translator đểxóa |
|                                   | > quyền xuống User. HOẶC, chọn    |
|                                   | > User đểthêm quyền Translator.   |
|                                   | >                                 |
|                                   | > 3\. Admin xác nhận và quay      |
|                                   | > trởlại màn hình chính.          |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Ởbước 1, dashboard hiện danh    |
|                                   | > sách tất cảngười dùng nhưng     |
|                                   | > chỉhiện thịnút cập nhật ởcác    |
|                                   | > người dùng có vai trò là        |
|                                   | > Translator hoặc User.           |
|                                   | >                                 |
|                                   | > Ởbước 3, hệthống thực hiện cập  |
|                                   | > nhật thông tin và trảvềthông    |
|                                   | > tinđã cập nhật cho người dùng.  |
+-----------------------------------+-----------------------------------+

> 3.2.4 Usecase của Student
>
> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image5.png){width="6.729166666666667in"
> height="4.458333333333333in"}

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Sửdụng bản dịch.                |
+===================================+===================================+
| > **Mô tả**                       | > Khi học viên vừa mởvào học      |
|                                   | > liệu, extension lấy thông tin   |
|                                   | > cần thiết, gửi tới Backend và   |
|                                   | > hiển thịlại kết quảdịch thuật   |
|                                   | > Backend trảvề.                  |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > \- Học viên đã cài đặt          |
|                                   | > Extension FUNiX Passport.       |
|                                   | >                                 |
|                                   | > \- Học liệu viết/nói tiếng Anh. |
|                                   | >                                 |
|                                   | > \- Học liệu thuộc quản lý, giáo |
|                                   | > trình môn học FUNiX.            |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > 1\. Học viên truy cập tới học   |
|                                   | > liệu tiếng anh bất kì thuộc     |
|                                   | > hệthống FUNiX.                  |
|                                   | >                                 |
|                                   | > 2\. Học viên chọn xác nhận muốn |
|                                   | > xem bản dịch video/document     |
|                                   | > này.                            |
|                                   | >                                 |
|                                   | > 3\. Học viên xem học liệu bằng  |
|                                   | > phụđề/bản dịch tiếng Việt.      |
|                                   | >                                 |
|                                   | > Extension lấy course_id và      |
|                                   | > video_id (đối với MOOC) hoặc    |
|                                   | > url (đối với document) và gửi   |
|                                   | > vềbackend.                      |
|                                   | >                                 |
|                                   | > 4\. Backend thực hiện tìm kiếm  |
|                                   | > trong kho tài liệu.             |
|                                   | >                                 |
|                                   | > 5\. Backend lấy file dịch thuật |
|                                   | > ứng với thông tin file được     |
|                                   | > extension cung cấp.             |
+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   | > Sau bước 2, Extension lấy       |
|                                   | > course_id và video_id (đối với  |
|                                   | > MOOC) hoặc url (đối với         |
|                                   | > document) và gửi vềbackend.     |
|                                   | > Backend thực hiện tìm kiếm      |
|                                   | > trong kho tài liệu. Backend lấy |
|                                   | > file dịch thuật ứng với thông   |
|                                   | > tin file được extension cung    |
|                                   | > cấp và gửi lại Extension.       |
|                                   | >                                 |
|                                   | > Extension hiển thay đổi giao    |
|                                   | > diện trang web và hiển thịcho   |
|                                   | > người dùng.                     |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Use Case Name**               | > Bật/Tắt Extension               |
+===================================+===================================+
| > **Mô tả**                       | > Học viên có thểbật hoặc tắt     |
|                                   | > extension này bằng cách truy    |
|                                   | > cập vào Extension store hoặc    |
|                                   | > tắt trực tiếp bằng Develop      |
|                                   | > tool.                           |
+-----------------------------------+-----------------------------------+
| > **Điều kiện**                   | > Học viên đã cài đặt Extension   |
|                                   | > FUNiX Passport.                 |
+-----------------------------------+-----------------------------------+
| > **Luồng chính**                 | > Có 2 cách triển khai:\          |
|                                   | > Cách 1: Học viên tắt extension  |
|                                   | > bằng extension store.           |
|                                   | >                                 |
|                                   | > Cách 2: Học viên sửdụng         |
|                                   | > Developer tools đểvô hiệu hóa   |
|                                   | > extension trên 1 trang web nhất |
|                                   | > định.                           |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| > **Luồng phụ**                   |                                   |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| 3.3                               | > tổng quát của hệthống           |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image6.png){width="6.729166666666667in"
> height="3.625in"}

+-----------------------------------+-----------------------------------+
| 3.3.1                             | > Phần Backend:                   |
+===================================+===================================+
+-----------------------------------+-----------------------------------+

> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image7.png){width="7.594443350831146in"
> height="4.386111111111111in"}
>
> 3.3.2 Phần Extension:
>
> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image8.png){width="5.615277777777778in"
> height="3.551388888888889in"}

  -----------------------------------------------------------------------
  3.4                                 
  ----------------------------------- -----------------------------------

  -----------------------------------------------------------------------

> ![](vertopal_a4b7f6ead3a04d33ac649a539e6234f8/media/image9.png){width="7.916666666666667in"
> height="6.219444444444444in"}

**FUNiX**

**THE END**
