# Phân tích ca sử dụng trong hệ thống "Payroll"

## Phân tích UC Login
+ Mục tiêu
   - Mô tả chi tiết quy trình đăng nhập của người dùng vào hệ thống.
   - Xác định các bước và điều kiện cần thiết để hoàn thành quy trình đăng nhập.
   - Tạo tài liệu rõ ràng để phát triển và kiểm thử hệ thống.
+ Đối tượng
   - Người dùng cuối (End Users): Những người sử dụng hệ thống để đăng nhập.
   - Nhà phát triển (Developers): Sử dụng sơ đồ để hiểu và triển khai chức năng.
   - Người kiểm thử (Testers): Dựa vào sơ đồ để thiết kế các kịch bản kiểm thử.
+ Lý do đưa ra thiết kế
   - Tính rõ ràng: Sơ đồ hoạt động (Activity Diagram) giúp minh họa quy trình một cách trực quan, dễ hiểu.
   - Xác định điểm quyết định: Hiển thị rõ ràng điều kiện kiểm tra tính hợp lệ của thông tin đăng nhập.
   - Tính linh hoạt: Dễ dàng điều chỉnh khi có thay đổi trong quy trình.
   - Hỗ trợ tốt cho phát triển và kiểm thử: Cung cấp cái nhìn tổng quan giúp các bên liên quan hiểu rõ quy trình và phát hiện lỗi tiềm ẩn.
