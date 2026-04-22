* Lỗi trong ảnh xác nhận rằng file .sql đang tải lên vượt quá giới hạn cấu hình của PHP trên server.
* Dưới đây là cách xử lý triệt để:
<img width="1532" height="367" alt="image" src="https://github.com/user-attachments/assets/a7d25697-5cf2-44c6-b75d-a705c6b5ef62" />

1. Phân tích nguyên nhân 
- Vấn đề: Mặc định, các thông số upload_max_filesize và post_max_size trong PHP thường được để ở mức thấp (2M đến 8M)
- Nguyên nhân: Khi file database của WordPress hay Laravel nặng hơn mức này, phpMyAdmin sẽ không thể nhận dữ liệu và trả về lỗi "No data was received"

2. Cách khắc phục
* Vào menu `PHP`, chọn version php
<img width="255" height="184" alt="image" src="https://github.com/user-attachments/assets/9231c446-6538-495d-bc46-343ad1808208" />

* Điều chỉnh dung lượng lớn hơn dung lượng database source và click `Save Changes`
<img width="1150" height="184" alt="image" src="https://github.com/user-attachments/assets/e0e5595a-1706-4a37-bf6a-73c6e310dae6" />
<img width="569" height="98" alt="image" src="https://github.com/user-attachments/assets/2527b090-97b4-4d24-a8f1-726f31a1acbd" />

