# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng vận chuyển của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng vận chuyển](#1-chức-năng-vận-chuyển)
   - 1.1 [Chọn đơn vị vận chuyển](#11-chọn-đơn-vị-vận-chuyển) - **ĐÃ SỬA**
   - 1.2 [Theo dõi vận chuyển](#12-theo-dõi-vận-chuyển)
   - 1.3 [Tính phí vận chuyển](#13-tính-phí-vận-chuyển)

---

## 1. CHỨC NĂNG VẬN CHUYỂN

### 1.1 CHỌN ĐƠN VỊ VẬN CHUYỂN - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Chọn đơn vị vận chuyển                                                                     |
| ------------- | ------------------------------------------------------------------------------------------ |
| Description   | Cho phép người dùng chọn đơn vị vận chuyển cho đơn hàng với validation chỉ 1 carrier/order |
| Screen Access | Hiển thị trong trang thanh toán, phần chọn đơn vị vận chuyển                               |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                         | Type   | Data                                                    | Description                                  |
| ---------------------------- | ------ | ------------------------------------------------------- | -------------------------------------------- |
| **Select đơn vị vận chuyển** | Select | Viettel Post, GHN, J&T Express...                       | **MỚI**: Dropdown chọn đơn vị vận chuyển     |
| **Thông báo giới hạn**       | Text   | ⚠️ Chỉ có thể chọn 1 đơn vị vận chuyển cho mỗi đơn hàng | **MỚI**: Cảnh báo chỉ 1 carrier/order        |
| **Badge đã chọn**            | Badge  | Đã chọn: Viettel Post                                   | **MỚI**: Hiển thị carrier đã chọn            |
| **Thông báo lỗi**            | Alert  | Chỉ có thể chọn 1 đơn vị vận chuyển                     | **MỚI**: Thông báo khi cố chọn nhiều carrier |

#### 1.1.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                                             | Success                                                              | Failure                                                          |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Chọn đơn vị vận chuyển**   | Cho phép người dùng chọn đơn vị vận chuyển cho đơn hàng. Hệ thống chỉ cho phép chọn 1 đơn vị vận chuyển cho mỗi đơn hàng.                                                                                               | Đơn vị vận chuyển được chọn thành công. Hiển thị thông báo xác nhận. | Cố gắng chọn nhiều đơn vị vận chuyển. Hiển thị thông báo lỗi.    |
| **Validation chỉ 1 carrier** | **MỚI**: Hệ thống kiểm tra và đảm bảo chỉ cho phép chọn 1 đơn vị vận chuyển cho mỗi đơn hàng. Nếu người dùng cố gắng chọn carrier khác, hệ thống sẽ tự động thay thế carrier cũ bằng carrier mới và hiển thị thông báo. | Chỉ 1 carrier được chọn. Carrier cũ được thay thế bằng carrier mới.  | Không thể kiểm tra validation. Nhiều carrier được chọn cùng lúc. |
| **UI control**               | **MỚI**: Trong UI, hệ thống sử dụng Radio button hoặc Select (single choice) để đảm bảo chỉ có thể chọn 1 carrier. Không cho phép multiple selection.                                                                   | UI chỉ cho phép chọn 1 carrier. Validation được thực hiện chính xác. | UI cho phép chọn nhiều carrier. Validation không hoạt động.      |
| **Thông báo rõ ràng**        | **MỚI**: Hệ thống hiển thị thông báo rõ ràng: "Chỉ có thể chọn 1 đơn vị vận chuyển cho mỗi đơn hàng" để người dùng biết quy tắc.                                                                                        | Thông báo được hiển thị rõ ràng. Người dùng hiểu quy tắc.            | Thông báo không rõ ràng. Người dùng không hiểu quy tắc.          |

#### 1.1.4 Validation Rules (MỚI):

| Field          | Rule                                             | Error Message                                          |
| -------------- | ------------------------------------------------ | ------------------------------------------------------ |
| **Carrier**    | Chỉ cho phép chọn 1 carrier cho mỗi đơn hàng     | "Chỉ có thể chọn 1 đơn vị vận chuyển cho mỗi đơn hàng" |
| **UI Control** | Sử dụng Radio button hoặc Select (single choice) | -                                                      |

---

### 1.2 THEO DÕI VẬN CHUYỂN

#### 1.2.1 Thông tin màn hình:

| Screen        | Theo dõi vận chuyển                                       |
| ------------- | --------------------------------------------------------- |
| Description   | Hiển thị trạng thái và lịch trình vận chuyển của đơn hàng |
| Screen Access | Người dùng chọn **Theo dõi vận chuyển** từ trang đơn hàng |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                    | Type     | Data             | Description                     |
| ----------------------- | -------- | ---------------- | ------------------------------- |
| **Timeline vận chuyển** | Timeline | Các mốc cập nhật | Hiển thị lịch trình vận chuyển  |
| **Mã vận đơn**          | Text     | GHN123456789     | Mã vận đơn từ đơn vị vận chuyển |

---

### 1.3 TÍNH PHÍ VẬN CHUYỂN

#### 1.3.1 Thông tin màn hình:

| Screen        | Tính phí vận chuyển                                                  |
| ------------- | -------------------------------------------------------------------- |
| Description   | Ước tính phí vận chuyển dựa trên trọng lượng, khoảng cách và carrier |
| Screen Access | Hiển thị trong trang thanh toán, phần tính phí vận chuyển            |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                   | Type   | Data                       | Description                      |
| ---------------------- | ------ | -------------------------- | -------------------------------- |
| **Input trọng lượng**  | Input  | 0.5 kg                     | Ô nhập trọng lượng               |
| **Select khoảng cách** | Select | Nội thành, Liên tỉnh...    | Dropdown chọn khoảng cách        |
| **Select carrier**     | Select | Viettel Post, GHN...       | Dropdown chọn carrier (chỉ 1)    |
| **Kết quả**            | Text   | Phí vận chuyển: 35.000 VNĐ | Hiển thị phí vận chuyển ước tính |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Validation chỉ 1 carrier**: Chỉ cho phép chọn 1 đơn vị vận chuyển cho mỗi đơn hàng
2. **UI control**: Sử dụng Radio button hoặc Select (single choice) để đảm bảo chỉ 1 carrier
3. **Thông báo rõ ràng**: Hiển thị thông báo "Chỉ có thể chọn 1 đơn vị vận chuyển cho mỗi đơn hàng"
4. **Auto-replace**: Tự động thay thế carrier cũ bằng carrier mới nếu chọn carrier khác
5. **Error handling**: Hiển thị thông báo lỗi nếu cố gắng chọn nhiều carrier
