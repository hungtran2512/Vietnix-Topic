IIS (Internet Information Services) là một máy chủ web do Microsoft phát triển, chuyên chạy trên hệ điều hành Windows để lưu trữ và cung cấp các ứng dụng web, dịch vụ FTP và các giao thức khác. IIS hỗ trợ việc chuyển tải nội dung trên mạng bằng các giao thức phổ biến như HTTP, HTTPS, FTP, SMTP hay NNTP, giúp các doanh nghiệp, tổ chức dễ dàng quản lý cũng như phân phối nội dung web trên cả môi trường Internet lẫn Intranet.
Tương tự như Apache hay Nginx bên Linux thì IIS là web server trên Windows.

**Cài đặt Webserver IIS (Internet Information Services)**

### Bước 1: Mở trình quản lý Server
<img width="1804" height="802" alt="image" src="https://github.com/user-attachments/assets/6d478de8-95e6-4081-b69d-daa573f7d5c2" />

1. Tại màn hình `Server Manager` nhấn vào dòng `(2) Add roles and features`
2. Nhấn **Next** liên tục 3 lần cho đến phần **Server Roles**.
<img width="790" height="562" alt="image" src="https://github.com/user-attachments/assets/3f05be00-7a54-4773-ae4c-62d66620c672" />

### Bước 2: Chọn Role Web Server (IIS)
- Trong danh sách Roles, tích vào ô **Web Server (IIS)** và mở rộng các mục con + tick các tính năng và chọn next
<img width="224" height="28" alt="image" src="https://github.com/user-attachments/assets/17ffb483-7918-4ba7-85e5-84520ef3a28a" />
<img width="690" height="881" alt="image" src="https://github.com/user-attachments/assets/067d5868-c1a9-4362-a3d9-bd4b04cb67d3" />

- Chọn Install
<img width="1437" height="881" alt="image" src="https://github.com/user-attachments/assets/4fd9b1b3-082c-4d2d-98aa-4a5297c94e81" />
<img width="292" height="124" alt="image" src="https://github.com/user-attachments/assets/eee03b37-485a-4b2b-89ac-5a9d3832563b" />
<img width="246" height="259" alt="image" src="https://github.com/user-attachments/assets/4a35b486-b637-47ff-b883-5e1d215156ec" />

- Truy cập để kiểm tra
<img width="1249" height="758" alt="image" src="https://github.com/user-attachments/assets/1deaab32-aeaf-4cad-bf22-e0174b4eb947" />

Vì WordPress chạy bằng ngôn ngữ PHP, nên sau khi cài xong IIS, cần cài đặt PHP
1. Tải và cấu hình **PHP for Windows** vào trang chủ https://www.php.net/downloads.php?os=windows chọn bản php 8.2 tải bản zip `VS16 x64 Non Thread Safe `
<img width="1055" height="757" alt="image" src="https://github.com/user-attachments/assets/62b180d8-99e2-4c29-a7bb-608ab213f404" />
2. Giải nén và Cấu hình file php.ini
* Giải nén toàn bộ file Zip PHP
* Tìm file php.ini-development, đổi tên nó thành php.ini
* Mở file php.ini bằng Notepad và tìm rồi sửa các dòng sau (bỏ dấu ; ở đầu dòng):
  ```
  extension_dir = "ext"
  cgi.force_redirect = 0
  cgi.fix_pathinfo = 1
  fastcgi.impersonate = 1
  ```
* Bật các extension cần cho WordPress: Tìm và bỏ dấu ; trước các dòng:
  ```
  extension=curl
  extension=mbstring
  extension=mysqli (nếu dùng MySQL)
  extension=openssl
  extension=pdo_mysql
  extension=gd
  ```

3. Khai báo PHP trong IIS (Handler Mappings)

* Mở IIS Manager ( vào Tools -> Internet Information Services (IIS) Manager trong Server Manager)
<img width="697" height="545" alt="image" src="https://github.com/user-attachments/assets/7e8924e9-bc0c-4f0c-8f52-7c29c3bad631" />

* Ở cột bên trái, nhấn vào tên Server (TRAINING-GIAHUN)
* Ở khung giữa, tìm và nhấp đúp vào biểu tượng Handler Mappings
<img width="1357" height="657" alt="image" src="https://github.com/user-attachments/assets/41b0bc5d-9916-4aa3-859e-0243e4daa4cf" />

* Ở cột Actions bên phải ngoài cùng, nhấn vào dòng Add Module Mapping
<img width="197" height="180" alt="image" src="https://github.com/user-attachments/assets/32b87d6b-6b43-4285-9e13-2e6ef0a85745" />

* Điền chính xác các thông số sau vào bảng hiện ra:
Request path: *.php
Module: Chọn FastCgiModule (Nếu không thấy cái này là do lúc nãy chưa cài CGI ở bước cài IIS đấy).
Executable (Optional): Nhấn vào nút ba chấm ... và tìm đến file php-cgi.exe trong thư mục php
Name: tên bất kì, ví dụ: PHP_FastCGI
<img width="463" height="407" alt="image" src="https://github.com/user-attachments/assets/3523b786-8e33-4032-8d4c-210ab2f090d9" />

