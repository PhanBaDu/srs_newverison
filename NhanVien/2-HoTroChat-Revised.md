# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng quản lý đánh giá của Admin_

## MỤC LỤC

1. [Chức năng quản lý đánh giá](#1-chức-năng-quản-lý-đánh-giá)
   - 1.1 [Xem tất cả đánh giá](#11-xem-tất-cả-đánh-giá)
   - 1.2 [Chi tiết đánh giá](#12-chi-tiết-đánh-giá)
   - 1.3 [Phản hồi đánh giá](#13-phản-hồi-đánh-giá)
   - 1.4 [Xóa đánh giá](#14-xóa-đánh-giá)

---

## 1. CHỨC NĂNG QUẢN LÝ ĐÁNH GIÁ

### 1.1 XEM TẤT CẢ ĐÁNH GIÁ

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách đánh giá khách hàng       |
| ------------- | ----------------------------------- |
| Description   | Xem toàn bộ đánh giá của khách hàng |
| Screen Access | /admin/reviews                      |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                                                       | Description          |
| --------------------- | ------ | ---------------------------------------------------------- | -------------------- |
| **Bộ lọc sản phẩm**   | Select | Tên sản phẩm                                               | Lọc theo sản phẩm    |
| **Bộ lọc điểm**       | Select | 1-5 sao                                                    | Lọc theo điểm        |
| **Bộ lọc trạng thái** | Select | Tất cả / Chờ duyệt / Đã duyệt / Từ chối / Hiển thị / Ẩn / Vi phạm                           | Lọc theo trạng thái (moderation)  |
| **Ô tìm kiếm**        | Input  | Tìm theo nội dung/khách hàng                               | Tìm nhanh            |
| **Bảng đánh giá**     | Table  | Sản phẩm, Người đánh giá, Điểm, Nội dung, Trạng thái, Ngày | Danh sách đánh giá   |
| **Nút xem chi tiết**  | Button | Xem chi tiết                                               | Mở chi tiết đánh giá |

#### 1.1.3 Hành động và xử lý:

| Action Name            | Description                            | Success                      | Failure              |
| ---------------------- | -------------------------------------- | ---------------------------- | -------------------- |
| **Hiển thị danh sách** | Hiển thị kèm lọc/tìm kiếm, phân trang. | Dữ liệu đúng, thao tác mượt. | Lỗi tải dữ liệu/lọc. |

### 1.2 CHI TIẾT ĐÁNH GIÁ

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết đánh giá                        |
| ------------- | ---------------------------------------- |
| Description   | Xem nội dung và thông tin người đánh giá |
| Screen Access | Từ danh sách đánh giá, Xem chi tiết      |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                   | Type    | Data                     | Description              |
| ---------------------- | ------- | ------------------------ | ------------------------ |
| **Thông tin sản phẩm** | Card    | Tên, SKU                 | Sản phẩm được đánh giá   |
| **Người đánh giá**     | Card    | Tên, Email, Badge đã mua | Thông tin người đánh giá |
| **Điểm đánh giá**      | Badge   | 1-5 sao                  | Điểm số                  |
| **Nội dung**           | Text    | Nội dung đánh giá        | Nội dung chi tiết        |
| **Ảnh/Video**          | Gallery | Media đính kèm           | Tư liệu minh họa         |
| **Trạng thái**         | Badge   | Chờ duyệt / Đã duyệt / Từ chối / Hiển thị / Ẩn / Vi phạm  | Trạng thái hiện tại (moderation)      |
| **Nút duyệt**          | Button  | Duyệt                     | Duyệt đánh giá            |
| **Nút từ chối**         | Button  | Từ chối                   | Từ chối đánh giá          |
| **Nút phản hồi**       | Button  | Phản hồi                 | Mở form phản hồi         |
| **Nút ẩn/xóa**         | Button  | Ẩn / Xóa                 | Quản trị nội dung        |

#### 1.2.3 Hành động và xử lý:

| Action Name               | Description                            | Success                              | Failure               |
| ------------------------- | -------------------------------------- | ------------------------------------ | --------------------- |
| **Xem chi tiết đánh giá** | Hiển thị đầy đủ nội dung, media, meta. Đánh giá mới sẽ có trạng thái "Chờ duyệt" và chờ admin kiểm duyệt trước khi hiển thị công khai. | Thông tin đầy đủ, media hiển thị OK. Trạng thái moderation được hiển thị rõ ràng. | Thiếu media/nội dung. Trạng thái moderation không được hiển thị. |
| **Duyệt đánh giá**        | Cho phép admin duyệt đánh giá để hiển thị công khai. Đánh giá được duyệt sẽ chuyển sang trạng thái "Đã duyệt" và hiển thị cho người dùng khác xem. | Đánh giá được duyệt thành công và hiển thị công khai. | Không thể duyệt đánh giá hoặc không hiển thị công khai. |
| **Từ chối đánh giá**     | Cho phép admin từ chối đánh giá nếu vi phạm quy định. Đánh giá bị từ chối sẽ chuyển sang trạng thái "Từ chối" và không hiển thị công khai. | Đánh giá bị từ chối thành công và không hiển thị công khai. | Không thể từ chối đánh giá. |

### 1.3 PHẢN HỒI ĐÁNH GIÁ

#### 1.3.1 Thông tin màn hình:

| Screen        | Phản hồi đánh giá                      |
| ------------- | -------------------------------------- |
| Description   | Admin phản hồi công khai dưới đánh giá |
| Screen Access | Từ chi tiết đánh giá                   |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data              | Description   |
| -------------------- | ------ | ----------------- | ------------- |
| **Form phản hồi**    | Form   | Nội dung phản hồi | Soạn phản hồi |
| **Nút gửi phản hồi** | Button | Gửi phản hồi      | Đăng phản hồi |

#### 1.3.3 Hành động và xử lý:

| Action Name       | Description                                   | Success                          | Failure                       |
| ----------------- | --------------------------------------------- | -------------------------------- | ----------------------------- |
| **Đăng phản hồi** | Đăng phản hồi công khai, lưu thời gian/người. | Phản hồi hiển thị dưới đánh giá. | Không đăng/lưu được phản hồi. |

### 1.4 XÓA ĐÁNH GIÁ

#### 1.4.1 Thông tin màn hình:

| Screen        | Xóa đánh giá vi phạm/spam     |
| ------------- | ----------------------------- |
| Description   | Xóa đánh giá vi phạm quy định |
| Screen Access | Từ chi tiết đánh giá          |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                 | Type   | Data                            | Description            |
| -------------------- | ------ | ------------------------------- | ---------------------- |
| **Modal xác nhận**   | Modal  | Lý do xóa, Cảnh báo mất dữ liệu | Xác nhận trước khi xóa |
| **Nút xác nhận xóa** | Button | Xác nhận                        | Thực hiện xóa          |

#### 1.4.3 Hành động và xử lý:

| Action Name      | Description                          | Success                            | Failure                           |
| ---------------- | ------------------------------------ | ---------------------------------- | --------------------------------- |
| **Xóa đánh giá** | Xóa vĩnh viễn đánh giá vi phạm/spam. | Đánh giá bị xóa, lịch sử ghi nhận. | Không xóa được hoặc lỗi hiển thị. |
