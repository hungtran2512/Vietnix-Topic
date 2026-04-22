# CYBERPANEL & REVERSE PROXY NÂNG CAO
# CyberPanel
## I. GIỚI THIỆU TỔNG QUAN (CONCEPT)
* **CyberPanel là gì:** Một Control Panel quản trị Hosting dựa trên nền tảng OpenLiteSpeed, hỗ trợ các công nghệ hiện đại như LSCache, quản lý Docker, và tích hợp sẵn bảo mật.
* **OpenLiteSpeed (OLS):** Web Server hiệu suất cao, tương thích tốt với WordPress và hỗ trợ các tính năng Proxy mạnh mẽ thông qua giao diện đồ họa.
* **Mục tiêu bài Lab:** Triển khai hạ tầng CyberPanel, di trú dữ liệu từ aaPanel/VPS cũ và cấu hình ProxyPass để chạy ứng dụng Backend song song với Website.

---

## II. TRIỂN KHAI HỆ THỐNG CYBERPANEL

### 1. Cài đặt CyberPanel
> **Cảnh báo:** Luôn thực hiện Backup toàn bộ dữ liệu (Source + DB) từ hệ thống cũ trước khi cài đặt vì CyberPanel yêu cầu một OS sạch.

* **Lệnh cài đặt:**
```bash
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
```

* **Giải thích:**
    * `curl/wget`: Tải script cài đặt từ server CyberPanel.
    * `sh / bash`: Thực thi script để tự động cấu hình OpenLiteSpeed, MariaDB, DNS, và Mail Server.

 <img width="1069" height="871" alt="image" src="https://github.com/user-attachments/assets/60ae3d53-64be-4cc6-99f3-b851bcecac5c" />
 <img width="1228" height="715" alt="image" src="https://github.com/user-attachments/assets/9b2623ff-edc3-4c71-954a-a9f066b1d67c" />

 
### 2. Di trú dữ liệu (Migration)
* **Mô tả:** Đưa source code WordPress và Laravel vào thư mục mới.
* **Đường dẫn tuyệt đối:** `/home/[domain_cua_ban]/public_html/`
* **Lệnh phân quyền:**
```bash
chown -R [user]:[group] /home/[domain_cua_ban]/public_html/
chmod -R 755 /home/[domain_cua_ban]/public_html/
```

### 3. Cấu hình SSL từ Certbot cũ
* **Nguyên nhân:** Tận dụng chứng chỉ ZeroSSL/Certbot đã tạo ở Topic 4 để tránh phải reissue.
* **Đường dẫn file cũ:** `/etc/letsencrypt/live/[domain]/`
* **Thao tác:** Copy nội dung `privkey.pem` (Key) và `fullchain.pem` (Certificate) dán vào mục SSL trong CyberPanel.

---

## III. XÂY DỰNG ỨNG DỤNG BACKEND (PORT 5000)

### 1. Khởi tạo ứng dụng Node.js/Python
* **Mục đích:** Tạo một service chạy ngầm trên port 5000 để mô phỏng hệ thống API.
* **Mã nguồn mẫu (Node.js):**
```javascript
// app.js chạy tại port 5000
```

### 2. Quản lý tiến trình bằng PM2
* **Lệnh:**
```bash
pm2 start app.js --name "api-backend"
```
* **Giải thích:**
    * `start`: Chạy ứng dụng.
    * `--name`: Đặt tên dễ quản lý trong danh sách tiến trình.

---

## IV. CẤU HÌNH PROXYPASS TRONG OPENLITESPEED



### 1. Thiết lập External App
* **Khái niệm:** Khai báo cho OpenLiteSpeed biết có một ứng dụng bên ngoài đang lắng nghe tại port 5000.
* **Thông số:** `Address: 127.0.0.1:5000`.

### 2. Cấu hình Context (URI Mapping)
* **Giải pháp:** Ánh xạ đường dẫn `/api` về External App vừa tạo.
* **Cơ chế:** Khi người dùng gọi `domain.com/api`, OLS sẽ đóng vai trò Proxy để forward request tới port 5000.

---

## V. KIỂM TRA VÀ TỐI ƯU (TROUBLESHOOTING)

### 1. Kiểm tra trạng thái Port
```bash
netstat -tuln | grep 5000
```
* **Giải thích:** `-t` (TCP), `-u` (UDP), `-l` (Listen), `-n` (Numeric). Phải thấy port 5000 đang Listen.

### 2. Lỗi thường gặp
* **Lỗi 502 Bad Gateway:** Ứng dụng Backend (port 5000) chưa chạy hoặc Firewall chặn kết nối nội bộ.
* **Lỗi SSL Handshake:** Do dán thiếu nội dung trong file `fullchain.pem`.

---

## VI. KẾT LUẬN
* Nắm vững cách vận hành CyberPanel và OpenLiteSpeed.
* Hiểu rõ cơ chế ProxyPass để triển khai các kiến trúc ứng dụng phức tạp (Microservices).
