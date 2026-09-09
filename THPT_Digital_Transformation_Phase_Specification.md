# SCHOOL DIGITAL TRANSFORMATION PLATFORM
## Specification triển khai theo Phase – THPT

**Phiên bản:** 0.1  
**Ngày:** 09/09/2026  
**Phạm vi ban đầu:** Trường Trung học Phổ thông (THPT)  
**Định hướng sản phẩm:** Core chuẩn hóa + Module hóa + Configuration + Integration + Customization

---

# 1. Mục tiêu tài liệu

Tài liệu này mô tả specification ở mức sản phẩm và hệ thống cho các phase triển khai nền tảng chuyển đổi số trường học dành cho THPT.

Mục tiêu:

- Xây dựng một hệ thống lõi có thể triển khai cho nhiều trường THPT.
- Không phụ thuộc vào yêu cầu riêng của một khách hàng cụ thể.
- Cho phép cấu hình theo từng trường mà không phải sửa mã nguồn lõi.
- Tạo nền tảng để mở rộng dần thành hệ sinh thái quản trị, vận hành và học tập số.
- Giảm rủi ro phải thiết kế lại hệ thống khi có khách hàng thực tế.
- Làm tài liệu đầu vào cho Product Owner, BA, UI/UX, Backend, Frontend, Mobile, Tester và DevOps.

---

# 2. Nguyên tắc thiết kế sản phẩm

## 2.1. Product Core

Các nghiệp vụ phổ biến ở hầu hết trường THPT được đưa vào Core Product:

- Cơ cấu trường học.
- Năm học và học kỳ.
- Giáo viên.
- Học sinh.
- Phụ huynh.
- Khối/lớp.
- Môn học.
- Phân công giảng dạy.
- Thời khóa biểu.
- Điểm danh.
- Kết quả học tập.
- Thông báo.
- Phân quyền.
- Nhật ký hệ thống.

## 2.2. Configuration First

Các nội dung có khả năng khác nhau giữa các trường phải ưu tiên cấu hình thay vì hard-code.

Ví dụ:

- Số học kỳ.
- Loại điểm.
- Quy tắc nhập điểm.
- Quyền sửa điểm.
- Cơ cấu tổ chuyên môn.
- Loại đơn từ.
- Workflow phê duyệt.
- Loại thông báo.
- Module được bật/tắt.
- Mẫu biểu.
- Quy tắc notification.

## 2.3. Modular Monolith

Kiến trúc giai đoạn đầu:

```text
school-platform
│
├── identity
├── tenant
├── organization
├── academic
├── student
├── teacher
├── parent
├── timetable
├── attendance
├── grading
├── workflow
├── notification
├── reporting
├── file-management
├── audit
└── integration
```

Không triển khai microservice trong giai đoạn MVP trừ khi có lý do kỹ thuật bắt buộc.

## 2.4. Multi-Tenant Ready

Mỗi trường được coi là một tenant.

Mọi dữ liệu nghiệp vụ chính phải gắn với:

```text
tenant_id
```

Mục tiêu:

- Một hệ thống có thể phục vụ nhiều trường.
- Dữ liệu giữa các trường được cách ly.
- Cấu hình có thể khác nhau theo tenant.
- Có khả năng mở rộng lên mô hình quản lý nhiều trường.

## 2.5. API First

Các chức năng quan trọng cần có API rõ ràng để:

- Web Admin sử dụng.
- Teacher Portal sử dụng.
- Student App sử dụng.
- Parent App sử dụng.
- Kết nối với hệ thống bên ngoài.

## 2.6. Audit by Default

Mọi hành động nhạy cảm phải ghi nhật ký:

- Người thực hiện.
- Thời điểm.
- Chức năng.
- Đối tượng dữ liệu.
- Giá trị trước.
- Giá trị sau.
- Tenant.
- Thiết bị/IP nếu cần.

---

# 3. Đối tượng người dùng

## 3.1. System Administrator

Quản trị toàn nền tảng.

## 3.2. School Administrator

Quản trị một trường.

## 3.3. Ban Giám hiệu

Theo dõi hoạt động toàn trường, dashboard và báo cáo.

## 3.4. Tổ trưởng chuyên môn

Theo dõi giáo viên và hoạt động thuộc tổ chuyên môn.

## 3.5. Giáo viên chủ nhiệm

