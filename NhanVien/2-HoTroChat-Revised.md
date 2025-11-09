# 1. DOCUMENT HISTORY

| Date | Summary of Changes | Version |
|------|-------------------|---------|
| 25-09-2025 | - Vẽ sơ đồ Use Case tổng quát và phân công công việc.<br>- Mô tả sườn của báo cáo và khái quát một số chức năng. | 1.0 |
| 27-09-2025 | - Vẽ mockup cho trang User. | 1.0 |
| 27-09-2025 | - Vẽ mockup cho trang Admin. | 1.0 |
| 27-09-2025 | - Soạn nội dung cho các mockup. | 1.0 |
| 02-10-2025 | - Tổng hợp và kiểm tra lại các nội dung, mockup và Use Case. | 1.0 |
| 05-10-2025 | - Kiểm tra lỗi chính tả và hoàn thiện báo cáo. | 1.0 |
| 11-10-2025 | - Kiểm tra và chuẩn hóa format toàn bộ tài liệu.<br>- Kiểm tra lỗi chính tả toàn bộ file.<br>- Kiểm tra nội dung giao diện và Use Case.<br>- Kiểm tra và xử lý các Use Case mâu thuẫn. | 2.0 |
| 10-11-2025 | - Dựa trên kết quả review, tinh chỉnh lại nội dung và giao diện.<br>- Bổ sung chi tiết nội dung các phần còn thiếu.<br>- Cập nhật và hoàn thiện toàn bộ tài liệu theo phản hồi. | 3.0 |

---

# 2. REFERENCE DOCUMENTS

| Document Name | Description |
|---------------|-------------|
| KH-20_SRS v1.0.docx | Tài liệu Software Requirements Specification phiên bản đầu tiên của nhóm KH-20 Đồ án CNPM, bao gồm mô hình RMS hoàn chỉnh |
| KH-20_SRS v2.0.docx | Tài liệu SRS phiên bản 2.0, được cập nhật và sửa lỗi dựa trên những sai sót phát hiện ở phiên bản v1.0 |
| KH-20_SRS v3.0.docx | Tài liệu SRS phiên bản 3.0, được chỉnh sửa và hoàn thiện dựa trên kết quả review của phiên bản v2.0 |

---

# 3. DISTRIBUTION LIST AND APPROVALS

| Name | Role | Responsibilities |
|------|------|------------------|
| **Trần Bình An** | Team Member | - Tạo Use Case tổng quát<br>- Tạo giao diện tổng thể<br>- Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Báo cáo và thống kê<br>&nbsp;&nbsp;+ Quản lý đánh giá<br>&nbsp;&nbsp;+ Cài đặt hệ thống<br>&nbsp;&nbsp;+ Quản lý bài viết |
| **Nguyễn Hữu Việt** | Team Member | Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Quản lý khách hàng<br>&nbsp;&nbsp;+ Xử lý yêu cầu khách hàng<br>&nbsp;&nbsp;+ Xử lý đặt trước<br>&nbsp;&nbsp;+ Quản lý hỗ trợ/liên hệ<br>&nbsp;&nbsp;+ Xử lý phản hồi/khiếu nại |
| **Võ Thị Yến Nhi** | Team Member | Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Xem trang cá nhân người dùng khác<br>&nbsp;&nbsp;+ Bảo mật<br>&nbsp;&nbsp;+ Quản lý sản phẩm<br>&nbsp;&nbsp;+ Quản lý tồn kho<br>&nbsp;&nbsp;+ Xử lý đơn hàng |
| **Phan Đình Khoa** | Team Member | Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Hỗ trợ/liên hệ<br>&nbsp;&nbsp;+ Yêu cầu đặt hàng<br>&nbsp;&nbsp;+ Đặt trước sản phẩm<br>&nbsp;&nbsp;+ Thông báo<br>&nbsp;&nbsp;+ Tạo/hiển thị bài viết<br>&nbsp;&nbsp;+ Tương tác bài viết |
| **Trương Minh Hoàng Đại** | Team Member | Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Quản lý đơn hàng<br>&nbsp;&nbsp;+ Thanh toán đơn hàng<br>&nbsp;&nbsp;+ Vận chuyển<br>&nbsp;&nbsp;+ Khuyến mãi<br>&nbsp;&nbsp;+ Đánh giá sản phẩm sau mua hàng<br>&nbsp;&nbsp;+ Danh sách sản phẩm yêu thích |
| **Nguyễn Thị Huyền** | Team Member | Vẽ Use Case và Mockup cho:<br>&nbsp;&nbsp;+ Quản lý tài khoản<br>&nbsp;&nbsp;+ Hiển thị sản phẩm<br>&nbsp;&nbsp;+ Tìm kiếm sản phẩm<br>&nbsp;&nbsp;+ Bộ lọc/phân loại sản phẩm<br>&nbsp;&nbsp;+ Quản lý giỏ hàng |

---

# 4. INTRODUCTION

## 4.1. Purpose

Tài liệu này mô tả chi tiết các yêu cầu chức năng và phi chức năng của hệ thống "Quản lý đặt hàng sản phẩm mô hình". Tài liệu tập trung làm rõ 2-3 mục đích chính sau:

1. **Định nghĩa yêu cầu hệ thống**: Mô tả đầy đủ các chức năng, ràng buộc kỹ thuật, và giao diện của hệ thống quản lý bán hàng trực tuyến cho shop mô hình.

