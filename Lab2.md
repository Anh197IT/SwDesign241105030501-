# Lab2 :
# Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
## 1.Phân tích ca sử dụng Create Employee
### 1.1. Xác định các lớp phân tích Create Employee
A. Lớp Boundary Classes
+ EmployeeUI: Giao diện tương tác với người dùng (Employee).

B. Lớp Entity Classes
+ Employee: Đại diện cho người dùng (nhân viên) đang tạo báo cáo.
+ ProjectManagementDatabase: Lớp này liên kết với cơ sở dữ liệu quản lý dự án, được sử dụng để lấy danh sách các mã dự án cho báo cáo.
+ Report: Đại diện cho báo cáo được tạo ra với các thuộc tính và nội dung theo yêu cầu của nhân viên.
+ FileManager: Xử lý việc lưu trữ và quản lý các báo cáo trên hệ thống theo tên và vị trí được chỉ định.

C. Lớp Control Classes
+ ReportManager: Chịu trách nhiệm quản lý và xử lý yêu cầu tạo báo cáo, bao gồm việc xác minh thông tin cần thiết và tạo báo cáo dựa trên tiêu chí đã chọn.
### 1.2. Biểu đồ Sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/ZPFFJiCm3CRlUGfhzxt03cWIuyy52G4IPvDuKo1DWkCExUt9ccLhQJVMGwN6-VcpFxlB9CZIDawXbi1mrqGNTaGgvcEhRKGly48ni3oXnmtn8FBCuPFq8TIGbnKAVc0QylVMqHHTyYfLHM5-CzHQvC_lbfA01D1CA0HSeC6zFLYJd9Xo4sGN2T0R4DiGH68Rp2N9tDFMcYgKPQra1fL2LqikEMs2sLiGTF0OMaxm7lYB3AopZLYTcId8pwZOixuju844OWc33ePIb-4i0FCfqwHbFv7b2jEoqOdS7klZ7Nt1izS9XBnHup6LWtsRddWqpmlTR0w0kM83LZP5XxjwivlSiVgVl7gfwnEtH_ahtJdiXCUch9GB6iK6_vy_TQUcmP5mxuV9tlufinVix3fLUHlysd83gTMQKbgthkknJ6APt_a__mK0)
### 1.3. Nhiệm vụ từng lớp phân tích
+ Employee: Cung cấp thông tin đầu vào và lựa chọn cho báo cáo, quyết định có lưu báo cáo hay không.
+ ReportManager: Xử lý toàn bộ quy trình tạo báo cáo, bao gồm việc yêu cầu thông tin từ Employee, kết nối với ProjectManagementDatabase nếu cần, tạo báo cáo, và gửi yêu cầu lưu trữ cho FileManager.
+ ProjectManagementDatabase: Cung cấp danh sách mã dự án khi Employee chọn loại báo cáo "Total Hours Worked for a Project".
+ Report: Giữ thông tin và nội dung của báo cáo sau khi được tạo.
+ FileManager: Lưu báo cáo tại vị trí và với tên do Employee cung cấp.
### 1.4. Thuộc tính và quan hệ giữa các 
+ Employee có thể tạo nhiều Report.
+ ReportManager phối hợp với Employee và FileManager để tạo và lưu Report.
+ ProjectManagementDatabase là nguồn dữ liệu cho ReportManager khi cần lấy mã dự án.
+ Report chứa các thuộc tính như type, beginDate, endDate, và nếu cần thì chargeNumber (khi là báo cáo cho dự án cụ thể).
+ FileManager có khả năng lưu trữ và truy xuất Report trong hệ thống.
## 2.Phân tích ca sử dụng Maintain Purchase Order
### 2.1. Xác định các lớp phân tích
A. Lớp Boundary Classes
+ CommissionedEmployeeUI: Thu thập thông tin từ nhân viên, hiển thị thông tin đơn hàng mua, và xác nhận các hành động yêu cầu từ người dùng.

