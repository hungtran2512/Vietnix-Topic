# cPanel
cPanel là hệ thống quản trị web hosting trên nền tảng Linux phổ biến và mạnh mẽ nhất hiện nay. cPanel cung cấp giao diện đồ họa đơn giản, linh hoạt. Kèm theo rất nhiều tính năng giúp các bạn quản trị hosting và website của mình một cách dễ dàng.

Tính năng bảo mật, tự động hóa của cPanel cũng vượt trội so với các hệ thống web hosting khác. Vậy có thể hiểu, cPanel hosting là Linux web hosting đã có cài đặt sẵn cPanel. cPanel có ưu điểm và nhược điểm, nhưng với hầu hết các trường hợp, nó đều hoạt động hiệu quả. Vì vậy cPanel là lựa chọn tốt cho những ai đang tìm kiếm giải pháp control panel cho hosting.

# Sử dụng cPanel
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
  - Vào giao diện Web của cPanel sau khi đã có file trên máy: https://host68.vietnix.vn:2083/, đăng nhập bằng tài khoản được cấp
  1. Upload mã nguồn WordPress:
  + Tìm mục `Files` và click vào `File Manager` -> Tìm đến thư mục của domain tương ứng (ví dụ `public_html/...`)
    <img width="832" height="329" alt="image" src="https://github.com/user-attachments/assets/6348bec4-d756-4636-8fd9-2fa54b75117d" />
    <img width="327" height="452" alt="image" src="https://github.com/user-attachments/assets/e7c0349d-6e7c-4198-9274-bf55047c8295" /> <img width="213" height="120" alt="image" src="https://github.com/user-attachments/assets/30959058-d5f5-4656-b39f-7d8cf2ac0ce5" />

  + Nhấn Upload -> Chọn file .tar.gz. Sau khi xong, chuột phải vào file và chọn `extract` để giải nén ngay trên Hosting.
<img width="375" height="323" alt="image" src="https://github.com/user-attachments/assets/931cf93f-ce72-4ab5-81cc-ad7a7532e47a" />

  + Sau khi giải nén, vào folder chứa source wordpress và click `Select All` -> click chuột phải chọn `Move`, đổi dường dẫn đích thành `/public_html`
  + Kết quả
