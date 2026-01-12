# Shopee – Phân tích hiệu quả kinh doanh shop (Q3/2025)
Power BI Dashboard hỗ trợ quản lý đa gian hàng & tối ưu marketing

---

## 1. Tổng quan dự án
Dự án này tập trung phân tích tình hình kinh doanh của shop trên sàn thương mại điện tử Shopee trong Quý 3/2025, 
nhằm hỗ trợ chủ shop đưa ra quyết định tối ưu doanh thu và chi phí marketing.

Dashboard được thiết kế với cơ chế **Parameter động**, cho phép thay đổi mã shop và cập nhật toàn bộ dữ liệu 
chỉ với một thao tác, giúp quản lý hiệu quả nhiều gian hàng trên cùng một báo cáo.

- **Đối tượng sử dụng:** Chủ shop
- **Mục tiêu phân tích:** 
  - Đánh giá hiệu quả kinh doanh tổng thể
  - Tối ưu chi phí quảng cáo (Paid Ads)
  - Hiểu hành vi mua sắm của khách hàng

---

## 2. Công cụ & kỹ thuật sử dụng
- **Power BI:** Mô hình dữ liệu, DAX measure, dashboard tương tác
- **Power Query (M):** ETL, xử lý dữ liệu & xây dựng Parameter động
- **Excel:** Nguồn dữ liệu đầu vào
- **Canva:** Thiết kế báo cáo insight định dạng A4

---

## 3. Xử lý dữ liệu & ETL
Dữ liệu xuất từ Shopee tồn tại nhiều vấn đề về định dạng và chất lượng. 
Power Query được sử dụng để chuẩn hóa dữ liệu trước khi phân tích:

- Thiết lập **Parameter** để thay đổi mã shop linh hoạt
- Chuẩn hóa định dạng số và kiểu dữ liệu doanh thu, chi phí
- Xử lý các đơn hàng bị huỷ và giá trị bị thiếu
- Tạo bảng **Dim_Date** phục vụ phân tích theo thời gian (MoM, QoQ)

---

## 4. Dashboard phân tích
*(Chèn GIF demo tính năng đổi Parameter tại đây)*

### Các trang chính trong dashboard:
1. **Overview:** Tổng quan GMV, số đơn hàng, tỷ lệ chuyển đổi
2. **Paid Ads:** Phân tích ROAS, CIR để tối ưu ngân sách quảng cáo
3. **Campaign Day:** So sánh hiệu quả ngày thường và các ngày Mega Sale
4. **Product:** Phân loại sản phẩm chủ lực, sản phẩm hỗ trợ và sản phẩm tồn kho
5. **Buyer:** Phân tích tần suất mua và nhóm khách hàng chính

<details>
  <summary>📊 Xem hình ảnh chi tiết Dashboard</summary>

  ![Overview](link_anh_1)
  ![Paid Ads](link_anh_2)
  ![Product](link_anh_3)
</details>

---

## 5. Insight & kế hoạch hành động
Bên cạnh dashboard tương tác, dự án cung cấp báo cáo insight định dạng A4 
phục vụ họp chiến lược và ra quyết định.

- **Insight chính:**  
  - Hiệu suất quảng cáo trong các ngày Campaign cao hơn ngày thường nhưng tỷ lệ hoàn hàng tăng
  - Một số nhóm sản phẩm đóng góp lợi nhuận cao nhưng chưa được phân bổ ngân sách phù hợp

- **Kế hoạch hành động:**  
  - Điều chỉnh ngân sách cho các chiến dịch có ROAS cao
  - Tối ưu nội dung quảng cáo và chiến lược sản phẩm trong ngày Campaign

👉 [Xem báo cáo A4 chi tiết](link_canva_cua_ban)

---

## 6. Kết quả đạt được
- Giảm thời gian tổng hợp báo cáo thủ công từ 4 giờ xuống còn dưới 5 phút nhờ cơ chế Parameter động
- Xác định nhóm sản phẩm mang lại ~60% lợi nhuận để ưu tiên đầu tư marketing
