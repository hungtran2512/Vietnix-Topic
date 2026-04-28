# Windows Server
## Truy cập vps win server
Mặc định Windows Server không cài sẵn dịch vụ SSH như Linux
- Dùng công cụ Remmina: đây là công cụ mặc định và tốt nhất trên Ubuntu để điều khiển máy tính Windows từ xa
1.  Cài đặt: Mở Terminal trên máy Ubuntu và gõ:
    ```bash
    sudo apt update
    sudo apt install remmina remmina-plugin-rdp -y
    ```
2.  Sử dụng:
    * Mở ứng dụng `Remmina` lên
    * Chọn giao thức là `RDP` (thanh menu thả xuống)
    * Nhập IP của VPS vào và nhấn enter
    * Sau đó điền thông tin đăng nhập
    * Kết quả sẽ thấy màn hình Windows hiện ra

<img width="137" height="149" alt="image" src="https://github.com/user-attachments/assets/21078d41-899a-4fdc-8902-964758618e58" />
<img width="605" height="453" alt="image" src="https://github.com/user-attachments/assets/4947c486-3308-4f11-9698-805c1d26d41f" />
<img width="822" height="514" alt="image" src="https://github.com/user-attachments/assets/33968164-957d-42e1-a8fa-6298bffed097" />
<img width="823" height="507" alt="image" src="https://github.com/user-attachments/assets/08cfda3c-f973-4200-b735-b1df501a1e5e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5dcff333-b613-4c76-b73e-ac4a04105f30" />

* Kết quả
<img width="1556" height="988" alt="image" src="https://github.com/user-attachments/assets/eb039829-0c71-4a56-ae47-aa756b61a124" />

## Thực hiện thao tác với các cổng (port)
- Nhấn nút `start`
<img width="77" height="86" alt="image" src="https://github.com/user-attachments/assets/8802cf52-9d91-4903-80c4-5434c6e4ba1f" />

- Tìm từ khóa firewall -> chọn `Windows Firewall with Advanced Security`
<img width="1567" height="1017" alt="image" src="https://github.com/user-attachments/assets/76ceb1d4-a4c6-425a-a794-bb95aed71e16" />

- Allow Port & Allow IP
    * Giả sử muốn cho phép Port 80 (Web) hoạt động và chỉ cho phép IP được chỉ định truy cập.
    * Bước 1: Ở cột bên trái, chọn `Inbound Rules`. Sau đó ở cột bên phải, chọn `New Rule`
<img width="438" height="248" alt="image" src="https://github.com/user-attachments/assets/8aeb78e7-6d86-4e4b-b8df-2b115be4ec25" />
<img width="341" height="236" alt="image" src="https://github.com/user-attachments/assets/dd828575-fc2e-4e61-8558-adf980185556" />

* Bước 2: Chọn Port -> Next 
<img width="1303" height="950" alt="image" src="https://github.com/user-attachments/assets/d27ba98a-f563-4a61-8342-9e923c8de72e" />

* Bước 3: Chọn TCP và gõ số cổng 80 vào ô Specific local ports -> Next
<img width="1303" height="950" alt="image" src="https://github.com/user-attachments/assets/48cf4703-37f8-4723-a955-4a8cbc7018c4" />

* Bước 4: Chọn Allow the connection -> Next
<img width="1303" height="950" alt="image" src="https://github.com/user-attachments/assets/ed44df4e-22a7-49bb-825e-0bab8d3d57b9" />

* Bước 5: Chọn hết (Domain, Private, Public) -> Next
<img width="1303" height="950" alt="image" src="https://github.com/user-attachments/assets/206e60e6-f9c2-48ec-a884-6d66c3a75a87" />

* Bước 6: Đặt tên cho rule, ví dụ: allow_web_80 -> Finish
<img width="1303" height="950" alt="image" src="https://github.com/user-attachments/assets/783cc2c1-7fa8-4a62-b216-c7dcf091908b" />

