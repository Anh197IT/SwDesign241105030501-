# LAB1 - PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích kiến trúc
### 1.1. Phân tích Kiến trúc
Đối với hệ thống Payroll System, kiến trúc Layered Architecture (Kiến trúc phân tầng) là một lựa chọn phù hợp. Lý do cho việc lựa chọn này là vì nó mang lại sự tách biệt rõ ràng giữa các chức năng, giúp dễ dàng duy trì và mở rộng hệ thống. Hệ thống này có thể được chia thành các lớp sau:

UI Layer (Lớp giao diện người dùng): Là điểm tiếp xúc trực tiếp với người dùng, cung cấp giao diện để nhân viên có thể nhập thông tin thẻ chấm công và chọn phương thức thanh toán. Nó cũng giúp người quản trị dễ dàng quản lý thông tin liên quan đến nhân viên.

Service Layer (Lớp dịch vụ): là nơi thực hiện tất cả các nghiệp vụ chính của hệ thống. Nó đảm bảo rằng các thông tin nhập vào từ UI đều được xác thực, như đảm bảo số giờ làm việc không vượt quá mức giới hạn, hay thông tin về phương thức thanh toán là hợp lệ.

Data Access Layer (Lớp truy cập dữ liệu): Lớp này giúp đảm bảo rằng hệ thống có thể tương tác hiệu quả với các cơ sở dữ liệu hiện tại, bao gồm cả cơ sở dữ liệu quản lý dự án (Project Management Database) và cơ sở dữ liệu nhân viên. Nó giúp trích xuất và lưu trữ dữ liệu một cách tối ưu, giúp giảm thiểu lỗi và tăng hiệu năng hệ thống.

External Systems (Các hệ thống bên ngoài): Hệ thống ngân hàng sẽ thực hiện các giao dịch chuyển tiền lương qua tài khoản ngân hàng. Hệ thống đồng hồ sẽ giúp tự động hóa quy trình chạy bảng lương vào thời điểm xác định.
### 1.2. Biểu đồ package:
![Package Diagram](https://www.planttext.com/api/plantuml/png/VLJFRfim6B_p59yuhPhw0ZrCxM1Qgh9gLLZldrmBMoKs1JiAgdhOQSzHJJr6spdHJfNw7hp9FcX2JGmzHC4slxyVS5ePB8rTv45G8Bl5Z4FuunmIh7aPmdq0m7AiAlWgKSUIgqk1Qad_tH70Hn2qI8LCRHq9JLUeHAfHVJZQdMTMVaQLHG8NaLPPj_z0Fu_vog9AIzaJtz4wgLCYpLBPwLxJNJlyWsDtpikbPDpt74ichcrlgMTU8Kk5PT-5RRdfodVDi215irSVta3YGmatOA-IO-q5dox43HIZGJXZZ9E05oejgMaiOfj8RlUjkA8H3KDoCoZCYJII-g3RSQcfZFvfhvXRVz-XZ_HSlwAlkb77zcmGv1ksEoFzV5aPNYhCOLvNXYygjvuPxsPscQ6QeUDqPHDgnjPSNGZTFcYKN_A2sDrf4dAcTnHlLhXAQCnfYObzZK4Gztte9d1y_Cbxu4uWh9hj6cwQxPFAmlT0WtgdSFjNf8MDFmU4lBFDvhU2_FbV60I7Zjv56Ze0rcpMHHYCkFAmXvxpPlDKjwR_G2wRxIyxIJCw-hs39T6e2U-7uoLCHar9C2JuKq6t8Dd182T6S_kyPWA4RZQF1an9hK7-ylVbiMtybAkRzgFu7m00)
## 2. Cơ chế phân tích
Các cơ chế phân tích:

- Cơ chế phân tích xác thực và ủy quyền: Đảm bảo chỉ người dùng hợp lệ (nhân viên, quản trị viên) mới có thể truy cập hệ thống thông qua đăng nhập và phân quyền dựa trên vai trò.
- Cơ chế phân tích lưu trữ và truy xuất dữ liệu an toàn: Mã hóa dữ liệu nhạy cảm (như thông tin tài khoản ngân hàng) và áp dụng kiểm soát truy cập để bảo mật dữ liệu.
- Cơ chế phân tích kiểm tra và xác thực dữ liệu: Đảm bảo đầu vào hợp lệ, chẳng hạn số giờ làm việc không vượt quá giới hạn cho phép và phương thức thanh toán phải hợp lệ.
- Cơ chế phân tích tự động hóa xử lý: Lập lịch tự động tính lương và gửi tiền vào tài khoản ngân hàng theo lịch trình hệ thống.
- Cơ chế phân tích xử lý lỗi và khôi phục: Quản lý lỗi hiệu quả, ghi lại nhật ký hệ thống và khôi phục giao dịch nếu có lỗi xảy ra để bảo toàn dữ liệu.
- Cơ chế phân tích quản lý phiên làm việc: Bảo mật phiên đăng nhập với cơ chế timeout và mã hóa phiên để tránh bị tấn công.
- Cơ chế phân tích tích hợp hệ thống ngân hàng: Sử dụng API ngân hàng để tự động thực hiện các giao dịch chuyển khoản cho nhân viên.

Kết quả mong đợi: Dựa trên các cơ chế phân tích, hệ thống Payroll System sẽ đạt được các yêu cầu về bảo mật, hiệu năng, và tính chính xác. Các cơ chế này sẽ giúp: Bảo vệ dữ liệu nhạy cảm của nhân viên và giao dịch tài chính. Đảm bảo các quy trình nghiệp vụ được thực hiện một cách trơn tru và tự động hóa. Đảm bảo khả năng phục hồi và xử lý lỗi khi có sự cố xảy ra.
## 3. Phân tích ca sử dụng 
### 3.1. Xác định các lớp phân tích:

A. Boundary Classes (Lớp biên):
- PaymentFormUI: Giao diện nhập liệu phương thức thanh toán
- PaymentDisplayUI: Giao diện hiển thị thông tin thanh toán

B. Control Classes (Lớp điều khiển):
- PaymentController: Xử lý logic nghiệp vụ thanh toán

C. Entity Classes (Lớp thực thể):

- Employee: Thông tin nhân viên
- Payment: Thông tin thanh toán
- DirectDeposit: Thông tin chuyển khoản
- MailDelivery: Thông tin gửi qua thư

### 3.2. Biểu đồ Sequence

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/fPJBIiD058RtynHdgOk-G1TIQBtXXIuYk1tJeJEOdedJYPYr2n4Hz0siBaH1K124174HwNlCcpYJ6jjuILlC9fnmvllF-VyaZRwcIaUzW13gQwbWkHS6CcQCxCa8ErJ5qAPnZw5UaQgtiqvyYLh9e7ZQ79K1KyHMGd-r5sLBAERh5WjbNtmztA8YQB50738L4r98GcsfB5O7dvlq7Djy-3WSODUprPtlSOhSaza05nP9gNy2C9wh3aScVTZCNYieX0OQchcMlKMnIOyHzhaqoGq2ThDh19vTOPU0lNue_39tdDr7JPFSHXxFdgsam6r7MNCGg-Sm5LiZDyb3-FVHcPRE1hxRzCcVoYblKWgi3jea0rbuiZ6ov0UeT0PguubiWcwLRRUGhWg01NrM9B1gyn9m457O6pv6y7ufJ7g2ytl_Vc7IC-gWfpdIi_gpcbznTZxt9q1Lhaz-4P-cVzUTRFctntatWbPkHj3296_XL8VhDWkJl7mJ6Q6ydEJb82l6i4F8B6bnuLuiHphRjQQDO6xQXaNO_z87)

