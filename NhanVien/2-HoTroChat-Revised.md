# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng quản lý hỗ trợ / liên hệ của Admin_

## MỤC LỤC

1. [Chức năng quản lý hỗ trợ / liên hệ](#1-chức-năng-quản-lý-hỗ-trợ--liên-hệ)
   - 1.1 [Hiển thị danh sách tin nhắn](#11-hiển-thị-danh-sách-tin-nhắn)
   - 1.2 [Xem chi tiết tin nhắn](#12-xem-chi-tiết-tin-nhắn)
   - 1.3 [Chat hỗ trợ khách hàng](#13-chat-hỗ-trợ-khách-hàng)
   - 1.4 [Quản lý SLA và phân công](#14-quản-lý-sla-và-phân-công)

---

## 1. CHỨC NĂNG QUẢN LÝ HỖ TRỢ / LIÊN HỆ

### 1.1 HIỂN THỊ DANH SÁCH TIN NHẮN

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách tin nhắn hỗ trợ                      |
| ------------- | ---------------------------------------------- |
| Description   | Hiển thị các hội thoại hỗ trợ với khách hàng   |
| Screen Access | Admin truy cập /admin/support hoặc menu Hỗ trợ |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type       | Data                                               | Description                   |
| ----------------------- | ---------- | -------------------------------------------------- | ----------------------------- |
| **Bộ lọc trạng thái**   | Select     | Tất cả / Mới / Đang xử lý / Đã giải quyết / Đóng   | Lọc theo trạng thái ticket    |
| **Bộ lọc ưu tiên**      | Select     | Thấp / Trung bình / Cao                            | Lọc theo mức độ ưu tiên       |
| **Ô tìm kiếm**          | Input      | Tìm theo mã, tên khách, số điện thoại              | Tìm nhanh                     |
| **Danh sách hội thoại** | List       | Avatar, Tên khách, Chủ đề, Trạng thái, Cập nhật... | Danh sách các cuộc trò chuyện |
| **Badge chưa đọc**      | Badge      | Số lượng tin nhắn chưa đọc                         | Thông báo số lượng chưa đọc   |
| **Nút xem chi tiết**    | Button     | Xem chi tiết                                       | Mở chi tiết hội thoại         |
| **Phân trang**          | Pagination | Điều hướng trang                                   | Điều hướng danh sách          |

#### 1.1.3 Hành động và xử lý:

| Action Name                     | Description                                                          | Success                                                   | Failure                                               |
| ------------------------------- | -------------------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------- |
| **Hiển thị danh sách tin nhắn** | Hiển thị hội thoại kèm lọc/tìm kiếm, sắp xếp theo cập nhật mới nhất. | Danh sách đầy đủ, chính xác, tương tác lọc/tìm kiếm mượt. | Không tải được dữ liệu, lọc/tìm kiếm không hoạt động. |
| **Đánh dấu đã đọc**             | Đánh dấu hội thoại hoặc tin nhắn là đã đọc.                          | Badge giảm chính xác, trạng thái cập nhật real-time.      | Trạng thái không lưu, badge sai lệch.                 |

### 1.2 XEM CHI TIẾT TIN NHẮN

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết hội thoại hỗ trợ                     |
| ------------- | --------------------------------------------- |
| Description   | Xem nội dung, lịch sử trao đổi, file đính kèm |
| Screen Access | Từ danh sách tin nhắn, chọn Xem chi tiết      |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type      | Data                                         | Description                      |
| --------------------- | --------- | -------------------------------------------- | -------------------------------- |
| **Thông tin khách**   | Card      | Tên, SĐT, Email, Mã khách                    | Hồ sơ khách hàng                 |
| **Luồng hội thoại**   | Container | Tin nhắn khách / Tin nhắn hỗ trợ / Thời gian | Khu vực hiển thị cuộc trò chuyện |
| **Lịch sử chat**      | List      | Danh sách tin nhắn đã lưu                    | Hiển thị lịch sử chat đã lưu     |
| **Tìm kiếm trong chat** | Input  | Tìm kiếm trong lịch sử chat                  | Ô tìm kiếm tin nhắn trong chat   |
| **Nút export chat**   | Button    | Xuất lịch sử chat                            | Nút để export lịch sử chat       |
| **Trạng thái đã đọc** | Badge     | Đã đọc / Chưa đọc                            | Hiển thị trạng thái đọc          |
| **File đính kèm**     | List      | Danh sách file                               | Tải xuống/xem trước              |
| **Nút trả lời**       | Button    | Trả lời                                      | Mở ô nhập nội dung               |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                       | Success                                               | Failure                                              |
| -------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------- |
| **Xem nội dung hội thoại** | Hiển thị đầy đủ lịch sử, hỗ trợ tải thêm theo trang, cuộn vô hạn. Tất cả tin nhắn được lưu trữ trong lịch sử chat để có thể xem lại và export. | Nội dung hiển thị đủ, cuộn mượt, tải trang chính xác. Lịch sử chat được lưu trữ đầy đủ. | Mất tin nhắn, thứ tự sai, không tải thêm. Lịch sử chat không được lưu trữ.            |
| **Tải/xem file đính kèm**  | Xem/tải các file khách gửi (ảnh, tài liệu).                       | File mở/tải thành công, an toàn.                      | Không mở/tải được, cảnh báo an toàn không hoạt động. |
| **Xem lịch sử chat**       | Cho phép admin xem lại lịch sử chat đã lưu trữ, bao gồm tất cả tin nhắn đã gửi và nhận. Hệ thống hỗ trợ tìm kiếm trong lịch sử chat để tìm tin nhắn cụ thể. | Lịch sử chat được hiển thị đầy đủ và chính xác. Tìm kiếm trong chat hoạt động tốt. | Lịch sử chat không được hiển thị đầy đủ hoặc không chính xác. Tìm kiếm trong chat không hoạt động. |
| **Export lịch sử chat**    | Cho phép admin xuất lịch sử chat ra file (CSV, TXT, PDF) để lưu trữ hoặc báo cáo. Hệ thống hỗ trợ export toàn bộ hoặc theo khoảng thời gian. | Lịch sử chat được export thành công. File được tạo đúng định dạng. | Không thể export lịch sử chat. File được tạo không đúng định dạng. |

### 1.3 CHAT HỖ TRỢ KHÁCH HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Chat hỗ trợ khách hàng                 |
| ------------- | -------------------------------------- |
| Description   | Nhắn tin real-time giữa admin và khách |
| Screen Access | Từ chi tiết hội thoại                  |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                   | Type     | Data                                   | Description       |
| ---------------------- | -------- | -------------------------------------- | ----------------- |
| **Ô nhập tin nhắn**    | Textarea | Nhập nội dung                          | Soạn tin nhắn     |
| **Nút gửi**            | Button   | Gửi                                    | Gửi tin nhắn      |
| **Trạng thái kết nối** | Badge    | Đang kết nối / Đã kết nối              | Trạng thái socket |
| **Gợi ý câu trả lời**  | Dropdown | Câu trả lời nhanh (template)           | Tăng tốc phản hồi |
| **Gắn thẻ nội bộ**     | Input    | Tag nội bộ (VD: vận chuyển, hoàn tiền) | Phân loại chủ đề  |

#### 1.3.3 Hành động và xử lý:

| Action Name                | Description                                                     | Success                                                  | Failure                                  |
| -------------------------- | --------------------------------------------------------------- | -------------------------------------------------------- | ---------------------------------------- |
| **Gửi tin nhắn real-time** | Gửi/nhận tin nhắn tức thời, hiển thị dấu đã đọc, thời gian gửi. Tất cả tin nhắn được lưu trữ trong lịch sử chat để có thể xem lại và export sau. | Tin nhắn đến ngay, trạng thái đã đọc cập nhật chính xác. Tin nhắn được lưu vào lịch sử. | Mất kết nối, tin nhắn trễ/không đồng bộ. Tin nhắn không được lưu vào lịch sử. |
| **Dùng câu trả lời nhanh** | Chèn template trả lời để rút ngắn thời gian phản hồi.           | Template chèn đúng chỗ, nội dung chuẩn hóa.              | Chèn sai, định dạng lỗi.                 |

### 1.4 QUẢN LÝ SLA VÀ PHÂN CÔNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Quản lý SLA & phân công                      |
| ------------- | -------------------------------------------- |
| Description   | Đặt mục tiêu phản hồi và giao việc cho agent |
| Screen Access | Từ module Hỗ trợ                             |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                                       | Description        |
| -------------------- | ------ | ------------------------------------------ | ------------------ |
| **Thiết lập SLA**    | Form   | Mục tiêu phản hồi (phút), giải quyết (giờ) | Thiết lập mục tiêu |
| **Phân công**        | Select | Agent phụ trách, Nhóm hỗ trợ               | Giao việc          |
| **Nút lưu cấu hình** | Button | Lưu cấu hình                               | Lưu thay đổi       |
| **Báo cáo tuân thủ** | Card   | Tỉ lệ đáp ứng SLA, tỉ lệ quá hạn           | Theo dõi hiệu suất |

#### 1.4.3 Hành động và xử lý:

| Action Name         | Description                                            | Success                                               | Failure                                             |
| ------------------- | ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------------- |
| **Thiết lập SLA**   | Lưu mục tiêu phản hồi/giải quyết để theo dõi tuân thủ. | SLA lưu thành công, áp dụng ngay.                     | Không lưu được, không áp dụng vào báo cáo.          |
| **Phân công agent** | Giao ticket/hội thoại cho agent hoặc nhóm phù hợp.     | Ticket hiển thị người phụ trách, thông báo đến agent. | Không gán được người phụ trách, thông báo thất bại. |