Quản lý lớp chủ nhiệm.

## 3.6. Giáo viên bộ môn

Quản lý hoạt động giảng dạy theo môn/lớp được phân công.

## 3.7. Học sinh

Xem thông tin học tập và tương tác với nhà trường.

## 3.8. Phụ huynh

Theo dõi học sinh và nhận thông tin từ nhà trường.

## 3.9. Nhân viên nghiệp vụ

Ví dụ:

- Giáo vụ.
- Văn thư.
- Kế toán.
- Thư viện.
- Thiết bị.
- Tuyển sinh.

Các vai trò này được mở rộng ở các phase sau.

---

# 4. Tổng quan Roadmap

| Phase | Tên | Mục tiêu chính |
|---|---|---|
| Phase 0 | Platform Foundation | Xây nền tảng kỹ thuật và mô hình dữ liệu lõi |
| Phase 1 | School Core MVP | Vận hành được chu trình học tập cơ bản |
| Phase 2 | School Operations | Số hóa quy trình hành chính và phối hợp nhà trường |
| Phase 3 | Digital School Platform | Mở rộng thành hệ sinh thái vận hành trường học |
| Phase 4 | AI School | Bổ sung AI hỗ trợ quản trị, giáo viên, học sinh và phụ huynh |

---

# 5. PHASE 0 – PLATFORM FOUNDATION

## 5.1. Mục tiêu

Xây dựng nền móng hệ thống trước khi phát triển nghiệp vụ trường học.

Phase này chưa cần có đầy đủ tính năng end-user nhưng phải đảm bảo kiến trúc đủ tốt để hỗ trợ các phase tiếp theo.

## 5.2. Phạm vi chức năng

### 5.2.1. Tenant Management

Chức năng:

- Tạo tenant.
- Cập nhật thông tin trường.
- Kích hoạt/vô hiệu hóa tenant.
- Cấu hình tenant.
- Quản lý logo, tên trường, mã trường.
- Cấu hình timezone.
- Cấu hình ngôn ngữ.
- Cấu hình module bật/tắt.

Dữ liệu chính:

```text
Tenant
- id
- code
- name
- status
- logo
- timezone
- language
- settings
```

### 5.2.2. Identity & Authentication

Chức năng:

- Đăng nhập.
- Đăng xuất.
- Đổi mật khẩu.
- Quên mật khẩu.
- Reset mật khẩu.
- Khóa tài khoản.
- Kích hoạt tài khoản.
- Quản lý session.
- Chuẩn bị khả năng tích hợp SSO.

### 5.2.3. RBAC – Role Based Access Control

Các khái niệm:

```text
User
Role
Permission
RolePermission
UserRole
Scope
```

Scope dự kiến:

- Toàn trường.
- Theo tổ chuyên môn.
- Theo khối.
- Theo lớp.
- Theo môn học.
- Theo học sinh.

### 5.2.4. Audit Log

Ghi nhận:

- Login.
- Logout.
- Tạo dữ liệu.
- Sửa dữ liệu.
- Xóa dữ liệu.
- Import dữ liệu.
- Export dữ liệu.
- Thay đổi quyền.
- Thay đổi điểm.
- Thay đổi dữ liệu học sinh.

### 5.2.5. File Management

Hỗ trợ:

- Upload file.
- Download file.
- Metadata.
- Phân quyền file.
- File public/private.
- Attachment cho các module.
- Chuẩn bị lưu trữ object storage.

### 5.2.6. Notification Framework

Chuẩn hóa các kênh:

```text
In-App
Email
Push Notification
SMS / OTT Adapter
```

MVP Phase 0 chỉ cần thiết kế framework và In-App Notification.

### 5.2.7. Configuration Framework

Hỗ trợ:

- Cấu hình theo tenant.
- Cấu hình theo module.
- Cấu hình theo năm học.
- Version cấu hình.
- Giá trị mặc định.

### 5.2.8. Integration Framework

Chuẩn bị:

- REST API.
- Webhook.
- API key.
- Import Excel.
- Export Excel.
- Mapping dữ liệu.
- Integration log.

## 5.3. Yêu cầu phi chức năng

- API có version.
- Có chuẩn error response.
- Có logging.
- Có request correlation ID.
- Có validation thống nhất.
- Có tenant isolation.
- Có migration database.
- Có CI/CD cơ bản.
- Có DEV/UAT/PROD environment.
- Có health check.
- Có backup database.
- Có monitoring cơ bản.

