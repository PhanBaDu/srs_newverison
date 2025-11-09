# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng yêu cầu nhập hàng của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng yêu cầu nhập hàng](#1-chức-năng-yêu-cầu-nhập-hàng)
   - 1.1 [Gửi yêu cầu nhập hàng](#11-gửi-yêu-cầu-nhập-hàng) - **ĐÃ SỬA**
   - 1.2 [Xem danh sách yêu cầu](#12-xem-danh-sách-yêu-cầu)
   - 1.3 [Hủy yêu cầu](#13-hủy-yêu-cầu)

---

## 1. CHỨC NĂNG YÊU CẦU NHẬP HÀNG

### 1.1 GỬI YÊU CẦU NHẬP HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Gửi yêu cầu nhập hàng                                                      |
| ------------- | -------------------------------------------------------------------------- |
| Description   | Cho phép người dùng gửi yêu cầu nhập hàng cho sách chưa có trong hệ thống  |
| Screen Access | Người dùng chọn **Yêu cầu nhập hàng** từ menu chính                        |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Form yêu cầu**          | Form         | Tên sản phẩm, link, mô tả               | Form để nhập thông tin yêu cầu                 |
| **Input tên sản phẩm**    | Input        | Nhập tên sản phẩm *                     | **MỚI**: Validation bắt buộc                  |
| **Input link**            | Input        | https://...                             | Ô nhập link sản phẩm (nếu có)                  |
| **Textarea mô tả**       | Textarea     | Phiên bản, màu sắc, kích thước...      | Ô nhập mô tả chi tiết                           |
| **Thông báo giới hạn**    | Alert        | ⚠️ Đã đạt giới hạn 5 yêu cầu/tuần      | **MỚI**: Cảnh báo khi đạt weekly limit         |
| **Nút gửi yêu cầu**       | Button       | Gửi yêu cầu (X/5 tuần này)             | **MỚI**: Hiển thị số lượng đã dùng/tối đa      |
| **Thông báo lỗi**         | Toast        | Đã đạt giới hạn 5 yêu cầu/tuần         | **MỚI**: Thông báo khi không thể gửi do giới hạn |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Gửi yêu cầu nhập hàng** | Cho phép người dùng gửi yêu cầu nhập hàng cho sách chưa có trong hệ thống. Hệ thống sẽ kiểm tra tính hợp lệ của yêu cầu và lưu vào cơ sở dữ liệu.                                                                                        | Yêu cầu được gửi thành công và chờ xử lý.                                                  | Yêu cầu không hợp lệ. Lỗi khi lưu yêu cầu.                                                 |
| **Kiểm tra weekly limit** | **MỚI**: Hệ thống kiểm tra số lượng yêu cầu đã gửi trong tuần hiện tại của người dùng. Tối đa 5 yêu cầu mỗi tuần. Nếu đã đạt giới hạn, hệ thống sẽ từ chối và thông báo người dùng đợi đến tuần sau.                                        | Số lượng yêu cầu trong tuần chưa đạt giới hạn. Yêu cầu được chấp nhận.                    | Đã đạt giới hạn 5 yêu cầu/tuần. Hiển thị: "Bạn đã đạt giới hạn 5 yêu cầu mỗi tuần..."     |
| **Tính toán tuần**       | **MỚI**: Hệ thống tính toán tuần hiện tại dựa trên ngày hiện tại (từ thứ 2 đến chủ nhật). Tất cả yêu cầu trong tuần này sẽ được đếm để kiểm tra giới hạn.                                                                                  | Tuần được tính toán chính xác. Số lượng yêu cầu được đếm đúng.                            | Lỗi khi tính toán tuần. Số lượng yêu cầu không được đếm đúng.                             |
| **Reset weekly limit**   | **MỚI**: Mỗi tuần mới (thứ 2), hệ thống tự động reset số lượng yêu cầu về 0, cho phép người dùng gửi lại 5 yêu cầu mới.                                                                                                                    | Weekly limit được reset thành công mỗi tuần mới.                                          | Lỗi khi reset weekly limit. Người dùng không thể gửi yêu cầu mới.                          |
| **Hiển thị số lượng**    | **MỚI**: Hệ thống hiển thị số lượng yêu cầu đã dùng/tối đa (X/5) trên nút gửi yêu cầu để người dùng biết còn bao nhiêu slot trống.                                                                                                         | Số lượng được hiển thị chính xác và cập nhật real-time.                                    | Số lượng không được hiển thị hoặc hiển thị sai.                                           |

#### 1.1.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Tên sản phẩm** | Bắt buộc, tối thiểu 2 ký tự             | "Vui lòng nhập tên sản phẩm"                     |
| **Weekly limit** | Tối đa 5 yêu cầu/tuần                   | "Bạn đã đạt giới hạn 5 yêu cầu mỗi tuần. Vui lòng đợi đến tuần sau để gửi yêu cầu mới." |
| **Tuần**        | Tính từ thứ 2 đến chủ nhật              | -                                                |

#### 1.1.5 Weekly Limit Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Weekly Limit**    | Tối đa 5 yêu cầu mỗi tuần cho mỗi người dùng                               | Từ chối yêu cầu và thông báo người dùng   |
| **Week Calculation** | Tuần được tính từ thứ 2 đến chủ nhật                                       | Đếm số lượng yêu cầu trong tuần hiện tại  |
| **Auto Reset**      | Tự động reset về 0 mỗi tuần mới (thứ 2)                                    | Cho phép người dùng gửi lại 5 yêu cầu mới |

---

### 1.2 XEM DANH SÁCH YÊU CẦU

#### 1.2.1 Thông tin màn hình:

| Screen        | Danh sách yêu cầu nhập hàng                                                      |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách các yêu cầu nhập hàng đã gửi và trạng thái xử lý             |
| Screen Access | Hiển thị trong trang **Yêu cầu nhập hàng**, phần danh sách yêu cầu               |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách yêu cầu** | List/Table   | Yêu cầu + trạng thái    | Hiển thị các yêu cầu đã gửi          |
| **Bộ lọc**            | Filter       | Tất cả, Chờ xử lý, Đã duyệt | Lọc yêu cầu theo trạng thái          |
| **Badge trạng thái**  | Badge        | Chờ xử lý, Đã duyệt...  | Hiển thị trạng thái yêu cầu          |

---

### 1.3 HỦY YÊU CẦU

#### 1.3.1 Thông tin màn hình:

| Screen        | Hủy yêu cầu nhập hàng                                                      |
| ------------- | -------------------------------------------------------------------------- |
| Description   | Cho phép người dùng hủy yêu cầu nhập hàng đang chờ xử lý                   |
| Screen Access | Người dùng click nút **Hủy yêu cầu** từ danh sách yêu cầu                  |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Nút hủy**           | Button       | Hủy yêu cầu             | Nút để hủy yêu cầu                    |
| **Dialog xác nhận**   | Dialog       | Bạn có chắc muốn hủy?   | Dialog xác nhận trước khi hủy         |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Weekly limit**: Giới hạn 5 yêu cầu mỗi tuần để tránh spam
2. **Week calculation**: Tính toán tuần từ thứ 2 đến chủ nhật
3. **Auto reset**: Tự động reset weekly limit mỗi tuần mới
4. **Hiển thị số lượng**: Hiển thị số lượng đã dùng/tối đa (X/5) trên nút gửi
5. **Thông báo rõ ràng**: Hiển thị cảnh báo khi đạt giới hạn và hướng dẫn đợi tuần sau
6. **Validation**: Kiểm tra weekly limit trước khi cho phép gửi yêu cầu mới

