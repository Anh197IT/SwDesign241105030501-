# Lab2 :
# Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
## 1.Phân tích ca sử dụng Create Employee
### 1.1. Xác định các lớp phân tích Create Employee
### 1.2. Biểu đồ Sequence
### 1.3. Nhiệm vụ từng lớp phân tích
### 1.4. Thuộc tính và quan hệ giữa các 
## 2.Phân tích ca sử dụng Maintain Purchase Order
## 3.Phân tích ca sử dụng Login
## 4.Phân tích ca sử dụng Create Administrative Report
### 4.1. Xác định các lớp phân tích Create Administrative Report
Đối với trường hợp sử dụng "Create Administrative Report", các lớp phân tích chính có thể bao gồm:

ReportRequest: Lưu trữ thông tin về loại báo cáo, khoảng thời gian, và tên nhân viên được yêu cầu báo cáo.
ReportGenerator: Chịu trách nhiệm xử lý yêu cầu từ ReportRequest và tạo báo cáo dựa trên các tiêu chí đã cung cấp.
Report: Đại diện cho báo cáo đã được tạo, có thể là "Total Hours Worked" hoặc "Pay Year-to-Date".
StorageService: Xử lý lưu trữ và quản lý các báo cáo nếu Quản trị viên chọn lưu.
PayrollAdministrator: Đại diện cho người dùng yêu cầu tạo báo cáo và xác định các tiêu chí, có quyền lưu hoặc loại bỏ báo cáo sau khi tạo.
### 4.2. Biểu đồ Sequence
### 4.3. Nhiệm vụ từng lớp phân tích
### 4.4. Thuộc tính và quan hệ giữa các 
## 5.Phân tích ca sử dụng Create Employee Report
## 6.Phân tích ca sử dụng Maintain Employee Information
## 7.Phân tích ca sử dụng Run Payroll
# Viết code Java mô phỏng ca sử dụng Maintain Timecard.
