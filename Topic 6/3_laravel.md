# Tạo website laravel
- Ở thanh menu bên trái màn hình chọn `Website` -> chọn `Add site`
    <img width="201" height="216" alt="image" src="https://github.com/user-attachments/assets/758f1aba-0ab2-4e24-819d-cb69660b0d4b" />
    <img width="285" height="135" alt="image" src="https://github.com/user-attachments/assets/0bf3c26d-8a49-49f6-b823-ba482c85dd7d" />

- Thêm tên miền cho laravel và nhập thông tin, sau đó chọn confirm
    <img width="798" height="631" alt="image" src="https://github.com/user-attachments/assets/8676f72b-2732-4d1e-9306-9de8a6de50b2" />

  + Kết quả
  <img width="592" height="224" alt="image" src="https://github.com/user-attachments/assets/db21311c-1be9-46dc-b7e8-912a503d305d" />

  + Vào kiểm tra 
  <img width="1391" height="563" alt="image" src="https://github.com/user-attachments/assets/166a2920-8322-41cd-bd60-1666bce5c059" />

- Upload source laravel vào aaPanel
  + Vào mục Files -> vào document root `/www/wwwroot/laravel.giahung.vietnix.tech`, click `File Operations` và click `Upload`, chọn file nén source laravel -> sau khi upload file nén, click chuột phải chọn `unzip`
  <img width="1163" height="581" alt="image" src="https://github.com/user-attachments/assets/d96c315d-14ef-4b6d-a0f2-027304784433" />

  + Vào thư mục laravel chọn tất cả file, folder và chọn cut -> paste tất cả ra thư mục `laravel.giahung.vietnix.tech`
    <img width="1068" height="759" alt="image" src="https://github.com/user-attachments/assets/0ff9b7c8-10ad-4454-a7fb-94e6764687e5" />

  + Vào phần quản lý site tìm `Directory` chọn `Running Directory` là `/public` và Save
  <img width="866" height="502" alt="image" src="https://github.com/user-attachments/assets/9588eb69-899f-4f2a-9478-2d71c014e472" />

- Upload database wordpress
  + Vào mục `Database`, tìm database đã tạo khi `Add site`, chọn import
  <img width="828" height="228" alt="image" src="https://github.com/user-attachments/assets/3b753c31-6645-4be9-ba6d-c145142122a9" />

  + Vào file `.env` của laravel chỉnh sửa lại thông tin database
  <img width="215" height="108" alt="image" src="https://github.com/user-attachments/assets/96465715-40f4-44ab-b1de-23203b010e93" />

  + Sau khi upload source và import database, vào domain laravel kiểm tra https://laravel.giahung.vietnix.tech/
<img width="1286" height="968" alt="image" src="https://github.com/user-attachments/assets/57260883-068b-4d97-b161-7cbf3d10da42" />

