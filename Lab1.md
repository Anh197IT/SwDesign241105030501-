# LAB1 - PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích kiến trúc
### a. Phân tích Kiến trúc
Đối với hệ thống Payroll System, kiến trúc Layered Architecture (Kiến trúc phân tầng) là một lựa chọn phù hợp. Lý do cho việc lựa chọn này là vì nó mang lại sự tách biệt rõ ràng giữa các chức năng, giúp dễ dàng duy trì và mở rộng hệ thống. Hệ thống này có thể được chia thành các lớp sau:

UI Layer (Lớp giao diện người dùng): Là điểm tiếp xúc trực tiếp với người dùng, cung cấp giao diện để nhân viên có thể nhập thông tin thẻ chấm công và chọn phương thức thanh toán. Nó cũng giúp người quản trị dễ dàng quản lý thông tin liên quan đến nhân viên.

Service Layer (Lớp dịch vụ): là nơi thực hiện tất cả các nghiệp vụ chính của hệ thống. Nó đảm bảo rằng các thông tin nhập vào từ UI đều được xác thực, như đảm bảo số giờ làm việc không vượt quá mức giới hạn, hay thông tin về phương thức thanh toán là hợp lệ.

Data Access Layer (Lớp truy cập dữ liệu): Lớp này giúp đảm bảo rằng hệ thống có thể tương tác hiệu quả với các cơ sở dữ liệu hiện tại, bao gồm cả cơ sở dữ liệu quản lý dự án (Project Management Database) và cơ sở dữ liệu nhân viên. Nó giúp trích xuất và lưu trữ dữ liệu một cách tối ưu, giúp giảm thiểu lỗi và tăng hiệu năng hệ thống.

External Systems (Các hệ thống bên ngoài): Hệ thống ngân hàng sẽ thực hiện các giao dịch chuyển tiền lương qua tài khoản ngân hàng. Hệ thống đồng hồ sẽ giúp tự động hóa quy trình chạy bảng lương vào thời điểm xác định.
### b. Biểu đồ package:
![Package Diagram](https://www.planttext.com/?text=VLJFRfim6B_p59yuhPhw0ZrCxM1Qgh9gLLZldrmBMoKs1JiAgdhOQSzHJJr6spdHJfNw7hp9FcX2JGmzHC4slxyVS5ePB8rTv45G8Bl5Z4FuunmIh7aPmdq0m7AiAlWgKSUIgqk1Qad_tH70Hn2qI8LCRHq9JLUeHAfHVJZQdMTMVaQLHG8NaLPPj_z0Fu_vog9AIzaJtz4wgLCYpLBPwLxJNJlyWsDtpikbPDpt74ichcrlgMTU8Kk5PT-5RRdfodVDi215irSVta3YGmatOA-IO-q5dox43HIZGJXZZ9E05oejgMaiOfj8RlUjkA8H3KDoCoZCYJII-g3RSQcfZFvfhvXRVz-XZ_HSlwAlkb77zcmGv1ksEoFzV5aPNYhCOLvNXYygjvuPxsPscQ6QeUDqPHDgnjPSNGZTFcYKN_A2sDrf4dAcTnHlLhXAQCnfYObzZK4Gztte9d1y_Cbxu4uWh9hj6cwQxPFAmlT0WtgdSFjNf8MDFmU4lBFDvhU2_FbV60I7Zjv56Ze0rcpMHHYCkFAmXvxpPlDKjwR_G2wRxIyxIJCw-hs39T6e2U-7uoLCHar9C2JuKq6t8Dd182T6S_kyPWA4RZQF1an9hK7-ylVbiMtybAkRzgFu7m00%5D(https://www.planttext.com/)
## 2. Cơ chế phân tích
Xác thực và ủy quyền: Đảm bảo chỉ người dùng hợp lệ (nhân viên, quản trị viên) mới có thể truy cập hệ thống thông qua đăng nhập và phân quyền dựa trên vai trò.

Lưu trữ và truy xuất dữ liệu an toàn: Mã hóa dữ liệu nhạy cảm (như thông tin tài khoản ngân hàng) và áp dụng kiểm soát truy cập để bảo mật dữ liệu.

Kiểm tra và xác thực dữ liệu: Đảm bảo đầu vào hợp lệ, chẳng hạn số giờ làm việc không vượt quá giới hạn cho phép và phương thức thanh toán phải hợp lệ.

Tự động hóa xử lý: Lập lịch tự động tính lương và gửi tiền vào tài khoản ngân hàng theo lịch trình hệ thống.

Xử lý lỗi và khôi phục: Quản lý lỗi hiệu quả, ghi lại nhật ký hệ thống và khôi phục giao dịch nếu có lỗi xảy ra để bảo toàn dữ liệu.

Quản lý phiên làm việc: Bảo mật phiên đăng nhập với cơ chế timeout và mã hóa phiên để tránh bị tấn công.

Tích hợp hệ thống ngân hàng: Sử dụng API ngân hàng để tự động thực hiện các giao dịch chuyển khoản cho nhân viên.

Kết quả mong đợi: Dựa trên các cơ chế phân tích, hệ thống Payroll System sẽ đạt được các yêu cầu về bảo mật, hiệu năng, và tính chính xác. Các cơ chế này sẽ giúp: Bảo vệ dữ liệu nhạy cảm của nhân viên và giao dịch tài chính. Đảm bảo các quy trình nghiệp vụ được thực hiện một cách trơn tru và tự động hóa. Đảm bảo khả năng phục hồi và xử lý lỗi khi có sự cố xảy ra.
## 3. Phân tích ca sử dụng 
3.1.Xác định các lớp phân tích:

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
