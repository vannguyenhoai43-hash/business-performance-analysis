# Phân tích Hiệu quả Kinh doanh Cửa hàng theo Quý

Đọc bằng: [English](README.md) | **Tiếng Việt**

---

## Tổng quan dự án

**Chỉ tăng trưởng doanh thu là chưa đủ để kết luận một cửa hàng đang vận hành tốt.** Một shop có thể tăng doanh số nhưng vẫn làm thất thoát hiệu quả quảng cáo, phụ thuộc quá nhiều vào một vài sản phẩm hoặc kênh bán, đồng thời chưa chuyển đổi được người mua mới thành khách hàng quay lại.

Dự án này xây dựng một **dashboard phân tích hiệu quả kinh doanh theo quý** phục vụ review shop e-commerce, được thiết kế để đánh giá hiệu suất trên các khía cạnh **doanh thu, quảng cáo, chiến dịch, sản phẩm, kênh bán và hành vi khách hàng**.

Bằng việc sử dụng **Power BI**, **Power Query** và **SQL**, tôi xây dựng một quy trình có thể tái sử dụng để hợp nhất các file dữ liệu tháng rời rạc, chuẩn bị logic cohort, và cho phép cùng một cấu trúc dashboard có thể refresh cho **nhiều shop trong cùng một mô hình báo cáo** thông qua **parameter mỗi shop**. Mục tiêu không chỉ là trực quan hóa hiệu suất, mà còn giúp quá trình review kinh doanh định kỳ trở nên nhanh hơn, nhất quán hơn và có tính hành động hơn.

---

## Bộ dữ liệu

Dashboard hợp nhất các file Excel theo tháng trong **một kỳ báo cáo theo quý (Jul–Sep 2025)** thành một mô hình báo cáo có thể tái sử dụng.

Các nhóm dữ liệu nguồn chính bao gồm:

- **Dữ liệu vận hành hằng ngày**
- **Dữ liệu quảng cáo trả phí**
- **Dữ liệu cấp độ sản phẩm**
- **Dữ liệu cấp độ khách hàng**

Các cấp độ phân tích chính bao gồm:

- **cấp độ hiệu suất theo ngày**
- **cấp độ sản phẩm**
- **cấp độ khách hàng**
- **cấp độ ngày chiến dịch**

Mô hình báo cáo được thiết kế để **tái sử dụng cho nhiều shop** thông qua **parameter**, nhờ đó cùng một cấu trúc dashboard có thể được refresh cho các shop khác nhau mà không cần xây lại báo cáo riêng.

---

## Những gì tôi đã xây dựng

- Xây dựng **dashboard Power BI** bao phủ các khía cạnh: sức khỏe kinh doanh, quảng cáo, chiến dịch, sản phẩm và người mua
- Xây dựng **parameter mã shop có thể tái sử dụng** để cùng một cấu trúc dashboard có thể refresh cho nhiều shop khác nhau mà không cần làm lại từng báo cáo
- Sử dụng **Power Query** để gộp các file theo tháng có cùng schema vào một mô hình báo cáo thống nhất
- Sử dụng **SQL** để chuẩn bị **bảng cohort mua đầu tiên** phục vụ trực quan hóa theo hướng retention
- Thiết kế phần **tóm tắt insight** ngắn gọn để phục vụ review kinh doanh và lập kế hoạch hành động

---

## Logic phân tích

Dashboard được tổ chức xoay quanh 5 lăng kính phân tích:

### 1. Sức khỏe kinh doanh
Sử dụng **số đơn hàng, doanh thu, chi tiêu quảng cáo, AOV và tỷ lệ chuyển đổi** để đánh giá liệu tăng trưởng topline có đi kèm với hiệu quả tốt hơn hay không.

![Overview](image/dashboard_Overview.png)

### 2. Hiệu quả quảng cáo
Sử dụng **ROAS, chi phí trên mỗi đơn hàng, mức suy giảm theo từng bước của phễu chuyển đổi và mức đóng góp quảng cáo theo sản phẩm** để xác định phần nào của ngân sách quảng cáo đang chuyển đổi tốt và phần nào đang bị thất thoát.

![Paid Ads](image/dashboard_PaidAds.png)

### 3. Hiệu quả chiến dịch
So sánh **Mini Spike và Spike Day** dựa trên **đơn hàng, doanh thu, chi tiêu quảng cáo, AOV và ROAS** để đánh giá khung chiến dịch nào mang lại hiệu quả cao hơn.

![Campaign Day](image/dashboard_Campaign.png)

