

## Revision History


|**Date**|**Version**|**Description**|**Author**|
| :-: | :-: | :-: | :-: |
|<04/13/07>|<1.0>|SRS 1.0|Group-1|
|<04/15/07>|<2.0>|SRS 2.0|Group-1|
|<04/15/07>|<3.0>|SRS 3.0|Group-1|
|<04/16/07>|<4.0>|SRS 4.0|Group-1|

**Bảng thuật ngữ**

Cung cấp tổng quan về bất kỳ định nghĩa nào mà người đọc nên hiểu trước khi đọc tiếp.


|Thuật ngữ|Định nghĩa|
| :- | :- |
|Cấu hình|Nó có nghĩa là một sản phẩm có sẵn / Được chọn từ một danh mục có thể được tùy chỉnh.|
|FAQ|Frequently Asked Questions|
|CRM|Customer Relationship Management|
|RAID 5|Redundant Array of Inexpensive Disk/Drives|






## **Giới thiệu tổng quan về dự án**
### **Tóm tắt dự án**
Dự án được tạo ra nhằm giúp đỡ các bạn học viên học Funix tiếp xúc với nguồn tài liệu tiếng Anh. Do tiếng Anh là ngoại ngữ đối với nước mình, và nhiều bạn không giỏi về ngoại ngữ, hoặc biết nhưng không cảm thấy thoải mái với việc sử dụng ngoại ngữ, nên project được lập ra nhằm dịch các bài giảng và cho phép các bạn tiếp cận dưới dạng một extension. Cũng nhằm đồng thời tạo một hệ thống quản lý tập trung các tài liệu được trường dịch.

### **Phạm vi của dự án**
Dự án nhằm phục vụ các bạn học viên bên Funix có nhu cầu đọc tài liệu bằng ngôn ngữ Tiếng Việt, chủ yếu trên các dòng máy tính để bàn và xách tay sử dụng Google Chrome. Dự án không phải là phần mềm hỗ trợ các bạn dịch thuật.

### **Yêu cầu và đặc tả dự án**
   #### **Yêu cầu chức năng**
Sẽ có 4 vai trò chính như sau:

- User: Người dùng bình thường, chỉ có thể đăng nhập và đăng xuất khỏi ứng dụng và xem phụ đề.
- Reviewer: Người phê duyệt các bài dịch của Translator.
- Translator: Các dịch thuật viên, có thể thực hiện các thao tác sau trên ứng dụng:

\- Upload file phụ đề đã dịch tiếng Việt:

\+ Translator sẽ vào màn hình upload, sau đó cần nhập các thông tin cần thiết như: Tên Video, URL Video, Course ID, Video ID.

\+ Sau đó Translator sẽ đính kèm thêm file phụ đề đã được dịch.

\+ Nhấn submit và ứng dụng thực hiện công đoạn upload, lưu dữ liệu vào Database.

\- Upload file Document đã dịch tiếng Việt:

\+ Tương tự với upload phụ đề, nhưng Translator sẽ cần nhập Tên bản dịch và URL của Document.

\+ Translator sẽ đính kèm file Document đã dịch.

\- Xem danh sách các file dịch thuật đã được upload: sẽ có hai Dashboard, 01 Dashboard hiển thị các bản dịch phụ đề và Dashboard còn lại sẽ hiển thị bản dịch Document.

\- Tải xuống file đã dịch: khi click vào link trên Dashboard thì có thể tải xuống dữ liệu của bản dịch (File phụ đề hoặc file Document).

\- Tìm kiếm các bản dịch theo bộ lọc:

\+ Translator có thể tìm kiếm các bản dịch theo những bộ lọc tính sau: Tên bản dịch, Url, Người dịch, Course ID, Video ID.

\- Xóa các file phụ đề hoặc document:

\+ Sau khi tìm kiếm bản dịch, Translator có thể lựa chọn để xóa bản dịch đó đi.

\- Chỉnh sửa thông tin:

\+ Sau khi tìm kiếm bản dịch, Translator có thể lựa chọn để chỉnh sửa lại thông tin của bản dịch đó. Sẽ có 2 loại chỉnh sửa như sau: Chỉnh sửa các metadata của file dịch và Reup file dịch khác lên thay thế.

- Admin: Các quản trị viên, nhiệm vụ chính là quản lý tài khoản người dùng. Admin có thể thực hiện các thao tác như sau:

