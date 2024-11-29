# Subsystem design in Payroll
# Run Payroll
## Distribute subsystem behavior to subsystem elements. 
+ PayrollController:
  - Điều khiển luồng chính của quy trình tính lương
  - Tạo séc lương (createWithAmount)
  - Kiểm tra ngày trả lương (isPayday)
  - Lấy số tiền lương (getPayAmount)
  - Quản lý thông tin ngân hàng (getBankInfo)
  - Gửi tiền (deposit)
+ IBankSystem:
  - Xử lý giao dịch ngân hàng (sendTransaction)
  - Tương tác với hệ thống ngân hàng bên ngoài
+ IPrintService:
  - In ấn séc lương và các tài liệu liên quan
  - Định dạng và xử lý dữ liệu in
## Document subsystem elements.
+ SystemClock: Quản lý thời gian hệ thống
+ Employee: Lưu trữ thông tin nhân viên
+ Paycheck: Đại diện cho séc lương
+ PurchaseOrder: Quản lý đơn hàng
+ Timecard: Quản lý thời gian làm việc
## Describe subsystem dependencies.
+ PayrollController phụ thuộc vào:
  - Employee để lấy thông tin nhân viên
  - IBankSystem để xử lý giao dịch
  - IPrintService để in séc lương
  - Paycheck để tạo séc
+ Employee phụ thuộc vào:
  - Timecard để lấy thông tin chấm công
  - PurchaseOrder để lấy thông tin đơn hàng
+ IBankSystem phụ thuộc vào:
  - Bank System bên ngoài để hoàn tất giao dịch
# Maintain Timecard
## Distribute subsystem behavior to subsystem elements. 
+ TimecardForm:
  - Hiển thị giao diện nhập liệu bảng chấm công
  - Xử lý các tương tác từ người dùng
  - Gửi yêu cầu tới TimecardController
+ TimecardController:
  - Điều khiển luồng xử lý bảng chấm công
  - Quản lý việc lấy và cập nhật dữ liệu
  - Tương tác với Timecard và Database
+Timecard:
  - Lưu trữ thông tin chấm công
  - Cung cấp các phương thức truy xuất và cập nhật dữ liệu
## Document subsystem elements. 
+ Employee: Người dùng hệ thống
+ TimecardForm: Giao diện người dùng
+ TimecardController: Bộ điều khiển
+ Timecard: Đối tượng dữ liệu
+ IProjectManagementDatabase: Cơ sở dữ liệu dự án
## Describe subsystem dependencies.
+ TimecardForm phụ thuộc vào:
  - TimecardController để xử lý logic
  - Employee để nhận input
+ TimecardController phụ thuộc vào:
  - Timecard để lưu trữ dữ liệu
  - IProjectManagementDatabase để truy xuất thông tin
+ Luồng xử lý chính:
  - Maintain timecard
  - Get current timecard
  - Display timecard
  - Get charge codes
  - Enter hours for charge numbers
  - Update timecard
  - Save timecard
# Login
## Distribute subsystem behavior to subsystem elements. 
+ MainEmployeeForm:
  - Khởi tạo quá trình đăng nhập
  - Hiển thị các chức năng sau khi đăng nhập
  - Lưu trữ context người dùng
+ LoginForm:
  - Hiển thị giao diện đăng nhập
  - Xử lý nhập liệu từ người dùng
  - Gọi các hàm xác thực
+ SecureUser/Employee Session:
  - Xác thực thông tin đăng nhập
  - Thiết lập context bảo mật
  - Quản lý phiên làm việc
## Document subsystem elements. 
+ Employee: Actor chính (người dùng)
+ MainEmployeeForm: Form chính của hệ thống
+ LoginForm: Giao diện đăng nhập
+ SecureUser: Đối tượng quản lý bảo mật
+ Employee Session: Quản lý phiên làm việc
## Describe subsystem dependencies.
+ MainEmployeeForm phụ thuộc vào:
  - LoginForm để thực hiện đăng nhập
  - SecureUser để lấy context bảo mật
+ LoginForm phụ thuộc vào:
  - SecureUser để xác thực người dùng
  - Employee Session để tạo phiên làm việc
+ Luồng xử lý chính:
  - start()
  - open()
  - enterUserName()
  - enterPassword()
  - loginUser()
  - validateUserIDPassword()
  - setupSecurityContext()
  - getUserContext()
  - displayAvailOperations()
# PayrollDBManager
## Distribute subsystem behavior to subsystem elements.
+ Hành vi "Shutdown":
  - Payroll Application Controller: Gọi phương thức shutdown() trên PayrollDBManager.
  - PayrollDBManager: Gọi phương thức close() trên PayrollDB (Database).
  - PayrollDB (Database): Gọi phương thức terminate() trên Session.
+ Hành vi "Save Paycheck":
  - Any PayrollDB Client: Gọi phương thức save(Paycheck, Employee) trên PayrollDBManager.
  - PayrollDBManager:
    - Bắt đầu một giao dịch bằng phương thức begin().
    - Lấy Employee ID bằng phương thức get Employee ID().
    - Truy xuất Employee bằng phương thức get(EmployeeID).
    - Nếu Employee không tồn tại, thêm Employee ID và Employee vào Map bằng phương thức put(EmployeeID, Employee).
    - Nếu Employee tồn tại, thêm Paycheck vào bằng phương thức add(Paycheck).
  - PayrollDBManager: Kết thúc giao dịch bằng phương thức commit().
## Document subsystem elements. 
+ Payroll Application Controller: Quản lý các thao tác chính trên PayrollDBManager.
+ PayrollDBManager:
  - Quản lý giao dịch và lưu trữ dữ liệu bảng chấm công.
  - Giao tiếp với PayrollDB để thực hiện các thao tác lưu trữ và truy xuất.
+ PayrollDB (Database): Lưu trữ và quản lý phiên bản mới nhất của dữ liệu Employee và Paycheck.
+ Session: Quản lý phiên làm việc với cơ sở dữ liệu.
## Describe subsystem dependencies.
+ Payroll Application Controller: Phụ thuộc vào PayrollDBManager để thực hiện các thao tác shutdown và lưu bảng chấm công.
+ PayrollDBManager:
  - Phụ thuộc vào PayrollDB để truy xuất và lưu trữ dữ liệu Employee và Paycheck.
  - Phụ thuộc vào Session để quản lý các phiên làm việc với cơ sở dữ liệu.
+ PayrollDB (Database): Phụ thuộc vào Session để thực hiện các thao tác terminate trong quá trình shutdown.