<img width="162" height="112" alt="image" src="https://github.com/user-attachments/assets/dbe4bb5b-2354-4f9c-94c0-4a3403eb2013" />

  2. Import Database:
  + Ở menu cPanel tìm mục Databases -> click chọn Database Wizard để tạo DB và user mới.
  <img width="1004" height="214" alt="image" src="https://github.com/user-attachments/assets/b13d1293-6509-48db-b859-e097c20cbf72" />
  <img width="721" height="363" alt="image" src="https://github.com/user-attachments/assets/c7f7a48f-2251-4dc6-86bf-babfeed8e395" />
  <img width="877" height="552" alt="image" src="https://github.com/user-attachments/assets/a5519aa1-9ec1-4a16-aa8a-e4817202a9d4" />
  <img width="1366" height="903" alt="image" src="https://github.com/user-attachments/assets/60ffdaa2-b531-44d7-b2da-1c59bc61fd52" />
  <img width="542" height="201" alt="image" src="https://github.com/user-attachments/assets/c80fa446-cd78-48e8-8a69-0f607d1e1795" />

  + Sau khi tạo database và user mới thành công -> vào phpMyAdmin -> Chọn database mới tạo -> Tab Import -> Chọn file .sql.
  <img width="1321" height="324" alt="image" src="https://github.com/user-attachments/assets/bb54759a-4096-4ce9-a902-0bc293c3613f" />

  + Để mặc định khi import
  <img width="1310" height="898" alt="image" src="https://github.com/user-attachments/assets/d74ceb47-1493-4868-b502-a54c577ed7ed" />
  <img width="492" height="39" alt="image" src="https://github.com/user-attachments/assets/f798c113-2505-4450-ae99-ea59636bf774" />
  + Kết quả
  <img width="1585" height="512" alt="image" src="https://github.com/user-attachments/assets/9ce70b62-7775-47dd-9eca-f4486e6fa4b2" />

  + Sau khi import database wordpress, quay lại File Manager -> vào thư mục /public_html tìm và mở file `wp-config.php` để cập nhật `DB_NAME, DB_USER, DB_PASSWORD` dùng thông tin đã tạo ở Database Wizard 
  <img width="320" height="121" alt="image" src="https://github.com/user-attachments/assets/6d5c1e16-1187-4005-ac15-073ae78929f8" />

  3. Kiểm tra file `.htaccess`
  + Trong menu File Manager, click `Settings` ở góc trên trái màn hình -> chọn `Show Hidden Files`. Nếu không có `.htacces` thì tạo lại file với cấu hình đã dùng khi làm ở Topic 4
  ```
  <IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.php$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.php [L]
  </IfModule>
  ```

  4. Dùng cert SSL đã tạo trước đó từ VPS
  + Lấy mã nguồn SSL từ VPS, dùng `cat` để lấy nội dung
  ```
  # Đọc Certificate
  sudo cat /etc/letsencrypt/live/wp.giahung.vietnix.tech/cert.pem
  # Đọc Private Key (đừng để lộ key này)
  sudo cat /etc/letsencrypt/live/wp.giahung.vietnix.tech/privkey.pem
  # Đọc CA Bundle
  sudo cat /etc/letsencrypt/live/wp.giahung.vietnix.tech/chain.pem
  ```
  + Trong menu cPanel tìm mục `Security` -> click vào `SSL/TLS Certificates`
  <img width="987" height="272" alt="image" src="https://github.com/user-attachments/assets/f9b1f3d3-b724-4a56-806c-3c99095c270a" />

  + Chọn Installation -> tìm ô nhập 3 mã của cert
  <img width="987" height="272" alt="image" src="https://github.com/user-attachments/assets/469be0e0-7b00-41c5-82b0-d6116166dd81" />
  <img width="725" height="895" alt="image" src="https://github.com/user-attachments/assets/20e7d460-663d-4db0-a14e-4a42db904270" />

  + Dán nội dung 3 file đã cat vào 3 ô tương ứng, sau đó click Install Certificate
  <img width="851" height="895" alt="image" src="https://github.com/user-attachments/assets/bc007273-5d10-4b8c-8d6c-d5c76803b7c8" />

  + Kết quả
  <img width="424" height="368" alt="image" src="https://github.com/user-attachments/assets/fd30e341-5399-4c32-a8be-366e9b34b29d" />

  + Trong menu cPanel tìm phần `Domains` -> click vào `Domains`
  <img width="998" height="274" alt="image" src="https://github.com/user-attachments/assets/21681dd1-1d1d-44c9-a0a4-302c2cbc673c" />

  + Bật Force HTTPS Redirect (On) để điều hướng http sang https
  <img width="1380" height="374" alt="image" src="https://github.com/user-attachments/assets/80240089-3de7-4459-bc71-048958d9c039" />

  5. Trỏ domain về IP Hosting
  + Trong trang chủ cPanel tìm `General Information`, lưu thông tin `Shared IP Address`
  <img width="326" height="368" alt="image" src="https://github.com/user-attachments/assets/bc467ce8-6b0e-4512-8dd0-c9c933d386ed" />

  + Trên Ubuntu vào file hosts: `sudo /etc/hosts`
  ```
  # Thêm IP hosting vào
  103.200.23.68    wp.giahung.vietnix.tech
  103.200.23.68    laravel.giahung.vietnix.tech
  ```
  + Kiểm tra bằng cách dùng `ping`
  <img width="814" height="314" alt="image" src="https://github.com/user-attachments/assets/d6d2b5a2-9d7b-4afe-a434-2dd33ce860a0" />

Truy cập vào web wordpress sau khi cấu hình và upload source lên cPanel https://wp.giahung.vietnix.tech/ http://wp.giahung.vietnix.tech/
