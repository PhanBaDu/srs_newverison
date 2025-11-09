# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Báo cáo và thống kê của Admin_

## MỤC LỤC

1. [Báo cáo và thống kê](#1-báo-cáo-và-thống-kê)
   - 1.1 [Doanh thu](#11-doanh-thu)
   - 1.2 [Sản phẩm bán chạy](#12-sản-phẩm-bán-chạy)
   - 1.3 [Thống kê khách hàng](#13-thống-kê-khách-hàng)
   - 1.4 [Báo cáo tồn kho](#14-báo-cáo-tồn-kho)
   - 1.5 [Báo cáo lợi nhuận](#15-báo-cáo-lợi-nhuận)
   - 1.6 [Báo cáo nâng cao](#16-báo-cáo-nâng-cao)

---

## 1. BÁO CÁO VÀ THỐNG KÊ

### 1.1 DOANH THU

#### 1.1.1 Thông tin màn hình:

| Screen        | Báo cáo doanh thu                      |
| ------------- | -------------------------------------- |
| Description   | Theo dõi doanh thu theo ngày/tháng/năm |
| Screen Access | Admin truy cập /admin/reports/revenue  |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                                                 | Description              |
| --------------------- | ------ | ---------------------------------------------------- | ------------------------ |
| **Bộ lọc thời gian**  | Select | Hôm nay / Tuần này / Tháng này / Năm nay / Tùy chỉnh | Khoảng thời gian báo cáo |
| **Bộ lọc kênh**       | Select | COD / Banking / E-wallet                             | Lọc theo kênh thanh toán |
| **Biểu đồ doanh thu** | Chart  | Line/Bar                                             | Xu hướng doanh thu       |
| **Tổng doanh thu**    | Card   | Số tiền VNĐ                                          | Tổng hợp                 |
| **Bảng chi tiết**     | Table  | Ngày, Số đơn, Doanh thu, Trung bình đơn, Tỷ lệ hoàn  | Chi tiết theo ngày       |

#### 1.1.3 Hành động và xử lý:

| Action Name             | Description                                            | Success                               | Failure                         |
| ----------------------- | ------------------------------------------------------ | ------------------------------------- | ------------------------------- |
| **Tính toán doanh thu** | Tổng hợp theo bộ lọc, hiển thị biểu đồ và số liệu thẻ. | Số liệu chính xác, biểu đồ trực quan. | Sai số, không tải được dữ liệu. |

### 1.2 SẢN PHẨM BÁN CHẠY

#### 1.2.1 Thông tin màn hình:

| Screen        | Sản phẩm bán chạy            |
| ------------- | ---------------------------- |
| Description   | Top sản phẩm có doanh số cao |
| Screen Access | /admin/reports/top-products  |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                                  | Description        |
| -------------------- | ------ | ------------------------------------- | ------------------ |
| **Khoảng thời gian** | Select | Hôm nay / Tuần / Tháng / Năm          | Lọc theo thời gian |
| **Bảng xếp hạng**    | Table  | Sản phẩm, SL bán, Doanh thu, Tỷ trọng | Top theo doanh số  |
| **Biểu đồ tỉ trọng** | Chart  | Pie/Donut                             | Tỷ trọng doanh thu |

#### 1.2.3 Hành động và xử lý:

| Action Name           | Description                       | Success                       | Failure                      |
| --------------------- | --------------------------------- | ----------------------------- | ---------------------------- |
| **Tính top bán chạy** | Xếp hạng theo doanh thu/số lượng. | Danh sách xếp hạng chính xác. | Sai xếp hạng, thiếu dữ liệu. |

### 1.3 THỐNG KÊ KHÁCH HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Thống kê khách hàng               |
| ------------- | --------------------------------- |
| Description   | Khách mới, VIP, tần suất mua hàng |
| Screen Access | /admin/reports/customers          |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                                    | Description         |
| -------------------- | ------ | --------------------------------------- | ------------------- |
| **Bộ lọc thời gian** | Select | Tuần / Tháng / Quý / Năm                | Lọc theo thời gian  |
| **Chỉ số tổng quan** | Cards  | Khách mới, Khách VIP, AOV, tần suất mua | KPI chính           |
| **Bảng khách hàng**  | Table  | Tên, Email, Số đơn, Tổng chi tiêu, Hạng | Chi tiết theo khách |

#### 1.3.3 Hành động và xử lý:

| Action Name             | Description                             | Success                                | Failure                  |
| ----------------------- | --------------------------------------- | -------------------------------------- | ------------------------ |
| **Tính KPI khách hàng** | Tính toán chỉ số tổng quan theo bộ lọc. | KPI hiển thị đúng, lọc hoạt động mượt. | Sai số hoặc lỗi dữ liệu. |

### 1.4 BÁO CÁO TỒN KHO

#### 1.4.1 Thông tin màn hình:

| Screen        | Báo cáo tồn kho                       |
| ------------- | ------------------------------------- |
| Description   | Tình trạng hàng hóa, sản phẩm sắp hết |
| Screen Access | /admin/reports/inventory              |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                | Type   | Data                                            | Description             |
| ------------------- | ------ | ----------------------------------------------- | ----------------------- |
| **Ngưỡng cảnh báo** | Input  | Số lượng sắp hết (ví dụ <= 5)                   | Cài đặt ngưỡng cảnh báo |
| **Bảng tồn kho**    | Table  | Sản phẩm, SKU, Tồn hiện tại, Ngưỡng, Trạng thái | Danh sách tồn kho       |
| **Xuất báo cáo**    | Button | CSV/XLSX                                        | Xuất dữ liệu            |
| **Chọn trường export** | Checkbox | Chọn các trường cần export                    | Tùy chọn trường export  |
| **Bộ lọc nâng cao**  | Form   | Bộ lọc theo nhiều tiêu chí                    | Lọc dữ liệu trước export |
| **Lưu mẫu export**   | Button | Lưu mẫu export                                 | Lưu cấu hình export     |

#### 1.4.3 Hành động và xử lý:

| Action Name                | Description                                   | Success                          | Failure              |
| -------------------------- | --------------------------------------------- | -------------------------------- | -------------------- |
| **Phát hiện sắp hết hàng** | Liệt kê sản phẩm dưới ngưỡng, gợi ý nhập hàng | Danh sách đúng, cảnh báo rõ ràng | Bỏ sót/cảnh báo sai. |
| **Xuất dữ liệu tùy chỉnh** | Cho phép admin chọn các trường cần export, áp dụng bộ lọc nâng cao, và lưu mẫu export để sử dụng lại. Hỗ trợ export CSV/XLSX với các trường được chọn. | Dữ liệu được export thành công với các trường đã chọn. Mẫu export được lưu và có thể sử dụng lại. | Không thể export dữ liệu hoặc thiếu trường. Mẫu export không được lưu. |

### 1.5 BÁO CÁO LỢI NHUẬN

#### 1.5.1 Thông tin màn hình:

| Screen        | Báo cáo lợi nhuận              |
| ------------- | ------------------------------ |
| Description   | Tính chi phí - doanh thu = lãi |
| Screen Access | /admin/reports/profit          |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                                   | Description        |
| -------------------- | ------ | -------------------------------------- | ------------------ |
| **Bộ lọc thời gian** | Select | Tháng / Quý / Năm                      | Khoảng thời gian   |
| **Bảng chi tiết**    | Table  | Doanh thu, Giá vốn, Chi phí, Lợi nhuận | Báo cáo tài chính  |
| **Biểu đồ**          | Chart  | Bar/Line                               | Xu hướng lợi nhuận |

#### 1.5.3 Hành động và xử lý:

| Action Name        | Description                                | Success                          | Failure                |
| ------------------ | ------------------------------------------ | -------------------------------- | ---------------------- |
| **Tính lợi nhuận** | Tổng hợp doanh thu và chi phí để tính lãi. | Số liệu đúng, trình bày rõ ràng. | Sai số, thiếu chi phí. |

### 1.6 BÁO CÁO NÂNG CAO

#### 1.6.1 Thông tin màn hình:

| Screen        | Báo cáo nâng cao                           |
| ------------- | ------------------------------------------ |
| Description   | Phân tích hiệu quả khuyến mãi, hành vi mua |
| Screen Access | /admin/reports/advanced                    |

#### 1.6.2 Chi tiết thành phần màn hình:

| Item                     | Type | Data                                          | Description         |
| ------------------------ | ---- | --------------------------------------------- | ------------------- |
| **Phân tích khuyến mãi** | Card | Tỉ lệ sử dụng mã, Doanh thu do khuyến mãi     | Hiệu quả chiến dịch |
| **Phân tích hành vi**    | Card | Tần suất mua, Tỷ lệ quay lại, Phễu chuyển đổi | Hành vi khách hàng  |

#### 1.6.3 Hành động và xử lý:

| Action Name               | Description                             | Success                            | Failure                      |
| ------------------------- | --------------------------------------- | ---------------------------------- | ---------------------------- |
| **Sinh báo cáo nâng cao** | Tổng hợp đa nguồn, hiển thị theo widget | Chỉ số hiển thị đúng, export được. | Lỗi truy vấn, thiếu dữ liệu. |
