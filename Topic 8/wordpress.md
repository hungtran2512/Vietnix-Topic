# Deploy WordPress lên VestaCP

## Tạo domain
* Vào mục `WEB`, chọn dấu `+` để thêm domain mới
<img width="1794" height="977" alt="Screenshot from 2026-04-23 11-03-03" src="https://github.com/user-attachments/assets/4ee61ea9-2539-41fb-8534-d9b74d6176ae" />

* Nhập thông tin
<img width="696" height="763" alt="image" src="https://github.com/user-attachments/assets/18578089-51b6-4208-a062-77cfc3d06bb0" />
<img width="771" height="808" alt="image" src="https://github.com/user-attachments/assets/abc81507-5d2d-4c8a-88d0-08018409db0a" />

* Kết quả
<img width="675" height="53" alt="image" src="https://github.com/user-attachments/assets/7e7d3df3-d707-4d14-ae49-29e44b125e33" />
<img width="1300" height="326" alt="image" src="https://github.com/user-attachments/assets/2046273c-fc01-470e-abdd-54b553f3ad7e" />

## Upload source wordpress
- Vì VestaCP không có chức năng upload file cho web nên cần thao tác trên terminal
```
# Đẩy file source web (.tar.gz) từ terminal không phải vps
scp /home/dahunq/*.tar.gz root@221.132.21.143:/home/admin/tmp/

# Từ terminal đang ssh vps
# Di chuyển file vào đúng thư mục web
mv /home/admin/tmp/wp_clean.tar.gz /home/admin/web/wp.giahung.vietnix.tech/public_html/

# Giải nén
cd /home/admin/web/wp.giahung.vietnix.tech/public_html/
tar -xzvf wp_clean.tar.gz

# Di chuyển các file ra thư mục /home/admin/web/wp.giahung.vietnix.tech/public_html/
mv wordpress/* .
# Di chuyển file ẩn (ví dụ .htaccess)
mv wordpress/.[!.]* .
```

<img width="843" height="646" alt="image" src="https://github.com/user-attachments/assets/0b23879b-3dd6-4219-819c-cb31fa0b08bb" />

- Trên web quản trị VestaCP, tìm mục DB -> bấm dấu `+` để thêm database cho wordpress
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
