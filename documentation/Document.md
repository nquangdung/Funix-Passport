**FUNiX**


![](Aspose.Words.3e3cffc2-4c05-43fb-9d3c-394625237b57.001.png)



**Tài liệu đặc tả yêu cầu**

***FUNiX Passport***






**Bảng thuật ngữ**

Cung cấp tổng quan về bất kỳ định nghĩa nào mà người đọc nên hiểu trước khi đọc tiếp.

|API Key|Chuỗi ký tự đặc biệt, duy nhất được nhà cung cấp cấp cho user để xác thực và ủy quyền khi truy cập vào API|
| - | - |
|API Token|Chuỗi mã hóa đại diện cho quyền truy cập vào tài nguyên cụ thể, xác thực quyền truy cập và xác thực rõ user cụ thể nào thực hiện yêu cầu|
|Manifest V3|Nền tảng kỹ thuật mới nhất dành cho Extension trên Chrome|
|Spring Boot|Framework open-source dựa trên Java|
|RESTful API|Tiêu chuẩn thiết kế API dựa trên kiến trúc REST cho phép hệ thống client – server thiết bị giao tiếp trao đổi dữ liệu thong qua giao thức HTTP (GET, POST, PUT, DELETE)|
|DBMS|Database Managemnet System – Hệ CSDL|
|AWS S3|Dịch vụ lưu trữ đối tượng trên đám mây do Amazon Web Services cung cấp|
|File Server|Máy tính trung tâm trên mạng dùng để lưu trữ, quản lý, và chia sẻ tệp dữ liệu (tài liệu, hình ảnh, video) cho các máy trạm (workstations)|













**Mục lục**