* Kết quả rule mới được tạo
<img width="604" height="655" alt="image" src="https://github.com/user-attachments/assets/e9c4e9e9-6342-4473-b3c2-1ff585bbf443" />

- Block Port & Block IP
    * Việc chặn thường dùng khi thấy hệ thống đang bị tấn công từ một dải IP lạ hoặc muốn đóng các cổng nguy hiểm
    * Chặn Port (Ví dụ chặn cổng 445)
    
    * Inbound Rules -> New Rule
    * Rule Type: Chọn Port -> Next
    * Protocol and Ports: Chọn TCP. Gõ cổng 445 -> Next
<img width="1292" height="937" alt="image" src="https://github.com/user-attachments/assets/e816526b-a905-488f-b838-14b865a5e62a" />

* Action: Chọn Block the connection -> Next
<img width="1292" height="937" alt="image" src="https://github.com/user-attachments/assets/09dc78e1-9a85-4c89-b5ca-d4ac02b77d91" />

* Profile: Chọn tất cả -> Next.

* Name: đặt tên rule dễ hiểu, ví dụ: block_smb_445 -> Finish
* Kết quả
<img width="592" height="601" alt="image" src="https://github.com/user-attachments/assets/2553e3f6-a3fd-43b7-861b-1fb734f89210" />

**Lưu ý: Trong Windows Firewall, luật Block luôn có quyền ưu tiên cao hơn luật Allow**

* Bước B: Chặn một IP cụ thể (Blacklist)
* Giả sử thấy được IP `1.2.3.4` đang cố tình dò mật khẩu VPS của mình:

* Tạo một Rule mới: Inbound Rules -> New Rule
* Rule Type: chọn Custom -> Next.
<img width="1282" height="948" alt="image" src="https://github.com/user-attachments/assets/46cdea08-43f5-4344-a9e6-7216e00ac664" />

* Program: Chọn All programs -> Next
* Protocol and Ports: Chọn Any -> Next
<img width="1282" height="948" alt="image" src="https://github.com/user-attachments/assets/acd6fcc8-510e-4059-a745-94544173d20c" />

* Scope: chọn These IP addresses -> nhấn add -> chọn This IP address or subnet -> nhập IP -> OK
<img width="343" height="376" alt="image" src="https://github.com/user-attachments/assets/c701728d-92f0-47f2-b0f2-a5728090cf1c" />

* Remote IP: Chọn These IP addresses -> Nhấn Add -> chọn This IP address range -> nhập range (trong hình chỉ để ví dụ) -> OK
<img width="343" height="376" alt="image" src="https://github.com/user-attachments/assets/30573596-adb1-4af7-bd57-9ec250be6ce3" />

* Xem kết quả và nhấn Next
<img width="708" height="582" alt="image" src="https://github.com/user-attachments/assets/ee695444-8188-4eed-ab43-89ef504f2d63" />

* Action: Chọn Block the connection -> Next
<img width="708" height="582" alt="image" src="https://github.com/user-attachments/assets/82240cd4-f096-48e6-af97-5996809a86cc" />

* Name: Đặt tên là blacklist_ip -> Finish
* Kết quả
<img width="1189" height="70" alt="image" src="https://github.com/user-attachments/assets/5ce419fe-e6ba-440f-b4f5-d06d2f0f5cc9" />

- Giới hạn Port, giới hạn IP: mục đích là chỉ cho phép IP mình thêm vào mới truy cập được cổng đã tạo
* Ví dụ với port `1433` của SQL Server -> tạo rule allow cho port 1433

* Mở Properties: Chuột phải vào rule `allow_db_1433` -> Chọn Properties
* Chỉnh Scope: Chuyển sang tab Scope
* Điền IP giới hạn:
  + Tại mục Remote IP address, tích chọn These IP addresses
  + Nhấn Add... -> Nhập một IP cụ thể (Ví dụ: IP máy Ubuntu)
  + Nhấn OK -> Apply
<img width="435" height="748" alt="image" src="https://github.com/user-attachments/assets/25bee533-3e02-413d-83c8-30c92ddc12db" />
