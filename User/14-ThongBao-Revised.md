# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng thông báo của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng thông báo](#1-chức-năng-thông-báo)
   - 1.1 [Xem danh sách thông báo](#11-xem-danh-sách-thông-báo) - **ĐÃ SỬA**
   - 1.2 [Đánh dấu đã đọc](#12-đánh-dấu-đã-đọc) - **ĐÃ SỬA**
   - 1.3 [Batch actions](#13-batch-actions) - **ĐÃ SỬA**
   - 1.4 [Lọc thông báo](#14-lọc-thông-báo)

---

## 1. CHỨC NĂNG THÔNG BÁO

### 1.1 XEM DANH SÁCH THÔNG BÁO - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách thông báo                                                      |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả thông báo với read/unread status               |
| Screen Access | Người dùng chọn **Thông báo** từ menu chính                              |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Tiêu đề trang**         | Text         | Thông báo                               | Tiêu đề chính của trang                        |
| **Thông tin số lượng**    | Text         | X thông báo chưa đọc                    | **MỚI**: Hiển thị số lượng thông báo chưa đọc  |
| **Danh sách thông báo**   | List         | Card thông báo với read/unread status   | Hiển thị các thông báo                         |
| **Badge chưa đọc**        | Badge        | Chưa đọc (dot indicator)                | **MỚI**: Hiển thị trạng thái chưa đọc         |
| **Badge đã đọc**          | Badge        | Đã đọc                                  | **MỚI**: Hiển thị trạng thái đã đọc            |
| **Icon loại thông báo**   | Icon         | Package, Percent, Heart, Star...        | Icon đại diện cho loại thông báo               |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem danh sách thông báo** | Hiển thị danh sách tất cả thông báo với trạng thái read/unread. Hệ thống tự động đánh dấu thông báo là đã đọc khi người dùng click vào thông báo.                                                                                      | Danh sách thông báo được hiển thị thành công với đầy đủ thông tin.                         | Không thể tải danh sách thông báo. Trạng thái read/unread không chính xác.                 |
| **Read/unread logic**    | **MỚI**: Hệ thống quản lý trạng thái read/unread cho mỗi thông báo. Khi người dùng click vào thông báo, hệ thống tự động đánh dấu thông báo là đã đọc. Thông báo chưa đọc được hiển thị với badge "Chưa đọc" và dot indicator.            | Trạng thái read/unread được quản lý chính xác. Thông báo được đánh dấu đã đọc khi click.  | Trạng thái read/unread không được quản lý đúng. Thông báo không được đánh dấu đã đọc.       |
| **Visual indicators**    | **MỚI**: Thông báo chưa đọc được hiển thị với border-primary và dot indicator. Thông báo đã đọc được hiển thị với border mặc định và không có dot indicator.                                                                          | Visual indicators được hiển thị rõ ràng. Người dùng dễ dàng phân biệt thông báo đã/chưa đọc. | Visual indicators không được hiển thị. Người dùng không thể phân biệt thông báo đã/chưa đọc. |

---

### 1.2 ĐÁNH DẤU ĐÃ ĐỌC - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Đánh dấu thông báo đã đọc                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Cho phép người dùng đánh dấu thông báo là đã đọc                              |
| Screen Access | Hiển thị trong trang thông báo, nút đánh dấu đã đọc trên mỗi thông báo        |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút đánh dấu đã đọc** | Button (Icon) | CheckCircle icon                        | **MỚI**: Nút để đánh dấu thông báo đã đọc     |
| **Thông báo thành công** | Toast      | Đã đánh dấu đã đọc                      | **MỚI**: Thông báo khi đánh dấu thành công    |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Đánh dấu đã đọc**      | Cho phép người dùng đánh dấu thông báo là đã đọc bằng cách click vào nút đánh dấu đã đọc hoặc click vào thông báo. Hệ thống sẽ cập nhật trạng thái read/unread và cập nhật UI.                                                              | Thông báo được đánh dấu đã đọc thành công. UI được cập nhật.                              | Không thể đánh dấu đã đọc. Trạng thái không được cập nhật.                                 |
| **Auto-mark as read**    | **MỚI**: Khi người dùng click vào thông báo để xem chi tiết, hệ thống tự động đánh dấu thông báo là đã đọc. Không cần click nút đánh dấu riêng.                                                                                            | Thông báo được tự động đánh dấu đã đọc khi click vào.                                        | Thông báo không được tự động đánh dấu đã đọc.                                              |

---

### 1.3 BATCH ACTIONS - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Batch actions cho thông báo                                                      |
| ------------- | ------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng thực hiện hành động hàng loạt trên nhiều thông báo           |
| Screen Access | Hiển thị trong trang thông báo, header với các nút batch actions                |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút đánh dấu tất cả đã đọc** | Button    | Đánh dấu tất cả đã đọc                  | **MỚI**: Nút để đánh dấu tất cả thông báo đã đọc |
| **Nút xóa đã đọc**       | Button       | Xóa đã đọc                              | **MỚI**: Nút để xóa tất cả thông báo đã đọc    |
| **Thông báo thành công** | Toast        | Đã đánh dấu tất cả thông báo là đã đọc  | **MỚI**: Thông báo khi batch action thành công |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Đánh dấu tất cả đã đọc** | **MỚI**: Cho phép người dùng đánh dấu tất cả thông báo là đã đọc bằng một lần click. Hệ thống sẽ cập nhật trạng thái read/unread cho tất cả thông báo và cập nhật UI.                                                                      | Tất cả thông báo được đánh dấu đã đọc thành công. UI được cập nhật.                        | Không thể đánh dấu tất cả thông báo. Một số thông báo không được cập nhật.                 |
| **Xóa đã đọc**           | **MỚI**: Cho phép người dùng xóa tất cả thông báo đã đọc bằng một lần click. Hệ thống sẽ xóa tất cả thông báo có trạng thái "đã đọc" và cập nhật UI.                                                                                        | Tất cả thông báo đã đọc được xóa thành công. UI được cập nhật.                            | Không thể xóa thông báo đã đọc. Một số thông báo không được xóa.                            |
| **Batch processing**     | **MỚI**: Hệ thống xử lý batch actions hiệu quả bằng cách cập nhật tất cả thông báo trong một transaction. Nếu có lỗi, hệ thống sẽ rollback và không cập nhật bất kỳ thông báo nào.                                                       | Batch actions được xử lý thành công. Tất cả thông báo được cập nhật.                      | Batch actions bị lỗi. Một số thông báo được cập nhật, một số không.                       |

#### 1.3.4 Batch Actions (MỚI):

| Action Type           | Description                                                                 | Result                                    |
| --------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Mark All as Read**  | Đánh dấu tất cả thông báo là đã đọc                                        | Tất cả thông báo có isRead = true         |
| **Clear All Read**    | Xóa tất cả thông báo đã đọc                                                | Tất cả thông báo có isRead = true bị xóa  |
| **Transaction Safety** | Sử dụng transaction để đảm bảo tính toàn vẹn dữ liệu                      | Rollback nếu có lỗi                        |

---

### 1.4 LỌC THÔNG BÁO

#### 1.4.1 Thông tin màn hình:

| Screen        | Lọc thông báo                                                      |
| ------------- | ----------------------------------------------------------------- |
| Description   | Cho phép người dùng lọc thông báo theo loại, độ ưu tiên, trạng thái read/unread |
| Screen Access | Hiển thị trong trang thông báo, phần bộ lọc                        |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Tabs loại**         | Tabs         | Tất cả, Đơn hàng, Khuyến mãi... | Tabs để lọc theo loại thông báo      |
| **Select độ ưu tiên** | Select       | Tất cả, Cao, Trung bình, Thấp | Dropdown lọc theo độ ưu tiên         |
| **Input tìm kiếm**    | Input        | Tìm kiếm thông báo...   | Ô tìm kiếm thông báo                  |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Read/unread logic**: Thêm trạng thái read/unread cho mỗi thông báo
2. **Visual indicators**: Hiển thị dot indicator và border-primary cho thông báo chưa đọc
3. **Auto-mark as read**: Tự động đánh dấu thông báo đã đọc khi click vào thông báo
4. **Batch actions**: Thêm tính năng đánh dấu tất cả đã đọc và xóa đã đọc
5. **Transaction safety**: Sử dụng transaction để đảm bảo tính toàn vẹn dữ liệu khi batch actions
6. **UI cải thiện**: Thêm nút đánh dấu đã đọc trên mỗi thông báo và batch action buttons trong header

