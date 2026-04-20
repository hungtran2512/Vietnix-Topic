# AAPanel
aaPanel là bảng điều khiển (control panel) quản trị VPS/Server miễn phí, mã nguồn mở, giúp quản lý website, database, FTP, và file qua giao diện đồ họa trực quan (GUI) thay vì dòng lệnh. Được phát triển bởi BT.cn, đây là phiên bản quốc tế của BAOTA Panel, tối ưu hóa cho Linux với cơ chế cài đặt phần mềm "một cú nhấp chuột" (one-click). 
Các đặc điểm chính của aaPanel:
  - Miễn phí & Dễ sử dụng: phù hợp cho người mới bắt đầu quản trị server.
  - Giao diện trực quan: quản lý mọi thứ qua trình duyệt web mà không cần thành thạo lệnh Linux.
  - Tích hợp mạnh mẽ: hỗ trợ cài đặt nhanh các thành phần như LEMP (Linux, Nginx, MySQL, PHP) hoặc LAMP (Linux, Apache, MySQL, PHP).
  - Tính năng đa dạng: hỗ trợ quản lý file, tạo database, sao lưu (backup), bảo mật SSL, và quản lý Docker.
  - Nhẹ và Tối ưu: không tiêu tốn quá nhiều tài nguyên máy chủ.

**aaPanel là lựa chọn phổ biến thay thế cho các bảng điều khiển trả phí như cPanel hay DirectAdmin.**

# Quá trình cài đặt
  - Đầu tiên chạy lệnh `apt-get update -y && apt-get upgrade -y` để cập nhật hệ thống
  - Trên terminal ssh vps, chạy lệnh `wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && sudo bash install.sh aapanel`
    + Lệnh này sẽ tự cài đặt script aapanel và cấu hình mọi thứ
  - Kết quả sau khi hoàn tất sẽ giống như sau: 
  ```
  ==================================================================
  Congratulations! Installed successfully!
  ==================================================================
  aaPanel Internet Address: https://IP_VPS:24415/ab83be78
  aaPanel Internal Address: https://IP_VPS:24415/ab83be78
  username: x06lbnix
  password: d67057f3
  Warning:
  If you cannot access the panel, 
  release the following port (24415|888|80|443|20|21) in the security group
  ==================================================================
  Time consumed: 1 Minute!
  ```

  - Trong quá trình cài đặt, firewall đã tự động điều chỉnh và mở các port cần thiết để có thể sử dụng aaPanel trên trình duyệt. Kiểm tra bằng lệnh `ufw status`
  <img width="546" height="472" alt="Screenshot from 2026-04-20 14-01-28" src="https://github.com/user-attachments/assets/2c584746-803a-4066-a56b-dc6095cb5a8b" />

  - Truy cập vào aaPanel bằng link và tài khoản mật khẩu hệ thống đã gửi.
  <img width="546" height="472" alt="image" src="https://github.com/user-attachments/assets/0b63012f-4074-4106-82a0-c31213e870d3" />
  
  - Lựa chọn Software Stack:
    + Web Server: OpenLiteSpeed 1.8
    + MySQL: chọn MariaDB 10.11 vì nhẹ và ổn định hơn MySQL thuần
    + PHP: chọn bản 8.1 hoặc 8.2
    + Chọn quick install sau đó nhấn nút "One-click"
  <img width="978" height="735" alt="image" src="https://github.com/user-attachments/assets/459779bd-10ab-4992-8dff-671609a53e20" />
  <img width="802" height="599" alt="image" src="https://github.com/user-attachments/assets/547775d7-c8e1-4ecb-93f7-8eb8f10e7f03" />


