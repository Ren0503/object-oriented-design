<h1 align="center">Thiết kế Trang Stack Overflow</h1>

**Ta sẽ thiết kế theo thứ tự sau:**

* [Yêu cầu hệ thống](#yêu-cầu-hệ-thống)
* [Sơ đồ Use Case](#sơ-đồ-use-case)
* [Sơ đồ lớp](#sơ-đồ-lớp)
* [Sơ đồ hoạt động](#sơ-đồ-hoạt-động)
* [Code](#code)

Stack OVerflow là diễn đàn lớn nhất cho các lập trình viên học tập và chia sẻ kiến thức. Website cung cấp một nền tảng cho người dùng hỏi và trả lời, và các thành viên có thể tham gia tích cực bằng bình chọn vote up và vote down cho câu hỏi và câu trả lời. 

Người dùng Stack Overflow có thể nhận điểm uy tín và huy hiệu. Ví dụ người dùng có thể nhận 10 điểm uy tín cho một lần "upvote" câu trả lời và 5 điểm cho upvote câu hỏi. Đồng thời có thể nhận huy hiệu cho những đóng góp giá trị. Uy tín cao sẽ mở khoá các chức năng mới như vote, comment, hay chỉnh sửa bài đăng người dùng.

<p align="center">
    <img src="/media-files/stack-overflow.jpg" alt="Stack Overflow">
    <br />
    Stack Overflow - Online Community for Developers
</p>

### Yêu cầu hệ thống

Ta sẽ thiết kế hệ thống dựa trên các yêu cầu sau:

1. Bất kỳ ai cũng có thể tìm kiếm câu hỏi. Nhưng để vote thì phải đăng ký thành viên.
2. Thành viên có thể đăng câu hỏi mới.
3. Thành viên có thể trả lời cho câu hỏi mở.
4. Thành viên có thể thêm bình luận cho câu hỏi hay trả lời.
5. Thành viên có thể upvote câu hỏi, bình luận hay câu trả lời.
6. Thành viên có thể cắm cờ câu hỏi, bình luận, trả lời do những vấn đề nghiệm trọng.
7. Bất kỳ thành viên nào cũng có thể thêm [tiền thưởng](https://stackoverflow.com/help/bounty) để câu hỏi được thu hút.
8. Thành viện có thể nhận [tiền thưởng](https://stackoverflow.com/help/bounty).
9. Thành viên có thể vote để [đóng](https://stackoverflow.com/help/closed-questions) câu hỏi. Người điều hành có thể đóng hay mở lại bất kỳ câu hỏi nào.
10. Thành viên có thể thêm [tag](https://stackoverflow.com/help/tagging) vào câu hỏi. Một tag là một từ hoặc một cụm từ mô tả chủ đề của câu hỏi.
11. Thành viên có thể vote [xoá](https://stackoverflow.com/help/deleted-questions) câu hỏi kém chất lượng.
12. Người điều hành có thể đóng một câu hỏi hay khôi phục một câu hỏi đã xoá.
13. Hệ thống có thể xác định các tag thường xuyên xuất hiện.

### Sơ đồ use case

Ta có 5 tác nhân trong hệ thống.

* **Admin:** có trách nhiệm block và unblock thành viên.
* **Guest:** mọi khách đều có thể tìm và xem câu hỏi.
* **Member:** thành viên có mọi quyền mà khách có, đồng thời có thể thêm/xoá câu hỏi, trả lời, bình luận. Thành viên cũng có thể khỏi phục câu hỏi, trả lời bình luận đã xoá.
* **Moderator:** có mọi quyền của thành viên, đồng thời có quyền đóng, xoá, khôi phục bất kỳ câu hỏi nào.
* **System:** có trách nhiệm gửi thông báo và phát huy hiệu cho thành viên.

Các use case nổi bật trong Stack OVerflow:

1. Tìm câu hỏi.
2. Tạo câu hỏi mới với điểm thưởng và tag.
3. Thêm/sửa câu trả lời cho câu hỏi.
4. Thêm bình luận cho câu hỏi và câu trả lời.
5. Người điều hành có thể đóng, xoá và khôi phục bất kỳ câu hỏi nào.

<p align="center">
    <img src="/media-files/stack-overflow-use-case.svg" alt="Stack Overflow Use Case Diagram">
    <br />
    Use Case Diagram for Stack Overflow
</p>

### Sơ đồ lớp

Các lớp chính trong hệ thống Stack Overflow:


* **Question:** lớp này là phần trung tâm của hệ thống. Có các thuộc tính như `Title` và `Description` để xác định câu hỏi. Thêm vào đó, ta có thể theo dõi số lượt xem và vote câu hỏi. Ta còn có thể theo dõi trạng thái câu hỏi, cũng như đóng nhận xét nếu câu hỏi đã đóng.
* **Answer:** các thuộc tính quan trọng nhất của bất kỳ câu trả lời nào sẽ là văn bản và số lượt xem. Ngoài ra, ta cũng sẽ theo dõi số lần một câu trả lời được bình chọn hoặc gắn cờ. Chúng ta cũng nên theo dõi xem chủ sở hữu câu hỏi có chấp nhận câu trả lời hay không. 
* **Comment:** Similar to answer, comments will have text, and view, vote, and flag counts. Members can add comments to questions and answers.
* **Tag:** Tags will be identified by their names and will have a field for a description to define them. We will also track daily and weekly frequencies at which tags are associated with questions.
* **Badge:** Similar to tags, badges will have a name and description.
* **Photo:** Questions or answers can have photos.
* **Bounty:** Each member, while asking a question, can place a bounty to draw attention. Bounties will have a total reputation and an expiry date.
* **Account:** We will have four types of accounts in the system, guest, member, admin, and moderator. Guests can search and view questions. Members can ask questions and earn reputation by answering questions and from bounties.
* **Notification:** This class will be responsible for sending notifications to members and assigning badges to members based on their reputations.

<p align="center">
    <img src="/media-files/stack-overflow-class-diagram.svg" alt="Stack Overflow Class Diagram">
    <br />
    Class Diagram for Stack Overflow
</p>

<p align="center">
    <img src="/media-files/stack-overflow-uml.svg" alt="Stack Overflow UML">
    <br />
    UML for Stack Overflow
</p>

### Activity Diagram

**Post a new question:** Any member or moderator can perform this activity. Here are the steps to post a question:

<p align="center">
    <img src="/media-files/stack-overflow-activity-diagram.svg" alt="Stack Overflow Activity Diagram">
    <br />
    Activity Diagram for Stack Overflow
</p>

### Sequence Diagram

Following is the sequence diagram for creating a new question:

<p align="center">
    <img src="/media-files/stack-overflow-sequence-diagram.svg" alt="Stack Overflow Sequence Diagram">
    <br />
    Sequence Diagram for Stack Overflow
</p>
