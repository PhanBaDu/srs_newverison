# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng hỗ trợ của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng hỗ trợ](#1-chức-năng-hỗ-trợ)
   - 1.1 [Chat trực tiếp](#11-chat-trực-tiếp) - **ĐÃ SỬA**
   - 1.2 [Tạo yêu cầu hỗ trợ](#12-tạo-yêu-cầu-hỗ-trợ)
   - 1.3 [Xem lịch sử hỗ trợ](#13-xem-lịch-sử-hỗ-trợ)

---

## 1. CHỨC NĂNG HỖ TRỢ

### 1.1 CHAT TRỰC TIẾP - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Chat trực tiếp với nhân viên hỗ trợ                                                      |
| ------------- | --------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng chat trực tiếp với nhân viên hỗ trợ để được giải đáp thắc mắc       |
| Screen Access | Người dùng chọn **Hỗ trợ** từ menu chính và chọn tab **Chat trực tiếp**                 |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Khung chat**            | Chat Window  | Hiển thị tin nhắn                       | Khung hiển thị cuộc trò chuyện                 |
| **Tin nhắn người dùng**   | Message      | Tin nhắn của người dùng                 | Tin nhắn được gửi bởi người dùng               |
| **Tin nhắn hỗ trợ**       | Message      | Tin nhắn của nhân viên hỗ trợ           | Tin nhắn được gửi bởi nhân viên hỗ trợ         |
| **Input tin nhắn**        | Input        | Nhập tin nhắn của bạn...                | Ô nhập tin nhắn                                 |
| **Nút gửi**               | Button       | Send                                    | Nút để gửi tin nhắn                            |
| **Thông báo timeout**     | Alert        | Chat đã tự động đóng do không hoạt động | **MỚI**: Cảnh báo khi chat bị timeout          |
| **Nút bắt đầu lại**       | Button       | Bắt đầu chat lại                        | **MỚI**: Nút để bắt đầu chat lại sau timeout   |
| **Thông báo thời gian**   | Text         | Chat sẽ tự động đóng sau 10 phút        | **MỚI**: Hiển thị thời gian timeout           |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Gửi tin nhắn**         | Cho phép người dùng gửi tin nhắn đến nhân viên hỗ trợ. Hệ thống sẽ hiển thị tin nhắn trong khung chat và gửi đến nhân viên hỗ trợ.                                                                                                          | Tin nhắn được gửi thành công và hiển thị trong khung chat.                                | Không thể gửi tin nhắn do lỗi kết nối hoặc hệ thống.                                       |
| **Nhận phản hồi**        | Hệ thống tự động nhận phản hồi từ nhân viên hỗ trợ và hiển thị trong khung chat.                                                                                                                          | Phản hồi được nhận và hiển thị thành công trong khung chat.                               | Không thể nhận phản hồi do lỗi kết nối hoặc nhân viên hỗ trợ không phản hồi.               |
| **Auto-close timeout**   | **MỚI**: Hệ thống tự động đóng chat sau 10 phút không có hoạt động (không có tin nhắn mới từ cả người dùng và nhân viên hỗ trợ). Khi chat bị đóng, người dùng sẽ nhận thông báo và có thể bắt đầu chat lại.                                  | Chat được tự động đóng sau 10 phút không hoạt động. Người dùng được thông báo rõ ràng.    | Lỗi khi đóng chat tự động. Người dùng không được thông báo.                                |
| **Reset timeout**        | **MỚI**: Mỗi khi có hoạt động (gửi tin nhắn hoặc nhận tin nhắn), hệ thống sẽ reset lại thời gian timeout về 10 phút. Điều này đảm bảo chat chỉ đóng khi thực sự không có hoạt động trong 10 phút liên tục.                                  | Timeout được reset thành công mỗi khi có hoạt động.                                      | Lỗi khi reset timeout. Chat bị đóng sớm hơn dự kiến.                                       |
| **Bắt đầu chat lại**     | **MỚI**: Sau khi chat bị đóng do timeout, người dùng có thể click nút "Bắt đầu chat lại" để mở lại chat và tiếp tục trò chuyện. Hệ thống sẽ reset timeout và cho phép chat hoạt động bình thường.                                          | Chat được mở lại thành công. Timeout được reset. Người dùng có thể tiếp tục trò chuyện.  | Không thể mở lại chat. Lỗi khi reset timeout.                                             |
| **Lưu lịch sử chat**     | **MỚI**: Hệ thống tự động lưu lịch sử chat để người dùng có thể xem lại sau này. Lịch sử được lưu ngay cả khi chat bị đóng do timeout.                                                                                                    | Lịch sử chat được lưu thành công và có thể xem lại.                                       | Không thể lưu lịch sử chat. Dữ liệu bị mất.                                               |

#### 1.1.4 Timeout Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Timeout Duration** | 10 phút không có hoạt động (không có tin nhắn mới)                        | Tự động đóng chat và thông báo người dùng |
| **Reset on Activity** | Mỗi khi có tin nhắn mới (từ người dùng hoặc nhân viên), reset timeout về 10 phút | Đảm bảo chat chỉ đóng khi thực sự không hoạt động |
| **Auto-assign Agent** | Nếu nhân viên hỗ trợ không phản hồi trong 10 phút, tự động chuyển sang nhân viên khác | Đảm bảo người dùng luôn được hỗ trợ |

---

### 1.2 TẠO YÊU CẦU HỖ TRỢ

#### 1.2.1 Thông tin màn hình:

| Screen        | Tạo yêu cầu hỗ trợ                                                      |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Cho phép người dùng tạo yêu cầu hỗ trợ để được giải đáp thắc mắc        |
| Screen Access | Người dùng chọn **Hỗ trợ** từ menu chính và chọn tab **Yêu cầu hỗ trợ** |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Form tạo yêu cầu**  | Form         | Tiêu đề, mô tả, danh mục | Form để tạo yêu cầu hỗ trợ           |
| **Nút gửi yêu cầu**   | Button       | Gửi yêu cầu             | Nút để gửi yêu cầu hỗ trợ            |

---

### 1.3 XEM LỊCH SỬ HỖ TRỢ

#### 1.3.1 Thông tin màn hình:

| Screen        | Lịch sử hỗ trợ                                                      |
| ------------- | ------------------------------------------------------------------ |
| Description   | Hiển thị danh sách các yêu cầu hỗ trợ đã gửi và trạng thái xử lý   |
| Screen Access | Hiển thị trong tab **Yêu cầu hỗ trợ**                              |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách yêu cầu** | List         | Yêu cầu + trạng thái    | Hiển thị các yêu cầu hỗ trợ          |
| **Bộ lọc**            | Filter       | Tất cả, Mở, Đã giải quyết | Lọc yêu cầu theo trạng thái          |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Auto-close timeout**: Chat tự động đóng sau 10 phút không có hoạt động
2. **Reset timeout**: Tự động reset timeout mỗi khi có tin nhắn mới
3. **Lưu lịch sử**: Tự động lưu lịch sử chat để xem lại sau này
4. **Thông báo rõ ràng**: Hiển thị thông báo khi chat bị đóng và hướng dẫn bắt đầu lại
5. **Auto-assign agent**: Tự động chuyển sang nhân viên khác nếu nhân viên hiện tại không phản hồi

