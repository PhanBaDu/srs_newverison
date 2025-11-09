# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng thông báo của User_

## MỤC LỤC

1. [Chức năng thông báo](#1-chức-năng-thông-báo)
   - 1.1 [Hiển thị danh sách thông báo](#11-hiển-thị-danh-sách-thông-báo)
   - 1.2 [Thông báo giảm giá](#12-thông-báo-giảm-giá)
   - 1.3 [Cập nhật đơn hàng](#13-cập-nhật-đơn-hàng)
   - 1.4 [Thông báo có hàng](#14-thông-báo-có-hàng)
   - 1.5 [Quản lý trạng thái thông báo](#15-quản-lý-trạng-thái-thông-báo)

---

## 1. CHỨC NĂNG THÔNG BÁO

### 1.1 HIỂN THỊ DANH SÁCH THÔNG BÁO

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách thông báo (được phân trang) |
| ------------- | ------------------------------------- |
| Description   | Hiển thị toàn bộ thông báo            |
| Screen Access | Từ sidebar menu "Thông báo"           |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type       | Data                                                                      | Description                          |
| ------------------------- | ---------- | ------------------------------------------------------------------------- | ------------------------------------ |
| **Tiêu đề trang**         | Text       | Thông báo                                                                 | Tiêu đề của trang thông báo          |
| **Icon trang**            | Icon       | Bell                                                                      | Icon đại diện cho thông báo          |
| **Số thông báo chưa đọc** | Badge      | Số lượng thông báo chưa đọc                                               | Badge hiển thị số thông báo chưa đọc |
| **Tab loại thông báo**    | Tabs       | Tất cả / Đơn hàng / Khuyến mãi / Yêu thích / Đánh giá / Hệ thống / Hỗ trợ | Tab để lọc theo loại thông báo       |
| **Bộ lọc loại**           | Select     | Lọc theo loại thông báo                                                   | Dropdown để lọc theo loại            |
| **Bộ lọc mức độ ưu tiên** | Select     | Lọc theo mức độ ưu tiên                                                   | Dropdown để lọc theo mức độ ưu tiên  |
| **Ô tìm kiếm**            | Input      | Tìm kiếm thông báo                                                        | Ô để tìm kiếm thông báo              |
| **Card thông báo**        | Card       | Thông tin thông báo                                                       | Card hiển thị thông tin thông báo    |
| **Icon loại thông báo**   | Icon       | Package / Percent / Heart / Star / AlertCircle / MessageSquare            | Icon đại diện cho loại thông báo     |
| **Tiêu đề thông báo**     | Text       | Tiêu đề thông báo                                                         | Tiêu đề của thông báo                |
| **Nội dung thông báo**    | Text       | Nội dung chi tiết thông báo                                               | Nội dung chi tiết của thông báo      |
| **Thời gian**             | Text       | Thời gian gửi thông báo                                                   | Thời gian thông báo được gửi         |
| **Trạng thái đọc**        | Badge      | Đã đọc / Chưa đọc                                                         | Trạng thái đã đọc hay chưa           |
| **Mức độ ưu tiên**        | Badge      | Thấp / Trung bình / Cao                                                   | Mức độ ưu tiên của thông báo         |
| **Nút hành động**         | Button     | Xem chi tiết / Đánh dấu đã đọc                                            | Nút để thực hiện hành động           |
| **Nút xóa**               | Button     | Xóa thông báo                                                             | Nút để xóa thông báo                 |
| **Phân trang**            | Pagination | Điều hướng trang                                                          | Phân trang cho danh sách thông báo   |

#### 1.1.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                                | Success                                                                                                                               | Failure                                                                                                                                              |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị danh sách thông báo** | Hiển thị danh sách tất cả thông báo của người dùng với thông tin đầy đủ bao gồm loại thông báo, tiêu đề, nội dung, thời gian, trạng thái đọc, và mức độ ưu tiên. Danh sách được sắp xếp theo thời gian mới nhất và hỗ trợ phân trang.                                      | Danh sách thông báo được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                                    | Danh sách thông báo không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.                            |
| **Lọc và tìm kiếm thông báo**    | Cho phép người dùng lọc thông báo theo loại (Đơn hàng, Khuyến mãi, Yêu thích, Đánh giá, Hệ thống, Hỗ trợ) và mức độ ưu tiên (Thấp, Trung bình, Cao), đồng thời tìm kiếm theo tiêu đề hoặc nội dung thông báo. Hệ thống sẽ cập nhật danh sách ngay lập tức khi có thay đổi. | Thông báo được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách được cập nhật ngay lập tức khi có thay đổi.                 | Thông báo không được lọc và tìm kiếm chính xác theo tiêu chí đã chọn. Danh sách không được cập nhật ngay lập tức khi có thay đổi.                    |
| **Đánh dấu đã đọc**              | Cho phép người dùng đánh dấu thông báo đã đọc hoặc chưa đọc. Hệ thống sẽ cập nhật trạng thái đọc và hiển thị số lượng thông báo chưa đọc. Có thể đánh dấu từng thông báo hoặc đánh dấu tất cả cùng lúc.                                                                    | Trạng thái đọc được cập nhật chính xác. Số lượng thông báo chưa đọc được hiển thị đúng. Người dùng có thể quản lý trạng thái dễ dàng. | Trạng thái đọc không được cập nhật chính xác. Số lượng thông báo chưa đọc không được hiển thị đúng. Người dùng không thể quản lý trạng thái dễ dàng. |

### 1.2 THÔNG BÁO GIẢM GIÁ

#### 1.2.1 Thông tin màn hình:

| Screen        | Thông báo giảm giá                             |
| ------------- | ---------------------------------------------- |
| Description   | Thông báo khi sản phẩm yêu thích có khuyến mãi |
| Screen Access | Từ tab "Khuyến mãi" trong trang thông báo      |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                    | Type   | Data                         | Description                      |
| ----------------------- | ------ | ---------------------------- | -------------------------------- |
| **Icon khuyến mãi**     | Icon   | Percent                      | Icon đại diện cho khuyến mãi     |
| **Tiêu đề khuyến mãi**  | Text   | Tiêu đề thông báo khuyến mãi | Tiêu đề của thông báo khuyến mãi |
| **Nội dung khuyến mãi** | Text   | Nội dung chi tiết khuyến mãi | Nội dung chi tiết của khuyến mãi |
| **Phần trăm giảm giá**  | Text   | Phần trăm giảm giá           | Phần trăm giảm giá được áp dụng  |
| **Thời gian áp dụng**   | Text   | Thời gian áp dụng khuyến mãi | Thời gian bắt đầu và kết thúc    |
| **Ngày hết hạn**        | Text   | Ngày hết hạn khuyến mãi      | Ngày hết hạn của khuyến mãi      |
| **Danh sách sản phẩm**  | List   | Danh sách sản phẩm áp dụng   | Danh sách sản phẩm được áp dụng  |
| **Nút mua ngay**        | Button | Mua ngay                     | Nút để mua sản phẩm ngay         |
| **Nút xem chi tiết**    | Button | Xem chi tiết                 | Nút để xem chi tiết khuyến mãi   |
| **Mức độ ưu tiên**      | Badge  | Trung bình                   | Mức độ ưu tiên của thông báo     |

#### 1.2.3 Hành động và xử lý:

| Action Name                       | Description                                                                                                                                                                                                              | Success                                                                                                                         | Failure                                                                                                                                             |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị thông báo khuyến mãi** | Hiển thị thông báo khuyến mãi với thông tin đầy đủ bao gồm phần trăm giảm giá, thời gian áp dụng, danh sách sản phẩm được áp dụng, và ngày hết hạn. Thông báo được hiển thị với icon và màu sắc phù hợp để dễ nhận biết. | Thông báo khuyến mãi được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                             | Thông báo khuyến mãi không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.                          |
| **Truy cập sản phẩm khuyến mãi**  | Cho phép người dùng truy cập trực tiếp đến sản phẩm hoặc danh mục sản phẩm được áp dụng khuyến mãi thông qua nút "Mua ngay" hoặc "Xem chi tiết". Hệ thống sẽ chuyển hướng đến trang sản phẩm tương ứng.                  | Người dùng được chuyển hướng chính xác đến sản phẩm khuyến mãi. Trang sản phẩm hiển thị đầy đủ thông tin khuyến mãi.            | Người dùng không được chuyển hướng chính xác đến sản phẩm khuyến mãi. Trang sản phẩm không hiển thị đầy đủ thông tin khuyến mãi.                    |
| **Theo dõi thời gian khuyến mãi** | Hiển thị thời gian còn lại của khuyến mãi và cảnh báo khi khuyến mãi sắp hết hạn. Hệ thống sẽ cập nhật thời gian real-time và thông báo cho người dùng khi khuyến mãi sắp kết thúc.                                      | Thời gian khuyến mãi được hiển thị chính xác và cập nhật real-time. Cảnh báo được hiển thị kịp thời khi khuyến mãi sắp hết hạn. | Thời gian khuyến mãi không được hiển thị chính xác hoặc không cập nhật real-time. Cảnh báo không được hiển thị kịp thời khi khuyến mãi sắp hết hạn. |

### 1.3 CẬP NHẬT ĐƠN HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Cập nhật đơn hàng                                  |
| ------------- | -------------------------------------------------- |
| Description   | Trạng thái đơn hàng (xác nhận, đang giao, đã giao) |
| Screen Access | Từ tab "Đơn hàng" trong trang thông báo            |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                    | Type   | Data                           | Description                    |
| ----------------------- | ------ | ------------------------------ | ------------------------------ |
| **Icon đơn hàng**       | Icon   | Package                        | Icon đại diện cho đơn hàng     |
| **Tiêu đề cập nhật**    | Text   | Tiêu đề thông báo đơn hàng     | Tiêu đề của thông báo đơn hàng |
| **Nội dung cập nhật**   | Text   | Nội dung chi tiết cập nhật     | Nội dung chi tiết của cập nhật |
| **Mã đơn hàng**         | Text   | Mã định danh đơn hàng          | Mã định danh của đơn hàng      |
| **Trạng thái mới**      | Badge  | Xác nhận / Đang giao / Đã giao | Trạng thái mới của đơn hàng    |
| **Thời gian cập nhật**  | Text   | Thời gian cập nhật trạng thái  | Thời gian cập nhật trạng thái  |
| **Thông tin giao hàng** | Text   | Thông tin giao hàng            | Thông tin về việc giao hàng    |
| **Dự kiến nhận hàng**   | Text   | Dự kiến nhận hàng              | Thời gian dự kiến nhận hàng    |
| **Nút xem chi tiết**    | Button | Xem chi tiết đơn hàng          | Nút để xem chi tiết đơn hàng   |
| **Nút theo dõi**        | Button | Theo dõi đơn hàng              | Nút để theo dõi đơn hàng       |
| **Mức độ ưu tiên**      | Badge  | Cao                            | Mức độ ưu tiên của thông báo   |

#### 1.3.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                   | Success                                                                                                                 | Failure                                                                                                                                  |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị cập nhật đơn hàng** | Hiển thị thông báo cập nhật trạng thái đơn hàng với thông tin đầy đủ bao gồm mã đơn hàng, trạng thái mới, thời gian cập nhật, thông tin giao hàng, và dự kiến nhận hàng. Thông báo được hiển thị với màu sắc và icon phù hợp theo trạng thái. | Thông báo cập nhật đơn hàng được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.              | Thông báo cập nhật đơn hàng không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.        |
| **Truy cập chi tiết đơn hàng** | Cho phép người dùng truy cập trực tiếp đến trang chi tiết đơn hàng thông qua nút "Xem chi tiết đơn hàng" hoặc "Theo dõi đơn hàng". Hệ thống sẽ chuyển hướng đến trang quản lý đơn hàng tương ứng.                                             | Người dùng được chuyển hướng chính xác đến trang chi tiết đơn hàng. Trang đơn hàng hiển thị đầy đủ thông tin cập nhật.  | Người dùng không được chuyển hướng chính xác đến trang chi tiết đơn hàng. Trang đơn hàng không hiển thị đầy đủ thông tin cập nhật.       |
| **Theo dõi tiến độ giao hàng** | Hiển thị thông tin chi tiết về tiến độ giao hàng bao gồm vị trí hiện tại, thời gian dự kiến nhận hàng, và thông tin liên hệ shipper. Hệ thống sẽ cập nhật thông tin real-time khi có thay đổi.                                                | Thông tin tiến độ giao hàng được hiển thị chính xác và cập nhật real-time. Người dùng có thể theo dõi đơn hàng dễ dàng. | Thông tin tiến độ giao hàng không được hiển thị chính xác hoặc không cập nhật real-time. Người dùng không thể theo dõi đơn hàng dễ dàng. |

### 1.4 THÔNG BÁO CÓ HÀNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Thông báo có hàng                                                           |
| ------------- | --------------------------------------------------------------------------- |
| Description   | Thông báo khi sản phẩm đặt trước hoặc sản phẩm theo yêu cầu đã được nhập về |
| Screen Access | Từ tab "Yêu thích" hoặc "Hệ thống" trong trang thông báo                    |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                            | Description                        |
| --------------------- | ------ | ------------------------------- | ---------------------------------- |
| **Icon có hàng**      | Icon   | Package / Heart                 | Icon đại diện cho có hàng          |
| **Tiêu đề có hàng**   | Text   | Tiêu đề thông báo có hàng       | Tiêu đề của thông báo có hàng      |
| **Nội dung có hàng**  | Text   | Nội dung chi tiết có hàng       | Nội dung chi tiết của có hàng      |
| **Tên sản phẩm**      | Text   | Tên sản phẩm có hàng            | Tên sản phẩm đã có hàng trở lại    |
| **Loại thông báo**    | Badge  | Đặt trước / Yêu cầu / Yêu thích | Loại thông báo có hàng             |
| **Số lượng có sẵn**   | Text   | Số lượng sản phẩm có sẵn        | Số lượng sản phẩm có sẵn           |
| **Giá sản phẩm**      | Text   | Giá sản phẩm                    | Giá hiện tại của sản phẩm          |
| **Thời gian có hàng** | Text   | Thời gian có hàng               | Thời gian sản phẩm có hàng trở lại |
| **Cài đặt kênh thông báo** | Select | Push / Email / SMS / Tất cả     | Chọn kênh nhận thông báo           |
| **Nút mua ngay**      | Button | Mua ngay                        | Nút để mua sản phẩm ngay           |
| **Nút xem sản phẩm**  | Button | Xem sản phẩm                    | Nút để xem chi tiết sản phẩm       |
| **Mức độ ưu tiên**    | Badge  | Trung bình                      | Mức độ ưu tiên của thông báo       |

#### 1.4.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                               | Success                                                                                                                            | Failure                                                                                                                                             |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hiển thị thông báo có hàng**   | Hiển thị thông báo có hàng với thông tin đầy đủ bao gồm tên sản phẩm, loại thông báo, số lượng có sẵn, giá sản phẩm, và thời gian có hàng. Thông báo được hiển thị với icon và màu sắc phù hợp theo loại. | Thông báo có hàng được hiển thị đầy đủ và chính xác. Thông tin được trình bày rõ ràng và dễ đọc.                                   | Thông báo có hàng không được hiển thị đầy đủ hoặc không chính xác. Thông tin không được trình bày rõ ràng hoặc khó đọc.                             |
| **Truy cập sản phẩm có hàng**    | Cho phép người dùng truy cập trực tiếp đến trang sản phẩm đã có hàng thông qua nút "Mua ngay" hoặc "Xem sản phẩm". Hệ thống sẽ chuyển hướng đến trang sản phẩm tương ứng với thông tin cập nhật.          | Người dùng được chuyển hướng chính xác đến trang sản phẩm có hàng. Trang sản phẩm hiển thị đầy đủ thông tin và trạng thái có hàng. | Người dùng không được chuyển hướng chính xác đến trang sản phẩm có hàng. Trang sản phẩm không hiển thị đầy đủ thông tin và trạng thái có hàng.      |
| **Cập nhật trạng thái sản phẩm** | Tự động cập nhật trạng thái sản phẩm từ "Hết hàng" hoặc "Đặt trước" thành "Có hàng" khi sản phẩm được nhập về. Hệ thống sẽ gửi thông báo cho tất cả người dùng đã quan tâm đến sản phẩm đó qua các kênh mà người dùng đã chọn (push notification, email, hoặc SMS). Người dùng có thể cài đặt kênh nhận thông báo trong cài đặt tài khoản.               | Trạng thái sản phẩm được cập nhật chính xác và thông báo được gửi đến đúng người dùng qua kênh đã chọn. Người dùng nhận được thông báo kịp thời.    | Trạng thái sản phẩm không được cập nhật chính xác hoặc thông báo không được gửi đến đúng người dùng. Thông báo không được gửi qua kênh đã chọn. Người dùng không nhận được thông báo kịp thời. |

### 1.5 QUẢN LÝ TRẠNG THÁI THÔNG BÁO

#### 1.5.1 Thông tin màn hình:

| Screen        | Quản lý trạng thái thông báo                           |
| ------------- | ------------------------------------------------------ |
| Description   | Theo dõi và quản lý trạng thái các thông báo           |
| Screen Access | Từ trang danh sách thông báo với các chức năng quản lý |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                      | Type   | Data                          | Description                             |
| ------------------------- | ------ | ----------------------------- | --------------------------------------- |
| **Số thông báo chưa đọc** | Badge  | Số lượng thông báo chưa đọc   | Hiển thị số lượng thông báo chưa đọc    |
| **Nút đánh dấu tất cả**   | Button | Đánh dấu tất cả đã đọc        | Nút để đánh dấu tất cả thông báo đã đọc |
| **Nút xóa tất cả**        | Button | Xóa tất cả thông báo          | Nút để xóa tất cả thông báo             |
| **Nút đánh dấu đã đọc**   | Button | Đánh dấu đã đọc               | Nút để đánh dấu thông báo đã đọc        |
| **Nút xóa thông báo**     | Button | Xóa thông báo                 | Nút để xóa thông báo                    |
| **Trạng thái đọc**        | Badge  | Đã đọc / Chưa đọc             | Badge hiển thị trạng thái đọc           |
| **Màu trạng thái**        | Color  | Xanh / Xám                    | Màu sắc đại diện cho trạng thái đọc     |
| **Thời gian cập nhật**    | Text   | Thời gian cập nhật cuối       | Thời gian cập nhật trạng thái cuối      |
| **Thông báo cập nhật**    | Toast  | Thông báo cập nhật trạng thái | Thông báo khi trạng thái thay đổi       |
| **Cập nhật real-time**    | System | Cập nhật tự động              | Hệ thống cập nhật trạng thái tự động    |

#### 1.5.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                             | Success                                                                                                                                 | Failure                                                                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Đánh dấu thông báo đã đọc**   | Cho phép người dùng đánh dấu thông báo đã đọc hoặc chưa đọc. Hệ thống sẽ cập nhật trạng thái đọc và hiển thị số lượng thông báo chưa đọc. Có thể đánh dấu từng thông báo hoặc đánh dấu tất cả cùng lúc. | Trạng thái đọc được cập nhật chính xác và số lượng thông báo chưa đọc được hiển thị đúng. Người dùng có thể quản lý trạng thái dễ dàng. | Trạng thái đọc không được cập nhật chính xác hoặc số lượng thông báo chưa đọc không được hiển thị đúng. Người dùng không thể quản lý trạng thái dễ dàng. |
| **Xóa thông báo**               | Cho phép người dùng xóa thông báo không cần thiết. Có thể xóa từng thông báo hoặc xóa tất cả thông báo cùng lúc. Hệ thống sẽ hiển thị xác nhận trước khi xóa và cập nhật danh sách sau khi xóa.         | Thông báo được xóa thành công và danh sách được cập nhật. Xác nhận xóa được hiển thị trước khi thực hiện.                               | Thông báo không được xóa thành công hoặc danh sách không được cập nhật. Xác nhận xóa không được hiển thị trước khi thực hiện.                            |
| **Cập nhật số lượng thông báo** | Tự động cập nhật số lượng thông báo chưa đọc khi có thông báo mới hoặc khi trạng thái đọc thay đổi. Hệ thống sẽ hiển thị số lượng chính xác và cập nhật real-time.                                      | Số lượng thông báo chưa đọc được cập nhật chính xác và hiển thị real-time. Badge số lượng được cập nhật kịp thời.                       | Số lượng thông báo chưa đọc không được cập nhật chính xác hoặc không hiển thị real-time. Badge số lượng không được cập nhật kịp thời.                    |