### 3.3. Nhiệm vụ từng lớp phân tích

A. Boundary Classes:

PaymentFormUI:
- Hiển thị form chọn phương thức thanh toán
- Thu thập thông tin từ người dùng
- Hiển thị thông báo kết quả

B. Control Classes:

PaymentController:
- Xử lý logic nghiệp vụ
- Kiểm tra tính hợp lệ của dữ liệu
- Điều phối luồng xử lý giữa UI và entity

C. Entity Classes:

Employee:
- Lưu trữ thông tin nhân viên
- Quản lý liên kết với phương thức thanh toán
Payment:
- Lưu trữ thông tin phương thức thanh toán
- Quản lý trạng thái thanh toán
DirectDeposit:
- Lưu trữ thông tin tài khoản ngân hàng
- Xử lý thanh toán qua chuyển khoản
MailDelivery:
- Lưu trữ thông tin địa chỉ gửi thư
- Xử lý thanh toán qua đường bưu điện
### 3.4 Xác Xác định một số thuộc tính và quan hệ giữa các lớp phân tích

A. Thuộc tính chính:
- Employee: id, name, status
- Payment: id, type, status
- DirectDeposit: bankInfo, accountNo
- MailDelivery: address, zipCode
- PaymentController: paymentType, validationStatus
- PaymentUI: displayMode, formData
B. Quan hệ giữa các lớp:
- Employee 1 --- 1 Payment (Mỗi nhân viên có một phương thức thanh toán)
- Payment 1 --- 0..1 DirectDeposit (Payment có thể có DirectDeposit)
- Payment 1 --- 0..1 MailDelivery (Payment có thể có MailDelivery)
- PaymentUI --- PaymentController (UI phụ thuộc Controller)
- PaymentController --- Entity Classes (Controller điều khiển các entity)
### 3.5 Kết quả mong đợi là các biểu đồ lớp mô tả lớp phân tích và giải thích

