# Lab 3. Identify design elements
# Xác định các phần tử thiết kế của hệ thống “Payroll System”
## 1. Subsystem context diagrams (Hãy vẽ biểu đồ ngữ cảnh của các hệ thống con và giải thích.)
A. Biểu đồ ngữ cảnh:
![Context Diagram](https://www.planttext.com/api/plantuml/png/VLHDZvim4BqZyH-yN7hQonvNgzM695Bt40K5UgYqbucP93J6HhQZ5bNzxnr_GCY7Si9YthmtyvxXmrZGzjIAD7cgSTT8PEMFlFnPLiiLUtipfwtfZSNs_JrDqiGS6zc1XfPnrNPAehIbxGKo8dYvMsP_quInNEaQzLm9fTbM03_wb_JSQtMITIY8Pd-mFGgXVgV9FoVtZIt2IECO9atEr5a1lLP2bBwKCJ2iA2VZU-b6MjGxuCYopuZtoCyYYapubcqdL8-u0WbxRDrsP-hbwY7tRM-GMQvkTQgclQzHFTQux0lyrHt-ugJv0GokdUjJTzQFxPcsHPFMOnJBFuIK8DYz97AGnubGNbxEezKlv7O15hR47sPPv5SOFqgeROBa1WNOHabpQ3hIet2VducRlRBCeAmDww1tJh2QcBC1K6mSe7DyXcdibBPcBBeKgRf7gc6CxBAzcY0i6Sv1rrS2wpE2DcWROsZ80PCcJiF15hcVr2gD4x56xXJ1gdkWGIyB-yyulGuH0VT6f0duT-DLZLUp60lnZi_gjf71pDbO2mdDXU97NohdOTmYxZsUQKDQTXOD6uu5dShvS4eJgImoxRvQfdRkqwD5leEi1MrYG83k6GV1Jo74BqcbCR5EAuxaczndrqGned3HpyPzIUUSRZtPJLDrsJGO6KJ1Mhek83dUzCKiXxukVWBC_x1CQ3zdR7mm7qH6Fxp_)
B. Mô tả hệ thống con

+  PayrollSystem (Hệ thống Lương)
  
    + Interface IPayroll {
      -   calculateSalary(employeeId: String): Double
      -   processPay(employeeId: String)
      -   generatePayslip(employeeId: String)
      -   runPayroll()
    }
    + Chức năng:
      - Tính toán lương cho nhân viên
      - Xử lý thanh toán lương
      - Tạo phiếu lương
      - Chạy quy trình trả lương tự động
+ EmployeeManagementSystem (Hệ thống Quản lý Nhân viên)

   + Interface IEmployeeManagement {
     -   createEmployee(employeeData: EmployeeInfo): Employee
     -   updateEmployee(employeeId: String, data: EmployeeInfo)
     -   deleteEmployee(employeeId: String)
     -   getEmployeeInfo(employeeId: String): EmployeeInfo
     -   validateLogin(username: String, password: String): Boolean
    }

  + Chức năng:
    - Tạo mới nhân viên
    - Cập nhật thông tin nhân viên
    - Xóa nhân viên
    - Truy xuất thông tin nhân viên
    - Xác thực đăng nhập
+ TimeManagementSystem (Hệ thống Quản lý Thời gian)

    + Interface ITimeManagement {
      -  submitTimecard(employeeId: String, timecardData: TimecardInfo)
      -  updateTimecard(timecardId: String, data: TimecardInfo)
      -  getTimecard(employeeId: String): TimecardInfo
      -  validateTimecard(timecardId: String): Boolean
    }

    + Chức năng:
      - Ghi nhận thời gian làm việc
      - Cập nhật bảng chấm công
      - Truy xuất dữ liệu chấm công
      - Kiểm tra hợp lệ bảng chấm công
+ PurchaseOrderSystem (Hệ thống Quản lý Đơn hàng)

    + Interface IPurchaseOrder {
      -  createPurchaseOrder(orderData: OrderInfo): PurchaseOrder
      -  updatePurchaseOrder(orderId: String, data: OrderInfo)
      -  calculateCommission(employeeId: String): Double
      -  getPurchaseOrders(employeeId: String): List<PurchaseOrder>
    }

    + Chức năng:
      - Tạo đơn hàng mới
      - Cập nhật đơn hàng
      - Tính toán hoa hồng
      - Truy xuất danh sách đơn hàng

C. Mối quan hệ giữa các hệ thống con

+ PayrollSystem:
  - Sử dụng IEmployeeManagement để lấy thông tin nhân viên
  - Sử dụng ITimeManagement để lấy dữ liệu chấm công
  - Sử dụng IPurchaseOrder để tính hoa hồng
  - Kết nối với BankSystem để chuyển lương
  - Kết nối với Printer để in phiếu lương
+ EmployeeManagementSystem:
  - Cung cấp dữ liệu cho PayrollSystem
  - Lưu trữ dữ liệu vào ProjectDatabase
  - Xác thực người dùng qua Login
+ TimeManagementSystem:
  - Cung cấp dữ liệu chấm công cho PayrollSystem
  - Lưu trữ dữ liệu vào ProjectDatabase
  - Tương tác trực tiếp với Employee
+ PurchaseOrderSystem:
  - Cung cấp dữ liệu hoa hồng cho PayrollSystem
  - Tương tác với Commissioned Employee
  - Quản lý đơn hàng và tính hoa hồng
## 2. Analysis class to design element map (Hãy ánh xạ các lớp phân tích đến các phần tử thiết kế.)

  | Analysis Classes | Design Elements |
  | :---| ---:|
  |LoginForm | LoginForm |
  |MaintainTimecardForm | MainEmployeeForm | 
  || TimecardForm |
  || MainApplicationForm |
  |TimecardController | TimecardController |
  |SystemClockInterface | SystemClockInterface |
  |PayrollController | PayrollController |
  |Paycheck | PayCheck |

## 3. Design element to owning package map (Hãy ánh xạ các phần tử thiết kế vào các gói.)

  | Design Element	| "Owning" Package |
  | :---| ---:|
  |LoginForm |	Middleware::Security:GUI Framework |
  |MainEmployeeForm |	Applications::Employee Activities |
  |TimecardForm |	Middleware::Security:GUI Framework |
  |MainApplicationForm |	Applications::Employee Activities |
  |TimecardController |	Applications::Payroll |
  |SystemClockInterface |	Applications::Payroll |
  |PayrollController |	Applications::Payroll |
  |Paycheck |	Business Services::Payroll Artifacts |

## 4. Architectural layers and their dependencies (Hãy vẽ biểu đồ mô tả các layers trong hệ thống và quan hệ giữa chúng.)
![Package Diagram](https://www.planttext.com/api/plantuml/png/XLFRJkCm47sFb7yOyR1l_0125Msv2Ab8IDrzMC4A3SvGhDYUQEnIHQZ_ldOR1xV0RbvYpyoPCvVZ2nzGmjgQkgehtshNeQ05nRPZHox0Urr1_6QesfNmsZLpDYomqAlNy9kCuSqGmDAGx9qp4wFhQfjoTl68AuAJytE3FSbaykZkTDCOsg3GsTcIr5fqw1_TpQzRk8xaj65fJm0zs34kb_6mu9Lsropsps3ugIqfb6QmVSivxJgZ5GRDpk-IuuSXPnznLxOpt1F1L0NzfeEcFOPizuIZASDsTToXTXbMr3Vw2lx2lTt_ZkZliHSsPaVPxSy7NBddERkGd2GbsxBtWUpSi6flNI1vGKMbVyZ-2Rpzn_HcQwyTUGzBaZUjXd4yP-ln_0OAc4hGaJuC4y-tWsPYh7ebrHvLKUp-z7HIRgkkojKbPwuZuHm70adg17uf59Io9uNDix8zB59tTKMkWOJwZ3uWZHBFxIOHgl_3Fye2kCI0y6CStrVWYtY93_4l)
  + Quan hệ giữa các layer:
    - Middleware phụ thuộc vào Application
    - Application phụ thuộc vào Business Services
    - Mỗi layer chỉ giao tiếp với layer ngay dưới nó
    - Tuân thủ nguyên tắc phân tầng và dependency inversion