\- Xóa tài khoản một người dùng.

\- Thêm quyền cho một người dùng (chuyển User thành Translator).

\- Xóa quyền cho một người dùng (chuyển Translator cho User).
#### **Yêu cầu phi chức năng**
- Sản phẩm là một Chrome Extension. được xây dựng để sử dụng chủ yếu trên trình duyệt Chrome.
- Giao diện của hệ thống được xây dựng dễ hiểu, người dùng không cần biết quá nhiều về công nghệ cũng có thể sử dụng hệ thống.
- ***Tính bảo mật:*** 
  - Phải có tính bảo mật cao, dữ liệu được lưu trữ ở Database an toàn. 
  - Đồng thời cũng cần các API Key hay Token mới có thể truy cập và chỉnh sửa dữ liệu ở Database.
  - Quyền hạn của các User chỉ được phép giới hạn ở các mức độ cho phép ở phần yêu cầu chức năng.
- **Tính sẵn sàng và khả năng đáp ứng:*** Hệ thống làm việc 24/7, luôn đáp ứng yêu cầu của học viên vào bất kỳ giờ phút nào.
- ***Hiệu suất***
  - Có tốc độ ổn định, thời gian để hiển thị bản dịch tính từ khi học viên vào Website không được quá 1s.
  - Thời gian để submit và thực hiện các thao tác của Translator cũng cần phải có tốc độ xử lý nhanh, trung bình mỗi thao tác không được quá 0.5s.
 ### **Đặc tả phần mềm**
- Sử dụng CSS, JS, HTML cho phần extension
- Sử dụng Nodejs cho phần server, framework Expressjs
- Sử dụng MySQL cho Database
- Sử dụng FPT Object Storage để lưu các tài liệu và phụ đề
## **Kiến trúc và thiết kế phần mềm**
   ### **Kiến trúc phần mềm**
Do đặc thù của dự án chỉ giúp đỡ các bạn trong Funix và Funix và các tài liệu đều hoạt động trên môi trường web nên dự định sẽ sử dụng mô hình Client - Server. Như thế các file phụ đề chỉ tập trung trên server của funix và các bạn học viên chỉ cần sử dụng trình duyệt Chromium, tải tiện ích về là có thể dùng.

Không sử dụng các kiến trúc khác vì không có kiến trúc nào có thể tách biệt Frontend và Backend ra để chỉ có các user có đủ quyền quản lý các file dịch.

### **Usecase**

#### ***Usecase của User***
**Đăng nhập:**


|**Use Case Name**|Đăng nhập|
| :- | :- |
|**Mô tả**|User có thể đăng nhập tài khoản vào hệ thống và sử dụng các chức năng trong đó.|
|**Điều kiện**|User chưa đăng nhập vào hệ thống|
|**Luồng chính**|<p>1\. User truy cập vào trang web quản lý. Nhấn vào mục “Login"</p><p>2\. Hệ thống hiển thị Form Login.</p><p>3\. User nhập vào các thông tin đăng nhập.</p><p>4\. Nếu thông tin đăng nhập đúng, cho phép đăng nhập.</p><p></p>|
|**Luồng phụ**|Ở bước 4, nếu thông tin đăng nhập sai sẽ hiển thị thông báo cho người dùng.|

**Xem phụ đề**


|**Use Case Name**|Xem phụ đề|
| :- | :- |
|**Mô tả**|User khi truy cập vào một trang web/video có nội dung được dịch sẽ được lựa chọn xem bản dịch hay không.|
|**Điều kiện**|User đã đăng nhập vào hệ thống|
|**Luồng chính**|<p>1\. User khi truy cập vào một trang web/video có nội dung được dịch</p><p>2\. User được hỏi có muốn xem bản dịch hay không</p><p>3\. Hiển thị bản dịch</p><p></p>|
|**Luồng phụ**|Ở bước 3, nếu từ chối sẽ tắt thông báo và cho user xem nội dung gốc.|

#### ***Usecase của Translator***
**\* Điều kiện của Translator: Là một User và có quyền Translator, và đã đăng nhập vào hệ thống.**

**Upload phụ đề:**


