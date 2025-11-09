# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý đơn hàng của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý đơn hàng](#1-chức-năng-quản-lý-đơn-hàng)
   - 1.1 [Xem chi tiết đơn hàng](#11-xem-chi-tiết-đơn-hàng) - **ĐÃ SỬA**
   - 1.2 [Hủy đơn hàng](#12-hủy-đơn-hàng) - **ĐÃ SỬA**
   - 1.3 [Hiển thị danh sách đơn hàng](#13-hiển-thị-danh-sách-đơn-hàng)

---

## 1. CHỨC NĂNG QUẢN LÝ ĐƠN HÀNG

### 1.1 XEM CHI TIẾT ĐƠN HÀNG - **ĐÃ SỬA**

#### 1.1.1 Thông tin màn hình:

| Screen        | Chi tiết đơn hàng                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Hiển thị thông tin chi tiết của đơn hàng với kiểm tra authorization   |
| Screen Access | Người dùng click **Xem chi tiết** từ danh sách đơn hàng                |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Loading indicator**     | Spinner      | Đang tải...                             | **MỚI**: Hiển thị khi đang kiểm tra authorization |
| **Alert không có quyền**  | Alert        | Bạn không có quyền xem đơn hàng này     | **MỚI**: Hiển thị khi không có quyền           |
| **Nút quay lại**          | Button       | Quay lại danh sách đơn hàng              | **MỚI**: Nút để quay lại khi không có quyền    |
| **Thông tin đơn hàng**    | Card         | Mã đơn, ngày tạo, trạng thái, sản phẩm... | Hiển thị chi tiết đơn hàng                     |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem chi tiết đơn hàng** | Cho phép người dùng xem thông tin chi tiết của đơn hàng. Hệ thống sẽ kiểm tra authorization trước khi hiển thị.                                                                                                                          | Đơn hàng được hiển thị thành công với đầy đủ thông tin.                                    | Người dùng không có quyền xem đơn hàng này. Hiển thị thông báo lỗi và chuyển hướng.        |
| **Kiểm tra authorization** | **MỚI**: Trước khi hiển thị đơn hàng, hệ thống kiểm tra xem đơn hàng có thuộc về user hiện tại không (order.userId === currentUserId). Nếu không, hệ thống sẽ từ chối và hiển thị thông báo lỗi.                                           | Authorization được kiểm tra thành công. Đơn hàng thuộc về user hiện tại.                  | Đơn hàng không thuộc về user hiện tại. Hiển thị: "Bạn không có quyền xem đơn hàng này".    |
| **Loading state**        | **MỚI**: Trong quá trình kiểm tra authorization, hệ thống hiển thị loading state để người dùng biết đang xử lý.                                                                                                                          | Loading state được hiển thị trong quá trình kiểm tra.                                     | Lỗi khi hiển thị loading state.                                                            |
| **Redirect khi không có quyền** | **MỚI**: Nếu người dùng không có quyền xem đơn hàng, hệ thống tự động chuyển hướng về trang danh sách đơn hàng và hiển thị thông báo lỗi.                                                                                                | Người dùng được chuyển hướng về trang danh sách đơn hàng.                                  | Không thể chuyển hướng. Người dùng vẫn ở trang chi tiết.                                   |

#### 1.1.4 Authorization Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **User Ownership**  | Chỉ cho phép user xem đơn hàng của chính mình (order.userId === currentUserId) | Từ chối và redirect nếu không phải chủ sở hữu |
| **Session Check**   | Kiểm tra session/user ID từ authentication system                          | Đảm bảo user đã đăng nhập                |
| **Real-time Check** | Kiểm tra authorization mỗi khi truy cập trang chi tiết đơn hàng            | Đảm bảo tính bảo mật                      |

---

### 1.2 HỦY ĐƠN HÀNG - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Hủy đơn hàng                                                      |
| ------------- | ----------------------------------------------------------------- |
| Description   | Cho phép người dùng hủy đơn hàng với kiểm tra authorization và validation |
| Screen Access | Hiển thị trong trang chi tiết đơn hàng, chỉ khi đơn chưa giao    |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Card hủy đơn hàng**     | Card         | Chỉ hiển thị khi đơn chưa giao          | **MỚI**: Conditional rendering                  |
| **Dialog xác nhận**       | Dialog       | Xác nhận hủy đơn hàng                   | **MỚI**: Dialog yêu cầu xác nhận               |
| **Textarea lý do**        | Textarea     | Nhập lý do hủy đơn hàng *               | **MỚI**: Bắt buộc nhập lý do                   |
| **Nút xác nhận hủy**      | Button       | Xác nhận hủy                            | Nút để xác nhận hủy đơn hàng                   |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Hủy đơn hàng**         | Cho phép người dùng hủy đơn hàng. Hệ thống sẽ kiểm tra authorization, trạng thái đơn hàng và yêu cầu nhập lý do trước khi hủy.                                                                                                            | Đơn hàng được hủy thành công. Thông báo xác nhận hiển thị.                                | Người dùng không có quyền hủy. Đơn hàng đã giao hoặc đã hủy. Lý do không được nhập.        |
| **Kiểm tra authorization** | **MỚI**: Trước khi cho phép hủy đơn hàng, hệ thống kiểm tra lại authorization (order.userId === currentUserId). Nếu không phải chủ sở hữu, hệ thống sẽ từ chối.                                                                          | Authorization được kiểm tra thành công. Người dùng có quyền hủy đơn hàng.                  | Người dùng không có quyền hủy đơn hàng. Hiển thị: "Bạn không có quyền hủy đơn hàng này".  |
| **Kiểm tra trạng thái**  | **MỚI**: Hệ thống kiểm tra trạng thái đơn hàng. Chỉ cho phép hủy nếu đơn hàng chưa giao (status !== "delivered" && status !== "cancelled"). Nếu đã giao hoặc đã hủy, hệ thống sẽ từ chối.                                                  | Trạng thái đơn hàng hợp lệ để hủy. Cho phép hủy đơn hàng.                                 | Đơn hàng đã giao hoặc đã hủy. Hiển thị: "Không thể hủy đơn hàng đã giao hoặc đã hủy".      |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu người dùng phải nhập lý do hủy đơn hàng (tối thiểu 10 ký tự). Nếu không nhập hoặc quá ngắn, hệ thống sẽ từ chối.                                                                                                  | Lý do được validate thành công. Cho phép hủy đơn hàng.                                    | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị: "Vui lòng nhập lý do hủy đơn hàng". |
| **Conditional rendering** | **MỚI**: Card "Hủy đơn hàng" chỉ hiển thị khi đơn hàng chưa giao và chưa hủy. Nếu đã giao hoặc đã hủy, card sẽ không hiển thị.                                                                                                            | Card được hiển thị/ẩn đúng theo trạng thái đơn hàng.                                     | Card hiển thị sai trạng thái.                                                              |

#### 1.2.4 Validation Rules (MỚI):

| Field           | Rule                                    | Error Message                                    |
| --------------- | --------------------------------------- | ------------------------------------------------ |
| **Authorization** | order.userId === currentUserId          | "Bạn không có quyền hủy đơn hàng này"           |
| **Trạng thái**  | status !== "delivered" && status !== "cancelled" | "Không thể hủy đơn hàng đã giao hoặc đã hủy"   |
| **Lý do**       | Bắt buộc, tối thiểu 10 ký tự            | "Vui lòng nhập lý do hủy đơn hàng (tối thiểu 10 ký tự)" |

---

### 1.3 HIỂN THỊ DANH SÁCH ĐƠN HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Danh sách đơn hàng                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả đơn hàng của người dùng                      |
| Screen Access | Người dùng chọn **Quản lý đơn hàng** từ menu chính                     |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách đơn hàng** | Table        | Mã đơn, ngày, trạng thái... | Hiển thị các đơn hàng                |
| **Bộ lọc**            | Filter       | Trạng thái, thời gian... | Lọc đơn hàng theo tiêu chí           |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Authorization check**: Kiểm tra quyền truy cập trước khi hiển thị đơn hàng
2. **User ownership validation**: Chỉ cho phép user xem/hủy đơn hàng của chính mình
3. **Status validation**: Chỉ cho phép hủy đơn hàng chưa giao
4. **Loading state**: Hiển thị loading khi đang kiểm tra authorization
5. **Error handling**: Hiển thị thông báo lỗi rõ ràng khi không có quyền
6. **Conditional rendering**: Chỉ hiển thị nút hủy khi đơn hàng có thể hủy được
7. **Reason validation**: Yêu cầu nhập lý do hủy đơn hàng (tối thiểu 10 ký tự)

