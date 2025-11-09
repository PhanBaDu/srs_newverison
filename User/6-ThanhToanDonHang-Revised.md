# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng thanh toán đơn hàng của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng thanh toán đơn hàng](#1-chức-năng-thanh-toán-đơn-hàng)
   - 1.1 [Xác nhận thông tin giao hàng](#11-xác-nhận-thông-tin-giao-hàng) - **ĐÃ SỬA**
   - 1.2 [Chọn phương thức thanh toán](#12-chọn-phương-thức-thanh-toán) - **ĐÃ SỬA**
   - 1.3 [Xử lý thanh toán](#13-xử-lý-thanh-toán) - **ĐÃ SỬA**
   - 1.4 [Xác nhận đơn hàng](#14-xác-nhận-đơn-hàng)

---

## 1. CHỨC NĂNG THANH TOÁN ĐƠN HÀNG

### 1.1 XÁC NHẬN THÔNG TIN GIAO HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Xác nhận thông tin giao hàng                                                      |
| ------------- | --------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng xác nhận và cập nhật thông tin giao hàng trước khi thanh toán |
| Screen Access | Người dùng chuyển từ giỏ hàng đến trang **Thanh toán**                            |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type             | Data                                    | Description                                    |
| --------------------- | ---------------- | --------------------------------------- | ---------------------------------------------- |
| **Họ và tên**         | Input (Text)     | Nguyễn Văn A *                          | **MỚI**: Validation bắt buộc                   |
| **Số điện thoại**       | Input (Tel)      | 0123456789 *                            | **MỚI**: Validation định dạng VN (0xxx hoặc +84xxx) |
| **Email**             | Input (Email)    | nguyenvana@example.com *                | **MỚI**: Validation RFC 5322                   |
| **Địa chỉ**           | Input (Text)     | 123 Đường ABC, Quận 1, TP.HCM *         | **MỚI**: Validation 10-500 ký tự                |
| **Thông báo lỗi**     | Text (Error)     | Email không hợp lệ (theo chuẩn RFC 5322) | **MỚI**: Hiển thị lỗi validation cụ thể       |
| **Tỉnh/Thành**        | Select           | TP.HCM, Hà Nội...                       | Dropdown chọn tỉnh/thành                       |
| **Quận/Huyện**        | Input            | Quận 1                                  | Ô nhập quận/huyện                              |
| **Phường/Xã**         | Select           | Phường Bến Nghé...                      | Dropdown chọn phường/xã                        |
| **Ghi chú**           | Textarea         | Giao hàng giờ hành chính                | Ô nhập ghi chú giao hàng                       |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xác nhận thông tin**   | Cho phép người dùng xác nhận và cập nhật thông tin giao hàng. Hệ thống sẽ kiểm tra tính hợp lệ của thông tin trước khi cho phép tiếp tục.                                                                                                  | Thông tin được xác nhận thành công và có thể tiếp tục thanh toán.                          | Thông tin không hợp lệ. Hiển thị thông báo lỗi cụ thể.                                    |
| **Validation địa chỉ**   | **MỚI**: Hệ thống kiểm tra tính hợp lệ của email (theo chuẩn RFC 5322), số điện thoại (định dạng VN: 0xxx hoặc +84xxx), và địa chỉ (tối thiểu 10 ký tự, tối đa 500 ký tự). Nếu không hợp lệ, hệ thống sẽ hiển thị thông báo lỗi cụ thể.    | Tất cả thông tin hợp lệ và được xác nhận thành công.                                       | Email không hợp lệ. Số điện thoại không đúng định dạng. Địa chỉ quá ngắn hoặc quá dài.    |
| **Lưu địa chỉ mặc định** | Nếu người dùng chọn "Lưu làm địa chỉ mặc định", hệ thống sẽ lưu thông tin địa chỉ để sử dụng cho các đơn hàng sau.                                                                                                                       | Địa chỉ được lưu thành công làm mặc định.                                                  | Lỗi khi lưu địa chỉ mặc định.                                                             |

#### 1.1.4 Validation Rules (MỚI):

| Field             | Rule                                    | Error Message                                    |
| ----------------- | --------------------------------------- | ------------------------------------------------ |
| **Họ và tên**     | Bắt buộc, tối thiểu 2 ký tự             | "Vui lòng nhập họ và tên"                       |
| **Số điện thoại** | Bắt buộc, định dạng: 0xxx hoặc +84xxx  | "Số điện thoại không hợp lệ (định dạng: 0xxxxxxxxx hoặc +84xxxxxxxxx)" |
| **Email**         | Bắt buộc, theo chuẩn RFC 5322          | "Email không hợp lệ (theo chuẩn RFC 5322)"       |
| **Địa chỉ**       | Bắt buộc, 10-500 ký tự                  | "Địa chỉ không hợp lệ (tối thiểu 10 ký tự, tối đa 500 ký tự)" |

---

### 1.2 CHỌN PHƯƠNG THỨC THANH TOÁN - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Chọn phương thức thanh toán                                                      |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng chọn phương thức thanh toán (COD, VNPay, MoMo, ZaloPay, ...) |
| Screen Access | Hiển thị trong trang thanh toán, sau phần thông tin giao hàng                    |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                                    |
| --------------------- | ------------ | ----------------------- | ---------------------------------------------- |
| **Radio COD**         | Radio        | Thanh toán khi nhận hàng | Radio button chọn COD                          |
| **Radio VNPay**       | Radio        | VNPay                   | Radio button chọn VNPay                        |
| **Radio MoMo**        | Radio        | MoMo                    | Radio button chọn MoMo                         |
| **Radio ZaloPay**     | Radio        | ZaloPay                 | Radio button chọn ZaloPay                      |
| **Radio Viettel Money** | Radio      | Viettel Money           | Radio button chọn Viettel Money                |

---

### 1.3 XỬ LÝ THANH TOÁN - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Xử lý thanh toán                                                      |
| ------------- | -------------------------------------------------------------------- |
| Description   | Hệ thống xử lý thanh toán theo phương thức đã chọn                    |
| Screen Access | Tự động thực hiện sau khi người dùng xác nhận đơn hàng                |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Loading indicator** | Spinner      | Đang xử lý...                           | Hiển thị khi đang xử lý thanh toán             |
| **Thông báo lỗi**     | Alert        | Thanh toán bị timeout. Vui lòng thử lại | **MỚI**: Hiển thị lỗi thanh toán cụ thể        |
| **Nút thử lại**       | Button       | Thử lại                                 | **MỚI**: Nút để thử lại thanh toán             |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xử lý thanh toán COD** | Đối với thanh toán COD, hệ thống chỉ cần xác nhận đơn hàng và không cần xử lý thanh toán trực tuyến.                                                                                                                                    | Đơn hàng được tạo thành công. Người dùng sẽ thanh toán khi nhận hàng.                      | Lỗi khi tạo đơn hàng. Không thể xác nhận đơn hàng.                                         |
| **Xử lý thanh toán online** | **MỚI**: Đối với thanh toán online (VNPay, MoMo, ZaloPay), hệ thống sẽ gọi API của cổng thanh toán. Nếu có lỗi (timeout, callback error, double payment), hệ thống sẽ xử lý retry, refund, hoặc thông báo admin.                          | Thanh toán thành công. Đơn hàng được tạo và xác nhận.                                      | Timeout từ cổng thanh toán. Lỗi callback. Double payment. Hiển thị thông báo lỗi cụ thể.  |
| **Xử lý lỗi timeout**   | **MỚI**: Nếu thanh toán bị timeout, hệ thống sẽ thông báo cho người dùng và cho phép thử lại. Nếu đã thanh toán nhưng chưa nhận được callback, hệ thống sẽ kiểm tra và xử lý refund nếu cần.                                              | Timeout được xử lý. Người dùng có thể thử lại hoặc được refund nếu đã thanh toán.         | Không thể xử lý timeout. Lỗi khi refund.                                                   |
| **Xử lý lỗi callback**  | **MỚI**: Nếu có lỗi callback từ cổng thanh toán, hệ thống sẽ thông báo admin và xử lý đơn hàng phù hợp (giữ đơn chờ xác nhận hoặc hủy đơn).                                                                                              | Lỗi callback được xử lý. Admin được thông báo. Đơn hàng được xử lý phù hợp.              | Không thể xử lý lỗi callback. Admin không được thông báo.                                 |
| **Xử lý double payment** | **MỚI**: Hệ thống kiểm tra và ngăn chặn double payment. Nếu phát hiện đơn hàng đã được thanh toán, hệ thống sẽ từ chối thanh toán lần 2 và thông báo cho người dùng.                                                                     | Double payment được ngăn chặn. Người dùng được thông báo đơn hàng đã được thanh toán.       | Không thể ngăn chặn double payment. Đơn hàng bị thanh toán 2 lần.                          |

#### 1.3.4 Error Handling (MỚI):

| Error Type          | Handling                                                                 | User Message                                    |
| ------------------- | ------------------------------------------------------------------------ | ----------------------------------------------- |
| **Timeout**         | Retry 3 lần, nếu vẫn lỗi thì thông báo và cho phép thử lại               | "Thanh toán bị timeout. Vui lòng thử lại hoặc chọn phương thức khác." |
| **Callback Error**  | Thông báo admin, giữ đơn chờ xác nhận hoặc hủy đơn                      | "Lỗi callback từ cổng thanh toán. Vui lòng kiểm tra lại." |
| **Double Payment**  | Từ chối thanh toán lần 2, thông báo đơn hàng đã được thanh toán          | "Đơn hàng đã được thanh toán. Vui lòng kiểm tra lại." |
| **Network Error**   | Retry 3 lần, nếu vẫn lỗi thì thông báo                                  | "Có lỗi xảy ra. Vui lòng thử lại sau."         |

---

### 1.4 XÁC NHẬN ĐƠN HÀNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Xác nhận đơn hàng                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Hiển thị thông tin đơn hàng đã đặt và xác nhận thành công               |
| Screen Access | Tự động chuyển đến sau khi thanh toán thành công                       |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Mã đơn hàng**       | Text         | #ORD-001                | Mã đơn hàng đã tạo                    |
| **Thông tin đơn hàng** | Card         | Sản phẩm, giá, tổng tiền | Hiển thị chi tiết đơn hàng           |
| **Nút xem đơn hàng**  | Button       | Xem đơn hàng            | Chuyển đến trang chi tiết đơn hàng    |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Validation địa chỉ**: Thêm validation chi tiết cho email (RFC 5322), số điện thoại (định dạng VN), và địa chỉ (10-500 ký tự)
2. **Error handling**: Xử lý chi tiết các lỗi thanh toán (timeout, callback error, double payment)
3. **Retry mechanism**: Tự động retry 3 lần khi có lỗi network hoặc timeout
4. **Thông báo lỗi rõ ràng**: Hiển thị thông báo lỗi cụ thể cho từng trường hợp
5. **Admin notification**: Thông báo admin khi có lỗi callback hoặc vấn đề nghiêm trọng
6. **UI cải thiện**: Hiển thị loading state và error state rõ ràng

