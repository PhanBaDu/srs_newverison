# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng hỗ trợ chat của Nhân viên (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng hỗ trợ chat](#1-chức-năng-hỗ-trợ-chat)
   - 1.1 [Xem chi tiết chat](#11-xem-chi-tiết-chat) - **ĐÃ SỬA**
   - 1.2 [Chuyển tiếp / Escalate chat](#12-chuyển-tiếp--escalate-chat) - **MỚI**
   - 1.3 [Xử lý error states](#13-xử-lý-error-states) - **MỚI**
   - 1.4 [Danh sách chat](#14-danh-sách-chat)

---

## 1. CHỨC NĂNG HỖ TRỢ CHAT

### 1.1 XEM CHI TIẾT CHAT - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Chi tiết chat hỗ trợ                                                      |
| ------------- | ------------------------------------------------------------------------- |
| Description   | Hiển thị thông tin chi tiết của cuộc chat hỗ trợ với khách hàng           |
| Screen Access | Nhân viên click **Xem** từ danh sách chat hỗ trợ                          |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Thông tin khách hàng** | Card       | Tên, email, SĐT, hạng...                | Hiển thị thông tin khách hàng                  |
| **Cuộc hội thoại**    | Card         | Lịch sử tin nhắn                        | Hiển thị cuộc trò chuyện                       |
| **Ghi chú & Ưu tiên** | Card         | Ghi chú nội bộ, độ ưu tiên              | Card để quản lý ghi chú và ưu tiên             |
| **Nút hành động**     | Button Group | Trả lời, Đánh dấu hoàn thành, Chuyển tiếp, Đóng chat | Các nút để thao tác với chat                   |

---

### 1.2 CHUYỂN TIẾP / ESCALATE CHAT - **MỚI**

#### 1.2.1 Thông tin màn hình:

| Screen        | Chuyển tiếp chat hỗ trợ                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên chuyển tiếp chat đến nhân viên khác hoặc cấp trên để xử lý |
| Screen Access | Nhân viên click nút **Chuyển tiếp / Escalate** từ trang chi tiết chat        |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Dialog chuyển tiếp**    | Dialog       | Chuyển tiếp chat hỗ trợ                 | **MỚI**: Dialog để chọn người nhận và lý do    |
| **Select người nhận**     | Select       | Quản lý, Nhân viên B, Admin, Bộ phận Kỹ thuật... | **MỚI**: Dropdown chọn người/bộ phận nhận      |
| **Textarea lý do**        | Textarea     | Nhập lý do chuyển tiếp *                | **MỚI**: Bắt buộc nhập lý do                   |
| **Nút xác nhận**          | Button       | Xác nhận chuyển tiếp                    | **MỚI**: Nút để xác nhận chuyển tiếp           |
| **Loading state**         | Text         | Đang chuyển tiếp...                     | **MỚI**: Hiển thị khi đang xử lý               |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Chuyển tiếp chat**     | Cho phép nhân viên chuyển tiếp chat đến nhân viên khác hoặc cấp trên. Hệ thống sẽ yêu cầu chọn người nhận và nhập lý do trước khi chuyển tiếp.                                                                                              | Chat được chuyển tiếp thành công. Thông báo xác nhận hiển thị.                            | Không chọn người nhận. Không nhập lý do. Lỗi khi chuyển tiếp.                              |
| **Validation người nhận** | **MỚI**: Hệ thống yêu cầu nhân viên phải chọn người nhận hoặc bộ phận để chuyển tiếp. Nếu không chọn, hệ thống sẽ từ chối và hiển thị thông báo lỗi.                                                                                      | Người nhận được chọn thành công. Cho phép chuyển tiếp.                                    | Không chọn người nhận. Hiển thị: "Vui lòng chọn nhân viên để chuyển tiếp".                 |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu nhân viên phải nhập lý do chuyển tiếp (tối thiểu 10 ký tự). Nếu không nhập hoặc quá ngắn, hệ thống sẽ từ chối.                                                                                                    | Lý do được validate thành công. Cho phép chuyển tiếp.                                     | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị: "Vui lòng nhập lý do chuyển tiếp".  |
| **Ghi nhận lịch sử**     | **MỚI**: Mỗi khi chat được chuyển tiếp, hệ thống tự động ghi nhận vào lịch sử: người chuyển, người nhận, thời gian, lý do.                                                                                                                  | Lịch sử chuyển tiếp được ghi nhận thành công.                                              | Không thể ghi nhận lịch sử. Thông tin lịch sử không đầy đủ.                                |
| **Thông báo người nhận** | **MỚI**: Sau khi chuyển tiếp thành công, hệ thống tự động thông báo cho người nhận về chat mới được chuyển tiếp.                                                                                                                            | Người nhận được thông báo thành công.                                                      | Không thể thông báo cho người nhận.                                                         |

#### 1.2.4 Escalate Options (MỚI):

| Option              | Description                                    |
| ------------------- | ---------------------------------------------- |
| **Quản lý / Supervisor** | Chuyển đến quản lý để xử lý vấn đề phức tạp    |
| **Nhân viên khác**  | Chuyển đến nhân viên khác có chuyên môn phù hợp |
| **Admin**           | Chuyển đến admin cho vấn đề cần quyền cao      |
| **Bộ phận Kỹ thuật** | Chuyển đến bộ phận kỹ thuật cho vấn đề kỹ thuật |

---

### 1.3 XỬ LÝ ERROR STATES - **MỚI**

#### 1.3.1 Thông tin màn hình:

| Screen        | Error states trong chat hỗ trợ                                                      |
| ------------- | ----------------------------------------------------------------------------------- |
| Description   | Hiển thị và xử lý các lỗi có thể xảy ra trong quá trình hỗ trợ chat                  |
| Screen Access | Tự động hiển thị khi có lỗi xảy ra                                                 |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Alert lỗi**             | Alert        | Lỗi: [chi tiết lỗi]                    | **MỚI**: Hiển thị thông báo lỗi cụ thể         |
| **Icon lỗi**              | Icon         | AlertCircle                             | **MỚI**: Icon đại diện cho lỗi                 |
| **Thông báo lỗi**         | Text         | Chi tiết lỗi và hướng dẫn xử lý         | **MỚI**: Mô tả lỗi và cách khắc phục           |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Hiển thị error state** | Khi có lỗi xảy ra (network, timeout, server, permission), hệ thống tự động hiển thị error state với thông báo lỗi cụ thể và hướng dẫn xử lý.                                                                                              | Error state được hiển thị thành công với thông báo rõ ràng.                               | Không thể hiển thị error state. Thông báo lỗi không rõ ràng.                               |
| **Xử lý lỗi network**    | **MỚI**: Khi có lỗi network (không thể kết nối đến server), hệ thống hiển thị: "Không thể kết nối đến server. Vui lòng kiểm tra kết nối mạng."                                                                                            | Thông báo lỗi network được hiển thị rõ ràng. Người dùng biết cách khắc phục.              | Thông báo lỗi không rõ ràng. Người dùng không biết cách khắc phục.                         |
| **Xử lý lỗi timeout**    | **MỚI**: Khi có lỗi timeout (yêu cầu bị timeout), hệ thống hiển thị: "Yêu cầu bị timeout. Vui lòng thử lại sau."                                                                                                                              | Thông báo lỗi timeout được hiển thị rõ ràng.                                                | Thông báo lỗi không rõ ràng.                                                               |
| **Xử lý lỗi server**     | **MỚI**: Khi có lỗi server (lỗi từ phía server), hệ thống hiển thị: "Lỗi server. Vui lòng liên hệ quản trị viên."                                                                                                                         | Thông báo lỗi server được hiển thị rõ ràng. Người dùng biết cần liên hệ admin.            | Thông báo lỗi không rõ ràng.                                                               |
| **Xử lý lỗi permission** | **MỚI**: Khi có lỗi permission (không có quyền thực hiện hành động), hệ thống hiển thị: "Bạn không có quyền thực hiện hành động này."                                                                                                      | Thông báo lỗi permission được hiển thị rõ ràng.                                           | Thông báo lỗi không rõ ràng.                                                               |

#### 1.3.4 Error Types (MỚI):

| Error Type          | Message                                                                 | Handling                                    |
| ------------------- | ----------------------------------------------------------------------- | ------------------------------------------- |
| **Network Error**   | "Không thể kết nối đến server. Vui lòng kiểm tra kết nối mạng."         | Hiển thị alert, cho phép retry             |
| **Timeout Error**   | "Yêu cầu bị timeout. Vui lòng thử lại sau."                             | Hiển thị alert, cho phép retry             |
| **Server Error**    | "Lỗi server. Vui lòng liên hệ quản trị viên."                           | Hiển thị alert, ghi log                     |
| **Permission Error** | "Bạn không có quyền thực hiện hành động này."                           | Hiển thị alert, disable action             |

---

### 1.4 DANH SÁCH CHAT

#### 1.4.1 Thông tin màn hình:

| Screen        | Danh sách chat hỗ trợ                                                      |
| ------------- | ------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả các cuộc chat hỗ trợ đang chờ xử lý             |
| Screen Access | Nhân viên chọn **Chat hỗ trợ** từ menu chính                              |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách chat**     | Table        | ID chat, khách hàng, trạng thái... | Hiển thị các cuộc chat               |
| **Bộ lọc**            | Filter       | Trạng thái, độ ưu tiên... | Lọc chat theo tiêu chí               |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Escalate/Forward feature**: Thêm tính năng chuyển tiếp chat đến nhân viên khác hoặc cấp trên
2. **Error states**: Xử lý và hiển thị các lỗi có thể xảy ra (network, timeout, server, permission)
3. **Validation**: Yêu cầu chọn người nhận và nhập lý do khi chuyển tiếp
4. **Lịch sử chuyển tiếp**: Ghi nhận lịch sử chuyển tiếp để theo dõi
5. **Thông báo**: Tự động thông báo cho người nhận khi chat được chuyển tiếp
6. **UI cải thiện**: Thêm dialog chuyển tiếp với validation và loading state
7. **Error handling**: Hiển thị thông báo lỗi cụ thể và hướng dẫn xử lý cho từng loại lỗi

