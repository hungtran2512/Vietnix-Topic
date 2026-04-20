# Laravel

GIAI ĐOẠN 1: ĐÓNG GÓI FILE TRONG VPS
  1. Nén Source Code:
  ```
  cd /var/www/giahung/
  # Nén WordPress
  sudo tar -czvf wordpress.tar.gz wordpress/
  # Nén Laravel
  sudo tar -czvf laravel.tar.gz laravel/
  ```
  2. Xuất Database:
  ```
  # Xuất DB WordPress
  mysqldump -u root -p linhlt_wp_lodoz > wordpress_db.sql
  # Xuất DB Laravel
  mysqldump -u root -p lihnlt_db > laravel_db.sql
  ```

GIAI ĐOẠN 2: ĐƯA FILE VỀ MÁY CÁ NHÂN
  Dùng lệnh scp
  Mở một tab Terminal mới (không phải trong SSH):
  ```
  # đưa 2 file source của wordpress và laravel về máy cá nhân
  scp root@221.132.21.143:/var/www/giahung/*.tar.gz /home/dahunq
  # đưa 2 file database của wordpress và laravel về máy cá nhân
  scp root@221.132.21.143:/var/www/giahung/*.sql /home/dahunq
  ```

GIAI ĐOẠN 3: ĐẨY LÊN CPANEL
  - Vào giao diện Web của cPanel sau khi đã có file trên máy: https://host68.vietnix.vn:2083/, đăng nhập bằng tài khoản được cấp. Sau đó tìm `Domains` chọn `Create A New Domain`
  <img width="896" height="896" alt="Screenshot from 2026-04-20 08-41-17" src="https://github.com/user-attachments/assets/f2368689-2588-42b2-827e-b7e553695bcf" />

  1. Upload mã nguồn Laravel:
  + Tìm mục `Files` và click vào `File Manager` -> Tìm đến thư mục của domain tương ứng (ví dụ `public_html/...`)
  <img width="239" height="328" alt="Screenshot from 2026-04-20 08-57-17" src="https://github.com/user-attachments/assets/c582f715-5c69-456e-988f-cc58dde042fa" />

  + Nhập các thông tin cho domain và bấm submit

  + Nhấn Upload -> Chọn file .tar.gz. Sau khi xong, chuột phải vào file và chọn `extract` để giải nén ngay trên Hosting.
<img width="349" height="306" alt="Screenshot from 2026-04-20 09-00-02" src="https://github.com/user-attachments/assets/68ed90b3-5685-4d14-8c4e-ca92fd72d678" />

  + Sau khi giải nén, vào folder chứa source laravel và click `Select All` -> click chuột phải chọn `Move`, đổi dường dẫn đích thành `/public_html/laravel`
  + Kết quả
<img width="285" height="351" alt="Screenshot from 2026-04-20 09-02-32" src="https://github.com/user-attachments/assets/86bc349d-3d4e-4514-81ae-21de5ff23095" />

  2. Import Database:
  + Ở menu cPanel tìm mục Databases -> click chọn Database Wizard để tạo DB và user mới.
  <img width="1004" height="214" alt="image" src="https://github.com/user-attachments/assets/b13d1293-6509-48db-b859-e097c20cbf72" />
  <img width="707" height="351" alt="Screenshot from 2026-04-20 09-05-47" src="https://github.com/user-attachments/assets/e72def0f-ec04-40ad-9e1a-d0ee6f56d07d" />
  <img width="707" height="548" alt="Screenshot from 2026-04-20 09-08-54" src="https://github.com/user-attachments/assets/836b9605-9b15-4703-8a6d-fc1f739d2448" />
  <img width="1337" height="894" alt="Screenshot from 2026-04-20 09-10-35" src="https://github.com/user-attachments/assets/3d5239ab-82b1-4dae-a9ac-ebd698c45c14" />
  <img width="547" height="200" alt="Screenshot from 2026-04-20 09-11-14" src="https://github.com/user-attachments/assets/7edb08c0-6197-42c8-8b40-8ff80abc09e8" />

  + Sau khi tạo database và user mới thành công -> vào phpMyAdmin -> Chọn database mới tạo -> Tab Import -> Chọn file .sql.
  <img width="1671" height="446" alt="Screenshot from 2026-04-20 09-12-06" src="https://github.com/user-attachments/assets/32813f68-3adc-4ae0-b597-df96eb98eb9f" />

  + Để mặc định khi import
<img width="486" height="39" alt="Screenshot from 2026-04-20 09-13-21" src="https://github.com/user-attachments/assets/3b0ace2a-c7fe-423e-9312-988588c91c9c" />

  + Kết quả