### sơ đồ Activity diagram
![Activity Diagram](https://www.planttext.com/api/plantuml/png/RP6nJiCm48PtItw7Ns99Xhv0aA2Y4gfKmaAO44D5tSPIuWJRGOhK1NLWO8694H1Y0AaRKpscB-8tuPfcAMKx_VV_lk_EVMF7sbPvnjdyqWWzvwnLE8jYxrunzEu1IUhTiveTSaQkYzfOaPCl6ahl5WgMkeyuBNIEzTDweMOuJ_rgMMxjtQFHLaFIVAjT6pYxQzuGKsqn8kch-Zjej1cKm-eneJG_54saQaroYg2Jh5GWaeyI6J4VXyGb589Qc90p81hurMU9swhsxfwWTLNZfiEaxiukiL0L1ccpL6dRDROeEHEP4GXK4Uu7EeIJvht0cNSlietrhWwqc5ptZlO3_rvBg8cSRhRgKqLVyWi0)
## Phân tích UC Maintain Timecard
+ Mục tiêu: Cung cấp một hệ thống quản lý bảng chấm công hiệu quả, cho phép nhân viên nhập và lưu trữ giờ làm việc một cách chính xác và dễ dàng. Hệ thống cũng cần đảm bảo rằng thông tin được cập nhật kịp thời và chính xác trong cơ sở dữ liệu quản lý dự án.
+ Đối tượng
   - Nhân viên (Employee): Người sử dụng hệ thống để nhập và quản lý giờ làm việc của họ.
   - Quản lý dự án (Project Management): Bộ phận sử dụng dữ liệu bảng chấm công để theo dõi tiến độ và chi phí dự án.
   - Hệ thống quản lý thời gian (Timecard System): Bao gồm các thành phần như TimecardForm, TimecardController, và TimecardDatabase.
+ Lý do đưa ra thiết kế
   - Tính rõ ràng và dễ hiểu: Thiết kế này chia nhỏ quy trình thành các bước rõ ràng, dễ theo dõi cho người dùng cuối là nhân viên.
   - Tính linh hoạt: Hệ thống cho phép tạo mới hoặc cập nhật timecard hiện có, phù hợp với nhiều tình huống sử dụng thực tế.
   - Tính chính xác: Bằng cách tích hợp với cơ sở dữ liệu quản lý dự án, hệ thống đảm bảo rằng thông tin về mã charge luôn được cập nhật và chính xác.
   - Tính hiệu quả: Quy trình tự động hóa việc lấy và cập nhật dữ liệu, giảm thiểu thời gian và công sức cần thiết từ phía nhân viên.
### sơ đồ activity diagram
![Activity Diagram](https://www.planttext.com/api/plantuml/png/ZLAzJiCm4Duj-HrkJ0TU84XGWH0CBMBe2wIk6uV6JfGuGsS61YR4Y50LLKnL119CyHYfx-4tuHmYXf8W5ikd-txkFdkSwo3JXOmfQM-KKE9Vo3HErfmVKt9q0lxKcWtC8slk2f2stXN0XArV9R3cKuK8yg-nhbB8hNc4484lY4YmNJAGpHQB25BHL9tUfJLL17DRRrLuA4L9j0Jlx7SFj3LF2i-wZ4v7e0LNuB7cOqG9W5ET87RTfme29xhlg6Z1uvo3jnAkzyEUOJFfPKjhdbkQMaJBDfuh5mNg2MiU1jPmakTj9if5e_-0VSzz41Ewt6J9BMSQfe4AGYwvqeC4byqEsBvqBx21XJLl4BkbYuuooz2-nsEoVo_-kq6V_00trqbAoHWJQpyM9Ly0)
## Phân tích UC Run Payroll
+ Mục tiêu
   - Tự động hóa việc xử lý bảng lương vào ngày trả lương.
   - Tính toán chính xác số tiền lương dựa trên dữ liệu chấm công và đơn hàng (nếu có).
   - Hỗ trợ nhiều phương thức thanh toán: in phiếu lương hoặc gửi tiền trực tiếp qua ngân hàng.
   - Đảm bảo tính tích hợp với các hệ thống khác như Printer và Bank System.
+ Đối tượng
   - System Clock Interface: Kích hoạt quy trình trả lương vào ngày được định sẵn.
   - Payroll Controller: Điều phối tất cả các bước trong quy trình trả lương.
   - Employee: Nhân viên nhận lương.
   - Timecard: Dữ liệu chấm công của nhân viên.
   - Purchase Order (PO): Dữ liệu đơn hàng (áp dụng cho nhân viên làm việc theo hoa hồng).
   - Paycheck: Phiếu lương được tạo sau khi tính toán.
   - Printer Interface và Printer: In phiếu lương (nếu chọn phương thức nhận lương qua thư hoặc nhận trực tiếp).
   - Bank System: Xử lý giao dịch gửi tiền vào tài khoản ngân hàng của nhân viên.
### sơ đồ activity diagram
![Activity Diagram](https://www.planttext.com/api/plantuml/png/TL8zJm914EqlkVym9LJsK4XYOGp4MFW7pkDWDt9poEqHhpIMDb9Ps826GkCb64nCRWkA9VoF_IVExjqP1BpYzklDl3TlfXKBRoIISE0wTkSwhjDegyndm2ATpmJS92c8aVf0HelENs6mMMncs6yQ8DVoFgHx3sw347orX24Z30VigsdwDm2kcVgoSQx3Ur3hgEaXs74T10iGQYTgMNSTeA-nVjHomc6ivJE7KCid8c3g1M7CrJisIrH7vtDAPbb0S8GhIajRdoJDZRg2_J1sFI5o-klyMm1JKxgkeSvNYQcgNeLTgipu42d2ngI9GhMymorF2XWv5v4Lt2QewY_aRuLPAqo0iUE2bJ31j7ppQV4ggbzBJhNCEEqtYwDpAYf3Ovtyz4s-V3KixR8Ipd2NlxdrMYJQ5MYgNo64QfO2hsmD1d50pM19Ihr6Qc9aNFsVUCzPwZ5robgwBw7FlGYwMZxGmEq30-podkiK4jesPKaLYsX83yMxcLrpRD7PZl8F)
+ Lý do đưa ra thiết kế
   - Tự động hóa: Hệ thống được kích hoạt tự động bởi System Clock, giảm thiểu sự can thiệp thủ công.
   - Tích hợp hệ thống: Quy trình tích hợp liền mạch với các hệ thống khác như Printer và Bank System.
   - Tính linh hoạt: Hỗ trợ cả hai phương thức thanh toán (in phiếu lương hoặc gửi tiền qua ngân hàng).
   - Tính chính xác: Dựa trên dữ liệu từ Timecard và Purchase Order, hệ thống đảm bảo tính toán chính xác số tiền lương.
## Phân tích UC Bank System Subsystem
+ Mục tiêu:
   - Xử lý giao dịch gửi tiền trực tiếp vào tài khoản ngân hàng của nhân viên.
   - Đảm bảo tính chính xác và bảo mật trong quá trình giao tiếp với hệ thống ngân hàng bên ngoài.
+ Mô tả chi tiết các thành phần
   1. Payroll Controller:
      - Đóng vai trò điều phối, gọi phương thức deposit() trong giao diện IBankSystem để thực hiện giao dịch.
      - Phương thức liên quan: run payroll().
   2. IBankSystem (Interface):
      - Giao diện trung gian giữa hệ thống bảng lương và hệ thống ngân hàng bên ngoài.
      - Phương thức: deposit(aPaycheck: Paycheck, intoBank: BankInformation): Chuyển phiếu lương và thông tin ngân hàng đến hệ thống ngân hàng.
   3. BankSystem (Subsystem Proxy):
      - Đại diện cho hệ thống ngân hàng bên ngoài.
      - Thực hiện chức năng gửi tiền vào tài khoản ngân hàng của nhân viên.
   4. Entity:
      - Paycheck: Thông tin về phiếu lương, bao gồm số tiền cần gửi.
      - BankInformation: Thông tin tài khoản ngân hàng của nhân viên.
+ Quy trình hoạt động
   1. Kích hoạt giao dịch:
      - Payroll Controller gọi phương thức deposit() trên giao diện IBankSystem với hai tham số:
      - aPaycheck: Phiếu lương của nhân viên.
      - intoBank: Thông tin ngân hàng của nhân viên.
   2. Truyền dữ liệu đến hệ thống ngân hàng:
      - IBankSystem chuyển tiếp thông tin đến BankSystem (proxy cho hệ thống ngân hàng bên ngoài).
   3. Thực hiện giao dịch:
      - BankSystem xử lý giao dịch gửi tiền vào tài khoản ngân hàng dựa trên thông tin nhận được.
   4. Xác nhận giao dịch:
      - Sau khi giao dịch hoàn tất, BankSystem gửi thông báo xác nhận lại cho IBankSystem, sau đó trả kết quả về cho Payroll Controller.
### Sơ đồ Sequnece diagram
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/bP0n3i8m34NtIBc3Hv3W0XrG1GFgXiJ26gM1H6qTb9gX8pENW86n5sZ7dYGteK42bNPYilJzlv--uvA4eqkHSoOaMGSxKJcRvnkB5APod9rxXv7cB90WMGlCzbL9glXT37M5PAWAfwHMCliAmPFWqRf2aB786MSJ72nNGqW4P7nxHJZvjZOpyRcv08DaWs_EsS0Vud-cX-4nV6k4XTItDwb1s-wEGBvvqWZPfoOz8ZXq3mceVLFtJME5wVlBBm00)
+ lý do đưa ra thiết kế
   1. Tách biệt trách nhiệm:
      - Payroll Controller chỉ chịu trách nhiệm điều phối và không làm việc trực tiếp với hệ thống ngân hàng.
      - IBankSystem đóng vai trò như một lớp trung gian, giúp tách biệt hệ thống bảng lương với hệ thống ngân hàng bên ngoài.
   2. Tính module hóa:
      - BankSystem được thiết kế như một proxy, dễ dàng thay đổi hoặc tích hợp với các hệ thống ngân hàng khác nhau.
   3. Bảo mật:
      - Dữ liệu nhạy cảm (phiếu lương và thông tin ngân hàng) chỉ được truyền qua các lớp được định nghĩa rõ ràng.
## Phân tích UC PrintService Subsystem
+ Mục tiêu: Hệ thống PrintService Subsystem chịu trách nhiệm in phiếu lương (Paycheck) trên máy in được chỉ định. Đây là một thành phần độc lập, được điều phối bởi PayrollController.
+ Mô tả các thành phần
   1. PayrollController
   Vai trò:
      - Là thành phần điều phối chính, kích hoạt quy trình in phiếu lương.
      - Gọi phương thức print() thông qua giao diện IPrintService.
      - Phương thức: run payroll(): Bắt đầu quy trình xử lý bảng lương, bao gồm cả việc in phiếu lương nếu cần.
   2. IPrintService (Interface)
   Vai trò:
      - Đóng vai trò giao diện trung gian giữa PayrollController và PrintService.
      - Định nghĩa phương thức print() để in phiếu lương.
      - Phương thức:
      - print(aPaycheck: Paycheck, onPrinter: String):
      - aPaycheck: Thông tin phiếu lương cần in.
      - onPrinter: Tên hoặc địa chỉ của máy in được chỉ định.
   3. PrintService (Subsystem Proxy)
   Vai trò:
      - Đại diện cho hệ thống in thực tế.
      - Thực hiện chức năng in phiếu lương trên máy in được chỉ định.
      - Phương thức: print(aPaycheck: Paycheck, onPrinter: String): Thực hiện in phiếu lương.
   4. Paycheck (Entity)
   Vai trò:
      - Lưu trữ thông tin phiếu lương của nhân viên, bao gồm số tiền, tên nhân viên, và các chi tiết liên quan.
+ Quy trình hoạt động
   1. Kích hoạt quy trình in:
      - PayrollController gọi phương thức print() trên giao diện IPrintService, truyền thông tin phiếu lương và máy in.
   2. Truyền yêu cầu đến hệ thống in:
      - IPrintService chuyển tiếp yêu cầu đến PrintService (proxy cho hệ thống máy in).
   3. Thực hiện in phiếu lương:
      - PrintService in phiếu lương trên máy in được chỉ định.
### Sơ đồ Sequence diagram
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/bP112W8n34NtWToXImMzm2naO5Rk1Zn1gH63RLfY5ERsJWikwgnSXK_U_pzaV9fNUwM8u8DbTRDVDCSuPR4wIH7AId3WuiNSULOMkv2-EL2_wZSanhRKk72dy410s4IxuwaF75ofQkU_jeFBqW3IFKB7LlCVtjwwBMxAJJcLI4QRhbhsU_wmud9ZJTuu2y98ScsV_000)
+ Lý do đưa ra thiết kế
   1. Tính module hóa:
      - Hệ thống in được tách riêng, dễ bảo trì và thay thế khi cần thay đổi công nghệ in.
   2. Tính linh hoạt:
      - Giao diện IPrintService cho phép tích hợp với nhiều loại máy in khác nhau.
   3. Tăng khả năng tái sử dụng:
      - PrintService có thể được sử dụng cho các mục đích in khác ngoài phiếu lương.
## Phân tích UC ProjectManagementDatabase Subsystem
+ Mục tiêu: Hệ thống ProjectManagementDatabase Subsystem chịu trách nhiệm giao tiếp với cơ sở dữ liệu quản lý dự án, nơi lưu trữ thông tin về các mã chi phí liên quan đến các dự án.
+ Mô tả các thành phần
   1. TimecardController
   Vai trò:
      - Là thành phần điều phối chính, quản lý các hoạt động liên quan đến bảng chấm công (timecard).
      - Gọi phương thức getChargeNumbers() thông qua giao diện IProjectManagementDatabase để lấy danh sách mã chi phí.
      Phương thức:
      - get current timecard(): Lấy thông tin bảng chấm công hiện tại.
      - get charge codes(): Lấy danh sách mã chi phí từ cơ sở dữ liệu.
      - update timecard(): Cập nhật thông tin bảng chấm công.
      - save timecard(): Lưu bảng chấm công vào hệ thống.
   2. IProjectManagementDatabase (Interface)
   Vai trò:
      - Là giao diện trung gian giữa TimecardController và ProjectManagementDatabase.
      - Định nghĩa phương thức getChargeNumbers() để lấy danh sách mã chi phí.
      Phương thức:
      - getChargeNumbers(criteria: String): chargeNumList:
      - criteria: Tiêu chí tìm kiếm mã chi phí (ví dụ: dựa trên dự án hoặc phòng ban).
      - chargeNumList: Danh sách mã chi phí trả về.
   4. ProjectManagementDatabase (Subsystem Proxy)
   Vai trò:
      - Đại diện cho cơ sở dữ liệu quản lý dự án thực tế.
      - Thực hiện các truy vấn để lấy thông tin mã chi phí từ hệ thống legacy.
      Phương thức:
      - getChargeNumbers(criteria: String): chargeNumList: Truy vấn cơ sở dữ liệu và trả về danh sách mã chi phí.
   5. ChargeNumList (Entity)
   Vai trò:
      - Lưu trữ danh sách mã chi phí được lấy từ cơ sở dữ liệu quản lý dự án.
+ Quy trình hoạt động
   1. Kích hoạt yêu cầu lấy mã chi phí:
      - TimecardController gọi phương thức getChargeNumbers() trên giao diện IProjectManagementDatabase, truyền vào tiêu chí tìm kiếm.
   2. Truyền yêu cầu đến cơ sở dữ liệu:
      - IProjectManagementDatabase chuyển tiếp yêu cầu đến ProjectManagementDatabase (proxy cho cơ sở dữ liệu legacy).
   3. Truy vấn cơ sở dữ liệu:
      - ProjectManagementDatabase thực hiện truy vấn dựa trên tiêu chí và trả về danh sách mã chi phí (ChargeNumList).
   4. Trả kết quả về:
      - ChargeNumList được trả về từ ProjectManagementDatabase qua IProjectManagementDatabase đến TimecardController.
### Sơ đồ Sequence Diagram
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/dP4z2W8n48NxGEwGKWilO24BQoEeM7Y1sUmGH_ApJ6OBRs-q49PW1Ck1DzzxywRB0Ynpy5g1bSJcIW4jyDYdA9oyHzPgAXAoD44KSxXmkgEL4qHm633A7WG6oBZKDMHb87cO_WRiy3o78sNHIglQscns3SEjSIWVoe2SLvP9a0dMMdtVUr7_X3QOFwBQvRMjT8LKLr4HEepZ-szF)
+ Lý do đưa ra thiết kế
   1. Tính module hóa:
      - Hệ thống cơ sở dữ liệu quản lý dự án được tách biệt, dễ bảo trì và thay thế khi cần nâng cấp hệ thống legacy.
   2. Tính linh hoạt:
      - Giao diện IProjectManagementDatabase cho phép tích hợp với các hệ thống cơ sở dữ liệu khác nhau mà không cần thay đổi logic trong TimecardController.
   3. Tăng khả năng tái sử dụng:
      - ProjectManagementDatabase có thể được sử dụng để truy vấn các thông tin khác ngoài mã chi phí.