|**Use Case Name**|Upload phụ đề|
| :- | :- |
|**Mô tả**|Translator có thể tải lên phụ đề cho video mình đã dịch.|
|**Điều kiện thêm**|Đã có một file dịch sẵn|
|**Luồng chính**|<p>1\. Trên Dashboard, bấm vào chức năng tải phụ đề lên</p><p>2\. Nhập metadata cho phụ đề</p><p>3\. Nếu nhập đầy đủ dữ liệu, cho phép chọn file để tải lên</p><p>4\. Kiểm tra file hợp lệ, lưu vào hệ thống.</p><p></p>|
|**Luồng phụ**|Ở bước 3, 4, nếu có bất kỳ thông tin vào không hợp lệ sẽ thông báo lỗi.|

` `**Upload tài liệu đã được dịch:**


|**Use Case Name**|Upload tài liệu đã được dịch|
| :- | :- |
|**Mô tả**|Translator có thể tải lên tài liệu mình đã dịch.|
|**Điều kiện thêm**|Đã có một file dịch sẵn|
|**Luồng chính**|<p>1\. Trên Dashboard, bấm vào chức năng tải tài liệu lên</p><p>2\. Nhập metadata cho tài liệu</p><p>3\. Nếu nhập đầy đủ dữ liệu, cho phép chọn file để tải lên</p><p>4\. Kiểm tra file hợp lệ, lưu vào hệ thống.</p><p></p>|
|**Luồng phụ**|Ở bước 3, 4, nếu có bất kỳ thông tin vào không hợp lệ sẽ thông báo lỗi.|

` `**Xem danh sách phụ đề/document**


|**Use Case Name**|Xem danh sách phụ đề/document|
| :- | :- |
|**Mô tả**|Cho phép translator xem các phụ đề và tài liệu đã được dịch trên hệ thống.|
|**Điều kiện thêm**||
|**Luồng chính**|<p>1\. Trên Dashboard, bấm vào một trong hai tính năng Xem danh sách phụ đề / Xem danh sách document</p><p>2\. Hiển thị danh sách</p>|
|**Luồng phụ**||
**Tải phụ đề/document**


|**Use Case Name**|Tải phụ đề/document|
| :- | :- |
|**Mô tả**|Cho phép translator tải các phụ đề và tài liệu đã được dịch trên hệ thống.|
|**Điều kiện thêm**|Đang ở trong trang danh sách phụ đề/document|
|**Luồng chính**|<p>1\. Trên danh sách phụ đề/document, Translator có thể bấm vào bất kỳ phụ đề/document nào.</p><p>2\. Cho phép Translator tải xuống.</p>|
|**Luồng phụ**||
**Tìm kiếm theo bộ lọc**


|**Use Case Name**|Tìm kiếm theo bộ lọc|
| :- | :- |
|**Mô tả**|Cho phép translator tìm và lọc phụ đề và tài liệu đã được dịch trên hệ thống.|
|**Điều kiện thêm**||
|**Luồng chính**|<p>1\. Trong dashboard, chọn tính năng tìm kiếm.</p><p>2\. Hiển thị bộ lọc: Tên bản dịch, Url, Người dịch, Course ID, Video ID và cho phép translator tùy chỉnh.</p><p>3\. Lọc database và hiện kết quả</p>|
|**Luồng phụ**||
**Xóa phụ đề/document**


|**Use Case Name**|Xóa phụ đề/document|
| :- | :- |
|**Mô tả**|Cho phép translator xóa phụ đề và tài liệu đã được dịch trên hệ thống.|
|**Điều kiện thêm**|Đang ở trang lọc phụ đề/document|
|**Luồng chính**|<p>1\. Khi có kết quả lọc phụ đề/document, người dùng có thể bấm nút xóa.</p><p>2\. Xác nhận có muốn xóa hay không.</p><p>3\. Nếu xác nhận, xóa phụ đề, hiện thông báo xóa thành công.</p>|
|**Luồng phụ**|<p>Ở bước 2, nếu không xác nhận xóa phụ đề thì không làm gì cả.</p><p>Ở bước 3, nếu gặp lỗi khi xóa, thì hiển thị lỗi.</p>|

**Chỉnh sửa tài liệu đã được dịch:**


