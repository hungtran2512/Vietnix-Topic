-----
# LỘ TRÌNH ĐÀO TẠO KỸ THUẬT (SYSADMIN) - VIETNIX TOPICS
-----

## 🟢 PHẦN 1: NỀN TẢNG VÀ LÝ THUYẾT

### Topic 1: Kỹ năng cơ bản & Tổng quan Control Panel

  * **Nội dung:** Luyện gõ 10 ngón (Target: 85 WPM), tìm hiểu sản phẩm dịch vụ và các loại Control Panel (cPanel, WHM).
  * **Khái niệm:** Control Panel là giao diện đồ họa giúp quản lý các dịch vụ lưu trữ (Hosting, DNS, Email) mà không cần dùng dòng lệnh phức tạp.
  * **Ưu điểm:** Tiết kiệm thời gian, giảm sai sót cho người mới.
  * **Nhược điểm:** Tốn tài nguyên hệ thống (RAM/CPU) để duy trì giao diện.

### Topic 2: Hạ tầng mạng & Linux căn bản

  * **Khái niệm:**
      * **DNS:** Hệ thống phân giải tên miền thành địa chỉ IP.
      * **SSL:** Giao thức bảo mật mã hóa dữ liệu giữa trình duyệt và máy chủ.
  * **Câu lệnh quan trọng:**
      * `ls -al`: Liệt kê file (bao gồm file ẩn) để kiểm tra phân quyền.
      * `cd /var/www/`: Di chuyển đến thư mục chứa code website.
      * `df -h`: Kiểm tra dung lượng ổ đĩa (để tránh đầy disk gây treo web).

-----

## 🟡 PHẦN 2: TRIỂN KHAI DỊCH VỤ WEB (LEMP & PROXY)

### Topic 3: Mô hình LEMP Stack

  * **Thành phần:** **L**inux - **E**ngine-X (Nginx) - **M**ySQL - **P**HP.
  * **Thực hành:** Xây dựng website WordPress và Laravel. Cấu hình Remote MySQL.
  * **Lợi ích:** Nginx xử lý các kết nối đồng thời cực tốt, phù hợp cho website có lượng truy cập cao.
  * **Câu lệnh cấu hình:**
      * Sửa file cấu hình Nginx: `nano /etc/nginx/conf.d/default.conf`
      * Kiểm tra lỗi syntax trước khi restart: `nginx -t` (Rất quan trọng để tránh làm sập toàn bộ web).

### Topic 4: Reverse Proxy (Nginx & Apache)

  * **Mô hình:** Nginx đứng trước (làm Proxy) xử lý file tĩnh và bảo mật, Apache đứng sau (Backend) xử lý PHP.
  * **Ví dụ:** Khi khách hàng truy cập, Nginx sẽ tiếp nhận trước, sau đó đẩy yêu cầu về Apache xử lý.
  * **Cấu hình Vhost:**
      * Đường dẫn: `/etc/nginx/sites-available/`
      * Tại sao dùng: Để chạy nhiều website khác nhau trên cùng một địa chỉ IP.

-----

## 🟠 PHẦN 3: QUẢN TRỊ CONTROL PANEL CHUYÊN SÂU

### Topic 5 & 6: cPanel & aaPanel

  * **Nhiệm vụ:** Di chuyển dữ liệu (Migration) giữa các VPS, cài đặt Plugin (Rank Math SEO, Elementor, Divi).
  * **Tìm hiểu:** **Litespeed Cache**.
      * **Lợi ích:** Tăng tốc độ tải trang lên gấp nhiều lần nhờ công nghệ cache ở tầng server.
  * **Lưu ý:** Đối với aaPanel, quản lý Module qua 1-click rất nhanh nhưng cần cẩn trọng với bảo mật cổng 8888.

### Topic 7 & 8: CyberPanel & VestaCP

  * **Kỹ thuật cao:** Chạy ứng dụng Python/Node.js trên cổng 5000 và cấu hình **ProxyPass** trong OpenLiteSpeed.
  * **Mục đích:** Chuyển tiếp yêu cầu từ `domain.com/api` về ứng dụng đang chạy nội bộ tại port 5000.
  * **Ưu điểm CyberPanel:** Miễn phí và tích hợp sẵn OpenLiteSpeed cho hiệu suất cực cao.

-----

## 🔵 PHẦN 4: HỆ ĐIỀU HÀNH WINDOWS SERVER

### Topic 9: Windows Server & IIS

  * **Dịch vụ:** IIS (Internet Information Services), SQL Server 2016.
  * **Bảo mật Firewall:**
      * **Allow/Block IP:** Chỉ cho phép IP của quản trị viên truy cập vào cổng quản lý (RDP - 3389).
      * **Lợi ích:** Ngăn chặn các cuộc tấn công Brute-force từ môi trường internet.
  * **Thực hành:** Cài đặt WordPress trên nền tảng Windows (sử dụng PHP Manager và MySQL for Windows).

-----

## 🛠 DANH MỤC CÂU LỆNH VÀ ĐƯỜNG DẪN HỆ THỐNG

| Đối tượng | Đường dẫn / Câu lệnh | Giải thích tại sao dùng |
| :--- | :--- | :--- |
| **Nginx Config** | `/etc/nginx/nginx.conf` | Chỉnh sửa các thông số global (worker\_processes, keepalive). |
| **Log Lỗi** | `tail -f /var/log/nginx/error.log` | Theo dõi lỗi thời gian thực để fix nhanh khi web không truy cập được. |
| **Permissions** | `chown -R www-data:www-data /var/www/` | Cấp quyền cho web server có thể đọc/ghi dữ liệu vào folder code. |
| **Firewall (Linux)** | `ufw allow 80/tcp` | Mở cổng HTTP để người dùng bên ngoài có thể thấy website. |
| **MySQL Backup** | `mysqldump -u [user] -p [db_name] > backup.sql` | Sao lưu cơ sở dữ liệu trước khi thực hiện các thay đổi lớn. |

-----
