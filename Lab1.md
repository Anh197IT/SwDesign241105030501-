# LAB1 - PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG
## 1. Phân tích kiến trúc
### 1.1. Phân tích Kiến trúc
Đối với hệ thống Payroll System, kiến trúc Layered Architecture (Kiến trúc phân tầng) là một lựa chọn phù hợp. Lý do cho việc lựa chọn này là vì nó mang lại sự tách biệt rõ ràng giữa các chức năng, giúp dễ dàng duy trì và mở rộng hệ thống. Hệ thống này có thể được chia thành các lớp sau:
- UI Layer (Lớp giao diện người dùng): Là điểm tiếp xúc trực tiếp với người dùng, cung cấp giao diện để nhân viên có thể nhập thông tin thẻ chấm công và chọn phương thức thanh toán. Nó cũng giúp người quản trị dễ dàng quản lý thông tin liên quan đến nhân viên.
- Service Layer (Lớp dịch vụ): là nơi thực hiện tất cả các nghiệp vụ chính của hệ thống. Nó đảm bảo rằng các thông tin nhập vào từ UI đều được xác thực, như đảm bảo số giờ làm việc không vượt quá mức giới hạn, hay thông tin về phương thức thanh toán là hợp lệ.
- Data Access Layer (Lớp truy cập dữ liệu): Lớp này giúp đảm bảo rằng hệ thống có thể tương tác hiệu quả với các cơ sở dữ liệu hiện tại, bao gồm cả cơ sở dữ liệu quản lý dự án (Project Management Database) và cơ sở dữ liệu nhân viên. Nó giúp trích xuất và lưu trữ dữ liệu một cách tối ưu, giúp giảm thiểu lỗi và tăng hiệu năng hệ thống.
- External Systems (Các hệ thống bên ngoài): Hệ thống ngân hàng sẽ thực hiện các giao dịch chuyển tiền lương qua tài khoản ngân hàng. Hệ thống đồng hồ sẽ giúp tự động hóa quy trình chạy bảng lương vào thời điểm xác định.
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
## 3. Phân tích ca sử dụng Payment
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

- PaymentFormUI:
  + Hiển thị form chọn phương thức thanh toán
  + Thu thập thông tin từ người dùng
  + Hiển thị thông báo kết quả

B. Control Classes:

- PaymentController:
  + Xử lý logic nghiệp vụ
  + Kiểm tra tính hợp lệ của dữ liệu
  + Điều phối luồng xử lý giữa UI và entity

C. Entity Classes:

- Employee:
  + Lưu trữ thông tin nhân viên
  + Quản lý liên kết với phương thức thanh toán
- Payment:
  + Lưu trữ thông tin phương thức thanh toán
  + Quản lý trạng thái thanh toán
- DirectDeposit:
  + Lưu trữ thông tin tài khoản ngân hàng
  + Xử lý thanh toán qua chuyển khoản
- MailDelivery:
  + Lưu trữ thông tin địa chỉ gửi thư
  + Xử lý thanh toán qua đường bưu điện
### 3.4 Xác Xác định một số thuộc tính và quan hệ giữa các lớp phân tích
- Lớp Employee: id, name, status: trạng thái
  + Quan hệ 1-1 với Payment: Mỗi nhân viên có một phương thức thanh toán
  + Chứa thông tin cơ bản của nhân viên
  + Thuộc tính status để theo dõi trạng thái nhân viên

- Lớp Payment:id, type, status: trạng thái thanh toán
  + Là lớp trung tâm quản lý thông tin thanh toán
  + Quan hệ 1-0..1 với DirectDeposit và MailDelivery
  + Enum PaymentType xác định loại thanh toán
  + Theo dõi lịch sử thay đổi qua dateModified

- Lớp DirectDeposit: bankInfo: thông tin ngân hàng, accountNo: số tài khoản
  + Chứa thông tin chi tiết tài khoản ngân hàng
  + Phương thức validateBankDetails() đảm bảo tính hợp lệ
  + Độc lập với MailDelivery

- Lớp MailDelivery: address: địa chỉ, zipCode: mã bưu điện
  + Quản lý thông tin địa chỉ gửi thư
  + Phương thức validateAddress() kiểm tra địa chỉ
  + Độc lập với DirectDeposit

- Lớp PaymentController: paymentType: loại thanh toán, validationStatus: trạng thái xác thực
  + Điều phối luồng xử lý giữa UI và Entity
  + Xử lý logic nghiệp vụ và validation
  + Kết nối với các lớp thực thể

- Lớp PaymentFormUI và PaymentDisplayUI: displayMode: chế độ hiển thị, formData: dữ liệu biểu mẫu
  + Tách biệt giao diện nhập liệu và hiển thị
  + Phụ thuộc vào PaymentController
  + Không trực tiếp tương tác với Entity

