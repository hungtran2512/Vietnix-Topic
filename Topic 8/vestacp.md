# VestaCP
1. VestaCP là gì?
- VestaCP là một bảng điều khiển quản lý máy chủ Web Hosting miễn phí, mã nguồn mở, được phát triển bởi Vesta Software và phát hành lần đầu tiên vào năm 2009. Nền tảng này dễ cài đặt và cấu hình bảng điều khiển thường được dựa trên nền tảng Linux. Bất cứ ai cũng có thể dùng nền tảng này để quản lý các trang web trong VPS. 

- VestaCP có thể hỗ trợ mô hình Nginx + Apache. Đây là những mô hình web server được sử dụng nhiều nhất hiện nay vì Nginx có thể giải quyết các nội dung tĩnh (ảnh, font chữ,..), còn Apache sẽ xử lý các request động. Từ đó, trang web có thể đáp ứng được nhiều truy cập cùng lúc nhưng ít lãng phí tài nguyên của máy chủ.
- Ưu điểm khi sử dụng VestaCP
  + VestaCP có nhiều ưu điểm nổi bật như:
```
    Không mất phí sử dụng
    Giao diện đơn giản
    Cấu hình dễ sử dụng
    Các tính năng thân thiện với người dùng
    Có khả năng sao lưu nhanh
    Có thể hỗ trợ DKIM
    Có tích hợp sẵn WHMCS để bán host
    Tự động cập nhật phiên bản mới
    Có chức năng chống virus và spam
    Giám sát hệ thống chặt chẽ 
    Có chứng chỉ SSL
```

- Nhược điểm khi sử dụng VestaCP
  + Sử dụng VestaCP có những mặt hạn chế nào? Một số tính năng và cấu hình sẽ không thể được tùy chỉnh hoặc mở rộng. Điều này dẫn đến việc điều khiển không có tính linh động. 
  + Bên cạnh đó, nền tảng này chưa được nhiều người biết đến như với cPanel. Do đó, người dùng muốn sử dụng VestaCP đều gặp khó khăn vì cộng đồng sử dụng ít. Phần lớn người dùng phải tự tìm hiểu và tự trải nghiệm. 

# Cài đặt VestaCP
```bash
# Tải script cài đặt
wget https://vestacp.com/pub/vst-install.sh

# Chạy cài đặt (có thể tùy chỉnh các thành phần)
bash vst-install.sh
```
<img width="907" height="739" alt="image" src="https://github.com/user-attachments/assets/cb1fcebc-44ed-4aba-a58f-75218fb08304" />

* Quá trình cài đặt tốn khoảng 15 phút hoặc lâu hơn
* Kết quả
```bash
=======================================================

 _|      _|  _|_|_|_|    _|_|_|  _|_|_|_|_|    _|_|   
 _|      _|  _|        _|            _|      _|    _| 
 _|      _|  _|_|_|      _|_|        _|      _|_|_|_| 
   _|  _|    _|              _|      _|      _|    _| 
     _|      _|_|_|_|  _|_|_|        _|      _|    _| 


Congratulations, you have just successfully installed Vesta Control Panel

    https://panel.giahung.vietnix.tech:8083
    username: admin
    password: R0RSGLdkG1

We hope that you enjoy your installation of Vesta. Please feel free to contact us anytime if you have any questions.
Thank you.

--
Sincerely yours
vestacp.com team
```
* Lưu ý: dùng ip vps để vào với port 8083 vì domain chưa trỏ tới vps do chỉ đặt để tượng trưng

* Chạy các lệnh sau khi gặp vấn đề không login được
```bash
# Khởi động lại dịch vụ quản lý nội bộ của VestaCP
root@training-giahung:~# service vesta restart

# Mở cổng firewall
root@training-giahung:~# ufw allow 8083/tcp
Rules updated
Rules updated (v6)
root@training-giahung:~# ufw allow 80/tcp
Rules updated
Rules updated (v6)
root@training-giahung:~# ufw allow 443/tcp
Rules updated
Rules updated (v6)

# Kiểm tra và sửa lỗi quyền quản trị tối cao
root@training-giahung:~# visudo -c
>>> /etc/sudoers.d/90-cloud-init-users: syntax error near line 20 <<<
parse error in /etc/sudoers.d/90-cloud-init-users near line 20

# xóa file lỗi sau khi kiểm tra
root@training-giahung:~# rm -f /etc/sudoers.d/90-cloud-init-users

# kiểm tra lại
root@training-giahung:~# visudo -c
/etc/sudoers: parsed OK
/etc/sudoers.d/README: parsed OK
/etc/sudoers.d/admin: parsed OK
```

* Vào trang panel https://221.132.21.143:8083, đăng nhập bằng thông tin đã được cấp
<img width="1266" height="760" alt="image" src="https://github.com/user-attachments/assets/1eb22ea8-3483-47b2-81f8-43695eb1cede" />
<img width="1794" height="977" alt="image" src="https://github.com/user-attachments/assets/d9bdca87-1ad1-4d12-a7d9-ba9c8359d009" />
