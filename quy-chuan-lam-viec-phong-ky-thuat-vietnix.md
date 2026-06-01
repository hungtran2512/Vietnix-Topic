# QUY CHUẨN LÀM VIỆC — PHÒNG KỸ THUẬT VIETNIX

Tài liệu tổng hợp các nội quy phòng kỹ thuật, áp dụng cho **toàn bộ nhân viên** (Lv1, Lv2, Lv3, R&D). Mọi vi phạm sẽ được tính vào KPI theo quy định.


---

## MỤC LỤC


1. [Nguyên tắc chung](#i-nguy%C3%AAn-t%E1%BA%AFc-chung)
2. [Giao tiếp với khách hàng](#ii-giao-ti%E1%BA%BFp-v%E1%BB%9Bi-kh%C3%A1ch-h%C3%A0ng)
3. [Quy trình xử lý Task / Ticket](#iii-quy-tr%C3%ACnh-x%E1%BB%AD-l%C3%BD-task--ticket)
4. [Xử lý sự cố & nguyên nhân gốc](#iv-x%E1%BB%AD-l%C3%BD-s%E1%BB%B1-c%E1%BB%91--nguy%C3%AAn-nh%C3%A2n-g%E1%BB%91c)
5. [Bảo mật & an toàn hệ thống](#v-b%E1%BA%A3o-m%E1%BA%ADt--an-to%C3%A0n-h%E1%BB%87-th%E1%BB%91ng)
6. [Phối hợp nội bộ](#vi-ph%E1%BB%91i-h%E1%BB%A3p-n%E1%BB%99i-b%E1%BB%99)
7. [Kỷ luật & ca trực](#vii-k%E1%BB%B7-lu%E1%BA%ADt--ca-tr%E1%BB%B1c)
8. [Lưu ý sản phẩm / dịch vụ](#viii-l%C6%B0u-%C3%BD-s%E1%BA%A3n-ph%E1%BA%A9m--d%E1%BB%8Bch-v%E1%BB%A5)
9. [Phụ lục: Danh mục lỗi tính KPI](#ph%E1%BB%A5-l%E1%BB%A5c-danh-m%E1%BB%A5c-l%E1%BB%97i-t%C3%ADnh-kpi)


---

## I. NGUYÊN TẮC CHUNG

### 1.1. Tư vấn khách hàng phải khắc phục **triệt để** (áp dụng tất cả level)

| Loại lỗi | Yêu cầu xử lý |
|----|----|
| Lỗi vận hành | Tư vấn khách cách vận hành để **tránh tái diễn** |
| Nghẽn resource | Tối ưu hoặc tư vấn nâng cấp gói |
| Lỗ hổng bảo mật | Yêu cầu cài lại máy cá nhân / VPS / Hosting, hạn chế chia sẻ mật khẩu, không dùng source từ nguồn không uy tín |

*Cần hướng dẫn khách tự làm các thao tác cơ bản khi có thể.* 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/m78EvNlW05YBkZQ)

### 1.2. Phải đọc thông báo công ty

* Không đọc thông báo trong **3 ngày liên tiếp** → Tính lỗi KPI: *"Sai quy trình làm việc - Không đọc thông báo"*.


---

## II. GIAO TIẾP VỚI KHÁCH HÀNG

### 2.1. Chuẩn mực giao tiếp

* **Nội bộ:** linh hoạt trong cách diễn đạt.
* **Với khách hàng:** **bắt buộc** chuyên nghiệp — ngôn từ trang trọng, chính xác, kiểm tra kỹ chính tả trước khi gửi.
* Mỗi nhân viên khi tiếp xúc khách hàng đều **đại diện cho hình ảnh và uy tín của công ty**.

🔗 [Nguồn](https://discord.com/channels/739709104678764545/1399599717759058002/1399599723312185415)

### 2.2. Thời gian phản hồi

| Tình huống | Yêu cầu | Vi phạm |
|----|----|----|
| Phản hồi ticket / Telegram (Lv1) | ≤ **10 phút** | Tính lỗi KPI cho **toàn bộ Lv1** trong ca trực |
| Task/Ticket xử lý quá **20 phút** | Bắt buộc reply khách báo tiến độ + hẹn thời gian dự kiến | — |
| Không nhận phản hồi từ Sale/KH sau 15 phút | **Chủ động** liên hệ lại Sale/KH | — |

🔗 [Nguồn — Reply 20p](https://discord.com/channels/739709104678764545/1399599717759058002/1404418622809571420) • [Nguồn — Tương tác 15p](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/d1jVbgWXa59ZaPQ)

### 2.3. Quy định gọi điện khách hàng

**Khi cần gọi:**

* Xin thông tin Remote Desktop / SSH / quản trị WordPress / các quản trị khác.
* Xin thông tin UltraViewer / AnyDesk.
* Xin cách/hướng dẫn kiểm tra/test sự cố.

**Khung giờ:**

* **Hạn chế gọi** trong khoảng **00:00 – 06:00**.
* **Ngoại lệ phải gọi:** khách chủ động cung cấp số; trường hợp khẩn cấp (chết dịch vụ, mất dữ liệu).

**Sau khi gọi:** bắt buộc note lại ticket, phản hồi theo mẫu.

🔗 [Nguồn — Gọi điện](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/XD4WBgBR4gL8kGo) • [Khung giờ gọi](https://discord.com/channels/739709104678764545/1399599717759058002/1406919603673763922)

### 2.4. Phản hồi khi không phát hiện lỗi như khách phản ánh

* Nếu kiểm tra thấy website nhanh / không thấy lỗi như khách mô tả:
* **Bắt buộc** quay video duyệt **tối thiểu 5 trang** trên website làm bằng chứng và gửi cùng phản hồi.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/G1B3Mg6Wb5RJmZO)

### 2.5. Khéo léo yêu cầu khách cung cấp thông tin / hình ảnh

Một số task **bắt buộc upload hình ảnh** → cần khéo léo để khách hợp tác.

**Mẫu câu tham khảo:**

> *"Dạ anh ơi, nếu được anh gửi giúp em hình ảnh đầy đủ liên quan đến lỗi mình gặp phải để bên em khoanh vùng xử lý nhanh hơn giúp mình với ạ."*

> *"Dạ anh ơi, nếu được anh gửi giúp em URL đang bị chậm để bên em khoanh vùng xử lý nhanh hơn giúp mình với ạ."* → sau đó tự check URL này.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/e942vKOz0NWBQmx)

### 2.6. Xác nhận trước khi truy cập dịch vụ KH

* Mọi thao tác cần SSH/remote/truy cập hosting cPanel → **xin phép và báo lại khách** qua kênh đang hỗ trợ (Ticket / Discord / Telegram / Livechat).
* KH không có room Telegram/Discord → **gọi điện** xác nhận nhanh / xin thông tin.
* KH có room Telegram nhưng phản hồi chậm → gọi Sale xin xác nhận / thông tin.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/Mo8V35pP25m4w0x)


---

## III. QUY TRÌNH XỬ LÝ TASK / TICKET

### 3.1. Đọc kỹ và xử lý chính xác task

* Đọc kỹ nội dung task yêu cầu, thực hiện chính xác.
* Nếu task không phù hợp nhu cầu khách:
  * **Hủy task**.
  * Hướng dẫn Lv1 tạo lại task chuẩn xác.

### 3.2. Reply ticket — bắt buộc đọc lịch sử

* Phản hồi ticket **không đọc thông tin trước đó** → tính lỗi **+1 KPI**. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/7B0wEgYQkgb2kJ3)

### 3.3. React ticket

* Ai nhận ticket → **giúp React** ticket đó. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/d1jVbgWYqN9ZaPQ)

### 3.4. Cập nhật thông tin trên Portal

**Yêu cầu:**

* Đầy đủ, rõ ràng, chính xác — đảm bảo người đọc hiểu được.
* Không update / update sai → tính lỗi KPI.

**Mô tả sự cố cần có:**

* Chi tiết lỗi (gián đoạn dịch vụ / lỗi kết nối / phản hồi chậm…).
* Log / error code (nếu có).
* Cách kiểm tra / khắc phục.

**Hướng xử lý cần có:**

* Các bước khắc phục đã thực hiện.
* Đề xuất phòng ngừa tái diễn (nếu có).
* Tài liệu đính kèm: ảnh chụp màn hình, file log, video minh họa.

### 3.5. Wait for Customer (WFC) & task treo

* Task WFC → ghi rõ **lý do hợp lý**.
* Task WFC / Open / In-progress treo quá lâu → khi vào ca **chủ động push lại** để member khác xử lý.
* Hình ảnh đính kèm trong task và livechat **phải đúng checklist**.

🔗 [Nguồn — WFC](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/qMX8pKd4rKnE7Wd) • [Nguồn — Push task](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/OABdx5ZwBNDp7Zq)

### 3.6. Theo dõi Automation Bot (Lv1)

* Trong ca trực, **chủ động kiểm tra** các task thuộc nhóm Automation Bot.
* Nếu bot chưa làm hoặc treo lâu:

  
  1. Chụp lại ảnh.
  2. Report.
  3. Thực hiện thủ công.

### 3.7. Task chuyển dữ liệu

* **Bắt buộc** xử lý chính xác và đầy đủ trước khi bàn giao.
* **Trách nhiệm kiểm tra kỹ lưỡng** trước khi bàn giao.
* Làm sai → **+1 KPI**. 🔗 [Nguồn](https://discord.com/channels/739709104678764545/1399599717759058002/1405474862620737546)

### 3.8. Task ảnh hưởng mất dữ liệu

* **Bắt buộc xác nhận với khách hàng** trước khi thực hiện. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/6Ajm7KorVNvEoyp)

### 3.9. Xử lý lỗi WordPress

* Không tìm ra nguyên nhân trong **15 phút** → **báo dev** kiểm tra.


---

## IV. XỬ LÝ SỰ CỐ & NGUYÊN NHÂN GỐC

### 4.1. Yêu cầu xử lý triệt để (đặc biệt Lv3)

* **Tất cả các lỗi cần xử lý triệt để**, đảm bảo không tái diễn do nguyên nhân chủ quan.
* **Không** dừng lại ở việc reboot nhanh mà không tìm hiểu nguyên nhân.
* Lỗi tái diễn do làm việc hời hợt, thiếu trách nhiệm → tính lỗi KPI.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/e942vKOXQgWBQmx)

### 4.2. Quy trình thao tác Stop VPS (task nâng cấp)

|    | Cách làm |
|----|----|
| ❌ **SAI** | Dùng "Stop / Shutdown / PowerOff" trực tiếp trên node |
| ✅ **ĐÚNG** | Remote Desktop / SSH vào VPS → thực hiện lệnh `poweroff` / `shutdown` |

Thao tác sai → tính lỗi *"Thao tác phát sinh kết quả không tốt"*. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/EeLVrNyYwNQOJwk)

### 4.3. Quy định về IP

**Hết IP:**

* **Không tự ý** báo cho Sales → phải có xác nhận từ Trưởng/Phó phòng Kỹ thuật.

**Trùng IP:**

* **KHÔNG** tự ý thông báo trực tiếp với khách.
* Báo ngay cho **Sale Admin** xử lý (trong giờ làm việc).
* Khi thông báo với khách, **chỉ nói câu mẫu**:

  > *"IP đang gặp lỗi route và có hiện tượng chập chờn ảnh hưởng đến dịch vụ. Nhờ khách hỗ trợ đổi IP khác để ổn định."*

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/oEm4DKP3aNGqAy3)

### 4.4. Tư vấn giải pháp dịch vụ

* **Không tự ý** tư vấn giải pháp.
* Phải có xác nhận thông tin từ **Level 3**.


---

## V. BẢO MẬT & AN TOÀN HỆ THỐNG

### 5.1. Quy tắc thao tác trên node hosting / VPS

🚫 **TUYỆT ĐỐI KHÔNG:**

* Sử dụng script tự động, hướng dẫn từ AI hoặc bất kỳ nguồn không chính thống nào trên mạng để thao tác trên node hosting và VPS.

✅ **YÊU CẦU:**

* Mọi thao tác kỹ thuật **chỉ được phép thực hiện bằng command đã hiểu rõ và nắm chắc**.

⚠️ Mọi vi phạm gây ảnh hưởng hệ thống → **xử lý nghiêm**.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/3YZ2lKqeDK1pVLx)

### 5.2. Thiết bị truy cập tài khoản công ty

* **TUYỆT ĐỐI KHÔNG** dùng máy Windows đăng nhập vào hệ thống / tài khoản công ty.
* Bị phát hiện → **xử lý kỷ luật**. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/lrwAygJGL58W6X3)

### 5.3. Bảo mật thông tin nội bộ

* **TUYỆT ĐỐI KHÔNG** cung cấp thông tin cho cá nhân **không còn làm việc** ở công ty. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/wb2aGKAnVgE4qA8)

