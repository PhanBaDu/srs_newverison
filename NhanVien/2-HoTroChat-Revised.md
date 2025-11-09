# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng hỗ trợ / liên hệ của User_

## MỤC LỤC

1. [Chức năng hỗ trợ / liên hệ](#1-chức-năng-hỗ-trợ--liên-hệ)
   - 1.1 [Chat hỗ trợ](#11-chat-hỗ-trợ)
   - 1.2 [Gửi phản hồi/khiếu nại](#12-gửi-phản-hồikhiếu-nại)
   - 1.3 [Quản lý yêu cầu hỗ trợ](#13-quản-lý-yêu-cầu-hỗ-trợ)
   - 1.4 [Câu hỏi thường gặp](#14-câu-hỏi-thường-gặp)
   - 1.5 [Thông tin liên hệ](#15-thông-tin-liên-hệ)

---

## 1. CHỨC NĂNG HỖ TRỢ / LIÊN HỆ

### 1.1 CHAT HỖ TRỢ

#### 1.1.1 Thông tin màn hình:

| Screen        | Chat hỗ trợ                              |
| ------------- | ---------------------------------------- |
| Description   | Liên hệ trực tiếp với admin/chủ shop     |
| Screen Access | Từ trang hỗ trợ với tab "Chat trực tiếp" |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type      | Data                                        | Description                      |
| ----------------------- | --------- | ------------------------------------------- | -------------------------------- |
| **Tiêu đề chat**        | Text      | Chat trực tiếp với nhân viên hỗ trợ         | Tiêu đề của khu vực chat         |
| **Icon chat**           | Icon      | MessageSquare                               | Icon đại diện cho chat           |
| **Mô tả chat**          | Text      | Nhân viên hỗ trợ sẽ phản hồi trong vài phút | Mô tả về thời gian phản hồi      |
| **Khu vực tin nhắn**    | Container | Hiển thị tin nhắn                           | Khu vực hiển thị cuộc trò chuyện |
| **Lịch sử chat**        | List      | Danh sách tin nhắn đã lưu                   | Hiển thị lịch sử chat đã lưu     |
| **Tìm kiếm trong chat** | Input     | Tìm kiếm trong lịch sử chat                 | Ô tìm kiếm tin nhắn trong chat   |
| **Nút export chat**     | Button    | Xuất lịch sử chat                           | Nút để export lịch sử chat       |
| **Tin nhắn người dùng** | Message   | Tin nhắn từ người dùng                      | Tin nhắn do người dùng gửi       |
| **Tin nhắn hỗ trợ**     | Message   | Tin nhắn từ nhân viên hỗ trợ                | Tin nhắn do nhân viên hỗ trợ gửi |
| **Thời gian tin nhắn**  | Text      | Thời gian gửi tin nhắn                      | Thời gian gửi tin nhắn           |
| **Trạng thái đã đọc**   | Badge     | Đã đọc / Chưa đọc                           | Trạng thái đã đọc tin nhắn       |
| **Ô nhập tin nhắn**     | Textarea  | Nhập tin nhắn                               | Ô để nhập tin nhắn               |
| **Nút gửi tin nhắn**    | Button    | Gửi                                         | Nút để gửi tin nhắn              |
| **Icon gửi**            | Icon      | Send                                        | Icon đại diện cho gửi            |
| **Trạng thái kết nối**  | Badge     | Đang kết nối / Đã kết nối                   | Trạng thái kết nối với hỗ trợ    |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                          | Success                                                                                                              | Failure                                                                                                                                         |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Kết nối chat hỗ trợ**  | Cho phép người dùng kết nối trực tiếp với nhân viên hỗ trợ để được hỗ trợ ngay lập tức. Hệ thống sẽ thiết lập kết nối chat real-time và hiển thị trạng thái kết nối. Tất cả tin nhắn được lưu trữ trong lịch sử chat để có thể xem lại sau. | Kết nối chat hỗ trợ thành công và trạng thái kết nối được hiển thị. Nhân viên hỗ trợ có thể phản hồi trong vài phút. Lịch sử chat được lưu trữ. | Kết nối chat hỗ trợ không thành công hoặc trạng thái kết nối không được hiển thị. Nhân viên hỗ trợ không thể phản hồi trong thời gian mong đợi. Lịch sử chat không được lưu trữ. |
| **Gửi tin nhắn**         | Cho phép người dùng gửi tin nhắn đến nhân viên hỗ trợ để mô tả vấn đề hoặc câu hỏi cần hỗ trợ. Tin nhắn sẽ được gửi ngay lập tức, hiển thị trong cuộc trò chuyện và được lưu vào lịch sử chat.  | Tin nhắn được gửi thành công và hiển thị trong cuộc trò chuyện. Thời gian gửi được ghi nhận chính xác. Tin nhắn được lưu vào lịch sử.               | Tin nhắn không được gửi thành công hoặc không hiển thị trong cuộc trò chuyện. Thời gian gửi không được ghi nhận chính xác. Tin nhắn không được lưu vào lịch sử.                      |
| **Nhận tin nhắn hỗ trợ** | Cho phép người dùng nhận tin nhắn phản hồi từ nhân viên hỗ trợ. Tin nhắn sẽ được hiển thị trong cuộc trò chuyện với thời gian và trạng thái đã đọc, đồng thời được lưu vào lịch sử chat.                  | Tin nhắn hỗ trợ được nhận và hiển thị chính xác trong cuộc trò chuyện. Trạng thái đã đọc được cập nhật đúng cách. Tin nhắn được lưu vào lịch sử.    | Tin nhắn hỗ trợ không được nhận hoặc không hiển thị chính xác trong cuộc trò chuyện. Trạng thái đã đọc không được cập nhật đúng cách. Tin nhắn không được lưu vào lịch sử.           |
| **Xem lịch sử chat**     | Cho phép người dùng xem lại lịch sử chat đã lưu trữ, bao gồm tất cả tin nhắn đã gửi và nhận. Hệ thống hỗ trợ tìm kiếm trong lịch sử chat để tìm tin nhắn cụ thể. | Lịch sử chat được hiển thị đầy đủ và chính xác. Tìm kiếm trong chat hoạt động tốt. | Lịch sử chat không được hiển thị đầy đủ hoặc không chính xác. Tìm kiếm trong chat không hoạt động. |
| **Export lịch sử chat**  | Cho phép người dùng xuất lịch sử chat ra file (CSV, TXT) để lưu trữ hoặc in. Hệ thống hỗ trợ export toàn bộ hoặc theo khoảng thời gian. | Lịch sử chat được export thành công. File được tạo đúng định dạng. | Không thể export lịch sử chat. File được tạo không đúng định dạng. |

### 1.2 GỬI PHẢN HỒI/KHIẾU NẠI

#### 1.2.1 Thông tin màn hình:

| Screen        | Gửi phản hồi/khiếu nại                           |
| ------------- | ------------------------------------------------ |
| Description   | Gửi phản hồi hoặc khiếu nại về dịch vụ, sản phẩm |
| Screen Access | Từ trang hỗ trợ với tab "Yêu cầu hỗ trợ"         |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                    | Type       | Data                        | Description                           |
| ----------------------- | ---------- | --------------------------- | ------------------------------------- |
| **Tiêu đề yêu cầu**     | Text       | Yêu cầu hỗ trợ              | Tiêu đề của trang yêu cầu hỗ trợ      |
| **Icon yêu cầu**        | Icon       | FileText                    | Icon đại diện cho yêu cầu hỗ trợ      |
| **Nút tạo yêu cầu mới** | Button     | Tạo yêu cầu hỗ trợ mới      | Nút để tạo yêu cầu hỗ trợ mới         |
| **Form tạo yêu cầu**    | Form       | Form nhập thông tin yêu cầu | Form để nhập thông tin yêu cầu hỗ trợ |
| **Tiêu đề yêu cầu**     | Input      | Tiêu đề yêu cầu             | Ô nhập tiêu đề yêu cầu                |
| **Danh mục**            | Select     | Danh mục yêu cầu            | Dropdown chọn danh mục                |
| **Mức độ ưu tiên**      | Select     | Mức độ ưu tiên              | Dropdown chọn mức độ ưu tiên          |
| **Mô tả vấn đề**        | Textarea   | Mô tả chi tiết vấn đề       | Ô nhập mô tả chi tiết vấn đề          |
| **Mã đơn hàng**         | Input      | Mã đơn hàng liên quan       | Ô nhập mã đơn hàng liên quan          |
| **File đính kèm**       | File Input | Đính kèm file               | Nút để đính kèm file                  |
| **Nút gửi yêu cầu**     | Button     | Gửi yêu cầu                 | Nút để gửi yêu cầu hỗ trợ             |
| **Nút hủy**             | Button     | Hủy                         | Nút để hủy tạo yêu cầu                |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                      | Success                                                                                                                        | Failure                                                                                                                                                     |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tạo yêu cầu hỗ trợ mới** | Cho phép người dùng tạo yêu cầu hỗ trợ mới bằng cách điền thông tin vào form bao gồm tiêu đề, danh mục, mức độ ưu tiên, mô tả vấn đề, và mã đơn hàng liên quan. Hệ thống sẽ tạo ticket hỗ trợ và gửi đến admin để xử lý.         | Yêu cầu hỗ trợ được tạo thành công và gửi đến admin. Form được điền đầy đủ thông tin và validation hoạt động đúng cách.        | Yêu cầu hỗ trợ không được tạo thành công hoặc không được gửi đến admin. Form không được điền đầy đủ thông tin hoặc validation không hoạt động đúng cách.    |
| **Chọn danh mục yêu cầu**  | Cho phép người dùng chọn danh mục phù hợp cho yêu cầu hỗ trợ từ các danh mục có sẵn như đơn hàng, sản phẩm, thanh toán, vận chuyển, tài khoản, kỹ thuật, hoặc khác. Danh mục giúp admin phân loại và xử lý yêu cầu hiệu quả hơn. | Danh mục yêu cầu được chọn chính xác và phù hợp với vấn đề. Admin có thể phân loại và xử lý yêu cầu hiệu quả.                  | Danh mục yêu cầu không được chọn chính xác hoặc không phù hợp với vấn đề. Admin không thể phân loại và xử lý yêu cầu hiệu quả.                              |
| **Đính kèm file**          | Cho phép người dùng đính kèm file để minh họa cho vấn đề cần hỗ trợ như hình ảnh, tài liệu, hoặc file log. Hệ thống hỗ trợ nhiều định dạng file và có giới hạn kích thước file.                                                  | File được đính kèm thành công và hiển thị trong danh sách. Hệ thống hỗ trợ nhiều định dạng file và giới hạn kích thước hợp lý. | File không được đính kèm thành công hoặc không hiển thị trong danh sách. Hệ thống không hỗ trợ đầy đủ định dạng file hoặc giới hạn kích thước không hợp lý. |

### 1.3 QUẢN LÝ YÊU CẦU HỖ TRỢ

#### 1.3.1 Thông tin màn hình:

| Screen        | Quản lý yêu cầu hỗ trợ                   |
| ------------- | ---------------------------------------- |
| Description   | Quản lý các yêu cầu hỗ trợ đã gửi        |
| Screen Access | Từ trang hỗ trợ với tab "Yêu cầu hỗ trợ" |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                         | Description                       |
| --------------------- | ------ | ---------------------------- | --------------------------------- |
| **Danh sách yêu cầu** | List   | Danh sách các yêu cầu hỗ trợ | Hiển thị danh sách yêu cầu hỗ trợ |
| **Bộ lọc trạng thái** | Select | Lọc theo trạng thái          | Dropdown để lọc theo trạng thái   |
| **Bộ lọc danh mục**   | Select | Lọc theo danh mục            | Dropdown để lọc theo danh mục     |
| **Ô tìm kiếm**        | Input  | Tìm kiếm yêu cầu             | Ô để tìm kiếm yêu cầu             |
| **Card yêu cầu**      | Card   | Thông tin yêu cầu hỗ trợ     | Card hiển thị thông tin yêu cầu   |
| **Mã yêu cầu**        | Text   | Mã định danh yêu cầu         | Mã định danh của yêu cầu          |
| **Tiêu đề yêu cầu**   | Text   | Tiêu đề yêu cầu              | Tiêu đề của yêu cầu               |
| **Danh mục**          | Badge  | Danh mục yêu cầu             | Danh mục của yêu cầu              |
| **Mức độ ưu tiên**    | Badge  | Mức độ ưu tiên               | Mức độ ưu tiên của yêu cầu        |
| **Trạng thái**        | Badge  | Trạng thái xử lý             | Trạng thái hiện tại của yêu cầu   |
| **Ngày tạo**          | Text   | Ngày tạo yêu cầu             | Thời gian tạo yêu cầu             |
| **Ngày cập nhật**     | Text   | Ngày cập nhật cuối           | Thời gian cập nhật cuối           |
| **Phản hồi admin**    | Text   | Phản hồi từ admin            | Phản hồi của admin về yêu cầu     |
| **Nút xem chi tiết**  | Button | Xem chi tiết                 | Nút để xem chi tiết yêu cầu       |

#### 1.3.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                     | Success                                                                                                             | Failure                                                                                                                         |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị danh sách yêu cầu** | Hiển thị danh sách tất cả các yêu cầu hỗ trợ mà người dùng đã gửi với thông tin đầy đủ bao gồm mã yêu cầu, tiêu đề, danh mục, mức độ ưu tiên, trạng thái, và thời gian tạo. Danh sách được sắp xếp theo thời gian tạo mới nhất. | Danh sách yêu cầu hỗ trợ được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.             | Danh sách yêu cầu hỗ trợ không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.  |
| **Lọc và tìm kiếm yêu cầu**    | Cho phép người dùng lọc yêu cầu hỗ trợ theo trạng thái và danh mục, đồng thời tìm kiếm theo tiêu đề hoặc mô tả. Hệ thống sẽ cập nhật danh sách ngay lập tức khi có thay đổi bộ lọc hoặc từ khóa tìm kiếm.                       | Yêu cầu được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách được cập nhật ngay lập tức khi có thay đổi. | Yêu cầu không được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách không được cập nhật ngay lập tức khi có thay đổi. |
| **Xem chi tiết yêu cầu**       | Cho phép người dùng xem chi tiết đầy đủ của yêu cầu hỗ trợ bao gồm mô tả vấn đề, phản hồi từ admin, thời gian tạo và cập nhật, và các file đính kèm. Thông tin được hiển thị rõ ràng và dễ đọc.                                 | Chi tiết yêu cầu được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                     | Chi tiết yêu cầu không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.          |

### 1.4 CÂU HỎI THƯỜNG GẶP

#### 1.4.1 Thông tin màn hình:

| Screen        | Câu hỏi thường gặp                             |
| ------------- | ---------------------------------------------- |
| Description   | Hiển thị các câu hỏi thường gặp và câu trả lời |
| Screen Access | Từ trang hỗ trợ với tab "Câu hỏi thường gặp"   |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                   | Type      | Data                             | Description                                          |
| ---------------------- | --------- | -------------------------------- | ---------------------------------------------------- |
| **Tiêu đề FAQ**        | Text      | Câu hỏi thường gặp               | Tiêu đề của trang FAQ                                |
| **Icon FAQ**           | Icon      | HelpCircle                       | Icon đại diện cho FAQ                                |
| **Ô tìm kiếm FAQ**     | Input     | Tìm kiếm câu hỏi                 | Ô để tìm kiếm câu hỏi                                |
| **Danh mục FAQ**       | Select    | Lọc theo danh mục                | Dropdown để lọc theo danh mục                        |
| **Danh sách câu hỏi**  | Accordion | Danh sách câu hỏi và câu trả lời | Hiển thị câu hỏi và câu trả lời                      |
| **Câu hỏi**            | Text      | Tiêu đề câu hỏi                  | Tiêu đề của câu hỏi                                  |
| **Câu trả lời**        | Text      | Nội dung câu trả lời             | Nội dung chi tiết câu trả lời                        |
| **Danh mục câu hỏi**   | Badge     | Danh mục của câu hỏi             | Danh mục phân loại câu hỏi                           |
| **Nút hữu ích**        | Button    | Hữu ích / Không hữu ích          | Nút để đánh giá câu trả lời                          |
| **Số lượt hữu ích**    | Text      | Số lượt đánh giá hữu ích         | Số lượt đánh giá hữu ích                             |
| **Nút liên hệ hỗ trợ** | Button    | Liên hệ hỗ trợ                   | Nút để liên hệ hỗ trợ nếu không tìm thấy câu trả lời |

#### 1.4.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                | Success                                                                                                                         | Failure                                                                                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị câu hỏi thường gặp** | Hiển thị danh sách các câu hỏi thường gặp được phân loại theo danh mục với câu trả lời chi tiết. Người dùng có thể mở rộng/thu gọn từng câu hỏi để xem câu trả lời.                        | Danh sách câu hỏi thường gặp được hiển thị đầy đủ và chính xác. Câu trả lời được trình bày rõ ràng và dễ hiểu.                  | Danh sách câu hỏi thường gặp không được hiển thị đầy đủ hoặc không chính xác. Câu trả lời không được trình bày rõ ràng hoặc khó hiểu.          |
| **Tìm kiếm câu hỏi**            | Cho phép người dùng tìm kiếm câu hỏi thường gặp bằng cách nhập từ khóa vào ô tìm kiếm. Hệ thống sẽ tìm kiếm theo tiêu đề câu hỏi và nội dung câu trả lời, sau đó hiển thị kết quả phù hợp. | Câu hỏi được tìm kiếm chính xác và kết quả được hiển thị đầy đủ. Hệ thống tìm kiếm theo nhiều tiêu chí và phản hồi nhanh chóng. | Câu hỏi không được tìm kiếm chính xác hoặc kết quả không được hiển thị đầy đủ. Hệ thống không tìm kiếm theo nhiều tiêu chí hoặc phản hồi chậm. |
| **Đánh giá câu trả lời**        | Cho phép người dùng đánh giá câu trả lời là hữu ích hoặc không hữu ích để giúp cải thiện chất lượng FAQ. Hệ thống sẽ cập nhật số lượt đánh giá và lưu lại phản hồi của người dùng.         | Câu trả lời được đánh giá thành công và số lượt đánh giá được cập nhật. Phản hồi của người dùng được lưu lại chính xác.         | Câu trả lời không được đánh giá thành công hoặc số lượt đánh giá không được cập nhật. Phản hồi của người dùng không được lưu lại chính xác.    |

### 1.5 THÔNG TIN LIÊN HỆ

#### 1.5.1 Thông tin màn hình:

| Screen        | Thông tin liên hệ                          |
| ------------- | ------------------------------------------ |
| Description   | Hiển thị thông tin liên hệ của shop        |
| Screen Access | Từ trang hỗ trợ với phần thông tin liên hệ |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                    | Description                        |
| --------------------- | ------ | ----------------------- | ---------------------------------- |
| **Tiêu đề liên hệ**   | Text   | Thông tin liên hệ       | Tiêu đề của phần thông tin liên hệ |
| **Thông tin shop**    | Card   | Thông tin chi tiết shop | Card hiển thị thông tin shop       |
| **Tên shop**          | Text   | Tên shop                | Tên đầy đủ của shop                |
| **Địa chỉ**           | Text   | Địa chỉ shop            | Địa chỉ đầy đủ của shop            |
| **Số điện thoại**     | Text   | Số điện thoại liên hệ   | Số điện thoại để liên hệ           |
| **Email**             | Text   | Email liên hệ           | Email để liên hệ                   |
| **Giờ làm việc**      | Text   | Giờ làm việc            | Thời gian làm việc của shop        |
| **Icon địa chỉ**      | Icon   | MapPin                  | Icon đại diện cho địa chỉ          |
| **Icon điện thoại**   | Icon   | Phone                   | Icon đại diện cho điện thoại       |
| **Icon email**        | Icon   | Mail                    | Icon đại diện cho email            |
| **Icon giờ làm việc** | Icon   | Clock3                  | Icon đại diện cho giờ làm việc     |
| **Nút gọi điện**      | Button | Gọi điện                | Nút để gọi điện trực tiếp          |
| **Nút gửi email**     | Button | Gửi email               | Nút để gửi email trực tiếp         |

#### 1.5.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                             | Success                                                                                                                      | Failure                                                                                                                                       |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị thông tin liên hệ** | Hiển thị đầy đủ thông tin liên hệ của shop bao gồm tên shop, địa chỉ, số điện thoại, email, và giờ làm việc. Thông tin được trình bày rõ ràng với icon phù hợp cho từng loại thông tin. | Thông tin liên hệ được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng với icon phù hợp.                      | Thông tin liên hệ không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc icon không phù hợp.            |
| **Liên hệ trực tiếp**          | Cho phép người dùng liên hệ trực tiếp với shop thông qua các kênh liên hệ như gọi điện, gửi email, hoặc chat hỗ trợ. Hệ thống sẽ mở ứng dụng tương ứng để thực hiện liên hệ.            | Liên hệ trực tiếp được thực hiện thành công và ứng dụng tương ứng được mở. Người dùng có thể liên hệ dễ dàng qua nhiều kênh. | Liên hệ trực tiếp không được thực hiện thành công hoặc ứng dụng tương ứng không được mở. Người dùng không thể liên hệ dễ dàng qua nhiều kênh. |
| **Hiển thị giờ làm việc**      | Hiển thị thông tin giờ làm việc của shop để người dùng biết được thời gian có thể liên hệ và nhận hỗ trợ. Thông tin bao gồm ngày trong tuần và giờ làm việc cụ thể.                     | Giờ làm việc được hiển thị chính xác và đầy đủ. Người dùng có thể biết được thời gian có thể liên hệ và nhận hỗ trợ.         | Giờ làm việc không được hiển thị chính xác hoặc không đầy đủ. Người dùng không thể biết được thời gian có thể liên hệ và nhận hỗ trợ.         |
