# Windows Server
## Truy cập vps win server
Mặc định Windows Server không cài sẵn dịch vụ SSH như Linux
-Dùng công cụ Remmina: đây là công cụ mặc định và tốt nhất trên Ubuntu để điều khiển máy tính Windows từ xa
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
