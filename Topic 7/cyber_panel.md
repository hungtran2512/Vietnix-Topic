# CYBERPANEL & REVERSE PROXY NÂNG CAO
## I. CyberPanel
* **CyberPanel là gì:** Một Control Panel quản trị Hosting dựa trên nền tảng OpenLiteSpeed, hỗ trợ các công nghệ hiện đại như LSCache, quản lý Docker, và tích hợp sẵn bảo mật.
* **OpenLiteSpeed (OLS):** Web Server hiệu suất cao, tương thích tốt với WordPress và hỗ trợ các tính năng Proxy mạnh mẽ thông qua giao diện đồ họa.

---

## II. TRIỂN KHAI HỆ THỐNG CYBERPANEL

### 1. Cài đặt CyberPanel
* **Lệnh cài đặt:**
```bash
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
```

* **Giải thích:**
    * `curl/wget`: Tải script cài đặt từ server CyberPanel
    * `sh / bash`: Thực thi script để tự động cấu hình OpenLiteSpeed, MariaDB, DNS, và Mail Server
* Chọn các option như trên hình
 <img width="1069" height="871" alt="image" src="https://github.com/user-attachments/assets/60ae3d53-64be-4cc6-99f3-b851bcecac5c" />
 <img width="1210" height="716" alt="image" src="https://github.com/user-attachments/assets/b3f17c33-c9fc-46f0-90e8-49d2ce7349d3" />

* Kết quả
   ```bash
   [2026-04-22 10:01:56] [INFO] Cleaning up temporary installation files
   [2026-04-22 10:01:56] [FUNCTION] Starting: Post_Install_Display_Final_Info
   [2026-04-22 10:01:56] [INFO] Preparing final installation information
   ###################################################################
                CyberPanel Successfully Installed                  
                                                                   
                Current Disk usage : 8/48GB (19%)                        
                                                                   
                Current RAM  usage : 1040/7953MB (13.08%)                         
                                                                   
                Installation time  : 0 hrs 12 min 0 sec                 
                                                                   
                Visit: https://221.132.21.143:8090                     
                Panel username: admin                              
                Panel password: uTKsDAaEcrUz2AKU                        
                                                                   
             Run cyberpanel help to get FAQ info
             Run cyberpanel upgrade to upgrade it to latest version.
             Run cyberpanel utility to access some handy tools .
                                                                   
              Website : https://www.cyberpanel.net                 
              Forums  : https://forums.cyberpanel.net              
              Wikipage: https://cyberpanel.net/KnowledgeBase/                
              Docs    : https://cyberpanel.net/docs/               
                                                                   
            Enjoy your accelerated Internet by                  
                CyberPanel & OpenLiteSpeed 				                     
   ###################################################################
   If your provider has a network-level firewall
   Please make sure you have opened following port for both in/out:
   TCP: 8090 for CyberPanel
   TCP: 80, TCP: 443 and UDP: 443 for webserver
   TCP: 21 and TCP: 40110-40210 for FTP
   TCP: 25, TCP: 587, TCP: 465, TCP: 110, TCP: 143 and TCP: 993 for mail service
   TCP: 53 and UDP: 53 for DNS service
   Would you like to restart your server now? [y/N]: y
   ```

* Truy cập https://221.132.21.143:8090 với thông tin đã được cho
<img width="1641" height="1006" alt="image" src="https://github.com/user-attachments/assets/afb199b5-63df-40fb-98ad-12990bc105d0" />
<img width="1792" height="1007" alt="image" src="https://github.com/user-attachments/assets/8ec8ee07-dbb6-43e3-be56-84e583e4cbb5" />

### 2. Cấu hình SSL từ Certbot cũ
* **Nguyên nhân:** Tận dụng chứng chỉ ZeroSSL/Certbot đã tạo ở Topic 4 để tránh phải reissue.
* **Đường dẫn file cũ:** `/etc/letsencrypt/live/[domain]/`
* **Thao tác:** Copy nội dung `privkey.pem` (Key) và `fullchain.pem` (Certificate) dán vào mục SSL trong CyberPanel.

---

## III. XÂY DỰNG ỨNG DỤNG BACKEND (PORT 5000)

### 1. Khởi tạo ứng dụng Python
* **Mục đích:** Tạo một service chạy ngầm trên port 5000 để mô phỏng hệ thống API.
* Tạo thư mục riêng để quản lý
<img width="525" height="75" alt="image" src="https://github.com/user-attachments/assets/934b3971-c062-4c8e-9642-9aa1aa5b6562" />

* **Mã nguồn mẫu (Python):**
```python
from http.server import HTTPServer, BaseHTTPRequestHandler

class SimpleHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-Type', 'text/plain; charset=utf-8')
        self.end_headers()
        self.wfile.write("Hello! Python Port 5000.".encode('utf-8'))

httpd = HTTPServer(('127.0.0.1', 5000), SimpleHandler)
print("App is running: port 5000...")
httpd.serve_forever()
```

* Để app không bị tắt khi đóng terminal
```bash
nohup python3 app.py > app.log 2>&1 &
```

* Dùng curl kiểm thử app -> app hoạt động tốt
<img width="683" height="56" alt="image" src="https://github.com/user-attachments/assets/a7fcbb0f-dc01-493b-9d09-b0eb9bcb5ec0" />

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
