# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng xử lý đơn hàng của Nhân viên (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng xử lý đơn hàng](#1-chức-năng-xử-lý-đơn-hàng)
   - 1.1 [Xem danh sách đơn hàng](#11-xem-danh-sách-đơn-hàng) - **ĐÃ SỬA**
   - 1.2 [Xác nhận đơn hàng](#12-xác-nhận-đơn-hàng) - **ĐÃ SỬA**
   - 1.3 [Hủy đơn hàng](#13-hủy-đơn-hàng) - **ĐÃ SỬA**
   - 1.4 [Error handling](#14-error-handling) - **MỚI**

---

## 1. CHỨC NĂNG XỬ LÝ ĐƠN HÀNG

### 1.1 XEM DANH SÁCH ĐƠN HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách đơn hàng online                                                      |
| ------------- | ------------------------------------------------------------------------------ |
| Description   | Hiển thị danh sách đơn hàng online với error handling chi tiết                 |
| Screen Access | Nhân viên chọn **Xử lý đơn hàng online** từ menu chính                        |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Danh sách đơn hàng**    | Table        | ID đơn, khách hàng, sản phẩm, trạng thái... | Hiển thị các đơn hàng online                   |
| **Alert lỗi**             | Alert        | Lỗi: [chi tiết lỗi]                    | **MỚI**: Hiển thị lỗi cụ thể                    |
| **Loading indicator**     | Text         | Đang xử lý...                           | **MỚI**: Hiển thị khi đang xử lý                |
| **Nút xác nhận**          | Button       | Xác nhận / Đang xử lý...                | **MỚI**: Thay đổi text theo trạng thái         |
| **Nút hủy**               | Button       | Hủy / Đang xử lý...                     | **MỚI**: Thay đổi text theo trạng thái         |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem danh sách đơn hàng** | Hiển thị danh sách tất cả đơn hàng online với thông tin chi tiết về khách hàng, sản phẩm, trạng thái. Hệ thống sẽ xử lý error states và hiển thị thông báo lỗi cụ thể nếu có.                                                                  | Danh sách đơn hàng được hiển thị thành công với đầy đủ thông tin.                          | Không thể tải danh sách đơn hàng. Error states không được xử lý đúng.                      |

---

### 1.2 XÁC NHẬN ĐƠN HÀNG - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Xác nhận đơn hàng                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Cho phép nhân viên xác nhận đơn hàng với error handling chi tiết      |
| Screen Access | Nhân viên click **Xác nhận** từ danh sách đơn hàng                    |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút xác nhận**      | Button       | Xác nhận                                | Nút để xác nhận đơn hàng                        |
| **Loading state**     | Text         | Đang xử lý...                           | **MỚI**: Hiển thị khi đang xử lý                |
| **Thông báo lỗi**     | Alert        | Lỗi database. Không thể cập nhật đơn hàng | **MỚI**: Hiển thị lỗi cụ thể                    |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xác nhận đơn hàng**    | Cho phép nhân viên xác nhận đơn hàng online. Hệ thống sẽ cập nhật trạng thái đơn hàng và xử lý error states nếu có.                                                                                                                       | Đơn hàng được xác nhận thành công. Trạng thái được cập nhật.                              | Không thể xác nhận đơn hàng. Lỗi database hoặc network.                                    |
| **Error handling**      | **MỚI**: Khi xác nhận đơn hàng, hệ thống xử lý các lỗi có thể xảy ra: network error, timeout, server error, database error, permission error. Nếu có lỗi, hệ thống sẽ hiển thị thông báo lỗi cụ thể và không cập nhật trạng thái đơn hàng.    | Error states được xử lý chính xác. Thông báo lỗi được hiển thị rõ ràng.                    | Error states không được xử lý. Thông báo lỗi không rõ ràng.                                |
| **Loading state**       | **MỚI**: Trong quá trình xác nhận đơn hàng, hệ thống hiển thị loading state để người dùng biết đang xử lý. Nút "Xác nhận" được disable và hiển thị text "Đang xử lý...".                                                                  | Loading state được hiển thị trong quá trình xử lý.                                        | Loading state không được hiển thị. Người dùng không biết đang xử lý.                        |
| **Retry mechanism**     | **MỚI**: Nếu có lỗi network hoặc timeout, hệ thống tự động retry 3 lần với delay 2 giây mỗi lần. Nếu retry thành công, đơn hàng được xác nhận. Nếu retry vẫn thất bại, hệ thống hiển thị thông báo lỗi và yêu cầu thử lại sau.              | Retry mechanism hoạt động chính xác. Đơn hàng được xác nhận sau khi retry.                | Retry mechanism không hoạt động. Đơn hàng không được xác nhận sau khi retry.                |

---

### 1.3 HỦY ĐƠN HÀNG - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Hủy đơn hàng                                                      |
| ------------- | ----------------------------------------------------------------- |
| Description   | Cho phép nhân viên hủy đơn hàng với error handling chi tiết      |
| Screen Access | Nhân viên click **Hủy** từ danh sách đơn hàng                     |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút hủy**           | Button       | Hủy                                     | Nút để hủy đơn hàng                            |
| **Loading state**     | Text         | Đang xử lý...                           | **MỚI**: Hiển thị khi đang xử lý                |
| **Thông báo lỗi**     | Alert        | Lỗi database. Không thể hủy đơn hàng   | **MỚI**: Hiển thị lỗi cụ thể                   |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Hủy đơn hàng**         | Cho phép nhân viên hủy đơn hàng online. Hệ thống sẽ cập nhật trạng thái đơn hàng và xử lý error states nếu có.                                                                                                                           | Đơn hàng được hủy thành công. Trạng thái được cập nhật.                                   | Không thể hủy đơn hàng. Lỗi database hoặc network.                                        |
| **Error handling**      | **MỚI**: Tương tự như xác nhận đơn hàng, hệ thống xử lý các lỗi có thể xảy ra khi hủy đơn hàng và hiển thị thông báo lỗi cụ thể.                                                                                                            | Error states được xử lý chính xác. Thông báo lỗi được hiển thị rõ ràng.                    | Error states không được xử lý. Thông báo lỗi không rõ ràng.                                |

---

### 1.4 ERROR HANDLING - **MỚI**

#### 1.4.1 Thông tin màn hình:

| Screen        | Error handling cho critical actions                                                      |
| ------------- | --------------------------------------------------------------------------------------- |
| Description   | Xử lý và hiển thị các lỗi có thể xảy ra khi thực hiện critical actions                 |
| Screen Access | Tự động hiển thị khi có lỗi xảy ra                                                     |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Alert lỗi network**     | Alert        | Lỗi: Không thể kết nối đến server...    | **MỚI**: Hiển thị lỗi network                  |
| **Alert lỗi timeout**     | Alert        | Lỗi: Yêu cầu bị timeout...              | **MỚI**: Hiển thị lỗi timeout                  |
| **Alert lỗi server**      | Alert        | Lỗi: Lỗi server. Vui lòng liên hệ admin | **MỚI**: Hiển thị lỗi server                   |
| **Alert lỗi database**    | Alert        | Lỗi: Lỗi database. Không thể cập nhật... | **MỚI**: Hiển thị lỗi database                 |
| **Alert lỗi permission**  | Alert        | Lỗi: Bạn không có quyền...              | **MỚI**: Hiển thị lỗi permission              |

#### 1.4.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xử lý lỗi network**    | **MỚI**: Khi có lỗi network (không thể kết nối đến server), hệ thống hiển thị: "Lỗi: Không thể kết nối đến server. Vui lòng kiểm tra kết nối mạng." Hệ thống tự động retry 3 lần với delay 2 giây mỗi lần.                                | Thông báo lỗi network được hiển thị rõ ràng. Retry mechanism hoạt động.                    | Thông báo lỗi không rõ ràng. Retry mechanism không hoạt động.                               |
| **Xử lý lỗi timeout**    | **MỚI**: Khi có lỗi timeout (yêu cầu bị timeout), hệ thống hiển thị: "Lỗi: Yêu cầu bị timeout. Vui lòng thử lại sau." Hệ thống tự động retry 3 lần.                                                                                        | Thông báo lỗi timeout được hiển thị rõ ràng. Retry mechanism hoạt động.                   | Thông báo lỗi không rõ ràng. Retry mechanism không hoạt động.                               |
| **Xử lý lỗi server**     | **MỚI**: Khi có lỗi server (lỗi từ phía server), hệ thống hiển thị: "Lỗi: Lỗi server. Vui lòng liên hệ quản trị viên." Hệ thống ghi log và thông báo admin.                                                                               | Thông báo lỗi server được hiển thị rõ ràng. Admin được thông báo.                          | Thông báo lỗi không rõ ràng. Admin không được thông báo.                                   |
| **Xử lý lỗi database**   | **MỚI**: Khi có lỗi database (không thể cập nhật đơn hàng), hệ thống hiển thị: "Lỗi: Lỗi database. Không thể cập nhật đơn hàng. Vui lòng thử lại sau." Hệ thống ghi log và thông báo admin.                                                | Thông báo lỗi database được hiển thị rõ ràng. Admin được thông báo.                        | Thông báo lỗi không rõ ràng. Admin không được thông báo.                                    |
| **Xử lý lỗi permission** | **MỚI**: Khi có lỗi permission (không có quyền thực hiện hành động), hệ thống hiển thị: "Lỗi: Bạn không có quyền thực hiện hành động này." Hệ thống disable action và thông báo người dùng.                                                  | Thông báo lỗi permission được hiển thị rõ ràng. Action được disable.                      | Thông báo lỗi không rõ ràng. Action không được disable.                                    |

#### 1.4.4 Error Types (MỚI):

| Error Type          | Message                                                                 | Handling                                    |
| ------------------- | ----------------------------------------------------------------------- | ------------------------------------------- |
| **Network Error**   | "Không thể kết nối đến server. Vui lòng kiểm tra kết nối mạng."         | Retry 3 lần, hiển thị alert                 |
| **Timeout Error**   | "Yêu cầu bị timeout. Vui lòng thử lại sau."                             | Retry 3 lần, hiển thị alert                 |
| **Server Error**    | "Lỗi server. Vui lòng liên hệ quản trị viên."                           | Ghi log, thông báo admin, hiển thị alert    |
| **Database Error**  | "Lỗi database. Không thể cập nhật đơn hàng. Vui lòng thử lại sau."     | Ghi log, thông báo admin, hiển thị alert    |
| **Permission Error** | "Bạn không có quyền thực hiện hành động này."                           | Disable action, hiển thị alert              |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Error handling chi tiết**: Xử lý và hiển thị các lỗi cụ thể cho critical actions (network, timeout, server, database, permission)
2. **Retry mechanism**: Tự động retry 3 lần khi có lỗi network hoặc timeout
3. **Loading states**: Hiển thị loading state trong quá trình xử lý
4. **Admin notification**: Tự động thông báo admin khi có lỗi server hoặc database
5. **Error logging**: Ghi log tất cả các lỗi để theo dõi và phân tích
6. **UI cải thiện**: Thêm alert boxes hiển thị lỗi cụ thể và disable buttons khi đang xử lý