### 5.4. Mật khẩu khi setup dịch vụ cho khách

Khi setup dịch vụ (vestacp, CyberPanel, database, WordPress…):

* Nếu khách **không yêu cầu** mật khẩu cụ thể → **bắt buộc** đặt mật khẩu random **trên 20 ký tự**.
* **Không** đặt các mật khẩu đơn giản.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/eADoJNbOnK1WG2Z)

### 5.5. Cảnh báo khách dùng mật khẩu đơn giản

* **Bắt buộc** cảnh báo / đề xuất khách đổi mật khẩu phức tạp **ngay khi phát hiện** KH dùng mật khẩu đơn giản.
* **Mục tiêu:** hạn chế việc KH bị hack / dính ransomware, và tránh mâu thuẫn/tranh chấp khi phát sinh tình trạng này.

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/ldRmoK8dGKpPaJq)

### 5.6. Unsuspend dịch vụ

* **Không tự ý** Unsuspend dịch vụ khách hàng. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/3kpb15ERmNYGAn0)

### 5.7. Phần mềm bản quyền

🚫 **TUYỆT ĐỐI KHÔNG:**

* Cài đặt, hỗ trợ cài đặt, hướng dẫn hoặc gợi ý khách hàng sử dụng phần mềm **null / crack / không bản quyền** dưới mọi hình thức.