### 3.5 Kết quả mong đợi
A. Biểu đồ lớp phân tích:

![Class Diagram](https://www.planttext.com/api/plantuml/png/fPH1QzH05CVl-HIFlQZ85htkGMet7dfOALG_m3IPpGoTl8d9P26A1_7Gas3n8CLBLn5HA2tqrZccxFUOR-BBRdQJjAa8FILlPlw_z-R_NhAT6PQQF5RU0_3vL2A7e9m7e9pzbi2iF0KZScTF0Z3b6Ge8dFt5813b5KPUe5YMmOiuKRhW7Dvv08zbE89zaqhQfWXPpDinPJDvjbbvxzMCFLR474qVmXG98Ue3hoZeuT1Ao0oVw51E9IUvJr53zsNA0-FpH6Uopd70y70NfxgDO46WSpGlEuipfcJ5tY61pmsJAdluQ0GxMYlEiCaneHsVApdZQR5AmS8mvLcdoBSo6UkGz_6VhqxtiklBZpMQL2l5qrM2fF7aba4rLchS_xVbhtTNi51cYMB5v4PvKvt6P2PhwxkJ4ZjxBE5DpX24iqSGIMVFMMkAlCs039uEO3XSFjOD7y5WuknN2IZAxmWpMVv1qbvMs1C3YLXSBEOOqHGw-vk6K30QGgFBEGwyDMEDVRArHM_TPXD_JD9F11LvuUn7X4EXtTKF18ogZA8ynUWkLgUf3IfozcnvPJXONEHmVKnNFceA8ak7msSzNIF27X5-hh-fZQ9rfb9k32F1zMU2VyYfQhciNf7o2naIaikWgiJvNPYMn_UWtFBp7goRVluNojlc65P_gBy0)

B. Giải thích các quan hệ:
- Employee - Payment (1-1): đảm bảo mỗi nhân viên có một phương thức thanh toán duy nhất.
- Payment - DirectDeposit/MailDelivery (1-0..1): đảm bảo chỉ một phương thức thanh toán được chọn (chuyển khoản hoặc gửi qua thư).
- PaymentUI - PaymentController: UI phụ thuộc Controller để xử lý logic và xác thực nghiệp vụ.
- PaymentController - Entities: Controller kết nối và điều phối luồng dữ liệu giữa UI và các lớp thực thể, tách biệt giao diện người dùng khỏi logic nghiệp vụ và dữ liệu hệ thống.
## 4. Phân tích ca sử dụng Maintain Timecard

### 4.1. Xác định các lớp phân tích:

A. Boundary Classes:
- TimecardFormUI: Giao diện nhập liệu thẻ chấm công
- TimecardDisplayUI: Giao diện hiển thị thông tin thẻ chấm công

B. Control Classes:
- TimecardController: Xử lý logic nghiệp vụ thẻ chấm công

C. Entity Classes:
- Employee: Thông tin nhân viên
- Timecard: Thông tin thẻ chấm công
- TimeEntry: Chi tiết giờ làm theo ngày và số phí
- ChargeCode: Thông tin số hiệu phí

### 4.2 Biểu đồ sequence

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/ZLMzZjGm4Exp5FC2h0Zt1obE9-qT4k94jJn0IAoDTNOSSivAMo8AQWf4WH2BLWW9QGN5LKb1ONJluJUvSPRinbadIXTFdE_xPkQRoSMj37DPSEQ5aHGvNF6CYIKXNePX6j4iJ2NCA2THcCVFHSvVlt2-cefKve8naZjV7mIlyFhIYawJC9-JgOY9vpKguD5vXpm0VmAl4brkCf29kald86aA4KP-S8XCm6H25w4aNTsUVMw3x-K7y6G2BwcktdEGUGYnhdu3m_E70lvzrENF0XPg9Gv9MXNm3cDzP4UZo5nuZj8S8vWk_qfuM-Xo3JSxO2ycWtf39k6onPteQfq1msSFO5pLJYOmq-LtWLtHPMKr1BYklb146j80qA9oros0KqmGjNsZ87kuN2nRR2P4XYOJHird2kbShPR0r8h3mYGTuPKX0RLX0pXhqemI547hQi_n-wyrL8rXyMzzRi8x_3faOFUE3-3f1AunYsNRr5oj8KlKnaPjpOc9xuyxI_oN-WobviO72rszwyLjEQE3t1NSqtZ_iSNJNvUE1nsL6MgzZtC_IzGltij0qdYSYtoSy9dQf0cwgFg4HR5Wcdlz2HyP3nn-w9YnCNeiQ9pWw_i_XTlO8xU0VsAl0OQ0RdbzuzTCEe8tcnXXJ-i661EzKVNigHMMS2kEi5jYRP2RxSt1HMB3dzdmp4ofPthgMbxDHh_02_ZpUW00)