### 4. Đóng góp của sản phẩm và kênh
Đo lường **mức độ tập trung doanh thu, ROAS theo sản phẩm và cơ cấu kênh** nhằm xác định các **tổ hợp sản phẩm - kênh mang lại hiệu quả cao nhất**.

![Product](image/dashboard_Product.png)

### 5. Mô hình giữ chân khách hàng
Sử dụng **tăng trưởng người mua, tần suất mua hàng và retention theo cohort** để đánh giá liệu tăng trưởng chủ yếu đến từ **thu hút người mua mới** hay được hỗ trợ bởi **hành vi mua lại**.

![Buyer](image/dashboard_Buyer.png)

---

## Logic chuẩn bị dữ liệu

Một thách thức lớn của dự án này là biến các file dữ liệu tháng rời rạc thành một mô hình có thể hỗ trợ review kinh doanh định kỳ.

![project_flow](image/project_flow.png)

### Power Query
Tôi sử dụng **Power Query (M)** để:

- gộp file qua nhiều tháng
- căn chỉnh các bộ dữ liệu có cùng cấu trúc
- chuẩn hóa định dạng cột
- loại bỏ các dòng dữ liệu không hợp lệ
- tạo một lớp dữ liệu báo cáo thống nhất có thể tái sử dụng giữa các chức năng

Điều này cho phép kết hợp các file tháng rời rạc vào cùng một mô hình dashboard, thay vì phải duy trì các file riêng cho từng tháng hoặc từng mảng chức năng.

### Thiết kế parameter động
Tôi xây dựng **parameter mã shop** để cùng một dashboard có thể tái sử dụng cho nhiều shop.

Thay vì phải xây lại báo cáo riêng hoặc thay file nguồn thủ công, người dùng chỉ cần thay đổi mã shop một lần rồi refresh toàn bộ dataset trong cùng một cấu trúc phân tích. Cách làm này biến dashboard từ một báo cáo dùng một lần thành một **mẫu báo cáo có khả năng mở rộng**.

![Demo parameter](image/Gif_DB.gif)

### SQL cho phân tích cohort

Tôi sử dụng **SQL** để chuẩn bị **bảng cohort mua đầu tiên** phục vụ trực quan hóa theo hướng retention, giúp theo dõi hành vi mua lại theo thời gian dễ hơn thay vì chỉ nhìn vào số lượng người mua tổng hợp.

[SQL_Cohort](sql/cohort_analysis)
---

## Insight mẫu:

- Trong quý, shop ghi nhận **10,32K đơn hàng**, **60,33K USD doanh thu** và **tỷ lệ chuyển đổi 7,15%**, trong khi **AOV đạt 5,84 USD**. Doanh thu tăng **+3,65% QoQ** và AOV tăng **+10,65%**, trong khi chi tiêu quảng cáo gần như đi ngang ở mức **5,59K USD (-0,18%)**.

- Hiệu quả quảng cáo chưa đồng đều. **ROAS đạt 9,01**, nhưng phễu chuyển đổi cho thấy điểm rơi rõ nhất nằm ở bước **Click → Add to Cart (-77,70%)**, tiếp theo là **Add to Cart → Orders (-67,93%)**. Điều này cho thấy vấn đề chính không nằm ở việc tạo traffic, mà nằm ở chất lượng chuyển đổi ở các bước sâu hơn trong phễu.

- **Livestream** là kênh quảng cáo trả phí có hiệu quả tốt nhất. ROAS của kênh này tăng từ **7,84 trong tháng 7** lên **8,79 trong tháng 9**, vượt **Video** ở mức **7,06** trong tháng 9. Ở cấp độ sản phẩm, **Sunshade Cover** đạt **ROAS cao nhất là 13,32**, trở thành ưu tiên rõ ràng nhất về tổ hợp sản phẩm - kênh hiệu quả cao.

- **Spike Day** vượt trội hơn **Mini Spike** với **ROAS 9,43** so với **8,69**, dù tỷ trọng chi tiêu quảng cáo thấp hơn (**39,07%** so với **60,93%**). Điều này cho thấy Spike Day tạo ra mức hoàn vốn trên mỗi đồng ngân sách tốt hơn và là khung thời điểm nên được ưu tiên tập trung ngân sách.

- Tăng trưởng vẫn chủ yếu dựa vào thu hút khách hàng mới. Shop có **9,54K người mua**, trong đó **8,59K là người mua mới**, trong khi **tần suất mua hàng trung bình chỉ đạt 1,08**. Retention theo cohort cũng suy giảm khá nhanh, với retention trung vị giảm từ **5,49% ở tuần 2** xuống **4,09% ở tuần 6**.