## 5.4. Exit Criteria

Phase 0 hoàn thành khi:

- Có thể tạo ít nhất 2 tenant độc lập.
- User tenant A không thể truy cập tenant B.
- RBAC hoạt động.
- Audit ghi nhận đúng các hành động chính.
- Có API authentication.
- Có module configuration.
- Có import/export framework.
- Có pipeline deploy UAT.

---

# 6. PHASE 1 – SCHOOL CORE MVP

## 6.1. Mục tiêu

Một trường THPT có thể:

1. Khởi tạo năm học.
2. Tạo cơ cấu lớp.
3. Quản lý học sinh.
4. Quản lý giáo viên.
5. Phân công giảng dạy.
6. Tạo thời khóa biểu.
7. Điểm danh.
8. Nhập điểm.
9. Học sinh/phụ huynh xem thông tin.
10. Nhà trường gửi thông báo.

Đây là phase cần đủ khả năng demo và pilot.

---

## 6.2. Module Organization

### Chức năng

- Quản lý trường.
- Quản lý tổ chuyên môn.
- Quản lý khối.
- Quản lý lớp.
- Quản lý phòng học.
- Cấu hình cơ cấu tổ chức.

### Dữ liệu

```text
Department
Grade
Class
Room
```

---

## 6.3. Module Academic Year

### Chức năng

- Tạo năm học.
- Mở/đóng năm học.
- Tạo học kỳ.
- Cấu hình ngày bắt đầu/kết thúc.
- Thiết lập năm học hiện tại.

### Dữ liệu

```text
AcademicYear
Term
AcademicCalendar
```

### Quy tắc

- Không hard-code chính xác 2 học kỳ.
- Cho phép tenant cấu hình số kỳ.
- Một thời điểm chỉ có một năm học mặc định.

---

## 6.4. Module Student

### Chức năng

- Tạo học sinh.
- Sửa hồ sơ.
- Xem hồ sơ.
- Import Excel.
- Export Excel.
- Gán học sinh vào lớp.
- Chuyển lớp.
- Tạm nghỉ.
- Thôi học.
- Tốt nghiệp.
- Lưu lịch sử học tập.

### Thông tin cơ bản

```text
Student
- student_code
- full_name
- gender
- date_of_birth
- status
- email
- phone
- address
- admission_date
```

### Lịch sử

```text
StudentClassHistory
StudentStatusHistory
```

---

## 6.5. Module Parent

### Chức năng

- Quản lý phụ huynh/người giám hộ.
- Liên kết phụ huynh – học sinh.
- Một phụ huynh có thể có nhiều học sinh.
- Một học sinh có thể có nhiều người giám hộ.
- Xác định người liên hệ chính.
- Tạo tài khoản phụ huynh.

### Dữ liệu

```text
Parent
StudentParent
```

---

## 6.6. Module Teacher

### Chức năng

- Tạo giáo viên.
- Import danh sách giáo viên.
- Gán tổ chuyên môn.
- Gán môn có thể giảng dạy.
- Chỉ định giáo viên chủ nhiệm.
- Kích hoạt tài khoản giáo viên.
- Quản lý trạng thái công tác cơ bản.

### Dữ liệu

```text
Teacher
TeacherSubject
TeacherDepartment
HomeroomAssignment
```

---

## 6.7. Module Subject

### Chức năng

- Quản lý môn học.
- Mã môn.
- Tên môn.
- Nhóm môn.
- Trạng thái.
- Cấu hình môn theo khối.

### Dữ liệu

```text
Subject
GradeSubject
```

---

## 6.8. Module Teaching Assignment

### Chức năng

Gán:

```text
Teacher
+ Subject
+ Class
+ Academic Year
+ Term
```

### Quy tắc

Chỉ giáo viên được phân công mới có quyền:

- Điểm danh môn.
- Nhập điểm môn.
- Xem danh sách học sinh lớp tương ứng.

---

# 7. PHASE 1 – TIMETABLE

## 7.1. Chức năng

- Tạo tiết học.
- Cấu hình số tiết/ngày.
- Tạo thời khóa biểu lớp.
- Tạo thời khóa biểu giáo viên.
- Xem lịch theo tuần.
- Import thời khóa biểu.
- Export thời khóa biểu.
- Phát hiện xung đột.

