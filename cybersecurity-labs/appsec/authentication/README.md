cả 3 bài lab đều có điểm chung là dùng brute-force attack để tấn công, nhưng sẽ có một vài điểm khác:

Username enumeration via different responses:
    -đầu tiên brute-force username, dựa vào response khác biệt để biết user có tồn tại hay không
    -sau khi biết username tồn tại, brute-force pasword, dựa vào length mà intruder trả về để biết passwword nào hợp lệ


Username enumeration via subtly different responses:
    -giống Username enumeration via different responses nhưng response trả về khác nhau rất nhỏ, mắt thường khó quan sát, phải dùng grep-extract để tìm sự khác biệt. Sau khi tìm được sự khác biệt thì giống Username enumeration via different responses


Username enumeration via response timing:
    -kết quả trà về đều giống nhau, nên phải dựa vào response time để xác định username nào tồn tại. 
    -khi brute-force mọi username cùng 1 password ngắn, response time gần như không khác biệt đáng kể, chỉ khi để password dài, response time mới có sự chênh lệch đáng kể (username tồn tại phải xử lí lâu gấp 10 lần so với username không tồn tại).
    -sau khi biết username tồn tại, brute-force password, nhưng bài lab chống brute-force dựa trên IP, nên phải thêm "X-Forwarded-For: §§" vào trong request với payload là các IP khác nhau, dùng pitchforck attack, để mỗi IP gán với 1 password thành 1 cặp.


KẾT LUẬN:
    Username enumeration via different responses + Username enumeration via subtly different responses: 
        -lỗ hổng: trả về response khac nhau, khiến cho việc nhận biết dữ liệu nào tồn tại trở nên dễ dàng
        -khắc phục: chuẩn hóa toàn bộ response 
    
    Username enumeration via response timing:
        -lỗ hổng: 
            +Hai authentication path có thời gian xử lý khác nhau
            +Tin vào IP từ client-controlled header
        -khắc phục: 
            +Constant-work authentication khiến cho thời gian xử lý thông tin tồn tại và không tồn tại tương đương nhau
            +Chỉ trust header từ trusted proxy

    GIẢi PHÁP CHUNG: rate limit, MFA để tránh brute-force