B. Lớp Entity Classes
+ CommissionedEmployee: Nhân viên này có thể tạo, sửa đổi, hoặc xóa các đơn hàng mua và lưu trữ thông tin.
+ PurchaseOrder: Lớp này chứa các thuộc tính cần thiết để ghi lại một đơn hàng mua.
+ Product: Chứa thông tin chi tiết về các sản phẩm được mua trong đơn hàng.
+ Database: Đại diện cho cơ sở dữ liệu nơi lưu trữ tất cả các đơn hàng mua và thông tin liên quan đến nhân viên và sản phẩm.

C. Lớp Control Classes
+ PurchaseOrderManager: Xác định chức năng được chọn (tạo, cập nhật, hoặc xóa), xác minh thông tin đơn hàng mua, liên kết với các lớp khác để truy xuất hoặc cập nhật dữ liệu, và thực hiện xác nhận khi xóa đơn hàng mua.
### 2.2. Biểu đồ sequence
![Sequnece Diagram](https://www.planttext.com/api/plantuml/png/tPR1ReCm38RlF8LFswalK4rJfL9DFKoRMh5xIamR2HAME9lwzaiRs6XBWDAUne43TZuS-_y3CqDCaotoYAMaDCnLKGXZX9B85qMPgprYLBeKaOgIIMfDI9OdAUzMfpjcy4rprAzCiYtgauIO4TkuXF2gA7g4kKP6-FiSV62hbIq3CN1NMtqmUGxKFOKLVbeq1AGWzL3LoKgM8TeVwqW0ZiH4RaPLjP3a29uZPAPwocdh-1JMTbC8EgUqvLumfdM79Nut6X9QMm_KlPDzDJjO1s0Ih7A5PBM4iXbSnbqRVfhS1tK0XGOG2rFcR7_1GiaFsanAVga_W4gThT5RrMazz7Pr3cvFhpwlc5bm_1-eHRQ_IcCls6QnuL8RPiykeTNg66Zq3fsjTweo66Jk-4KkICZjg9bKTlSwuUEFZUHSQ0DTNx_OBwoC4cEEeKEyFNQZJRY7_bERi3H5O-01t6URRATuUpUOAfa9NJ1oyL6xctk0RtaNf6jZTJKda7x5nSqn7xKsStVt7_C3)
### 2.3. Nhiệm vụ từng lóp phân tích
+ CommissionedEmployeeUI: Thu thập thông tin người dùng và hiển thị dữ liệu. Xác nhận các hành động yêu cầu như tạo, cập nhật, hoặc xóa đơn hàng mua.
+ PurchaseOrderManager: Thực hiện logic nghiệp vụ chính, như xác thực thông tin, xử lý tạo, cập nhật và xóa đơn hàng, và xác minh quyền sở hữu đơn hàng.
+ CommissionedEmployee: Đại diện cho nhân viên tương tác với hệ thống. Lưu trữ và quản lý thông tin nhân viên.
+ PurchaseOrder: Giữ thông tin về đơn hàng, bao gồm các sản phẩm, thông tin khách hàng, địa chỉ thanh toán, và trạng thái của đơn hàng.
+ Product: Lưu trữ thông tin chi tiết về các sản phẩm trong đơn hàng.
+ Database: Cung cấp các chức năng truy cập dữ liệu để lưu trữ và lấy thông tin đơn hàng, nhân viên, và sản phẩm.
### 2.4. Thuộc tính và quan hệ
+ CommissionedEmployee: Có thuộc tính employeeID, name.
+ PurchaseOrder: Có các thuộc tính purchaseOrderID, customerContact, billingAddress, productList, date, status. Mỗi PurchaseOrder thuộc về một CommissionedEmployee.
+ Product: Thuộc tính gồm productID, productName, quantity, và price.
+ Database: Quan hệ lưu trữ với PurchaseOrder, CommissionedEmployee, và Product. Cung cấp các phương thức savePurchaseOrder(), retrievePurchaseOrder(), deletePurchaseOrder().
## 3.Phân tích ca sử dụng Login
### 3.1. Xác định các lớp phân tích
A. Lớp Boundary Classes
+ LoginUI: Là giao diện cho phép người dùng nhập tên và mật khẩu để đăng nhập vào hệ thống.

B. Lớp Entity Classes
+ User: Đại diện cho một người dùng trong hệ thống.
+ Database: Đại diện cho cơ sở dữ liệu lưu trữ thông tin người dùng.

C. Lớp Control Classes
+ AuthenticationManager: Lớp điều khiển chính xử lý logic đăng nhập.
### 3.2. Biểu đồ sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/dLD1JiCm4Bpx5NlYrW_aW8eeGfNWKbJkssHJB3bswbq3_JrhfoaK6b7mmRB7ixFZSJ9dmIYfSmPh2H7MJD7q2jdQzkW57iBM-lNo1Bj9ya9UjoWs-4VqkFrMjK313JATW5bxwTjWJ5x1x7eKh-3EYo99OOyTmHNqoFmMOcCEbCm-sxQ2fxJfh40TgScdwDYSPMQ9qLS5zoIb7zZiQCHXDjrdHPAY7ueQvHk3RhWKqBjbOGCw9bjFgDw6JZEYuuK7bJ9b-MTqjlbC0mvZeilNICi2EDKrCRV97MkFYIexkwzWORbtk1_96lysvWV3iYs5v3ISfN_zjvrJ2hHe7JKNUA8OzRFir8Tg_kIFz1Nj4h6018WaSJ-OzaC7KzoNb_91e0tfS721xpDLVp7xkz5iqinrrf_m0m00)
### 3.3. Nhiệm vụ từng lóp phân tích
+ LoginUI: Thu thập thông tin đăng nhập từ người dùng, hiển thị trạng thái đăng nhập, và thông báo lỗi nếu cần.
+ AuthenticationManager: Xử lý logic xác thực đăng nhập, bao gồm truy xuất thông tin người dùng từ cơ sở dữ liệu, xác minh tính hợp lệ của thông tin đăng nhập, và cung cấp phản hồi cho LoginUI.
+ User: Đối tượng chứa thông tin về người dùng, bao gồm các thuộc tính đăng nhập và quyền truy cập.
+ Database: Quản lý và cung cấp truy cập vào dữ liệu người dùng. Đảm bảo thông tin người dùng được bảo mật và truy xuất theo yêu cầu.
### 3.4. Thuộc tính và quan hệ
+ User
  - Thuộc tính: username, passwordHash, userID, role
  - Quan hệ: Một đối tượng User có mối quan hệ với Database để xác minh thông tin đăng nhập.
+ LoginUI
  - Thuộc tính: inputUsername, inputPassword
  - Quan hệ: Tương tác với User và gửi thông tin đăng nhập đến AuthenticationManager.
+ AuthenticationManager
  - Thuộc tính: Không cần lưu trữ dữ liệu lâu dài, chỉ xử lý các chức năng xác thực tạm thời.
  - Quan hệ: Tương tác với LoginUI và Database để xác minh thông tin đăng nhập.
+ Database
  - Thuộc tính: Lưu trữ danh sách User, với thông tin chi tiết bao gồm username và passwordHash.
  - Quan hệ: Cung cấp thông tin cho AuthenticationManager để xác thực quyền truy cập.
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
### 5.1. Xác định các lớp phân tích
A. Lớp Boundary Classes
+ ReportUI: Giao diện cho phép nhân viên chọn loại báo cáo, cung cấp các tiêu chí cần thiết và yêu cầu lưu báo cáo.

B. Lớp Entity Classes
+ Employee: Đại diện cho nhân viên trong hệ thống.
+ Report: Đại diện cho báo cáo được tạo ra.
+ ProjectManagementDatabase: Đại diện cho cơ sở dữ liệu dự án.
+ FileManager: Xử lý lưu trữ và quản lý các báo cáo trên hệ thống dựa trên tên và vị trí được chỉ định.

C. Lớp Control Classes
+ ReportManager: Xử lý logic để tạo báo cáo và tạo báo cáo dựa trên tiêu chí được chỉ định.
### 5.2. Biểu đồ sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/VLJBRi8m4BpxArOSUkC7E5H8qDUXKWMjUbwIXRfrx7IzeUBlwyGn4FB88GVlpEnulFRI2x9KXL6OYMDuA4hZJaIg3CiwqoLQWGsLZkNZPM3n5IqUY3kLDtRVbBMbWgoiKN27VaYqi_Ie3IL1bPp0_FviO05RCa4Qk5a0EPK4Tv2n5cADAk4kd5Qk9jeyqSvuXIOPYLhQm-pT2HfuTXLx-7JyGpdiGpAOzZLJ4BwEVDrlTDSBU2A1CfOXSpdvHc6K0FE-_Gr9nNP0fUVZajLQ-zBWQPGKSqevXuY-t5yN34PxQHYJft7DwUaFdODlU27O3ZDKb1hPpm9MJ2YKZj3jQbwBdWZiG9OOwrQHEAOVTsDlOBS9fKHRK3C-vsIOVYloua4SU3mcgnFnRIAZXnvkdj3xS4ii5lNW6vUXQ6SdUeGfE-gSOe-S1BNfpy3LnHjtTGNgSRPJs8wVbRDxpKLK3u-FL5CZcG9llVZAI1oJPVY7L-iV)
### 5.3. Nhiệm vụ từng lóp phân tích
+ ReportUI: Thu thập tiêu chí báo cáo từ nhân viên, hiển thị báo cáo được tạo, yêu cầu nhập thông tin lưu trữ nếu cần, và thông báo lỗi khi có thông tin thiếu hoặc không hợp lệ.
+ ReportManager: Xử lý việc tạo báo cáo dựa trên các tiêu chí đầu vào, quản lý logic cho các loại báo cáo khác nhau, và đảm bảo rằng dữ liệu đúng và đầy đủ trước khi tạo báo cáo.
+ Employee: Đối tượng đại diện cho người dùng, có khả năng khởi tạo yêu cầu báo cáo và xác định các tiêu chí cụ thể cho báo cáo.
+ ProjectManagementDatabase: Cung cấp danh sách mã số dự án khi nhân viên chọn tạo báo cáo "Total Hours Worked for a Project".
+ Report: Chứa dữ liệu và thông tin báo cáo được tạo ra, bao gồm các thuộc tính như ngày bắt đầu, ngày kết thúc, loại báo cáo, và các kết quả cụ thể.
+ FileManager: Đảm nhiệm lưu trữ báo cáo ở tên và vị trí được chỉ định, xử lý các vấn đề liên quan đến lưu trữ và quản lý file.
### 5.4. Thuộc tính và quan hệ
+ Employee
  - Thuộc tính: employeeID, name
  - Quan hệ: Tương tác với ReportUI để khởi tạo và quản lý quy trình tạo báo cáo.
+ ReportUI
  - Thuộc tính: selectedReportType, beginDate, endDate, saveLocation, reportName
  - Quan hệ: Tương tác với Employee và ReportManager để gửi yêu cầu tạo báo cáo và hiển thị kết quả.
+ ReportManager
  - Thuộc tính: Không cần lưu trữ dữ liệu lâu dài, chỉ xử lý các chức năng tạo báo cáo tạm thời.
  - Quan hệ: Nhận yêu cầu từ ReportUI và lấy dữ liệu từ ProjectManagementDatabase nếu cần, tạo Report dựa trên tiêu chí.
+ ProjectManagementDatabase
  - Thuộc tính: Danh sách các projectChargeNumber
  - Quan hệ: Cung cấp thông tin về các dự án khi ReportManager yêu cầu để tạo báo cáo cho "Total Hours Worked for a Project".
+ Report
  - Thuộc tính: reportID, reportType, beginDate, endDate, content
  - Quan hệ: Là đối tượng chứa kết quả báo cáo do ReportManager tạo ra.
+ FileManager
  - Thuộc tính: saveLocation, reportName
  - Quan hệ: Đảm nhận việc lưu trữ báo cáo tại vị trí được chỉ định, có thể tương tác với ReportUI để xác nhận lưu trữ thành công.
## 6.Phân tích ca sử dụng Maintain Employee Information
### 6.1. Xác định các lớp phân tích
A. Lớp Boundary Classes
+ EmployeeInfoUI: Cung cấp giao diện cho Payroll Administrator.

B. Lớp Entity Classes
+ Employee: Lưu trữ thông tin chi tiết của một nhân viên.
+ PayrollDatabase: Đại diện cho cơ sở dữ liệu nhân viên, lưu trữ và quản lý dữ liệu liên quan đến tất cả nhân viên.
+ Paycheck: Đại diện cho phiếu lương, được liên kết với nhân viên để tính toán lương lần cuối khi nhân viên bị xóa khỏi hệ thống.

C. Lớp Control Classes
+ EmployeeManager: Xử lý các thao tác quản lý thông tin nhân viên.
### 6.2. Biểu đồ sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/xLRBJiCm4BptArPSEFK7Ua2W1gGUa12e7x2DjyNWsC4FeVuzsyQX975IypZIGwIkFPdrp6oIQ-VH-b2f6PRUMBXumBqrIi6DgAIMpblayWMWQogpchVBKjQeFTnMjJ9xefNUclKgkNIF6dTaEskHea2F6tIKnCrcbqmeJlztreIwMmB-7Pk2-LMlbmKyaQBI3m7TVL-HiTK5FD9R8EV16q26KmeUDwUOMtYB0yaBja8lZPxk-LPxlkKdJf17gLnksq-anJZfHECBM5f2JoUmsRomU6Eudd_Cp14XqFJUrQgt3-PfiNsm-aIzAjAqIQ4deQrKZ3mgle12kbhXleDWqGvPMzVYe40lRlrgJk9IcA5xiQD1Lk8PSYCoSkI9K7S2aktmdTJY3ymTvqmSjNMh3DOIFne-mMV42KS3n93itEoC0gUKYNOFZvWbqDBehRHLfCwM9fAwK9Rat3QepE2N3LtpL8Z9BpYsm-Jtgpd9Js7-a_-Bv8-ZH-KK1m_OtQxLayAs6MoXtzKrYPkIz1xjA_3RwInoEARbCucW2BPIeuAwkVFtnwtY3gJUvHlIgbfRSvWuE7uraVZns5tpbJ-wFW00)
### 6.3. Nhiệm vụ từng lóp phân tích
+ EmployeeInfoUI: Thu thập thông tin về nhân viên từ Payroll Administrator, hiển thị các thông báo lỗi hoặc kết quả, và yêu cầu xác nhận trong các thao tác xóa.
+ EmployeeManager: Quản lý logic nghiệp vụ của việc thêm, cập nhật, và xóa nhân viên. Xác nhận tính hợp lệ của dữ liệu và xử lý yêu cầu trước khi lưu trữ vào PayrollDatabase.
+ Employee: Đại diện cho một nhân viên với các thuộc tính về tên, loại nhân viên, thông tin lương, và các khoản khấu trừ.
+ PayrollDatabase: Lưu trữ và quản lý thông tin của nhân viên, cung cấp các chức năng để tìm kiếm, thêm, và đánh dấu nhân viên cần xóa.
+ Paycheck: Tính toán và xử lý phiếu lương cuối cùng của nhân viên khi nhân viên bị xóa khỏi hệ thống.
### 6.4. Thuộc tính và quan hệ
+ Employee
  - Thuộc tính: employeeID, name, employeeType, address, ssn, taxDeductions, otherDeductions, phoneNumber, hourlyRate, salary, commissionRate, hourLimit
  - Quan hệ: Được quản lý bởi EmployeeManager và lưu trữ trong PayrollDatabase.
+ EmployeeInfoUI
  - Thuộc tính: actionType, employeeData
  - Quan hệ: Tương tác với Payroll Administrator và EmployeeManager để nhận và gửi thông tin.
+ EmployeeManager
  - Thuộc tính: Không yêu cầu lưu trữ lâu dài, chỉ quản lý các quy trình thêm, sửa, và xóa nhân viên.
  - Quan hệ: Làm việc với PayrollDatabase để thêm, cập nhật và đánh dấu xóa nhân viên, đồng thời gửi thông báo cho EmployeeInfoUI.
+ PayrollDatabase
  - Thuộc tính: Danh sách các Employee
  - Quan hệ: Cung cấp các chức năng truy vấn và lưu trữ nhân viên cho EmployeeManager.
+ Paycheck
  - Thuộc tính: payAmount, payDate
  - Quan hệ: Được tạo và xử lý cho nhân viên bị xóa khỏi hệ thống, lưu trữ và quản lý thông tin lương của nhân viên.
## 7.Phân tích ca sử dụng Run Payroll
### 7.1. Xác định các lớp phân tích
A. Lớp Boundary Classes
+ PayrollScheduler: Kích hoạt tự động quy trình tính lương vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng.
+ BankSystemInterface: Quản lý giao tiếp với hệ thống ngân hàng để xử lý các giao dịch thanh toán qua phương thức chuyển khoản.
B. Lớp Entity Classes
+ Employee: Lưu trữ thông tin chi tiết về nhân viên.
+ Timecard: Lưu trữ thông tin về số giờ làm việc của nhân viên.
+ PurchaseOrder: Lưu trữ thông tin về các đơn hàng đã ghi nhận của nhân viên.
+ Paycheck: Đại diện cho phiếu lương, lưu trữ thông tin lương sau khi đã được tính toán.
C. Lớp Control Classes
+ PayrollProcessor: Xử lý toàn bộ quy trình tính toán và thực hiện chi trả lương.
+ BankTransactionManager: Điều khiển và giám sát quá trình gửi giao dịch đến ngân hàng.
### 7.2. Biểu đồ sequence
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/fLLPRXin3FsVK-YlFvaB54MHDccA02qQsBu0BN4yWhL1YmlVljHidZLDsW11Of5l4IdIzo62Zqch0dYqdht0rLkbzhn6aHJwmb5OSkd0n3xuuYt74Engy14Y727W9FPDEsMlE3qyI8qSl9Yo9CzhWl_oOYbEflXvSlWLpFdWmGHoBwtv2GPECrnEsLz3HFri8leAE6x4Y-B3uluiUdaYoi1YZSorKURQ2XIBxFBpeaZi8pkq70luJU-MxP4KyOA1OLUqm7xNbeNQ9YNOCPkGebZWRifz1qZuEyOHJRHp-91QhXll-yQK337R_M6jeqfucqurG-3rG5-e77eYM7CyT9pHpyerJq3rfAeASi0gR_M0k1iUnXq38sOl8jEjtNrmEhqqawQocw1Ug0F5_kEhe8cV3kcwCsRp8JLsuzOS54yA8ZMZUmlRCijkFFJeuI61jid4NkuXZqUEQQHthJ7MLh2gxmYEEmAg6QWcyNXb6gGYxyn9VawkoNZ5LpE6sO_7R2OtoNb9JAuVqGn6HVKOQGZfaKScqDaWuwiQwrDDYiz6HfarZvH1epca37GRq8vqjWU8SO_aVaIKXoHdicubZ7ddw0afSNLts3QNgzwGXnQI35oeyd1KEEHiYNqgowdQ4o6JdmAR6TpH1haITwIUXiIpfIgfITw_L6g7OLQhLSgt5ccBXpI6pyqJ6XViFygrRojHp7Not_nBo-rB5VEIRWrASw9-gTlwVEFAROSmJvq6VqPHqh-bG8NDwrgmtJRmwiW_PY2ATxlOeRON_8k5ufukdh_w_m00)
### 7.3. Nhiệm vụ từng lóp phân tích
+ PayrollScheduler: Khởi động quy trình trả lương vào thời gian quy định (thứ Sáu và ngày làm việc cuối tháng).
+ PayrollProcessor: Điều khiển toàn bộ quy trình xử lý tính lương, tính toán tiền lương của từng nhân viên dựa trên thông tin từ các đối tượng Employee, Timecard, và PurchaseOrder, và quyết định phương thức thanh toán phù hợp.
+ BankTransactionManager: Quản lý giao dịch ngân hàng khi phương thức thanh toán là chuyển khoản, bao gồm việc gửi và theo dõi các giao dịch cho đến khi được xác nhận thành công bởi hệ thống ngân hàng.
+ BankSystemInterface: Tạo kết nối với hệ thống ngân hàng và gửi các giao dịch cho các nhân viên có phương thức thanh toán là chuyển khoản.
+ Employee: Lưu trữ thông tin về lương, các khoản khấu trừ, và phương thức nhận lương của nhân viên.
+ Timecard: Lưu trữ giờ làm việc của nhân viên làm theo giờ.
+ PurchaseOrder: Lưu trữ thông tin về đơn hàng của nhân viên hưởng hoa hồng, hỗ trợ tính toán tiền hoa hồng.
+ Paycheck: Lưu trữ chi tiết về phiếu lương cho mỗi nhân viên sau khi tính toán xong.
### 7.4. Thuộc tính và quan hệ
+ Employee
  - Thuộc tính: employeeID, name, paymentMethod, salary, hourlyRate, commissionRate, deductions, benefits
  - Quan hệ: Liên kết với PayrollProcessor để cung cấp dữ liệu tính lương, liên kết với PayrollDatabase để lưu trữ.