## 7.2. Conflict Detection

Phát hiện:

- Giáo viên dạy hai lớp cùng lúc.
- Một lớp học hai môn cùng lúc.
- Một phòng được sử dụng bởi hai lớp.
- Giáo viên ngoài phân công.

## 7.3. Dữ liệu

```text
TimeSlot
Timetable
TimetableEntry
```

---

# 8. PHASE 1 – ATTENDANCE

## 8.1. Chức năng

Giáo viên có thể ghi nhận:

```text
Present
Absent
Absent With Permission
Late
Early Leave
```

## 8.2. Luồng cơ bản

```text
Giáo viên mở tiết học
        ↓
Danh sách học sinh
        ↓
Điểm danh
        ↓
Lưu kết quả
        ↓
Hệ thống cập nhật chuyên cần
        ↓
Gửi thông báo nếu học sinh vắng
        ↓
Phụ huynh xem thông tin
```

## 8.3. Quy tắc

- Chỉ giáo viên được phân công/GVCN/admin có quyền.
- Có thời gian khóa chỉnh sửa.
- Sửa dữ liệu sau khóa cần quyền đặc biệt.
- Mọi chỉnh sửa phải audit.

## 8.4. Dữ liệu

```text
AttendanceSession
AttendanceRecord
AttendanceReason
```

---

# 9. PHASE 1 – GRADING

## 9.1. Chức năng

- Khai báo loại điểm.
- Nhập điểm.
- Sửa điểm.
- Import điểm.
- Xem bảng điểm lớp.
- Xem bảng điểm học sinh.
- Khóa điểm.
- Mở khóa điểm có thẩm quyền.
- Tính điểm tổng hợp.

## 9.2. Không hard-code loại điểm

Ví dụ cấu hình:

```text
Regular
Midterm
Final
Other
```

Mỗi loại có thể có:

```text
weight
max_score
min_score
number_of_entries
```

## 9.3. Luồng

```text
Giáo viên chọn lớp
      ↓
Chọn môn
      ↓
Chọn loại điểm
      ↓
Nhập điểm
      ↓
Validate
      ↓
Lưu
      ↓
Audit
      ↓
Cập nhật kết quả học tập
```

## 9.4. Dữ liệu

```text
GradeType
Assessment
StudentScore
GradeLock
```

---

# 10. PHASE 1 – NOTIFICATION

## 10.1. Chức năng

Nhà trường có thể gửi tới:

- Toàn trường.
- Giáo viên.
- Học sinh.
- Phụ huynh.
- Khối.
- Lớp.
- Cá nhân.

## 10.2. Nội dung

- Tiêu đề.
- Nội dung.
- File đính kèm.
- Thời gian gửi.
- Đối tượng nhận.
- Trạng thái đã đọc.

---

# 11. PHASE 1 – STUDENT/PARENT APPLICATION

## 11.1. Student App

Học sinh xem:

- Thông tin cá nhân.
- Thời khóa biểu.
- Điểm danh.
- Kết quả học tập.
- Thông báo.
- Lịch học.

## 11.2. Parent App

Phụ huynh xem:

- Danh sách con.
- Điểm danh.
- Kết quả học tập.
- Thời khóa biểu.
- Thông báo.

## 11.3. Teacher Portal

Giáo viên:

- Xem lịch dạy.
- Xem lớp được phân công.
- Điểm danh.
- Nhập điểm.
- Xem thông báo.

---

# 12. PHASE 1 – REPORTING

Dashboard tối thiểu cho BGH:

- Tổng số học sinh.
- Tổng số lớp.
- Tổng số giáo viên.
- Tỷ lệ chuyên cần.
- Học sinh vắng trong ngày.
- Tình trạng nhập điểm.
- Các thông báo gần đây.

---

# 13. PHASE 1 – EXIT CRITERIA

Phase 1 hoàn thành khi thực hiện thành công flow:

```text
Tạo trường
↓
Tạo năm học
↓
Tạo khối/lớp
↓
Import học sinh
↓
Import giáo viên
↓
Phân công GVCN
↓
Phân công giảng dạy
↓
Tạo TKB
↓
Giáo viên điểm danh
↓
Phụ huynh nhận/xem thông tin
↓
Giáo viên nhập điểm
↓
Học sinh/phụ huynh xem kết quả
↓
BGH xem dashboard
```

