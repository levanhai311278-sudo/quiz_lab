# Quiz Lab – Netlify v12 (04/11/2026)

## Thành phần
- `index.html`: giao diện Quiz Lab.
- `netlify.toml`: cấu hình thư mục xuất bản `.` và Netlify Functions.
- `netlify/functions/quizlab-api.js`: proxy same-origin đến Google Apps Script.
- Các tệp logo, favicon, biểu tượng và `site.webmanifest`.

## Cập nhật từ v11
1. Bảng xem trước Excel có nút **Sửa** cho từng dòng trước khi nạp. Có thể sửa nội dung câu hỏi, đáp án/lựa chọn, đáp án đúng và thời gian; Đúng/Sai cho phép sửa từng mệnh đề và từng giá trị Đúng/Sai. Bản ghi được kiểm tra lại trước khi nạp.
2. Xem trước câu hỏi và đáp án trong danh sách bản nháp luôn hiển thị, không cần mở từng mục.
3. Thêm **Hủy bản nháp** ở màn hình Bản nháp đang soạn. Nút cần bấm xác nhận lần hai; hành động này xóa nội dung bản nháp hiện tại khỏi bộ nhớ trình duyệt. Khi đang chỉnh sửa đề đã xuất bản, vẫn dùng nút **Hủy chỉnh sửa** riêng để giữ nguyên đề gốc.

## Cách cập nhật GitHub / Netlify
1. Giải nén ZIP.
2. Thay `index.html` hiện tại ở thư mục publish bằng `index.html` trong gói.
3. Giữ `netlify.toml` ở thư mục gốc của publish directory.
4. Giữ `netlify/functions/quizlab-api.js` đúng đường dẫn.
5. Giữ hoặc cập nhật các tệp logo/favicon trong cùng thư mục với `index.html`.
6. Commit lên GitHub và chờ Netlify deploy.
7. Không đổi biến môi trường `QUIZLAB_GAS_URL`; giá trị vẫn là URL Apps Script `/exec`.

## Lưu ý
- Không cần triển khai lại Apps Script hoặc thay đổi Google Sheets cho các tính năng giao diện trong v12.
- Nút Hủy bản nháp xóa các câu đang soạn trong `localStorage` của trình duyệt hiện tại. Không dùng nút này để hủy chỉnh sửa đề đã xuất bản; hãy dùng **Hủy chỉnh sửa**.
- Sau deploy nên thử mở mục Nhập câu hỏi, tải một file Excel mẫu, sửa thử một câu MC và một câu Đúng/Sai, rồi nạp vào bản nháp. Kiểm tra một đề nháp nhiều câu để xem preview luôn hiện.
