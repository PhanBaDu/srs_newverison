# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng xử lý phản hồi / khiếu nại của Admin_

## MỤC LỤC

1. [Chức năng xử lý phản hồi / khiếu nại](#1-chức-năng-xử-lý-phản-hồi--khiếu-nại)
   - 1.1 [Xem danh sách phản hồi/khiếu nại](#11-xem-danh-sách-phản-hồikhiếu-nại)
   - 1.2 [Xem chi tiết phản hồi](#12-xem-chi-tiết-phản-hồi)
   - 1.3 [Trả lời phản hồi](#13-trả-lời-phản-hồi)
   - 1.4 [Cập nhật trạng thái xử lý](#14-cập-nhật-trạng-thái-xử-lý)
   - 1.5 [Phân loại khiếu nại](#15-phân-loại-khiếu-nại)

---

## 1. CHỨC NĂNG XỬ LÝ PHẢN HỒI / KHIẾU NẠI

### 1.1 XEM DANH SÁCH PHẢN HỒI/KHIẾU NẠI

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách phản hồi/khiếu nại                         |
| ------------- | ---------------------------------------------------- |
| Description   | Hiển thị tất cả phản hồi/khiếu nại từ khách hàng     |
| Screen Access | Admin truy cập /admin/complaints hoặc menu Khiếu nại |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                     | Type       | Data                                                            | Description                  |
| ------------------------ | ---------- | --------------------------------------------------------------- | ---------------------------- |
| **Bộ lọc trạng thái**    | Select     | Mới / Đang xử lý / Đã giải quyết / Đóng                         | Lọc theo trạng thái          |
| **Bộ lọc phân loại**     | Select     | Sản phẩm / Dịch vụ / Giao hàng / Thanh toán / Khác              | Lọc theo loại khiếu nại      |
| **Ô tìm kiếm**           | Input      | Tìm theo mã, tên khách, số điện thoại                           | Tìm nhanh                    |
| **Bảng danh sách**       | Table      | Mã, Khách, Loại, Trạng thái, Ngày tạo, Cập nhật, Mức ưu tiên... | Danh sách phản hồi/khiếu nại |
| **Badge mức độ ưu tiên** | Badge      | Thấp / Trung bình / Cao                                         | Nhấn mạnh độ ưu tiên         |
| **Nút xem chi tiết**     | Button     | Xem chi tiết                                                    | Mở chi tiết phản hồi         |
| **Phân trang**           | Pagination | Điều hướng trang                                                | Điều hướng danh sách         |

#### 1.1.3 Hành động và xử lý:

| Action Name                     | Description                                                                             | Success                                                     | Failure                                               |
| ------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------- |
| **Hiển thị danh sách phản hồi** | Hiển thị danh sách kèm lọc/tìm kiếm và phân trang, sắp xếp theo thời gian tạo/cập nhật. | Danh sách chính xác, lọc/tìm kiếm mượt, phân trang ổn định. | Không tải được dữ liệu, lọc/tìm kiếm không hoạt động. |

### 1.2 XEM CHI TIẾT PHẢN HỒI

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết phản hồi/khiếu nại     |
| ------------- | ------------------------------- |
| Description   | Xem nội dung và thông tin khách |
| Screen Access | Từ danh sách, chọn Xem chi tiết |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                        | Type     | Data                                           | Description         |
| --------------------------- | -------- | ---------------------------------------------- | ------------------- |
| **Thông tin khách hàng**    | Card     | Họ tên, SĐT, Email, Mã đơn (nếu có)            | Hồ sơ khách         |
| **Chi tiết phản hồi**       | Card     | Chủ đề, Nội dung, Ảnh đính kèm                 | Nội dung khiếu nại  |
| **Trạng thái**              | Badge    | Mới / Đang xử lý / Đã giải quyết / Đóng        | Trạng thái hiện tại |
| **Phân loại**               | Badge    | Sản phẩm / Dịch vụ / Giao hàng / Thanh toán... | Loại khiếu nại      |
| **Cam kết thời gian trả lời** | Text   | Cam kết trả lời trong X ngày                    | Hiển thị cam kết    |
| **Progress bar tiến độ**   | Progress | Tiến độ xử lý                                   | Hiển thị tiến độ    |
| **Lịch sử xử lý**           | Timeline | Mốc thời gian, Người xử lý, Hành động, Ghi chú | Lịch sử tiến trình  |
| **Nút trả lời**             | Button   | Trả lời                                        | Mở form trả lời     |
| **Nút cập nhật trạng thái** | Button   | Cập nhật trạng thái                            | Mở modal cập nhật   |

#### 1.2.3 Hành động và xử lý:

| Action Name               | Description                                                     | Success                                       | Failure                      |
| ------------------------- | --------------------------------------------------------------- | --------------------------------------------- | ---------------------------- |
| **Xem chi tiết phản hồi** | Hiển thị đầy đủ nội dung, phân loại, trạng thái, lịch sử xử lý. Hệ thống hiển thị cam kết thời gian trả lời (ví dụ: "Cam kết trả lời trong 3 ngày") và progress bar tiến độ xử lý để user biết bao giờ được phản hồi. | Thông tin đầy đủ, rõ ràng, trích xuất ảnh OK. Cam kết thời gian và progress bar hiển thị chính xác. | Thiếu nội dung, lỗi ảnh/tệp. Cam kết thời gian và progress bar không hiển thị. |

### 1.3 TRẢ LỜI PHẢN HỒI

#### 1.3.1 Thông tin màn hình:

| Screen        | Trả lời phản hồi/khiếu nại            |
| ------------- | ------------------------------------- |
| Description   | Gửi phản hồi đến khách qua email/push |
| Screen Access | Từ chi tiết phản hồi                  |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                             | Description        |
| -------------------- | ------ | -------------------------------- | ------------------ |
| **Form trả lời**     | Form   | Tiêu đề, Nội dung, File đính kèm | Soạn phản hồi      |
| **Kênh gửi**         | Select | Email / Push                     | Chọn kênh gửi      |
| **Nút gửi phản hồi** | Button | Gửi phản hồi                     | Gửi đến khách hàng |

#### 1.3.3 Hành động và xử lý:

| Action Name                | Description                                                  | Success                                 | Failure                            |
| -------------------------- | ------------------------------------------------------------ | --------------------------------------- | ---------------------------------- |
| **Gửi phản hồi cho khách** | Gửi phản hồi kèm nội dung/đính kèm, lưu bản sao vào lịch sử. Hệ thống cập nhật progress bar tiến độ xử lý và thông báo cho user về thời gian cam kết trả lời. | Khách nhận được, lịch sử lưu chính xác. Progress bar được cập nhật. | Không gửi được, không lưu lịch sử. Progress bar không được cập nhật. |

### 1.4 CẬP NHẬT TRẠNG THÁI XỬ LÝ

#### 1.4.1 Thông tin màn hình:

| Screen        | Cập nhật trạng thái xử lý                                |
| ------------- | -------------------------------------------------------- |
| Description   | Chuyển trạng thái: Mới → Đang xử lý → Đã giải quyết/Đóng |
| Screen Access | Từ chi tiết phản hồi                                     |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                      | Type  | Data                                      | Description           |
| ------------------------- | ----- | ----------------------------------------- | --------------------- |
| **Modal trạng thái**      | Modal | Trạng thái mới, Người xử lý, Ghi chú      | Xác nhận thay đổi     |
| **Mẫu phản hồi kết thúc** | Form  | Lý do kết thúc, Hướng dẫn/đền bù (nếu có) | Chuẩn hóa đóng ticket |

#### 1.4.3 Hành động và xử lý:

| Action Name             | Description                                      | Success                                     | Failure                         |
| ----------------------- | ------------------------------------------------ | ------------------------------------------- | ------------------------------- |
| **Cập nhật trạng thái** | Lưu trạng thái mới và thêm bản ghi vào Timeline. | Trạng thái cập nhật chuẩn, Timeline đầy đủ. | Không lưu được, Timeline thiếu. |

### 1.5 PHÂN LOẠI KHIẾU NẠI

#### 1.5.1 Thông tin màn hình:

| Screen        | Phân loại khiếu nại                  |
| ------------- | ------------------------------------ |
| Description   | Gắn nhãn/nhóm để phân tích & báo cáo |
| Screen Access | Từ chi tiết phản hồi                 |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                                        | Description        |
| --------------------- | ------ | ------------------------------------------- | ------------------ |
| **Chọn phân loại**    | Select | Sản phẩm / Dịch vụ / Giao hàng / Thanh toán | Gắn nhãn           |
| **Nút lưu phân loại** | Button | Lưu                                         | Lưu loại khiếu nại |

#### 1.5.3 Hành động và xử lý:

| Action Name       | Description                                               | Success                                 | Failure                   |
| ----------------- | --------------------------------------------------------- | --------------------------------------- | ------------------------- |
| **Lưu phân loại** | Lưu loại khiếu nại để phục vụ thống kê & tối ưu quy trình | Loại lưu thành công, xuất báo cáo được. | Không lưu được phân loại. |
