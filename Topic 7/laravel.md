# Deploy Laravel với CyberPanel
1. Tạo website
* Sau khi đăng nhập vào CyberPanel, tìm mục `Website` ở thanh bẹn trái -> chọn `Create Website`
<img width="241" height="372" alt="image" src="https://github.com/user-attachments/assets/f550878f-4b7a-40ae-b3d3-e2e6edc5d301" />

* Nhập thông tin và click `Create Website`
<img width="1158" height="771" alt="image" src="https://github.com/user-attachments/assets/97f7cf03-d856-42eb-a7a7-f07ffec06907" />

* Kết quả
<img width="900" height="647" alt="image" src="https://github.com/user-attachments/assets/1166baec-dbc9-443a-b9d6-1442e3546e40" />
<img width="1302" height="523" alt="image" src="https://github.com/user-attachments/assets/857c4cda-5320-47f0-8889-45c7b8993318" />

2. Upload source laravel
* Vào `List Website`, chọn File Manager của tên miền vừa tạo, upload source wordpress vào
<img width="1361" height="465" alt="image" src="https://github.com/user-attachments/assets/ffa7139a-336e-4279-96cf-c5325b2e64f5" />
<img width="1719" height="455" alt="image" src="https://github.com/user-attachments/assets/1aae455b-6467-4283-a651-5607e6fc4d3c" />
<img width="926" height="867" alt="image" src="https://github.com/user-attachments/assets/a6c3a2c2-a974-4b8a-b167-6efb628e4679" />

* Sau khi giải nén source, thì move các file, folder nằm ngay sau đường dẫn `/home/wp.giahung.vietnix.tech/public_html/`
<img width="796" height="434" alt="image" src="https://github.com/user-attachments/assets/ca25f8bc-a33d-4113-a5aa-b183ae419a7b" />
<img width="1666" height="953" alt="image" src="https://github.com/user-attachments/assets/b49e483a-b0e9-4453-af69-c8b0f44e515c" />

3. Import database wordpress
* Thêm database, trong mục `Databases` tìm `Create Database`, nhập thông tin vào tạo database
<img width="239" height="274" alt="image" src="https://github.com/user-attachments/assets/11904ecf-bbc5-4ab7-b341-fc4bad6da09c" />
<img width="880" height="779" alt="image" src="https://github.com/user-attachments/assets/68c63dfb-9df4-42f4-9039-8919366f1ad2" />

* Vào phpMyAdmin
<img width="231" height="285" alt="image" src="https://github.com/user-attachments/assets/e733461c-1fb5-417e-9e51-8adae4e8ddf1" />

* Chọn database vừa tạo và chọn `Import`, chọn đúng format file để import (ở đây là `sql.zip`)
<img width="1320" height="366" alt="image" src="https://github.com/user-attachments/assets/4ae04dde-8d81-48c3-89a9-9d547b03ec18" />
<img width="538" height="47" alt="image" src="https://github.com/user-attachments/assets/7f034938-b898-4e21-abbd-cfacc9e2fa4f" />

* Sau khi tạo và import database -> vào file `wp-config.php` để sửa thông tin database như các topic trước
<img width="663" height="243" alt="image" src="https://github.com/user-attachments/assets/b9b0f612-86fd-4690-8658-3f085516ed15" />

4. Kiểm tra
* Truy cập https://wp.giahung.vietnix.tech/
<img width="1794" height="998" alt="image" src="https://github.com/user-attachments/assets/17ef9a3d-34dd-42c6-ba11-d33f0f31c46a" />

5. Dùng lại cert SSL đã tạo từ certbot
* Vào Websites -> List Websites -> chọn Manage
<img width="1375" height="336" alt="image" src="https://github.com/user-attachments/assets/45fc2f73-3c27-4f62-80a5-5bfbaf3a62a8" />

* Tìm `Configurations` chọn `Add SSL` thêm cert và private key -> nhấn Save
<img width="1375" height="455" alt="image" src="https://github.com/user-attachments/assets/9f576267-5d69-4d24-91b1-c80092a3da65" />
<img width="1313" height="628" alt="image" src="https://github.com/user-attachments/assets/210f1f02-f218-4446-b512-0564a40c1495" />

