# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng bộ lọc sách của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng bộ lọc sách](#1-chức-năng-bộ-lọc-sách)
   - 1.1 [Bộ lọc theo giá](#11-bộ-lọc-theo-giá) - **ĐÃ SỬA**
   - 1.2 [Bộ lọc theo thể loại](#12-bộ-lọc-theo-thể-loại)
   - 1.3 [Bộ lọc theo nhà xuất bản](#13-bộ-lọc-theo-nhà-xuất-bản)
   - 1.4 [Bộ lọc theo đánh giá](#14-bộ-lọc-theo-đánh-giá)

---

## 1. CHỨC NĂNG BỘ LỌC SÁCH

### 1.1 BỘ LỌC THEO GIÁ - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Bộ lọc theo khoảng giá                                                      |
| ------------- | --------------------------------------------------------------------------- |
| Description   | Cho phép người dùng lọc sách theo khoảng giá từ giá tối thiểu đến giá tối đa |
| Screen Access | Hiển thị trong panel bộ lọc bên trái trang danh sách sách                   |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                          | Description                                    |
| --------------------- | ------------ | ----------------------------- | ---------------------------------------------- |
| **Slider giá**        | Range Slider | Từ 0 đến 10.000.000 VNĐ        | **MỚI**: Slider với min=0, max=10M           |
| **Giá tối thiểu**     | Text         | Từ: 0 VNĐ                     | **MỚI**: Hiển thị giá tối thiểu đã chọn       |
| **Giá tối đa**        | Text         | Đến: 10.000.000 VNĐ            | **MỚI**: Hiển thị giá tối đa đã chọn          |
| **Thông báo giới hạn** | Text         | Giá từ 0 đến 10.000.000 VNĐ    | **MỚI**: Hiển thị phạm vi giá hợp lệ          |
| **Nút áp dụng**       | Button       | Áp dụng                       | Nút để áp dụng bộ lọc giá                      |

#### 1.1.3 Hành động và xử lý:

| Action Name          | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Lọc theo giá**     | Cho phép người dùng chọn khoảng giá để lọc sách. Hệ thống sẽ hiển thị các sách có giá trong khoảng đã chọn.                                                                                                                                | Kết quả được lọc thành công theo khoảng giá đã chọn.                                      | Không có sách nào trong khoảng giá đã chọn.                                               |
| **Validation giá**   | **MỚI**: Hệ thống kiểm tra và đảm bảo giá tối thiểu >= 0, giá tối đa <= 10.000.000 VNĐ, và giá tối thiểu <= giá tối đa. Nếu không hợp lệ, hệ thống sẽ tự động điều chỉnh hoặc hiển thị thông báo lỗi.                                    | Giá được validate thành công và áp dụng bộ lọc.                                            | Giá không hợp lệ (âm, quá lớn, hoặc min > max). Hiển thị thông báo lỗi cụ thể.            |
| **Tự động điều chỉnh** | **MỚI**: Nếu người dùng nhập giá âm, hệ thống tự động đặt về 0. Nếu giá tối đa vượt quá 10M, hệ thống tự động đặt về 10M.                                                                                                                  | Giá được tự động điều chỉnh về phạm vi hợp lệ.                                             | Lỗi khi điều chỉnh giá.                                                                    |
| **Reset bộ lọc**     | Người dùng có thể reset bộ lọc giá về mặc định (0 - 10.000.000 VNĐ).                                                                                                                                                                       | Bộ lọc được reset về mặc định thành công.                                                  | Lỗi khi reset bộ lọc.                                                                      |

#### 1.1.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Giá tối thiểu** | Phải >= 0, tự động đặt về 0 nếu âm      | "Giá tối thiểu không thể âm"                     |
| **Giá tối đa**  | Phải <= 10.000.000 VNĐ, tự động đặt về 10M nếu vượt | "Giá tối đa không được vượt quá 10.000.000 VNĐ" |
| **Khoảng giá**  | Giá tối thiểu phải <= giá tối đa        | "Giá tối thiểu không thể lớn hơn giá tối đa"     |

---

### 1.2 BỘ LỌC THEO THỂ LOẠI

#### 1.2.1 Thông tin màn hình:

| Screen        | Bộ lọc theo thể loại                                    |
| ------------- | ------------------------------------------------------- |
| Description   | Cho phép người dùng lọc sách theo thể loại (Văn học, Khoa học, ...) |
| Screen Access | Hiển thị trong panel bộ lọc bên trái trang danh sách sách |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item              | Type         | Data                    | Description                          |
| ----------------- | ------------ | ----------------------- | ------------------------------------ |
| **Checkbox thể loại** | Checkbox Group | Văn học, Khoa học...    | Danh sách checkbox để chọn thể loại  |
| **Nút xóa lọc**   | Button       | Xóa bộ lọc              | Xóa tất cả lựa chọn thể loại         |

---

### 1.3 BỘ LỌC THEO NHÀ XUẤT BẢN

#### 1.3.1 Thông tin màn hình:

| Screen        | Bộ lọc theo nhà xuất bản                                    |
| ------------- | ------------------------------------------------------------ |
| Description   | Cho phép người dùng lọc sách theo nhà xuất bản               |
| Screen Access | Hiển thị trong panel bộ lọc bên trái trang danh sách sách    |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item              | Type         | Data                    | Description                          |
| ----------------- | ------------ | ----------------------- | ------------------------------------ |
| **Select NXB**     | Select       | Chọn nhà xuất bản       | Dropdown để chọn nhà xuất bản        |

---

### 1.4 BỘ LỌC THEO ĐÁNH GIÁ

#### 1.4.1 Thông tin màn hình:

| Screen        | Bộ lọc theo đánh giá                                        |
| ------------- | ------------------------------------------------------------ |
| Description   | Cho phép người dùng lọc sách theo điểm đánh giá (4 sao trở lên, ...) |
| Screen Access | Hiển thị trong panel bộ lọc bên trái trang danh sách sách    |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item              | Type         | Data                    | Description                          |
| ----------------- | ------------ | ----------------------- | ------------------------------------ |
| **Radio đánh giá** | Radio Group  | 4 sao trở lên, 3 sao... | Radio button để chọn mức đánh giá    |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Validation giá**: Thêm validation đảm bảo giá >= 0 và <= 10.000.000 VNĐ
2. **Tự động điều chỉnh**: Tự động điều chỉnh giá về phạm vi hợp lệ nếu người dùng nhập sai
3. **Thông báo lỗi rõ ràng**: Hiển thị thông báo lỗi cụ thể cho từng trường hợp validation
4. **Giới hạn hợp lý**: Đặt giới hạn giá tối đa 10.000.000 VNĐ để tránh giá không hợp lý
5. **UI cải thiện**: Hiển thị rõ ràng giá tối thiểu và tối đa, kèm thông báo phạm vi hợp lệ

