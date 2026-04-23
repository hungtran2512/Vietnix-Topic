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
  + Bên cạnh đó, nền tảng này chưa được nhiều người biết đến như với cPanel và Plesk. Do đó, người dùng muốn sử dụng VestaCP đều gặp khó khăn vì cộng đồng sử dụng ít. Phần lớn người dùng phải tự tìm hiểu và tự trải nghiệm. 

# Cài đặt VestaCP
```bash
# Tải script cài đặt
wget https://vestacp.com/pub/vst-install.sh

# Chạy cài đặt (có thể tùy chỉnh các thành phần)
bash vst-install.sh
```
<img width="907" height="739" alt="image" src="https://github.com/user-attachments/assets/cb1fcebc-44ed-4aba-a58f-75218fb08304" />

* Quá trình cài đặt tốn khoảng 15 phút hoặc lâu hơn
