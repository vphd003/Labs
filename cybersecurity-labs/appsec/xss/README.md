reflected xss:
    -nhập dữ liệu ở search box, parameter,...
    -request bị ảnh hưởng: request chứa payload và request phản hồi
    -lỗ hổng: lấy input người dùng đưa thẳng vào html response
    -hậu quả: ảnh hướng đến người click vào đường link có chứa parameter độc hại
    -khắc phục: output encoding, input validation, csp

stored xss:
    -nhập dữ liệu ở comment,...
    -request bị ảnh hưởng: request gửi dữ liệu để lưu chứa payload và request phản hồi đã chứa dữ liệu đã lưu
    -lỗ hổng: lưu dữ liệu chưa được xử lý, rồi render ra thẳng html
    -hậu quả: ảnh hưởng tới tất cả người dùng truy cập vào trang chứa dữ liệu
    -khắc phục: output encoding, input validation, encode dữ liệu khi lưu, csp