- Giá trị khách hàng có mức độ tập trung cao. **Người mua nam** đóng góp **80,55% doanh thu** và **75,82% số đơn hàng**, trong khi **top 5 thị trường** đóng góp **87,91% doanh thu được theo dõi**, và riêng **TP. Hồ Chí Minh đóng góp 43,7%**.

- Đóng góp của sản phẩm và lợi nhuận cũng tập trung cao. **7 sản phẩm hàng đầu tạo ra 80% doanh thu**, và một nhóm sản phẩm đóng góp **hơn 60% tổng lợi nhuận**.

> **Kết luận chính:** shop vẫn đang tăng trưởng, nhưng chất lượng tăng trưởng chưa đồng đều. Những cơ hội lớn nhất nằm ở việc cải thiện chuyển đổi ở phần sâu của phễu, mở rộng các tổ hợp livestream/sản phẩm có ROAS cao, và giảm phụ thuộc vào việc thu hút khách hàng mới bằng cách củng cố hành vi mua lại.

---

## Hành động đề xuất

Dựa trên các tín hiệu từ dashboard, những hành động chính được đề xuất gồm:

- phân bổ thêm ngân sách cho **Spike Day**, khi **ROAS đạt 9,43** so với **8,69** ở Mini Spike
- ưu tiên **Livestream** và các sản phẩm có ROAS cao như **Sunshade Cover (ROAS 13,32)**
- tập trung xử lý điểm nghẽn **Click → Add to Cart**, nơi mức suy giảm của phễu đạt **-77,70%**
- tăng cường hoạt động sau mua hàng, khi **8,59K / 9,54K người mua là khách hàng mới** và tần suất mua hàng trung bình chỉ ở mức **1,08**
- tập trung đẩy chuyển đổi và sản phẩm vào nhóm khách hàng - thị trường hiệu quả nhất, đặc biệt là **người mua nam** và các thị trường trọng điểm như **TP. Hồ Chí Minh, Đà Nẵng, Đồng Nai và Hải Phòng**

👉 [Xem báo cáo mẫu chi tiết](https://www.canva.com/design/DAG9s3TrI1E/cRN25avmiY0nkDxe0fObDw/view?utm_content=DAG9s3TrI1E&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h3d8a1d75ec#1)
<details>
  <summary>📊 Hình ảnh báo cáo </summary>

 <!-- PAGE BÌA -->
<p align="center">
  <img src="image/pagebia.png" width="70%">
</p>

<!-- ROW 1 -->
<p align="center">
  <img src="image/page1.png" width="23%">
  <img src="image/page2.png" width="23%">
  <img src="image/page3.png" width="23%">
  <img src="image/page4.png" width="23%">
</p>

<!-- ROW 2 -->
<p align="center">
  <img src="image/page5.png" width="23%">
  <img src="image/page6.png" width="23%">
  <img src="image/page7.png" width="23%">
  <img src="image/page8.png" width="23%">
</p>

<!-- ROW 3 -->
<p align="center">
  <img src="image/page9.png" width="23%">
  <img src="image/page10.png" width="23%">
</p>

</details>

---

## Phạm vi và hạn chế

Dự án này được thiết kế cho mục tiêu **phân tích kinh doanh và review hiệu suất định kỳ**, không nhằm phục vụ dự báo hay kiểm định quan hệ nhân quả.

Điểm mạnh của dự án nằm ở khả năng xác định **mẫu hình vận động, điểm nghẽn, rủi ro tập trung và ưu tiên hành động** từ dữ liệu quý về shop, quảng cáo, sản phẩm và khách hàng. Phân tích cohort được đưa vào để hỗ trợ đọc hành vi mua lại, nhưng các kết luận về retention dài hạn vẫn bị giới hạn bởi độ dài của cửa sổ dữ liệu lịch sử hiện có.

---

## Đầu ra bàn giao

- **Dashboard Power BI** gồm 5 trang phân tích
- **Thiết lập parameter động** để refresh cho nhiều shop
- **Logic cohort bằng SQL** để trực quan hóa hành vi mua lại
- **Báo cáo tóm tắt insight** phục vụ review kinh doanh

---

## Kết quả

- Giảm thời gian làm báo cáo thủ công từ **~4 giờ xuống dưới 10 phút** nhờ cơ chế parameter động
- Xây dựng cấu trúc báo cáo có thể tái sử dụng và refresh cho **nhiều shop** mà không cần xây lại dashboard riêng
- Xác định một nhóm sản phẩm đóng góp khoảng **60% tổng lợi nhuận**, qua đó hỗ trợ tập trung đầu tư marketing hiệu quả hơn