+ Timecard
  - Thuộc tính: employeeID, hoursWorked, date
  - Quan hệ: Cung cấp thông tin giờ làm việc cho PayrollProcessor.
+ PurchaseOrder
  - Thuộc tính: employeeID, orderAmount, orderDate
  - Quan hệ: Cung cấp thông tin đơn hàng cho PayrollProcessor để tính toán hoa hồng.
+ PayrollScheduler
  - Thuộc tính: scheduleDate
  - Quan hệ: Kích hoạt PayrollProcessor vào thời gian quy định.
+ PayrollProcessor
  - Thuộc tính: Không yêu cầu lưu trữ lâu dài; chỉ dùng để quản lý quy trình xử lý tính lương.
  - Quan hệ: Nhận thông tin từ Employee, Timecard, và PurchaseOrder; tạo và quản lý Paycheck.
+ BankTransactionManager
  - Thuộc tính: transactionStatus
  - Quan hệ: Làm việc với BankSystemInterface để gửi và theo dõi giao dịch chuyển khoản.
+ BankSystemInterface
  - Thuộc tính: connectionStatus
  - Quan hệ: Tạo kết nối và gửi giao dịch đến hệ thống ngân hàng bên ngoài.
+ Paycheck
  - Thuộc tính: employeeID, amount, payDate, paymentMethod
  - Quan hệ: Được lưu trữ hoặc in ra sau khi tính toán xong, dùng để ghi lại chi tiết lương của nhân viên.
