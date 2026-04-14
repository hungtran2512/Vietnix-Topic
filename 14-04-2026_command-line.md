# **Linux Command Line**

## - Ping vietnix.vn và giải thích kết quả lệnh `ping` và `hping3`.
  - `ttl=` (time to live) là một số nguyên thể hiện số lượng giới hạn bước nhảy (hop). Ví dụ: là số lượng Router gói tín có thể đi qua trước khi bị hủy bỏ.
    + Mỗi khi gói tin đi qua một Router, giá trị của TTL sẽ trừ đi 1
    + *Mục đích*: ngăn chặn tình trạng gói tin bị lặp trên internet, ước tính được số lượng router đi qua từ máy nguồn đến máy đích
  - `time=` là tổng thời gian gói tin đi từ máy của mình đến đích và quay trở lại.
    + *Mục đích*: để đánh giá độ trễ và độ ổn định của mạng, time càng thấp và ít dao động thì kết nối mạng càng tốt và ổn định 
<img width="644" height="195" alt="image" src="https://github.com/user-attachments/assets/550ee7aa-5f0a-4dcd-841f-a6b1f249b472" />

  - Với kết quả ping vietnix.vn:
    + `ttl=53` có thể tính được gói tin đã đi qua `64 - 53 = 11` thiết bị trung gian (64 là giá trị ttl)
    + Các giá trị `time=` đều dưới 5ms chửng tỏ kết nối mạng tốt và ổn định

<img width="888" height="228" alt="image" src="https://github.com/user-attachments/assets/49ca01be-182e-46d3-94c0-6d5a6f576807" />
  - Với kết quả ping vietnix.vn:
    + Các giá trị `id=` là số định danh các gói tin
    + `len=46`: tổng độ dài gói tin phẩn hồi là 46 bytes
    + `ip=`: địa chỉ IP của máy chủ Vietnix đã trả lời
    + `ttl=53` có thể tính được gói tin đã đi qua `64 - 53 = 11` thiết bị trung gian (64 là giá trị ttl)
    + `icmp=`: số tự của gói tin, từ kết quả (bắt đầu từ 0 đến 3) cho thấy các gói tin vế đúng thứ tự
    + `rtt=`: thời gian phản hồi trong khoảng 3ms - 5ms -> khoảng cách địa lý giữa máy ping và server là gần nhau 

## - SSH Command:
  - Kết nối bằng password: cú pháp là
  - Kết nối bằng key.
  - Kết nối bằng port custom.

- SCP Command:
    + Copy 1 file.
    + Copy 1 folder.

- Rsync Command:
    + Copy file.
    + Copy folder.
    + `rsync incremental`.

- Cat Command:
    + Xem nội dung 1 file.
    + Xem dòng thứ `<n>` trong file.
    + Ghi nhiều dòng vào 1 file bằng EOF.

- Echo Command:
    + Chèn thêm 1 dòng vào cuối file.
    + Overwrite nội dung file.

- Tail/Head Command:
    + Sự khác biệt giữa `tail` và `head`.
    + Sự khác biệt giữa `tail` và `tailf`.

- Sed Command:
    + Find and replace string trong file.

- Traceroute/Tracert Command:
    + Thực hiện và giải thích kết quả.

- Netstat Command:
    + Hiển thị các socket đang listen.
    + Không resolve hostname.
    + Không resolve portname.
    + Display process name/PID.
    + Chỉ hiển thị socket TCP.
    + Chỉ hiển thị socket UDP.

- Sort Command:
    + Theo thứ tự tăng dần.
    + Theo thứ tự giảm dần.
    + Theo column.

- Uniq Command:
    + Lọc các dòng lặp lại.
    + Lọc và đếm số lượng dòng lặp lại.

- Wc Command:
    + Đếm số dòng.
    + Đếm số ký tự.

- Chmod, Chown, Chattr Command:
    + Phân quyền bằng số và chữ.
    + Đổi owner user/group.
    + Set Immutable Attribute.

- Find Command:
    + Tìm file đuôi `.log`.
    + Tìm folder tên `abc`.
    + Tìm file tên `abc`.
    + Tìm file `abc` và đặt quyền read only.

- Cp Command:
    + Copy file.
    + Copy folder.

- Mv Command:
    + Di chuyển/đổi tên file/folder.

- Cut Command:
    + Lấy ký tự thứ `<n>`.
    + Lấy từ ký tự `<n>` trở về sau.
    + Lấy đến ký tự thứ `<n>`.

- Dig Command:
    + Kiểm tra record A, MX, NS.
    + Kiểm tra record A, MX, NS với custom DNS.

- Tar/Zip/Unzip Command:
    + Nén/giải nén `tar.gz`.
    + Nén/giải nén `.zip`.

- Mount/Umount Command:
    + Thêm ổ cứng `sdb` ~ 5gb.
    + Kiểm tra số lượng ổ cứng.
    + Mount vào `/mnt/test`.
    + Umount `/mnt/test`.

- Symbolic Links, Hard Links Command:
    + Định nghĩa Sym Link.
    + Định nghĩa Hard Link.
    + Ví dụ về Sym Link và Hard Link.

- Ls Command:
    + Liệt kê file/thư mục.
    + Liệt kê file/thư mục và thuộc tính.
    + Show file ẩn.

- Ps Command:
    + Show tiến trình.
    + Kill tiến trình.

- Top Command:
    + Kiểm tra tài nguyên CPU.
    + Giải thích các thông số.

- Free Command:
    + Giải thích các thông số về RAM.

- Df Command:
    + Xem dung lượng disk.
    + Phân vùng `/` là gì.
