# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng đánh giá và nhận xét của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng đánh giá và nhận xét](#1-chức-năng-đánh-giá-và-nhận-xét)
   - 1.1 [Viết đánh giá](#11-viết-đánh-giá) - **ĐÃ SỬA**
   - 1.2 [Xem đánh giá](#12-xem-đánh-giá)
   - 1.3 [Chỉnh sửa đánh giá](#13-chỉnh-sửa-đánh-giá)

---

## 1. CHỨC NĂNG ĐÁNH GIÁ VÀ NHẬN XÉT

### 1.1 VIẾT ĐÁNH GIÁ - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Viết đánh giá sách                                                      |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Cho phép người dùng viết đánh giá và nhận xét về sách đã mua            |
| Screen Access | Người dùng chọn **Viết đánh giá** từ trang chi tiết sách hoặc đơn hàng  |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type             | Data                                    | Description                                    |
| --------------------- | ---------------- | --------------------------------------- | ---------------------------------------------- |
| **Chọn điểm đánh giá** | Star Rating      | 1-5 sao                                  | Cho phép chọn điểm đánh giá từ 1-5 sao         |
| **Nhập nhận xét**     | Textarea         | Viết nhận xét của bạn...                | Ô nhập nội dung đánh giá                        |
| **Thông báo lỗi spam** | Alert            | Nội dung chứa từ cấm: "spam"            | **MỚI**: Hiển thị lỗi spam filter              |
| **Thông báo giới hạn** | Alert            | Bạn đã đạt giới hạn 5 đánh giá/ngày     | **MỚI**: Hiển thị khi đạt giới hạn daily       |
| **Nút gửi đánh giá**  | Button           | Gửi đánh giá                            | Nút để gửi đánh giá                             |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Gửi đánh giá**         | Cho phép người dùng gửi đánh giá về sách đã mua. Hệ thống sẽ kiểm tra tính hợp lệ của đánh giá và lưu vào cơ sở dữ liệu.                                                                                                                    | Đánh giá được gửi thành công và hiển thị công khai.                                        | Đánh giá không hợp lệ. Lỗi khi lưu đánh giá.                                               |
| **Kiểm tra spam**        | **MỚI**: Hệ thống kiểm tra đánh giá có chứa từ cấm (spam, scam, lừa đảo, fake, giả, rác, tệ, tồi tệ, hack, virus, malware, phishing, lừa, đạo) hoặc từ lặp lại quá nhiều lần (>= 5 lần). Nếu phát hiện spam, hệ thống sẽ từ chối và hiển thị thông báo lỗi. | Đánh giá không chứa spam và được chấp nhận.                                                 | Đánh giá chứa spam. Hiển thị: "Đánh giá không hợp lệ: Nội dung chứa từ cấm: [từ cấm]".    |
| **Kiểm tra giới hạn daily** | **MỚI**: Hệ thống kiểm tra số lượng đánh giá trong ngày của người dùng. Tối đa 5 đánh giá mỗi ngày. Nếu đã đạt giới hạn, hệ thống sẽ từ chối và thông báo người dùng thử lại vào ngày mai.                                                    | Số lượng đánh giá trong ngày chưa đạt giới hạn. Đánh giá được chấp nhận.                  | Đã đạt giới hạn 5 đánh giá/ngày. Hiển thị: "Bạn đã đạt giới hạn 5 đánh giá mỗi ngày..."  |
| **Kiểm tra từ lặp lại**  | **MỚI**: Hệ thống kiểm tra xem có từ nào trong đánh giá được lặp lại >= 5 lần không. Nếu có, hệ thống sẽ coi đó là spam và từ chối đánh giá.                                                                                              | Không có từ nào lặp lại quá nhiều. Đánh giá được chấp nhận.                                | Có từ lặp lại >= 5 lần. Hiển thị: "Nội dung có từ lặp lại quá nhiều lần".                 |

#### 1.1.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Điểm đánh giá** | Bắt buộc, từ 1-5 sao                    | "Vui lòng chọn điểm đánh giá"                    |
| **Nội dung**    | Bắt buộc, tối thiểu 10 ký tự            | "Vui lòng viết nhận xét"                         |
| **Spam filter** | Không chứa từ cấm, không lặp từ >= 5 lần | "Đánh giá không hợp lệ: [lý do cụ thể]"          |
| **Daily limit** | Tối đa 5 đánh giá/ngày                  | "Bạn đã đạt giới hạn 5 đánh giá mỗi ngày..."     |

#### 1.1.5 Spam Filter Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Forbidden Words** | Danh sách từ cấm: spam, scam, lừa đảo, fake, giả, rác, tệ, tồi tệ, hack, virus, malware, phishing, lừa, đạo | Từ chối đánh giá và hiển thị thông báo lỗi |
| **Word Repetition** | Kiểm tra từ lặp lại >= 5 lần trong cùng một đánh giá                       | Từ chối đánh giá và hiển thị thông báo lỗi |
| **Daily Limit**     | Tối đa 5 đánh giá mỗi ngày cho mỗi người dùng                               | Từ chối đánh giá và thông báo thử lại ngày mai |

---

### 1.2 XEM ĐÁNH GIÁ

#### 1.2.1 Thông tin màn hình:

| Screen        | Xem đánh giá sách                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Hiển thị danh sách đánh giá của người dùng và người dùng khác về sách  |
| Screen Access | Người dùng truy cập trang **Đánh giá** từ menu hoặc trang chi tiết sách |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách đánh giá** | List         | Đánh giá + người dùng   | Hiển thị các đánh giá                |
| **Bộ lọc đánh giá**   | Filter       | Tất cả, 5 sao, 4 sao... | Lọc đánh giá theo điểm               |
| **Sắp xếp**           | Select       | Mới nhất, Hữu ích nhất  | Sắp xếp đánh giá                     |

---

### 1.3 CHỈNH SỬA ĐÁNH GIÁ

#### 1.3.1 Thông tin màn hình:

| Screen        | Chỉnh sửa đánh giá                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Cho phép người dùng chỉnh sửa đánh giá đã viết                          |
| Screen Access | Người dùng click **Chỉnh sửa** từ đánh giá của mình                    |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Form chỉnh sửa**    | Form         | Điểm + nội dung         | Form để chỉnh sửa đánh giá           |
| **Nút lưu**           | Button       | Lưu thay đổi            | Nút để lưu đánh giá đã chỉnh sửa     |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Spam Filter**: Thêm bộ lọc spam với danh sách từ cấm và kiểm tra từ lặp lại
2. **Daily Limit**: Giới hạn 5 đánh giá mỗi ngày cho mỗi người dùng
3. **Validation nội dung**: Kiểm tra nội dung đánh giá không chứa spam hoặc từ lặp lại quá nhiều
4. **Thông báo lỗi rõ ràng**: Hiển thị thông báo lỗi cụ thể cho từng trường hợp spam
5. **Blacklist words**: Danh sách từ cấm được cập nhật và kiểm tra tự động

