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

- Lúc này cần có database cho wordpress để hoàn thành website

## Cài đặt database server
- Dùng MySQL
- Vào trang tải phần mềm, tải bản `mysql-installer-community-5.7.44.0.msi`
<img width="992" height="726" alt="image" src="https://github.com/user-attachments/assets/28ae7d20-42ae-4d1e-a3a6-740783e0644d" />

- Chọn Server Only -> Execute
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/25d330a1-6b0d-4a11-b21c-3938eb6edb0f" />
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/0f1069b9-5395-46d7-981b-f20203bfc9b1" />

- Chọn config type: `Server Computer`
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/4e204afb-6ea7-4a73-a6a6-7ec9fa8486f9" />

- Chọn Next hết để dùng cấu hình mặc định, đến phần yêu cầu mật khẩu -> nhập mật khẩu để vào database server
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/a08cbde4-9c95-4a3c-a4fc-cc9d5dddb1ce" />

- Chọn next tới Apply Configuration -> Execute
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/959fc84c-48e8-439f-ad5c-0eaee83500c1" />
<img width="786" height="589" alt="image" src="https://github.com/user-attachments/assets/2e76cd7a-34c7-40ca-be02-f40d01c05e81" />

- Vào mysql và tạo database, user
<img width="244" height="44" alt="image" src="https://github.com/user-attachments/assets/289e4518-1b5d-4f9a-9c8c-bed116495f3e" />
<img width="518" height="234" alt="image" src="https://github.com/user-attachments/assets/3b2d6443-6635-4b93-8fbe-12347b9b5f1a" />

## Quay lại wordpress để cài đặt
<img width="848" height="729" alt="image" src="https://github.com/user-attachments/assets/11f44a7e-3924-4d36-bdc4-4ca5c41b6d52" />
<img width="842" height="330" alt="image" src="https://github.com/user-attachments/assets/62cc34cc-3790-40aa-af1b-6cb4087799ab" />
<img width="843" height="941" alt="image" src="https://github.com/user-attachments/assets/5f33d5fd-5614-474d-b40a-7e3c32d8ecf8" />
<img width="843" height="474" alt="image" src="https://github.com/user-attachments/assets/df6f49a0-19fa-4a1a-926f-8820141ae2e8" />

* Kiểm tra website wordpress và trang quản trị
<img width="1400" height="924" alt="image" src="https://github.com/user-attachments/assets/12d49c5b-7bf6-4405-a607-58991298ba8b" />
<img width="1802" height="949" alt="image" src="https://github.com/user-attachments/assets/88c81a45-6ef0-4b2a-aed8-be3896177584" />

