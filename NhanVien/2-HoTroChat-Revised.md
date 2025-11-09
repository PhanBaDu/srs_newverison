# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng quản lý đơn hàng của User_

## MỤC LỤC

1. [Chức năng quản lý đơn hàng](#1-chức-năng-quản-lý-đơn-hàng)
   - 1.1 [Hiển thị danh sách đơn hàng](#11-hiển-thị-danh-sách-đơn-hàng)
   - 1.2 [Xem chi tiết đơn hàng](#12-xem-chi-tiết-đơn-hàng)
   - 1.3 [Đặt lại đơn hàng](#13-đặt-lại-đơn-hàng)
   - 1.4 [Đánh giá đơn hàng](#14-đánh-giá-đơn-hàng)
   - 1.5 [Hủy đơn hàng](#15-hủy-đơn-hàng)
   - 1.6 [Theo dõi đơn hàng](#16-theo-dõi-đơn-hàng)
   - 1.7 [Yêu cầu đổi/trả hàng](#17-yêu-cầu-đổi-trả-hàng)

---

## 1. CHỨC NĂNG QUẢN LÝ ĐƠN HÀNG

### 1.1 HIỂN THỊ DANH SÁCH ĐƠN HÀNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách đơn hàng                                        |
| ------------- | --------------------------------------------------------- |
| Description   | Hiển thị danh sách đơn hàng đã đặt hàng / đã hủy đặt hàng |
| Screen Access | Từ trang tài khoản, click "Xem lịch sử giao dịch"         |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type      | Data                                                    | Description                              |
| ----------------------- | --------- | ------------------------------------------------------- | ---------------------------------------- |
| **Tiêu đề trang**       | Text      | Lịch sử đơn hàng                                        | Tiêu đề chính của trang                  |
| **Bộ lọc trạng thái**   | Select    | Tất cả, Chờ xử lý, Đang giao hàng, Đã giao hàng, Đã hủy, Đã hoàn tiền, Hoàn tiền một phần | Dropdown để lọc đơn hàng theo trạng thái |
| **Bộ lọc thời gian**    | Select    | 7 ngày qua, 30 ngày qua, 3 tháng qua, Tất cả            | Dropdown để lọc đơn hàng theo thời gian  |
| **Tìm kiếm đơn hàng**   | Input     | Nhập mã đơn hàng                                        | Input để tìm kiếm đơn hàng theo mã       |
| **Danh sách đơn hàng**  | Card List | Hiển thị từng đơn hàng                                  | Danh sách các đơn hàng                   |
| **Mã đơn hàng**         | Text      | Mã đơn hàng                                             | Mã định danh duy nhất của đơn hàng       |
| **Ngày đặt hàng**       | Text      | Ngày đặt hàng                                           | Ngày tạo đơn hàng                        |
| **Trạng thái đơn hàng** | Badge     | Trạng thái hiện tại                                     | Badge hiển thị trạng thái đơn hàng       |
| **Tổng tiền**           | Text      | Tổng tiền đơn hàng (VNĐ)                                | Tổng tiền của đơn hàng                   |
| **Nút xem chi tiết**    | Button    | Xem chi tiết                                            | Nút để xem chi tiết đơn hàng             |
| **Nút đặt lại**         | Button    | Đặt lại                                                 | Nút để đặt lại đơn hàng                  |

#### 1.1.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                           | Success                                                                                   | Failure                                                                                                       |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Hiển thị danh sách đơn hàng**  | Hiển thị tất cả đơn hàng của người dùng với thông tin cơ bản bao gồm mã đơn hàng, ngày đặt hàng, trạng thái, tổng tiền. Danh sách được sắp xếp theo thời gian đặt hàng mới nhất. Hỗ trợ phân trang để hiển thị nhiều đơn hàng.                        | Danh sách đơn hàng được hiển thị đầy đủ và chính xác. Giao diện rõ ràng và dễ sử dụng.    | Không thể hiển thị danh sách đơn hàng hoặc thông tin không chính xác. Giao diện bị lỗi hoặc không responsive. |
| **Lọc đơn hàng theo trạng thái** | Cho phép người dùng lọc đơn hàng theo trạng thái cụ thể như Chờ xử lý, Đang giao hàng, Đã giao hàng, Đã hủy. Khi chọn trạng thái, danh sách sẽ chỉ hiển thị những đơn hàng có trạng thái tương ứng. Hỗ trợ chọn "Tất cả" để hiển thị tất cả đơn hàng. | Đơn hàng được lọc theo trạng thái chính xác. Danh sách được cập nhật ngay lập tức.        | Không thể lọc đơn hàng theo trạng thái hoặc kết quả lọc không chính xác. Danh sách không được cập nhật.       |
| **Tìm kiếm đơn hàng**            | Cho phép người dùng tìm kiếm đơn hàng bằng cách nhập mã đơn hàng vào ô tìm kiếm. Hệ thống sẽ tìm kiếm và hiển thị đơn hàng có mã phù hợp. Tìm kiếm hỗ trợ tìm kiếm một phần của mã đơn hàng.                                                          | Đơn hàng được tìm thấy chính xác và hiển thị trong danh sách. Tìm kiếm hoạt động mượt mà. | Không thể tìm kiếm đơn hàng hoặc kết quả tìm kiếm không chính xác. Tìm kiếm không hoạt động hoặc chậm.        |

### 1.2 XEM CHI TIẾT ĐƠN HÀNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết đơn hàng                                   |
| ------------- | --------------------------------------------------- |
| Description   | Xem chi tiết đơn hàng đã đặt hàng / đã hủy đặt hàng |
| Screen Access | Từ danh sách đơn hàng, click "Xem chi tiết"         |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                     | Type      | Data                                     | Description                          |
| ------------------------ | --------- | ---------------------------------------- | ------------------------------------ |
| **Tiêu đề trang**        | Text      | Chi tiết đơn hàng                        | Tiêu đề chính của trang              |
| **Mã đơn hàng**          | Text      | Mã đơn hàng                              | Mã định danh duy nhất của đơn hàng   |
| **Trạng thái đơn hàng**  | Badge     | Trạng thái hiện tại                      | Badge hiển thị trạng thái đơn hàng   |
| **Thông tin khách hàng** | Card      | Thông tin người đặt hàng                 | Thông tin khách hàng                 |
| **Danh sách sản phẩm**   | Card List | Hiển thị sản phẩm trong đơn hàng         | Danh sách sản phẩm trong đơn hàng    |
| **Hình ảnh sản phẩm**    | Image     | Hình ảnh sản phẩm                        | Hình ảnh đại diện của sản phẩm       |
| **Tên sản phẩm**         | Text      | Tên sản phẩm                             | Tên đầy đủ của sản phẩm              |
| **Số lượng**             | Text      | Số lượng sản phẩm                        | Số lượng sản phẩm trong đơn hàng     |
| **Giá sản phẩm**         | Text      | Giá sản phẩm (VNĐ)                       | Giá của từng sản phẩm                |
| **Tổng tiền sản phẩm**   | Text      | Tổng tiền sản phẩm (VNĐ)                 | Tổng tiền của từng sản phẩm          |
| **Thông tin giao hàng**  | Card      | Thông tin người nhận và địa chỉ          | Thông tin giao hàng                  |
| **Thông tin thanh toán** | Card      | Phương thức và trạng thái thanh toán     | Thông tin thanh toán                 |
| **Tóm tắt đơn hàng**     | Card      | Tạm tính, phí vận chuyển, giảm giá, tổng | Tóm tắt chi phí đơn hàng             |
| **Lịch sử trạng thái**   | Timeline  | Timeline các trạng thái (bao gồm trạng thái hoàn tiền)                  | Hiển thị lịch sử thay đổi trạng thái |

#### 1.2.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                              | Success                                                                                                            | Failure                                                                                                                 |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị chi tiết đơn hàng**  | Hiển thị đầy đủ thông tin chi tiết của đơn hàng bao gồm thông tin khách hàng, danh sách sản phẩm, thông tin giao hàng, thông tin thanh toán, tóm tắt đơn hàng, và lịch sử trạng thái. Tất cả thông tin được trình bày rõ ràng và dễ đọc. | Chi tiết đơn hàng được hiển thị đầy đủ và chính xác. Giao diện rõ ràng và dễ đọc.                                  | Không thể hiển thị chi tiết đơn hàng hoặc thông tin không chính xác. Giao diện khó đọc hoặc thiếu thông tin quan trọng. |
| **Hiển thị lịch sử trạng thái** | Hiển thị timeline các thay đổi trạng thái của đơn hàng theo thời gian thực tế. Bao gồm thời gian thay đổi, trạng thái cũ và mới (bao gồm trạng thái hoàn tiền như "Đã hoàn tiền", "Hoàn tiền một phần"), và người thực hiện thay đổi. Timeline được sắp xếp theo thứ tự thời gian và dễ theo dõi.                | Lịch sử trạng thái được hiển thị đầy đủ và chính xác theo timeline, bao gồm cả trạng thái hoàn tiền. Thông tin được sắp xếp rõ ràng và dễ theo dõi. | Lịch sử trạng thái không được hiển thị đầy đủ hoặc không chính xác. Timeline không được sắp xếp đúng hoặc khó theo dõi. Trạng thái hoàn tiền không được hiển thị. |

### 1.3 ĐẶT LẠI ĐƠN HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Đặt lại đơn hàng                             |
| ------------- | -------------------------------------------- |
| Description   | Cho phép người dùng đặt lại đơn hàng đã mua  |
| Screen Access | Từ danh sách đơn hàng hoặc chi tiết đơn hàng |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                        | Description                      |
| ------------------------ | ------ | ------------------------------------------- | -------------------------------- |
| **Nút đặt lại**          | Button | Đặt lại                                     | Nút để đặt lại đơn hàng          |
| **Modal xác nhận**       | Dialog | Xác nhận đặt lại đơn hàng                   | Dialog để xác nhận đặt lại       |
| **Thông báo xác nhận**   | Text   | Bạn có chắc chắn muốn đặt lại đơn hàng này? | Thông báo xác nhận               |
| **Nút xác nhận**         | Button | Xác nhận                                    | Nút để xác nhận đặt lại          |
| **Nút hủy**              | Button | Hủy                                         | Nút để hủy đặt lại               |
| **Thông báo thành công** | Toast  | Đã thêm sản phẩm vào giỏ hàng               | Thông báo khi đặt lại thành công |
| **Thông báo lỗi**        | Toast  | Không thể đặt lại đơn hàng                  | Thông báo khi có lỗi xảy ra      |

#### 1.3.3 Hành động và xử lý:

| Action Name          | Description                                                                                                                                                                                                                                                                                      | Success                                                                                                                 | Failure                                                                                                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Đặt lại đơn hàng** | Cho phép người dùng đặt lại đơn hàng đã mua trước đó bằng cách thêm tất cả sản phẩm trong đơn hàng vào giỏ hàng với số lượng tương ứng. Hệ thống sẽ kiểm tra tồn kho của sản phẩm và chỉ thêm những sản phẩm còn hàng. Sau khi đặt lại thành công, người dùng sẽ được chuyển đến trang giỏ hàng. | Đơn hàng được đặt lại thành công và sản phẩm được thêm vào giỏ hàng. Người dùng được chuyển đến trang giỏ hàng.         | Không thể đặt lại đơn hàng hoặc sản phẩm không được thêm vào giỏ hàng. Người dùng không được chuyển đến trang giỏ hàng. |
| **Kiểm tra tồn kho** | Hệ thống tự động kiểm tra tồn kho của từng sản phẩm trong đơn hàng cũ trước khi đặt lại. Nếu sản phẩm hết hàng hoặc không đủ số lượng, hệ thống sẽ hiển thị thông báo và chỉ thêm những sản phẩm còn hàng.                                                                                       | Tồn kho được kiểm tra chính xác và thông báo được hiển thị khi cần thiết. Chỉ sản phẩm còn hàng được thêm vào giỏ hàng. | Không thể kiểm tra tồn kho hoặc thông tin tồn kho không chính xác. Sản phẩm hết hàng vẫn được thêm vào giỏ hàng.        |

### 1.4 ĐÁNH GIÁ ĐƠN HÀNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Đánh giá đơn hàng                                       |
| ------------- | ------------------------------------------------------- |
| Description   | Cho phép người dùng đánh giá sao và reviews về sản phẩm |
| Screen Access | Từ chi tiết đơn hàng đã giao hàng                       |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type        | Data                            | Description                           |
| ------------------------ | ----------- | ------------------------------- | ------------------------------------- |
| **Nút đánh giá**         | Button      | Đánh giá sản phẩm               | Nút để mở form đánh giá               |
| **Modal đánh giá**       | Dialog      | Đánh giá sản phẩm               | Dialog để đánh giá sản phẩm           |
| **Tên sản phẩm**         | Text        | Tên sản phẩm                    | Tên sản phẩm cần đánh giá             |
| **Hình ảnh sản phẩm**    | Image       | Hình ảnh sản phẩm               | Hình ảnh đại diện của sản phẩm        |
| **Đánh giá sao**         | Star Rating | 1-5 sao                         | Component để đánh giá bằng sao        |
| **Nhận xét**             | Textarea    | Nhận xét về sản phẩm            | Textarea để nhập nhận xét             |
| **Upload hình ảnh**      | File Input  | Upload hình ảnh                 | Input để upload hình ảnh đánh giá     |
| **Nút gửi đánh giá**     | Button      | Gửi đánh giá                    | Nút để gửi đánh giá                   |
| **Nút hủy**              | Button      | Hủy                             | Nút để hủy đánh giá                   |
| **Thông báo thành công** | Toast       | Đánh giá đã được gửi thành công | Thông báo khi gửi đánh giá thành công |

#### 1.4.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                                                                             | Success                                                                                              | Failure                                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Đánh giá sản phẩm**        | Cho phép người dùng đánh giá sản phẩm bằng cách chọn số sao (1-5), nhập nhận xét, và upload hình ảnh (tùy chọn). Đánh giá chỉ có thể thực hiện sau khi đơn hàng đã được giao hàng thành công. Hệ thống sẽ lưu đánh giá và hiển thị trên trang sản phẩm. | Đánh giá được gửi thành công và hiển thị trên trang sản phẩm. Thông báo xác nhận được hiển thị.      | Không thể gửi đánh giá hoặc đánh giá không được hiển thị trên trang sản phẩm. Thông báo lỗi được hiển thị. |
| **Upload hình ảnh đánh giá** | Cho phép người dùng upload hình ảnh để minh họa cho đánh giá của mình. Hệ thống hỗ trợ upload nhiều hình ảnh và tự động resize để tối ưu hiệu suất. Hình ảnh được lưu trữ an toàn và hiển thị trong đánh giá.                                           | Hình ảnh được upload thành công và hiển thị trong đánh giá. Upload hoạt động mượt mà và nhanh chóng. | Không thể upload hình ảnh hoặc hình ảnh không được hiển thị trong đánh giá. Upload chậm hoặc bị lỗi.       |

### 1.5 HỦY ĐƠN HÀNG

#### 1.5.1 Thông tin màn hình:

| Screen        | Hủy đơn hàng                                                                       |
| ------------- | ---------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng hủy đơn hàng nếu đơn hàng chưa vào trạng thái "đang giao hàng" |
| Screen Access | Từ chi tiết đơn hàng có trạng thái phù hợp                                         |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                     | Type     | Data                                    | Description                           |
| ------------------------ | -------- | --------------------------------------- | ------------------------------------- |
| **Nút hủy đơn hàng**     | Button   | Hủy đơn hàng                            | Nút để hủy đơn hàng                   |
| **Modal xác nhận**       | Dialog   | Xác nhận hủy đơn hàng                   | Dialog để xác nhận hủy đơn hàng       |
| **Thông báo xác nhận**   | Text     | Bạn có chắc chắn muốn hủy đơn hàng này? | Thông báo xác nhận                    |
| **Lý do hủy đơn hàng**   | Select   | Lý do hủy đơn hàng                      | Dropdown để chọn lý do hủy            |
| **Lý do chi tiết**       | Textarea | Nhập lý do hủy chi tiết (bắt buộc)     | Textarea để nhập lý do hủy tự do      |
| **Ghi chú**              | Textarea | Ghi chú thêm                            | Textarea để nhập ghi chú              |
| **Nút xác nhận hủy**     | Button   | Xác nhận hủy                            | Nút để xác nhận hủy đơn hàng          |
| **Nút hủy**              | Button   | Hủy                                     | Nút để hủy thao tác                   |
| **Thông báo thành công** | Toast    | Đơn hàng đã được hủy thành công         | Thông báo khi hủy đơn hàng thành công |
| **Thông báo lỗi**        | Toast    | Không thể hủy đơn hàng                  | Thông báo khi có lỗi xảy ra           |

#### 1.5.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                              | Success                                                                                                 | Failure                                                                                           |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Hủy đơn hàng**           | Cho phép người dùng hủy đơn hàng nếu đơn hàng chưa vào trạng thái "Đang giao hàng". Khi hủy đơn hàng, người dùng cần chọn lý do hủy và nhập lý do chi tiết (bắt buộc) bằng văn bản tự do. Hệ thống sẽ cập nhật trạng thái đơn hàng thành "Đã hủy" và hoàn tiền nếu đã thanh toán. Trạng thái hoàn tiền sẽ được cập nhật thành "Đã hoàn tiền" hoặc "Hoàn tiền một phần" tùy theo tình huống. | Đơn hàng được hủy thành công và trạng thái được cập nhật. Hoàn tiền được xử lý đúng cách và trạng thái hoàn tiền được cập nhật. | Không thể hủy đơn hàng hoặc trạng thái không được cập nhật. Hoàn tiền không được xử lý đúng cách. Lý do hủy chi tiết chưa được nhập. |
| **Kiểm tra điều kiện hủy** | Hệ thống tự động kiểm tra điều kiện để cho phép hủy đơn hàng. Chỉ những đơn hàng có trạng thái "Chờ xử lý" hoặc "Đã xác nhận" mới có thể được hủy. Đơn hàng đã vào trạng thái "Đang giao hàng" không thể hủy.                                            | Điều kiện hủy được kiểm tra chính xác và nút hủy được hiển thị/ẩn đúng cách.                            | Điều kiện hủy không được kiểm tra chính xác hoặc nút hủy được hiển thị khi không được phép.       |

### 1.6 THEO DÕI ĐƠN HÀNG

#### 1.6.1 Thông tin màn hình:

| Screen        | Theo dõi đơn hàng                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng theo dõi tình trạng đơn hàng mình đang ở đâu cũng như trạng thái của đơn hàng |
| Screen Access | Từ danh sách đơn hàng hoặc chi tiết đơn hàng                                                      |

#### 1.6.2 Chi tiết thành phần màn hình:

| Item                     | Type         | Data                        | Description                                 |
| ------------------------ | ------------ | --------------------------- | ------------------------------------------- |
| **Tiêu đề theo dõi**     | Text         | Theo dõi đơn hàng           | Tiêu đề của trang theo dõi                  |
| **Mã đơn hàng**          | Text         | Mã đơn hàng                 | Mã định danh duy nhất của đơn hàng          |
| **Trạng thái hiện tại**  | Badge        | Trạng thái hiện tại         | Badge hiển thị trạng thái đơn hàng          |
| **Timeline trạng thái**  | Timeline     | Timeline các trạng thái     | Hiển thị lịch sử thay đổi trạng thái        |
| **Thông tin vận chuyển** | Card         | Thông tin vận chuyển        | Thông tin về quá trình vận chuyển           |
| **Mã vận đơn**           | Text         | Mã vận đơn                  | Mã vận đơn để theo dõi                      |
| **Địa chỉ giao hàng**    | Text         | Địa chỉ giao hàng           | Địa chỉ nhận hàng                           |
| **Thời gian dự kiến**    | Text         | Thời gian giao hàng dự kiến | Thời gian dự kiến nhận hàng                 |
| **Nút liên hệ hỗ trợ**   | Button       | Liên hệ hỗ trợ              | Nút để liên hệ hỗ trợ khi cần thiết         |
| **Thông báo cập nhật**   | Notification | Thông báo khi có cập nhật   | Thông báo real-time khi trạng thái thay đổi |

#### 1.6.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                     | Success                                                                                                            | Failure                                                                                                                |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị trạng thái đơn hàng** | Hiển thị trạng thái hiện tại của đơn hàng và timeline các thay đổi trạng thái theo thời gian. Bao gồm các trạng thái: Chờ xử lý, Đã xác nhận, Đang chuẩn bị, Đang giao hàng, Đã giao hàng. Mỗi trạng thái được hiển thị với thời gian cụ thể và mô tả chi tiết. | Trạng thái đơn hàng được hiển thị chính xác và timeline được cập nhật real-time. Giao diện rõ ràng và dễ theo dõi. | Trạng thái đơn hàng không được hiển thị chính xác hoặc timeline không được cập nhật real-time. Giao diện khó theo dõi. |
| **Thông báo cập nhật real-time** | Hệ thống tự động gửi thông báo real-time khi có thay đổi trạng thái đơn hàng. Thông báo có thể được gửi qua email, SMS, hoặc push notification tùy theo cài đặt của người dùng.                                                                                 | Thông báo cập nhật được gửi real-time và chính xác. Người dùng nhận được thông tin đầy đủ về thay đổi trạng thái.  | Thông báo cập nhật không được gửi real-time hoặc không chính xác. Người dùng không nhận được thông tin về thay đổi.    |

### 1.7 YÊU CẦU ĐỔI/TRẢ HÀNG

#### 1.7.1 Thông tin màn hình:

| Screen        | Yêu cầu đổi/trả hàng                                             |
| ------------- | ---------------------------------------------------------------- |
| Description   | Cho phép người dùng gửi yêu cầu đổi hàng / trả hàng đến chủ shop |
| Screen Access | Từ chi tiết đơn hàng đã giao hàng                                |

#### 1.7.2 Chi tiết thành phần màn hình:

| Item                     | Type       | Data                           | Description                          |
| ------------------------ | ---------- | ------------------------------ | ------------------------------------ |
| **Nút yêu cầu đổi/trả**  | Button     | Yêu cầu đổi/trả hàng           | Nút để mở form yêu cầu               |
| **Modal yêu cầu**        | Dialog     | Yêu cầu đổi/trả hàng           | Dialog để gửi yêu cầu                |
| **Loại yêu cầu**         | Select     | Đổi hàng, Trả hàng             | Dropdown để chọn loại yêu cầu        |
| **Sản phẩm**             | Select     | Chọn sản phẩm cần đổi/trả      | Dropdown để chọn sản phẩm            |
| **Lý do**                | Select     | Lý do đổi/trả hàng             | Dropdown để chọn lý do               |
| **Mô tả chi tiết**       | Textarea   | Mô tả chi tiết về vấn đề       | Textarea để mô tả chi tiết           |
| **Upload hình ảnh**      | File Input | Upload hình ảnh minh chứng     | Input để upload hình ảnh             |
| **Nút gửi yêu cầu**      | Button     | Gửi yêu cầu                    | Nút để gửi yêu cầu                   |
| **Nút hủy**              | Button     | Hủy                            | Nút để hủy yêu cầu                   |
| **Thông báo thành công** | Toast      | Yêu cầu đã được gửi thành công | Thông báo khi gửi yêu cầu thành công |

#### 1.7.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                       | Success                                                                                                           | Failure                                                                                                        |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Gửi yêu cầu đổi/trả hàng**   | Cho phép người dùng gửi yêu cầu đổi hàng hoặc trả hàng với thông tin chi tiết bao gồm loại yêu cầu, sản phẩm, lý do, mô tả chi tiết, và hình ảnh minh chứng. Yêu cầu sẽ được gửi đến admin để xử lý và người dùng sẽ nhận được phản hồi trong thời gian sớm nhất. | Yêu cầu đổi/trả hàng được gửi thành công và admin nhận được thông báo. Người dùng nhận được xác nhận gửi yêu cầu. | Không thể gửi yêu cầu đổi/trả hàng hoặc admin không nhận được thông báo. Người dùng không nhận được xác nhận.  |
| **Upload hình ảnh minh chứng** | Cho phép người dùng upload hình ảnh để minh chứng cho yêu cầu đổi/trả hàng của mình. Hình ảnh có thể là ảnh sản phẩm bị lỗi, ảnh hóa đơn, hoặc các bằng chứng khác. Hệ thống hỗ trợ upload nhiều hình ảnh và tự động resize để tối ưu hiệu suất.                  | Hình ảnh minh chứng được upload thành công và hiển thị trong yêu cầu. Upload hoạt động mượt mà và nhanh chóng.    | Không thể upload hình ảnh minh chứng hoặc hình ảnh không được hiển thị trong yêu cầu. Upload chậm hoặc bị lỗi. |
