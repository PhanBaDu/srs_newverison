# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng danh sách sách yêu thích của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng danh sách sách yêu thích](#1-chức-năng-danh-sách-sách-yêu-thích)
   - 1.1 [Xem danh sách yêu thích](#11-xem-danh-sách-yêu-thích) - **ĐÃ SỬA**
   - 1.2 [Thêm sách vào yêu thích](#12-thêm-sách-vào-yêu-thích) - **ĐÃ SỬA**
   - 1.3 [Xóa sách khỏi yêu thích](#13-xóa-sách-khỏi-yêu-thích)

---

## 1. CHỨC NĂNG DANH SÁCH SÁCH YÊU THÍCH

### 1.1 XEM DANH SÁCH YÊU THÍCH - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách yêu thích                                                      |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Hiển thị danh sách các sách đã được người dùng đánh dấu yêu thích       |
| Screen Access | Người dùng đã đăng nhập chọn **Yêu thích** từ menu chính                |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Tiêu đề trang**         | Text         | Danh sách yêu thích                     | Tiêu đề chính của trang                        |
| **Thông tin số lượng**    | Text         | X/200 sách trong danh sách yêu thích    | **MỚI**: Hiển thị số lượng hiện tại/tối đa     |
| **Thông báo giới hạn**    | Alert        | ⚠️ Đã đạt giới hạn 200 sách             | **MỚI**: Cảnh báo khi đạt max items            |
| **Danh sách sách**        | Grid/List    | Card sách với hình ảnh, tên, giá...    | Hiển thị các sách trong danh sách yêu thích    |
| **Nút xóa khỏi yêu thích** | Button (Icon) | Heart (filled)                         | Nút để xóa sách khỏi danh sách yêu thích       |
| **Nút thêm vào giỏ hàng** | Button       | Thêm vào giỏ hàng                       | Nút để thêm sách vào giỏ hàng                  |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem danh sách yêu thích** | Hiển thị danh sách tất cả sách đã được đánh dấu yêu thích với thông tin chi tiết như tên, giá, hình ảnh.                                                                                                                                | Danh sách yêu thích được hiển thị thành công với đầy đủ thông tin.                          | Lỗi khi tải danh sách yêu thích do vấn đề kết nối hoặc dữ liệu.                            |
| **Kiểm tra giới hạn**    | **MỚI**: Hệ thống kiểm tra và hiển thị cảnh báo khi danh sách yêu thích đạt giới hạn tối đa 200 sách. Hiển thị số lượng hiện tại/tối đa (X/200) để người dùng biết còn bao nhiêu slot trống.                                                 | Cảnh báo được hiển thị khi đạt giới hạn. Người dùng được thông báo rõ ràng về giới hạn.    | Lỗi khi kiểm tra giới hạn.                                                                 |

---

### 1.2 THÊM SÁCH VÀO YÊU THÍCH - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Thêm sách vào yêu thích                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Cho phép người dùng thêm sách vào danh sách yêu thích từ trang chi tiết sách |
| Screen Access | Người dùng click nút **Yêu thích** (Heart icon) từ trang chi tiết sách       |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút yêu thích**     | Button (Icon) | Heart (outline/filled)                  | Nút để thêm/xóa sách khỏi yêu thích           |
| **Thông báo lỗi**     | Toast        | Đã đạt giới hạn 200 sách                | **MỚI**: Thông báo khi không thể thêm do giới hạn |
| **Thông báo thành công** | Toast      | Đã thêm vào danh sách yêu thích         | Thông báo khi thêm thành công                  |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Thêm sách vào yêu thích** | Cho phép người dùng thêm sách vào danh sách yêu thích. Hệ thống sẽ kiểm tra xem sách đã có trong danh sách chưa và số lượng sách hiện tại trước khi thêm.                                                                              | Sách được thêm vào danh sách yêu thích thành công. Hiển thị thông báo xác nhận.            | Sách đã có trong danh sách. Danh sách đã đạt giới hạn 200 sách. Lỗi khi thêm sách.        |
| **Kiểm tra giới hạn**    | **MỚI**: Trước khi thêm sách, hệ thống kiểm tra xem danh sách yêu thích đã đạt giới hạn 200 sách chưa. Nếu đã đạt, hệ thống sẽ từ chối và hiển thị thông báo lỗi: "Danh sách yêu thích đã đạt giới hạn tối đa 200 sách. Vui lòng xóa bớt sách để thêm mới." | Kiểm tra thành công. Sách được thêm vào nếu chưa đạt giới hạn.                            | Danh sách đã đạt giới hạn. Hiển thị thông báo lỗi cụ thể.                                 |
| **Kiểm tra trùng lặp**   | Hệ thống kiểm tra xem sách đã có trong danh sách yêu thích chưa. Nếu đã có, hệ thống sẽ thông báo và không thêm lại.                                                                                                                      | Kiểm tra thành công. Sách được thêm vào nếu chưa có trong danh sách.                       | Sách đã có trong danh sách. Hiển thị: "Sách đã có trong danh sách yêu thích".              |

#### 1.2.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Số lượng sách** | Tối đa 200 sách trong danh sách yêu thích | "Danh sách yêu thích đã đạt giới hạn tối đa 200 sách. Vui lòng xóa bớt sách để thêm mới." |
| **Trùng lặp**   | Không được thêm sách đã có trong danh sách | "Sách đã có trong danh sách yêu thích"           |

---

### 1.3 XÓA SÁCH KHỎI YÊU THÍCH

#### 1.3.1 Thông tin màn hình:

| Screen        | Xóa sách khỏi yêu thích                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Cho phép người dùng xóa sách khỏi danh sách yêu thích                        |
| Screen Access | Người dùng click nút **Xóa khỏi yêu thích** từ danh sách yêu thích hoặc trang chi tiết sách |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Nút xóa**           | Button (Icon) | Heart (filled) → outline | Nút để xóa sách khỏi yêu thích       |
| **Xác nhận xóa**      | Dialog       | Bạn có chắc muốn xóa?   | Dialog xác nhận trước khi xóa        |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xóa sách khỏi yêu thích** | Cho phép người dùng xóa sách khỏi danh sách yêu thích. Sau khi xóa, người dùng có thể thêm sách mới vào danh sách nếu chưa đạt giới hạn.                                                                                                  | Sách được xóa khỏi danh sách yêu thích thành công. Hiển thị thông báo xác nhận.           | Lỗi khi xóa sách. Sách không tồn tại trong danh sách.                                      |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Giới hạn số lượng**: Tối đa 200 sách trong danh sách yêu thích để tránh quá tải
2. **Hiển thị số lượng**: Hiển thị số lượng hiện tại/tối đa (X/200) để người dùng biết còn bao nhiêu slot
3. **Validation**: Kiểm tra giới hạn trước khi cho phép thêm sách mới
4. **Thông báo rõ ràng**: Hiển thị cảnh báo khi đạt giới hạn và thông báo lỗi cụ thể
5. **UI cải thiện**: Thêm alert box cảnh báo khi đạt giới hạn 200 sách