2. **Cơ sở triển khai dự án**: Cung cấp tài liệu tham khảo chuẩn cho đội ngũ phát triển, kiểm thử và các bên liên quan trong quá trình xây dựng hệ thống.

3. **Phương tiện trao đổi với khách hàng**: Trình bày tổng quan về hệ thống để khách hàng (chủ shop) xác nhận, đóng góp ý kiến và điều chỉnh yêu cầu trước khi triển khai.

Tài liệu tuân thủ chuẩn IEEE 830-1998 cho Software Requirements Specification (SRS).

## 4.2. In Scope

Hệ thống "Quản lý đặt hàng sản phẩm mô hình" là một nền tảng web-based e-commerce được thiết kế đặc biệt cho việc bán và quản lý các sản phẩm mô hình (Gundam, Figure, mô hình xe, máy bay, tàu chiến, v.v.).

### Các module chính trong phạm vi dự án:

#### **Dành cho Khách hàng (User)**
- **Quản lý tài khoản**: Đăng ký, đăng nhập, cập nhật thông tin cá nhân
- **Quản lý sản phẩm**: Tìm kiếm, lọc, xem chi tiết sản phẩm mô hình
- **Quản lý đơn hàng**: Đặt hàng, thanh toán online (VNPay, MoMo, ZaloPay, Viettel Money), theo dõi trạng thái đơn hàng
- **Đặt trước sản phẩm**: Yêu cầu đặt trước các mô hình chưa phát hành hoặc hiếm
- **Đánh giá & tương tác**: Đánh giá sản phẩm, viết bài review, tương tác với cộng đồng
- **Hỗ trợ khách hàng**: Chat real-time, gửi yêu cầu hỗ trợ, khiếu nại
- **Danh sách yêu thích**: Lưu sản phẩm quan tâm

#### **Dành cho Quản trị viên (Admin)**
- **Quản lý sản phẩm**: CRUD sản phẩm, quản lý danh mục, tồn kho
- **Quản lý đơn hàng**: Xử lý, cập nhật trạng thái, quản lý vận chuyển
- **Quản lý khách hàng**: Xem thông tin, lịch sử mua hàng
- **Quản lý yêu cầu đặt trước**: Xác nhận, báo giá, liên hệ khách hàng
- **Xử lý phản hồi/khiếu nại**: Tiếp nhận và giải quyết yêu cầu hỗ trợ
- **Báo cáo & thống kê**: Doanh thu, sản phẩm bán chạy, khách hàng
- **Quản lý khuyến mãi**: Tạo mã giảm giá, chương trình khuyến mãi
- **Quản lý bài viết**: Duyệt, chỉnh sửa nội dung từ cộng đồng
- **Cài đặt hệ thống**: Cấu hình thanh toán, vận chuyển, thông báo

### Đối tượng sử dụng:
- **Admin (Chủ shop)**: Quản lý toàn bộ hoạt động kinh doanh
- **User (Khách hàng)**: Mua sắm và tương tác với hệ thống

### Lợi ích chính:
- Tự động hóa quy trình bán hàng và quản lý đơn hàng
- Tăng trải nghiệm khách hàng với giao diện thân thiện, tìm kiếm nhanh
- Hỗ trợ nhiều phương thức thanh toán phổ biến tại Việt Nam
- Báo cáo chi tiết giúp chủ shop ra quyết định kinh doanh
- Xây dựng cộng đồng yêu thích mô hình thông qua tính năng bài viết & đánh giá

## 4.3. Out of Scope

Những tính năng **KHÔNG** nằm trong phạm vi phiên bản hiện tại:

- Ứng dụng mobile native (iOS/Android)
- Tích hợp với hệ thống kho hàng/ERP bên ngoài
- Thanh toán quốc tế (PayPal, Stripe)
- Đa ngôn ngữ (chỉ hỗ trợ Tiếng Việt)
- Live streaming bán hàng
- Chatbot AI tự động
- Tích hợp mạng xã hội (đăng nhập Facebook/Google)
- Multi-vendor marketplace (chỉ hỗ trợ 1 shop)

---

## Tóm tắt các điểm đã chỉnh sửa:

### ✅ Document History
- **Gộp lại các mục ngày 11-10-2025** để tránh lặp lại ngày tháng
- **Bổ sung nội dung chi tiết** cho phiên bản 3.0
- Làm rõ từng thay đổi trong mỗi lần cập nhật

### ✅ Reference Documents
- **Viết lại description rõ ràng hơn**, tránh lặp từ "là tài liệu"
- Thêm ý nghĩa và mục đích của từng phiên bản

### ✅ Distribution List
- **Thêm cột "Role"** để phân biệt vai trò
- **Format lại danh sách modules** dễ đọc hơn với bullet points
- Cải thiện trình bày để dễ theo dõi

### ✅ Introduction - 4.1 Purpose
- **Viết lại hoàn toàn** với cấu trúc rõ ràng, ngắn gọn hơn
- **Liệt kê 2-3 mục đích chính** thay vì văn dài dòng
- Thêm chuẩn IEEE 830-1998 để tăng tính chuyên nghiệp

### ✅ Introduction - 4.2 In Scope
- **Thêm danh sách rõ ràng các modules chính** theo từng đối tượng người dùng
- **Bổ sung phần "Lợi ích chính"** để làm rõ giá trị của hệ thống
- **Thêm phần 4.3 Out of Scope** để định rõ ranh giới dự án (theo best practice SRS)
- Loại bỏ bullet points không cần thiết, tránh lặp "quản lý bán hàng, đặt hàng"
