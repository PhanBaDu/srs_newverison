# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý tồn kho của Nhân viên kho (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý tồn kho](#1-chức-năng-quản-lý-tồn-kho)
   - 1.1 [Nhập hàng](#11-nhập-hàng) - **ĐÃ SỬA**
   - 1.2 [Xuất hàng](#12-xuất-hàng) - **ĐÃ SỬA**
   - 1.3 [Kiểm kê kho](#13-kiểm-kê-kho)

---

## 1. CHỨC NĂNG QUẢN LÝ TỒN KHO

### 1.1 NHẬP HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Nhập hàng vào kho                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho tạo đơn nhập hàng và cập nhật tồn kho với transaction/rollback |
| Screen Access | Nhân viên kho chọn **Quản lý tồn kho** → **Nhập hàng** từ menu chính   |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Form đơn nhập**         | Form         | Mã đơn nhập, nhà cung cấp, ngày nhập... | Form để tạo đơn nhập hàng                      |
| **Input mã đơn nhập**     | Input        | IMP001 (readonly)                       | Mã đơn nhập tự động                             |
| **Input nhà cung cấp**    | Input        | Nhà xuất bản Trẻ                        | Ô nhập nhà cung cấp                             |
| **Input ngày nhập**       | Input (Date) | 2023-11-20                              | Ô nhập ngày nhập                                |
| **Textarea ghi chú**      | Textarea     | Ghi chú về đơn nhập                     | Ô nhập ghi chú                                  |
| **Bảng danh sách sách**   | Table        | Mã sách, tên sách, số lượng, giá nhập... | Hiển thị danh sách sách nhập                    |
| **Nút thêm sách**         | Button       | Thêm sách                               | Nút để thêm sách vào đơn nhập                   |
| **Nút lưu đơn nhập**      | Button       | Lưu đơn nhập                            | **MỚI**: Nút xử lý transaction                  |
| **Loading indicator**     | Spinner      | Đang xử lý transaction...               | **MỚI**: Hiển thị khi đang xử lý                |
| **Thông báo lỗi transaction** | Alert    | Lỗi: [chi tiết]. Transaction đã được rollback | **MỚI**: Thông báo khi transaction fail        |
| **Thông báo thành công**  | Alert        | Nhập hàng thành công. Transaction ID: TXN-xxx | **MỚI**: Hiển thị transaction ID khi thành công |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Tạo đơn nhập hàng**    | Cho phép nhân viên kho tạo đơn nhập hàng với danh sách sách và số lượng. Hệ thống sẽ kiểm tra tính hợp lệ của thông tin trước khi lưu.                                                                                                    | Đơn nhập hàng được tạo thành công.                                                         | Thông tin không hợp lệ. Lỗi khi tạo đơn nhập hàng.                                         |
| **Xử lý transaction**    | **MỚI**: Khi lưu đơn nhập hàng, hệ thống sử dụng database transaction để đảm bảo tính toàn vẹn dữ liệu. Transaction bao gồm: (1) Validate tất cả items, (2) Start transaction, (3) Process từng item, (4) Commit nếu tất cả thành công, hoặc Rollback nếu có lỗi. | Transaction được commit thành công. Tất cả sách được nhập vào kho. Hiển thị Transaction ID. | Transaction bị lỗi. Tất cả thay đổi được rollback. Không có sách nào được nhập. Hiển thị thông báo lỗi chi tiết. |
| **Validation items**     | **MỚI**: Trước khi bắt đầu transaction, hệ thống kiểm tra tất cả items trong đơn nhập: số lượng phải > 0, giá nhập phải > 0. Nếu có item không hợp lệ, transaction sẽ không được bắt đầu.                                                  | Tất cả items được validate thành công. Transaction được bắt đầu.                          | Có item không hợp lệ. Transaction không được bắt đầu. Hiển thị thông báo lỗi cụ thể.    |
| **Rollback mechanism**   | **MỚI**: Nếu có bất kỳ lỗi nào xảy ra trong quá trình xử lý transaction (database error, network timeout, validation error), hệ thống sẽ tự động rollback tất cả thay đổi và đảm bảo không có dữ liệu nào bị lưu một phần.                    | Rollback được thực hiện thành công. Không có dữ liệu nào bị lưu một phần.                 | Không thể rollback. Dữ liệu bị lưu một phần. Hiển thị cảnh báo nghiêm trọng.              |
| **Error notification**    | **MỚI**: Khi transaction bị lỗi và rollback, hệ thống hiển thị thông báo lỗi chi tiết: "Lỗi: [chi tiết lỗi]. Transaction đã được rollback. Không có thay đổi nào được lưu. Vui lòng kiểm tra và thử lại."                                  | Thông báo lỗi được hiển thị rõ ràng. Người dùng biết chính xác vấn đề và cách xử lý.       | Thông báo lỗi không rõ ràng. Người dùng không biết vấn đề.                                 |

#### 1.1.4 Transaction Flow (MỚI):

| Step | Action | Description |
|------|--------|-------------|
| 1 | **Validate** | Kiểm tra tất cả items: số lượng > 0, giá nhập > 0 |
| 2 | **Start Transaction** | Bắt đầu database transaction |
| 3 | **Process Items** | Xử lý từng item: cập nhật tồn kho, ghi nhận lịch sử |
| 4 | **Check Success** | Kiểm tra tất cả items đã được xử lý thành công |
| 5a | **Commit** | Nếu thành công: commit transaction, lưu tất cả thay đổi |
| 5b | **Rollback** | Nếu có lỗi: rollback transaction, không lưu thay đổi nào |

#### 1.1.5 Error Handling (MỚI):

| Error Type          | Handling                                                                 | User Message                                    |
| ------------------- | ------------------------------------------------------------------------ | ----------------------------------------------- |
| **Validation Error** | Rollback transaction, không bắt đầu xử lý                               | "Số lượng nhập không hợp lệ cho sách [tên]. Transaction không được bắt đầu." |
| **Database Error**  | Rollback transaction, không lưu thay đổi nào                             | "Lỗi: Database error. Transaction đã được rollback. Không có thay đổi nào được lưu." |
| **Network Timeout** | Rollback transaction, không lưu thay đổi nào                             | "Lỗi: Network timeout. Transaction đã được rollback. Vui lòng thử lại." |
| **Partial Failure** | Rollback toàn bộ transaction, không lưu item nào                       | "Lỗi: Một số sách không được nhập thành công. Transaction đã được rollback." |

---

### 1.2 XUẤT HÀNG - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Xuất hàng từ kho                                                      |
| ------------- | -------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho tạo đơn xuất hàng và giảm tồn kho với transaction/rollback |
| Screen Access | Nhân viên kho chọn **Quản lý tồn kho** → **Xuất hàng** từ menu chính |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Form đơn xuất**         | Form         | Mã đơn xuất, lý do xuất, ngày xuất...  | Form để tạo đơn xuất hàng                       |
| **Bảng danh sách sách**   | Table        | Mã sách, tên sách, số lượng xuất...     | Hiển thị danh sách sách xuất                    |
| **Nút lưu đơn xuất**      | Button       | Lưu đơn xuất                            | **MỚI**: Nút xử lý transaction                  |
| **Thông báo lỗi transaction** | Alert    | Lỗi: [chi tiết]. Transaction đã được rollback | **MỚI**: Thông báo khi transaction fail        |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Tạo đơn xuất hàng**    | Cho phép nhân viên kho tạo đơn xuất hàng với danh sách sách và số lượng. Hệ thống sẽ kiểm tra tồn kho và xử lý transaction.                                                                                                                | Đơn xuất hàng được tạo thành công. Tồn kho được cập nhật.                                  | Tồn kho không đủ. Lỗi khi tạo đơn xuất hàng.                                                |
| **Xử lý transaction**    | **MỚI**: Tương tự như nhập hàng, hệ thống sử dụng database transaction để đảm bảo tính toàn vẹn dữ liệu khi xuất hàng. Nếu có lỗi, transaction sẽ được rollback.                                                                          | Transaction được commit thành công. Tất cả sách được xuất khỏi kho.                         | Transaction bị lỗi. Tất cả thay đổi được rollback. Không có sách nào được xuất.           |
| **Kiểm tra tồn kho**     | **MỚI**: Trước khi xuất hàng, hệ thống kiểm tra tồn kho có đủ số lượng yêu cầu không. Nếu không đủ, transaction sẽ không được bắt đầu.                                                                                                    | Tồn kho đủ. Transaction được bắt đầu.                                                     | Tồn kho không đủ. Transaction không được bắt đầu. Hiển thị thông báo lỗi.                  |

---

### 1.3 KIỂM KÊ KHO

#### 1.3.1 Thông tin màn hình:

| Screen        | Kiểm kê kho                                                      |
| ------------- | ---------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho kiểm kê số lượng thực tế trong kho        |
| Screen Access | Nhân viên kho chọn **Quản lý tồn kho** → **Kiểm kê kho** từ menu chính |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Form kiểm kê**      | Form         | Mã sách, số lượng thực tế | Form để nhập số lượng kiểm kê        |
| **Nút lưu kiểm kê**   | Button       | Lưu kết quả kiểm kê     | Nút để lưu kết quả kiểm kê            |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Transaction/rollback**: Sử dụng database transaction để đảm bảo tính toàn vẹn dữ liệu khi nhập/xuất hàng
2. **Validation trước transaction**: Kiểm tra tất cả items trước khi bắt đầu transaction
3. **Rollback tự động**: Tự động rollback nếu có bất kỳ lỗi nào xảy ra trong quá trình xử lý
4. **Error handling chi tiết**: Hiển thị thông báo lỗi cụ thể và giải thích rõ ràng về rollback
5. **Transaction ID**: Hiển thị Transaction ID khi thành công để theo dõi
6. **UI cải thiện**: Hiển thị loading state và error state rõ ràng trong quá trình xử lý transaction

