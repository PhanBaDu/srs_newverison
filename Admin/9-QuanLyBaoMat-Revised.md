# TỔNG HỢP CHỨC NĂNG (ĐÃ SỬA)

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý bảo mật của Admin (Đã sửa theo review)_

## MỤC LỤC

1. [Chức năng quản lý bảo mật](#1-chức-năng-quản-lý-bảo-mật)
   - 1.1 [Force logout all sessions](#11-force-logout-all-sessions) - **MỚI**
   - 1.2 [Quản lý sessions](#12-quản-lý-sessions) - **MỚI**
   - 1.3 [Force logout user](#13-force-logout-user) - **MỚI**

---

## 1. CHỨC NĂNG QUẢN LÝ BẢO MẬT

### 1.1 FORCE LOGOUT ALL SESSIONS - **MỚI**

#### 1.1.1 Thông tin màn hình:

| Screen        | Force logout tất cả sessions                                                      |
| ------------- | --------------------------------------------------------------------------------- |
| Description   | Cho phép Admin force logout tất cả sessions khi phát hiện security risk          |
| Screen Access | Admin chọn **Quản lý bảo mật** từ menu chính                                      |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                      | Type         | Data                                    | Description                                    |
| ------------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Card force logout**     | Card         | Force Logout Tất Cả Sessions            | **MỚI**: Card chứa nút force logout           |
| **Dialog xác nhận**       | Dialog       | Xác nhận force logout                    | **MỚI**: Dialog yêu cầu xác nhận               |
| **Textarea lý do**        | Textarea     | Nhập lý do force logout *                | **MỚI**: Bắt buộc nhập lý do                   |
| **Nút force logout**      | Button       | Force Logout Tất Cả Sessions             | **MỚI**: Nút để force logout tất cả sessions    |
| **Alert cảnh báo**        | Alert        | Cảnh báo về force logout                 | **MỚI**: Cảnh báo về tác động của force logout |

#### 1.1.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Force logout tất cả sessions** | Cho phép Admin force logout tất cả sessions trong hệ thống khi phát hiện security risk (đổi mật khẩu admin, suspicious activity, security breach). Hệ thống sẽ yêu cầu nhập lý do trước khi thực hiện.                                    | Tất cả sessions được force logout thành công. Tất cả users bị đăng xuất và cần đăng nhập lại. | Không thể force logout tất cả sessions. Một số sessions không được đóng.                  |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu Admin phải nhập lý do force logout (tối thiểu 20 ký tự) để đảm bảo tính minh bạch và trách nhiệm. Nếu không nhập hoặc quá ngắn, hệ thống sẽ từ chối.                                                              | Lý do được validate thành công. Force logout được thực hiện.                              | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị thông báo lỗi.                      |
| **Ghi nhận audit log**   | **MỚI**: Mỗi khi Admin force logout tất cả sessions, hệ thống tự động ghi nhận vào audit log với thông tin: thời gian, Admin thực hiện, lý do, số lượng sessions bị đóng.                                                                  | Audit log được ghi nhận thành công với đầy đủ thông tin.                                  | Không thể ghi nhận audit log. Thông tin audit log không đầy đủ.                            |
| **Notification to users** | **MỚI**: Sau khi force logout tất cả sessions, hệ thống tự động gửi thông báo đến tất cả users về việc bị đăng xuất và lý do (nếu cần).                                                                                                    | Tất cả users được thông báo về việc force logout.                                          | Không thể thông báo cho users. Một số users không nhận được thông báo.                       |

#### 1.1.4 Force Logout Rules (MỚI):

| Rule Type           | Description                                                                 | Action                                    |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **Security Risk Detection** | Phát hiện security risk (đổi mật khẩu admin, suspicious activity, security breach) | Tự động đề xuất force logout hoặc Admin thực hiện thủ công |
| **Validation**      | Yêu cầu nhập lý do force logout (tối thiểu 20 ký tự)                        | Từ chối nếu không có lý do                |
| **Audit Log**       | Ghi nhận audit log với đầy đủ thông tin                                     | Đảm bảo tính minh bạch                    |
| **User Notification** | Thông báo cho tất cả users về việc force logout                            | Đảm bảo users biết lý do                  |

---

### 1.2 QUẢN LÝ SESSIONS - **MỚI**

#### 1.2.1 Thông tin màn hình:

| Screen        | Quản lý sessions                                                      |
| ------------- | --------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả sessions đang hoạt động trong hệ thống      |
| Screen Access | Hiển thị trong trang quản lý bảo mật, phần danh sách sessions        |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Danh sách sessions** | Table        | User, Thiết bị, IP Address, Vị trí, Hoạt động cuối, Trạng thái | Hiển thị các sessions đang hoạt động           |
| **Badge trạng thái**  | Badge        | Đang hoạt động, Đã đóng                 | Hiển thị trạng thái session                    |
| **Bộ lọc**            | Select       | Tất cả users, User cụ thể                | Lọc sessions theo user                         |
| **Stats cards**       | Card Group   | Tổng sessions, Đang hoạt động, Đã đóng, Users online | Hiển thị thống kê sessions                     |

#### 1.2.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Xem danh sách sessions** | Hiển thị danh sách tất cả sessions đang hoạt động trong hệ thống với thông tin chi tiết về user, thiết bị, IP address, vị trí, và hoạt động cuối.                                                                                        | Danh sách sessions được hiển thị thành công với đầy đủ thông tin.                         | Không thể tải danh sách sessions. Thông tin sessions không chính xác.                      |

---

### 1.3 FORCE LOGOUT USER - **MỚI**

#### 1.3.1 Thông tin màn hình:

| Screen        | Force logout user                                                      |
| ------------- | ---------------------------------------------------------------------- |
| Description   | Cho phép Admin force logout tất cả sessions của một user cụ thể        |
| Screen Access | Hiển thị trong danh sách sessions, nút force logout trên mỗi session   |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                  | Type         | Data                                    | Description                                    |
| --------------------- | ------------ | --------------------------------------- | ---------------------------------------------- |
| **Nút force logout**  | Button       | Force Logout                            | **MỚI**: Nút để force logout user              |
| **Dialog xác nhận**   | Dialog       | Xác nhận force logout user              | **MỚI**: Dialog yêu cầu xác nhận               |
| **Textarea lý do**    | Textarea     | Nhập lý do force logout *               | **MỚI**: Bắt buộc nhập lý do                   |

#### 1.3.3 Hành động và xử lý:

| Action Name              | Description                                                                                                                                                                                                                                 | Success                                                                                    | Failure                                                                                    |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| **Force logout user**    | Cho phép Admin force logout tất cả sessions của một user cụ thể khi phát hiện security risk (suspicious activity, account compromise). Hệ thống sẽ yêu cầu nhập lý do trước khi thực hiện.                                                    | Tất cả sessions của user được force logout thành công. User bị đăng xuất và cần đăng nhập lại. | Không thể force logout sessions của user. Một số sessions không được đóng.                |
| **Validation lý do**     | **MỚI**: Hệ thống yêu cầu Admin phải nhập lý do force logout user (tối thiểu 10 ký tự). Nếu không nhập hoặc quá ngắn, hệ thống sẽ từ chối.                                                                                                  | Lý do được validate thành công. Force logout được thực hiện.                            | Lý do không hợp lệ (quá ngắn hoặc không có). Hiển thị thông báo lỗi.                      |
| **Ghi nhận audit log**   | **MỚI**: Mỗi khi Admin force logout user, hệ thống tự động ghi nhận vào audit log với thông tin: thời gian, Admin thực hiện, user bị force logout, lý do, số lượng sessions bị đóng.                                                       | Audit log được ghi nhận thành công với đầy đủ thông tin.                                  | Không thể ghi nhận audit log. Thông tin audit log không đầy đủ.                             |

---

## THAY ĐỔI CHÍNH SO VỚI BẢN GỐC

1. **Force logout all sessions**: Thêm tính năng force logout tất cả sessions khi phát hiện security risk
2. **Force logout user**: Thêm tính năng force logout tất cả sessions của một user cụ thể
3. **Session management**: Hiển thị danh sách tất cả sessions đang hoạt động với thông tin chi tiết
4. **Validation lý do**: Yêu cầu nhập lý do force logout để đảm bảo tính minh bạch
5. **Audit log**: Ghi nhận audit log cho tất cả các hành động force logout
6. **User notification**: Tự động thông báo cho users về việc force logout
7. **UI cải thiện**: Thêm dialog xác nhận, textarea lý do, và stats cards cho sessions