✅ **YÊU CẦU:**

* Luôn **gợi ý khách hàng mua bản quyền Windows** khi khách hỏi các vấn đề liên quan đến Windows / license.
* Tương tự với các phần mềm khác có yêu cầu license: tư vấn khách sử dụng bản có bản quyền hợp pháp.

> **Lý do:** Phần mềm crack/null tiềm ẩn rủi ro bảo mật cao (malware, backdoor, ransomware), gây ảnh hưởng đến dịch vụ và uy tín Vietnix. Đồng thời đảm bảo tuân thủ pháp lý về bản quyền phần mềm.


---

## VI. PHỐI HỢP NỘI BỘ

### 6.1. Quy định tag Sale

| Thời gian | Cách tag |
|----|----|
| Trong giờ hành chính — kênh Sale Admin | Tag **Sale Admin** |
| Trong giờ hành chính — group sale cụ thể | Tag **tên Sale phụ trách** |
| Ngoài giờ hành chính | Tag **Sale Admin** để được hỗ trợ |

🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/ldRmoK8mngpPaJq)

### 6.2. Không chat riêng với Sale

* Khi làm việc, **không được trao đổi riêng** với Sale (chat riêng).
* Mọi thông tin trao đổi phải ở **room liên quan** để cùng xử lý.
* Bị phát hiện → xử lý. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/GV0lY5zoPN9edRz)

