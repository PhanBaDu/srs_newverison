# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng đặt trước sản phẩm của User_

## MỤC LỤC

1. [Chức năng đặt trước sản phẩm](#1-chức-năng-đặt-trước-sản-phẩm)
   - 1.1 [Danh sách sản phẩm đã đặt trước](#11-danh-sách-sản-phẩm-đã-đặt-trước)
   - 1.2 [Đặt trước sản phẩm](#12-đặt-trước-sản-phẩm)
   - 1.3 [Xem chi tiết đặt trước](#13-xem-chi-tiết-đặt-trước)
   - 1.4 [Hủy đặt trước](#14-hủy-đặt-trước)
   - 1.5 [Quản lý trạng thái đặt trước](#15-quản-lý-trạng-thái-đặt-trước)

---

## 1. CHỨC NĂNG ĐẶT TRƯỚC SẢN PHẨM

### 1.1 DANH SÁCH SẢN PHẨM ĐÃ ĐẶT TRƯỚC

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách sản phẩm đã đặt trước |
| ------------- | ------------------------------- |
| Description   | Hiển thị danh sách đã đặt trước |
| Screen Access | Từ trang đặt trước sản phẩm     |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                       | Type   | Data                                                                | Description                          |
| -------------------------- | ------ | ------------------------------------------------------------------- | ------------------------------------ |
| **Tiêu đề trang**          | Text   | Đặt trước sản phẩm                                                  | Tiêu đề của trang đặt trước sản phẩm |
| **Icon trang**             | Icon   | Package                                                             | Icon đại diện cho đặt trước sản phẩm |
| **Danh sách đặt trước**    | List   | Danh sách các sản phẩm đã đặt trước                                 | Hiển thị danh sách đặt trước         |
| **Tab trạng thái**         | Tabs   | Tất cả / Chờ xử lý / Đã xác nhận / Đang chuẩn bị / Đã giao / Đã hủy | Tab để lọc theo trạng thái           |
| **Bộ lọc trạng thái**      | Select | Lọc theo trạng thái                                                 | Dropdown để lọc theo trạng thái      |
| **Bộ lọc loại sản phẩm**   | Select | Lọc theo loại sản phẩm                                              | Dropdown để lọc theo loại sản phẩm   |
| **Ô tìm kiếm**             | Input  | Tìm kiếm đặt trước                                                  | Ô để tìm kiếm đặt trước              |
| **Card đặt trước**         | Card   | Thông tin đặt trước                                                 | Card hiển thị thông tin đặt trước    |
| **Mã đặt trước**           | Text   | Mã định danh đặt trước                                              | Mã định danh của đặt trước           |
| **Tên sản phẩm**           | Text   | Tên sản phẩm                                                        | Tên sản phẩm đã đặt trước            |
| **Số lượng**               | Text   | Số lượng đặt trước                                                  | Số lượng sản phẩm đặt trước          |
| **Giá dự kiến**            | Text   | Giá dự kiến                                                         | Giá dự kiến của sản phẩm             |
| **Tổng tiền**              | Text   | Tổng tiền đặt trước                                                 | Tổng tiền của đặt trước              |
| **Tiền cọc**               | Text   | Tiền cọc đã đặt                                                     | Số tiền cọc đã đặt                   |
| **Số tiền còn lại**        | Text   | Số tiền còn lại                                                     | Số tiền còn lại cần thanh toán       |
| **Trạng thái**             | Badge  | Trạng thái xử lý                                                    | Trạng thái hiện tại của đặt trước    |
| **Mức độ ưu tiên**         | Badge  | Mức độ ưu tiên                                                      | Mức độ ưu tiên của đặt trước         |
| **Ngày tạo**               | Text   | Ngày tạo đặt trước                                                  | Thời gian tạo đặt trước              |
| **Ngày giao dự kiến**      | Text   | Ngày giao dự kiến                                                   | Thời gian giao hàng dự kiến          |
| **Phương thức thanh toán** | Text   | Phương thức thanh toán                                              | Phương thức thanh toán đã chọn       |
| **Nhân viên phụ trách**    | Text   | Nhân viên phụ trách                                                 | Tên nhân viên phụ trách              |
| **Ghi chú**                | Text   | Ghi chú                                                             | Ghi chú về đặt trước                 |
| **Nút xem chi tiết**       | Button | Xem chi tiết                                                        | Nút để xem chi tiết đặt trước        |
| **Nút hủy đặt trước**      | Button | Hủy đặt trước                                                       | Nút để hủy đặt trước                 |

#### 1.1.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                               | Success                                                                                                               | Failure                                                                                                                                |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị danh sách đặt trước** | Hiển thị danh sách tất cả các sản phẩm mà người dùng đã đặt trước với thông tin đầy đủ bao gồm mã đặt trước, tên sản phẩm, số lượng, giá dự kiến, tổng tiền, tiền cọc, số tiền còn lại, trạng thái, và thời gian tạo. Danh sách được sắp xếp theo thời gian tạo mới nhất. | Danh sách đặt trước được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                    | Danh sách đặt trước không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.              |
| **Lọc và tìm kiếm đặt trước**    | Cho phép người dùng lọc đặt trước theo trạng thái và loại sản phẩm, đồng thời tìm kiếm theo tên sản phẩm hoặc mã đặt trước. Hệ thống sẽ cập nhật danh sách ngay lập tức khi có thay đổi bộ lọc hoặc từ khóa tìm kiếm.                                                     | Đặt trước được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách được cập nhật ngay lập tức khi có thay đổi. | Đặt trước không được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách không được cập nhật ngay lập tức khi có thay đổi.      |
| **Theo dõi trạng thái**          | Cho phép người dùng theo dõi trạng thái của các đặt trước đã gửi thông qua các tab trạng thái như "Chờ xử lý", "Đã xác nhận", "Đang chuẩn bị", "Đã giao", và "Đã hủy". Trạng thái được cập nhật real-time khi admin xử lý.                                                | Trạng thái đặt trước được hiển thị chính xác và cập nhật real-time. Người dùng có thể theo dõi tiến độ xử lý dễ dàng. | Trạng thái đặt trước không được hiển thị chính xác hoặc không cập nhật real-time. Người dùng không thể theo dõi tiến độ xử lý dễ dàng. |

### 1.2 ĐẶT TRƯỚC SẢN PHẨM

#### 1.2.1 Thông tin màn hình:

| Screen        | Đặt trước sản phẩm                                          |
| ------------- | ----------------------------------------------------------- |
| Description   | Cho phép người dùng đặt hàng trước các sản phẩm chưa ra mắt |
| Screen Access | Từ trang sản phẩm hoặc trang đặt trước sản phẩm             |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                       | Type     | Data                          | Description                          |
| -------------------------- | -------- | ----------------------------- | ------------------------------------ |
| **Nút đặt trước**          | Button   | Đặt trước sản phẩm            | Nút để đặt trước sản phẩm            |
| **Icon đặt trước**         | Icon     | Package                       | Icon đại diện cho đặt trước          |
| **Form đặt trước**         | Form     | Form nhập thông tin đặt trước | Form để nhập thông tin đặt trước     |
| **Tên sản phẩm**           | Text     | Tên sản phẩm                  | Tên sản phẩm muốn đặt trước          |
| **Số lượng**               | Input    | Số lượng đặt trước            | Ô nhập số lượng đặt trước            |
| **Giá dự kiến**            | Text     | Giá dự kiến                   | Giá dự kiến của sản phẩm             |
| **Tổng tiền**              | Text     | Tổng tiền đặt trước           | Tổng tiền của đặt trước              |
| **Tiền cọc**               | Text     | Tiền cọc cần đặt              | Số tiền cọc cần đặt                  |
| **Số tiền còn lại**        | Text     | Số tiền còn lại               | Số tiền còn lại cần thanh toán       |
| **Phương thức thanh toán** | Select   | Phương thức thanh toán        | Dropdown chọn phương thức thanh toán |
| **Địa chỉ giao hàng**      | Textarea | Địa chỉ giao hàng             | Ô nhập địa chỉ giao hàng             |
| **Ngày giao dự kiến**      | Text     | Ngày giao dự kiến             | Thời gian giao hàng dự kiến          |
| **Ghi chú**                | Textarea | Ghi chú                       | Ô nhập ghi chú về đặt trước          |
| **Mức độ ưu tiên**         | Select   | Thấp / Trung bình / Cao       | Dropdown chọn mức độ ưu tiên         |
| **Nút xác nhận đặt trước** | Button   | Xác nhận đặt trước            | Nút để xác nhận đặt trước            |
| **Nút hủy**                | Button   | Hủy                           | Nút để hủy đặt trước                 |

#### 1.2.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                              | Success                                                                                                                     | Failure                                                                                                                                                      |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Tạo đặt trước sản phẩm**      | Cho phép người dùng tạo đặt trước sản phẩm mới bằng cách điền thông tin vào form bao gồm tên sản phẩm, số lượng, phương thức thanh toán, địa chỉ giao hàng, ghi chú, và mức độ ưu tiên. Hệ thống sẽ tính toán giá dự kiến, tiền cọc, và số tiền còn lại. | Đặt trước sản phẩm được tạo thành công và gửi đến admin. Form được điền đầy đủ thông tin và validation hoạt động đúng cách. | Đặt trước sản phẩm không được tạo thành công hoặc không được gửi đến admin. Form không được điền đầy đủ thông tin hoặc validation không hoạt động đúng cách. |
| **Tính toán giá tiền**          | Hệ thống tự động tính toán giá dự kiến, tiền cọc (thường là 20% tổng giá), và số tiền còn lại dựa trên số lượng và giá sản phẩm. Các tính toán được hiển thị real-time khi người dùng thay đổi số lượng.                                                 | Giá tiền được tính toán chính xác và hiển thị real-time. Người dùng có thể thấy rõ chi phí của đặt trước.                   | Giá tiền không được tính toán chính xác hoặc không hiển thị real-time. Người dùng không thể thấy rõ chi phí của đặt trước.                                   |
| **Chọn phương thức thanh toán** | Cho phép người dùng chọn phương thức thanh toán phù hợp từ các tùy chọn có sẵn như COD, Banking, MoMo, hoặc Credit Card. Phương thức thanh toán ảnh hưởng đến cách thức thanh toán tiền cọc và số tiền còn lại.                                          | Phương thức thanh toán được chọn chính xác và phù hợp. Hệ thống hỗ trợ nhiều phương thức thanh toán.                        | Phương thức thanh toán không được chọn chính xác hoặc không phù hợp. Hệ thống không hỗ trợ đầy đủ phương thức thanh toán.                                    |

### 1.3 XEM CHI TIẾT ĐẶT TRƯỚC

#### 1.3.1 Thông tin màn hình:

| Screen        | Xem chi tiết đặt trước                              |
| ------------- | --------------------------------------------------- |
| Description   | Xem trước đơn hàng đã đặt trước                     |
| Screen Access | Từ trang danh sách đặt trước với nút "Xem chi tiết" |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                       | Type     | Data                       | Description                          |
| -------------------------- | -------- | -------------------------- | ------------------------------------ |
| **Tiêu đề chi tiết**       | Text     | Chi tiết đặt trước         | Tiêu đề của trang chi tiết đặt trước |
| **Thông tin cơ bản**       | Card     | Thông tin đặt trước cơ bản | Card hiển thị thông tin cơ bản       |
| **Mã đặt trước**           | Text     | Mã định danh đặt trước     | Mã định danh của đặt trước           |
| **Tên sản phẩm**           | Text     | Tên sản phẩm               | Tên sản phẩm đã đặt trước            |
| **Số lượng**               | Text     | Số lượng đặt trước         | Số lượng sản phẩm đặt trước          |
| **Giá dự kiến**            | Text     | Giá dự kiến                | Giá dự kiến của sản phẩm             |
| **Tổng tiền**              | Text     | Tổng tiền đặt trước        | Tổng tiền của đặt trước              |
| **Tiền cọc**               | Text     | Tiền cọc đã đặt            | Số tiền cọc đã đặt                   |
| **Số tiền còn lại**        | Text     | Số tiền còn lại            | Số tiền còn lại cần thanh toán       |
| **Trạng thái**             | Badge    | Trạng thái xử lý           | Trạng thái hiện tại của đặt trước    |
| **Mức độ ưu tiên**         | Badge    | Mức độ ưu tiên             | Mức độ ưu tiên của đặt trước         |
| **Phương thức thanh toán** | Text     | Phương thức thanh toán     | Phương thức thanh toán đã chọn       |
| **Địa chỉ giao hàng**      | Text     | Địa chỉ giao hàng          | Địa chỉ giao hàng đã nhập            |
| **Ngày tạo**               | Text     | Ngày tạo đặt trước         | Thời gian tạo đặt trước              |
| **Ngày giao dự kiến**      | Text     | Ngày giao dự kiến          | Thời gian giao hàng dự kiến          |
| **Nhân viên phụ trách**    | Text     | Nhân viên phụ trách        | Tên nhân viên phụ trách              |
| **Ghi chú**                | Text     | Ghi chú                    | Ghi chú về đặt trước                 |
| **Lịch sử xử lý**          | Timeline | Lịch sử xử lý đặt trước    | Timeline hiển thị lịch sử xử lý      |
| **Nút quay lại**           | Button   | Quay lại                   | Nút để quay lại danh sách            |
| **Nút hủy đặt trước**      | Button   | Hủy đặt trước              | Nút để hủy đặt trước                 |

#### 1.3.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                            | Success                                                                                                                           | Failure                                                                                                                                    |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị chi tiết đặt trước** | Hiển thị chi tiết đầy đủ của đặt trước bao gồm thông tin cơ bản, phương thức thanh toán, địa chỉ giao hàng, thời gian tạo và giao dự kiến, nhân viên phụ trách, và ghi chú. Thông tin được hiển thị rõ ràng và dễ đọc. | Chi tiết đặt trước được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                                 | Chi tiết đặt trước không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.                   |
| **Hiển thị lịch sử xử lý**      | Hiển thị lịch sử xử lý đặt trước bao gồm các bước đã thực hiện, thời gian xử lý, và nhân viên phụ trách. Lịch sử được hiển thị dưới dạng timeline để dễ theo dõi tiến độ.                                              | Lịch sử xử lý được hiển thị đầy đủ và chính xác. Timeline được trình bày rõ ràng và dễ theo dõi.                                  | Lịch sử xử lý không được hiển thị đầy đủ hoặc không chính xác. Timeline không được trình bày rõ ràng hoặc khó theo dõi.                    |
| **Quay lại danh sách**          | Cho phép người dùng quay lại trang danh sách đặt trước từ trang chi tiết. Hệ thống sẽ lưu lại trạng thái lọc và tìm kiếm hiện tại.                                                                                     | Trang danh sách đặt trước được hiển thị với trạng thái lọc và tìm kiếm được lưu lại. Người dùng có thể tiếp tục làm việc dễ dàng. | Trang danh sách đặt trước không được hiển thị với trạng thái lọc và tìm kiếm được lưu lại. Người dùng không thể tiếp tục làm việc dễ dàng. |

### 1.4 HỦY ĐẶT TRƯỚC

#### 1.4.1 Thông tin màn hình:

| Screen        | Hủy đặt trước                                    |
| ------------- | ------------------------------------------------ |
| Description   | Cho phép hủy yêu cầu đặt trước                   |
| Screen Access | Từ trang danh sách đặt trước hoặc trang chi tiết |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                 | Description                     |
| ------------------------ | ------ | ------------------------------------ | ------------------------------- |
| **Nút hủy đặt trước**    | Button | Hủy đặt trước                        | Nút để hủy đặt trước            |
| **Icon hủy**             | Icon   | XCircle                              | Icon đại diện cho hủy           |
| **Modal xác nhận**       | Modal  | Modal xác nhận hủy                   | Modal để xác nhận hủy đặt trước |
| **Tiêu đề modal**        | Text   | Xác nhận hủy đặt trước               | Tiêu đề của modal xác nhận      |
| **Nội dung modal**       | Text   | Bạn có chắc chắn muốn hủy đặt trước? | Nội dung xác nhận hủy           |
| **Thông tin hoàn cọc**   | Text   | Thông tin hoàn cọc                   | Thông tin về việc hoàn cọc       |
| **Trạng thái hoàn cọc**  | Badge  | Chưa hoàn / Đã hoàn cọc / Đang xử lý | Trạng thái hoàn cọc             |
| **Lý do hoàn cọc**       | Text   | Lý do hoàn cọc                       | Lý do thực hiện hoàn cọc        |
| **Nút xác nhận**         | Button | Xác nhận                             | Nút để xác nhận hủy             |
| **Nút hủy**              | Button | Hủy                                  | Nút để hủy thao tác             |
| **Thông báo thành công** | Toast  | Đã hủy đặt trước                     | Thông báo khi hủy thành công    |
| **Thông báo lỗi**        | Toast  | Không thể hủy đặt trước              | Thông báo khi không thể hủy     |

#### 1.4.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                     | Success                                                                                                                          | Failure                                                                                                                                  |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Hủy đặt trước chưa xử lý** | Cho phép người dùng hủy đặt trước chưa được admin xử lý (trạng thái "Chờ xử lý"). Hệ thống sẽ hiển thị modal xác nhận trước khi hủy và loại bỏ đặt trước khỏi danh sách sau khi hủy thành công. Khi hủy, hệ thống sẽ tự động xử lý hoàn cọc cho người dùng và cập nhật trạng thái hoàn cọc. | Đặt trước được hủy thành công và loại bỏ khỏi danh sách. Modal xác nhận được hiển thị trước khi hủy. Hoàn cọc được xử lý và trạng thái được cập nhật.                             | Đặt trước không được hủy thành công hoặc không được loại bỏ khỏi danh sách. Modal xác nhận không được hiển thị trước khi hủy. Hoàn cọc không được xử lý.            |
| **Xác nhận hủy đặt trước**   | Cho phép người dùng xác nhận việc hủy đặt trước thông qua modal xác nhận. Modal sẽ hiển thị thông tin đặt trước, thông tin hoàn cọc (số tiền cọc sẽ được hoàn, thời gian hoàn dự kiến), và yêu cầu người dùng xác nhận trước khi thực hiện hủy.    | Modal xác nhận được hiển thị với thông tin đầy đủ về hoàn cọc và người dùng có thể xác nhận dễ dàng.                                         | Modal xác nhận không được hiển thị với thông tin đầy đủ về hoàn cọc hoặc người dùng không thể xác nhận dễ dàng.                                      |
| **Kiểm tra trạng thái hủy**  | Hệ thống kiểm tra trạng thái của đặt trước trước khi cho phép hủy. Chỉ những đặt trước có trạng thái "Chờ xử lý" mới có thể được hủy. Các đặt trước đã được xử lý không thể hủy. Khi hủy thành công, hệ thống sẽ tự động tạo yêu cầu hoàn cọc và cập nhật trạng thái hoàn cọc.                | Hệ thống kiểm tra trạng thái chính xác và chỉ cho phép hủy đặt trước chưa xử lý. Người dùng được thông báo rõ ràng về quyền hủy và quy trình hoàn cọc. | Hệ thống không kiểm tra trạng thái chính xác hoặc cho phép hủy đặt trước đã xử lý. Người dùng không được thông báo rõ ràng về quyền hủy và quy trình hoàn cọc. |

### 1.5 QUẢN LÝ TRẠNG THÁI ĐẶT TRƯỚC

#### 1.5.1 Thông tin màn hình:

| Screen        | Quản lý trạng thái đặt trước                        |
| ------------- | --------------------------------------------------- |
| Description   | Theo dõi và quản lý trạng thái các đặt trước        |
| Screen Access | Từ trang danh sách đặt trước với các tab trạng thái |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                                                | Description                                 |
| ------------------------ | ------ | ------------------------------------------------------------------- | ------------------------------------------- |
| **Tab trạng thái**       | Tabs   | Tất cả / Chờ xử lý / Đã xác nhận / Đang chuẩn bị / Đã giao / Đã hủy | Tab để lọc theo trạng thái                  |
| **Số lượng đặt trước**   | Text   | Số lượng đặt trước theo trạng thái                                  | Hiển thị số lượng đặt trước theo trạng thái |
| **Badge trạng thái**     | Badge  | Màu sắc và icon trạng thái                                          | Badge hiển thị trạng thái với màu sắc       |
| **Icon trạng thái**      | Icon   | Clock / CheckCircle / AlertCircle / Package / XCircle               | Icon đại diện cho trạng thái                |
| **Màu trạng thái**       | Color  | Vàng / Xanh / Xanh dương / Xanh lá / Đỏ                             | Màu sắc đại diện cho trạng thái             |
| **Thời gian cập nhật**   | Text   | Thời gian cập nhật cuối                                             | Thời gian cập nhật trạng thái cuối          |
| **Thông báo trạng thái** | Toast  | Thông báo thay đổi trạng thái                                       | Thông báo khi trạng thái thay đổi           |
| **Cập nhật real-time**   | System | Cập nhật tự động                                                    | Hệ thống cập nhật trạng thái tự động        |

#### 1.5.3 Hành động và xử lý:

| Action Name                       | Description                                                                                                                                                                              | Success                                                                                                                             | Failure                                                                                                                                              |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Theo dõi trạng thái real-time** | Cho phép người dùng theo dõi trạng thái của các đặt trước được cập nhật real-time khi admin xử lý. Hệ thống sẽ tự động cập nhật trạng thái và hiển thị thông báo khi có thay đổi.        | Trạng thái đặt trước được cập nhật real-time và thông báo được hiển thị kịp thời. Người dùng có thể theo dõi tiến độ xử lý dễ dàng. | Trạng thái đặt trước không được cập nhật real-time hoặc thông báo không được hiển thị kịp thời. Người dùng không thể theo dõi tiến độ xử lý dễ dàng. |
| **Lọc theo trạng thái**           | Cho phép người dùng lọc danh sách đặt trước theo trạng thái cụ thể thông qua các tab trạng thái. Mỗi tab sẽ hiển thị số lượng đặt trước tương ứng và danh sách đặt trước được lọc.       | Danh sách đặt trước được lọc chính xác theo trạng thái đã chọn. Số lượng đặt trước được hiển thị chính xác cho từng trạng thái.     | Danh sách đặt trước không được lọc chính xác theo trạng thái đã chọn. Số lượng đặt trước không được hiển thị chính xác cho từng trạng thái.          |
| **Hiển thị thông tin trạng thái** | Hiển thị thông tin chi tiết về trạng thái của đặt trước bao gồm thời gian thay đổi trạng thái, nhân viên xử lý, và ghi chú. Thông tin được hiển thị rõ ràng với màu sắc và icon phù hợp. | Thông tin trạng thái được hiển thị đầy đủ và chính xác. Màu sắc và icon được sử dụng phù hợp để dễ nhận biết.                       | Thông tin trạng thái không được hiển thị đầy đủ hoặc không chính xác. Màu sắc và icon không được sử dụng phù hợp để dễ nhận biết.                    |
