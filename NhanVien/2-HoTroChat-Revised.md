# Non-Functional Requirements

## 1. Performance (Hiệu năng)

| No. | Requirement |
|-----|-------------|
| 1 | Hệ thống phải hỗ trợ tối thiểu **2000 người dùng truy cập đồng thời** (peak load) với tối thiểu **500 đơn hàng/giờ** mà không ảnh hưởng đến hiệu suất |
| 2 | Thời gian phản hồi API trung bình phải dưới 200ms cho các thao tác đơn giản (xem sản phẩm, giỏ hàng) và dưới 500ms cho các thao tác phức tạp (tìm kiếm, lọc) |
| 3 | Thời gian tải trang không vượt quá 3 giây với kết nối internet tốc độ trung bình |
| 4 | Thời gian xử lý thanh toán và đặt hàng không vượt quá 5 giây |
| 5 | Real-time chat hỗ trợ khách hàng có độ trễ tối đa 1 giây (sử dụng Socket.IO) |
| 6 | **Hỗ trợ batch jobs và report lớn**: Export dữ liệu (đơn hàng, sản phẩm, khách hàng) tối đa 10,000 bản ghi hoàn thành trong vòng 10 phút |
| 7 | **Monitoring & Load Testing**: Thực hiện load testing định kỳ với các case: normal load (1000 users), peak load (2000 users), stress test (3000+ users) để đảm bảo hệ thống ổn định |

## 2. Scalability (Khả năng mở rộng)

| No. | Requirement |
|-----|-------------|
| 1 | Database PostgreSQL phải có khả năng lưu trữ tối thiểu 10,000 sản phẩm và 50,000 người dùng |
| 2 | Hệ thống phải xử lý được ít nhất 1,000 đơn hàng mỗi ngày |
| 3 | Cho phép nhiều admin đồng thời quản lý đơn hàng, cập nhật sản phẩm mà không xung đột dữ liệu |
| 4 | Hỗ trợ upload và lưu trữ tối thiểu 50,000 hình ảnh sản phẩm và 20,000 ảnh/video từ bài viết người dùng |
| 5 | **Kiến trúc hệ thống phải hỗ trợ multi-region/cross-datacenter deployment và CDN cho ảnh/video** để tối ưu tốc độ truy cập toàn quốc |
| 6 | Horizontal scaling: Có khả năng tăng số lượng server instances khi lưu lượng tăng cao |

## 3. Security (Bảo mật)

| No. | Requirement |
|-----|-------------|
| 1 | Backend sử dụng Node.js phiên bản 20.0 trở lên để đảm bảo các bản vá bảo mật mới nhất |
| 2 | Xác thực người dùng bắt buộc sử dụng JWT (JSON Web Token) với thời gian hết hạn 24 giờ |
| 3 | Mật khẩu người dùng phải được mã hóa bằng Bcrypt với salt rounds tối thiểu là 10 |
| 4 | Phân quyền rõ ràng giữa User và Admin - mỗi vai trò chỉ truy cập được các chức năng được phép |
| 5 | **Tuân thủ compliance GDPR/PDPA**: Lưu trữ log truy cập, xóa dữ liệu theo yêu cầu người dùng/khách hàng, có cơ chế consent management |
| 6 | **Logging & Audit Trail**: Ghi lại tất cả thao tác quan trọng (đăng nhập, thay đổi quyền, xóa dữ liệu, giao dịch thanh toán) trong hệ thống với đầy đủ thông tin user, timestamp, action |
| 7 | Tích hợp các cổng thanh toán (VNPay, MoMo, ZaloPay, Viettel Money) phải tuân thủ chuẩn bảo mật PCI DSS |
| 8 | Dữ liệu hệ thống được sao lưu tự động hàng ngày và lưu trữ tại server backup riêng biệt |
| 9 | Tất cả API endpoints phải được bảo vệ bởi middleware xác thực (Passport.js) |
| 10 | Sử dụng HTTPS/SSL cho mọi kết nối giữa client và server |
| 11 | Implement CORS policy để chỉ cho phép các domain được phê duyệt truy cập API |
| 12 | Chống tấn công XSS, SQL Injection, CSRF thông qua validation (Zod) và sanitization dữ liệu đầu vào |

## 4. Reliability (Độ tin cậy)

| No. | Requirement |
|-----|-------------|
| 1 | Uptime hệ thống đạt tối thiểu 99.5% trong tháng (cho phép downtime không quá 3.6 giờ/tháng) |
| 2 | **Recovery Plan**: Thời gian phục hồi hệ thống (RTO - Recovery Time Objective) không quá 4 giờ, điểm phục hồi dữ liệu (RPO - Recovery Point Objective) không quá 1 giờ |
| 3 | Cơ chế retry tự động cho các giao dịch thanh toán thất bại |
| 4 | Health check endpoints để monitor trạng thái hệ thống real-time |

## 5. Availability (Tính sẵn sàng)