---

# 14. PHASE 2 – SCHOOL OPERATIONS

## 14.1. Mục tiêu

Số hóa các quy trình vận hành trường học ngoài việc dạy và học cơ bản.

---

# 15. MODULE WORKFLOW ENGINE

## Chức năng

Cho phép cấu hình:

```text
Request
→ Approver
→ Approve / Reject
→ Next Approver
→ Complete
```

Workflow có thể cấu hình theo tenant.

Các chức năng:

- Workflow definition.
- Step definition.
- Role approver.
- Deadline.
- Approve.
- Reject.
- Request for update.
- History.
- Notification.

---

# 16. MODULE REQUEST / FORM

Các loại đơn có thể triển khai:

- Xin nghỉ học.
- Xin phép đi muộn.
- Xin về sớm.
- Xin nghỉ của giáo viên.
- Đề nghị sửa thông tin.
- Đề nghị điều chỉnh điểm.
- Đăng ký hoạt động.

Thiết kế dạng form động để dễ mở rộng.

---

# 17. MODULE DISCIPLINE & REWARD

## 17.1. Khen thưởng

- Ghi nhận thành tích.
- Đề xuất khen thưởng.
- Phê duyệt.
- Theo dõi lịch sử.

## 17.2. Kỷ luật

- Ghi nhận vi phạm.
- Biện pháp xử lý.
- Người ghi nhận.
- Phụ huynh xác nhận.
- Theo dõi lịch sử.

---

# 18. MODULE EVENTS

Chức năng:

- Tạo sự kiện.
- Lịch sự kiện.
- Đăng ký tham gia.
- Danh sách tham gia.
- Check-in.
- Thông báo.

Ví dụ:

- Sinh hoạt ngoại khóa.
- Hội thao.
- Họp phụ huynh.
- Hoạt động Đoàn.
- Sự kiện trường.

---

# 19. MODULE EXAM SCHEDULE

Chức năng:

- Tạo kỳ thi.
- Lịch thi.
- Phòng thi.
- Danh sách học sinh.
- Giáo viên coi thi.
- Công bố lịch thi.

---

# 20. MODULE HOMEROOM MANAGEMENT

GVCN có dashboard riêng:

- Sĩ số.
- Chuyên cần.
- Học sinh vắng.
- Kết quả học tập.
- Vi phạm.
- Khen thưởng.
- Thông báo phụ huynh.
- Học sinh cần chú ý.

---

# 21. MODULE COMMUNICATION

Nâng cấp từ Notification thành Communication Center:

- Thông báo.
- Xác nhận đã đọc.
- Phản hồi.
- Trao đổi GVCN – phụ huynh.
- Trao đổi nhà trường – phụ huynh.
- Thông báo yêu cầu xác nhận.

---

# 22. PHASE 2 – REPORTING

Bổ sung:

- Báo cáo chuyên cần.
- Báo cáo học sinh nghỉ nhiều.
- Báo cáo vi phạm.
- Báo cáo thành tích.
- Báo cáo điểm theo lớp.
- Báo cáo điểm theo môn.
- Báo cáo tiến độ nhập điểm.
- Báo cáo giáo viên.

---

# 23. PHASE 2 – EXIT CRITERIA

Một trường có thể vận hành các quy trình:

```text
Xin nghỉ
Xin phép
Sửa điểm
Kỷ luật
Khen thưởng
Hoạt động ngoại khóa
Lịch thi
Giao tiếp phụ huynh
```

trên hệ thống thay vì sử dụng giấy + Excel + Zalo rời rạc.

---

# 24. PHASE 3 – DIGITAL SCHOOL PLATFORM

## 24.1. Mục tiêu

Mở rộng School Core thành nền tảng quản trị trường học toàn diện.

Các module được triển khai độc lập và có thể bật/tắt theo tenant.

---

# 25. MODULE ADMISSION

Chức năng dự kiến:

- Tạo đợt tuyển sinh.
- Tiếp nhận hồ sơ.
- Upload hồ sơ.
- Kiểm tra hồ sơ.
- Phê duyệt.
- Nhập học.
- Chuyển dữ liệu thành Student.

---

# 26. MODULE TUITION & PAYMENT

Chức năng:

