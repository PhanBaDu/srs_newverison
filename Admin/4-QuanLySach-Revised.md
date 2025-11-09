# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý sách của Admin (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý sách](#1-chức-năng-quản-lý-sách)
   - 1.1 [Thiết lập giá sách](#11-thiết-lập-giá-sách) - **ĐÃ SỬA**
   - 1.2 [Thay đổi trạng thái sách](#12-thay-đổi-trạng-thái-sách) - **ĐÃ SỬA**
   - 1.3 [Xem lịch sử thay đổi](#13-xem-lịch-sử-thay-đổi) - **MỚI**

---

## 1. CHỨC NĂNG QUẢN LÝ SÁCH

### 1.1 THIẾT LẬP GIÁ SÁCH - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Thiết lập giá sách                                                      |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Cho phép Admin thay đổi giá bán của sách với ghi nhận versioning        |
| Screen Access | Admin chọn **Quản lý sách** từ menu và click **Chỉnh sửa** trên sách   |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Input giá hiện tại**    | Input        | 150.000 VNĐ (readonly)                  | Hiển thị giá hiện tại                          |
| **Input giá mới**         | Input (Number) | Nhập giá mới                           | **MỚI**: Ô nhập giá mới                        |
| **Textarea lý do**        | Textarea     | Nhập lý do thay đổi giá (tùy chọn)      | **MỚI**: Ô nhập lý do thay đổi                 |
| **Nút lưu**               | Button       | Lưu thay đổi                            | Nút để lưu giá mới                              |
| **Bảng lịch sử giá**      | Table        | Thời gian, Giá cũ, Giá mới, Người thay đổi | **MỚI**: Hiển thị lịch sử thay đổi giá        |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Thay đổi giá sách**    | Cho phép Admin thay đổi giá bán của sách. Hệ thống sẽ kiểm tra tính hợp lệ của giá mới và ghi nhận vào versioning history trước khi cập nhật.                                                                                              | Giá được cập nhật thành công. Versioning history được ghi nhận với đầy đủ thông tin.     | Giá mới không hợp lệ (âm hoặc quá lớn). Không thể ghi nhận versioning history.             |
| **Ghi nhận versioning**  | **MỚI**: Mỗi khi Admin thay đổi giá sách, hệ thống tự động ghi nhận vào versioning history với thông tin: thời gian, giá cũ, giá mới, người thay đổi (Admin), và lý do (nếu có). Versioning history được lưu vĩnh viễn và không thể xóa. | Versioning history được ghi nhận thành công với đầy đủ thông tin.                         | Không thể ghi nhận versioning history. Thông tin versioning không đầy đủ.                  |
| **Validation giá**       | Hệ thống kiểm tra giá mới phải là số dương và trong phạm vi hợp lý (ví dụ: 0 < giá <= 50.000.000 VNĐ).                                                                                                                                    | Giá được validate thành công và được cập nhật.                                             | Giá không hợp lệ. Hiển thị thông báo lỗi cụ thể.                                          |

#### 1.1.4 Versioning Schema (MỚI):

| Field              | Type     | Description                                    |
| ------------------ | -------- | ---------------------------------------------- |
| **ID**             | String   | Mã định danh duy nhất của version entry        |
| **Product ID**     | Number   | Mã sản phẩm bị thay đổi                        |
| **Old Price**      | Number   | Giá cũ trước khi thay đổi                      |
| **New Price**      | Number   | Giá mới sau khi thay đổi                       |
| **Changed By**     | String   | Tên Admin thực hiện thay đổi                    |
| **Changed At**     | DateTime | Thời gian thực hiện thay đổi                   |
| **Reason**         | String   | Lý do thay đổi (tùy chọn)                      |

---

### 1.2 THAY ĐỔI TRẠNG THÁI SÁCH - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Thay đổi trạng thái sách                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Cho phép Admin thay đổi trạng thái sách (Đang bán, Hết hàng, Ngừng bán) với ghi nhận versioning |
| Screen Access | Admin chọn **Quản lý sách** từ menu và click **Chỉnh sửa** trên sách         |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Select trạng thái hiện tại** | Select    | Đang bán (readonly)                     | Hiển thị trạng thái hiện tại                   |
| **Select trạng thái mới** | Select        | Đang bán, Hết hàng, Ngừng bán, Ẩn       | **MỚI**: Dropdown chọn trạng thái mới          |
| **Textarea lý do**        | Textarea     | Nhập lý do thay đổi trạng thái (tùy chọn) | **MỚI**: Ô nhập lý do thay đổi                |
| **Nút lưu**               | Button       | Lưu thay đổi                             | Nút để lưu trạng thái mới                      |
| **Bảng lịch sử trạng thái** | Table      | Thời gian, Trạng thái cũ, Trạng thái mới, Người thay đổi | **MỚI**: Hiển thị lịch sử thay đổi trạng thái |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Thay đổi trạng thái**  | Cho phép Admin thay đổi trạng thái sách. Hệ thống sẽ ghi nhận vào versioning history trước khi cập nhật.                                                                                                                                    | Trạng thái được cập nhật thành công. Versioning history được ghi nhận với đầy đủ thông tin. | Không thể cập nhật trạng thái. Không thể ghi nhận versioning history.                      |
| **Ghi nhận versioning**  | **MỚI**: Mỗi khi Admin thay đổi trạng thái sách, hệ thống tự động ghi nhận vào versioning history với thông tin: thời gian, trạng thái cũ, trạng thái mới, người thay đổi (Admin), và lý do (nếu có). Versioning history được lưu vĩnh viễn. | Versioning history được ghi nhận thành công với đầy đủ thông tin.                          | Không thể ghi nhận versioning history. Thông tin versioning không đầy đủ.                   |

#### 1.2.4 Status Versioning Schema (MỚI):

| Field              | Type     | Description                                    |
| ------------------ | -------- | ---------------------------------------------- |
| **ID**             | String   | Mã định danh duy nhất của version entry        |
| **Product ID**     | Number   | Mã sản phẩm bị thay đổi                        |
| **Old Status**     | String   | Trạng thái cũ trước khi thay đổi              |
| **New Status**     | String   | Trạng thái mới sau khi thay đổi               |
| **Changed By**     | String   | Tên Admin thực hiện thay đổi                  |
| **Changed At**     | DateTime | Thời gian thực hiện thay đổi                  |
| **Reason**         | String   | Lý do thay đổi (tùy chọn)                      |

---

### 1.3 XEM LỊCH SỬ THAY ĐỔI - **MỚI**

#### 1.3.1 Thông tin màn hình:

| Screen        | Lịch sử thay đổi giá và trạng thái                                                      |
| ------------- | --------------------------------------------------------------------------------------- |
| Description   | Hiển thị lịch sử tất cả các thay đổi về giá và trạng thái của sách                     |
| Screen Access | Hiển thị trong trang chi tiết sách, tab **Lịch sử thay đổi**                            |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Tabs lịch sử**      | Tabs         | Lịch sử giá, Lịch sử trạng thái         | Tabs để chuyển đổi giữa các loại lịch sử       |
| **Bảng lịch sử giá** | Table        | Thời gian, Giá cũ, Giá mới, Người thay đổi, Lý do | Hiển thị lịch sử thay đổi giá                |
| **Bảng lịch sử trạng thái** | Table   | Thời gian, Trạng thái cũ, Trạng thái mới, Người thay đổi, Lý do | Hiển thị lịch sử thay đổi trạng thái         |
| **Bộ lọc**            | Filter       | Thời gian, Người thay đổi                | Lọc lịch sử theo tiêu chí                      |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem lịch sử giá**      | Cho phép Admin xem lịch sử tất cả các thay đổi về giá của sách. Hiển thị đầy đủ thông tin về từng lần thay đổi để đảm bảo tính minh bạch và trách nhiệm.                                                                                  | Lịch sử giá được hiển thị thành công với đầy đủ thông tin.                                 | Không thể tải lịch sử giá. Thông tin lịch sử không đầy đủ.                                |
| **Xem lịch sử trạng thái** | Cho phép Admin xem lịch sử tất cả các thay đổi về trạng thái của sách. Hiển thị đầy đủ thông tin về từng lần thay đổi.                                                                                                                  | Lịch sử trạng thái được hiển thị thành công với đầy đủ thông tin.                          | Không thể tải lịch sử trạng thái. Thông tin lịch sử không đầy đủ.                          |
| **Lọc lịch sử**          | Admin có thể lọc lịch sử theo thời gian hoặc người thay đổi để tìm kiếm dễ dàng hơn.                                                                                                                                    | Lịch sử được lọc thành công theo tiêu chí đã chọn.                                         | Không thể lọc lịch sử. Kết quả lọc không chính xác.                                       |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Versioning cho giá**: Thêm hệ thống ghi nhận versioning cho mọi thay đổi về giá sách
2. **Versioning cho trạng thái**: Thêm hệ thống ghi nhận versioning cho mọi thay đổi về trạng thái sách
3. **Lịch sử đầy đủ**: Ghi nhận đầy đủ thông tin: thời gian, giá/trạng thái cũ, giá/trạng thái mới, người thay đổi, lý do
4. **Lưu vĩnh viễn**: Versioning history được lưu vĩnh viễn và không thể xóa để đảm bảo tính minh bạch
5. **UI cải thiện**: Thêm tab "Lịch sử thay đổi" trong trang chi tiết sách để Admin có thể xem versioning history
6. **Bộ lọc**: Cho phép lọc lịch sử theo thời gian và người thay đổi để tìm kiếm dễ dàng hơn

