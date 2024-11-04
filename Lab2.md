# Lab2 :
# Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
## 1.Phân tích ca sử dụng Create Employee
### 1.1. Xác định các lớp phân tích Create Employee
Đối với trường hợp sử dụng "Create Employee", các lớp phân tích có thể bao gồm: 
### 1.2. Biểu đồ Sequence
### 1.3. Nhiệm vụ từng lớp phân tích
### 1.4. Thuộc tính và quan hệ giữa các 
## 2.Phân tích ca sử dụng Maintain Purchase Order
## 3.Phân tích ca sử dụng Login
## 4.Phân tích ca sử dụng Create Administrative Report
### 4.1. Xác định các lớp phân tích Create Administrative Report
Đối với trường hợp sử dụng "Create Administrative Report", các lớp phân tích chính có thể bao gồm:

A. Lớp Control Classes
+ ReportRequest: Lưu trữ thông tin về loại báo cáo, khoảng thời gian, và tên nhân viên được yêu cầu báo cáo.
+ ReportGenerator: Chịu trách nhiệm xử lý yêu cầu từ ReportRequest và tạo báo cáo dựa trên các tiêu chí đã cung cấp.

B. Lớp Entity Classes
+ Report: Đại diện cho báo cáo đã được tạo, có thể là "Total Hours Worked" hoặc "Pay Year-to-Date".
+ StorageService: Xử lý lưu trữ và quản lý các báo cáo nếu Quản trị viên chọn lưu.

C. Lớp Boundary Classes
+ PayrollAdministrator: Đại diện cho người dùng yêu cầu tạo báo cáo và xác định các tiêu chí, có quyền lưu hoặc loại bỏ báo cáo sau khi tạo.
### 4.2. Biểu đồ Sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/TL8xJiGm5EnzYgUjibAum1PeeQ6XGBidS19hry9hW_CSAMUWegJZKo2jXA3s5XH6tCCtmHjmuaYXoMSyCs_UoCiQgKQp4uIMg3HSqLOh8Swg7PUyHaq3I0fbP4Lr2xCLkr4QL-pMi1fdG6lGAK9A9J7e8_62ITPP9DGU8qmYnzuqeGmswy2Z6xPckk4bwoZr229aAZ6Sd8w3BG2zVLAG2HNU70eNVihmo45kt6CBXRVl25_tthwQY5rx-uc0MsVB7D3j9SYjUvRGyF0z9wC1myH-lpZpFCw2h7Lx0-LnHfJtxC7WJvT9VtZWK1cvoU4tTWpMdUTJQHAxYGgqjoyWnWNyN-2uw0M8xmypB9Cb5JR-S1VStTkSZ4NfKfT1JfPCLiVBzWC0)
### 4.3. Nhiệm vụ từng lớp phân tích
+ ReportRequest: Xác định và lưu trữ thông tin về loại báo cáo, khoảng thời gian, và danh sách nhân viên cần báo cáo.
+ ReportGenerator: Tạo báo cáo dựa trên thông tin từ ReportRequest và gửi báo cáo cho PayrollAdministrator.
+ Report: Giữ dữ liệu của báo cáo, bao gồm nội dung báo cáo và thông tin nhân viên liên quan.
+ StorageService: Lưu báo cáo vào hệ thống theo yêu cầu từ Quản trị viên.
+ PayrollAdministrator: Đặt yêu cầu tạo báo cáo, xác định tiêu chí báo cáo và quyết định có lưu báo cáo hay không.
### 4.4. Thuộc tính và quan hệ giữa các 
+ ReportRequest:
  - Thuộc tính: reportType, beginDate, endDate, employeeNames[]
  - Quan hệ: Tương tác với ReportGenerator để truyền thông tin yêu cầu báo cáo.
+ ReportGenerator:
  - Thuộc tính: generateReport(request: ReportRequest)
  - Quan hệ: Nhận yêu cầu từ ReportRequest và tạo Report theo tiêu chí yêu cầu.
+ Report:
  - Thuộc tính: content, type, createdDate, employees[]
  - Quan hệ: Được khởi tạo bởi ReportGenerator và có thể được lưu bởi StorageService nếu Quản trị viên yêu cầu.
+ StorageService:
  - Thuộc tính: saveReport(report: Report, location: String)
  - Quan hệ: Nhận yêu cầu từ PayrollAdministrator để lưu Report.
+ PayrollAdministrator:
  - Thuộc tính: name, id, privileges
  - Quan hệ: Khởi tạo ReportRequest và quyết định lưu Report thông qua StorageService.
## 5.Phân tích ca sử dụng Create Employee Report
## 6.Phân tích ca sử dụng Maintain Employee Information
## 7.Phân tích ca sử dụng Run Payroll
# Viết code Java mô phỏng ca sử dụng Maintain Timecard.
