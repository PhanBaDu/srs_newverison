# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng khuyến mãi của User_

## MỤC LỤC

1. [Chức năng khuyến mãi](#1-chức-năng-khuyến-mãi)
   - 1.1 [Hiển thị các mã giảm giá](#11-hiển-thị-các-mã-giảm-giá)
   - 1.2 [Xem chi tiết mã giảm](#12-xem-chi-tiết-mã-giảm)
   - 1.3 [Áp dụng mã giảm giá](#13-áp-dụng-mã-giảm-giá)
   - 1.4 [Chức năng xếp hạng người dùng](#14-chức-năng-xếp-hạng-người-dùng)
   - 1.5 [Xem xếp hạng hiện tại](#15-xem-xếp-hạng-hiện-tại)
   - 1.6 [Mã giảm cho riêng từng sản phẩm](#16-mã-giảm-cho-riêng-từng-sản-phẩm)

---

## 1. CHỨC NĂNG KHUYẾN MÃI

### 1.1 HIỂN THỊ CÁC MÃ GIẢM GIÁ

#### 1.1.1 Thông tin màn hình:

| Screen        | Hiển thị các mã giảm giá                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Mã giảm giá được Admin tạo với số lượng có hạn và hiển thị ở các nơi mua hàng |
| Screen Access | Tích hợp trong trang giỏ hàng và trang sản phẩm                               |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type   | Data                             | Description                       |
| ------------------------- | ------ | -------------------------------- | --------------------------------- |
| **Tiêu đề khuyến mãi**    | Text   | Mã giảm giá                      | Tiêu đề của khu vực khuyến mãi    |
| **Icon khuyến mãi**       | Icon   | Percent                          | Icon đại diện cho khuyến mãi      |
| **Danh sách mã giảm giá** | Card   | Danh sách các mã giảm giá có sẵn | Hiển thị danh sách mã giảm giá    |
| **Mã giảm giá**           | Text   | WELCOME10, SAVE50K               | Mã code của giảm giá              |
| **Loại giảm giá**         | Badge  | Phần trăm / Cố định              | Loại giảm giá (percentage/fixed)  |
| **Mức giảm giá**          | Text   | 10% / 50.000 VNĐ                 | Mức giảm giá cụ thể               |
| **Điều kiện áp dụng**     | Text   | Đơn hàng tối thiểu               | Điều kiện để áp dụng mã giảm giá  |
| **Mô tả mã giảm giá**     | Text   | Mô tả chi tiết mã giảm giá       | Mô tả về mã giảm giá              |
| **Thời gian hiệu lực**    | Text   | Thời gian áp dụng                | Thời gian mã giảm giá có hiệu lực |
| **Số lượng còn lại**      | Text   | Số lượng mã còn lại              | Số lượng mã giảm giá còn lại      |
| **Giới hạn lượt dùng/user** | Text   | Số lượt dùng tối đa mỗi user     | Giới hạn số lần mỗi user có thể dùng |
| **Nút áp dụng**           | Button | Áp dụng mã                       | Nút để áp dụng mã giảm giá        |

#### 1.1.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                                          | Success                                                                                                                       | Failure                                                                                                                     |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị mã giảm giá**        | Hiển thị danh sách các mã giảm giá có sẵn với thông tin chi tiết bao gồm mã code, loại giảm giá, mức giảm giá, điều kiện áp dụng, và thời gian hiệu lực. Mã giảm giá được Admin tạo với số lượng có hạn và hiển thị ở các nơi mua hàng để người dùng có thể sử dụng. | Danh sách mã giảm giá được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ hiểu.                         | Không thể hiển thị danh sách mã giảm giá hoặc thông tin không chính xác. Giao diện khó đọc hoặc thiếu thông tin quan trọng. |
| **Hiển thị thông tin chi tiết** | Cung cấp thông tin chi tiết về từng mã giảm giá bao gồm mô tả, điều kiện áp dụng, thời gian hiệu lực, và số lượng còn lại. Thông tin được cập nhật real-time và phản ánh đúng tình trạng hiện tại của mã giảm giá.                                                   | Thông tin chi tiết được hiển thị đầy đủ và chính xác. Thông tin được cập nhật real-time và phản ánh đúng tình trạng hiện tại. | Thông tin chi tiết không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được cập nhật real-time.                |
| **Hiển thị điều kiện áp dụng**  | Hiển thị rõ ràng các điều kiện để áp dụng mã giảm giá như giá trị đơn hàng tối thiểu, loại sản phẩm áp dụng, và thời gian hiệu lực. Hệ thống tự động kiểm tra và hiển thị trạng thái khả dụng của mã giảm giá dựa trên điều kiện hiện tại.                           | Điều kiện áp dụng được hiển thị rõ ràng và chính xác. Hệ thống tự động kiểm tra trạng thái khả dụng đúng cách.                | Điều kiện áp dụng không được hiển thị rõ ràng hoặc không chính xác. Hệ thống không kiểm tra trạng thái khả dụng đúng cách.  |

### 1.2 XEM CHI TIẾT MÃ GIẢM GIÁ

#### 1.2.1 Thông tin màn hình:

| Screen        | Xem chi tiết mã giảm giá                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Cho phép người dùng xem chi tiết thông tin mức giảm giá và các thông tin khác |
| Screen Access | Từ trang giỏ hàng hoặc trang sản phẩm                                         |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                           | Type  | Data                                 | Description                         |
| ------------------------------ | ----- | ------------------------------------ | ----------------------------------- |
| **Tiêu đề chi tiết**           | Text  | Chi tiết mã giảm giá                 | Tiêu đề của trang chi tiết          |
| **Mã giảm giá**                | Text  | Mã code của giảm giá                 | Mã định danh của mã giảm giá        |
| **Loại giảm giá**              | Badge | Phần trăm / Cố định                  | Loại giảm giá                       |
| **Mức giảm giá**               | Text  | Mức giảm giá cụ thể                  | Mức giảm giá chi tiết               |
| **Mô tả chi tiết**             | Text  | Mô tả đầy đủ về mã giảm giá          | Mô tả chi tiết về mã giảm giá       |
| **Điều kiện áp dụng**          | Card  | Thông tin điều kiện áp dụng          | Hiển thị điều kiện áp dụng          |
| **Giá trị đơn hàng tối thiểu** | Text  | Giá trị đơn hàng tối thiểu           | Điều kiện giá trị đơn hàng          |
| **Loại sản phẩm áp dụng**      | Text  | Loại sản phẩm được áp dụng           | Điều kiện loại sản phẩm             |
| **Thời gian hiệu lực**         | Card  | Thông tin thời gian hiệu lực         | Hiển thị thời gian hiệu lực         |
| **Ngày bắt đầu**               | Text  | Ngày bắt đầu áp dụng                 | Thời gian bắt đầu hiệu lực          |
| **Ngày kết thúc**              | Text  | Ngày kết thúc áp dụng                | Thời gian kết thúc hiệu lực         |
| **Số lượng còn lại**           | Text  | Số lượng mã còn lại                  | Số lượng mã giảm giá còn lại        |
| **Giới hạn lượt dùng/user**    | Text  | Số lượt dùng tối đa mỗi user         | Giới hạn số lần mỗi user có thể dùng |
| **Trạng thái**                 | Badge | Có hiệu lực / Hết hạn / Hết số lượng | Trạng thái hiện tại của mã giảm giá |

#### 1.2.3 Hành động và xử lý:

| Action Name                       | Description                                                                                                                                                                                                                                                 | Success                                                                                                                     | Failure                                                                                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị chi tiết mã giảm giá** | Hiển thị đầy đủ thông tin chi tiết về mã giảm giá bao gồm mức giảm giá, mô tả, điều kiện áp dụng, thời gian hiệu lực, và trạng thái hiện tại. Thông tin được trình bày rõ ràng và dễ hiểu để người dùng có thể nắm bắt được tất cả các thông tin cần thiết. | Thông tin chi tiết mã giảm giá được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ hiểu.              | Thông tin chi tiết mã giảm giá không được hiển thị đầy đủ hoặc không chính xác. Thông tin được trình bày khó hiểu hoặc thiếu thông tin quan trọng. |
| **Kiểm tra trạng thái mã**        | Hệ thống tự động kiểm tra trạng thái hiện tại của mã giảm giá bao gồm tính hợp lệ, thời gian hiệu lực, và số lượng còn lại. Trạng thái được cập nhật real-time và hiển thị ngay lập tức khi có thay đổi.                                                    | Trạng thái mã giảm giá được kiểm tra chính xác và cập nhật real-time. Thông tin được hiển thị ngay lập tức khi có thay đổi. | Trạng thái mã giảm giá không được kiểm tra chính xác hoặc không được cập nhật real-time. Thông tin không được hiển thị ngay lập tức.               |
| **Hiển thị điều kiện áp dụng**    | Hiển thị rõ ràng các điều kiện để áp dụng mã giảm giá bao gồm giá trị đơn hàng tối thiểu, loại sản phẩm áp dụng, và các điều kiện đặc biệt khác. Điều kiện được trình bày một cách dễ hiểu và có thể kiểm tra được.                                         | Điều kiện áp dụng được hiển thị rõ ràng và chính xác. Điều kiện được trình bày dễ hiểu và có thể kiểm tra được.             | Điều kiện áp dụng không được hiển thị rõ ràng hoặc không chính xác. Điều kiện được trình bày khó hiểu hoặc không thể kiểm tra được.                |

### 1.3 ÁP DỤNG MÃ GIẢM GIÁ

#### 1.3.1 Thông tin màn hình:

| Screen        | Áp dụng mã giảm giá                                          |
| ------------- | ------------------------------------------------------------ |
| Description   | Cho phép người dùng nhập và áp dụng mã giảm giá vào đơn hàng |
| Screen Access | Tích hợp trong trang giỏ hàng                                |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                      | Description                       |
| ------------------------ | ------ | ------------------------- | --------------------------------- |
| **Tiêu đề áp dụng**      | Text   | Mã giảm giá               | Tiêu đề của khu vực áp dụng mã    |
| **Icon mã giảm giá**     | Icon   | Percent                   | Icon đại diện cho mã giảm giá     |
| **Ô nhập mã**            | Input  | Nhập mã giảm giá          | Ô để nhập mã giảm giá             |
| **Nút áp dụng**          | Button | Áp dụng                   | Nút để áp dụng mã giảm giá        |
| **Thông báo lỗi**        | Alert  | Thông báo lỗi             | Thông báo khi mã không hợp lệ     |
| **Thông báo thành công** | Alert  | Thông báo thành công      | Thông báo khi áp dụng thành công  |
| **Mã đã áp dụng**        | Card   | Thông tin mã đã áp dụng   | Hiển thị thông tin mã đã áp dụng  |
| **Tên mã**               | Text   | Tên mã giảm giá           | Tên của mã giảm giá               |
| **Mức giảm giá**         | Text   | Mức giảm giá được áp dụng | Mức giảm giá hiện tại             |
| **Số tiền giảm**         | Text   | Số tiền được giảm         | Số tiền được giảm từ đơn hàng     |
| **Nút xóa mã**           | Button | Xóa mã                    | Nút để xóa mã giảm giá đã áp dụng |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                        | Success                                                                                                                | Failure                                                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Nhập mã giảm giá**     | Cho phép người dùng nhập mã giảm giá vào ô input và hệ thống sẽ kiểm tra tính hợp lệ của mã. Mã giảm giá có thể được nhập bằng cách gõ trực tiếp hoặc copy-paste từ các nguồn khác. Hệ thống hỗ trợ cả mã viết hoa và viết thường. | Mã giảm giá được nhập thành công và hệ thống kiểm tra tính hợp lệ. Giao diện phản hồi nhanh chóng và chính xác.        | Không thể nhập mã giảm giá hoặc hệ thống không kiểm tra tính hợp lệ. Giao diện phản hồi chậm hoặc không chính xác.                   |
| **Kiểm tra mã giảm giá** | Hệ thống tự động kiểm tra tính hợp lệ của mã giảm giá bao gồm kiểm tra mã có tồn tại, còn hiệu lực, đủ điều kiện áp dụng, còn số lượng, và kiểm tra giới hạn lượt dùng của user (nếu có). Nếu mã hết số lượng hoặc user đã dùng hết lượt cho phép, hệ thống sẽ báo lỗi rõ ràng. Nếu mã hợp lệ, hệ thống sẽ hiển thị thông tin chi tiết và cho phép áp dụng.             | Mã giảm giá được kiểm tra chính xác và thông tin được hiển thị đầy đủ. Hệ thống phản hồi nhanh chóng và chính xác. Thông báo lỗi rõ ràng khi hết số lượng hoặc vượt quá giới hạn lượt dùng.     | Mã giảm giá không được kiểm tra chính xác hoặc thông tin không được hiển thị đầy đủ. Hệ thống phản hồi chậm hoặc không chính xác. Không báo lỗi rõ ràng khi hết số lượng hoặc vượt quá giới hạn.    |
| **Áp dụng mã giảm giá**  | Khi mã giảm giá hợp lệ, hệ thống sẽ tự động áp dụng vào đơn hàng và tính toán lại tổng tiền. Hệ thống sẽ giảm số lượng mã còn lại và tăng số lượt đã dùng của user (nếu có giới hạn). Mức giảm giá được tính theo loại mã (phần trăm hoặc cố định) và được hiển thị rõ ràng trong tổng kết đơn hàng.                        | Mã giảm giá được áp dụng thành công và tổng tiền được tính toán chính xác. Số lượng mã và lượt dùng được cập nhật. Thông tin được hiển thị rõ ràng và dễ hiểu. | Mã giảm giá không được áp dụng thành công hoặc tổng tiền không được tính toán chính xác. Số lượng mã và lượt dùng không được cập nhật. Thông tin không được hiển thị rõ ràng.      |
| **Xóa mã giảm giá**      | Cho phép người dùng xóa mã giảm giá đã áp dụng và hệ thống sẽ tính toán lại tổng tiền đơn hàng. Khi xóa mã, đơn hàng sẽ trở về trạng thái ban đầu không có giảm giá.                                                               | Mã giảm giá được xóa thành công và tổng tiền được tính toán lại chính xác. Giao diện được cập nhật ngay lập tức.       | Mã giảm giá không được xóa thành công hoặc tổng tiền không được tính toán lại chính xác. Giao diện không được cập nhật ngay lập tức. |

### 1.4 CHỨC NĂNG XẾP HẠNG NGƯỜI DÙNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Chức năng xếp hạng người dùng                                                        |
| ------------- | ------------------------------------------------------------------------------------ |
| Description   | Mỗi sản phẩm mua sẽ được quy đổi thành tổng giá trị chi tiêu để phân hạng người dùng |
| Screen Access | Tích hợp trong trang tài khoản người dùng                                            |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                         | Type     | Data                            | Description                          |
| ---------------------------- | -------- | ------------------------------- | ------------------------------------ |
| **Tiêu đề xếp hạng**         | Text     | Thông tin thành viên            | Tiêu đề của khu vực xếp hạng         |
| **Icon xếp hạng**            | Icon     | Crown                           | Icon đại diện cho xếp hạng           |
| **Hạng hiện tại**            | Badge    | Bronze, Silver, Gold, Platinum  | Hạng hiện tại của người dùng         |
| **Tổng chi tiêu**            | Text     | Tổng số tiền đã chi tiêu        | Tổng giá trị chi tiêu của người dùng |
| **Điểm tích lũy**            | Text     | Số điểm tích lũy                | Điểm tích lũy từ các giao dịch       |
| **Mức giảm giá**             | Text     | Phần trăm giảm giá theo hạng    | Mức giảm giá được hưởng theo hạng    |
| **Tiến độ hạng tiếp theo**   | Progress | Tiến độ đến hạng tiếp theo      | Thanh tiến độ đến hạng tiếp theo     |
| **Điều kiện hạng tiếp theo** | Text     | Điều kiện để lên hạng tiếp theo | Thông tin điều kiện lên hạng         |
| **Lịch sử giao dịch**        | Button   | Xem lịch sử giao dịch           | Nút để xem lịch sử giao dịch         |
| **Quyền lợi hạng**           | Card     | Danh sách quyền lợi theo hạng   | Hiển thị quyền lợi của hạng hiện tại |

#### 1.4.3 Hành động và xử lý:

| Action Name                 | Description                                                                                                                                                                                                                      | Success                                                                                                                  | Failure                                                                                                                                  |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Tính toán xếp hạng**      | Hệ thống tự động tính toán xếp hạng người dùng dựa trên tổng giá trị chi tiêu và các tiêu chí do Admin thiết lập. Mỗi sản phẩm mua sẽ được quy đổi thành điểm tích lũy và tổng giá trị chi tiêu để xác định hạng của người dùng. | Xếp hạng người dùng được tính toán chính xác và cập nhật real-time. Hệ thống phản ánh đúng tình trạng chi tiêu hiện tại. | Xếp hạng người dùng không được tính toán chính xác hoặc không được cập nhật real-time. Hệ thống không phản ánh đúng tình trạng chi tiêu. |
| **Hiển thị thông tin hạng** | Hiển thị đầy đủ thông tin về hạng hiện tại của người dùng bao gồm tên hạng, tổng chi tiêu, điểm tích lũy, mức giảm giá được hưởng, và tiến độ đến hạng tiếp theo. Thông tin được trình bày rõ ràng và dễ hiểu.                   | Thông tin hạng được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ hiểu.                           | Thông tin hạng không được hiển thị đầy đủ hoặc không chính xác. Thông tin được trình bày khó hiểu hoặc thiếu thông tin quan trọng.       |
| **Cập nhật tiến độ hạng**   | Hệ thống tự động cập nhật tiến độ đến hạng tiếp theo dựa trên chi tiêu hiện tại và điều kiện lên hạng. Tiến độ được hiển thị bằng thanh progress bar và thông tin cụ thể về số tiền cần chi thêm để lên hạng tiếp theo.          | Tiến độ hạng được cập nhật chính xác và hiển thị rõ ràng. Thông tin về điều kiện lên hạng được hiển thị đầy đủ.          | Tiến độ hạng không được cập nhật chính xác hoặc không được hiển thị rõ ràng. Thông tin về điều kiện lên hạng không được hiển thị đầy đủ. |

### 1.5 XEM XẾP HẠNG HIỆN TẠI

#### 1.5.1 Thông tin màn hình:

| Screen        | Xem xếp hạng hiện tại                                           |
| ------------- | --------------------------------------------------------------- |
| Description   | Hiển thị các thông tin đơn hàng, số tiền đã chi trong tháng/năm |
| Screen Access | Từ trang tài khoản người dùng                                   |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                        | Type  | Data                              | Description                            |
| --------------------------- | ----- | --------------------------------- | -------------------------------------- |
| **Tiêu đề thống kê**        | Text  | Thống kê chi tiêu                 | Tiêu đề của trang thống kê             |
| **Thống kê theo thời gian** | Card  | Thống kê chi tiêu theo thời gian  | Hiển thị thống kê theo thời gian       |
| **Chi tiêu tháng này**      | Text  | Số tiền chi tiêu trong tháng      | Tổng chi tiêu trong tháng hiện tại     |
| **Chi tiêu năm này**        | Text  | Số tiền chi tiêu trong năm        | Tổng chi tiêu trong năm hiện tại       |
| **Số đơn hàng**             | Text  | Tổng số đơn hàng đã đặt           | Tổng số đơn hàng đã thực hiện          |
| **Đơn hàng thành công**     | Text  | Số đơn hàng thành công            | Số đơn hàng đã hoàn thành thành công   |
| **Đơn hàng đang xử lý**     | Text  | Số đơn hàng đang xử lý            | Số đơn hàng đang trong quá trình xử lý |
| **Biểu đồ chi tiêu**        | Chart | Biểu đồ chi tiêu theo thời gian   | Biểu đồ hiển thị xu hướng chi tiêu     |
| **Top sản phẩm**            | Card  | Danh sách sản phẩm mua nhiều nhất | Hiển thị sản phẩm được mua nhiều nhất  |
| **Lịch sử giao dịch**       | Table | Bảng lịch sử giao dịch            | Hiển thị lịch sử giao dịch chi tiết    |

#### 1.5.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                | Success                                                                                                                | Failure                                                                                                                              |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị thống kê chi tiêu** | Hiển thị đầy đủ thống kê chi tiêu của người dùng bao gồm chi tiêu theo tháng/năm, số đơn hàng, và các chỉ số khác. Thống kê được tính toán chính xác và hiển thị theo định dạng dễ đọc.                    | Thống kê chi tiêu được hiển thị đầy đủ và chính xác. Thống kê được trình bày theo định dạng dễ đọc và hiểu.            | Thống kê chi tiêu không được hiển thị đầy đủ hoặc không chính xác. Thống kê được trình bày khó đọc hoặc không hiểu được.             |
| **Hiển thị biểu đồ chi tiêu**  | Hiển thị biểu đồ chi tiêu theo thời gian để người dùng có thể theo dõi xu hướng chi tiêu của mình. Biểu đồ được cập nhật real-time và hiển thị các thông tin quan trọng như xu hướng tăng/giảm chi tiêu.   | Biểu đồ chi tiêu được hiển thị chính xác và cập nhật real-time. Biểu đồ hiển thị xu hướng chi tiêu rõ ràng và dễ hiểu. | Biểu đồ chi tiêu không được hiển thị chính xác hoặc không được cập nhật real-time. Biểu đồ không hiển thị xu hướng chi tiêu rõ ràng. |
| **Hiển thị lịch sử giao dịch** | Hiển thị lịch sử giao dịch chi tiết của người dùng bao gồm thông tin đơn hàng, số tiền, thời gian, và trạng thái. Lịch sử được sắp xếp theo thời gian và có thể tìm kiếm, lọc theo các tiêu chí khác nhau. | Lịch sử giao dịch được hiển thị đầy đủ và chính xác. Lịch sử được sắp xếp hợp lý và có thể tìm kiếm, lọc dễ dàng.      | Lịch sử giao dịch không được hiển thị đầy đủ hoặc không chính xác. Lịch sử không được sắp xếp hợp lý hoặc khó tìm kiếm, lọc.         |

### 1.6 MÃ GIẢM CHO RIÊNG TỪNG SẢN PHẨM

#### 1.6.1 Thông tin màn hình:

| Screen        | Mã giảm cho riêng từng sản phẩm                                                   |
| ------------- | --------------------------------------------------------------------------------- |
| Description   | Mã giảm được Admin trực tiếp tạo ra cho từng sản phẩm và thông báo đến người dùng |
| Screen Access | Tích hợp trong trang sản phẩm và trang chi tiết sản phẩm                          |

#### 1.6.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                            | Description                         |
| ------------------------ | ------ | ------------------------------- | ----------------------------------- |
| **Tiêu đề mã sản phẩm**  | Text   | Khuyến mãi đặc biệt             | Tiêu đề của mã giảm giá sản phẩm    |
| **Badge khuyến mãi**     | Badge  | Giảm giá                        | Badge hiển thị có khuyến mãi        |
| **Mã giảm giá sản phẩm** | Text   | Mã code riêng cho sản phẩm      | Mã giảm giá dành riêng cho sản phẩm |
| **Mức giảm giá**         | Text   | Phần trăm hoặc số tiền giảm     | Mức giảm giá cụ thể cho sản phẩm    |
| **Giá gốc**              | Text   | Giá gốc của sản phẩm            | Giá ban đầu của sản phẩm            |
| **Giá sau giảm**         | Text   | Giá sau khi áp dụng mã giảm giá | Giá cuối cùng sau khi giảm giá      |
| **Thời gian áp dụng**    | Text   | Thời gian mã có hiệu lực        | Thời gian mã giảm giá có hiệu lực   |
| **Điều kiện áp dụng**    | Text   | Điều kiện để sử dụng mã         | Điều kiện để áp dụng mã giảm giá    |
| **Nút áp dụng mã**       | Button | Áp dụng mã                      | Nút để áp dụng mã giảm giá          |
| **Thông báo đặc biệt**   | Alert  | Thông báo về mã đặc biệt        | Thông báo về mã giảm giá đặc biệt   |

#### 1.6.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                              | Success                                                                                                               | Failure                                                                                                                       |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị mã sản phẩm**   | Hiển thị mã giảm giá dành riêng cho từng sản phẩm được Admin tạo ra. Mã giảm giá được hiển thị nổi bật trên trang sản phẩm với thông tin chi tiết về mức giảm giá, thời gian áp dụng, và điều kiện sử dụng.              | Mã giảm giá sản phẩm được hiển thị nổi bật và chính xác. Thông tin chi tiết được trình bày rõ ràng và dễ hiểu.        | Mã giảm giá sản phẩm không được hiển thị nổi bật hoặc không chính xác. Thông tin chi tiết không được trình bày rõ ràng.       |
| **Tính toán giá sau giảm** | Hệ thống tự động tính toán giá sau khi áp dụng mã giảm giá cho sản phẩm cụ thể. Giá được hiển thị rõ ràng với giá gốc và giá sau giảm để người dùng có thể so sánh và đưa ra quyết định mua hàng.                        | Giá sau giảm được tính toán chính xác và hiển thị rõ ràng. Người dùng có thể dễ dàng so sánh giá gốc và giá sau giảm. | Giá sau giảm không được tính toán chính xác hoặc không được hiển thị rõ ràng. Người dùng khó so sánh giá gốc và giá sau giảm. |
| **Thông báo mã đặc biệt**  | Hệ thống tự động thông báo đến người dùng về mã giảm giá đặc biệt cho sản phẩm thông qua các kênh thông báo như email, SMS, hoặc push notification. Thông báo bao gồm thông tin chi tiết về mã giảm giá và cách sử dụng. | Thông báo mã đặc biệt được gửi thành công và chính xác. Người dùng nhận được thông tin đầy đủ về mã giảm giá.         | Thông báo mã đặc biệt không được gửi thành công hoặc không chính xác. Người dùng không nhận được thông tin về mã giảm giá.    |
