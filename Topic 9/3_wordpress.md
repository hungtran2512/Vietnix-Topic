# Wordpress
## Cài đặt Website WordPress
* WordPress cần PHP để chạy và cần một nơi chứa dữ liệu (database).
* Chuẩn bị mã nguồn
- Tải bản WordPress mới nhất: [wordpress.org/latest.zip](https://wordpress.org/latest.zip)
- Giải nén và copy toàn bộ nội dung bên trong thư mục wordpress vào: C:\inetpub\wwwroot
<img width="687" height="456" alt="image" src="https://github.com/user-attachments/assets/7d522e5f-a982-4cea-8c7a-a97c3d560c7e" />
<img width="727" height="535" alt="image" src="https://github.com/user-attachments/assets/34f2b2c2-a9de-4ee0-8f5e-9f7f04ef38dd" />

- Phân quyền (Bắt buộc): Chuột phải vào thư mục wwwroot -> Properties -> Security -> Edit -> Add -> Gõ IUSR -> OK -> Tích Full Control -> OK. Tương tự với IIS_IUSRS
<img width="1262" height="518" alt="image" src="https://github.com/user-attachments/assets/15e830f2-86f3-4726-8edd-8835c5098665" />
<img width="360" height="454" alt="image" src="https://github.com/user-attachments/assets/c2648885-3884-4e7e-b39b-04f948c99732" />
<img width="360" height="454" alt="image" src="https://github.com/user-attachments/assets/a16c2729-9a01-4759-976d-4177ec8ea820" />

- Truy cập lại để kiểm tra -> trang setup của wordpress
<img width="1408" height="735" alt="image" src="https://github.com/user-attachments/assets/7edfa5f6-b60c-4181-9250-a4cbcaaabbda" />
<img width="783" height="685" alt="image" src="https://github.com/user-attachments/assets/f0146ded-3bf9-42a8-9abe-7209f594a0b1" />

- Lúc này wordpress sẽ báo lỗi kết nối database -> cài đặt mysql hoặc sql server để có database cho wordpress
<img width="781" height="468" alt="image" src="https://github.com/user-attachments/assets/cdf436fe-0f79-4cb8-8b6a-0acf13c02c3e" />

## Cài đặt database server
- Dùng mariadb (là database server tương tự mysql)
<img width="1431" height="846" alt="image" src="https://github.com/user-attachments/assets/d6d41dd0-6148-4192-8c9c-99662da6e073" />
<img width="489" height="381" alt="image" src="https://github.com/user-attachments/assets/9409c69e-c84b-47f8-bdb5-661ff83b34fb" />

- Chọn Next hết để dùng cấu hình mặc định, đến phần yêu cầu mật khẩu -> nhập mật khẩu để vào database server
<img width="489" height="381" alt="image" src="https://github.com/user-attachments/assets/50f53432-18ff-4f1e-9653-0130c8926426" />

- Chọn next tới phần cài đặt -> nhấn `Installation`
<img width="489" height="381" alt="image" src="https://github.com/user-attachments/assets/9bcf3ee5-9659-42d8-a83b-c96c7373a132" />