- Khai báo khoản thu.
- Tính khoản phải thu.
- Miễn/giảm.
- Theo dõi thanh toán.
- Biên lai.
- Tích hợp payment gateway.
- Báo cáo công nợ.

---

# 27. MODULE LIBRARY

Chức năng:

- Quản lý sách.
- Mã tài liệu.
- Mượn/trả.
- Gia hạn.
- Quá hạn.
- Phạt.
- Tra cứu.

---

# 28. MODULE ASSET MANAGEMENT

Quản lý:

- Thiết bị.
- Tài sản.
- Phòng học.
- Tình trạng.
- Bàn giao.
- Sửa chữa.
- Thanh lý.

---

# 29. MODULE LMS

Chức năng cơ bản:

- Khóa học.
- Bài học.
- Tài liệu.
- Bài tập.
- Nộp bài.
- Chấm bài.
- Theo dõi tiến độ.

Có thể:

- Tự phát triển.
- Hoặc tích hợp LMS bên thứ ba.

---

# 30. MODULE ONLINE EXAM

Chức năng:

- Ngân hàng câu hỏi.
- Đề thi.
- Trộn đề.
- Thi online.
- Chấm tự động.
- Kết quả.
- Phân tích câu hỏi.

---

# 31. MODULE CLUB & EXTRACURRICULAR

- Câu lạc bộ.
- Thành viên.
- Hoạt động.
- Đăng ký.
- Điểm danh.
- Thành tích.

---

# 32. MODULE STAFF BASIC HR

Không phát triển thành HRM doanh nghiệp hoàn chỉnh ở giai đoạn đầu.

Phạm vi:

- Hồ sơ cán bộ.
- Tổ chuyên môn.
- Chức vụ.
- Phân công.
- Trạng thái công tác.
- Hồ sơ chuyên môn.

---

# 33. INTEGRATION HUB

## 33.1. Mục tiêu

Cho phép kết nối với hệ thống ngoài.

## 33.2. Phương thức

```text
REST API
Webhook
Excel
CSV
SFTP
Message Queue
SSO
```

## 33.3. Quản trị integration

- API Credential.
- Integration mapping.
- Retry.
- Integration log.
- Error log.
- Webhook management.

---

# 34. PHASE 3 – EXIT CRITERIA

Hệ thống đạt trạng thái platform khi:

- Module có thể bật/tắt theo tenant.
- Có integration API chuẩn.
- Các module không phụ thuộc chặt vào nhau.
- Một trường có thể sử dụng hệ thống như hệ thống quản trị trung tâm.
- Có thể tích hợp với LMS/payment/SSO hoặc các nền tảng khác.

---

# 35. PHASE 4 – AI SCHOOL

## 35.1. Nguyên tắc

AI không được dùng để thay thế nền tảng dữ liệu lõi.

AI chỉ được phát triển khi:

- Dữ liệu đã đủ.
- Quy trình đã số hóa.
- Có lịch sử dữ liệu.
- Có permission rõ ràng.
- Có audit.

---

# 36. AI ASSISTANT FOR SCHOOL MANAGEMENT

Hỗ trợ BGH:

- Hỏi đáp số liệu.
- Tạo báo cáo.
- Tóm tắt tình hình trường.
- Phân tích chuyên cần.
- Phân tích kết quả học tập.
- Phát hiện bất thường.

Ví dụ:

```text
"Tuần này lớp nào có tỷ lệ vắng cao nhất?"

"Những lớp nào có kết quả môn Toán giảm mạnh?"

"Tạo báo cáo chuyên cần tháng 9."
```

---

# 37. AI ASSISTANT FOR TEACHERS

Chức năng tiềm năng:

- Tạo giáo án nháp.
- Gợi ý nội dung bài học.
- Sinh câu hỏi.
- Tạo quiz.
- Tóm tắt tài liệu.
- Phân tích kết quả lớp.
- Gợi ý học sinh cần hỗ trợ.

---

# 38. AI ASSISTANT FOR STUDENTS

Chức năng tiềm năng:

- Hỏi đáp kiến thức.
- Tóm tắt bài học.
- Gợi ý kế hoạch học.
- Giải thích bài.
- Sinh bài luyện tập.
- Phân tích điểm yếu.

---

# 39. AI ASSISTANT FOR PARENTS

Có thể hỗ trợ:

