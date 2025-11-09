# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng tìm kiếm sách của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng tìm kiếm sách](#1-chức-năng-tìm-kiếm-sách)
   - 1.1 [Tìm kiếm sách](#11-tìm-kiếm-sách) - **ĐÃ SỬA**
   - 1.2 [Gợi ý tìm kiếm](#12-gợi-ý-tìm-kiếm)
   - 1.3 [Lịch sử tìm kiếm](#13-lịch-sử-tìm-kiếm)

---

## 1. CHỨC NĂNG TÌM KIẾM SÁCH

### 1.1 TÌM KIẾM SÁCH - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Tìm kiếm sách                                                                 |
| ------------- | ----------------------------------------------------------------------------- |
| Description   | Cho phép người dùng tìm kiếm sách theo từ khóa, tác giả, nhà xuất bản        |
| Screen Access | Người dùng truy cập trang **Tìm kiếm** từ menu chính hoặc thanh tìm kiếm     |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type             | Data                                    | Description                                    |
| ----------------------- | ---------------- | --------------------------------------- | ---------------------------------------------- |
| **Thanh tìm kiếm**      | Input (Search)   | Tìm kiếm sách, tác giả, NXB...         | Ô nhập từ khóa tìm kiếm                        |
| **Nút tìm kiếm**        | Button           | Tìm kiếm                                | Nút để thực hiện tìm kiếm                      |
| **Kết quả tìm kiếm**    | Grid/List        | Danh sách sách                          | Hiển thị kết quả tìm kiếm                     |
| **Pagination**          | Pagination       | Trang 1, 2, 3...                       | **MỚI**: Phân trang kết quả (20 items/trang)  |
| **Thông tin phân trang** | Text             | Hiển thị 1-20 trong tổng số X sách     | **MỚI**: Hiển thị số lượng kết quả             |
| **Bộ lọc**              | Filter Panel     | Thể loại, giá, nhà xuất bản...        | Panel bộ lọc kết quả                          |
| **Sắp xếp**             | Select           | Mới nhất, Giá tăng, Giá giảm...        | Dropdown sắp xếp kết quả                      |

#### 1.1.3 Hành động và xử lý:

| Action Name          | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Tìm kiếm sách**    | Cho phép người dùng nhập từ khóa và tìm kiếm sách trong hệ thống. Hệ thống sẽ tìm kiếm theo tên sách, tác giả, nhà xuất bản và hiển thị kết quả.                                                                                          | Tìm thấy kết quả và hiển thị danh sách sách phù hợp.                                       | Không tìm thấy kết quả nào phù hợp với từ khóa.                                            |
| **Phân trang kết quả** | **MỚI**: Hệ thống tự động phân trang kết quả tìm kiếm với mặc định 20 items mỗi trang để tránh quá tải khi có nhiều kết quả. Người dùng có thể chuyển trang để xem thêm kết quả.                                                           | Kết quả được phân trang thành công. Hiển thị thông tin "Hiển thị X-Y trong tổng số Z sách". | Lỗi khi phân trang do dữ liệu quá lớn hoặc lỗi hệ thống.                                   |
| **Lọc kết quả**      | Người dùng có thể áp dụng các bộ lọc như thể loại, khoảng giá, nhà xuất bản để thu hẹp kết quả tìm kiếm.                                                                                                                                    | Kết quả được lọc thành công theo tiêu chí đã chọn.                                        | Không có kết quả nào phù hợp sau khi lọc.                                                  |
| **Sắp xếp kết quả**  | Người dùng có thể sắp xếp kết quả theo nhiều tiêu chí như giá tăng/giảm, mới nhất, đánh giá cao nhất.                                                                                                                                    | Kết quả được sắp xếp thành công theo tiêu chí đã chọn.                                    | Lỗi khi sắp xếp do dữ liệu không hợp lệ.                                                   |
| **Reset phân trang** | **MỚI**: Khi người dùng thay đổi từ khóa tìm kiếm hoặc bộ lọc, hệ thống tự động reset về trang 1 để hiển thị kết quả mới từ đầu.                                                                                                            | Phân trang được reset về trang 1 khi có thay đổi tìm kiếm.                                | Lỗi khi reset phân trang.                                                                  |

#### 1.1.4 Validation Rules (MỚI):

| Field        | Rule                                                      | Error Message                                    |
| ------------ | --------------------------------------------------------- | ------------------------------------------------ |
| **Từ khóa**  | Tối thiểu 1 ký tự, tối đa 100 ký tự                      | "Từ khóa tìm kiếm phải từ 1-100 ký tự"          |
| **Pagination** | Mặc định 20 items/trang, tối đa 100 items/trang          | "Số lượng items mỗi trang không hợp lệ"          |
| **Kết quả**  | Tối đa 10,000 kết quả được hiển thị (phân trang)         | "Quá nhiều kết quả, vui lòng thu hẹp tìm kiếm"   |

---

### 1.2 GỢI Ý TÌM KIẾM

#### 1.2.1 Thông tin màn hình:

| Screen        | Gợi ý tìm kiếm                                                              |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Hiển thị các gợi ý tìm kiếm phổ biến và từ khóa liên quan khi người dùng nhập |
| Screen Access | Tự động hiển thị khi người dùng nhập vào thanh tìm kiếm                      |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item              | Type         | Data                    | Description                          |
| ----------------- | ------------ | ----------------------- | ------------------------------------ |
| **Dropdown gợi ý** | Dropdown     | Danh sách từ khóa       | Hiển thị gợi ý khi người dùng nhập   |
| **Từ khóa phổ biến** | Badge Group  | "Sách mới", "Bestseller" | Hiển thị các từ khóa tìm kiếm phổ biến |

---

### 1.3 LỊCH SỬ TÌM KIẾM

#### 1.3.1 Thông tin màn hình:

| Screen        | Lịch sử tìm kiếm                                                      |
| ------------- | --------------------------------------------------------------------- |
| Description   | Hiển thị danh sách các từ khóa đã tìm kiếm gần đây                    |
| Screen Access | Hiển thị trong dropdown khi click vào thanh tìm kiếm                  |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data              | Description                        |
| --------------------- | ------------ | ----------------- | ---------------------------------- |
| **Danh sách lịch sử** | List         | Từ khóa + thời gian | Hiển thị các từ khóa đã tìm kiếm  |
| **Nút xóa lịch sử**   | Button       | Xóa tất cả        | Xóa toàn bộ lịch sử tìm kiếm      |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Thêm Pagination**: Mặc định 20 items/trang, tối đa 100 items/trang để tránh quá tải khi có nhiều kết quả
2. **Thông tin phân trang**: Hiển thị "Hiển thị X-Y trong tổng số Z sách" để người dùng biết vị trí hiện tại
3. **Auto-reset pagination**: Tự động reset về trang 1 khi thay đổi từ khóa hoặc bộ lọc
4. **Validation**: Thêm validation cho từ khóa tìm kiếm và số lượng items mỗi trang
5. **Performance**: Giới hạn số lượng kết quả hiển thị để tối ưu hiệu suất

