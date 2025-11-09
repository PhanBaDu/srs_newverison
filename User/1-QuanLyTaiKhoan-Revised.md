# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý tài khoản của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý tài khoản](#1-chức-năng-quản-lý-tài-khoản)
   - 1.1 [Đăng ký tài khoản](#11-đăng-ký-tài-khoản) - **ĐÃ SỬA**
   - 1.2 [Đăng nhập hệ thống](#12-đăng-nhập-hệ-thống) - **ĐÃ SỬA**
   - 1.3 [Đổi mật khẩu](#13-đổi-mật-khẩu) - **ĐÃ SỬA**
   - 1.4 [Thông tin cá nhân](#14-thông-tin-cá-nhân)
   - 1.5 [Điểm tích lũy và hạng thành viên](#15-điểm-tích-lũy-và-hạng-thành-viên)
   - 1.6 [Đăng xuất hệ thống](#16-đăng-xuất-hệ-thống)

---

## 1. CHỨC NĂNG QUẢN LÝ TÀI KHOẢN

### 1.1 ĐĂNG KÝ TÀI KHOẢN - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Đăng ký tài khoản mới                                                                |
| ------------- | ------------------------------------------------------------------------------------ |
| Description   | Cho phép người dùng tạo tài khoản mới để sử dụng các dịch vụ của nhà sách trực tuyến |
| Screen Access | Người dùng truy cập trang **Đăng ký** từ menu chính hoặc từ trang đăng nhập          |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                   | Type             | Data                                 | Description                                    |
| ---------------------- | ---------------- | ------------------------------------ | ---------------------------------------------- |
| **Tiêu đề trang**      | Text             | Tạo tài khoản mới                    | Tiêu đề chính của trang đăng ký                |
| **Mô tả chức năng**    | Text             | Hoặc đăng nhập vào tài khoản hiện có | Mô tả ngắn gọn về mục đích của trang           |
| **Form đăng ký**       | Form             |                                      | Form nhập thông tin để tạo tài khoản mới       |
| **Họ và tên**          | Input (Text)     | Nguyễn Văn A *                       | **MỚI**: Validation tối thiểu 2 ký tự         |
| **Email**              | Input (Email)    | nguyenvana@example.com *             | **MỚI**: Validation RFC 5322                   |
| **Số điện thoại**      | Input (Tel)      | 0123456789 *                         | **MỚI**: Validation định dạng VN (0xxx hoặc +84xxx) |
| **Mật khẩu**           | Input (Password) |                                      | **MỚI**: Validation tối thiểu 6 ký tự         |
| **Xác nhận mật khẩu**  | Input (Password) |                                      | **MỚI**: Validation phải khớp với mật khẩu    |
| **Địa chỉ**            | Textarea         | 123 Đường ABC, Quận 1, TP.HCM        | Ô nhập địa chỉ đầy đủ                          |
| **Điều khoản sử dụng** | Checkbox         | Tôi đồng ý với điều khoản sử dụng    | Checkbox xác nhận đồng ý điều khoản             |
| **Nút đăng ký**        | Button           | Đăng ký                              | Nút để hoàn tất quá trình đăng ký              |
| **Thông báo lỗi**      | Alert            | Email không hợp lệ (RFC 5322)        | **MỚI**: Hiển thị lỗi validation cụ thể        |
| **Thông báo retry**    | Alert            | Đang thử lại gửi email...            | **MỚI**: Hiển thị khi retry gửi email          |

#### 1.1.3 Hành động và xử lý:

| Action Name               | Description                                                                                                                                                                                                                                 | Success                                                                                                          | Failure                                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Đăng ký tài khoản mới** | Cho phép người dùng tạo tài khoản mới với thông tin cá nhân đầy đủ. Hệ thống sẽ kiểm tra tính hợp lệ của email, số điện thoại và mật khẩu. Sau khi đăng ký thành công, người dùng sẽ nhận được email xác nhận và có thể đăng nhập vào hệ thống. | Tài khoản được tạo thành công. Email xác nhận được gửi đến người dùng. Người dùng có thể đăng nhập ngay lập tức. | Email đã tồn tại trong hệ thống. Số điện thoại không hợp lệ. Mật khẩu không đủ mạnh. Lỗi khi gửi email xác nhận. |
| **Kiểm tra tính hợp lệ**  | **MỚI**: Hệ thống kiểm tra tính hợp lệ của các trường thông tin trước khi cho phép đăng ký. Bao gồm: email (RFC 5322), số điện thoại (định dạng VN: 0xxx hoặc +84xxx), mật khẩu (tối thiểu 6 ký tự, phải khớp với xác nhận), họ tên (tối thiểu 2 ký tự). | Tất cả thông tin hợp lệ và có thể tiến hành đăng ký.                                                             | Phát hiện thông tin không hợp lệ và hiển thị thông báo lỗi cụ thể.                                               |
| **Gửi email xác nhận**    | **MỚI**: Sau khi đăng ký thành công, hệ thống tự động gửi email xác nhận đến địa chỉ email của người dùng. Nếu gửi email thất bại, hệ thống sẽ tự động retry 3 lần với delay 2 giây mỗi lần. Nếu vẫn thất bại, hệ thống sẽ thông báo và cho phép người dùng thử lại sau. | Email xác nhận được gửi thành công.                                                                              | Lỗi khi gửi email do vấn đề hệ thống hoặc địa chỉ email không tồn tại. Retry 3 lần vẫn thất bại.                |
| **Retry mechanism**       | **MỚI**: Nếu gửi email thất bại, hệ thống tự động retry 3 lần với delay 2 giây mỗi lần. Trong quá trình retry, hệ thống hiển thị thông báo "Đang thử lại gửi email... (Lần X/3)". | Email được gửi thành công sau khi retry.                                                                          | Retry 3 lần vẫn thất bại. Hiển thị thông báo lỗi và cho phép người dùng thử lại sau.                              |

#### 1.1.4 Validation Rules (MỚI):

| Field             | Rule                                    | Error Message                                    |
| ----------------- | --------------------------------------- | ------------------------------------------------ |
| **Họ và tên**     | Bắt buộc, tối thiểu 2 ký tự             | "Họ và tên phải có ít nhất 2 ký tự"              |
| **Email**         | Bắt buộc, theo chuẩn RFC 5322          | "Email không hợp lệ (theo chuẩn RFC 5322)"       |
| **Số điện thoại** | Bắt buộc, định dạng: 0xxx hoặc +84xxx  | "Số điện thoại không hợp lệ (định dạng: 0xxxxxxxxx hoặc +84xxxxxxxxx)" |
| **Mật khẩu**      | Bắt buộc, tối thiểu 6 ký tự             | "Mật khẩu phải có ít nhất 6 ký tự"               |
| **Xác nhận mật khẩu** | Bắt buộc, phải khớp với mật khẩu      | "Mật khẩu xác nhận không khớp"                    |

---

### 1.2 ĐĂNG NHẬP HỆ THỐNG - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Đăng nhập vào hệ thống                                                                    |
| ------------- | ----------------------------------------------------------------------------------------- |
| Description   | Cho phép người dùng đăng nhập vào hệ thống nhà sách bằng tài khoản và mật khẩu đã đăng ký |
| Screen Access | Người dùng truy cập trang **Đăng nhập** từ menu chính hoặc từ trang đăng ký               |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type             | Data                    | Description                                    |
| --------------------- | ---------------- | ----------------------- | ---------------------------------------------- |
| **Tiêu đề trang**     | Text             | Đăng nhập vào tài khoản | Tiêu đề chính của trang đăng nhập              |
| **Mô tả chức năng**   | Text             | Hoặc tạo tài khoản mới  | Mô tả ngắn gọn về mục đích của trang           |
| **Form đăng nhập**    | Form             |                         | Form nhập thông tin để đăng nhập               |
| **Email**             | Input (Email)    | nguyenvana@example.com  | Ô nhập địa chỉ email đã đăng ký                |
| **Mật khẩu**          | Input (Password) |                         | Ô nhập mật khẩu tài khoản                      |
| **Hiện/Ẩn mật khẩu**  | Button (Icon)    | Eye/EyeOff              | Nút để hiện hoặc ẩn mật khẩu                   |
| **Ghi nhớ đăng nhập** | Checkbox         | Ghi nhớ đăng nhập       | Checkbox để lưu thông tin đăng nhập            |
| **Quên mật khẩu**     | Link             | Quên mật khẩu?          | Link để khôi phục mật khẩu                     |
| **Nút đăng nhập**     | Button           | Đăng nhập               | Nút để thực hiện đăng nhập                     |
| **CAPTCHA**           | CAPTCHA          | [Hình ảnh CAPTCHA]      | **MỚI**: Hiển thị sau 3 lần đăng nhập sai        |
| **Input CAPTCHA**     | Input            | Nhập mã CAPTCHA         | **MỚI**: Ô nhập mã CAPTCHA                     |
| **Thông báo lockout** | Alert            | Tài khoản bị khóa 30 phút | **MỚI**: Hiển thị khi bị khóa                  |
| **Thông báo CAPTCHA** | Alert            | Vui lòng nhập CAPTCHA   | **MỚI**: Hiển thị khi cần CAPTCHA             |

#### 1.2.3 Hành động và xử lý:

| Action Name            | Description                                                                                                                                                                                                                                 | Success                                                                                                | Failure                                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Đăng nhập hệ thống** | Cho phép người dùng đăng nhập vào hệ thống bằng email và mật khẩu đã đăng ký. Hệ thống sẽ xác thực thông tin và cấp quyền truy cập phù hợp. Sau khi đăng nhập thành công, người dùng sẽ được chuyển hướng đến trang chủ hoặc trang đã yêu cầu trước đó. | Đăng nhập thành công. Người dùng được chuyển hướng đến trang chủ. Phiên đăng nhập được tạo và lưu trữ. | Email hoặc mật khẩu không đúng. Tài khoản bị khóa hoặc chưa được kích hoạt. Lỗi hệ thống khi xác thực. |
| **Anti-brute force**    | **MỚI**: Hệ thống theo dõi số lần đăng nhập sai. Sau 5 lần đăng nhập sai, tài khoản sẽ bị khóa trong 30 phút. Sau 3 lần đăng nhập sai, hệ thống sẽ hiển thị CAPTCHA và yêu cầu người dùng nhập mã CAPTCHA trước khi tiếp tục.                  | Số lần đăng nhập sai được theo dõi chính xác. Tài khoản được khóa sau 5 lần sai. CAPTCHA được hiển thị sau 3 lần sai. | Không thể theo dõi số lần đăng nhập sai. Tài khoản không được khóa khi cần thiết.                      |
| **CAPTCHA verification** | **MỚI**: Sau 3 lần đăng nhập sai, hệ thống tự động hiển thị CAPTCHA và yêu cầu người dùng nhập mã CAPTCHA trước khi cho phép tiếp tục đăng nhập. Nếu CAPTCHA không đúng, hệ thống sẽ từ chối đăng nhập.                                        | CAPTCHA được hiển thị và xác thực thành công. Người dùng có thể tiếp tục đăng nhập.                     | CAPTCHA không được hiển thị khi cần thiết. CAPTCHA không được xác thực chính xác.                      |
| **Account lockout**    | **MỚI**: Sau 5 lần đăng nhập sai, tài khoản sẽ bị khóa trong 30 phút. Trong thời gian khóa, người dùng không thể đăng nhập. Hệ thống hiển thị thông báo: "Tài khoản đã bị khóa do đăng nhập sai quá nhiều lần. Vui lòng thử lại sau 30 phút." | Tài khoản được khóa thành công sau 5 lần sai. Thông báo lockout được hiển thị rõ ràng.                 | Tài khoản không được khóa khi cần thiết. Thông báo lockout không được hiển thị.                        |

#### 1.2.4 Anti-Brute Force Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Failed Attempts** | Theo dõi số lần đăng nhập sai cho mỗi email                                | Tăng counter mỗi lần đăng nhập sai        |
| **CAPTCHA Trigger** | Hiển thị CAPTCHA sau 3 lần đăng nhập sai                                  | Yêu cầu nhập CAPTCHA trước khi tiếp tục   |
| **Lockout Trigger** | Khóa tài khoản sau 5 lần đăng nhập sai                                     | Khóa tài khoản trong 30 phút              |
| **Lockout Duration** | Thời gian khóa: 30 phút                                                     | Tự động mở khóa sau 30 phút               |
| **Reset on Success** | Reset counter khi đăng nhập thành công                                     | Cho phép đăng nhập bình thường            |

---

### 1.3 ĐỔI MẬT KHẨU - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Đổi mật khẩu                                                      |
| ------------- | ----------------------------------------------------------------- |
| Description   | Cho phép người dùng thay đổi mật khẩu tài khoản với OTP verification cho VIP/Admin |
| Screen Access | Người dùng chọn **Đổi mật khẩu** từ trang tài khoản               |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Input mật khẩu hiện tại** | Input (Password) | Nhập mật khẩu hiện tại *             | Ô nhập mật khẩu hiện tại                       |
| **Input mật khẩu mới**   | Input (Password) | Nhập mật khẩu mới *                   | Ô nhập mật khẩu mới                            |
| **Input xác nhận mật khẩu** | Input (Password) | Xác nhận mật khẩu mới *              | Ô nhập lại mật khẩu mới                        |
| **Alert OTP requirement** | Alert        | Tài khoản VIP/Admin yêu cầu OTP         | **MỚI**: Cảnh báo cho VIP/Admin                 |
| **Input OTP**             | Input        | Nhập mã OTP (6 số) *                    | **MỚI**: Ô nhập mã OTP cho VIP/Admin           |
| **Thông báo gửi OTP**     | Text         | Mã OTP đã được gửi đến email...         | **MỚI**: Thông báo khi gửi OTP                 |
| **Nút gửi lại OTP**       | Button       | Gửi lại mã OTP                          | **MỚI**: Nút để gửi lại mã OTP                |
| **Nút đổi mật khẩu**      | Button       | Đổi mật khẩu / Tiếp tục                 | **MỚI**: Thay đổi text theo bước               |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Đổi mật khẩu**         | Cho phép người dùng thay đổi mật khẩu tài khoản. Đối với VIP/Admin, hệ thống yêu cầu xác thực OTP qua email trước khi cho phép đổi mật khẩu.                                                                                                | Mật khẩu được thay đổi thành công.                                                          | Mật khẩu hiện tại không đúng. Mật khẩu mới không đủ mạnh. OTP không đúng (VIP/Admin).     |
| **OTP verification cho VIP/Admin** | **MỚI**: Đối với tài khoản VIP (Gold, Platinum, Diamond) hoặc Admin, hệ thống yêu cầu xác thực OTP qua email trước khi cho phép đổi mật khẩu. Sau khi nhập mật khẩu hiện tại và mật khẩu mới, hệ thống sẽ gửi OTP đến email và yêu cầu nhập mã OTP. | OTP được gửi thành công. OTP được xác thực chính xác. Mật khẩu được thay đổi thành công.  | Không thể gửi OTP. OTP không đúng. OTP đã hết hạn.                                         |
| **Gửi OTP**              | **MỚI**: Khi VIP/Admin nhập mật khẩu hiện tại và mật khẩu mới, hệ thống tự động gửi mã OTP 6 số đến email của người dùng. OTP có thời hạn 10 phút.                                                                                        | OTP được gửi thành công đến email. Thông báo hiển thị rõ ràng.                            | Không thể gửi OTP do lỗi email server. Email không tồn tại.                                |
| **Validation OTP**       | **MỚI**: Hệ thống kiểm tra mã OTP phải là 6 số và phải khớp với mã đã gửi. Nếu không đúng, hệ thống sẽ từ chối và yêu cầu nhập lại.                                                                                                          | OTP được validate thành công. Cho phép đổi mật khẩu.                                       | OTP không đúng. OTP đã hết hạn. Hiển thị thông báo lỗi cụ thể.                             |

#### 1.3.4 OTP Verification Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **VIP/Admin Check** | Kiểm tra user có phải VIP (Gold, Platinum, Diamond) hoặc Admin không      | Yêu cầu OTP nếu là VIP/Admin              |
| **OTP Format**      | Mã OTP phải là 6 số                                                         | Validate format trước khi kiểm tra        |
| **OTP Expiry**      | OTP có thời hạn 10 phút                                                     | Từ chối nếu OTP đã hết hạn                |
| **Resend OTP**      | Cho phép gửi lại OTP nếu chưa nhận được                                     | Gửi OTP mới và invalidate OTP cũ         |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Validation chi tiết**: Thêm validation rules cụ thể cho từng trường (email RFC 5322, phone VN format, password min 6 chars)
2. **Email retry mechanism**: Tự động retry 3 lần khi gửi email thất bại
3. **Anti-brute force**: Khóa tài khoản sau 5 lần đăng nhập sai, hiển thị CAPTCHA sau 3 lần
4. **OTP verification**: Yêu cầu OTP cho VIP/Admin khi đổi mật khẩu
5. **Error handling**: Hiển thị thông báo lỗi cụ thể cho từng trường hợp
6. **UI cải thiện**: Thêm alert boxes, CAPTCHA UI, OTP input với validation
