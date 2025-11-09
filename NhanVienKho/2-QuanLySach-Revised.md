# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý sách của Nhân viên kho (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý sách](#1-chức-năng-quản-lý-sách)
   - 1.1 [Thêm sách mới](#11-thêm-sách-mới) - **ĐÃ SỬA**
   - 1.2 [Chỉnh sửa thông tin sách](#12-chỉnh-sửa-thông-tin-sách)
   - 1.3 [Xem danh sách sách](#13-xem-danh-sách-sách)

---

## 1. CHỨC NĂNG QUẢN LÝ SÁCH

### 1.1 THÊM SÁCH MỚI - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Thêm sách mới                                                      |
| ------------- | ------------------------------------------------------------------ |
| Description   | Cho phép nhân viên kho thêm sách mới vào hệ thống với kiểm tra duplicate code |
| Screen Access | Nhân viên kho chọn **Quản lý sách** từ menu và click **Thêm sách mới** |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Form thêm sách**        | Form         | Tên sách, tác giả, thể loại, giá...     | Form để nhập thông tin sách mới                |
| **Input mã sách/ISBN**    | Input        | BK001 hoặc ISBN-978-... *               | **MỚI**: Ô nhập mã sách với validation duplicate |
| **Thông báo duplicate**    | Alert        | ⚠️ Mã sách này đã tồn tại              | **MỚI**: Cảnh báo khi mã sách trùng            |
| **Thông báo hợp lệ**      | Text         | ✓ Mã sách hợp lệ                        | **MỚI**: Xác nhận mã sách hợp lệ                |
| **Input tên sách**        | Input        | Nhập tên sách *                         | Ô nhập tên sách                                 |
| **Input tác giả**         | Input        | Nhập tên tác giả *                      | Ô nhập tên tác giả                              |
| **Select thể loại**       | Select       | Văn học, Khoa học...                    | Dropdown chọn thể loại                          |
| **Input giá bán**         | Input (Number) | Nhập giá bán *                         | Ô nhập giá bán                                  |
| **Input số lượng**        | Input (Number) | Nhập số lượng *                        | Ô nhập số lượng nhập                            |
| **Nút lưu**               | Button       | Lưu                                     | Nút để lưu sách mới                             |
| **Thông báo lỗi transaction** | Alert    | Lỗi: Database error. Đã rollback...    | **MỚI**: Thông báo khi transaction fail        |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Thêm sách mới**        | Cho phép nhân viên kho thêm sách mới vào hệ thống. Hệ thống sẽ kiểm tra tính hợp lệ của thông tin và duplicate code trước khi lưu.                                                                                                        | Sách được thêm thành công vào hệ thống.                                                    | Thông tin không hợp lệ. Mã sách trùng lặp. Lỗi khi lưu sách.                              |
| **Kiểm tra duplicate code** | **MỚI**: Trước khi thêm sách, hệ thống kiểm tra xem mã sách/ISBN đã tồn tại trong hệ thống chưa. Nếu đã tồn tại, hệ thống sẽ từ chối và hiển thị thông báo lỗi: "Mã sách '[mã]' đã tồn tại trong hệ thống. Vui lòng sử dụng mã khác." | Mã sách không trùng lặp và được chấp nhận. Sách được thêm thành công.                     | Mã sách đã tồn tại. Hiển thị thông báo lỗi cụ thể và yêu cầu sử dụng mã khác.              |
| **Validation mã sách**   | **MỚI**: Hệ thống kiểm tra mã sách/ISBN phải là duy nhất trong hệ thống. Kiểm tra được thực hiện real-time khi người dùng nhập mã sách để phản hồi ngay lập tức.                                                                          | Mã sách được validate thành công. Hiển thị thông báo "✓ Mã sách hợp lệ".                  | Mã sách trùng lặp. Hiển thị thông báo "⚠️ Mã sách này đã tồn tại. Vui lòng sử dụng mã khác." |
| **Transaction handling** | **MỚI**: Khi thêm sách, hệ thống sử dụng database transaction để đảm bảo tính toàn vẹn dữ liệu. Nếu có lỗi xảy ra, transaction sẽ được rollback và không có thay đổi nào được lưu.                                                          | Transaction được commit thành công. Sách được thêm vào database.                           | Transaction bị lỗi. Tất cả thay đổi được rollback. Hiển thị thông báo lỗi và yêu cầu thử lại. |

#### 1.1.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Mã sách/ISBN** | Bắt buộc, phải là duy nhất trong hệ thống | "Mã sách '[mã]' đã tồn tại trong hệ thống. Vui lòng sử dụng mã khác." |
| **Tên sách**    | Bắt buộc, tối thiểu 2 ký tự             | "Vui lòng nhập tên sách"                         |
| **Tác giả**     | Bắt buộc, tối thiểu 2 ký tự             | "Vui lòng nhập tên tác giả"                      |
| **Giá bán**     | Bắt buộc, phải > 0                       | "Giá bán phải lớn hơn 0"                         |
| **Số lượng**    | Bắt buộc, phải >= 0                     | "Số lượng phải >= 0"                             |

#### 1.1.5 Duplicate Check Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Real-time Check** | Kiểm tra duplicate code ngay khi người dùng nhập mã sách (không phân biệt hoa thường) | Hiển thị thông báo ngay lập tức           |
| **Case Insensitive** | Kiểm tra không phân biệt hoa thường (BK001 = bk001 = Bk001)                | Đảm bảo mã sách thực sự duy nhất          |
| **Transaction Safety** | Sử dụng database transaction để đảm bảo không có duplicate code được tạo trong quá trình xử lý | Rollback nếu phát hiện duplicate trong transaction |

---

### 1.2 CHỈNH SỬA THÔNG TIN SÁCH

#### 1.2.1 Thông tin màn hình:

| Screen        | Chỉnh sửa thông tin sách                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho chỉnh sửa thông tin sách đã có trong hệ thống          |
| Screen Access | Nhân viên kho click **Chỉnh sửa** từ danh sách sách hoặc trang chi tiết sách  |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Form chỉnh sửa**    | Form         | Tên, tác giả, giá...    | Form để chỉnh sửa thông tin sách     |
| **Nút lưu**           | Button       | Lưu thay đổi             | Nút để lưu thông tin đã chỉnh sửa    |

---

### 1.3 XEM DANH SÁCH SÁCH

#### 1.3.1 Thông tin màn hình:

| Screen        | Danh sách sách trong kho                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả sách có trong kho                                  |
| Screen Access | Nhân viên kho chọn **Quản lý sách** từ menu chính                            |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách sách**     | Table        | Mã sách, tên, tác giả... | Hiển thị thông tin sách              |
| **Bộ lọc**            | Filter       | Thể loại, trạng thái... | Lọc sách theo tiêu chí               |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Prevent duplicate codes**: Kiểm tra và ngăn chặn mã sách/ISBN trùng lặp trước khi thêm vào hệ thống
2. **Real-time validation**: Kiểm tra duplicate code ngay khi người dùng nhập để phản hồi ngay lập tức
3. **Case insensitive check**: Kiểm tra không phân biệt hoa thường để đảm bảo mã sách thực sự duy nhất
4. **Transaction safety**: Sử dụng database transaction để đảm bảo tính toàn vẹn dữ liệu và rollback nếu có lỗi
5. **UI cải thiện**: Hiển thị thông báo rõ ràng khi mã sách trùng lặp hoặc hợp lệ
6. **Error handling**: Xử lý lỗi transaction và thông báo rollback cho người dùng