<img width="1353" height="576" alt="Screenshot from 2026-04-20 09-14-06" src="https://github.com/user-attachments/assets/97d7502b-e519-42ca-807d-d72610435b09" />

  + Sau khi import database laravel, quay lại File Manager -> vào thư mục /public_html/public tìm và mở file `.env` để cập nhật `DB_NAME, DB_USER, DB_PASSWORD` dùng thông tin đã tạo ở Database Wizard 
  <img width="223" height="50" alt="Screenshot from 2026-04-20 09-37-53" src="https://github.com/user-attachments/assets/50f6da62-e7f5-47b2-8d11-62ccd144212f" />

  3. Kiểm tra file `.htaccess`
  + Trong menu File Manager, click `Settings` ở góc trên trái màn hình -> chọn `Show Hidden Files`. Nếu không có `.htacces` thì tạo lại file với cấu hình đã dùng khi làm ở Topic 4
  ```
  <IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews -Indexes
    </IfModule>

    RewriteEngine On

    # Handle Authorization Header
    RewriteCond %{HTTP:Authorization} .
    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    # Redirect Trailing Slashes If Not A Folder...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_URI} (.+)/$
    RewriteRule ^ %1 [L,R=301]

    # Send Requests To Front Controller...
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php [L]
    
    # Force HTTPS
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
  </IfModule>
  ```

  4. Dùng cert SSL đã tạo trước đó từ VPS
  + Lấy mã nguồn SSL từ VPS, dùng `cat` để lấy nội dung
  ```
  # Đọc Certificate
  sudo cat /etc/letsencrypt/live/laravel.giahung.vietnix.tech/cert.pem
  # Đọc Private Key (đừng để lộ key này)
  sudo cat /etc/letsencrypt/live/laravel.giahung.vietnix.tech/privkey.pem
  # Đọc CA Bundle
  sudo cat /etc/letsencrypt/live/laravel.giahung.vietnix.tech/chain.pem
  ```
  + Trong menu cPanel tìm mục `Security` -> click vào `SSL/TLS Certificates`
  <img width="987" height="272" alt="image" src="https://github.com/user-attachments/assets/f9b1f3d3-b724-4a56-806c-3c99095c270a" />

  + Chọn Installation -> tìm ô nhập 3 mã của cert
  <img width="987" height="272" alt="image" src="https://github.com/user-attachments/assets/469be0e0-7b00-41c5-82b0-d6116166dd81" />
  <img width="679" height="868" alt="Screenshot from 2026-04-20 09-59-03" src="https://github.com/user-attachments/assets/2a1e03a2-7eef-4fca-bed3-8bb3e50bb0ef" />

  + Dán nội dung 3 file đã cat vào 3 ô tương ứng, sau đó click Install Certificate
  <img width="679" height="868" alt="Screenshot from 2026-04-20 10-01-22" src="https://github.com/user-attachments/assets/fa176c83-c8c8-4e5b-81c7-65125f13eb40" />

  + Kết quả
  <img width="421" height="382" alt="Screenshot from 2026-04-20 10-02-00" src="https://github.com/user-attachments/assets/98f6060f-4fc2-450e-8de9-400061fd919c" />

  5. Trỏ domain về IP Hosting
  + Trong trang chủ cPanel tìm `General Information`, lưu thông tin `Shared IP Address`
  <img width="326" height="368" alt="image" src="https://github.com/user-attachments/assets/bc467ce8-6b0e-4512-8dd0-c9c933d386ed" />

  + Trên Ubuntu vào file hosts: `sudo /etc/hosts`
  ```
  # Thêm IP hosting vào
  103.200.23.68    wp.giahung.vietnix.tech
  103.200.23.68    laravel.giahung.vietnix.tech
  ```
  + Kiểm tra bằng cách dùng `ping` xem đã đúng IP host chưa
  <img width="922" height="240" alt="Screenshot from 2026-04-20 10-33-18" src="https://github.com/user-attachments/assets/01788e29-0f94-4d8c-99f2-42a21a2ca101" />

  + Kiểm tra nhanh với curl -IL
  <img width="911" height="568" alt="Screenshot from 2026-04-20 10-33-44" src="https://github.com/user-attachments/assets/44ed1d49-b8a3-4770-82d2-8a1e12414344" />

Truy cập vào web laravel sau khi cấu hình và upload source lên cPanel https://laravel.giahung.vietnix.tech/ http://laravel.giahung.vietnix.tech/
