# Deploy WordPress với CyberPanel
1. Tạo website
* Sau khi đăng nhập vào CyberPanel, tìm mục `Website` ở thanh bẹn trái -> chọn `Create Website`
<img width="241" height="372" alt="image" src="https://github.com/user-attachments/assets/f550878f-4b7a-40ae-b3d3-e2e6edc5d301" />

* Nhập thông tin và click `Create Website`
<img width="900" height="647" alt="image" src="https://github.com/user-attachments/assets/93feded5-8606-458a-b84b-aaeebc3601f4" />

* Kết quả
<img width="900" height="647" alt="image" src="https://github.com/user-attachments/assets/1166baec-dbc9-443a-b9d6-1442e3546e40" />
<img width="1302" height="525" alt="image" src="https://github.com/user-attachments/assets/4a4ba2a3-6ec8-4f22-b832-5b51c33b64a6" />

2. Upload source wordpress
* Vào `List Website`, chọn File Manager của tên miền vừa tạo, upload source wordpress vào
<img width="1397" height="416" alt="image" src="https://github.com/user-attachments/assets/207db98f-53da-4cf4-8eec-ff7350576976" />
<img width="1630" height="488" alt="image" src="https://github.com/user-attachments/assets/0ecc7a09-a41e-4e8f-b6bd-b7ccd79f0bed" />
<img width="796" height="748" alt="image" src="https://github.com/user-attachments/assets/c4ab0cb6-9ddf-4663-9e79-dc9c098824f0" />

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
