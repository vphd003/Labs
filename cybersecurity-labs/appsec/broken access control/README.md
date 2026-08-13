Unprotected admin functionality:
    -nhập dữ liệu ở URL/path
    -request bị ảnh hưởng: toàn bộ những request có liên quan tới chức năng quản trị
    -lỗ hổng: server không kiểm tra quyền admin trước khi trả về kết quả hoặc thực hiện chức năng
    -hậu quả: có thể truy cập vào các chức năng của admin mà không thông qua xác thực
    -khắc phục: server-side authorization cho từng endpoint

Unprotected admin functionality with unpredictable URL:
    Giống hệt Unprotected admin functionality, chỉ khác URL không đoán trước được, phải vào check java script để biết được URL dẫn tới admin. Về cơ bản một khi đã biết được path thì vẫn như Unprotected admin functionality.

User role controlled by request parameter:
    -điểm nhập dữ liệu: parameter trong request gửi lên server
    -lỗ hổng: server tin vào authorization do client gửi lên
    -hậu quả: user có thể vượt quyền lên admin
    -khắc phục: server không được lấy quyền từ request client, mà phải lấy từ session trong request mà server đã phản hồi trước đó 