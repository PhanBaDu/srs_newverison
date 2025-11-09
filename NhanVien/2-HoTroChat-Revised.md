# TỔNG HỢP CHỨC NĂNG USER

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng của User (Khách hàng)_

## MỤC LỤC

1. [Quản lý tài khoản](#1-quản-lý-tài-khoản)
   - 1.1 [Đăng ký tài khoản](#11-đăng-ký-tài-khoản)
   - 1.2 [Đăng nhập](#12-đăng-nhập)
   - 1.3 [Thông tin cá nhân](#13-thông-tin-cá-nhân)
   - 1.4 [Đổi mật khẩu](#14-đổi-mật-khẩu)
   - 1.5 [Đăng xuất](#15-đăng-xuất)

---

## 1. QUẢN LÝ TÀI KHOẢN

### 1.1 ĐĂNG KÝ TÀI KHOẢN

#### 1.1.1 Thông tin màn hình:

| Screen        | Đăng ký tài khoản                                                                           |
| ------------- | ------------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng tạo tài khoản mới để sử dụng hệ thống quản lý đặt hàng sản phẩm mô hình |
| Screen Access | User truy cập **/user/auth/register** hoặc click nút "Đăng ký" từ trang đăng nhập           |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                   | Type             | Data                                                     | Description                                 |
| ---------------------- | ---------------- | -------------------------------------------------------- | ------------------------------------------- |
| **Tiêu đề trang**      | Text             | Đăng ký tài khoản                                        | Tiêu đề chính của trang đăng ký             |
| **Mô tả chức năng**    | Text             | Tạo tài khoản mới để trải nghiệm dịch vụ mua sắm mô hình | Mô tả ngắn gọn về mục đích của trang        |
| **Form đăng ký**       | Form             |                                                          | Biểu mẫu nhập thông tin đăng ký             |
| **Họ và tên**          | Input (Text)     |                                                          | Ô nhập họ và tên đầy đủ của người dùng      |
| **Email**              | Input (Email)    |                                                          | Ô nhập địa chỉ email hợp lệ (kiểm tra trùng lặp real-time)                 |
| **Số điện thoại**      | Input (Tel)      |                                                          | Ô nhập số điện thoại liên hệ                |
| **Mật khẩu**           | Input (Password) |                                                          | Ô nhập mật khẩu bảo mật                     |
| **Xác nhận mật khẩu**  | Input (Password) |                                                          | Ô nhập lại mật khẩu để xác nhận             |
| **Địa chỉ**            | Textarea         |                                                          | Ô nhập địa chỉ giao hàng mặc định           |
| **Điều khoản sử dụng** | Checkbox         | Tôi đồng ý với điều khoản sử dụng                        | Xác nhận đồng ý với điều khoản của hệ thống |
| **Nút Đăng ký**        | Button           |                                                          | Nút để thực hiện đăng ký tài khoản          |
| **Nút Hủy**            | Button           |                                                          | Nút để hủy bỏ quá trình đăng ký             |
| **Link đăng nhập**     | Link             | Đã có tài khoản? Đăng nhập                               | Liên kết đến trang đăng nhập                |

#### 1.1.3 Hành động và xử lý:

| Action Name            | Description                                                                                                                                                                                                                                                                                                                              | Success                                                                                                                     | Failure                                                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Đăng ký tài khoản**  | Cho phép người dùng tạo tài khoản mới bằng cách nhập đầy đủ thông tin cá nhân bao gồm họ tên, email, số điện thoại, mật khẩu và địa chỉ. Hệ thống sẽ kiểm tra tính hợp lệ của email, độ mạnh của mật khẩu và tính duy nhất của thông tin. Sau khi đăng ký thành công, tài khoản sẽ được tạo và người dùng có thể đăng nhập ngay lập tức. | Tài khoản được tạo thành công. Người dùng được chuyển đến trang đăng nhập hoặc trang chủ. Email xác nhận được gửi (nếu có). | Email đã tồn tại trong hệ thống. Mật khẩu không đủ mạnh. Thông tin nhập vào không hợp lệ. Lỗi kết nối cơ sở dữ liệu. |
| **Xác thực thông tin** | Hệ thống kiểm tra tính hợp lệ của các trường thông tin nhập vào. Email phải có định dạng hợp lệ và chưa được sử dụng. Hệ thống kiểm tra email trùng lặp real-time khi người dùng nhập (không cần chờ submit), hiển thị cảnh báo ngay lập tức nếu email đã tồn tại. Mật khẩu phải có ít nhất 8 ký tự, bao gồm chữ hoa, chữ thường và số. Số điện thoại phải có định dạng Việt Nam hợp lệ. Tất cả các trường bắt buộc phải được điền đầy đủ.                                            | Tất cả thông tin được xác thực thành công. Form sẵn sàng để gửi đăng ký. Email được kiểm tra real-time và hiển thị trạng thái ngay lập tức.                                                    | Thông tin không hợp lệ. Email đã tồn tại (hiển thị cảnh báo ngay khi nhập). Mật khẩu không đủ mạnh. Các trường bắt buộc chưa được điền.                |
| **Gửi email xác nhận** | Sau khi đăng ký thành công, hệ thống tự động gửi email xác nhận đến địa chỉ email người dùng đã đăng ký. Email chứa liên kết kích hoạt tài khoản và thông tin hướng dẫn sử dụng hệ thống. Người dùng cần click vào liên kết để kích hoạt tài khoản trước khi có thể sử dụng đầy đủ các chức năng.                                        | Email xác nhận được gửi thành công. Người dùng nhận được email trong hộp thư.                                               | Lỗi khi gửi email. Địa chỉ email không tồn tại. Hệ thống email bị lỗi.                                               |

### 1.2 ĐĂNG NHẬP

#### 1.2.1 Thông tin màn hình:

| Screen        | Đăng nhập                                                                        |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng đăng nhập vào hệ thống bằng tài khoản và mật khẩu đã đăng ký |
| Screen Access | User truy cập **/user/auth/login** hoặc click nút "Đăng nhập" từ trang chủ       |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type             | Data                                                             | Description                                  |
| --------------------- | ---------------- | ---------------------------------------------------------------- | -------------------------------------------- |
| **Tiêu đề trang**     | Text             | Đăng nhập                                                        | Tiêu đề chính của trang đăng nhập            |
| **Mô tả chức năng**   | Text             | Đăng nhập để truy cập tài khoản và sử dụng các chức năng mua sắm | Mô tả ngắn gọn về mục đích của trang         |
| **Form đăng nhập**    | Form             |                                                                  | Biểu mẫu nhập thông tin đăng nhập            |
| **Email**             | Input (Email)    |                                                                  | Ô nhập địa chỉ email đã đăng ký              |
| **Mật khẩu**          | Input (Password) |                                                                  | Ô nhập mật khẩu tài khoản                    |
| **Ghi nhớ đăng nhập** | Checkbox         | Ghi nhớ đăng nhập                                                | Tùy chọn lưu thông tin đăng nhập             |
| **Quên mật khẩu**     | Link             | Quên mật khẩu?                                                   | Liên kết đến trang khôi phục mật khẩu        |
| **Captcha**           | Captcha          |                                                                  | Hiển thị captcha sau X lần đăng nhập sai (mặc định 3 lần)     |
| **Nút Đăng nhập**     | Button           |                                                                  | Nút để thực hiện đăng nhập                   |
| **Nút Hủy**           | Button           |                                                                  | Nút để hủy bỏ quá trình đăng nhập            |
| **Link đăng ký**      | Link             | Chưa có tài khoản? Đăng ký                                       | Liên kết đến trang đăng ký                   |
| **Đăng nhập xã hội**  | Button Group     | Google, Facebook                                                 | Các nút đăng nhập bằng tài khoản mạng xã hội |

#### 1.2.3 Hành động và xử lý:

| Action Name             | Description                                                                                                                                                                                                                                                                                              | Success                                                                                          | Failure                                                                                                 |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| **Đăng nhập tài khoản** | Cho phép người dùng đăng nhập vào hệ thống bằng email và mật khẩu đã đăng ký. Hệ thống sẽ xác thực thông tin đăng nhập, kiểm tra trạng thái tài khoản và tạo phiên đăng nhập. Sau khi đăng nhập thành công, người dùng sẽ được chuyển đến trang chủ và có thể sử dụng đầy đủ các chức năng của hệ thống. | Đăng nhập thành công. Người dùng được chuyển đến trang chủ. Phiên đăng nhập được tạo và lưu trữ. | Email hoặc mật khẩu không đúng. Tài khoản chưa được kích hoạt. Tài khoản bị khóa. Lỗi kết nối hệ thống. |
| **Xác thực thông tin**  | Hệ thống kiểm tra tính hợp lệ của email và mật khẩu. Email phải có định dạng hợp lệ và tồn tại trong hệ thống. Mật khẩu phải khớp với mật khẩu đã lưu trong cơ sở dữ liệu. Hệ thống sử dụng mã hóa để so sánh mật khẩu một cách an toàn. Hệ thống kiểm tra số lần đăng nhập sai liên tiếp và hiển thị captcha sau X lần sai (mặc định 3 lần). Nếu vượt quá số lần cho phép, tài khoản sẽ bị tạm khóa trong một khoảng thời gian nhất định.                                                                 | Thông tin đăng nhập được xác thực thành công. Tài khoản đang hoạt động bình thường.              | Email không tồn tại trong hệ thống. Mật khẩu không đúng. Tài khoản bị khóa hoặc chưa kích hoạt. Đã vượt quá số lần đăng nhập sai, cần nhập captcha hoặc chờ thời gian khóa tài khoản.         |
| **Tạo phiên đăng nhập** | Sau khi xác thực thành công, hệ thống tạo một phiên đăng nhập (session) cho người dùng. Phiên này chứa thông tin xác thực và được lưu trữ an toàn. Phiên đăng nhập có thời hạn sử dụng và có thể được gia hạn tự động nếu người dùng chọn "Ghi nhớ đăng nhập".                                           | Phiên đăng nhập được tạo thành công. Thông tin xác thực được lưu trữ an toàn.                    | Lỗi khi tạo phiên đăng nhập. Không thể lưu trữ thông tin xác thực. Hệ thống bảo mật gặp sự cố.          |

### 1.3 THÔNG TIN CÁ NHÂN

#### 1.3.1 Thông tin màn hình:

| Screen        | Thông tin cá nhân                                                                                                |
| ------------- | ---------------------------------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng xem và cập nhật thông tin cá nhân bao gồm họ tên, tuổi, số điện thoại, ảnh đại diện, địa chỉ |
| Screen Access | User truy cập **/user/account** hoặc click vào avatar/ảnh đại diện                                               |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type          | Data                                                         | Description                                    |
| --------------------- | ------------- | ------------------------------------------------------------ | ---------------------------------------------- |
| **Tiêu đề trang**     | Text          | Thông tin cá nhân                                            | Tiêu đề chính của trang quản lý tài khoản      |
| **Mô tả chức năng**   | Text          | Quản lý và cập nhật thông tin cá nhân của bạn                | Mô tả ngắn gọn về mục đích của trang           |
| **Ảnh đại diện**      | Avatar        |                                                              | Hiển thị ảnh đại diện hiện tại của người dùng  |
| **Nút đổi ảnh**       | Button        | Đổi ảnh đại diện                                             | Nút để thay đổi ảnh đại diện                   |
| **Form thông tin**    | Form          |                                                              | Biểu mẫu chỉnh sửa thông tin cá nhân           |
| **Họ và tên**         | Input (Text)  |                                                              | Ô nhập họ và tên đầy đủ                        |
| **Email**             | Input (Email) |                                                              | Ô nhập địa chỉ email (chỉ đọc)                 |
| **Số điện thoại**     | Input (Tel)   |                                                              | Ô nhập số điện thoại liên hệ                   |
| **Ngày sinh**         | Input (Date)  |                                                              | Ô nhập ngày sinh                               |
| **Giới tính**         | Select        | Nam, Nữ, Khác                                                | Lựa chọn giới tính                             |
| **Địa chỉ**           | Textarea      |                                                              | Ô nhập địa chỉ giao hàng mặc định              |
| **Thành phố**         | Select        | Hà Nội, TP.HCM, Đà Nẵng, ...                                 | Lựa chọn thành phố                             |
| **Quận/Huyện**        | Select        |                                                              | Lựa chọn quận/huyện dựa trên thành phố đã chọn |
| **Phường/Xã**         | Select        |                                                              | Lựa chọn phường/xã dựa trên quận/huyện đã chọn |
| **Nút Lưu**           | Button        |                                                              | Nút để lưu thay đổi thông tin                  |
| **Nút Hủy**           | Button        |                                                              | Nút để hủy bỏ các thay đổi                     |
| **Thông tin bổ sung** | Card          | Ngày tham gia, Hạng thành viên, Tổng đơn hàng, Tổng chi tiêu | Hiển thị thông tin thống kê của tài khoản      |

#### 1.3.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                                                 | Success                                                                                                               | Failure                                                                                              |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **Cập nhật thông tin**     | Cho phép người dùng chỉnh sửa và cập nhật thông tin cá nhân bao gồm họ tên, số điện thoại, ngày sinh, giới tính, địa chỉ. Hệ thống sẽ kiểm tra tính hợp lệ của thông tin mới và cập nhật vào cơ sở dữ liệu. Email không thể thay đổi để đảm bảo tính bảo mật của tài khoản. | Thông tin được cập nhật thành công. Dữ liệu mới được lưu vào cơ sở dữ liệu. Giao diện hiển thị thông tin đã cập nhật. | Thông tin không hợp lệ. Số điện thoại đã được sử dụng bởi tài khoản khác. Lỗi kết nối cơ sở dữ liệu. |
| **Đổi ảnh đại diện**       | Cho phép người dùng tải lên và thay đổi ảnh đại diện của tài khoản. Hệ thống hỗ trợ các định dạng ảnh phổ biến (JPG, PNG, GIF) và tự động resize ảnh về kích thước phù hợp. Ảnh cũ sẽ được thay thế hoàn toàn bằng ảnh mới.                                                 | Ảnh đại diện được cập nhật thành công. Ảnh mới hiển thị trên giao diện. Ảnh cũ được xóa khỏi hệ thống.                | Định dạng ảnh không được hỗ trợ. Kích thước ảnh quá lớn. Lỗi khi tải lên file.                       |
| **Xem thông tin thống kê** | Hiển thị các thông tin thống kê về tài khoản như ngày tham gia, hạng thành viên, tổng số đơn hàng đã đặt, tổng số tiền đã chi tiêu. Thông tin này giúp người dùng theo dõi hoạt động mua sắm và hiểu rõ hơn về tình trạng tài khoản của mình.                               | Thông tin thống kê được hiển thị chính xác. Dữ liệu được cập nhật theo thời gian thực.                                | Không thể tải thông tin thống kê. Dữ liệu hiển thị không chính xác. Lỗi kết nối cơ sở dữ liệu.       |

### 1.4 ĐỔI MẬT KHẨU

#### 1.4.1 Thông tin màn hình:

| Screen        | Đổi mật khẩu                                                                             |
| ------------- | ---------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng thay đổi mật khẩu đăng nhập hiện tại để tăng cường bảo mật tài khoản |
| Screen Access | User truy cập **/user/account** và chọn tab "Bảo mật" hoặc click "Đổi mật khẩu"          |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                      | Type             | Data                                                                | Description                               |
| ------------------------- | ---------------- | ------------------------------------------------------------------- | ----------------------------------------- |
| **Tiêu đề trang**         | Text             | Đổi mật khẩu                                                        | Tiêu đề chính của trang đổi mật khẩu      |
| **Mô tả chức năng**       | Text             | Thay đổi mật khẩu để bảo vệ tài khoản của bạn                       | Mô tả ngắn gọn về mục đích của trang      |
| **Form đổi mật khẩu**     | Form             |                                                                     | Biểu mẫu nhập thông tin đổi mật khẩu      |
| **Mật khẩu hiện tại**     | Input (Password) |                                                                     | Ô nhập mật khẩu hiện tại để xác thực      |
| **Mật khẩu mới**          | Input (Password) |                                                                     | Ô nhập mật khẩu mới                       |
| **Xác nhận mật khẩu mới** | Input (Password) |                                                                     | Ô nhập lại mật khẩu mới để xác nhận       |
| **Hiển thị mật khẩu**     | Checkbox         | Hiển thị mật khẩu                                                   | Tùy chọn hiển thị mật khẩu dạng text      |
| **Xác thực 2 bước (2FA)** | Checkbox         | Sử dụng xác thực 2 bước                                             | Tùy chọn bật xác thực 2 bước              |
| **Phương thức 2FA**        | Select           | Email OTP / SMS OTP                                                 | Chọn phương thức xác thực 2 bước          |
| **Mã OTP**                 | Input            |                                                                     | Ô nhập mã OTP khi bật 2FA                 |
| **Yêu cầu mật khẩu**      | Text             | Mật khẩu phải có ít nhất 8 ký tự, bao gồm chữ hoa, chữ thường và số | Hướng dẫn yêu cầu về độ mạnh của mật khẩu | 
| **Nút Đổi mật khẩu**      | Button           |                                                                     | Nút để thực hiện đổi mật khẩu             |
| **Nút Hủy**               | Button           |                                                                     | Nút để hủy bỏ quá trình đổi mật khẩu      |

#### 1.4.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                                                                               | Success                                                                                                    | Failure                                                                                                                    |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Đổi mật khẩu**               | Cho phép người dùng thay đổi mật khẩu đăng nhập hiện tại. Người dùng cần nhập mật khẩu hiện tại để xác thực, sau đó nhập mật khẩu mới và xác nhận lại. Nếu người dùng đã bật xác thực 2 bước (2FA), hệ thống sẽ yêu cầu nhập mã OTP được gửi qua email hoặc SMS để xác thực thêm. Hệ thống sẽ kiểm tra tính hợp lệ của mật khẩu mới và cập nhật vào cơ sở dữ liệu. Sau khi đổi mật khẩu thành công, tất cả các phiên đăng nhập cũ sẽ bị vô hiệu hóa. | Mật khẩu được thay đổi thành công. Tất cả phiên đăng nhập cũ bị vô hiệu hóa. Người dùng cần đăng nhập lại. | Mật khẩu hiện tại không đúng. Mật khẩu mới không đủ mạnh. Mật khẩu mới và xác nhận không khớp. Mã OTP không đúng hoặc đã hết hạn (nếu bật 2FA). Lỗi cập nhật cơ sở dữ liệu. |
| **Xác thực mật khẩu hiện tại** | Hệ thống kiểm tra mật khẩu hiện tại người dùng nhập vào có khớp với mật khẩu đã lưu trong cơ sở dữ liệu hay không. Việc xác thực được thực hiện một cách an toàn bằng cách so sánh hash của mật khẩu. Nếu người dùng đã bật xác thực 2 bước, hệ thống sẽ gửi mã OTP qua email hoặc SMS và yêu cầu nhập mã để xác thực thêm trước khi cho phép đổi mật khẩu.                                                                                                                     | Mật khẩu hiện tại được xác thực thành công. Nếu bật 2FA, mã OTP được gửi và xác thực thành công. Người dùng có thể tiếp tục đổi mật khẩu.                       | Mật khẩu hiện tại không đúng. Tài khoản bị khóa. Mã OTP không đúng hoặc đã hết hạn (nếu bật 2FA). Lỗi xác thực hệ thống.                                                    |
| **Kiểm tra độ mạnh mật khẩu**  | Hệ thống kiểm tra mật khẩu mới có đáp ứng các yêu cầu bảo mật hay không. Mật khẩu phải có ít nhất 8 ký tự, bao gồm ít nhất một chữ hoa, một chữ thường và một số. Mật khẩu không được trùng với mật khẩu hiện tại hoặc các mật khẩu đã sử dụng gần đây.                                                                   | Mật khẩu mới đáp ứng tất cả yêu cầu bảo mật. Hệ thống cho phép tiếp tục quá trình đổi mật khẩu.            | Mật khẩu mới không đủ mạnh. Mật khẩu trùng với mật khẩu hiện tại. Mật khẩu đã được sử dụng gần đây.                        |

### 1.5 ĐĂNG XUẤT

#### 1.5.1 Thông tin màn hình:

| Screen        | Đăng xuất                                                                        |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng đăng xuất khỏi hệ thống và kết thúc phiên đăng nhập hiện tại |
| Screen Access | User click vào nút "Đăng xuất" từ menu sidebar hoặc dropdown tài khoản           |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                   | Type   | Data                                                                     | Description                             |
| ---------------------- | ------ | ------------------------------------------------------------------------ | --------------------------------------- |
| **Xác nhận đăng xuất** | Modal  |                                                                          | Cửa sổ xác nhận trước khi đăng xuất     |
| **Tiêu đề modal**      | Text   | Xác nhận đăng xuất                                                       | Tiêu đề của cửa sổ xác nhận             |
| **Nội dung xác nhận**  | Text   | Bạn có chắc chắn muốn đăng xuất khỏi hệ thống?                           | Thông báo xác nhận hành động đăng xuất  |
| **Nút Xác nhận**       | Button | Đăng xuất                                                                | Nút để xác nhận đăng xuất               |
| **Nút Hủy**            | Button | Hủy                                                                      | Nút để hủy bỏ hành động đăng xuất       |
| **Thông tin phiên**    | Text   | Phiên đăng nhập sẽ kết thúc và bạn cần đăng nhập lại để tiếp tục sử dụng | Thông báo về hậu quả của việc đăng xuất |

#### 1.5.3 Hành động và xử lý:

| Action Name             | Description                                                                                                                                                                                                                                                                      | Success                                                                                                                 | Failure                                                                                       |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Đăng xuất tài khoản** | Cho phép người dùng kết thúc phiên đăng nhập hiện tại và đăng xuất khỏi hệ thống. Hệ thống sẽ xóa thông tin xác thực khỏi phiên đăng nhập, vô hiệu hóa token xác thực và chuyển người dùng về trang đăng nhập. Tất cả dữ liệu tạm thời trong phiên sẽ bị xóa để đảm bảo bảo mật. | Đăng xuất thành công. Phiên đăng nhập được kết thúc. Người dùng được chuyển về trang đăng nhập. Dữ liệu phiên được xóa. | Lỗi khi kết thúc phiên đăng nhập. Không thể xóa dữ liệu phiên. Lỗi chuyển hướng trang.        |
| **Xác nhận đăng xuất**  | Hiển thị cửa sổ xác nhận trước khi thực hiện đăng xuất để đảm bảo người dùng thực sự muốn kết thúc phiên đăng nhập. Cửa sổ này giúp tránh việc đăng xuất nhầm và cung cấp thông tin về hậu quả của hành động.                                                                    | Cửa sổ xác nhận hiển thị thành công. Người dùng có thể lựa chọn tiếp tục hoặc hủy bỏ.                                   | Không thể hiển thị cửa sổ xác nhận. Lỗi giao diện người dùng.                                 |
| **Xóa dữ liệu phiên**   | Sau khi xác nhận đăng xuất, hệ thống sẽ xóa tất cả dữ liệu liên quan đến phiên đăng nhập hiện tại bao gồm token xác thực, thông tin tạm thời và các biến phiên. Điều này đảm bảo rằng không có thông tin nhạy cảm nào được lưu trữ sau khi người dùng đăng xuất.                 | Dữ liệu phiên được xóa thành công. Không còn thông tin nhạy cảm nào được lưu trữ.                                       | Không thể xóa một số dữ liệu phiên. Thông tin nhạy cảm vẫn còn tồn tại. Lỗi hệ thống bảo mật. |
