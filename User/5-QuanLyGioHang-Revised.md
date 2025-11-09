# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý giỏ hàng của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý giỏ hàng](#1-chức-năng-quản-lý-giỏ-hàng)
   - 1.1 [Xem giỏ hàng](#11-xem-giỏ-hàng) - **ĐÃ SỬA**
   - 1.2 [Thêm sản phẩm vào giỏ hàng](#12-thêm-sản-phẩm-vào-giỏ-hàng) - **ĐÃ SỬA**
   - 1.3 [Cập nhật số lượng](#13-cập-nhật-số-lượng) - **ĐÃ SỬA**
   - 1.4 [Xóa sản phẩm](#14-xóa-sản-phẩm)
   - 1.5 [Áp dụng mã giảm giá](#15-áp-dụng-mã-giảm-giá)

---

## 1. CHỨC NĂNG QUẢN LÝ GIỎ HÀNG

### 1.1 XEM GIỎ HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Giỏ hàng của tôi                                                                 |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách sản phẩm đã thêm vào giỏ hàng và tổng tiền                    |
| Screen Access | Người dùng đã đăng nhập chọn **Giỏ hàng** từ menu chính                          |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Danh sách sản phẩm**    | List/Table   | Tên, giá, số lượng, tổng tiền           | Hiển thị các sản phẩm trong giỏ hàng           |
| **Thông báo giới hạn**    | Alert        | ⚠️ Đã đạt giới hạn 20 sản phẩm          | **MỚI**: Cảnh báo khi đạt max items            |
| **Tổng tiền**             | Text         | Tổng: 500.000 VNĐ                       | Tổng tiền của tất cả sản phẩm                  |
| **Nút thanh toán**        | Button       | Thanh toán                               | Chuyển đến trang thanh toán                    |
| **Nút tiếp tục mua sắm**  | Button       | Tiếp tục mua sắm                         | Quay lại trang sản phẩm                        |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem giỏ hàng**         | Hiển thị danh sách tất cả sản phẩm đã thêm vào giỏ hàng với thông tin chi tiết như tên, giá, số lượng, tổng tiền.                                                                                                                          | Giỏ hàng được hiển thị thành công với đầy đủ thông tin.                                    | Lỗi khi tải giỏ hàng do vấn đề kết nối hoặc dữ liệu.                                      |
| **Kiểm tra giới hạn**    | **MỚI**: Hệ thống kiểm tra và hiển thị cảnh báo khi giỏ hàng đạt giới hạn tối đa 20 sản phẩm. Người dùng không thể thêm sản phẩm mới khi đã đạt giới hạn.                                                                                   | Cảnh báo được hiển thị khi đạt giới hạn. Người dùng được thông báo rõ ràng.               | Lỗi khi kiểm tra giới hạn.                                                                 |

---

### 1.2 THÊM SẢN PHẨM VÀO GIỎ HÀNG - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Thêm sản phẩm vào giỏ hàng                                                      |
| ------------- | ------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng thêm sản phẩm vào giỏ hàng từ trang chi tiết sản phẩm       |
| Screen Access | Người dùng click nút **Thêm vào giỏ hàng** từ trang chi tiết sản phẩm           |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                                    |
| --------------------- | ------------ | ----------------------- | ---------------------------------------------- |
| **Nút thêm vào giỏ**  | Button       | Thêm vào giỏ hàng       | Nút để thêm sản phẩm vào giỏ hàng              |
| **Thông báo lỗi**     | Toast        | Đã đạt giới hạn 20 sản phẩm | **MỚI**: Thông báo khi không thể thêm do giới hạn |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Thêm sản phẩm**        | Cho phép người dùng thêm sản phẩm vào giỏ hàng. Hệ thống sẽ kiểm tra số lượng sản phẩm trong giỏ hàng và trạng thái sản phẩm trước khi thêm.                                                                                              | Sản phẩm được thêm vào giỏ hàng thành công. Hiển thị thông báo xác nhận.                  | Giỏ hàng đã đạt giới hạn 20 sản phẩm. Sản phẩm không còn hàng. Lỗi khi thêm sản phẩm.      |
| **Kiểm tra giới hạn**    | **MỚI**: Trước khi thêm sản phẩm, hệ thống kiểm tra xem giỏ hàng đã đạt giới hạn 20 sản phẩm chưa. Nếu đã đạt, hệ thống sẽ từ chối và hiển thị thông báo lỗi.                                                                               | Kiểm tra thành công. Sản phẩm được thêm vào nếu chưa đạt giới hạn.                        | Giỏ hàng đã đạt giới hạn. Hiển thị thông báo: "Bạn đã đạt giới hạn tối đa 20 sản phẩm..." |

---

### 1.3 CẬP NHẬT SỐ LƯỢNG - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Cập nhật số lượng sản phẩm trong giỏ hàng                                      |
| ------------- | ------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng thay đổi số lượng sản phẩm trong giỏ hàng                   |
| Screen Access | Người dùng sử dụng nút +/- hoặc nhập trực tiếp số lượng trong giỏ hàng          |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                                    |
| --------------------- | ------------ | ----------------------- | ---------------------------------------------- |
| **Nút giảm số lượng** | Button       | -                       | Giảm số lượng sản phẩm                         |
| **Input số lượng**    | Input (Number) | 1, 2, 3...             | Ô nhập số lượng sản phẩm                       |
| **Nút tăng số lượng** | Button       | +                       | Tăng số lượng sản phẩm                         |
| **Thông báo lỗi**     | Toast        | Số lượng tối đa là 50   | **MỚI**: Thông báo khi vượt quá giới hạn       |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Cập nhật số lượng**    | Cho phép người dùng thay đổi số lượng sản phẩm trong giỏ hàng. Hệ thống sẽ kiểm tra số lượng tồn kho và giới hạn tối đa trước khi cập nhật.                                                                                                | Số lượng được cập nhật thành công. Tổng tiền được tính lại tự động.                       | Số lượng vượt quá tồn kho. Số lượng vượt quá giới hạn tối đa (50). Lỗi khi cập nhật.      |
| **Kiểm tra tồn kho**     | Hệ thống kiểm tra số lượng tồn kho của sản phẩm trước khi cho phép cập nhật số lượng. Nếu số lượng yêu cầu vượt quá tồn kho, hệ thống sẽ từ chối và hiển thị thông báo.                                                                     | Số lượng hợp lệ và được cập nhật thành công.                                               | Số lượng vượt quá tồn kho. Hiển thị: "Chỉ còn X sản phẩm trong kho".                       |
| **Kiểm tra giới hạn số lượng** | **MỚI**: Hệ thống kiểm tra số lượng tối đa cho mỗi sản phẩm là 50. Nếu người dùng nhập số lượng > 50, hệ thống sẽ từ chối và hiển thị thông báo lỗi.                                                                                    | Số lượng hợp lệ (<= 50) và được cập nhật thành công.                                       | Số lượng > 50. Hiển thị: "Số lượng tối đa cho mỗi sản phẩm là 50".                        |

#### 1.3.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Số lượng**    | Phải >= 1 và <= 50 cho mỗi sản phẩm     | "Số lượng tối đa cho mỗi sản phẩm là 50"        |
| **Tồn kho**     | Số lượng không được vượt quá tồn kho    | "Chỉ còn X sản phẩm trong kho"                   |
| **Tổng sản phẩm** | Tối đa 20 sản phẩm khác nhau trong giỏ | "Bạn đã đạt giới hạn tối đa 20 sản phẩm..."      |

---

### 1.4 XÓA SẢN PHẨM

#### 1.4.1 Thông tin màn hình:

| Screen        | Xóa sản phẩm khỏi giỏ hàng                                              |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Cho phép người dùng xóa sản phẩm khỏi giỏ hàng                          |
| Screen Access | Người dùng click nút **Xóa** bên cạnh sản phẩm trong giỏ hàng           |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Nút xóa**           | Button (Icon) | Trash icon              | Nút để xóa sản phẩm khỏi giỏ hàng    |
| **Xác nhận xóa**      | Dialog       | Bạn có chắc muốn xóa?   | Dialog xác nhận trước khi xóa        |

---

### 1.5 ÁP DỤNG MÃ GIẢM GIÁ

#### 1.5.1 Thông tin màn hình:

| Screen        | Áp dụng mã giảm giá                                                      |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Cho phép người dùng nhập mã giảm giá để được giảm giá cho đơn hàng       |
| Screen Access | Hiển thị trong giỏ hàng, phần tổng kết đơn hàng                          |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Input mã giảm giá** | Input        | Nhập mã giảm giá        | Ô nhập mã giảm giá                   |
| **Nút áp dụng**       | Button       | Áp dụng                 | Nút để áp dụng mã giảm giá           |
| **Thông tin giảm giá** | Text         | Giảm: 50.000 VNĐ        | Hiển thị số tiền được giảm           |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Giới hạn số sản phẩm**: Tối đa 20 sản phẩm khác nhau trong giỏ hàng
2. **Giới hạn số lượng**: Tối đa 50 sản phẩm cho mỗi loại sản phẩm
3. **Validation tồn kho**: Kiểm tra số lượng tồn kho trước khi cho phép cập nhật
4. **Thông báo rõ ràng**: Hiển thị cảnh báo khi đạt giới hạn và thông báo lỗi cụ thể
5. **UI cải thiện**: Thêm alert box cảnh báo khi đạt giới hạn 20 sản phẩm

