<h1 align="center">Sơ đồ Use Case</h1>

Sơ đồ use case mô tả một tập hợp các hành động (gọi là use case) mà hệ thống có thể thực hiện ứng với một hoặc nhiều "tác nhân" bên ngoài đến hệ thống. Mỗi use case nên cung cấp một quan sát và giá trị kết quả với các tác nhân.

1. Sơ đồ Use Case mô tả các hành vi chức năng cấp cao của hệ thống.
2. Nó trả lời câu hỏi hệ thống có thể làm gì từ góc độ người dùng.
3. Đồng thời nó cũng trả lời câu hỏi hệ thống không thể làm gì.

Một use case mô tả một đơn vị chức năng được cung cấp bởi hệ thống. Mục đích chính của sơ đồ use case là giúp team dev thấy được các yêu cầu bắt buộc của hệ thống, bao gồm mối liên hệ giữa các tác nhân đến quá trình cốt lõi, cũng như mối liên hệ giữa các use case khác nhau.

Để minh hoạ một use case trên sơ đồ use case, ta vẽ một hình tròn giữa sơ đồ và đặt tên của use case vào giữa hình tròn đó. Để vẽ tác nhân trong sơ đồ, ta vẽ một người qua ở bên trái hoặc bên phải sơ đồ.

<p align="center">
    <img src="/media-files/use-case-diagram.svg" alt="UML">
    <br />
    Sơ đồ use-case cho hệ thống đặt hàng điện tử
</p>

Các thành phần trong sơ đồ use case:

**System Boundary** xác định phạm vi và giới hạn của hệ thống. Nó được biểu diễn là một hình chữ nhật bao gồm tất cả use case của hệ thống.

**Actors** tác nhân là một thực thể thực hiện hành động cụ thể. Những vai trò này là những vai trò nghiệp vụ thực của người dùng trong hệ thống đã cho. Một tác nhân tương tác với một use case của hệ thống. Ví dụ như hệ thống ngân hàng thì khách hàng là một tác nhân.

**Use Case**, tất cả chức năng nghiệp vụ là một use case. Use case nên liệt kê các chức năng nghiệp vụ riêng biệt trong một vấn đề.

**Include** biểu diễn quan hệ một use case yêu cầu một use case khác. Nó cũng tương tự code, một hàm được gọi bởi một hàm khác.

**Extend** mối quan hệ này biểu thị một use case mở rộng sẽ hoạt động như một use case cơ sở, đi cùng với một vài chức năng bổ sung.