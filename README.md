# n8n_project
📸 EditPicture: Telegram to Google Drive Image Automation
Dự án này là một n8n Workflow tự động hóa quy trình xử lý hậu kỳ hình ảnh. Hệ thống cho phép người dùng gửi ảnh qua Telegram, tự động xử lý tách nền bằng AI và lưu trữ tệp tin lên Google Drive với tên file được đặt động theo yêu cầu của người dùng.

🚀 Tính năng chính
Tiếp nhận dữ liệu đa phương tiện: Tự động lắng nghe và tải hình ảnh từ Telegram Bot.

Xử lý ảnh bằng AI: Tích hợp API chuyên dụng để xóa nền ảnh (Background Removal) một cách chính xác.

Quản lý lưu trữ thông minh: Tự động đẩy file lên Google Drive.

Đặt tên file động: Sử dụng nội dung caption của người dùng làm tên file để dễ dàng quản lý và tìm kiếm.

🏗️ Cấu trúc Workflow
Workflow bao gồm 4 giai đoạn chính:

Telegram Trigger: Nhận tin nhắn chứa hình ảnh và mô tả.

Get a File: Truy xuất thông tin file_id và tải dữ liệu nhị phân (Binary) của ảnh từ máy chủ Telegram.

HTTP Request (Xử lý AI): Kết nối với API (như Remove.bg) để thực hiện tác vụ xóa nền.

Google Drive Upload: Lưu trữ kết quả cuối cùng vào thư mục đám mây.

🛠️ Công nghệ sử dụng
n8n: Nền tảng low-code để kết nối các dịch vụ.

Telegram Bot API: Giao diện tương tác người dùng.

Remove.bg API / HTTP Request: Xử lý hậu kỳ hình ảnh.

Google Drive API: Lưu trữ dữ liệu.

JavaScript (Expression): Xử lý logic đặt tên file và trích xuất dữ liệu.

📝 Hướng dẫn cài đặt
Chuẩn bị API Keys:

Tạo Bot trên Telegram qua @BotFather để lấy API Token.

Đăng ký tài khoản tại remove.bg để lấy API Key.

Thiết lập Credentials cho Google Drive trên n8n.

Import Workflow:

Mở n8n, chọn Import from File.

Chọn file EditPicture.json.

Cấu hình Node:

Cập nhật Credentials cho các node: Telegram, HTTP Request và Google Drive.

Đảm bảo node HTTP Request đã được điền đúng API Key trong phần Header (X-Api-Key).

💡 Giải quyết vấn đề (Problem Solving)
Dự án này đã được tối ưu hóa từ các thử nghiệm ban đầu:

Vượt qua rào cản hạn mức: Chuyển đổi từ Google Gemini (bị giới hạn Quota) sang API chuyên dụng qua HTTP Request để đảm bảo hệ thống luôn hoạt động ổn định.

Xử lý Binary Data: Cấu hình chính xác luồng dữ liệu nhị phân để đảm bảo hình ảnh không bị hỏng trong quá trình truyền tải giữa các API.
5. Kết quả đạt được
Hệ thống cho phép người dùng chỉ cần gửi một tấm ảnh kèm tên gọi mong muốn, ngay lập tức họ sẽ có một tấm ảnh đã được tách nền chuyên nghiệp lưu trữ sẵn trên đám mây, giúp tối ưu hóa quy trình làm việc thủ công.
