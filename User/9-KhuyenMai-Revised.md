# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng khuyến mãi của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng khuyến mãi](#1-chức-năng-khuyến-mãi)
   - 1.1 [Xem danh sách mã giảm giá](#11-xem-danh-sách-mã-giảm-giá) - **ĐÃ SỬA**
   - 1.2 [Áp dụng mã giảm giá](#12-áp-dụng-mã-giảm-giá) - **ĐÃ SỬA**
   - 1.3 [Xem chi tiết mã giảm giá](#13-xem-chi-tiết-mã-giảm-giá)

---

## 1. CHỨC NĂNG KHUYẾN MÃI

### 1.1 XEM DANH SÁCH MÃ GIẢM GIÁ - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách mã giảm giá                                                      |
| ------------- | -------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách các mã giảm giá có sẵn với priority rule khi multiple codes |
| Screen Access | Người dùng chọn **Khuyến mãi** từ menu chính                               |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Alert priority rule**   | Alert        | Quy tắc ưu tiên: Chỉ 1 mã/đơn hàng     | **MỚI**: Hiển thị quy tắc ưu tiên              |
| **Card mã giảm giá**      | Card         | Mã code, loại, giá trị, điều kiện...    | Hiển thị thông tin mã giảm giá                 |
| **Badge đã chọn**         | Badge        | Đã chọn                                 | **MỚI**: Hiển thị mã đã chọn                   |
| **Text giá trị ước tính** | Text         | Giá trị ước tính: 200.000 VNĐ           | **MỚI**: Hiển thị giá trị thực tế của mã        |
| **Nút sử dụng ngay**         | Button       | Sử dụng ngay / Đã chọn                   | **MỚI**: Thay đổi text theo trạng thái        |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Chọn mã giảm giá**     | Cho phép người dùng chọn mã giảm giá để áp dụng cho đơn hàng. Hệ thống chỉ cho phép chọn 1 mã giảm giá cho mỗi đơn hàng. Nếu chọn nhiều mã, hệ thống sẽ tự động chọn mã có giá trị cao nhất.                                                  | Mã giảm giá được chọn thành công. Hiển thị giá trị ước tính.                              | Không thể chọn mã giảm giá. Lỗi khi tính toán giá trị.                                     |
| **Priority rule**        | **MỚI**: Khi người dùng chọn nhiều mã giảm giá, hệ thống tự động so sánh giá trị thực tế của từng mã (tính theo % hoặc số tiền cố định) và chọn mã có giá trị cao nhất. Mã có giá trị thấp hơn sẽ bị bỏ chọn.                                  | Mã có giá trị cao nhất được tự động chọn. Người dùng được thông báo rõ ràng.                | Không thể so sánh giá trị. Mã không được chọn đúng.                                         |
| **Tính giá trị thực tế** | **MỚI**: Hệ thống tính giá trị thực tế của từng mã giảm giá dựa trên tổng tiền đơn hàng. Đối với mã giảm %: giá trị = (tổng tiền * % giảm) / 100. Đối với mã giảm cố định: giá trị = số tiền giảm. Sau đó so sánh và chọn mã có giá trị cao nhất. | Giá trị thực tế được tính chính xác. Mã có giá trị cao nhất được chọn.                    | Không thể tính giá trị thực tế. So sánh không chính xác.                                    |
| **Thông báo rõ ràng**    | **MỚI**: Khi người dùng chọn mã có giá trị thấp hơn mã đã chọn, hệ thống hiển thị thông báo: "Mã [code] có giá trị thấp hơn mã đã chọn. Chỉ có thể áp dụng 1 mã giảm giá." Khi chọn mã có giá trị cao hơn, hệ thống tự động thay thế và thông báo: "Đã chọn mã [code] (giá trị cao hơn: [value])". | Thông báo được hiển thị rõ ràng. Người dùng hiểu quy tắc ưu tiên.                          | Thông báo không rõ ràng. Người dùng không hiểu quy tắc.                                      |

#### 1.1.4 Priority Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Single Code Rule** | Chỉ cho phép áp dụng 1 mã giảm giá cho mỗi đơn hàng                        | Từ chối nếu cố chọn nhiều mã              |
| **Value Comparison** | So sánh giá trị thực tế của các mã (tính theo tổng tiền đơn hàng)          | Chọn mã có giá trị cao nhất                |
| **Auto Selection**  | Tự động chọn mã có giá trị cao nhất nếu chọn nhiều mã                      | Thay thế mã cũ bằng mã mới có giá trị cao hơn |
| **User Notification** | Thông báo rõ ràng về mã được chọn và lý do                                  | Hiển thị giá trị ước tính và thông báo    |

#### 1.1.5 Calculation Example (MỚI):

| Order Total | Code 1 (10%) | Code 2 (50K) | Code 3 (20%) | Selected Code |
| ----------- | ------------- | ------------ | ------------ | ------------- |
| 500.000 VNĐ | 50.000 VNĐ    | 50.000 VNĐ   | 100.000 VNĐ  | Code 3        |
| 300.000 VNĐ | 30.000 VNĐ    | 50.000 VNĐ   | 60.000 VNĐ   | Code 3        |
| 400.000 VNĐ | 40.000 VNĐ    | 50.000 VNĐ   | 80.000 VNĐ   | Code 3        |

---

### 1.2 ÁP DỤNG MÃ GIẢM GIÁ - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Áp dụng mã giảm giá                                                      |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Cho phép người dùng áp dụng mã giảm giá đã chọn cho đơn hàng              |
| Screen Access | Hiển thị trong trang thanh toán, phần áp dụng mã giảm giá                |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Input mã giảm giá** | Input        | Nhập mã giảm giá                        | Ô nhập mã giảm giá                              |
| **Nút áp dụng**       | Button       | Áp dụng                                 | Nút để áp dụng mã giảm giá                     |
| **Thông tin giảm giá** | Text         | Giảm: 50.000 VNĐ                        | **MỚI**: Hiển thị giá trị thực tế              |
| **Alert priority**    | Alert        | Chỉ có thể áp dụng 1 mã giảm giá        | **MỚI**: Cảnh báo khi cố áp dụng nhiều mã      |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Áp dụng mã giảm giá** | Cho phép người dùng áp dụng mã giảm giá đã chọn cho đơn hàng. Hệ thống sẽ tính toán giá trị giảm giá và cập nhật tổng tiền đơn hàng.                                                                                                      | Mã giảm giá được áp dụng thành công. Tổng tiền được cập nhật.                              | Mã giảm giá không hợp lệ. Mã đã hết hạn. Mã không áp dụng được cho đơn hàng này.          |
| **Validation chỉ 1 mã** | **MỚI**: Hệ thống kiểm tra và đảm bảo chỉ cho phép áp dụng 1 mã giảm giá cho mỗi đơn hàng. Nếu người dùng cố gắng áp dụng mã thứ 2, hệ thống sẽ từ chối và thông báo: "Chỉ có thể áp dụng 1 mã giảm giá cho mỗi đơn hàng. Vui lòng bỏ mã cũ trước khi áp dụng mã mới." | Chỉ 1 mã được áp dụng. Validation hoạt động chính xác.                                    | Nhiều mã được áp dụng cùng lúc. Validation không hoạt động.                                |

---

### 1.3 XEM CHI TIẾT MÃ GIẢM GIÁ

#### 1.3.1 Thông tin màn hình:

| Screen        | Chi tiết mã giảm giá                                                      |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Hiển thị thông tin chi tiết về mã giảm giá                               |
| Screen Access | Người dùng click **Chi tiết** từ danh sách mã giảm giá                   |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Thông tin mã**      | Card         | Mã code, loại, giá trị... | Hiển thị chi tiết mã giảm giá        |
| **Điều kiện áp dụng** | Text         | Đơn hàng tối thiểu...   | Hiển thị điều kiện áp dụng            |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Priority rule**: Tự động chọn mã có giá trị cao nhất khi chọn nhiều mã
2. **Value calculation**: Tính giá trị thực tế của từng mã dựa trên tổng tiền đơn hàng
3. **Single code enforcement**: Chỉ cho phép áp dụng 1 mã giảm giá cho mỗi đơn hàng
4. **Auto-selection**: Tự động thay thế mã cũ bằng mã mới có giá trị cao hơn
5. **User notification**: Hiển thị giá trị ước tính và thông báo rõ ràng về mã được chọn
6. **UI cải thiện**: Thêm badge "Đã chọn" và hiển thị giá trị ước tính cho mỗi mã

