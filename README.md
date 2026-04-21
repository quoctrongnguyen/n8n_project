# 📸 EditPicture: Telegram to Google Drive Automation

Dự án này là một hệ thống tự động hóa được xây dựng trên **n8n**, cho phép tiếp nhận hình ảnh từ Telegram, thực hiện tách nền bằng AI (qua API) và tự động lưu trữ vào Google Drive với tên file được đặt theo yêu cầu.

## 🌟 Tính năng chính
- **Nhận diện tự động:** Lắng nghe và tải ảnh kèm caption từ Telegram Bot.
- **Xử lý hậu kỳ:** Tự động xóa nền ảnh (Background Removal) sử dụng API chuyên dụng.
- **Lưu trữ đám mây:** Tự động đẩy tệp tin đã xử lý lên Google Drive.
- **Định danh thông minh:** Tên file được đặt động dựa trên nội dung tin nhắn (`caption`) của người dùng.

## 🏗️ Cấu trúc Workflow
Hệ thống bao gồm các node chính:
1. **Telegram Trigger:** Tiếp nhận tin nhắn (Ảnh + Caption).
2. **Get a File (Telegram Node):** Truy xuất và tải dữ liệu Binary của ảnh.
3. **HTTP Request:** Gửi dữ liệu ảnh tới API xử lý (Remove.bg) và nhận lại ảnh đã xóa nền.
4. **Google Drive Upload:** Lưu trữ ảnh vào thư mục chỉ định với tên file tương ứng.

## 🛠️ Yêu cầu hệ thống
- **n8n** (Desktop hoặc Docker version).
- **Telegram Bot Token** (Lấy từ @BotFather).
- **Remove.bg API Key** (Đăng ký tại remove.bg).
- **Google Drive OAuth2** (Cấu hình qua Google Cloud Console).

## 🚀 Hướng dẫn cài đặt
1. Tải file `EditPicture.json` từ repository này.
2. Trong giao diện n8n, chọn **Import from File** và tải file vừa tải lên.
3. Cấu hình **Credentials** cho:
   - Telegram API
   - Header Auth (cho mã API của Remove.bg)
   - Google Drive OAuth2
4. Nhấn **Execute Workflow** và gửi ảnh từ Telegram để kiểm tra.

## 📝 Giải quyết vấn đề (Troubleshooting)
Trong quá trình thực hiện bài kiểm tra giữa kỳ, dự án đã được tối ưu hóa như sau:
- **Lỗi Quota AI:** Chuyển đổi từ Gemini/OpenAI (thường xuyên lỗi hạn mức hoặc yêu cầu nạp tiền) sang sử dụng API xử lý chuyên dụng qua node **HTTP Request** để đảm bảo độ ổn định 100%.
- **Xử lý Binary:** Cấu hình chính xác định dạng `multipart/form-data` để truyền tải ảnh nhị phân mà không bị hỏng tệp.

## 👨‍💻 Tác giả
- **Nguyễn Quốc Trọng**
- Dự án: Bài kiểm tra giữa kỳ - Hệ thống hóa quy trình tự động.
