Khi upload source wordpress và import database xong sẽ tới bước kiểm tra website có hoạt động không, khi vào `https://wp.giahung.vietnix.tech/` có thông báo của wordpress
<img width="868" height="239" alt="image" src="https://github.com/user-attachments/assets/c4d8368d-d007-4936-8365-6413860120c7" />

Bật debug để xem cụ thể lỗi
<img width="771" height="408" alt="image" src="https://github.com/user-attachments/assets/beb47e10-6cb0-4718-b8ef-492bf987659d" />

Có dòng `Fatal error: Call to undefined function putenv()`

1. Phân tích lỗi: Tại sao lại bị Fatal Error?
- PHP thông báo rằng nó không tìm thấy hàm putenv(). Đây là hàm dùng để thiết lập các biến môi trường (environment variables).
- Nguyên nhân: Trên aaPanel, vì lý do bảo mật, các hàm có khả năng can thiệp sâu vào hệ thống thường bị đưa vào danh sách "Disabled Functions" (Hàm bị vô hiệu hóa) trong file php.ini. WooCommerce và Google Site Kit cần hàm này để hoạt động, nhưng aaPanel đã chặn nó lại.
2. Cách xử lý trên aaPanel
Không cần sửa code WordPress, chỉ cần cấu hình lại PHP trên aaPanel để mở khóa cho hàm này.
Bước 1: Truy cập cấu hình PHP
- Vào aaPanel -> Website.
- Như trong hình dưới đây - chọn `8.1` (là bản php đã chọn lúc cài đặt) -> Nhấn vào nút Setting.
  <img width="886" height="106" alt="image" src="https://github.com/user-attachments/assets/718e653f-ea3c-4ba5-be6c-e268b532492e" />

Bước 2: Loại bỏ hàm bị chặn
- Trong cửa sổ hiện ra, chọn mục Disabled functions ở cột bên trái.
- Tìm hàm có tên putenv trong danh sách.
- Nhấn nút Del (Xóa) bên cạnh hàm đó để cho phép PHP sử dụng lại nó.
  <img width="809" height="691" alt="Screenshot from 2026-04-20 16-43-28" src="https://github.com/user-attachments/assets/16edd7d2-43f7-4dc4-9475-f986c2f0f92b" />

==> Sau khi chỉnh sửa wordpress hoạt động bình thường
<img width="1785" height="929" alt="image" src="https://github.com/user-attachments/assets/6d1248b6-b8b1-45a1-a03e-6aafc2aa15ec" />
