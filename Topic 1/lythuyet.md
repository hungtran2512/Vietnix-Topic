# Chuyên đề lý thuết
I. CÁC SẢN PHẨM HẠ TẦNG CƠ BẢN
  - 1. Shared Hosting
Không gian lưu trữ được chia nhỏ trên một máy chủ vật lý nhằm mục đích xuất bản website lên internet.
Ưu và nhược: Chi phí thấp, dễ sử dụng, phù hợp cho người mới bắt đầu. Tuy nhiên, tài nguyên được chia sẻ với nhiều người dùng khác trên cùng máy chủ.
  - 2. Dedicated Hosting
Doanh nghiệp thuê trọn gói một máy chủ vật lý với quyền sở hữu toàn bộ tài nguyên phần cứng
Ưu và nhược: hiệu suất tối đa, toàn quyền kiểm soát (tùy chỉnh sâu vào hệ điều hành, cài đặt phần mềm đặc thù), an ninh cao (loại bỏ rủi ro mã độc) phù hợp với các trang thương mại điện tử lớn, hệ thống doanh nghiệp, website có lượng truy cập lớn. Tuy nhiên, chi phí đắt đỏ (thuê và bảo trì phần cứng), cần chuyên môn (đội ngũ quản trị hệ thống am hiểu kỹ thuật để vận hành và xử lý sự cố)
  - 3. VPS (Virtual Private Server)
Máy chủ riêng ảo được tạo ra bằng công nghệ ảo hóa, chia một máy chủ vật lý thành nhiều môi trường độc lập.
Ưu và nhược: Có tài nguyên riêng (CPU, RAM) và quyền quản trị cao nhất (Root). Hiệu suất ổn định và bảo mật cao hơn Hosting. Nhưng đòi hỏi kiến thức kỹ thuật nhất định.
  - 4. Cloud Hosting
Công nghệ dựa trên điện toán đám mây, dữ liệu website được lưu trữ phân tán trên 1 cụm nhiều máy chủ kết nối với nhau.
Ưu và nhược: time hoạt động tối đa (1 máy chủ khác sẽ lập tức thay thế cho máy chủ gặp sự cố) -> website không bị gián đoạn; khả năng mở rộng (tự tăng/giảm tài nguyên theo lượng truy cập thực tế) -> website hoạt động mượt mà. Phù hợp website có truy cập biến động cao, các ứng dụng SaaS và dự án yêu cầu độ sẵn sàng cao. Tuy nhiên đòi hỏi phải có kiến thức kỹ thuật cao và chịu được chi phí đắt đỏ để vận hành.

II. ĐỊNH DANH VÀ KẾT NỐI MẠNG
  - 5. Địa chỉ IP (IP Address)
Là dãy số định danh duy nhất cho mỗi thiết bị khi kết nối vào internet (ví dụ: 192.168.1.1).
Vai trò: Giúp các thiết bị nhận diện và giao tiếp với nhau trong môi trường mạng.
  - 6. Domain (Tên miền)
Là địa chỉ định danh thay thế cho dãy số IP khó nhớ (ví dụ: vietnix.vn).
Vai trò: Giúp người dùng dễ dàng truy cập website thông qua các tên gọi có ý nghĩa.
  - 7. Whois
Là một giao thức tra cứu thông tin công khai về chủ sở hữu tên miền.
Vai trò: Kiểm tra trạng thái đăng ký, ngày hết hạn và thông tin liên hệ của một Domain.
  - 8. DNS (Domain Name System)
Là hệ thống phân giải tên miền, đóng vai trò như một cuốn danh bạ của internet.
Vai trò: Chuyển đổi tên miền (ngôn ngữ người dùng) sang địa chỉ IP (ngôn ngữ máy tính).

III. THÔNG SỐ KỸ THUẬT VÀ VẬN HÀNH
| Thông số | Khái niệm | Ý chính |
| :--- | :--- | :--- |
| Datacenter | Trung tâm dữ liệu | Nơi tập trung máy chủ, hệ thống mạng và lưu trữ với tiêu chuẩn an toàn cao. |
| CPU | Bộ vi xử lý trung tâm |Đóng vai trò "não bộ", xử lý mọi tác vụ và câu lệnh của hệ thống. |
| RAM | Bộ nhớ truy cập ngẫu nhiên | Lưu trữ dữ liệu tạm thời để CPU xử lý, ảnh hưởng trực tiếp đến tốc độ đa nhiệm. |

IV. CÁC LOẠI BẢNG ĐIỀU KHIỂN (CONTROL PANEL)
| Control Panel | Đặc điểm nổi bật | Ứng dụng tiêu biểu |
| DirectAdmin | Nhẹ, cực kỳ ổn định, tốc độ xử lý nhanh. | Quản lý hosting chuyên nghiệp cho cá nhân và đại lý. |
| aaPanel | Miễn phí, mã nguồn mở, giao diện đồ họa hiện đại. |Quản lý nhanh các module như Nginx, Docker, Python với 1-click. |
| CyberPanel | Tích hợp OpenLiteSpeed cho tốc độ vượt trội. | Tối ưu hóa hiệu suất cho các website WordPress (LSCache). |

V. TÓM TẮT LẠI MỐI QUAN HỆ TRONG HỆ THỐNG
Để một dịch vụ trực tuyến vận hành hoàn chỉnh, cần có:

Hạ tầng: Thuê Shared Hosting/VPS/Dedicated Hosting/Cloud Hosting đặt tại Datacenter (vd: VNPT IDC).
Định danh: Đăng ký Domain và cấu hình DNS để trỏ về IP của máy chủ.
Quản trị: Sử dụng Control Panel để vận hành website và các ứng dụng một cách trực quan.