- Tóm tắt tình hình học tập.
- Tóm tắt chuyên cần.
- Thông báo điểm đáng chú ý.
- Tổng hợp hoạt động trong tuần.

AI không được tự đưa ra kết luận mang tính kỷ luật hoặc đánh giá chính thức học sinh.

---

# 40. EARLY WARNING SYSTEM

Phân tích:

```text
Attendance
+
Grades
+
Behavior
+
Assignment
+
Historical Trend
```

Để tạo:

- Warning.
- Risk score.
- Recommendation.

Kết quả chỉ mang tính hỗ trợ ra quyết định.

---

# 41. DATA & ANALYTICS PLATFORM

Ở Phase 4 có thể bổ sung:

```text
Operational DB
      ↓
ETL / CDC
      ↓
Data Warehouse
      ↓
BI / Analytics
      ↓
AI
```

---

# 42. YÊU CẦU PHI CHỨC NĂNG TOÀN HỆ THỐNG

## 42.1. Security

- Tenant isolation.
- RBAC.
- Encryption in transit.
- Password hashing.
- Sensitive data masking.
- Audit log.
- Session management.
- Rate limiting.
- File validation.
- Backup.
- Access log.

## 42.2. Performance

Mục tiêu ban đầu:

- API thông thường phản hồi < 2 giây ở tải tiêu chuẩn.
- Danh sách hỗ trợ pagination.
- Import dữ liệu chạy background khi file lớn.
- Report lớn không block request chính.

## 42.3. Availability

MVP:

```text
99.5%
```

Có thể nâng dần tùy SLA.

## 42.4. Scalability

Thiết kế hỗ trợ:

- Nhiều tenant.
- Nhiều năm học.
- Nhiều học sinh.
- Horizontal scale khi cần.

## 42.5. Backup

Tối thiểu:

- Daily backup.
- Retention.
- Restore test.
- Backup audit.

## 42.6. Observability

- Application logs.
- Error tracking.
- Metrics.
- Health check.
- Integration logs.
- Audit logs.

---

# 43. UI/UX PRINCIPLES

## Admin Web

Ưu tiên:

- Data table.
- Filter.
- Search.
- Bulk action.
- Import/export.
- Dashboard.

## Teacher

Ưu tiên thao tác nhanh:

```text
Hôm nay
→ Tiết dạy
→ Điểm danh
→ Nhập điểm
```

Không bắt giáo viên đi qua quá nhiều menu.

## Student/Parent

Mobile-first.

Dashboard nên tập trung:

- Hôm nay học gì.
- Có thông báo gì.
- Có vắng học không.
- Điểm mới.
- Lịch sắp tới.

---

# 44. DATA IMPORT STRATEGY

Excel import/export được coi là tính năng Core.

Các import cần hỗ trợ:

- Học sinh.
- Giáo viên.
- Lớp.
- Môn học.
- Phân công.
- Thời khóa biểu.
- Điểm.

Quy trình:

```text
Upload
↓
Validate
↓
Preview
↓
Show Error
↓
Confirm
↓
Import
↓
Audit
```

Không import trực tiếp mà không preview/validate.

---

# 45. CONFIGURATION VS CUSTOMIZATION

## Level 1 – Configuration

Không sửa code.

Ví dụ:

- Loại điểm.
- Workflow.
- Permission.
- Module.
- Notification.
- Form.

## Level 2 – Shared Extension

Nhu cầu của một trường nhưng có giá trị cho nhiều trường.

Phát triển thành module chung.

## Level 3 – Customer Extension

Chức năng chỉ một khách hàng sử dụng.

Phát triển dưới dạng:

```text
plugin
extension
integration
custom module
```

Không thay đổi School Core nếu không cần thiết.

---

# 46. QUY TẮC ĐÁNH GIÁ YÊU CẦU MỚI

Mỗi yêu cầu khách hàng cần được phân loại:

| Loại | Câu hỏi |
|---|---|
| Core | Hầu hết trường THPT có cần không? |
| Config | Có thể xử lý bằng cấu hình không? |
| Shared Module | Nhiều trường có thể dùng không? |
| Integration | Có thể kết nối hệ thống khác không? |
| Custom | Chỉ riêng khách hàng này cần không? |

---

# 47. PRODUCT RELEASE STRATEGY

## Release 0.x

