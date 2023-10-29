# FUNiX Passport

Tên dự án: Quản lý mã nguồn phần mềm FUNiX Passport
Mã sinh viên: FX20520

Repository này được sử dụng để quản lý source code cũng như các tài liệu cho Funix Passport. Đồng thời, để thực hiện một số yêu cầu liên quan đến việc nâng cấp các chức năng, bổ sung tài liệu cho Extension Funix Passport.

Có 9 brand:
- Active branches
	+ backend
	+ document
	+ feat/auto_enable_subtitle
	+ bug/clear_console_log
	+ master (default)

- Stale branches
	+ youtube-subtitle
	+ subtitle-by-time
	+ bug/onpage_on_sololearn
	+ bug/applieddigitalskills

Những sự thay đổi tại active branches:
- master (default): 
	+ Revert "Fix Udemy bug": FUNiX Passport đang bị lỗi do có một đoạn code đã bị sửa, khiến cho Extension không thể hiển thị popup khi có phụ đề trên các video thuộc nguồn Udemy. Cần Roll Back lại commit trước đó để sửa lại lỗi này.

- bug/clear_console_log (từ branch master):
	+ Revert "Fix Udemy bug": (giống branch master)
	+ Clear console.log() functions: Ở các đoạn code trong file script/subtitle/udemy-subtitle.js có các dùng console.log để Dev có thể debug ứng dụng. Tuy nhiên khi triên khai sản phẩm thì sẽ cần xóa các đoạn Log này đi, tránh cho các log này làm ảnh hướng đến người dùng. Vì vậy, cần xóa các câu lệnh console.log ở file udemy-subtitle.js.

- feat/auto_enable_subtitle (từ branch master):
	+ Revert "Fix Udemy bug": (giống branch master)
	+ Auto enable subtitle: Thay vì khi có hỗ trợ phụ đề thì Extension sẽ hiển thị ra popup cho người dùng để hỏi xem có muốn bật hay không. Chỉnh sửa lại thành nếu như có hỗ trợ phụ đề thì sẽ tự động hiển thị ra. Cần chỉnh sửa hàm pageLoad() ở file script/subtitle/udemy-subtitle.js về thành như sau:
function pageLoad(code) {
	startObserver();
	if (code === 200) {
		start(1, false);
	}
}

- document (từ branch master):
	+ Revert "Fix Udemy bug": (giống branch master)
	+ Add documentation folder: Cập nhật thêm các tài liệu của dự án này
	+ Add Diagram folder: Lưu lại các file ảnh (png) các sơ đồ đã được vẽ trên diagram vào folder bao gồm Usecase, Class, Activity, Senquence, Client-Sever Architecture
	+ Upload Requirements Specification Document - FUNiX Passport
	+ Add Document.MD Folder: Upload Requirements Specification Document - FUNiX Passport dưới định dạng Markdown

- backend (từ branch master):
	+ Revert "Fix Udemy bug": (giống branch master)
	+ Branch này sẽ chứa các thông tin cũng như source code của Backend và tài liệu cho Backend.
	+ Add backend.md: Tạo với các nội dung như sau: Backend này có vai trò gì, mục đích xây dựng là gì? Các vai trò nào sẽ sử dụng Backend? Mỗi vai trò sẽ được sử dụng những thao tác/chức năng gì?