[**1. Giới thiệu tổng quan về dự án**	3](#_toc229014967)

[1.1 Tổng quan dự án	3](#_toc229014968)

[1.2 Phạm vi dự án	3](#_toc229014969)

[**2. Yêu cầu và đặc tả dự án**	4](#_toc229014970)

[2.1 Yêu cầu chức năng	4](#_toc229014971)

[2.2 Yêu cầu phi chức năng	5](#_toc229014972)

[2.3 Đặc tả phần mềm	6](#_toc229014973)

[**3. Kiến trúc và thiết kế phần mềm**	8](#_toc229014974)

[3.1 Kiến trúc phần mềm	8](#_toc229014975)

[3.2 Vẽ sơ đồ Use Case và đặc tả Use Case	10](#_toc229014976)

[3.2.1 Use Case của User :	11](#_toc229014977)

[3.2.2 Use Case của Translator:	13](#_toc229014978)

[3.2.3 Use Case của Admin:	15](#_toc229014979)

[3.2.4 Use Case của Reviewer:	15](#_toc229014980)

[3.3 Sơ đồ Use Case tổng quát (đã bao gồm phần nâng cao – actor Reviewer)	18](#_toc229014981)

[3.4 Sơ đồ Class Diagram	19](#_toc229014982)

[3.5 Sequence Diagram	23](#_toc229014983)

[3.6 Activity Diagram	24](#_toc229014984)









**Tài liệu đặc tả**
# <a name="_toc229014871"></a><a name="_toc229014967"></a>**1. Giới thiệu tổng quan về dự án**
## <a name="_toc229014872"></a><a name="_toc229014968"></a>**1.1 Tổng quan dự án**
**- Dự án:** Xây dựng hệ thống hỗ trợ sinh viên FUNiX xem tài liệu/video bằng tiếng Việt thông qua phụ đề hoặc bản dịch Document

**- Mục tiêu của dự án:**

\+ Hỗ trợ sinh viên dễ dàng tiếp cận nội dung kiến thức bài học bằng tiếng Việt thay vì phải xem phụ đề tiếng Anh có sẵn

\+ Cung cấp công cụ cho các translator quản lý, upload và cập nhật các bản dịch nhanh chóng và chất lượng cao

## <a name="_toc229014873"></a><a name="_toc229014969"></a>**1.2 Phạm vi dự án**
**- Hai thành phần chính trong hệ thống:** 

**+ Backend:** 

- Xây dựng CSDL để lưu trữ Metadata và quản lý tệp tin dịch thuật
- Cung cấp các API bảo mật (Sử dụng Token/API Key) để giao tiếp với Extension 
- Cung cấp giao diện quản lý cho User, Translator và Admin 

**+ Extension:** Giao tiếp với Backend, trích xuất thông tin URL, gửi request và hiển thị bản dịch lên trình duyệt 

- Chạy trực tiếp trên trình duyệt Google Chrome
- Tự động nhận diện ngữ cảnh (URL, Video ID, Course ID) để Backend truy xuất bản dịch tương ứng. 
- Nếu có bản dịch thì Extension hiển thị popup cho người dùng để lựa chọn xem có muốn xem dịch không, user đồng ý => Hiển thị bản dịch 

**- Đối tượng sử dụng hệ thống:** 

\+ User (Sinh viên): Sử dụng bản dịch thông qua Extension

\+ Translator (Dịch thuật viên): Đóng góp nội dung bản dịch

\+ Admin (Quản trị viên): Điều phối hệ thống và quản lý người dùng và dịch thuật viên

# <a name="_toc229014874"></a><a name="_toc229014970"></a>**2. Yêu cầu và đặc tả dự án**
## <a name="_toc229014875"></a><a name="_toc229014971"></a>**2.1 Yêu cầu chức năng**
**- Hệ thống chia thành 4 nhóm chức năng chính:**

**a. Quản lý Tài khoản:** 

\- Xóa tài khoản người dùng: Gỡ bỏ hoàn toàn tài khoản khỏi hệ thống 

\- Phân quyền: Chuyển đổi linh hoạt giữa các quyền User và Translator (Thêm quyền và xóa quyền)

**b. Quản lý Bản dịch:**

\- Upload Phụ đề: Nhập Metadata (Tên, URL, Course/Video ID) đính kèm file phụ đề.

\- Upload Document: Nhập Tên/URL bản dịch và đính kèm file tài liệu 

\- Dashboard: Hiển thị danh sách bản dịch và tải file dịch của Phụ đề và Document

\- Thao tác dữ liệu: Tìm kiếm theo bộ lọc, xóa file, tải xuống file, chỉnh sửa thông tin (Metadata hoặc Re-up file)

\- Kiểm duyệt bản dịch (Bổ sung): Duyệt bản dịch và Từ chối bản dịch 

**c. Hiển thị Bản dịch:**

\- Trích xuất dữ liệu: Tự động trích xuất URL, Video/Course ID từ thời điểm trang web hiện tại

\- Giao tiếp với Backend: Gửi request tìm kiếm bản dịch khớp với thông tin đã trích xuất (Nếu là web thuộc nguồn MOOC: gửi course\_id và video\_id, còn nếu là Document: gửi toàn bộ URL)

\- Tương tác với người dùng: Hiển thị Popup xác nhận xem bản dịch và thực hiện nhúng bản dịch vào trang web 

**d. Cài đặt hệ thống** 

\- Xác thực trạng thái Đăng nhập/Đăng xuất cho mọi đối tượng

\- Trạng thái Bật/Tắt hoạt động của Extension thông qua giao diện UI

## <a name="_toc229014876"></a><a name="_toc229014972"></a>**2.2 Yêu cầu phi chức năng** 
**a. Tính bảo mật**

\- Sử dụng cơ chế Token hoặc API Key cho mọi yêu cầu truy cập từ Extension lên Backend

\- Bảo mật Database: Dữ liệu nhạy cảm từ người dùng phải được mã hóa. Chỉ có những tài khoản có quyền như Admin hay Translator mới có quyền được thao tác dữ liệu trong Database

\- Không thu thập thông tin cá nhân của sinh viên (người dùng) khi duyệt web, chỉ trích xuất URL và các ID liên quan đến bài học

**b. Tính sẵn sàng và khả năng đáp ứng** 

\- Hệ thống luôn sẵn sàng 24/7 để phục vụ nhu cầu học tập mọi lúc của sinh viên 

\- Đảm bảo hệ thống phải luôn trong trạng thái ổn định, vẫn phản hồi ngay cả khi có nhiều Translator cùng upload dữ liệu hoặc nhiều User cùng truy cập bản dịch cùng lúc

**c. Hiệu suất**

\+ Thời gian tính từ lúc sinh viên (user) vào Website cho đến khi hiển thị bản dịch cho sinh viên trong (bao gồm trích xuất URL, và nhận phản hồi từ Backend) phải dưới 1 giây (<1.0s)

\+ Các tác vụ/thao tác của Translator (Upload, Edit, Submit) phải có tốc độ phản hồi/xử lý không quá 0.5 giây (<0.5s)

\+ Tối ưu hóa Extension, tiêu tốn ít tài nguyên trình duyệt (RAM/CPU) để không làm chậm máy tính của sinh viên
## <a name="_toc229014877"></a><a name="_toc229014973"></a>**2.3 Đặc tả phần mềm** 
\- Môi trường chạy:

\+ Extension: Tương thích với Google Chrome (Manifest V3)

\+ Backend: Chạy trên môi trường server hỗ trợ Java (Spring Boot) hoặc Node.js 

\- Giao thức kết nối: RESTful API để truyền tải dữ liệu JSON giữa Extension và Backend

\- Về dữ liệu và cách thức lưu trữ:

\+ Cơ sở dữ liệu: Sử dụng các DBMS như MySQL hoặc PostgreSQL để lưu trữ các metadata với các ràng buộc về tính toàn vẹn dữ liệu

\+ Lưu trữ tệp tin: Các file vật lý như Phụ đề và Document không lưu trực tiếp trong Database mà lưu trên hệ thống File Server hoặc Cloud Storage (AWS S3). Database chỉ lưu đường dẫn lưu trữ URL tới các tệp này

\+ Xác thực quyền hạn truy cập: Sử dụng cơ chế JSON Web Token để duy trì phiên đăng nhập và kiểm tra quyền hạn cho các API chỉnh sửa dữ liệu 

\- Về metadata:

|**Loại bản dịch**|**Các trường dữ liệu (Metadata)**|
| :-: | :-: |
|**Video** **(Subtitle)**|ID, Translator, UploadedDate (tự động); Name, URL, Video ID, Course ID, VI Subtitle URL, En Subtitle URL (nhập/tạo).|
|**Tài liệu (Document)**|ID, Translator, UploadedDate (tự động); Name, URL, Document URL (nhập/tạo).|


\- Về giao tiếp API: 

\+ API lấy bản dịch cho Extension:

- Endpoint: GET /api/v1/translations/search
- Tham số truyền vào (gửi request cho Backend):

  + url: Toàn bộ đường dẫn web (Dùng cho Documents)

  + course\_id: Mã khóa học (Dùng cho MOOC)

  + video\_id: Mã định danh video (Dùng cho MOOC)

- Dữ liệu trả về Response Body từ Backend– JSON

\+ API Upload bản dịch cho Translator:

- Endpoint: POST /api/v1/translator/upload
- Định dạng: multipart/form-data
- Các trường dữ liệu:

  + file: tệp tin .str, .vtt, .pdf hoặc .docx

  + metadata: Chuỗi JSON chứa name, course\_id, video\_id

- Cơ chế bảo mật: Header phải có dòng “Authorization: Bearer <JWT\_Token>”
- Mã trạng thái phản hồi thành công (Status 200 Created): Trả về ID của bản dịch vừa tạo để có thể xem ngay trên Dashboard

\+ API Quản lý người dùng cho Admin:

- Endpoint: PATCH /apiv1/admin/users/{user\_id}/role
- Tham số: role\_id (01: User và 02: Translator)
- Chỉ có những tài khoản có quyền Admin (xác thực qua Token) mới có thể gọi API này

\+ API Phê duyệt/Từ chối bản dịch cho Reviewer:

- Endpoint: PATCH /api/v1/reviewer/translations/{translation\_id}/status
- Tham số truyền vào (JSON Body):

  + status: "PUBLISHED" (Phê duyệt) hoặc "REJECTED" (Từ chối)

  + reviewNote: Lý do từ chối (bắt buộc nếu status là REJECTED)

- Cơ chế bảo mật: Xác thực qua Token (Role Reviewer).
- Mã trạng thái phản hồi:

  + 200 OK: Cập nhật thành công. Nếu là PUBLISHED, bản dịch sẽ lập tức hiển thị trên Extension.

  + 403 Forbidden: Nếu Token không có quyền Reviewer.

\+ Về cơ chế hiển thị trên trình duyệt (Content Scripts Injection): Giao tiếp giữa Extension và các Website như Coursera hay Udemy

- Cơ chế trích xuất: Extension sử dụng Regex (Biểu thức chính quy) để tách “v1” từ URL ngay khi website tải xong 
- Cơ chế hiển thị: Nếu là video thì Extension nhúng 1 thẻ <track> vào một thẻ <video> của trang web để hiển thị phụ đề tiếng Việt. Còn là Document thì Extension sẽ tạo 1 lớp Overlay hoặc nút “Xem bản dịch” trên màn hình 


# <a name="_toc229014878"></a><a name="_toc229014974"></a>**3. Kiến trúc và thiết kế phần mềm**
## <a name="_toc229014879"></a><a name="_toc229014975"></a>**3.1 Kiến trúc phần mềm**
Kiến trúc phần mềm phù hợp với dự án: Kiến trúc **Client-Server** kết hợp với kiến trúc **Phân tầng (Layered Architecture)** ở phía Backend.

**- Mô hình tổng quát Client-Server: Hệ thống được chia làm 2 phần giao tiếp qua môi trường mạng** 

\+ Client (Extension): Đóng vai trò là công cụ thu thập các dữ liệu URL, ID và hiển thị kết quả ra ngoài website. Không xử lý logic nghiệp vụ quá phức tạp hay truy cập trực tiếp vào Databae để đảm bảo tốc độ thao tác nhanh chóng.

\+ Server (Backend): Có vai trò là trung tâm xử lý logic nghiệp vụ, xác định quyền hạn truy cập cho các user, quản lý dữ liệu Database và trả về dữ liệu tương ứng với Request của của Client.

**- Mô hình Phân tầng của Backend: Chia làm 4 tầng**  

\+ Tầng 1 – API Layer: Tiếp nhận các request từ Extension và Dashboard của Translator, điều hướng dữ liệu

\+ Tầng 2 – Bussines Logic: Xử lý tính toán các thao tác và quy tắc nghiệp vụ (Ví dụ: xử lý logic tìm kiếm bản dịch tối ưu, kiểm tra bản upload file dịch có đúng định dạng không, xử lý thao tác xóa file dịch của Document hoặc Phụ đề,…)

\+ Tầng 3 – Data Access Object (DAO): Quản lý thao tác với Database, thực thi các câu lệnh truy vấn SQL hoặc NoSQL để lấy Metadata tương ứng

\+ Tầng 4 – Database: Lưu trữ metadata vật lý (DBMS như MySQL, PostgreSQL,..)

**- Lý do chọn kiến trúc Client-Server kết hợp với kiến trúc Phân tầng bên trong Backend:**

\+ Với Client-Server:

- Decoupling (Tính độc lập): Extension chỉ chịu trách nhiệm phần UI trong khi Backend lưu trữ tất cả tài nguyên dữ liệu, và thực hiện tất cả các thao tác tính toán xử lý logic. Giusp cho hệ thống nhẹ hơn, việc sao lưu quản lý, cập nhật và đồng bộ dữ liệu dễ dàng hơn. 
- Đáp ứng được yêu cầu về Hiệu suất: Client-Server cho phép chúng ta xử lý yêu cầu tại Server và trả về kết quả JSON không tốn bộ nhớ qua môi trường mạng, đảm bảo thời gian hiển thị bản dịch nhanh nhất.
- Dễ dàng cập nhật, khi cần thay đổi logic thao tác hoặc sửa các lỗi Database thì chỉ cần cập nhật bên Server. User vẫn dùng các Extension phiên bản cũ mà không bị gián đoạn dịch vụ
- Khả năng mở rộng (Scalability): Hệ thống có thể dễ dàng nâng cấp Server hoặc thêm nhiều Server khi số lượng sinh viên truy cập tăng đột biến vào giờ cao điểm mà không cần cập nhật lại Extension trên máy user.

\+ Với Phân tầng trong Backend:

- Đáp ứng yêu cầu Bảo mật, cho phép đặt một "cửa chặn" tại class Controller để kiểm tra API Key/Token ngay khi có yêu cầu từ Extension.
- Lớp DAO (Data Access Object) cô lập hoàn toàn Database, ngăn chặn các truy cập trực tiếp từ bên ngoài, bảo vệ an toàn dữ liệu metadata.
- Đáp ứng yêu cầu Tốc độ xử lý (< 0.5s) khi luồng dữ liệu đi thẳng và rõ ràng. Ta có thể dễ dàng nhúng thêm một lớp Caching (như Redis) ở giữa lớp Service và DAO để trả về kết quả ngay lập tức cho các video phổ biến mà không cần truy vấn Database.
- Dễ bảo trì (Modifiability): Việc sử dụng các lớp DAO (như UserDAO, TranslationDAO) giúp tách biệt mã nguồn SQL khỏi logic nghiệp vụ. Nếu hệ thống yêu cầu thay đổi cách lưu trữ (ví dụ từ MySQL sang Cloud Database), ta chỉ cần viết lại lớp DAO mà không phải sửa lại toàn bộ hệ thống.
- Kiến trúc này hỗ trợ tốt cho việc hiện thực hóa các lớp kế thừa (User > Translator > Admin) và quản lý 2 loại bản dịch khác nhau (Subtitle & Document) thông qua các Class chuyên trách.

## <a name="_toc229014880"></a><a name="_toc229014976"></a>**3.2 Vẽ sơ đồ Use Case và đặc tả Use Case** 
**- Danh sách Use Case theo từng Actor**

|**Actor**|**Use Case**|
| :-: | :-: |
|**User**|<p>- Đăng nhập/Đăng xuất</p><p>- Bật/Tắt Extension</p><p>- Xem bản dịch trên Extension </p><p></p>|
|**Translator**|<p>- Update file dịch Document/Phụ đề</p><p>- Xem danh sách file dịch</p><p>- Tải xuống file đã dịch</p><p>- Tìm kiếm file theo bộ lọc</p><p>- Xóa các file Document/Phụ đề</p><p>- Chỉnh sửa thông tin</p>|
|**Admin**|<p>- Xóa tài khoản người dùng</p><p>- Cấp/Xóa quyền Translator </p>|
|**Reviewer**|<p>- Duyệt bản dịch</p><p>- Từ chối bản dịch</p>|
### <a name="_toc229014881"></a><a name="_toc229014977"></a>**3.2.1 Use Case của User :**
**Use Case 01:** 

|<p>**Use Case**</p><p>**Name**</p>|Đăng nhập|
| :- | :- |
|**Mô tả**|User đăng nhập tài khoản vào hệ thống và sử dụng chức năng Extension của FUNiX|
|**Điều kiện**|User chưa đăng nhập vào hệ thống |
|**Luồng chính**|<p>1\. User truy cập vào trang web Funix. Nhấn vào mục “Login"</p><p>2\. Hệ thống hiển thị Form Login.</p><p>3\. User nhập vào các thông tin đăng nhập.</p><p>4\. Nếu thông tin đăng nhập đúng, cập nhật thông tin vào hệ thống.</p>|
|**Luồng phụ**|Ở bước 4, nếu thông tin đăng nhập sai sẽ hiển thị thông báo cho người dùng.|

**+ Use Case 02:** 

|<p>**Use Case**</p><p>**Name**</p>|Xem bản dịch qua Extension|
| :- | :- |
|**Mô tả**|Hệ thống tự động nhận diện video/document và hiển thị bản dịch tiếng Việt cho User|
|**Điều kiện**|Đã cài đặt Extension từ Chrome và bật Extension trong trạng thái “On”  (Đã bật)|
|**Luồng chính**|<p>1. ` `User truy cập trang web MOOC (Udemy, Coursera, hoặc trang tài liệu) </p><p>2. Extension tự động trích xuất URL và ID từ video hoặc course</p><p>3. Extension gửi request đến Backend và kèm theo ID hoặc URL</p><p>4. Backend sẽ kiểm tra trong database và gửi response với đường dẫn file dịch tương ứng</p><p>5. Extension sẽ pop up ra màn hình “FUNiX Passport” với 2 lựa chọn “Phụ Đề” và “Keep Original” (Bật/Tắt Extension)</p><p>6. User chọn “Phụ Đề”</p><p>7. Extension nhúng phụ đề vào trình phát video hoặc hiển thị nội dung dịch cho document (tài liệu)</p>|
|**Luồng phụ**|Bước 4: Nếu không tìm thấy bản dịch, Extension sẽ ở trạng thái chờ và không hiển thị Popup lựa chọn dịch.|

**+ Use Case 03:** 

|<p>**Use Case**</p><p>**Name**</p>|Đăng xuất|
| :- | :- |
|**Mô tả**|User muốn thoát ra ngoài khỏi hệ thống|
|**Điều kiện**|User đang đăng nhập vào hệ thống |
|**Luồng chính**|<p>1\. User truy cập vào trang web Funix. Nhấn vào mục “Log out"</p><p>2\. Hệ thống hiển thị Pop-up xác nhận “Có chắc chắn muốn đăng xuất khỏi hệ thống”” </p><p>3\. User ấn vào lựa chọn “Có” để xác nhận đăng xuất </p><p>4\. Hệ thống thực hiện đăng xuất và hiển thị thông báo “Đã đăng xuất thành công”</p>|
|**Luồng phụ**|Ở bước 2, nếu User chọn option “Không”thì hệ thống quay về giao diện ban đầu |

### <a name="_toc229014882"></a><a name="_toc229014978"></a>**3.2.2 Use Case của Translator:**
**+ Use Case 04:** 

|<p>**Use Case**</p><p>**Name**</p>|**Upload bản dịch** |
| :- | :- |
|**Mô tả**|Translator tải bản dịch thuật lên database và khai báo thông tin về bản dịch|
|**Điều kiện**|Có API Key/Token của Translator và được cấp quyền chỉnh sửa và upload bản dịch|
|**Luồng chính**|<p>1. Hệ thống chọn chức năng Upload (Subtitle/Document)</p><p>2. Hệ thống hiển thị form nhập dữ liệu</p><p>3. Include: Translator nhập các metadata gồm: Name, URL, Video/Course ID</p><p>4. Translator đính kèm file từ máy tính </p><p>5. Nhấn Submit để tải dữ liệu </p><p>6. Hệ thống kiểm tra định dạng file và các thuộc tính metadata cần thiết cho bản dịch của Subtitle/Document</p><p>7. Khi các kiểm tra hợp lệ, lưu file vào storage và lưu nhận thông tin vào Database (gồm các trường dữ liệu đã liệt kê ở “Đặc tả metadata” trong phần “Đặc tả phần mềm”)</p><p>8. Translator upload bản dịch thành công, kết thúc Use Case</p>|
|**Luồng phụ**|<p>- Ở bước 6: Nếu các trường dữ liệu bị để trống hoặc nhập sai, hệ thống backend kiểm tra và trả về lỗi trong thời gian < 0.5 giây sau khi ấn Submit</p><p>+ Hiển thị thông báo lỗi và cảnh báo đỏ khi nhập sai hoặc thiếu</p><p>+ Giữ lại các dữ liệu đã nhập đúng, người dùng không phải nhập lại từ đầu</p><p>- Ở bước 7: Nếu Metadata đã được lưu vào Database nhưng việc đẩy file vật lý lên Storage bị thất bại thì hệ thống sẽ thông báo “Hệ thống lưu trữ đang bận, vui lòng thử lại sau!”</p>|

**+ Use Case 05:** 

|<p>**Use Case**</p><p>**Name**</p>|**Tìm kiếm bản dịch** |
| :- | :- |
|**Mô tả**|Giúp Translator nhanh chóng tìm lại bản dịch cũ để chỉnh sửa hoặc kiểm tra |
|**Điều kiện**|Có API Key/Token của Translator và được cấp quyền chỉnh sửa và upload bản dịch|
|**Luồng chính**|<p>1\. Translator nhập từ khóa (Tên bản dịch, URL, người dịch, Course/Video ID)</p><p>2\. Hệ thống thực hiện lọc và hiển thị kết quả tương ứng trong < 0.5 giây </p>|
|**Luồng phụ**|Nếu không tìm thấy dữ liệu, hệ thống sẽ trả về thông báo “Không tìm thấy bản dịch!” |


**+ Use Case 06:** 

|<p>**Use Case**</p><p>**Name**</p>|**Chỉnh sửa file dịch**|
| :- | :- |
|**Mô tả**|Cập nhật thông tin hoặc thay thế file dịch cũ bằng bản dịch mới |
|**Điều kiện**|Có API Key/Token của Translator và được cấp quyền chỉnh sửa và upload bản dịch|
|**Luồng chính**|<p>1. Translator thực hiện thao tác “Tìm kiếm bản dịch” trên Dashboard</p><p>2. Extend: Từ kết quả tìm kiếm, Translator chọn option “Chỉnh sửa file dịch”</p><p>3. Ở lựa chọn “Chỉnh sửa file dịch” sẽ có 2 option: Chỉnh sửa các Metadata và Re-up file dịch mới thay thế file cũ</p><p>1. 4. Hệ thống cập nhật dữ liệu mới và tự động ghi lại thời gian chỉnh sửa mới nhất </p>|
|**Luồng phụ**|<p>- Khi thực hiện Re-up file mới, nếu re-up sai định dạng file so với bản dịch gốc: Hệ thống Backend thực hiện kiểm tra và đưa ra thông báo chú thích “Vui lòng upload đúng định dạng file” trong vòng < 0.5 giây</p><p>- Xảy ra lỗi lưu trữ vật lý sau khi Metadata được chỉnh sửa: Khi Metadata đã được cập nhật thành công nhưng trong quá trình ghi đè file cũ trên Storage lại bị lỗi => Hệ thống sử dụng cơ chế Transaction, phải Rollback về Metadata cũ trong Database và ngoài giao diện hiển thị thông báo “Cập nhật metadata thất bại. Vui lòng thử lại khi khác”</p>|

### <a name="_toc229014883"></a><a name="_toc229014979"></a>**3.2.3 Use Case của Admin:**
**+ Use Case 06**

|<p>**Use Case**</p><p>**Name**</p>|**Cấp/Xóa quyền Translator** |
| :- | :- |
|**Mô tả**|Thay đổi vai trò của người dùng trong hệ thống|
|**Điều kiện**|Ở trạng thái đăng nhập vào hệ thống quản trị |
|**Luồng chính**|<p>1. Admin đăng nhập vào hệ thống quản trị người dùng</p><p>2. Tìm kiếm người dùng bằng email hoặc ID </p><p>3. Có 2 lựa chọn “Thêm quyền” để nâng cấp User -> Translator, “Xóa quyền” để từ Translator -> User</p><p>4. Hệ thống cập nhật Token/API Key của người dùng đó </p>|
|**Luồng phụ**|<p>- Ở bước 2: Nếu người dùng không tồn tại </p><p>+ Trường hợp Admin nhập sai ID hoặc Email => Không tìm thấy dữ liệu tồn tại => Khi thực hiện thao tác tìm kiếm, hệ thống sẽ xử lý trả về lỗi < 0.5 giây với thông báo “Không tìm thấy người dùng với Email hoặc ID này!”</p><p>+ Ở bước 3: Nếu cấp trùng lặp quyền hạn => Hệ thống giao diện Admin disable nút cáp quyền, còn nếu vẫn gửi request Backend sẽ trả về thông báo “Người dùng này đã được cấp quyền Translator”</p>|

### <a name="_toc229014884"></a><a name="_toc229014980"></a>**3.2.4 Use Case của Reviewer:**
**+ Use Case 07**

|<p>**Use Case**</p><p>**Name**</p>|**Duyệt bản dịch**|
| :- | :- |
|**Mô tả**|Reviewer xác nhận nội dung bản dịch chính xác và cho phép hiển thị lên hệ thống.|
|**Điều kiện**|Bản dịch phải ở trạng thái PENDING.|
|**Luồng chính**|<p>1. Reviewer đăng nhập và chọn danh sách "Pending" từ Dashboard.</p><p>2. Hệ thống hiển thị danh sách các bản dịch có status = PENDING.</p><p>3. Reviewer chọn một bản dịch để kiểm tra nội dung.</p><p>4. Reviewer nhấn nút **"Approve"**.</p><p>5. Hệ thống gọi API PATCH với body { "status": "PUBLISHED" }.</p><p>6. Hệ thống cập nhật status, Reviewer\_ID và Review\_Date vào Database.</p><p>7. Hệ thống thông báo thành công. Bản dịch sẵn sàng để Extension truy xuất, hiển thị cho User</p>|
|**Luồng phụ**|- Ở bước 4 khi nội dung bản dịch không hợp lệ:** Reviewer chuyển sang Use Case "Từ chối bản dịch". (Reject)|

**+ Use Case 08**

|<p>**Use Case**</p><p>**Name**</p>|**Từ chối bản dịch**|
| :- | :- |
|**Mô tả**|Reviewer từ chối bản dịch không đạt yêu cầu và yêu cầu Translator chỉnh sửa lại.|
|**Điều kiện**|Bản dịch phải ở trạng thái PENDING.|
|**Luồng chính**|<p>1. Reviewer xem chi tiết bản dịch trong danh sách chờ duyệt</p><p>2. Reviewer nhấn nút **"Reject"**.</p><p>3. Hệ thống hiển thị hộp thoại yêu cầu nhập **Review\_Note** (Lý do từ chối).</p><p>4. Reviewer nhập lý do và nhấn "Xác nhận".</p><p>5. Hệ thống gọi API PATCH gửi kèm status: REJECTED và review\_note.</p><p>6. Hệ thống cập nhật Database, bản dịch sẽ không được hiển thị trên Extension.</p><p>7. Hệ thống gửi thông báo/trạng thái mới về Dashboard của Translator.</p>|
|**Luồng phụ**|- Ở bước 4 nếu Reviewer để trống phần lý do:** Nút “Xác nhận” bị vô hiệu hóa và hệ thống đưa ra cảnh báo “Yêu cầu nhập lý do”|
















## <a name="_toc229014885"></a><a name="_toc229014981"></a>**3.3 Sơ đồ Use Case tổng quát (đã bao gồm phần nâng cao – actor Reviewer)**
![D:\FUNIX ASM\SWE102x - Nhập môn kỹ thuật phần mềm\ASM2\fx-18096-assignment-02-swe\documentation\diagram\Usecase Diagram.png](Aspose.Words.3e3cffc2-4c05-43fb-9d3c-394625237b57.002.png)


## <a name="_toc229014886"></a><a name="_toc229014982"></a>**3.4 Sơ đồ Class Diagram**
**a. Cấu trúc Class về các Vai trò (Role) trong hệ thống (Quan hệ Kế thừa)**\


|**Tên Class**|**Thông tin cơ bản**|**Phương thức**|
| :-: | :-: | :-: |
|**User**|<p>- username: tên người dùng</p><p>- password: mật khẩu</p><p>- email</p>|<p>- login(): Đăng nhập</p><p>- logout(): Đăng xuất</p>|
|**Translator (Kế thừa từ User)**|<p>- username: tên người dùng</p><p>- password: mật khẩu</p><p>- email</p><p>- translatorID</p>|<p>- login(): Đăng nhập</p><p>- logout(): Đăng xuất</p><p>(Bổ sung)</p><p>uploadSubtitle(): Đăng phụ đề cho video</p><p>uploadDoc(): Đăng bản dịch cho tài liệu</p><p>searchTranslation(): Tìm kiếm bản dịch</p><p>editTranslation(): Chỉnh sửa bản dịch </p><p>deleteTranslation(): Xóa bản dịch </p><p></p>|
|**Admin (Kế thừa từ User)**|<p>- username: tên người dùng</p><p>- password: mật khẩu</p><p>- email</p>|<p>- login(): Đăng nhập</p><p>- logout(): Đăng xuất</p><p>(Bổ sung)</p><p>deleteUser(): Xóa tài khoản người dùng</p><p>assignRole(): Cấp/Xóa quyền Translator</p>|

**b. Cấu trúc thông tin bản dịch (Quan hệ Kế thừa):**

**- Mô tả: Quản lý loại bản dịch Subtitle và Document** 

**\*Class Translation (Class cha):** 

**- Chứa các thuộc tính chung:**

\+ ID: Mã bản dịch

\+ name: Tên bản dịch

\+ url: Link website (video hoặc document)

\+ translator: Tên của dịch thuật viên đã upload

\+ uploadedDate: Thời gian bản dịch được upload 

**\*Class Subtitle (Kế thừa từ Translation):** 

**- Các thuộc tính bổ sung:**

\+ videoID: Mã ID của video đó

\+ courseID: Nguồn của video đó

\+ viSubtitleURL: Đường dẫn file phụ đề tiếng Việt

\+ enSubtitleURL: Đường dẫn file phụ đề tiếng ANH 

**\*Class Document (Kế thừa từ Translation):**

**- Thuộc tính bổ sung:** documentURL - Đường dẫn đén file Document đã được dịch 

**c. Lớp DAO (Data Access Object – Truy cập dữ liệu)**

**- Mô tả: Tương tác với Database và lấy ra dữ liệu**

**- Mỗi Database Table sẽ cần tạo 1 class DAO tương ứng và các class sẽ có có các hàm để tương tác với Database** 

**\*Class UserDAO:** 

\+ getUserByID(): Lấy thông tin chi tiết người dùng 

\+ validateUser(): Xác nhận đăng nhập 

\+ addNewUser(): Thêm một người dùng mới 

**\*Class TranslationDAO:**

\+ insertTranslation(): Lưu bản dịch mới

\+ deleteTranslation(): Xóa bản dịch

\+ updateTranslation(): Chỉnh sửa thông tin (Re-up file dịch hoặc Chỉnh sửa Metadata)

\+ searchTranslation(): Tìm kiếm các bản dịch theo bộ lọc

\+ getListByTranslator(): Lấy danh sách bản dịch từ Dashboard của Translator

\+ updateStatus: Thay đổi trạng thái bản dịch (Publised hoặc Pending)

**\*Class AdminDAO:**

\+ getAllUser(): Lấy toàn bộ danh sách người dùng

\+ updateUserRole(): Cấp quyền Translator hoặc hạ quyền User (từ Translator xuống User)

\+ deleteAccount(): Xóa tài khoản vĩnh viễn khỏi hệ thống 








**d. Sơ đồ Class Diagram![C:\Users\Name\Downloads\ASM1 Class Diagram (3).png](Aspose.Words.3e3cffc2-4c05-43fb-9d3c-394625237b57.003.png)**
## <a name="_toc229014887"></a><a name="_toc229014983"></a>**3.5 Sequence Diagram**
Hoạt động kiểm tra và hiển thị bản dịch của Extension:

![C:\Users\Name\Downloads\ASM 1 Sequence Diagram.png](Aspose.Words.3e3cffc2-4c05-43fb-9d3c-394625237b57.004.png)








## <a name="_toc229014888"></a><a name="_toc229014984"></a>**3.6 Activity Diagram**
Hoạt động bật/tắt Extension:

![D:\FUNIX ASM\SWE102x - Nhập môn kỹ thuật phần mềm\ASM2\fx-18096-assignment-02-swe\documentation\diagram\Activity Diagram.png](Aspose.Words.3e3cffc2-4c05-43fb-9d3c-394625237b57.005.png)
