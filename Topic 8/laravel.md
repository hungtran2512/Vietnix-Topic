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
<img width="1348" height="578" alt="image" src="https://github.com/user-attachments/assets/ef2bd118-2a8a-4a03-aebc-37434e86ef3f" />
<img width="784" height="841" alt="image" src="https://github.com/user-attachments/assets/f6a4c456-19d7-4170-a32c-1133fe555963" />
<img width="784" height="48" alt="image" src="https://github.com/user-attachments/assets/f0349b3f-712e-4924-840d-da47bd580433" />

- Vào phpMyAdmin -> chọn database vừa tạo -> import
<img width="603" height="292" alt="image" src="https://github.com/user-attachments/assets/a7a43e9d-7529-4f5a-8da0-68c4085cd2f8" />
<img width="564" height="43" alt="image" src="https://github.com/user-attachments/assets/fd6880ab-657e-45c8-9868-595e1bd1c2ae" />

- Vào file `wp-config.php` sửa thông tin database vừa tạo
<img width="424" height="192" alt="image" src="https://github.com/user-attachments/assets/31b0a43e-617f-4d78-b56c-dfa06bbc9ef1" />

- Trong thư mục wordpress, xóa file `index.html` (đây là trang mặc định khi tạo từ vestacp thêm domain) vì web server là nginx/apache ưu tiên đọc file `index.html` nên cần xóa đi để đọc file `index.php` của source wordpress để website wordpress hoạt động

- Kiểm tra https://wp.giahung.vietnix.tech/
<img width="1793" height="979" alt="image" src="https://github.com/user-attachments/assets/206ec75c-579e-4989-8706-894c1f1cb526" />