# Viết code Java mô phỏng ca sử dụng Maintain Timecard.
*

import java.util.Date;
public class Timecard {
    private Date date;
    private String employeeId;
    private double hoursWorked;
    public Timecard(Date date, String employeeId, double hoursWorked) {
        this.date = date;
        this.employeeId = employeeId;
        this.hoursWorked = hoursWorked;
    }
    // Getters và Setters
    public Date getDate() {
        return date;
    }
    public String getEmployeeId() {
        return employeeId;
    }
    public double getHoursWorked() {
        return hoursWorked;
    }
    public void setHoursWorked(double hoursWorked) {
        this.hoursWorked = hoursWorked;
    }
}
import java.util.ArrayList;
import java.util.List;

public class TimecardService {
    private List<Timecard> timecards = new ArrayList<>();
    // Phương thức thêm thẻ chấm công
    public void addTimecard(Timecard timecard) {
        timecards.add(timecard);
    }
    // Phương thức sửa thẻ chấm công
    public void updateTimecard(String employeeId, Date date, double hoursWorked) {
        for (Timecard timecard : timecards) {
            if (timecard.getEmployeeId().equals(employeeId) && timecard.getDate().equals(date)) {
                timecard.setHoursWorked(hoursWorked);
                System.out.println("Timecard updated successfully for " + employeeId);
                return;
            }
        }
        System.out.println("Timecard not found for " + employeeId + " on date " + date);
    }
}
import java.util.Date;

public class Main {
    public static void main(String[] args) {
        TimecardService timecardService = new TimecardService();
        / Thêm một thẻ chấm công mới
        Timecard timecard1 = new Timecard(new Date(), "E001", 8);
        timecardService.addTimecard(timecard1);
        // Cập nhật thẻ chấm công
        timecardService.updateTimecard("E001", timecard1.getDate(), 7.5);
    }
}

*