Internal development.

## Release 1.0

School Core MVP.

## Release 1.x

Pilot improvements.

## Release 2.0

School Operations.

## Release 3.0

Digital School Platform.

## Release 4.0

AI capabilities.

---

# 48. PILOT STRATEGY

Sau Phase 1 nên tìm:

```text
1–3 trường THPT
```

làm Design Partner.

Mục tiêu pilot không chỉ là bán sản phẩm mà để thu thập:

- Quy trình thực tế.
- Dữ liệu thực tế.
- Điểm đau.
- Workflow khác nhau.
- Yêu cầu báo cáo.
- Các ngoại lệ.

Sau mỗi pilot:

```text
Requirement
↓
Classification
↓
Core / Config / Module / Custom
↓
Product Decision
```

---

# 49. DEFINITION OF MVP

MVP được coi là đạt khi một trường có thể thực hiện end-to-end:

```text
Khởi tạo trường
↓
Khởi tạo năm học
↓
Tạo lớp
↓
Nhập giáo viên
↓
Nhập học sinh
↓
Gán GVCN
↓
Phân công giảng dạy
↓
Tạo TKB
↓
Giáo viên dạy
↓
Điểm danh
↓
Thông báo phụ huynh
↓
Nhập điểm
↓
Học sinh/phụ huynh xem
↓
BGH theo dõi
```

---

# 50. NHỮNG HẠNG MỤC KHÔNG NÊN LÀM TRONG MVP

Chưa ưu tiên trong Phase 1:

- HRM đầy đủ.
- Payroll.
- Kế toán tổng thể.
- LMS nâng cao.
- Thi online hoàn chỉnh.
- Thư viện.
- Tài sản.
- Camera AI.
- AI chấm bài.
- AI chatbot toàn trường.
- Xe đưa đón.
- Ký túc xá.
- Cổng thanh toán phức tạp.
- Tuyển sinh toàn diện.

---

# 51. BACKLOG ƯU TIÊN PHASE 1

## P0

- Tenant.
- User.
- Role/Permission.
- Academic Year.
- Term.
- Grade.
- Class.
- Student.
- Parent.
- Teacher.
- Subject.
- Teaching Assignment.
- Timetable.
- Attendance.
- Grading.
- Notification.
- Audit.
- Import/export.

## P1

- Dashboard BGH.
- Teacher Dashboard.
- Student App.
- Parent App.
- Basic reporting.
- Notification push.
- Bulk operation.

## P2

- Advanced analytics.
- Flexible reporting.
- Advanced timetable.
- Advanced workflow.

---

# 52. ĐỀ XUẤT TEAM TRIỂN KHAI

Team tối thiểu có thể gồm:

```text
Product Owner
BA
UI/UX
Backend
Frontend
Mobile
Tester
DevOps
```

Nếu nguồn lực hạn chế:

```text
PO/BA
2 Backend
1 Frontend
1 Mobile
1 Tester
DevOps part-time
```

---

# 53. THỨ TỰ PHÂN TÍCH CHI TIẾT TIẾP THEO

Sau tài liệu này nên tạo lần lượt:

1. Product Functional Map.
2. Domain Model.
3. ERD.
4. Permission Matrix.
5. User Journey.
6. Business Process.
7. User Story.
8. API Specification.
9. UI Wireframe.
10. Test Scenario.
11. Deployment Architecture.
12. Security Architecture.

---

# 54. KẾT LUẬN

Định hướng triển khai phù hợp nhất:

```text
Phase 0
Foundation
        ↓
Phase 1
School Core MVP
        ↓
Pilot 1–3 trường
        ↓
Product Validation
        ↓
Phase 2
School Operations
        ↓
Phase 3
Digital School Platform
        ↓
Phase 4
AI School
```

Nguyên tắc quan trọng nhất:

> Không xây một phần mềm cho một trường cụ thể ngay từ đầu.  
> Xây một School Core đủ chuẩn, sau đó sử dụng Configuration, Module và Integration để thích ứng với từng khách hàng.

Mục tiêu của Phase 1 không phải là có thật nhiều chức năng.

Mục tiêu là:

> **Một trường THPT có thể vận hành được chu trình học tập cơ bản hoàn toàn trên hệ thống, từ lớp học → thời khóa biểu → điểm danh → điểm → phụ huynh → báo cáo.**
