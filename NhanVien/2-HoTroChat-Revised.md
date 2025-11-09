# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng bảo mật của User_

## MỤC LỤC

1. [Chức năng bảo mật](#1-chức-năng-bảo-mật)
   - 1.1 [Khôi phục mật khẩu](#11-khôi-phục-mật-khẩu)
   - 1.2 [Lịch sử đăng nhập](#12-lịch-sử-đăng-nhập)
   - 1.3 [Xóa phiên đăng nhập](#13-xóa-phiên-đăng-nhập)

---

## 1. CHỨC NĂNG BẢO MẬT

### 1.1 KHÔI PHỤC MẬT KHẨU

#### 1.1.1 Thông tin màn hình:

| Screen        | Khôi phục mật khẩu                           |
| ------------- | -------------------------------------------- |
| Description   | Lấy lại mật khẩu qua email/SMS               |
| Screen Access | Từ trang đăng nhập với link "Quên mật khẩu?" |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                                       | Description                        |
| ------------------------ | ------ | ---------------------------------------------------------- | ---------------------------------- |
| **Tiêu đề trang**        | Text   | Quên mật khẩu                                              | Tiêu đề của trang khôi phục        |
| **Icon trang**           | Icon   | Mail                                                       | Icon đại diện cho email            |
| **Mô tả chức năng**      | Text   | Nhập email của bạn để nhận link khôi phục mật khẩu         | Mô tả ngắn gọn về chức năng        |
| **Form khôi phục**       | Form   | Form nhập email                                            | Form để nhập email khôi phục       |
| **Ô nhập email**         | Input  | Email                                                      | Ô nhập email để khôi phục          |
| **Nút gửi link**         | Button | Gửi link khôi phục                                         | Nút để gửi link khôi phục          |
| **Nút quay lại**         | Button | Quay lại đăng nhập                                         | Nút để quay lại trang đăng nhập    |
| **Thông báo thành công** | Toast  | Email khôi phục mật khẩu đã được gửi!                      | Thông báo khi gửi email thành công |
| **Thông báo lỗi**        | Toast  | Có lỗi xảy ra, vui lòng thử lại                            | Thông báo khi có lỗi xảy ra        |
| **Trạng thái gửi**       | Card   | Email đã được gửi                                          | Card hiển thị trạng thái gửi email |
| **Icon thành công**      | Icon   | CheckCircle                                                | Icon đại diện cho thành công       |
| **Thông báo gửi**        | Text   | Chúng tôi đã gửi link khôi phục mật khẩu đến email của bạn | Thông báo email đã được gửi        |
| **Hướng dẫn**            | Text   | Vui lòng kiểm tra hộp thư và làm theo hướng dẫn            | Hướng dẫn người dùng               |
| **Nút đăng nhập**        | Button | Quay lại đăng nhập                                         | Nút để quay lại trang đăng nhập    |

#### 1.1.3 Hành động và xử lý:

| Action Name             | Description                                                                                                                                                                                                                                    | Success                                                                                                               | Failure                                                                                                            |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Gửi link khôi phục**  | Cho phép người dùng nhập email để nhận link khôi phục mật khẩu. Hệ thống sẽ kiểm tra email có tồn tại trong cơ sở dữ liệu, tạo token khôi phục, và gửi email chứa link reset mật khẩu. Link có thời hạn sử dụng và chỉ có thể sử dụng một lần. | Email khôi phục được gửi thành công. Link reset được tạo và có thời hạn hợp lệ. Người dùng nhận được email hướng dẫn. | Email không tồn tại trong hệ thống. Lỗi khi gửi email. Token khôi phục không được tạo. Link reset không hoạt động. |
| **Xác thực email**      | Hệ thống kiểm tra tính hợp lệ của email và xác nhận email có tồn tại trong cơ sở dữ liệu. Email phải có định dạng hợp lệ và được đăng ký trong hệ thống. Hệ thống sẽ ghi lại thời gian yêu cầu khôi phục để tránh spam.                        | Email được xác thực thành công và tồn tại trong hệ thống. Thời gian yêu cầu được ghi lại.                             | Email không tồn tại trong hệ thống. Email có định dạng không hợp lệ. Yêu cầu khôi phục quá thường xuyên.           |
| **Tạo token khôi phục** | Hệ thống tạo token khôi phục duy nhất và an toàn cho mỗi yêu cầu khôi phục mật khẩu. Token có thời hạn sử dụng (thường là 1 giờ) và chỉ có thể sử dụng một lần. Token được mã hóa và lưu trữ an toàn trong cơ sở dữ liệu.                      | Token khôi phục được tạo thành công và lưu trữ an toàn. Token có thời hạn hợp lệ và tính duy nhất.                    | Lỗi khi tạo token. Token không được lưu trữ an toàn. Token có thời hạn không hợp lệ.                               |

### 1.2 LỊCH SỬ ĐĂNG NHẬP

#### 1.2.1 Thông tin màn hình:

| Screen        | Lịch sử đăng nhập                    |
| ------------- | ------------------------------------ |
| Description   | Xem các lần đăng nhập gần đây        |
| Screen Access | Từ trang tài khoản với tab "Bảo mật" |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                       | Type       | Data                                            | Description                        |
| -------------------------- | ---------- | ----------------------------------------------- | ---------------------------------- |
| **Tiêu đề tab**            | Text       | Lịch sử đăng nhập                               | Tiêu đề của tab lịch sử            |
| **Mô tả chức năng**        | Text       | Xem các lần đăng nhập gần đây của tài khoản     | Mô tả ngắn gọn về chức năng        |
| **Bộ lọc thời gian**       | Select     | Tất cả / Tuần này / Tháng này / 3 tháng gần đây | Dropdown để lọc theo thời gian     |
| **Bộ lọc thiết bị**        | Select     | Tất cả / Desktop / Mobile / Tablet              | Dropdown để lọc theo thiết bị      |
| **Bộ lọc trạng thái**      | Select     | Tất cả / Thành công / Thất bại                  | Dropdown để lọc theo trạng thái    |
| **Danh sách đăng nhập**    | List       | Danh sách lịch sử đăng nhập                     | Danh sách các lần đăng nhập        |
| **Card đăng nhập**         | Card       | Thông tin lần đăng nhập                         | Card hiển thị thông tin đăng nhập  |
| **Thời gian đăng nhập**    | Text       | Thời gian đăng nhập                             | Thời gian thực hiện đăng nhập      |
| **Địa chỉ IP**             | Text       | Địa chỉ IP                                      | Địa chỉ IP của thiết bị đăng nhập  |
| **Thiết bị**               | Text       | Tên thiết bị                                    | Tên thiết bị đăng nhập             |
| **Hệ điều hành**           | Text       | Hệ điều hành                                    | Hệ điều hành của thiết bị          |
| **Trình duyệt**            | Text       | Tên trình duyệt                                 | Tên trình duyệt sử dụng            |
| **Vị trí**                 | Text       | Vị trí địa lý                                   | Vị trí địa lý của đăng nhập        |
| **Trạng thái**             | Badge      | Thành công / Thất bại                           | Trạng thái của lần đăng nhập       |
| **Lý do thất bại**         | Text       | Lý do đăng nhập thất bại                        | Lý do khi đăng nhập thất bại       |
| **Nút xem chi tiết**       | Button     | Xem chi tiết                                    | Nút để xem chi tiết đăng nhập      |
| **Nút đăng xuất thiết bị** | Button     | Đăng xuất thiết bị                              | Nút để đăng xuất thiết bị khác     |
| **Phân trang**             | Pagination | Điều hướng trang                                | Phân trang cho danh sách đăng nhập |

#### 1.2.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                     | Success                                                                                                 | Failure                                                                                                                  |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Hiển thị lịch sử đăng nhập** | Hiển thị danh sách các lần đăng nhập gần đây của tài khoản với thông tin đầy đủ bao gồm thời gian, địa chỉ IP, thiết bị, hệ điều hành, trình duyệt, vị trí, và trạng thái. Danh sách được sắp xếp theo thời gian mới nhất và hỗ trợ phân trang. Hệ thống tự động phát hiện và đánh dấu đăng nhập lạ (từ thiết bị mới hoặc vị trí mới) và gửi thông báo qua email/SMS để cảnh báo người dùng.                 | Lịch sử đăng nhập được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc. Đăng nhập lạ được phát hiện và thông báo kịp thời.        | Lịch sử đăng nhập không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc. Đăng nhập lạ không được phát hiện hoặc không gửi thông báo.  |
| **Lọc lịch sử đăng nhập**      | Cho phép người dùng lọc lịch sử đăng nhập theo thời gian (Tất cả, Tuần này, Tháng này, 3 tháng gần đây), thiết bị (Tất cả, Desktop, Mobile, Tablet), và trạng thái (Tất cả, Thành công, Thất bại). Hệ thống sẽ cập nhật danh sách ngay lập tức khi có thay đổi. | Lịch sử được lọc chính xác theo tiêu chí đã chọn. Danh sách được cập nhật ngay lập tức khi có thay đổi. | Lịch sử không được lọc chính xác theo tiêu chí đã chọn. Danh sách không được cập nhật ngay lập tức khi có thay đổi.      |
| **Xem chi tiết đăng nhập**     | Cho phép người dùng xem chi tiết về một lần đăng nhập cụ thể bao gồm thông tin thiết bị, vị trí, thời gian, và các thông tin bảo mật khác. Chi tiết được hiển thị trong modal hoặc trang riêng.                                                                 | Chi tiết đăng nhập được hiển thị đầy đủ và chính xác. Thông tin bảo mật được trình bày rõ ràng.         | Chi tiết đăng nhập không được hiển thị đầy đủ hoặc không chính xác. Thông tin bảo mật không được trình bày rõ ràng.      |
| **Đăng xuất thiết bị khác**    | Cho phép người dùng đăng xuất các thiết bị khác đang đăng nhập vào tài khoản của mình. Hệ thống sẽ vô hiệu hóa phiên đăng nhập trên thiết bị được chọn và thông báo cho người dùng.                                                                             | Thiết bị được đăng xuất thành công. Phiên đăng nhập được vô hiệu hóa. Thông báo được gửi đến thiết bị.  | Thiết bị không được đăng xuất thành công. Phiên đăng nhập không được vô hiệu hóa. Thông báo không được gửi đến thiết bị. |

### 1.3 XÓA PHIÊN ĐĂNG NHẬP

#### 1.3.1 Thông tin màn hình:

| Screen        | Xóa phiên đăng nhập                  |
| ------------- | ------------------------------------ |
| Description   | Xóa phiên đăng nhập khỏi thiết bị    |
| Screen Access | Từ trang tài khoản với tab "Bảo mật" |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type   | Data                                             | Description                        |
| ------------------------ | ------ | ------------------------------------------------ | ---------------------------------- |
| **Tiêu đề tab**          | Text   | Quản lý phiên đăng nhập                          | Tiêu đề của tab quản lý phiên      |
| **Mô tả chức năng**      | Text   | Quản lý và xóa các phiên đăng nhập trên thiết bị | Mô tả ngắn gọn về chức năng        |
| **Phiên hiện tại**       | Card   | Thông tin phiên đăng nhập hiện tại               | Card hiển thị phiên hiện tại       |
| **Thiết bị hiện tại**    | Text   | Tên thiết bị hiện tại                            | Tên thiết bị đang đăng nhập        |
| **Thời gian đăng nhập**  | Text   | Thời gian đăng nhập hiện tại                     | Thời gian đăng nhập phiên hiện tại |
| **Địa chỉ IP hiện tại**  | Text   | Địa chỉ IP hiện tại                              | Địa chỉ IP của phiên hiện tại      |
| **Vị trí hiện tại**      | Text   | Vị trí địa lý hiện tại                           | Vị trí của phiên hiện tại          |
| **Nút đăng xuất tất cả** | Button | Đăng xuất tất cả thiết bị                        | Nút để đăng xuất tất cả thiết bị   |
| **Danh sách phiên khác** | List   | Danh sách phiên đăng nhập khác                   | Danh sách các phiên đăng nhập khác |
| **Card phiên**           | Card   | Thông tin phiên đăng nhập                        | Card hiển thị thông tin phiên      |
| **Thiết bị**             | Text   | Tên thiết bị                                     | Tên thiết bị của phiên             |
| **Hệ điều hành**         | Text   | Hệ điều hành                                     | Hệ điều hành của thiết bị          |
| **Trình duyệt**          | Text   | Tên trình duyệt                                  | Tên trình duyệt sử dụng            |
| **Thời gian hoạt động**  | Text   | Thời gian hoạt động cuối                         | Thời gian hoạt động cuối của phiên |
| **Trạng thái**           | Badge  | Hoạt động / Không hoạt động                      | Trạng thái của phiên đăng nhập     |
| **Nút xóa phiên**        | Button | Xóa phiên                                        | Nút để xóa phiên đăng nhập         |
| **Modal xác nhận**       | Modal  | Modal xác nhận xóa phiên                         | Modal để xác nhận xóa phiên        |
| **Tiêu đề modal**        | Text   | Xác nhận xóa phiên đăng nhập                     | Tiêu đề của modal xác nhận         |
| **Nội dung modal**       | Text   | Bạn có chắc chắn muốn xóa phiên đăng nhập này?   | Nội dung xác nhận xóa phiên        |
| **Thông tin phiên**      | Card   | Thông tin phiên sẽ xóa                           | Card hiển thị thông tin phiên      |
| **Nút xác nhận**         | Button | Xác nhận xóa                                     | Nút để xác nhận xóa phiên          |
| **Nút hủy**              | Button | Hủy                                              | Nút để hủy thao tác xóa            |
| **Thông báo thành công** | Toast  | Đã xóa phiên đăng nhập                           | Thông báo khi xóa phiên thành công |
| **Thông báo lỗi**        | Toast  | Không thể xóa phiên đăng nhập                    | Thông báo khi không thể xóa phiên  |

#### 1.3.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                            | Success                                                                                                                  | Failure                                                                                                                                       |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị phiên đăng nhập**  | Hiển thị danh sách tất cả phiên đăng nhập đang hoạt động của tài khoản với thông tin đầy đủ bao gồm thiết bị, hệ điều hành, trình duyệt, thời gian hoạt động, thời gian hết hạn, và trạng thái. Danh sách được sắp xếp theo thời gian hoạt động mới nhất. Hệ thống tự động đăng xuất phiên khi hết hạn (timeout) và cảnh báo trước khi hết hạn. | Danh sách phiên đăng nhập được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc. Thời gian hết hạn được hiển thị và cảnh báo hoạt động đúng.                 | Danh sách phiên đăng nhập không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc. Cảnh báo hết hạn không hoạt động.               |
| **Xóa phiên đăng nhập**       | Cho phép người dùng xóa một phiên đăng nhập cụ thể với xác nhận trước khi thực hiện. Hệ thống sẽ hiển thị modal xác nhận với thông tin phiên và vô hiệu hóa phiên đăng nhập trên thiết bị được chọn.                                   | Phiên đăng nhập được xóa thành công. Modal xác nhận được hiển thị trước khi xóa. Thiết bị được đăng xuất.                | Phiên đăng nhập không được xóa thành công. Modal xác nhận không được hiển thị trước khi xóa. Thiết bị không được đăng xuất.                   |
| **Đăng xuất tất cả thiết bị** | Cho phép người dùng đăng xuất tất cả thiết bị khác đang đăng nhập vào tài khoản của mình. Hệ thống sẽ vô hiệu hóa tất cả phiên đăng nhập trừ phiên hiện tại và thông báo cho người dùng.                                               | Tất cả thiết bị được đăng xuất thành công. Tất cả phiên đăng nhập được vô hiệu hóa. Thông báo được gửi đến các thiết bị. | Một số thiết bị không được đăng xuất thành công. Một số phiên đăng nhập không được vô hiệu hóa. Thông báo không được gửi đến một số thiết bị. |
| **Xác nhận xóa phiên**        | Cho phép người dùng xác nhận việc xóa phiên đăng nhập thông qua modal xác nhận. Modal sẽ hiển thị thông tin chi tiết về phiên, thiết bị, và cảnh báo về hậu quả của việc xóa.                                                          | Modal xác nhận được hiển thị với thông tin đầy đủ và người dùng có thể xác nhận dễ dàng.                                 | Modal xác nhận không được hiển thị với thông tin đầy đủ hoặc người dùng không thể xác nhận dễ dàng.                                           |
| **Cập nhật trạng thái phiên** | Tự động cập nhật trạng thái của các phiên đăng nhập dựa trên thời gian hoạt động cuối và thời gian hết hạn. Phiên không hoạt động trong thời gian dài hoặc đã hết hạn sẽ được đánh dấu là không hoạt động và tự động đăng xuất (auto logout). Hệ thống cảnh báo trước khi phiên hết hạn.                                         | Trạng thái phiên được cập nhật chính xác. Phiên không hoạt động hoặc hết hạn được đánh dấu đúng cách và tự động đăng xuất. Cảnh báo hết hạn hoạt động đúng.                                 | Trạng thái phiên không được cập nhật chính xác. Phiên không hoạt động không được đánh dấu đúng cách. Auto logout không hoạt động. Cảnh báo hết hạn không hoạt động.                                          |
