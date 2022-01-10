<h1 align="center">Sơ đồ trình tự</h1>

Sơ đồ trình tự mô tả tương tác giữa các lớp theo các thay đổi của thông điệp theo thời gian và được dùng để khám phá logic của các hoạt động, chức năng và thủ tục phức tạp. Trong sơ đồ này, trình tự tương tác giữa các đối tượng được biểu diễn từng bước một.

Sơ đồ trình tự biểu diễn một luồng chi tiết cho toàn bộ hoặc một phần của một trường hợp cụ thể. Sơ đồ này biểu diễn lời gọi giữa các đối tượng khác nhau theo trình tự thời gian. Ở mức chi tiết nó biểu diễn các lệnh gọi khác nhau từ các đối tượng khác nhau.

Biểu đồ trình tự có hai chiều: chiều dọc thể hiện chuỗi thông điệp theo trình tự thời gian mà chúng xảy ra; chiều ngang hiển thị các đối tượng mà thông điệp được gửi đến.

<p align="center">
    <img src="../assets/sequence-diagram.svg" alt="Sequence Diagram">
    <br />
    Biểu đồ trình tự cho truy vấn số dư ATM
</p>

Một biểu đồ trình tự rất dễ vẽ. Trên đầu sơ đồ của bạn, xác định các thực thể (đối tượng) bằng cách đặt mỗi thực thể bên trong một hộp (xem hình trên). Nếu một thực thể gửi thông điệp đến một thực thể khác, hãy vẽ một mũi tên trỏ đến thực thể nhận và đặt tên của thông điệp phía trên mũi tên. Đối với các thông điệp quan trọng, bạn có thể vẽ một đường gạch chấm với mũi tên trỏ trở lại thực thể gốc; gắn nhãn giá trị trả về phía trên đường chấm.