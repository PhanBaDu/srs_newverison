# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý nhân viên của Admin (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý nhân viên](#1-chức-năng-quản-lý-nhân-viên)
   - 1.1 [Xem danh sách nhân viên](#11-xem-danh-sách-nhân-viên)
   - 1.2 [Khóa/Mở khóa tài khoản](#12-khóamở-khóa-tài-khoản) - **ĐÃ SỬA**
   - 1.3 [Xóa tài khoản](#13-xóa-tài-khoản) - **ĐÃ SỬA**
   - 1.4 [Xem audit log](#14-xem-audit-log) - **MỚI**

---

## 1. CHỨC NĂNG QUẢN LÝ NHÂN VIÊN

### 1.1 XEM DANH SÁCH NHÂN VIÊN

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách nhân viên                                                      |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Hiển thị danh sách tất cả nhân viên trong hệ thống với thông tin cơ bản  |
| Screen Access | Admin chọn **Quản lý nhân viên** từ menu chính                           |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                    | Description                          |
| --------------------- | ------------ | ----------------------- | ------------------------------------ |
| **Danh sách nhân viên** | Table        | Tên, email, vị trí, trạng thái | Hiển thị thông tin nhân viên         |
| **Bộ lọc**            | Filter       | Vị trí, trạng thái, thời gian | Lọc nhân viên theo tiêu chí          |
| **Nút xem chi tiết** | Button       | Xem chi tiết            | Chuyển đến trang chi tiết nhân viên  |

---

### 1.2 KHÓA/MỞ KHÓA TÀI KHOẢN - **ĐÃ SỬA**

#### 1.2.1 Thông tin màn hình:

| Screen        | Khóa/Mở khóa tài khoản nhân viên                                                      |
| ------------- | -------------------------------------------------------------------------------------- |
| Description   | Cho phép Admin khóa hoặc mở khóa tài khoản nhân viên với lý do và ghi nhận audit log  |
| Screen Access | Admin click nút **Khóa tài khoản** hoặc **Mở khóa tài khoản** từ trang chi tiết nhân viên |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Dialog khóa tài khoản** | Dialog       | Xác nhận khóa tài khoản                 | **MỚI**: Dialog yêu cầu nhập lý do             |
| **Textarea lý do**        | Textarea     | Nhập lý do khóa tài khoản *             | **MỚI**: Bắt buộc nhập lý do                   |
| **Dialog mở khóa**        | Dialog       | Xác nhận mở khóa tài khoản              | **MỚI**: Dialog yêu cầu nhập lý do             |
| **Nút xác nhận**          | Button       | Xác nhận khóa/Mở khóa                   | Nút để xác nhận hành động                       |
| **Bảng audit log**       | Table        | Thời gian, hành động, người thực hiện... | **MỚI**: Hiển thị lịch sử thao tác nhạy cảm    |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Khóa tài khoản**       | Cho phép Admin khóa tài khoản nhân viên. Hệ thống sẽ yêu cầu nhập lý do khóa và ghi nhận vào audit log trước khi thực hiện.                                                                                                                | Tài khoản được khóa thành công. Audit log được ghi nhận với đầy đủ thông tin.             | Không thể khóa tài khoản. Lý do không được nhập. Audit log không được ghi nhận.            |
| **Mở khóa tài khoản**    | Cho phép Admin mở khóa tài khoản nhân viên. Hệ thống sẽ yêu cầu nhập lý do mở khóa và ghi nhận vào audit log trước khi thực hiện.                                                                                                          | Tài khoản được mở khóa thành công. Audit log được ghi nhận với đầy đủ thông tin.           | Không thể mở khóa tài khoản. Lý do không được nhập. Audit log không được ghi nhận.        |
| **Ghi nhận audit log**   | **MỚI**: Mỗi khi Admin thực hiện khóa/mở khóa tài khoản, hệ thống tự động ghi nhận vào audit log với thông tin: thời gian, hành động, người thực hiện (Admin), lý do, IP address, và chi tiết. Audit log được lưu vĩnh viễn và không thể xóa. | Audit log được ghi nhận thành công với đầy đủ thông tin.                                  | Không thể ghi nhận audit log. Thông tin audit log không đầy đủ.                            |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu Admin phải nhập lý do khóa/mở khóa tài khoản. Lý do phải có ít nhất 10 ký tự để đảm bảo tính minh bạch và trách nhiệm.                                                                                            | Lý do được validate thành công. Hành động được thực hiện.                                | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị thông báo lỗi.                      |

#### 1.2.4 Audit Log Schema (MỚI):

| Field              | Type     | Description                                    |
| ------------------ | -------- | ---------------------------------------------- |
| **ID**             | String   | Mã định danh duy nhất của log entry            |
| **Action**         | String   | Hành động (Khóa tài khoản, Mở khóa tài khoản)  |
| **Performed By**   | String   | Tên Admin thực hiện hành động                  |
| **Timestamp**      | DateTime | Thời gian thực hiện hành động                  |
| **Reason**         | String   | Lý do thực hiện hành động                      |
| **IP Address**     | String   | Địa chỉ IP của Admin khi thực hiện            |
| **Details**        | String   | Chi tiết bổ sung về hành động                 |
| **Employee ID**    | String   | Mã nhân viên bị ảnh hưởng                      |

---

### 1.3 XÓA TÀI KHOẢN - **ĐÃ SỬA**

#### 1.3.1 Thông tin màn hình:

| Screen        | Xóa tài khoản nhân viên                                                      |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Cho phép Admin xóa tài khoản nhân viên với lý do và ghi nhận audit log       |
| Screen Access | Admin click nút **Xóa tài khoản** từ trang chi tiết nhân viên                 |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Dialog xóa**        | Dialog       | Xác nhận xóa tài khoản                 | **MỚI**: Dialog yêu cầu nhập lý do             |
| **Textarea lý do**    | Textarea     | Nhập lý do xóa tài khoản *             | **MỚI**: Bắt buộc nhập lý do                   |
| **Cảnh báo**          | Alert        | Hành động này không thể hoàn tác       | Cảnh báo về tính không thể hoàn tác            |
| **Nút xác nhận**      | Button       | Xác nhận xóa                            | Nút để xác nhận xóa tài khoản                  |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xóa tài khoản**        | Cho phép Admin xóa tài khoản nhân viên. Hệ thống sẽ yêu cầu nhập lý do xóa và ghi nhận vào audit log trước khi thực hiện. Hành động này không thể hoàn tác.                                                                                | Tài khoản được xóa thành công. Audit log được ghi nhận với đầy đủ thông tin.             | Không thể xóa tài khoản. Lý do không được nhập. Audit log không được ghi nhận.            |
| **Ghi nhận audit log**   | **MỚI**: Mỗi khi Admin thực hiện xóa tài khoản, hệ thống tự động ghi nhận vào audit log với thông tin đầy đủ. Audit log được lưu vĩnh viễn ngay cả khi tài khoản đã bị xóa.                                                                 | Audit log được ghi nhận thành công với đầy đủ thông tin.                                  | Không thể ghi nhận audit log. Thông tin audit log không đầy đủ.                            |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu Admin phải nhập lý do xóa tài khoản. Lý do phải có ít nhất 20 ký tự để đảm bảo tính nghiêm trọng của hành động.                                                                                                   | Lý do được validate thành công. Hành động được thực hiện.                                | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị thông báo lỗi.                      |

---

### 1.4 XEM AUDIT LOG - **MỚI**

#### 1.4.1 Thông tin màn hình:

| Screen        | Audit Log - Lịch sử thao tác nhạy cảm                                                      |
| ------------- | ------------------------------------------------------------------------------------------ |
| Description   | Hiển thị lịch sử tất cả các thao tác nhạy cảm (khóa, mở khóa, xóa tài khoản) của Admin     |
| Screen Access | Hiển thị trong trang chi tiết nhân viên, tab **Audit Log**                                 |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Bảng audit log**    | Table        | Thời gian, Hành động, Người thực hiện, Lý do, IP, Chi tiết | Hiển thị lịch sử thao tác nhạy cảm            |
| **Badge hành động**   | Badge        | Khóa tài khoản, Mở khóa, Xóa tài khoản | Hiển thị loại hành động với màu sắc phù hợp    |
| **Bộ lọc**            | Filter       | Hành động, Thời gian, Người thực hiện   | Lọc audit log theo tiêu chí                    |

#### 1.4.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem audit log**        | Cho phép Admin xem lịch sử tất cả các thao tác nhạy cảm đã thực hiện trên tài khoản nhân viên. Audit log hiển thị đầy đủ thông tin để đảm bảo tính minh bạch và trách nhiệm.                                                                 | Audit log được hiển thị thành công với đầy đủ thông tin.                                  | Không thể tải audit log. Thông tin audit log không đầy đủ.                                |
| **Lọc audit log**       | Admin có thể lọc audit log theo hành động, thời gian, hoặc người thực hiện để tìm kiếm dễ dàng hơn.                                                                                                                                    | Audit log được lọc thành công theo tiêu chí đã chọn.                                      | Không thể lọc audit log. Kết quả lọc không chính xác.                                      |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Audit Log**: Thêm hệ thống ghi nhận audit log cho tất cả các thao tác nhạy cảm (khóa, mở khóa, xóa tài khoản)
2. **Validation lý do**: Yêu cầu Admin phải nhập lý do khi thực hiện các thao tác nhạy cảm
3. **Thông tin đầy đủ**: Audit log ghi nhận đầy đủ thông tin: thời gian, hành động, người thực hiện, lý do, IP address, chi tiết
4. **Lưu vĩnh viễn**: Audit log được lưu vĩnh viễn và không thể xóa để đảm bảo tính minh bạch
5. **UI cải thiện**: Thêm bảng audit log trong trang chi tiết nhân viên để Admin có thể xem lịch sử thao tác
6. **Bảo mật**: Ghi nhận IP address để theo dõi nguồn gốc của các thao tác nhạy cảm

