# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng đánh giá nâng cao của User_

## MỤC LỤC

1. [Chức năng đánh giá nâng cao](#1-chức-năng-đánh-giá-nâng-cao)
   - 1.1 [Đánh giá sản phẩm](#11-đánh-giá-sản-phẩm)
   - 1.2 [Viết review](#12-viết-review)
   - 1.3 [Xem đánh giá](#13-xem-đánh-giá)
   - 1.4 [Quản lý đánh giá của tôi](#14-quản-lý-đánh-giá-của-tôi)
   - 1.5 [Tương tác với đánh giá](#15-tương-tác-với-đánh-giá)

---

## 1. CHỨC NĂNG ĐÁNH GIÁ NÂNG CAO

### 1.1 ĐÁNH GIÁ SẢN PHẨM

#### 1.1.1 Thông tin màn hình:

| Screen        | Đánh giá sản phẩm                              |
| ------------- | ---------------------------------------------- |
| Description   | Cho điểm từ 1-5 sao (chỉ khách đã mua)         |
| Screen Access | Từ trang đánh giá hoặc trang chi tiết sản phẩm |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type        | Data                            | Description                    |
| ------------------------- | ----------- | ------------------------------- | ------------------------------ |
| **Tiêu đề đánh giá**      | Text        | Đánh giá sản phẩm               | Tiêu đề của trang đánh giá     |
| **Icon đánh giá**         | Icon        | Star                            | Icon đại diện cho đánh giá     |
| **Sản phẩm cần đánh giá** | Card        | Danh sách sản phẩm chờ đánh giá | Hiển thị sản phẩm chờ đánh giá |
| **Hình ảnh sản phẩm**     | Image       | Hình ảnh sản phẩm               | Hình ảnh của sản phẩm          |
| **Tên sản phẩm**          | Text        | Tên sản phẩm                    | Tên đầy đủ của sản phẩm        |
| **Ngày mua**              | Text        | Ngày mua sản phẩm               | Ngày mua sản phẩm              |
| **Mã đơn hàng**           | Text        | Mã đơn hàng                     | Mã định danh của đơn hàng      |
| **Hệ thống sao**          | Star Rating | 1-5 sao                         | Hệ thống đánh giá bằng sao     |
| **Sao 1**                 | Star        | 1 sao                           | Đánh giá 1 sao                 |
| **Sao 2**                 | Star        | 2 sao                           | Đánh giá 2 sao                 |
| **Sao 3**                 | Star        | 3 sao                           | Đánh giá 3 sao                 |
| **Sao 4**                 | Star        | 4 sao                           | Đánh giá 4 sao                 |
| **Sao 5**                 | Star        | 5 sao                           | Đánh giá 5 sao                 |
| **Nút đánh giá**          | Button      | Đánh giá                        | Nút để bắt đầu đánh giá        |

#### 1.1.3 Hành động và xử lý:

| Action Name                        | Description                                                                                                                                                                                                                          | Success                                                                                                                    | Failure                                                                                                                            |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị sản phẩm chờ đánh giá** | Hiển thị danh sách các sản phẩm mà người dùng đã mua nhưng chưa đánh giá. Chỉ những khách hàng đã mua sản phẩm mới có thể đánh giá. Hệ thống kiểm tra lịch sử mua hàng để xác định quyền đánh giá.                                   | Danh sách sản phẩm chờ đánh giá được hiển thị đầy đủ và chính xác. Hệ thống kiểm tra quyền đánh giá đúng cách.             | Danh sách sản phẩm chờ đánh giá không được hiển thị đầy đủ hoặc không chính xác. Hệ thống không kiểm tra quyền đánh giá đúng cách. |
| **Chọn điểm đánh giá**             | Cho phép người dùng chọn điểm đánh giá từ 1-5 sao bằng cách click vào các ngôi sao. Hệ thống hiển thị trực quan điểm đánh giá đã chọn và cho phép thay đổi trước khi gửi đánh giá.                                                   | Điểm đánh giá được chọn thành công và hiển thị trực quan. Người dùng có thể thay đổi điểm đánh giá dễ dàng.                | Điểm đánh giá không được chọn thành công hoặc không được hiển thị trực quan. Người dùng không thể thay đổi điểm đánh giá.          |
| **Xác thực quyền đánh giá**        | Hệ thống tự động xác thực quyền đánh giá của người dùng dựa trên lịch sử mua hàng. Chỉ những khách hàng đã mua sản phẩm mới có thể đánh giá. Hệ thống kiểm tra trạng thái đơn hàng và thời gian mua hàng để xác định quyền đánh giá. | Quyền đánh giá được xác thực chính xác và chỉ cho phép khách hàng đã mua đánh giá. Hệ thống kiểm tra đầy đủ các điều kiện. | Quyền đánh giá không được xác thực chính xác hoặc cho phép người chưa mua đánh giá. Hệ thống không kiểm tra đầy đủ các điều kiện.  |

### 1.2 VIẾT REVIEW

#### 1.2.1 Thông tin màn hình:

| Screen        | Viết review                                                                               |
| ------------- | ----------------------------------------------------------------------------------------- |
| Description   | Nhận xét chi tiết về chất lượng mô hình (chỉ khách đã mua) có thể đính kèm ảnh hoặc video |
| Screen Access | Từ trang đánh giá sau khi chọn sản phẩm cần đánh giá                                      |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                         | Type        | Data                             | Description                       |
| ---------------------------- | ----------- | -------------------------------- | --------------------------------- |
| **Tiêu đề viết review**      | Text        | Viết đánh giá                    | Tiêu đề của trang viết review     |
| **Thông tin sản phẩm**       | Card        | Thông tin sản phẩm đang đánh giá | Hiển thị thông tin sản phẩm       |
| **Hình ảnh sản phẩm**        | Image       | Hình ảnh sản phẩm                | Hình ảnh của sản phẩm             |
| **Tên sản phẩm**             | Text        | Tên sản phẩm                     | Tên đầy đủ của sản phẩm           |
| **Hệ thống sao**             | Star Rating | 1-5 sao                          | Hệ thống đánh giá bằng sao        |
| **Ô nhập nhận xét**          | Textarea    | Nhập nhận xét chi tiết           | Ô để nhập nhận xét chi tiết       |
| **Upload ảnh**               | File Input  | Đính kèm ảnh                     | Nút để upload ảnh                 |
| **Upload video**             | File Input  | Đính kèm video                   | Nút để upload video               |
| **Danh sách file đã upload** | List        | Danh sách file đã upload         | Hiển thị danh sách file đã upload |
| **Nút gửi đánh giá**         | Button      | Gửi đánh giá                     | Nút để gửi đánh giá               |
| **Nút hủy**                  | Button      | Hủy                              | Nút để hủy viết đánh giá          |
| **Thông báo lỗi**            | Alert       | Thông báo lỗi                    | Thông báo khi có lỗi              |
| **Thông báo thành công**     | Alert       | Thông báo thành công             | Thông báo khi gửi thành công      |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                          | Success                                                                                                                              | Failure                                                                                                                                                                |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nhập nhận xét chi tiết** | Cho phép người dùng nhập nhận xét chi tiết về chất lượng sản phẩm, trải nghiệm sử dụng, và các đánh giá khác. Ô nhập hỗ trợ nhiều dòng và có thể chứa nhiều ký tự để người dùng có thể mô tả đầy đủ trải nghiệm của mình.                            | Nhận xét chi tiết được nhập thành công và hiển thị đầy đủ. Ô nhập hoạt động mượt mà và không có lỗi.                                 | Nhận xét chi tiết không được nhập thành công hoặc không được hiển thị đầy đủ. Ô nhập hoạt động không mượt mà hoặc có lỗi.                                              |
| **Upload ảnh và video**    | Cho phép người dùng đính kèm ảnh hoặc video để minh họa cho đánh giá của mình. Hệ thống hỗ trợ nhiều định dạng file và có giới hạn kích thước file. File được upload sẽ được hiển thị trong danh sách để người dùng có thể xem trước và xóa nếu cần. | File ảnh và video được upload thành công và hiển thị trong danh sách. Hệ thống hỗ trợ nhiều định dạng và giới hạn kích thước hợp lý. | File ảnh và video không được upload thành công hoặc không được hiển thị trong danh sách. Hệ thống không hỗ trợ đầy đủ định dạng hoặc giới hạn kích thước không hợp lý. |
| **Gửi đánh giá**           | Khi người dùng hoàn thành việc nhập điểm đánh giá và nhận xét, hệ thống sẽ gửi đánh giá đến hệ thống để xử lý. Đánh giá sẽ được lưu trữ với trạng thái "Đang chờ duyệt" và chờ admin kiểm duyệt trước khi hiển thị công khai. Chỉ những đánh giá đã được duyệt mới hiển thị cho người dùng khác xem. Hệ thống gửi thông báo xác nhận khi đánh giá được gửi thành công và thông báo khi đánh giá được duyệt hoặc từ chối.   | Đánh giá được gửi thành công và lưu trữ trong hệ thống với trạng thái "Đang chờ duyệt". Thông báo xác nhận được hiển thị rõ ràng.                                    | Đánh giá không được gửi thành công hoặc không được lưu trữ trong hệ thống. Thông báo xác nhận không được hiển thị rõ ràng.                                             |

### 1.3 XEM ĐÁNH GIÁ

#### 1.3.1 Thông tin màn hình:

| Screen        | Xem đánh giá                                                   |
| ------------- | -------------------------------------------------------------- |
| Description   | Xem danh sách reviews của khách hàng khác (ai cũng có thể xem) |
| Screen Access | Từ trang chi tiết sản phẩm hoặc trang đánh giá                 |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                         | Type        | Data                            | Description                        |
| ---------------------------- | ----------- | ------------------------------- | ---------------------------------- |
| **Tiêu đề đánh giá**         | Text        | Đánh giá sản phẩm               | Tiêu đề của trang đánh giá         |
| **Số lượng đánh giá**        | Text        | Số lượng đánh giá từ khách hàng | Tổng số đánh giá hiện có           |
| **Bộ lọc đánh giá**          | Filter      | Lọc theo điểm đánh giá          | Bộ lọc để tìm đánh giá theo điểm   |
| **Sắp xếp đánh giá**         | Sort        | Sắp xếp theo thời gian / điểm   | Tùy chọn sắp xếp đánh giá          |
| **Danh sách đánh giá**       | List        | Danh sách các đánh giá          | Hiển thị danh sách đánh giá        |
| **Thông tin người đánh giá** | Card        | Thông tin người đánh giá        | Hiển thị thông tin người đánh giá  |
| **Tên người dùng**           | Text        | Tên người dùng                  | Tên của người đánh giá             |
| **Badge đã mua**             | Badge       | Đã mua                          | Badge xác nhận đã mua sản phẩm     |
| **Điểm đánh giá**            | Star Rating | 1-5 sao                         | Điểm đánh giá của người dùng       |
| **Ngày đánh giá**            | Text        | Ngày đánh giá                   | Thời gian đánh giá                 |
| **Nội dung đánh giá**        | Text        | Nội dung đánh giá               | Nội dung chi tiết của đánh giá     |
| **Ảnh đính kèm**             | Image       | Ảnh đính kèm                    | Ảnh được đính kèm trong đánh giá   |
| **Video đính kèm**           | Video       | Video đính kèm                  | Video được đính kèm trong đánh giá |
| **Nút hữu ích**              | Button      | Hữu ích                         | Nút để đánh dấu đánh giá hữu ích   |
| **Số lượt hữu ích**          | Text        | Số lượt hữu ích                 | Số lượt đánh dấu hữu ích           |

#### 1.3.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                              | Success                                                                                                    | Failure                                                                                                                        |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị danh sách đánh giá** | Hiển thị danh sách đánh giá của các khách hàng khác với thông tin đầy đủ bao gồm tên người đánh giá, điểm đánh giá, nội dung đánh giá, và thời gian đánh giá. Chỉ hiển thị những đánh giá đã được admin duyệt (trạng thái "Đã duyệt"). Danh sách được sắp xếp theo thời gian hoặc điểm đánh giá tùy theo lựa chọn của người dùng. | Danh sách đánh giá được hiển thị đầy đủ và chính xác, chỉ bao gồm đánh giá đã được duyệt. Danh sách được sắp xếp theo lựa chọn của người dùng. | Danh sách đánh giá không được hiển thị đầy đủ hoặc không chính xác. Hiển thị cả đánh giá chưa được duyệt. Danh sách không được sắp xếp theo lựa chọn của người dùng. |
| **Lọc và sắp xếp đánh giá**     | Cho phép người dùng lọc đánh giá theo điểm đánh giá (1-5 sao) và sắp xếp theo thời gian hoặc điểm đánh giá. Hệ thống cập nhật danh sách đánh giá ngay lập tức khi có thay đổi bộ lọc hoặc cách sắp xếp.                                                  | Đánh giá được lọc và sắp xếp chính xác theo lựa chọn của người dùng. Danh sách được cập nhật ngay lập tức. | Đánh giá không được lọc và sắp xếp chính xác theo lựa chọn của người dùng. Danh sách không được cập nhật ngay lập tức.         |
| **Hiển thị đánh giá chi tiết**  | Hiển thị đầy đủ thông tin của từng đánh giá bao gồm thông tin người đánh giá, điểm đánh giá, nội dung đánh giá, ảnh/video đính kèm, và số lượt hữu ích. Thông tin được trình bày rõ ràng và dễ đọc.                                                      | Đánh giá chi tiết được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.           | Đánh giá chi tiết không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.        |

### 1.4 QUẢN LÝ ĐÁNH GIÁ CỦA TÔI

#### 1.4.1 Thông tin màn hình:

| Screen        | Quản lý đánh giá của tôi                     |
| ------------- | -------------------------------------------- |
| Description   | Quản lý các đánh giá mà người dùng đã viết   |
| Screen Access | Từ trang đánh giá với tab "Đánh giá của tôi" |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type        | Data                           | Description                          |
| ------------------------ | ----------- | ------------------------------ | ------------------------------------ |
| **Tiêu đề quản lý**      | Text        | Đánh giá của tôi               | Tiêu đề của trang quản lý            |
| **Tab đánh giá của tôi** | Tab         | Đánh giá của tôi               | Tab để xem đánh giá của mình         |
| **Danh sách đánh giá**   | List        | Danh sách đánh giá của tôi     | Hiển thị danh sách đánh giá của mình |
| **Thông tin sản phẩm**   | Card        | Thông tin sản phẩm đã đánh giá | Hiển thị thông tin sản phẩm          |
| **Hình ảnh sản phẩm**    | Image       | Hình ảnh sản phẩm              | Hình ảnh của sản phẩm                |
| **Tên sản phẩm**         | Text        | Tên sản phẩm                   | Tên đầy đủ của sản phẩm              |
| **Điểm đánh giá**        | Star Rating | 1-5 sao                        | Điểm đánh giá của tôi                |
| **Nội dung đánh giá**    | Text        | Nội dung đánh giá của tôi      | Nội dung chi tiết của đánh giá       |
| **Ngày đánh giá**        | Text        | Ngày đánh giá                  | Thời gian đánh giá                   |
| **Trạng thái**           | Badge       | Đã gửi / Đang chờ duyệt / Đã duyệt / Từ chối        | Trạng thái của đánh giá (moderation)              |
| **Nút chỉnh sửa**        | Button      | Chỉnh sửa                      | Nút để chỉnh sửa đánh giá            |
| **Nút xóa**              | Button      | Xóa                            | Nút để xóa đánh giá                  |
| **Số lượt hữu ích**      | Text        | Số lượt hữu ích                | Số lượt đánh dấu hữu ích             |

#### 1.4.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                        | Success                                                                                                                 | Failure                                                                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị đánh giá của tôi** | Hiển thị danh sách tất cả các đánh giá mà người dùng đã viết với thông tin đầy đủ bao gồm sản phẩm đã đánh giá, điểm đánh giá, nội dung đánh giá, và trạng thái đánh giá. Danh sách được sắp xếp theo thời gian đánh giá mới nhất. | Danh sách đánh giá của tôi được hiển thị đầy đủ và chính xác. Danh sách được sắp xếp theo thời gian đánh giá mới nhất.  | Danh sách đánh giá của tôi không được hiển thị đầy đủ hoặc không chính xác. Danh sách không được sắp xếp theo thời gian đánh giá mới nhất.       |
| **Chỉnh sửa đánh giá**        | Cho phép người dùng chỉnh sửa đánh giá đã viết bao gồm thay đổi điểm đánh giá, nội dung đánh giá, và các file đính kèm. Hệ thống lưu lại lịch sử chỉnh sửa và hiển thị thời gian chỉnh sửa cuối cùng.                              | Đánh giá được chỉnh sửa thành công và lưu lại lịch sử chỉnh sửa. Thời gian chỉnh sửa cuối cùng được hiển thị chính xác. | Đánh giá không được chỉnh sửa thành công hoặc không được lưu lại lịch sử chỉnh sửa. Thời gian chỉnh sửa cuối cùng không được hiển thị chính xác. |
| **Xóa đánh giá**              | Cho phép người dùng xóa đánh giá đã viết. Hệ thống sẽ hiển thị xác nhận trước khi xóa và cập nhật danh sách đánh giá sau khi xóa thành công. Đánh giá đã xóa sẽ không thể khôi phục.                                               | Đánh giá được xóa thành công và danh sách được cập nhật. Hệ thống hiển thị xác nhận trước khi xóa.                      | Đánh giá không được xóa thành công hoặc danh sách không được cập nhật. Hệ thống không hiển thị xác nhận trước khi xóa.                           |

### 1.5 TƯƠNG TÁC VỚI ĐÁNH GIÁ

#### 1.5.1 Thông tin màn hình:

| Screen        | Tương tác với đánh giá                         |
| ------------- | ---------------------------------------------- |
| Description   | Tương tác với các đánh giá của người dùng khác |
| Screen Access | Từ trang xem đánh giá                          |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                      | Type     | Data                  | Description                            |
| ------------------------- | -------- | --------------------- | -------------------------------------- |
| **Nút hữu ích**           | Button   | Hữu ích               | Nút để đánh dấu đánh giá hữu ích       |
| **Icon hữu ích**          | Icon     | ThumbsUp              | Icon đại diện cho hữu ích              |
| **Số lượt hữu ích**       | Text     | Số lượt hữu ích       | Số lượt đánh dấu hữu ích               |
| **Nút không hữu ích**     | Button   | Không hữu ích         | Nút để đánh dấu đánh giá không hữu ích |
| **Icon không hữu ích**    | Icon     | ThumbsDown            | Icon đại diện cho không hữu ích        |
| **Số lượt không hữu ích** | Text     | Số lượt không hữu ích | Số lượt đánh dấu không hữu ích         |
| **Nút báo cáo**           | Button   | Báo cáo               | Nút để báo cáo đánh giá không phù hợp  |
| **Icon báo cáo**          | Icon     | Flag                  | Icon đại diện cho báo cáo              |
| **Modal báo cáo**         | Modal    | Modal báo cáo         | Modal để nhập lý do báo cáo            |
| **Lý do báo cáo**         | Select   | Lý do báo cáo         | Dropdown để chọn lý do báo cáo         |
| **Mô tả báo cáo**         | Textarea | Mô tả chi tiết        | Ô để nhập mô tả chi tiết về báo cáo    |
| **Nút gửi báo cáo**       | Button   | Gửi báo cáo           | Nút để gửi báo cáo                     |
| **Nút hủy báo cáo**       | Button   | Hủy                   | Nút để hủy báo cáo                     |

#### 1.5.3 Hành động và xử lý:

| Action Name                       | Description                                                                                                                                                                                                                                              | Success                                                                                                                                        | Failure                                                                                                                                                                 |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Đánh dấu hữu ích**              | Cho phép người dùng đánh dấu đánh giá là hữu ích hoặc không hữu ích để giúp các người dùng khác đánh giá chất lượng của đánh giá. Hệ thống cập nhật số lượt hữu ích/không hữu ích ngay lập tức và lưu lại lựa chọn của người dùng.                       | Đánh giá được đánh dấu hữu ích/không hữu ích thành công và số lượt được cập nhật ngay lập tức. Lựa chọn của người dùng được lưu lại chính xác. | Đánh giá không được đánh dấu hữu ích/không hữu ích thành công hoặc số lượt không được cập nhật ngay lập tức. Lựa chọn của người dùng không được lưu lại chính xác.      |
| **Báo cáo đánh giá**              | Cho phép người dùng báo cáo đánh giá không phù hợp hoặc vi phạm quy định. Hệ thống cung cấp các lý do báo cáo phổ biến và cho phép người dùng nhập mô tả chi tiết. Báo cáo sẽ được gửi đến admin để xem xét và xử lý.                                    | Đánh giá được báo cáo thành công và báo cáo được gửi đến admin. Hệ thống cung cấp đầy đủ các lý do báo cáo và cho phép nhập mô tả chi tiết.    | Đánh giá không được báo cáo thành công hoặc báo cáo không được gửi đến admin. Hệ thống không cung cấp đầy đủ các lý do báo cáo hoặc không cho phép nhập mô tả chi tiết. |
| **Hiển thị trạng thái tương tác** | Hiển thị trạng thái tương tác của người dùng với từng đánh giá bao gồm đã đánh dấu hữu ích/không hữu ích hay chưa, và đã báo cáo hay chưa. Trạng thái được cập nhật real-time và hiển thị rõ ràng để người dùng biết được tình trạng tương tác của mình. | Trạng thái tương tác được hiển thị chính xác và cập nhật real-time. Người dùng có thể dễ dàng biết được tình trạng tương tác của mình.         | Trạng thái tương tác không được hiển thị chính xác hoặc không được cập nhật real-time. Người dùng không thể dễ dàng biết được tình trạng tương tác của mình.            |
