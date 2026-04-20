# Tạo website wordpress
- Ở thanh menu bên trái màn hình chọn `Website` -> chọn `Add site`
    <img width="201" height="216" alt="image" src="https://github.com/user-attachments/assets/758f1aba-0ab2-4e24-819d-cb69660b0d4b" />
    <img width="285" height="135" alt="image" src="https://github.com/user-attachments/assets/0bf3c26d-8a49-49f6-b823-ba482c85dd7d" />

- Thêm tên miền cho wordpress và nhập thông tin, sau đó chọn confirm
    <img width="41" height="41" alt="image" src="https://github.com/user-attachments/assets/127304d8-1176-4f3c-9b0e-ae923fd6da44" />
    <img width="813" height="638" alt="image" src="https://github.com/user-attachments/assets/7af725d5-52c0-4fe8-bb0d-297e1ab8e9ce" />
    <img width="779" height="240" alt="image" src="https://github.com/user-attachments/assets/2d87c2e5-d692-4f11-a0a6-d59e9c53d02b" />

  + Kết quả
  <img width="621" height="231" alt="image" src="https://github.com/user-attachments/assets/efa5396b-a982-4be4-a7b5-945c24b289e4" />
  
  + Vào kiểm tra 
  <img width="1177" height="513" alt="image" src="https://github.com/user-attachments/assets/69849a17-48b4-4568-b44f-5088f7757dae" />

- Upload source wordpress vào aaPanel
  + Vào mục Files -> vào document root `/www/wwwroot/wp.giahung.vietnix.tech`, click `File Operations` và click `Upload`, chọn file nén source wordpress -> sau khi upload file nén, click chuột phải chọn `unzip`
  + Vào thư mục wordpress chọn tất cả file, folder và chọn cut -> paste tất cả ra thư mục `wp.giahung.vietnix.tech`
    <img width="973" height="851" alt="image" src="https://github.com/user-attachments/assets/dba43e2d-6bf0-4b9f-a62f-75e87acbcca7" />

- Upload database wordpress
  + Vào mục `Database`, tìm database đã tạo khi `Add site`, chọn import
  <img width="834" height="217" alt="image" src="https://github.com/user-attachments/assets/94bb0c78-6884-4244-8064-0599cd09cadb" />

  + Vào file `wp-config.php` của wordpress chỉnh sửa lại thông tin database
  <img width="392" height="138" alt="image" src="https://github.com/user-attachments/assets/056f6e2d-90f0-45f1-ac59-c8addf6d9708" />
