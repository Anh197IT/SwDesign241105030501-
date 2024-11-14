# Lab 3. Identify design elements
# Xác định các phần tử thiết kế của hệ thống “Payroll System”
## 1. Subsystem context diagrams (Hãy vẽ biểu đồ ngữ cảnh của các hệ thống con và giải thích.)
+  PayrollSystem (Hệ thống Lương)
  
  Interface IPayroll {
      calculateSalary(employeeId: String): Double
      processPay(employeeId: String)
      generatePayslip(employeeId: String)
      runPayroll()
  }
  
  + Chức năng:
    - Tính toán lương cho nhân viên
    - Xử lý thanh toán lương
    - Tạo phiếu lương
    - Chạy quy trình trả lương tự động
+ EmployeeManagementSystem (Hệ thống Quản lý Nhân viên)

Interface IEmployeeManagement {
    createEmployee(employeeData: EmployeeInfo): Employee
    updateEmployee(employeeId: String, data: EmployeeInfo)
    deleteEmployee(employeeId: String)
    getEmployeeInfo(employeeId: String): EmployeeInfo
    validateLogin(username: String, password: String): Boolean
}

 + Chức năng:
  - Tạo mới nhân viên
  - Cập nhật thông tin nhân viên
  - Xóa nhân viên
  - Truy xuất thông tin nhân viên
  - Xác thực đăng nhập
TimeManagementSystem (Hệ thống Quản lý Thời gian)
less

Copy
Interface ITimeManagement {
    submitTimecard(employeeId: String, timecardData: TimecardInfo)
    updateTimecard(timecardId: String, data: TimecardInfo)
    getTimecard(employeeId: String): TimecardInfo
    validateTimecard(timecardId: String): Boolean
}

Chức năng:
- Ghi nhận thời gian làm việc
- Cập nhật bảng chấm công
- Truy xuất dữ liệu chấm công
- Kiểm tra hợp lệ bảng chấm công
PurchaseOrderSystem (Hệ thống Quản lý Đơn hàng)
less

Copy
Interface IPurchaseOrder {
    createPurchaseOrder(orderData: OrderInfo): PurchaseOrder
    updatePurchaseOrder(orderId: String, data: OrderInfo)
    calculateCommission(employeeId: String): Double
    getPurchaseOrders(employeeId: String): List<PurchaseOrder>
}

Chức năng:
- Tạo đơn hàng mới
- Cập nhật đơn hàng
- Tính toán hoa hồng
- Truy xuất danh sách đơn hàng
Mối quan hệ giữa các hệ thống con:

PayrollSystem:
Sử dụng IEmployeeManagement để lấy thông tin nhân viên
Sử dụng ITimeManagement để lấy dữ liệu chấm công
Sử dụng IPurchaseOrder để tính hoa hồng
Kết nối với BankSystem để chuyển lương
Kết nối với Printer để in phiếu lương
EmployeeManagementSystem:
Cung cấp dữ liệu cho PayrollSystem
Lưu trữ dữ liệu vào ProjectDatabase
Xác thực người dùng qua Login
TimeManagementSystem:
Cung cấp dữ liệu chấm công cho PayrollSystem
Lưu trữ dữ liệu vào ProjectDatabase
Tương tác trực tiếp với Employee
PurchaseOrderSystem:
Cung cấp dữ liệu hoa hồng cho PayrollSystem
Tương tác với Commissioned Employee
Quản lý đơn hàng và tính hoa hồng
## 2. Analysis class to design element map (Hãy ánh xạ các lớp phân tích đến các phần tử thiết kế.)
## 3. Design element to owning package map (Hãy ánh xạ các phần tử thiết kế vào các gói.)
## 4. Architectural layers and their dependencies (Hãy vẽ biểu đồ mô tả các layers trong hệ thống và quan hệ giữa chúng.)