### 4.3. Nhiệm vụ từng lớp phân tích

A. Boundary Classes:
- TimecardFormUI:
  + Hiển thị form nhập liệu thẻ chấm công
  + Thu thập thông tin giờ làm và số phí
  + Hiển thị danh sách số phí khả dụng
  + Hiển thị thông báo lỗi/thành công

- TimecardDisplayUI:
  + Hiển thị thông tin thẻ chấm công
  + Hiển thị trạng thái thẻ chấm công
  + Hiển thị chế độ chỉ đọc khi đã nộp

B. Control Classes:
- TimecardController:
  + Xử lý logic nghiệp vụ
  + Kiểm tra tính hợp lệ của giờ làm
  + Quản lý trạng thái thẻ chấm công
  + Xử lý việc nộp thẻ chấm công
  + Kết nối với CSDL dự án

C. Entity Classes:
- Employee:
  + Lưu thông tin nhân viên
  + Quản lý giới hạn giờ làm

- Timecard:
  + Lưu thông tin thẻ chấm công
  + Quản lý trạng thái nộp/chưa nộp
  + Quản lý khoảng thời gian

- TimeEntry:
  + Lưu chi tiết giờ làm theo ngày
  + Liên kết với số phí

- ChargeCode:
  + Lưu thông tin số hiệu phí
  + Quản lý trạng thái khả dụng

### 4.4. Xác định thuộc tính và quan hệ

- Lớp Employee:
  + id, name, maxHours
  + Quan hệ 1-n với Timecard

- Lớp Timecard:
  + id, startDate, endDate, status, submitDate
  + Quan hệ 1-n với TimeEntry
  + Quan hệ n-1 với Employee

- Lớp TimeEntry:
  + id, date, hours
  + Quan hệ n-1 với Timecard
  + Quan hệ n-1 với ChargeCode

- Lớp ChargeCode:
  + id, code, description, status
  + Quan hệ 1-n với TimeEntry

- Lớp TimecardController:
  + validationStatus
  + employeeId
  + currentTimecard

- Lớp TimecardFormUI/DisplayUI:
  + displayMode
  + formData
  + messages

### 4.5. Kết quả mong đợi
A. Biểu đồ lớp phân tích:

![Class diagram](https://www.planttext.com/api/plantuml/png/ZLInRXGn4EttAuPhI8Wk4kqLKU0k0HGK8J3qmwvPZ-Ar5w-DM24AFeCQKL1GqN5AbI_PFyauUxVdMoqefP_Vp1k_D_9fuz7vKEdiWLUoab1h99CrLsHgT5X18JzWqFxS6d-9VF_44UhaNfEHlgqbMEULpR9SOzF0MLLhsqe9NpA0UOMN2iqxacO1RxmZKqPKMR4FrCgQyYccs976LaHOaDdsE3YC5t5QeUHIORNaUmQ_RiK5LJ97Lsp5cPRAc1BR2-c52la2LkXb1Br35b58gRWdemGtVqPs9xfK94Zw0TCX_6UEC-DTsmyITNU2ZUKEVBJXlRu3IaLB5KPl7ulbMBCDc_CWnEAkb4jR37w_Kkb3vfKLc9uzqeMo_tIQgwVyFBUkUllYJk98SH12KOGsDc2x2Yz91fwlFZY4Y5qHP-ImntlQfaxqKTifcHKrl8JjI2bwtFkRO0myj_LK4-PwPxMMhk_YqUwdD94Sx397CrZ-6VEuAipiTHx2QwdHapMDehh9XbMVFPx1V0upCzjju0BocpzmaWr093rAMFr-C4rrwr-uOVPWf4GcLoG1By2hqAs_v_2fMt_ZWcmKp_7noPGB2sYwzMyeklLFKoOJxTo-Ps4smKbBkU1ZwFx-CA1lhXEX2VhsyVVXxramckXKceA_i5i0)

B. Giải thích:
- Employee - Timecard (1-n): Một nhân viên có nhiều thẻ chấm công
- Timecard - TimeEntry (1-n): Một thẻ chấm công có nhiều bản ghi giờ
- TimeEntry - ChargeCode (n-1): Một bản ghi giờ thuộc về một số phí
- TimecardUI - TimecardController: UI phụ thuộc Controller để xử lý logic
- TimecardController - Entities: Controller điều phối luồng dữ liệu

