# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng đổi/trả hàng của User (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng đổi/trả hàng](#1-chức-năng-đổitrả-hàng)
   - 1.1 [Tạo yêu cầu đổi/trả hàng](#11-tạo-yêu-cầu-đổitrả-hàng)
   - 1.2 [Xem danh sách yêu cầu](#12-xem-danh-sách-yêu-cầu) - **ĐÃ SỬA**
   - 1.3 [State machine diagram](#13-state-machine-diagram) - **MỚI**

---

## 1. CHỨC NĂNG ĐỔI/TRẢ HÀNG

### 1.1 TẠO YÊU CẦU ĐỔI/TRẢ HÀNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Tạo yêu cầu đổi/trả hàng                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Cho phép người dùng tạo yêu cầu đổi/trả hàng cho sản phẩm đã mua             |
| Screen Access | Người dùng chọn **Yêu cầu đổi/trả hàng** từ trang chi tiết đơn hàng          |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Form yêu cầu**      | Form         | Lý do, sản phẩm, số lượng... | Form để tạo yêu cầu đổi/trả hàng     |
| **Nút gửi yêu cầu**   | Button       | Gửi yêu cầu             | Nút để gửi yêu cầu đổi/trả hàng      |

---

### 1.2 XEM DANH SÁCH YÊU CẦU - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Danh sách yêu cầu đổi/trả hàng                                                      |
| ------------- | ----------------------------------------------------------------------------------- |
| Description   | Hiển thị danh sách các yêu cầu đổi/trả hàng với state machine diagram              |
| Screen Access | Người dùng chọn **Yêu cầu đổi/trả hàng** từ menu chính                              |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Danh sách yêu cầu**     | Table        | Mã yêu cầu, đơn hàng, sản phẩm, trạng thái... | Hiển thị các yêu cầu đổi/trả hàng              |
| **Badge trạng thái**      | Badge        | Chờ duyệt, Đã duyệt, Từ chối, Đang xử lý, Hoàn thành, Đã đóng | **MỚI**: Hiển thị trạng thái theo state machine |
| **Bộ lọc trạng thái**     | Select       | Tất cả, Chờ duyệt, Đã duyệt...          | **MỚI**: Lọc theo trạng thái                   |
| **State machine diagram** | Card         | Quy trình đổi/trả hàng                  | **MỚI**: Hiển thị state machine diagram        |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem danh sách yêu cầu** | Hiển thị danh sách tất cả các yêu cầu đổi/trả hàng với trạng thái hiện tại. Hệ thống sử dụng state machine để quản lý trạng thái và valid transitions.                                                                                  | Danh sách yêu cầu được hiển thị thành công với đầy đủ thông tin.                            | Không thể tải danh sách yêu cầu. Thông tin trạng thái không chính xác.                      |
| **State machine validation** | **MỚI**: Hệ thống sử dụng state machine để quản lý trạng thái yêu cầu đổi/trả hàng. Chỉ cho phép chuyển trạng thái theo valid transitions. Các trạng thái: pending → approved/denied → processing → completed/closed.                    | Trạng thái được quản lý chính xác theo state machine. Valid transitions được thực thi đúng. | Trạng thái không được quản lý đúng. Invalid transitions được thực thi.                    |
| **Valid transitions**    | **MỚI**: Hệ thống chỉ cho phép chuyển trạng thái theo valid transitions: pending → approved/denied, approved → processing, processing → completed, completed → closed. Không cho phép chuyển trạng thái không hợp lệ (ví dụ: pending → completed). | Valid transitions được thực thi thành công.                                                 | Invalid transitions được thực thi. Trạng thái không được cập nhật đúng.                    |

#### 1.2.4 State Machine Diagram (MỚI):

```
[pending] → [approved] → [processing] → [completed] → [closed]
     ↓           ↓
  [denied] → [closed]
```

**Valid Transitions:**
- `pending` → `approved` (Admin duyệt)
- `pending` → `denied` (Admin từ chối)
- `pending` → `closed` (User hủy)
- `approved` → `processing` (Bắt đầu xử lý)
- `approved` → `closed` (Hủy sau khi duyệt)
- `denied` → `closed` (Đóng yêu cầu bị từ chối)
- `processing` → `completed` (Hoàn thành xử lý)
- `processing` → `closed` (Hủy trong quá trình xử lý)
- `completed` → `closed` (Đóng yêu cầu đã hoàn thành)

**Invalid Transitions:**
- `pending` → `completed` (Không thể hoàn thành trực tiếp)
- `denied` → `processing` (Không thể xử lý yêu cầu bị từ chối)
- `closed` → `pending` (Không thể mở lại yêu cầu đã đóng)

---

### 1.3 STATE MACHINE DIAGRAM - **MỚI**

#### 1.3.1 Thông tin màn hình:

| Screen        | State machine diagram cho đổi/trả hàng                                                      |
| ------------- | -------------------------------------------------------------------------------------------- |
| Description   | Hiển thị state machine diagram và valid transitions cho yêu cầu đổi/trả hàng                |
| Screen Access | Hiển thị trong trang danh sách yêu cầu đổi/trả hàng, phần quy trình                         |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Card quy trình**    | Card         | Quy trình đổi/trả hàng                  | **MỚI**: Hiển thị state machine diagram       |
| **Badge trạng thái**  | Badge Group  | Chờ duyệt → Đã duyệt → Đang xử lý → Hoàn thành | **MỚI**: Hiển thị các trạng thái và transitions |
| **Mô tả transitions** | Text         | Valid transitions: pending → approved... | **MỚI**: Mô tả các valid transitions          |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Hiển thị state machine** | Hiển thị state machine diagram và valid transitions để người dùng hiểu quy trình đổi/trả hàng.                                                                                                                                    | State machine diagram được hiển thị rõ ràng. Người dùng hiểu quy trình.                   | State machine diagram không được hiển thị. Thông tin không rõ ràng.                        |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **State machine diagram**: Thêm state machine diagram để quản lý trạng thái yêu cầu đổi/trả hàng
2. **Valid transitions**: Chỉ cho phép chuyển trạng thái theo valid transitions
3. **State validation**: Kiểm tra và từ chối invalid transitions
4. **UI cải thiện**: Hiển thị state machine diagram và valid transitions trong UI
5. **Status badges**: Hiển thị trạng thái với màu sắc phù hợp theo state machine
6. **Filter by status**: Cho phép lọc yêu cầu theo trạng thái