| No. | Requirement |
|-----|-------------|
| 1 | **Planned Maintenance**: Hệ thống chỉ được bảo trì trong khung giờ 2-4h sáng, thông báo trước ít nhất 24 giờ |
| 2 | **Hotfix deployment**: Hỗ trợ triển khai bản vá khẩn cấp mà không cần restart toàn bộ hệ thống (zero-downtime deployment hoặc downtime < 10 phút) |
| 3 | **Monitoring & Alerting**: Cảnh báo tự động khi uptime giảm dưới 99%, response time vượt ngưỡng, hoặc có lỗi nghiêm trọng |

## 6. Maintainability (Khả năng bảo trì)

| No. | Requirement |
|-----|-------------|
| 1 | **Upgrade Strategy**: Hệ thống cho phép nâng cấp Node.js, PostgreSQL, dependencies mà không cần downtime quá 10 phút |
| 2 | Code phải tuân thủ coding standards, có documentation đầy đủ |
| 3 | Sử dụng version control (Git) với branching strategy rõ ràng (GitFlow/trunk-based) |

## 7. Usability (Khả năng sử dụng)

| No. | Requirement |
|-----|-------------|
| 1 | **Accessibility**: Giao diện phải tuân thủ WCAG 2.1 Level AA - hỗ trợ người khuyết tật (screen reader, keyboard navigation, sufficient color contrast) |
| 2 | Tab order logic và phím tắt cho các thao tác thường xuyên |
| 3 | Error messages rõ ràng, hướng dẫn người dùng khắc phục |
| 4 | Loading states và feedback cho mọi action |

## 8. Browser (Trình duyệt)

| No. | Requirement |
|-----|-------------|
| 1 | Hỗ trợ các trình duyệt hiện đại: **Chrome, Firefox (3 phiên bản gần nhất)** |
| 2 | Hỗ trợ Microsoft Edge (phiên bản dựa trên Chromium) |
| 3 | Hỗ trợ Safari 14 trở lên (cho người dùng macOS và iOS) |
| 4 | Responsive design tương thích với các thiết bị mobile (iOS, Android) |
| 5 | Không hỗ trợ Internet Explorer (đã ngừng hỗ trợ từ Microsoft) |
| 6 | **Testing Coverage**: Có test matrix tự động trên các thiết bị/trình duyệt chính (automated cross-browser testing) |

## 9. Interfaces (Giao diện)

| No. | Requirement |
|-----|-------------|
| 1 | **API Documentation**: Tất cả REST API endpoints phải có OpenAPI/Swagger documentation đầy đủ |
| 2 | Sử dụng Framework Next.js để tạo giao diện người dùng |
| 3 | Styling sử dụng Tailwind CSS kết hợp shadcn/ui components |
| 4 | Hỗ trợ đa ngôn ngữ thông qua next-intl |
| 5 | Responsive design tương thích mọi kích thước màn hình |

## 10. Compliance (Tuân thủ)

| No. | Requirement |
|-----|-------------|
| 1 | **Audit & Compliance Check**: Kiểm toán bảo mật/kiểm toán nghiệp vụ định kỳ **ít nhất 1 lần/năm** |
| 2 | Tuân thủ luật bảo vệ dữ liệu cá nhân Việt Nam (Nghị định 13/2023/NĐ-CP) |
| 3 | Compliance với các quy định về thương mại điện tử |

## 11. Assumptions (Các giả định)

| No. | Requirement |
|-----|-------------|
| 1 | Có thể tạm ngưng hệ thống nếu cần phải nâng cấp (thời gian bảo trì: 2-4h sáng, thông báo trước 24h) |
| 2 | Người dùng có kết nối internet ổn định tối thiểu 5 Mbps |
| 3 | Admin được đào tạo cơ bản trước khi vận hành hệ thống |
| 4 | Môi trường dev, staging, production được tách biệt hoàn toàn |

---

## Tóm tắt các thay đổi chính:

### ✅ Performance
- Tăng concurrent users từ 1000 → 2000 (peak load)
- Thêm yêu cầu 500 đơn hàng/giờ
- Bổ sung batch jobs/export report (10,000 bản ghi < 10 phút)
- Thêm load testing định kỳ

### ✅ Scalability
- Bổ sung multi-region/CDN deployment
- Rõ ràng hóa horizontal scaling

### ✅ Security
- Thêm GDPR/PDPA compliance
- Bổ sung Logging & Audit Trail chi tiết

### ✅ Reliability
- Định nghĩa rõ RTO (4h) và RPO (1h)
- Thêm health check endpoints

### ✅ Availability (Mới)
- Planned maintenance windows
- Hotfix deployment strategy < 10 phút downtime
- Monitoring & alerting tự động

### ✅ Maintainability (Mới)
- Upgrade strategy với downtime < 10 phút
- Coding standards và documentation

### ✅ Usability
- Bổ sung WCAG 2.1 Level AA compliance
- Tab order và keyboard navigation

### ✅ Browser
- Thêm automated cross-browser testing

### ✅ Interfaces
- Bổ sung OpenAPI/Swagger documentation

### ✅ Compliance (Mới)
- Kiểm toán định kỳ 1 lần/năm
- Tuân thủ luật Việt Nam
