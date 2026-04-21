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

  + Sau khi upload source và import database, vào domain wordpress kiểm tra https://wp.giahung.vietnix.tech/
<img width="1785" height="929" alt="image" src="https://github.com/user-attachments/assets/d8770874-349a-4183-b7db-112fd8b810d7" />

# Cài đặt Themes và Plugins
Vào trang portal https://portal.vietnix.vn/index.php?rp=/download để tải themes và plugins
<img width="1382" height="549" alt="Screenshot from 2026-04-20 17-19-33" src="https://github.com/user-attachments/assets/729aaae7-b885-4b0a-b407-600474174a6a" />

- Tải về `Rank Math SEO`, `Mytheme Shop`, `Elementor`, `Divi Theme`

- Divi Theme: là 1 hệ sinh thái gồm cả Theme và Builder đi kèm. Nó cực kỳ linh hoạt nhưng khá nặng, đòi hỏi server phải cấu hình tốt
    + Vào trang quản trị wordpress tìm `Appearance` (Giao diện) -> `Add New` (Thêm giao diện mới) -> `Upload Theme` (Tải giao diện lên), chọn file đã tải về của `Divi`.
    <img width="653" height="338" alt="image" src="https://github.com/user-attachments/assets/11688c59-14fd-431f-bd23-23f1cc23a731" />
    <img width="1159" height="406" alt="image" src="https://github.com/user-attachments/assets/af498e49-272c-419f-905d-c59d94547f48" />
    <img width="686" height="327" alt="image" src="https://github.com/user-attachments/assets/bd584e5f-9c2f-474c-81dd-61ad5f95571e" />

    + Kết quả và áp dụng vào website wordpress (Lưu ý: vì đang làm lab nên có thể thử nghiệm để xem chức năng, vì theme có thể xung đột với theme có sẵn làm bể giao diện)
    <img width="1418" height="969" alt="image" src="https://github.com/user-attachments/assets/66db08f2-87f1-472a-9524-8d1c57c0bd7c" />
    <img width="1472" height="877" alt="image" src="https://github.com/user-attachments/assets/da8587fc-f82e-4046-995a-0faf1a11e3b6" />

- Plugin (Rank Math, Elementor, MyTheme Shop)
Vào Plugins -> Add New -> Upload Plugin.
Tải lên lần lượt các file .zip của Rank Math Pro, MyTheme Shop và Elementor Pro.
- Vào trang quản trị wordpress tìm `Plugin` -> `Cài plugin` -> `Tải` plugin lên, chọn file đã tải về
  + Rank Math Pro: tự động phân tích nội dung, từ khóa và kỹ thuật (Sitemap, Schema) để giúp website leo hạng trên Google. Nó có giao diện chấm điểm (0-100) rất trực quan
    <img width="1326" height="846" alt="image" src="https://github.com/user-attachments/assets/b16f5601-a073-44de-95e4-3b60a907796f" />
    <img width="856" height="673" alt="image" src="https://github.com/user-attachments/assets/f2bcf690-eb73-4733-9257-6248de9e277a" />
    <img width="1213" height="862" alt="image" src="https://github.com/user-attachments/assets/3d2447da-e382-4f3a-9ddc-02127757ebeb" />

  + MyTheme Shop: đây là kho theme nổi tiếng với các giao diện cực nhẹ, mã nguồn sạch và được tối ưu sẵn cho SEO. Thường dùng cho các trang tin tức hoặc blog cần tải nhanh
  <img width="1316" height="459" alt="image" src="https://github.com/user-attachments/assets/c7cea399-383a-4570-ad4b-d8853f7a8075" />
  <img width="1759" height="460" alt="image" src="https://github.com/user-attachments/assets/1d8e6ceb-6abc-41d7-98d4-17b2abd5f3f8" />

  + Elementor: là 1 trong các page builder mạnh nhất hiện nay. Giúp thiết kế mọi giao diện từ trang chủ đến trang bán hàng bằng cách kéo thả mà không cần viết một dòng code nào. Plugin này yêu cầu cài thêm 1 plugin khác là `Elementor Website Builder` để hoạt động
  <img width="885" height="256" alt="image" src="https://github.com/user-attachments/assets/c2c7f26b-ed40-42cc-91cb-a56f29141fbf" />
  <img width="531" height="375" alt="image" src="https://github.com/user-attachments/assets/9eb9b3ba-682d-4389-b7f4-2a4c3c15395a" />
  <img width="1793" height="885" alt="image" src="https://github.com/user-attachments/assets/696246cb-898b-45f4-99c3-073ff038b26e" />
