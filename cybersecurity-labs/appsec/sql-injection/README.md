Cả 2 bài lab có điểm chung:

-Điểm nhập dữ liệu ở parameter thông qua phương thức GET hoặc POST
-Lỗi nằm ở cách backend trong khi xây dựng SQL query
-Hậu quả: Bypass authentication, truy cập tài khoản người khác, đọc dữ liệu trong database,...
-Cách sửa: 
    +Không dùng string concatenation để tạo SQL mà nên truyền vào như 1 tham số
    +Validate input
    +Có thể dùng EF Core (LINQ)