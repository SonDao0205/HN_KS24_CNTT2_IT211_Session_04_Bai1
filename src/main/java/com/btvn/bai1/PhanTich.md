Nguyên nhân gốc rễ
Lỗi nằm ở dòng code: return movies.toString(); và kiểu trả về của hàm là String.

Cơ chế của List.toString() trong Java:
Khi bạn gọi movies.toString(), Java sẽ duyệt qua từng phần tử trong danh sách và gọi hàm toString() của từng đối tượng Movie để nối thành một chuỗi.

Hành vi mặc định của lớp Movie:
Lớp Movie của bạn chưa override (ghi đè) phương thức toString(). Do đó, nó sẽ sử dụng hàm toString() mặc định của lớp Object trong Java. Định dạng mặc định này là: Tên_Lớp@Mã_Băm_Hex (ví dụ: Movie@3a1b2c3d).

Bỏ lỡ tính năng tự động của Spring Boot:
Spring Boot (nhờ thư viện Jackson đi kèm sẵn) có khả năng tự động chuyển đổi (serialize) một Object hoặc một List<Object> thành chuỗi JSON chuẩn chỉ nếu bạn trả về chính Object/List đó. Việc bạn ép nó về kiểu String thủ công bằng toString() đã vô tình chặn đứng cơ chế chuyển đổi tự động này, khiến Spring trả về một chuỗi text thuần túy (Plain Text) vô nghĩa với frontend.