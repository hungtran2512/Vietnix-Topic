# Recap Topic 5: Website Migration (VPS to cPanel)

## 1. Nội dung đã thực hiện
* **Giai đoạn 1: Đóng gói:** Nén mã nguồn bằng lệnh `tar` và xuất cơ sở dữ liệu bằng `mysqldump` từ VPS đã làm ở (Topic 4).
* **Giai đoạn 2: Chuẩn bị môi trường Hosting:** * Khởi tạo Database và User MySQL trên cPanel.
    * Cấu hình **Addon Domain** cho Laravel, tách biệt Document Root với WordPress.
* **Giai đoạn 3: Triển khai:** * Upload và giải nén source qua File Manager.
    * Import Database qua phpMyAdmin.
* **Giai đoạn 4: Cấu hình ứng dụng (Configuration):** Đồng bộ hóa các tệp tin cấu hình (`wp-config.php`, `.env`) để khớp với thông số của Hosting mới.
* **Giai đoạn 5: Bảo mật và Điều hướng:**
    * Cập nhật chứng chỉ SSL Let's Encrypt thủ công.
    * Thiết lập Rewrite Rules và Force HTTPS trong tệp tin `.htaccess`.

---

## 2. Một số chỗ lưu ý 

* **Về Document Root:** Đối với các Framework hiện đại (Laravel), luôn trỏ Document Root vào thư mục `/public` để bảo vệ mã nguồn cốt lõi và các file nhạy cảm (`.env`).
* **Về Cache:** Nên kiểm tra bằng **Tab ẩn danh (cognitive)** hoặc dùng lệnh **`curl -I`**.
* **Về Phân quyền:** Thư mục `storage` và `bootstrap/cache` của Laravel cần quyền ghi (**755/775**) để không bị lỗi 500 khi khởi chạy.

---

## 3. Chi tiết cấu hình & Các mục cần chỉnh sửa

Để hệ thống hoạt động, cần can thiệp vào các mục sau:

### A. File cấu hình ứng dụng
* **WordPress (`/public_html/wp-config.php`):** Cập nhật `DB_NAME`, `DB_USER`, `DB_PASSWORD`.
* **Laravel (`/public_html/laravel/.env`):**
    * `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD` (Phải có Prefix).
    * `APP_URL=https://...` (Chuyển sang giao thức bảo mật).
    * `APP_DEBUG=false` (Tắt debug khi chạy chính thức).

### B. File điều hướng (`.htaccess`)
Cần thêm đoạn mã Force HTTPS lên trên cùng của file `.htaccess` (đặc biệt là trong `/public_html/laravel/public/`):

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

### C. Giao diện cPanel UI
* **Database Wizard:** Nơi tạo Database và **phải thực hiện bước Add User to Database** (Cấp quyền All Privileges).
* **Domains:** Bỏ tick "Share document root" cho Addon Domain thứ hai.
* **SSL/TLS -> Manage SSL sites:** Nơi dán 3 đoạn mã CRT, KEY, và CABUNDLE từ VPS sang.

---