|**Use Case Name**|Chỉnh sửa tài liệu đã được dịch|
| :- | :- |
|**Mô tả**|Translator có thể chỉnh sửa các bản dịch trên hệ thống|
|**Điều kiện thêm**|Đang ở trang lọc phụ đề/document|
|**Luồng chính**|<p>1\. Khi có kết quả lọc phụ đề/document, người dùng có thể bấm nút chỉnh sửa.</p><p>2\. Cho phép chỉnh sửa metadata.</p><p>3\. Kiểm tra metadata hợp lệ, lưu vào hệ thống.</p><p>4\. Cho phép upload file mới</p><p>5\. Kiểm tra file hợp lệ, lưu vào hệ thống.</p><p></p>|
|**Luồng phụ**|<p>Ở bước 3, 5, nếu có bất kỳ thông tin vào không hợp lệ sẽ thông báo lỗi.</p><p>Ở bước 2, 4, nếu bấm hủy thì không lưu thay đổi.</p>|

#### ***Usecase của Admin***
**\* Điều kiện của Admin: Là một User và có quyền Admin, và đã đăng nhập vào hệ thống admin.**

` `**Xóa tài khoản**


|**Use Case Name**|Xóa tài khoản|
| :- | :- |
|**Mô tả**|Cho phép Admin xóa các tài khoản trên hệ thống|
|**Điều kiện thêm**||
|**Luồng chính**|<p>1\. Trên giao diện quản lý người dùng, cho phép xóa người dùng bất kỳ.</p><p>2\. Xác nhận có muốn xóa hay không.</p><p>3\. Nếu xác nhận, xóa người dùng, hiện thông báo xóa thành công.</p>|
|**Luồng phụ**|<p>Ở bước 2, nếu không xác nhận xóa thì không làm gì cả.</p><p>Ở bước 3, nếu gặp lỗi khi xóa, thì hiển thị lỗi.</p>|

**Xóa quyền translator**


|**Use Case Name**|Xóa quyền translator|
| :- | :- |
|**Mô tả**|Cho phép Admin xóa quyền translator ra khỏi các tài khoản trên hệ thống|
|**Điều kiện thêm**||
|**Luồng chính**|<p>1\. Trên giao diện quản lý người dùng, cho phép xóa quyền từ người dùng bất kỳ.</p><p>2\. Xác nhận có muốn xóa hay không.</p><p>3\. Nếu xác nhận, xóa quyền, hiện thông báo xóa thành công.</p>|
|**Luồng phụ**|<p>Ở bước 2, nếu không xác nhận xóa thì không làm gì cả.</p><p>Ở bước 3, nếu gặp lỗi khi xóa, thì hiển thị lỗi.</p>|

**Thêm quyền translator**


|**Use Case Name**|Xóa quyền translator|
| :- | :- |
|**Mô tả**|Cho phép Admin thêm quyền translator vào các tài khoản trên hệ thống|
|**Điều kiện thêm**||
|**Luồng chính**|<p>1\. Trên giao diện quản lý người dùng, cho phép thêm quyền vào người dùng bất kỳ.</p><p>2\. Xác nhận có muốn thêm hay không.</p><p>3\. Nếu xác nhận, thêm quyền, hiện thông báo thêm thành công.</p>|
|**Luồng phụ**|<p>Ở bước 2, nếu không xác nhận thêm thì không làm gì cả.</p><p>Ở bước 3, nếu gặp lỗi khi thêm, thì hiển thị lỗi.</p>|

#### ***Usecase của Reviewer***
**\* Điều kiện của Reviewer: Là một User và có quyền Reviewer, và đã đăng nhập vào hệ thống.**

**Duyệt phụ đề:**

<a name="_heading=h.26in1rg"></a> 

|**Use Case Name**|Duyệt phụ đề|
| :- | :- |
|**Mô tả**|Reviewer có thể duyệt các phụ đề do Translator dịch|
|**Điều kiện thêm**|Phải có các phụ đề đã dịch và chưa được duyệt.|
|**Luồng chính**|<p>1\. Trên Dashboard, bấm vào duyệt phụ đề</p><p>2\. Xem các thông tin về phụ đề chưa được duyệt</p><p>3\. Xem và xác nhận có duyệt một phụ đề hay không</p><p>4\. Nếu không duyệt phụ đề nào đó, để lại comment</p>|
|**Luồng phụ**||

###**Sơ đồ use case tổng quát của hệ thống**
![](UML.png)

**Hình 2 Sơ đồ use case tổng quát**

### **Class Diagram**
![](class.png)

![](classDAO.png)

### **Sequence Diagram**
![](sequence.png)

### **Activity Diagram**


