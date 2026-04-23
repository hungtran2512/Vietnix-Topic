# Deploy Laravel lên VestaCP

## Tạo domain
* Vào mục `WEB`, chọn dấu `+` để thêm domain mới
<img width="1279" height="760" alt="image" src="https://github.com/user-attachments/assets/8dd8f6a9-f08d-4a78-a9c2-d7188dadb05c" />

* Nhập thông tin
<img width="756" height="765" alt="image" src="https://github.com/user-attachments/assets/5f6f096d-2a11-4edf-9a4a-eff8eb84e77f" />
<img width="767" height="807" alt="image" src="https://github.com/user-attachments/assets/1400d84f-4c64-48b1-9b33-f717ba731b79" />

* Kết quả
<img width="647" height="45" alt="image" src="https://github.com/user-attachments/assets/6fb86b70-503e-4401-9496-25892804ffcc" />
<img width="1246" height="280" alt="image" src="https://github.com/user-attachments/assets/c1629301-63a5-4fba-a3f8-518800758c3b" />

## Upload source laravel
- Vì VestaCP không có chức năng upload file cho web nên cần thao tác trên terminal
```bash
# Đẩy file source web (.tar.gz) từ terminal không phải vps
scp /home/dahunq/*.tar.gz root@221.132.21.143:/home/admin/tmp/

# Từ terminal đang ssh vps
# Di chuyển file vào đúng thư mục web
mv /home/admin/tmp/laravel_clean.tar.gz /home/admin/web/laravel.giahung.vietnix.tech/public_html/

# Giải nén
cd /home/admin/web/laravel.giahung.vietnix.tech/public_html/
tar -xzvf laravel_clean.tar.gz

# Di chuyển các file ra thư mục /home/admin/web/laravel.giahung.vietnix.tech/public_html/
mv laravel/* .
# Di chuyển file ẩn (ví dụ .env)
mv laravel/.[!.]* .
```

<img width="881" height="755" alt="image" src="https://github.com/user-attachments/assets/a19ed9b4-1fdb-4502-b58c-381a6d1f0075" />

- Trên web quản trị VestaCP, tìm mục DB -> bấm dấu `+` để thêm database cho laravel
<img width="1312" height="756" alt="image" src="https://github.com/user-attachments/assets/e9edca37-254a-44a0-8077-56461b465128" />
<img width="890" height="858" alt="image" src="https://github.com/user-attachments/assets/e4dac544-792b-4a82-8ec0-09245c03e0d5" />
<img width="779" height="43" alt="image" src="https://github.com/user-attachments/assets/485bfb00-f6f7-41df-b5df-9be2bc579f39" />

- Vào phpMyAdmin -> chọn database vừa tạo -> import
<img width="599" height="291" alt="image" src="https://github.com/user-attachments/assets/5a3f2b93-ed2e-4f52-b76f-fa26ed7f8864" />
<img width="536" height="47" alt="image" src="https://github.com/user-attachments/assets/f3090780-d0f9-4686-bcb0-27e585cc204f" />

- Vào file `.env` sửa thông tin database vừa tạo
<img width="287" height="79" alt="image" src="https://github.com/user-attachments/assets/7fe8f495-be62-4237-aaaa-6edf272ad0a9" />

- Chỉnh sửa file cấu hình apache `nano /home/admin/conf/web/laravel.giahung.vietnix.tech.apache2.conf` tìm `DocumentRoot` và chỉnh sửa đường dẫn thành `/home/admin/web/laravel.giahung.vietnix.tech/public_html/public` - tương tự với file `/home/admin/conf/web/laravel.giahung.vietnix.tech.apache2.ssl.conf`
- Tương tự với nginx `nano /home/admin/conf/web/laravel.giahung.vietnix.tech.nginx.conf` tìm `root` và chỉnh sửa đường dẫn thành `/home/admin/web/laravel.giahung.vietnix.tech/public_html/public` - tương tự với file `/home/admin/conf/web/laravel.giahung.vietnix.tech.nginx.ssl.conf`
- Khởi động lại 2 dịch vụ
  ```bash
  service apache2 restart
  service nginx restart
  ```
  
- Tương tự như khi deploy wordpress, trong thư mục laravel, xóa file `index.html`

- Kiểm tra https://laravel.giahung.vietnix.tech/
<img width="1260" height="540" alt="image" src="https://github.com/user-attachments/assets/d90d5b32-0274-469f-b15c-2efdf20e26a4" />

- Website vẫn chưa hoạt động vì laravel cần phiên bản php 8.1
```bash
# Cài đặt công cụ hỗ trợ kho lưu trữ
apt-get update
apt-get install software-properties-common -y


# Thêm kho PPA của Ondrej (Để lấy các thư viện phụ trợ nhanh hơn)
add-apt-repository ppa:ondrej/php -y
apt-get update

# Cài đặt thư viện nền cho Giai đoạn 1.2
apt-get install -y build-essential libxml2-dev libssl-dev libsqlite3-dev \
libcurl4-openssl-dev libpng-dev libjpeg-dev libonig-dev libzip-dev \
libreadline-dev libicu-dev

# Bắt đầu Giai đoạn biên dịch (Compile)
wget https://www.php.net/distributions/php-8.1.27.tar.gz
tar -xvf php-8.1.27.tar.gz
cd php-8.1.27

# Cấu hình (Configure):
./configure --prefix=/usr/local/php81 \
--with-config-file-path=/usr/local/php81 \
--enable-mbstring \
--enable-fpm \
--with-mysqli=mysqlnd \
--with-pdo-mysql=mysqlnd \
--with-openssl \
--with-curl \
--with-zlib \
--enable-gd \
--with-zip \
--enable-bcmath \
--enable-intl

make -j$(nproc)
make install

ln -s /usr/local/php81/bin/php /usr/bin/php81
```
<img width="552" height="93" alt="image" src="https://github.com/user-attachments/assets/91a03803-528a-4404-8146-1f6b1c06c717" />

- Các bước trên chỉ mới là cài đặt thủ công cho php 8.1, để VestaCP dùng phiên bản php này cần cấu hình
