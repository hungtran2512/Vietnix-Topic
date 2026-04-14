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
  - Dùng để kết nối và điều khiển máy chủ từ xa an toàn qua giao thức mã hóa. Lệnh này cho phép quản lý hệ thống, chuyển tệp và thực thi các câu lệnh trên máy chủ từ xa một cách bảo 
  - Kết nối bằng password: phương thức cơ bản sử dụng định dạng `user@hostname`
    + Execute: `ssh username@192.168.1.10`
    + Hệ thống yêu cầu mật khẩu của `username` tại máy chủ `192.168.1.10`. Lần đầu kết nối sẽ có thông báo xác nhận (key fingerprint) -> nhấn `yes` để tiếp tục
  - Kết nối bằng key: phương thức bảo mật cao hơn, không cần mật khẩu mỗi lần đăng nhập
    + Tạo cặp khóa: `ssh-keygen -t rsa`
    + Copy khóa lên server: `ssh-copy-id username@192.168.1.10`
    + Execute lệnh kết nối `ssh -i ~/.ssh/id_rsa username@192.168.1.10`
    + `-i` chỉ định đường dẫn đến file private key -> server kiểm tra private key có khớp với public key trong `~/.ssh/id_rsa` không
  - Kết nối bằng port custom: thay đổi port mặc định để bảo mật hơn (tránh brute-force)
    + Execute lệnh: `ssh -p 2222 username@192.168.1.10`
    + `-p 2222` chỉ định port cụ thể của dịch vụ SSH mà server đang lắng nghe

## - SCP Command: 
  - Dùng để sao chép tệp và thư mục an toàn giữa máy cục bộ và máy chủ từ xa hoặc giữa hai máy chủ qua mạng, sử dụng giao thức SSH để bảo mật. Cú pháp cơ bản là `scp [lựa chọn] [nguồn] [đích]`, hỗ trợ truyền file nhanh chóng, mã hóa dữ liệu.
  - Copy 1 file:
    + Sao chép file từ máy cục bộ lên máy chủ từ xa:
      `scp /path/to/local/file.txt username@remote_host:/path/to/remote/dir/`
    + Sao chép file từ máy chủ từ xa về máy cục bộ:
      `scp username@remote_host:/path/to/remote/file.txt /path/to/local/dir/`
  - Copy 1 folder:
    + Sao chép thư mục (bao gồm tất cả file bên trong):
      `scp -r /path/to/local/dir/ username@remote_host:/path/to/remote/dir/`
      
## - Rsync Command:
  - Dùng để đồng bộ và sao lưu tệp/thư mục cục bộ hoặc từ xa một cách nhanh chóng. Nó chỉ chuyển đổi các phần khác biệt giúp tiết kiệm băng thông và thời gian. Cú pháp cơ bản là `rsync [options] source destination`
  - Copy file:
    + Sao chép tệp tin (Local):
      `rsync -v /path/to/source_file /path/to/destination`
  - Copy folder.
    + Sao chép/Đồng bộ thư mục (bao gồm thư mục con - đệ quy):
      `rsync -av /path/to/source_folder/ /path/to/destination_folder/`
  - `rsync incremental`:
      `rsync -av --update /source/ /destination/`
    + Tùy chọn -a (archive) kết hợp -v (verbose) và --update đảm bảo chỉ sao chép các tệp mới hơn hoặc chưa có ở đích.

## - Cat Command:
  - Dùng để xem, tạo, nối và ghi nội dung tệp tin nhanh chóng ngay trên terminal
  - Xem nội dung 1 file:
    + Cú pháp: `cat filename.txt`
    <img width="402" height="74" alt="image" src="https://github.com/user-attachments/assets/62b94e3a-2026-418c-9766-860ccc108613" />

  - Xem dòng thứ `<n>` trong file:
    + Cú pháp: `sed -n '2p' filename.txt`
  <img width="473" height="51" alt="image" src="https://github.com/user-attachments/assets/2d79b80a-88b9-45a9-9dfa-20e91e5e62a9" />

  - Ghi nhiều dòng vào 1 file bằng EOF.
    + Cú pháp: `cat <<EOF > filename.txt` để bắt đầu, khi muốn kết thúc ghi -> gõ `EOF`
  <img width="482" height="163" alt="image" src="https://github.com/user-attachments/assets/eb80d990-cade-4af0-8c46-2792e59a37cf" />

## - Echo Command:
  - Chèn thêm 1 dòng vào cuối file.
    + Cú pháp: `echo "text..." >> file.txt`
    <img width="562" height="363" alt="image" src="https://github.com/user-attachments/assets/a19e532f-cac1-41fa-9433-1cd647a78793" />

  - Overwrite nội dung file:
    + Cú pháp: `echo "text..." > file.txt`
    <img width="560" height="270" alt="image" src="https://github.com/user-attachments/assets/6e4ebd06-6c8e-4313-8ec9-cecdf234f560" />

## - Tail/Head Command:
  - Sự khác biệt giữa `tail` và `head`: tail dùng để xem các dòng cuối file còn head dùng để xem các dòng đầu file
    + Cú pháp: `head/tail -n [số dòng muốn xem] file.txt` 
  <img width="956" height="251" alt="image" src="https://github.com/user-attachments/assets/5a72e6c1-b7f3-4654-808e-e9f26d843dd9" />

  - Sự khác biệt giữa `tail` và `tailf`:
    + `tail -f`: mở file và theo dõi trực tiếp nếu nội file thay đổi. Sẽ gây tốn tài nguyên
    + `tailf`: được tối ưu hóa để theo dõi file log

## - Sed Command:
  - Find and replace string trong file: `sed -i 's/text cũ/text mới/g' file.txt`
    + `s`: dùng để thay thế từ đầu tiên tìm thấy trên mỗi dòng
    + `g`: dùng để thay thế tất cả cụm từ khớp tìm thấy trên cùng một dòng

## - Traceroute/Tracert Command:
  <img width="953" height="340" alt="image" src="https://github.com/user-attachments/assets/e783f64a-a2d5-4e1a-b1e1-6275253a15ab" />
  + Target: ang truy vấn đến IP 14.225.253.240.
  + 30 hops max: Giới hạn tối đa 30 trạm trung chuyển. Nếu quá 30 trạm mà chưa tới đích, lệnh sẽ dừng.
  + 60 byte packets: Kích thước mỗi gói tin thăm dò là 60 byte.
      
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