### 6.3. Email làm việc với VDC

* **Chỉ sử dụng duy nhất** email `tech@vietnix.vn`.
* Không dùng các mail khác. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/VRrBMNxnogW9vXD)


---

## VII. KỶ LUẬT & CA TRỰC

### 7.1. Trong giờ làm

* **Không** làm việc riêng: chơi game, stream…
* Các task sự cố phải **note hướng xử lý vào task**. 🔗 [Nguồn](https://workplace.vietnix.vn/groups/ZQxlm05GjgwpzO1/posts/XD4WBgBWe5L8kGo)

### 7.2. Check-in/out khi rời ca

Khi đi ăn / rời ca làm việc, **chat với bot Discord** theo cú pháp:

| Tình huống | Cú pháp |
|----|----|
| Khi đi ăn / rời ca | `/techoff` |
| Khi trở lại ca | `/techon` |

🔗 [Nguồn](https://discord.com/channels/739709104678764545/1399599717759058002/1443136232539422823)


---

## VIII. LƯU Ý SẢN PHẨM / DỊCH VỤ

* Các gói **Hosting SSD** và **VPS Cheap** **chưa hỗ trợ** kích hoạt license **Elementor Pro**.


---

## PHỤ LỤC: DANH MỤC LỖI TÍNH KPI

| # | Hành vi | Mức |
|----|----|----|
| 1 | Lv1 không phản hồi ticket/telegram trong 10 phút | Tính lỗi cho **toàn bộ Lv1 ca trực** |
| 2 | Phản hồi ticket không đọc thông tin trước đó | +1 KPI |
| 3 | Update sai / không update info trên Portal | +1 KPI |
| 4 | Task chuyển dữ liệu làm sai | +1 KPI |
| 5 | Lv3 không xử lý triệt để, lỗi tái diễn do thiếu trách nhiệm | Tính lỗi KPI |
| 6 | Thao tác Stop VPS sai cách (dùng nút trên node) | Tính lỗi "Thao tác phát sinh kết quả không tốt" |
| 7 | Không đọc thông báo trong 3 ngày | Tính lỗi "Sai quy trình làm việc – Không đọc thông báo" |
| 8 | Dùng script tự động / AI / nguồn lạ trên node, VPS | **Xử lý nghiêm** |
| 9 | Dùng máy Windows đăng nhập tài khoản công ty | **Xử lý kỷ luật** |
| 10 | Cung cấp thông tin cho cá nhân đã nghỉ việc | Vi phạm bảo mật |
| 11 | Chat riêng với Sale về công việc | Bị xử lý khi phát hiện |
| 12 | Tự ý báo Sales khi hết IP / thông báo khách khi trùng IP | Vi phạm quy trình |
| 13 | Tự ý Unsuspend dịch vụ | Vi phạm quy trình |
| 14 | Tự ý tư vấn giải pháp khi chưa có xác nhận Lv3 | Vi phạm quy trình |
| 15 | Cài đặt / hỗ trợ / gợi ý KH dùng phần mềm null, crack, không bản quyền | **Vi phạm nghiêm trọng** |


---

## CAM KẾT

> Mọi nhân viên phòng kỹ thuật **đã đọc, hiểu và cam kết tuân thủ** đầy đủ các quy chuẩn trên trong suốt quá trình làm việc tại Vietnix.

**Cập nhật mới nhất:** Tháng 5/2026 **Phụ trách tài liệu:** Phòng Kỹ thuật — Vietnix