# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng bảo mật của Admin_

## MỤC LỤC

1. [Chức năng bảo mật](#1-chức-năng-bảo-mật)
   - 1.1 [Khôi phục mật khẩu](#11-khôi-phục-mật-khẩu)
   - 1.2 [Lịch sử đăng nhập](#12-lịch-sử-đăng-nhập)
   - 1.3 [Xóa phiên đăng nhập](#13-xóa-phiên-đăng-nhập)

---

## 1. CHỨC NĂNG BẢO MẬT

### 1.1 KHÔI PHỤC MẬT KHẨU

#### 1.1.1 Thông tin màn hình:

| Screen        | Khôi phục mật khẩu Admin         |
| ------------- | -------------------------------- |
| Description   | Gửi link khôi phục qua email/SMS |
| Screen Access | Từ trang đăng nhập Admin         |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                  | Description                 |
| ------------------------ | ------ | ------------------------------------- | --------------------------- |
| **Ô nhập email**         | Input  | Email                                 | Nhập email khôi phục        |
| **Nút gửi link**         | Button | Gửi link khôi phục                    | Gửi link reset              |
| **Thông báo thành công** | Toast  | Email khôi phục mật khẩu đã được gửi! | Phản hồi khi gửi thành công |

#### 1.1.3 Hành động và xử lý:

| Action Name            | Description                                              | Success                                        | Failure                                           |
| ---------------------- | -------------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------- |
| **Gửi link khôi phục** | Tạo token, gửi email chứa link reset 1 lần, có thời hạn. | Email gửi thành công, token hợp lệ, hoạt động. | Email không tồn tại, lỗi gửi, token không hợp lệ. |

### 1.2 LỊCH SỬ ĐĂNG NHẬP

#### 1.2.1 Thông tin màn hình:

| Screen        | Lịch sử đăng nhập Admin       |
| ------------- | ----------------------------- |
| Description   | Xem các lần đăng nhập gần đây |
| Screen Access | /admin/security/login-history |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                                                         | Description         |
| --------------------- | ------ | ------------------------------------------------------------ | ------------------- |
| **Bộ lọc thời gian**  | Select | Tất cả / Tuần này / Tháng này / 3 tháng gần đây              | Lọc theo thời gian  |
| **Bộ lọc thiết bị**   | Select | Tất cả / Desktop / Mobile / Tablet                           | Lọc theo thiết bị   |
| **Bộ lọc trạng thái** | Select | Tất cả / Thành công / Thất bại                               | Lọc theo trạng thái |
| **Bảng lịch sử**      | Table  | Thời gian, IP, Thiết bị, OS, Trình duyệt, Vị trí, Trạng thái | Danh sách đăng nhập |

#### 1.2.3 Hành động và xử lý:

| Action Name                    | Description                             | Success                          | Failure              |
| ------------------------------ | --------------------------------------- | -------------------------------- | -------------------- |
| **Hiển thị lịch sử đăng nhập** | Hiển thị lịch sử kèm lọc theo tiêu chí. Hệ thống tự động phát hiện và đánh dấu đăng nhập lạ (từ thiết bị mới hoặc vị trí mới) và gửi thông báo qua email/SMS để cảnh báo admin. | Dữ liệu đúng, lọc hoạt động tốt. Đăng nhập lạ được phát hiện và thông báo kịp thời. | Lỗi tải dữ liệu/lọc. Đăng nhập lạ không được phát hiện hoặc không gửi thông báo. |

### 1.3 XÓA PHIÊN ĐĂNG NHẬP

#### 1.3.1 Thông tin màn hình:

| Screen        | Quản lý phiên đăng nhập Admin         |
| ------------- | ------------------------------------- |
| Description   | Xóa/đăng xuất các phiên trên thiết bị |
| Screen Access | /admin/security/sessions              |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                                  | Description               |
| ------------------------ | ------ | ----------------------------------------------------- | ------------------------- |
| **Phiên hiện tại**       | Card   | Thiết bị, Thời gian, IP, Vị trí                       | Thông tin phiên hiện tại  |
| **Danh sách phiên khác** | List   | Thiết bị, OS, Trình duyệt, Hoạt động cuối, Trạng thái | Các phiên còn lại         |
| **Nút xóa phiên**        | Button | Xóa phiên                                             | Đăng xuất thiết bị        |
| **Nút đăng xuất tất cả** | Button | Đăng xuất tất cả thiết bị                             | Vô hiệu hóa toàn bộ phiên |

#### 1.3.3 Hành động và xử lý:

| Action Name                   | Description                                  | Success                                          | Failure                                 |
| ----------------------------- | -------------------------------------------- | ------------------------------------------------ | --------------------------------------- |
| **Xóa phiên đăng nhập**       | Xóa 1 phiên đã chọn, lưu log bảo mật. Hệ thống tự động đăng xuất phiên khi hết hạn (timeout) và cảnh báo trước khi hết hạn.        | Phiên bị xoá, thiết bị đăng xuất. Auto logout hoạt động đúng khi hết hạn.                | Không xoá được, thiết bị vẫn hoạt động. Auto logout không hoạt động. |
| **Đăng xuất tất cả thiết bị** | Vô hiệu hóa tất cả phiên trừ phiên hiện tại. Hệ thống tự động đăng xuất các phiên hết hạn và cảnh báo trước khi hết hạn. | Tất cả phiên bị vô hiệu hóa, thông báo được gửi. Auto logout hoạt động đúng. | Một số phiên không bị vô hiệu hóa. Auto logout không hoạt động.      |
