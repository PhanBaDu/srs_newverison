# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Tương tác bài viết của User_

## MỤC LỤC

1. [Tương tác bài viết](#1-tương-tác-bài-viết)
   - 1.1 [Hiển thị danh sách bình luận](#11-hiển-thị-danh-sách-bình-luận)
   - 1.2 [Hiển thị số lượng like](#12-hiển-thị-số-lượng-like)
   - 1.3 [Tạo bình luận](#13-tạo-bình-luận)
   - 1.4 [Xóa bình luận](#14-xóa-bình-luận)
   - 1.5 [Chỉnh sửa bình luận](#15-chỉnh-sửa-bình-luận)

---

## 1. TƯƠNG TÁC BÀI VIẾT

### 1.1 HIỂN THỊ DANH SÁCH BÌNH LUẬN

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách bình luận bài viết                   |
| ------------- | ---------------------------------------------- |
| Description   | Hiển thị danh sách bình luận từ người dùng     |
| Screen Access | Từ trang chi tiết bài viết với tab "Bình luận" |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type       | Data                                          | Description                        |
| ----------------------- | ---------- | --------------------------------------------- | ---------------------------------- |
| **Tiêu đề tab**         | Text       | Bình luận                                     | Tiêu đề của tab bình luận          |
| **Số lượng bình luận**  | Badge      | Số lượng bình luận                            | Hiển thị tổng số bình luận         |
| **Bộ lọc bình luận**    | Select     | Tất cả / Mới nhất / Nhiều like nhất / Cũ nhất | Dropdown để lọc bình luận          |
| **Bộ lọc thời gian**    | Select     | Hôm nay / Tuần này / Tháng này / Tất cả       | Dropdown để lọc theo thời gian     |
| **Danh sách bình luận** | List       | Danh sách bình luận                           | Danh sách các bình luận            |
| **Card bình luận**      | Card       | Thông tin bình luận                           | Card hiển thị thông tin bình luận  |
| **Ảnh đại diện**        | Avatar     | Ảnh đại diện người bình luận                  | Avatar của người bình luận         |
| **Tên người dùng**      | Text       | Tên người bình luận                           | Tên của người bình luận            |
| **Thời gian bình luận** | Text       | Thời gian bình luận                           | Thời gian bình luận được đăng      |
| **Nội dung bình luận**  | Text       | Nội dung bình luận                            | Nội dung của bình luận             |
| **Hình ảnh đính kèm**   | Image      | Hình ảnh trong bình luận                      | Hình ảnh được đính kèm             |
| **Số lượng like**       | Badge      | Số lượng like bình luận                       | Số lượng người thích bình luận     |
| **Số lượng phản hồi**   | Badge      | Số lượng phản hồi                             | Số lượng phản hồi cho bình luận    |
| **Nút like bình luận**  | Button     | Like / Unlike                                 | Nút để thích/bỏ thích bình luận    |
| **Nút phản hồi**        | Button     | Phản hồi                                      | Nút để phản hồi bình luận          |
| **Nút báo cáo**         | Button     | Báo cáo                                       | Nút để báo cáo bình luận           |
| **Nút chỉnh sửa**       | Button     | Chỉnh sửa                                     | Nút để chỉnh sửa bình luận         |
| **Nút xóa**             | Button     | Xóa                                           | Nút để xóa bình luận               |
| **Phân trang**          | Pagination | Điều hướng trang                              | Phân trang cho danh sách bình luận |

#### 1.1.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                 | Success                                                                                                              | Failure                                                                                                                          |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị danh sách bình luận** | Hiển thị danh sách tất cả bình luận của bài viết với thông tin đầy đủ bao gồm người bình luận, nội dung, hình ảnh đính kèm, số lượng tương tác, và thời gian. Danh sách được sắp xếp theo thời gian mới nhất và hỗ trợ phân trang.          | Danh sách bình luận được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                   | Danh sách bình luận không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.        |
| **Lọc và sắp xếp bình luận**     | Cho phép người dùng lọc bình luận theo các tiêu chí khác nhau như "Tất cả", "Mới nhất", "Nhiều like nhất", "Cũ nhất" và theo thời gian (Hôm nay, Tuần này, Tháng này, Tất cả). Hệ thống sẽ cập nhật danh sách ngay lập tức khi có thay đổi. | Bình luận được lọc và sắp xếp chính xác theo tiêu chí đã chọn. Danh sách được cập nhật ngay lập tức khi có thay đổi. | Bình luận không được lọc và sắp xếp chính xác theo tiêu chí đã chọn. Danh sách không được cập nhật ngay lập tức khi có thay đổi. |

### 1.2 HIỂN THỊ SỐ LƯỢNG LIKE

#### 1.2.1 Thông tin màn hình:

| Screen        | Hiển thị số lượng like bài viết                    |
| ------------- | -------------------------------------------------- |
| Description   | Hiển thị chi tiết số lượng like                    |
| Screen Access | Từ trang chi tiết bài viết với thông tin tương tác |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                           | Description                         |
| ------------------------ | ------ | ------------------------------ | ----------------------------------- |
| **Thông tin tương tác**  | Card   | Thông tin like, comment, share | Card hiển thị thông tin tương tác   |
| **Số lượng like**        | Badge  | Số lượng like                  | Số lượng người thích bài viết       |
| **Nút like**             | Button | Like / Unlike                  | Nút để thích/bỏ thích bài viết      |
| **Icon like**            | Icon   | Heart                          | Icon đại diện cho like              |
| **Danh sách người like** | Modal  | Danh sách người đã like        | Modal hiển thị danh sách người like |
| **Avatar người like**    | Avatar | Ảnh đại diện người like        | Avatar của người đã like            |
| **Tên người like**       | Text   | Tên người đã like              | Tên của người đã like               |
| **Thời gian like**       | Text   | Thời gian like                 | Thời gian người dùng like           |
| **Nút đóng modal**       | Button | Đóng                           | Nút để đóng modal                   |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                   | Success                                                                                                                | Failure                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị số lượng like** | Hiển thị số lượng like của bài viết với khả năng xem chi tiết danh sách người đã like. Khi click vào số lượng like, hiển thị modal với danh sách đầy đủ người đã like bao gồm avatar, tên, và thời gian like. | Số lượng like được hiển thị chính xác và modal danh sách người like hoạt động đúng cách.                               | Số lượng like không được hiển thị chính xác hoặc modal danh sách người like không hoạt động đúng cách.                                     |
| **Tương tác like**         | Cho phép người dùng like hoặc unlike bài viết. Hệ thống sẽ cập nhật số lượng like real-time và hiển thị trạng thái like của người dùng. Khi like, người dùng sẽ được thêm vào danh sách người like. Hệ thống kiểm tra spam và giới hạn số lần like của mỗi user (mỗi user chỉ được like 1 lần cho mỗi bài viết). Hệ thống phát hiện và chặn hành vi bom like (nhiều like trong thời gian ngắn).           | Tương tác like được thực hiện thành công và số lượng được cập nhật real-time. Trạng thái like được hiển thị chính xác. Hệ thống chặn spam và bom like hiệu quả. | Tương tác like không được thực hiện thành công hoặc số lượng không được cập nhật real-time. Trạng thái like không được hiển thị chính xác. Hệ thống không chặn được spam hoặc bom like. |

### 1.3 TẠO BÌNH LUẬN

#### 1.3.1 Thông tin màn hình:

| Screen        | Tạo bình luận mới                             |
| ------------- | --------------------------------------------- |
| Description   | Cho phép mọi người bình luận vào bài viết     |
| Screen Access | Từ trang chi tiết bài viết với form bình luận |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                       | Type      | Data                          | Description                    |
| -------------------------- | --------- | ----------------------------- | ------------------------------ |
| **Form bình luận**         | Form      | Form viết bình luận           | Form để viết bình luận mới     |
| **Avatar người dùng**      | Avatar    | Ảnh đại diện người dùng       | Avatar của người dùng hiện tại |
| **Tên người dùng**         | Text      | Tên người dùng hiện tại       | Tên của người dùng hiện tại    |
| **Ô nhập bình luận**       | Textarea  | Nội dung bình luận            | Ô nhập nội dung bình luận      |
| **Upload hình ảnh**        | FileInput | Upload hình ảnh đính kèm      | Ô upload hình ảnh đính kèm     |
| **Preview hình ảnh**       | Image     | Xem trước hình ảnh đã upload  | Xem trước hình ảnh đã upload   |
| **Nút xóa hình ảnh**       | Button    | Xóa hình ảnh                  | Nút để xóa hình ảnh đã upload  |
| **Cài đặt quyền riêng tư** | Select    | Công khai / Bạn bè / Riêng tư | Dropdown chọn quyền riêng tư   |
| **Nút gửi bình luận**      | Button    | Gửi bình luận                 | Nút để gửi bình luận           |
| **Nút hủy**                | Button    | Hủy                           | Nút để hủy tạo bình luận       |
| **Thông báo thành công**   | Toast     | Đã gửi bình luận              | Thông báo khi gửi thành công   |
| **Thông báo lỗi**          | Toast     | Không thể gửi bình luận       | Thông báo khi không thể gửi    |

#### 1.3.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                               | Success                                                                                                                       | Failure                                                                                                                                                   |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tạo bình luận mới**        | Cho phép người dùng tạo bình luận mới cho bài viết bằng cách điền nội dung vào form, đính kèm hình ảnh (tùy chọn), và chọn quyền riêng tư. Hệ thống sẽ validate dữ liệu trước khi cho phép gửi bình luận. Hệ thống kiểm tra spam và giới hạn số lần bình luận của mỗi user trong khoảng thời gian nhất định để chống bom comment. | Bình luận được tạo thành công và hiển thị trong danh sách. Form được điền đầy đủ thông tin và validation hoạt động đúng cách. Hệ thống chặn spam và bom comment hiệu quả. | Bình luận không được tạo thành công hoặc không hiển thị trong danh sách. Form không được điền đầy đủ thông tin hoặc validation không hoạt động đúng cách. Hệ thống không chặn được spam hoặc bom comment. |
| **Upload hình ảnh đính kèm** | Cho phép người dùng upload hình ảnh đính kèm với bình luận và hiển thị preview trước khi gửi. Hệ thống sẽ validate định dạng file, kích thước, và hiển thị preview để người dùng kiểm tra.                | Hình ảnh được upload thành công và preview hiển thị chính xác. Validation file hoạt động đúng cách.                           | Hình ảnh không được upload thành công hoặc preview không hiển thị chính xác. Validation file không hoạt động đúng cách.                                   |

### 1.4 XÓA BÌNH LUẬN

#### 1.4.1 Thông tin màn hình:

| Screen        | Xóa bình luận                                           |
| ------------- | ------------------------------------------------------- |
| Description   | Cho phép người bình luận có thể xóa bình luận           |
| Screen Access | Từ trang chi tiết bài viết với nút "Xóa" trên bình luận |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                     | Description                       |
| ------------------------ | ------ | ---------------------------------------- | --------------------------------- |
| **Nút xóa bình luận**    | Button | Xóa                                      | Nút để xóa bình luận              |
| **Icon xóa**             | Icon   | Trash2                                   | Icon đại diện cho xóa             |
| **Modal xác nhận**       | Modal  | Modal xác nhận xóa                       | Modal để xác nhận xóa bình luận   |
| **Tiêu đề modal**        | Text   | Xác nhận xóa bình luận                   | Tiêu đề của modal xác nhận        |
| **Nội dung modal**       | Text   | Bạn có chắc chắn muốn xóa bình luận này? | Nội dung xác nhận xóa             |
| **Thông tin bình luận**  | Card   | Thông tin bình luận sẽ xóa               | Card hiển thị thông tin bình luận |
| **Nội dung bình luận**   | Text   | Nội dung bình luận                       | Nội dung của bình luận sẽ xóa     |
| **Thời gian bình luận**  | Text   | Thời gian bình luận                      | Thời gian bình luận được đăng     |
| **Số lượng tương tác**   | Text   | Số like, phản hồi                        | Số lượng tương tác của bình luận  |
| **Cảnh báo dữ liệu**     | Alert  | Cảnh báo về việc mất dữ liệu             | Cảnh báo về hậu quả của việc xóa  |
| **Nút xác nhận**         | Button | Xác nhận xóa                             | Nút để xác nhận xóa               |
| **Nút hủy**              | Button | Hủy                                      | Nút để hủy thao tác xóa           |
| **Thông báo thành công** | Toast  | Đã xóa bình luận                         | Thông báo khi xóa thành công      |
| **Thông báo lỗi**        | Toast  | Không thể xóa bình luận                  | Thông báo khi không thể xóa       |

#### 1.4.3 Hành động và xử lý:

| Action Name                 | Description                                                                                                                                                                                                                         | Success                                                                                                         | Failure                                                                                                                      |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Xóa bình luận**           | Cho phép người dùng xóa bình luận đã đăng với xác nhận trước khi thực hiện. Hệ thống sẽ hiển thị modal xác nhận với thông tin bình luận và cảnh báo về việc mất dữ liệu. Sau khi xóa, tất cả dữ liệu liên quan sẽ bị xóa vĩnh viễn. | Bình luận được xóa thành công và tất cả dữ liệu liên quan được xóa. Modal xác nhận được hiển thị trước khi xóa. | Bình luận không được xóa thành công hoặc dữ liệu liên quan không được xóa. Modal xác nhận không được hiển thị trước khi xóa. |
| **Xác nhận xóa**            | Cho phép người dùng xác nhận việc xóa bình luận thông qua modal xác nhận. Modal sẽ hiển thị thông tin chi tiết về bình luận, số lượng tương tác, và cảnh báo về hậu quả của việc xóa.                                               | Modal xác nhận được hiển thị với thông tin đầy đủ và người dùng có thể xác nhận dễ dàng.                        | Modal xác nhận không được hiển thị với thông tin đầy đủ hoặc người dùng không thể xác nhận dễ dàng.                          |
| **Xử lý dữ liệu liên quan** | Tự động xóa tất cả dữ liệu liên quan đến bình luận bao gồm like, phản hồi, và thông báo. Hệ thống sẽ thông báo cho người tương tác về việc bình luận đã bị xóa.                                                                     | Tất cả dữ liệu liên quan được xóa chính xác và thông báo được gửi đến người tương tác.                          | Dữ liệu liên quan không được xóa chính xác hoặc thông báo không được gửi đến người tương tác.                                |

### 1.5 CHỈNH SỬA BÌNH LUẬN

#### 1.5.1 Thông tin màn hình:

| Screen        | Chỉnh sửa bình luận                                           |
| ------------- | ------------------------------------------------------------- |
| Description   | Cho phép người dùng sửa đổi nội dung bình luận                |
| Screen Access | Từ trang chi tiết bài viết với nút "Chỉnh sửa" trên bình luận |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                     | Type      | Data                         | Description                         |
| ------------------------ | --------- | ---------------------------- | ----------------------------------- |
| **Nút chỉnh sửa**        | Button    | Chỉnh sửa                    | Nút để chỉnh sửa bình luận          |
| **Icon chỉnh sửa**       | Icon      | Edit                         | Icon đại diện cho chỉnh sửa         |
| **Form chỉnh sửa**       | Form      | Form chỉnh sửa bình luận     | Form để chỉnh sửa bình luận         |
| **Nội dung hiện tại**    | Textarea  | Nội dung bình luận hiện tại  | Ô nhập nội dung bình luận           |
| **Hình ảnh hiện tại**    | Image     | Hình ảnh đã đính kèm         | Hình ảnh hiện tại của bình luận     |
| **Nút thêm hình ảnh**    | Button    | Thêm hình ảnh                | Nút để thêm hình ảnh mới            |
| **Nút xóa hình ảnh**     | Button    | Xóa hình ảnh                 | Nút để xóa hình ảnh                 |
| **Upload hình ảnh mới**  | FileInput | Upload hình ảnh mới          | Ô upload hình ảnh mới               |
| **Preview hình ảnh mới** | Image     | Xem trước hình ảnh mới       | Xem trước hình ảnh mới              |
| **Lịch sử chỉnh sửa**    | Timeline  | Lịch sử các lần chỉnh sửa    | Timeline hiển thị lịch sử chỉnh sửa |
| **Nút lưu thay đổi**     | Button    | Lưu thay đổi                 | Nút để lưu các thay đổi             |
| **Nút hủy**              | Button    | Hủy                          | Nút để hủy chỉnh sửa                |
| **Thông báo thành công** | Toast     | Đã cập nhật bình luận        | Thông báo khi cập nhật thành công   |
| **Thông báo lỗi**        | Toast     | Không thể cập nhật bình luận | Thông báo khi không thể cập nhật    |

#### 1.5.3 Hành động và xử lý:

| Action Name               | Description                                                                                                                                                                                          | Success                                                                                                        | Failure                                                                                                                         |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Chỉnh sửa bình luận**   | Cho phép người dùng chỉnh sửa bình luận đã đăng bao gồm nội dung, hình ảnh đính kèm, và cài đặt quyền riêng tư. Hệ thống sẽ lưu lịch sử chỉnh sửa và thông báo cho người tương tác về việc cập nhật. | Bình luận được chỉnh sửa thành công và lịch sử được lưu. Thông báo được gửi đến người tương tác.               | Bình luận không được chỉnh sửa thành công hoặc lịch sử không được lưu. Thông báo không được gửi đến người tương tác.            |
| **Quản lý hình ảnh**      | Cho phép người dùng thêm, xóa, hoặc thay thế hình ảnh trong bình luận. Hệ thống sẽ hiển thị preview của hình ảnh mới và xác nhận trước khi thực hiện thay đổi.                                       | Hình ảnh được quản lý thành công và preview hiển thị chính xác. Xác nhận hoạt động đúng cách.                  | Hình ảnh không được quản lý thành công hoặc preview không hiển thị chính xác. Xác nhận không hoạt động đúng cách.               |
| **Lưu lịch sử chỉnh sửa** | Tự động lưu lịch sử các lần chỉnh sửa bình luận bao gồm thời gian, nội dung thay đổi, và người thực hiện. Hệ thống sẽ hiển thị timeline lịch sử để người dùng có thể theo dõi các thay đổi.          | Lịch sử chỉnh sửa được lưu đầy đủ và timeline hiển thị chính xác. Người dùng có thể theo dõi thay đổi dễ dàng. | Lịch sử chỉnh sửa không được lưu đầy đủ hoặc timeline không hiển thị chính xác. Người dùng không thể theo dõi thay đổi dễ dàng. |
