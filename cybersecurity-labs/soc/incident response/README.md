Scenario 1: 500 lần login failed
    -Kiểm tra log: Authentication logs, VPN/AD/SSO logs, firewall logs
    -Cần thêm dữ liệu: IP nguồn, username, thời gian, số lần fail, có login thành công sau đó không, GeoIP
    -Incident: Chưa, có thể là brute-force
    -Severity: Medium -> High nếu có login thành công sau brute-force
    -Cách kiểm soát: Block/rate-limit IP, vô hiệu hóa account nếu compromise
    -Escalate cho Senior SOC, Incident Response, IAM

Scenario 2: Login từ IP hoặc vị trí lạ
    -Kiểm tra log: Authentication logs, VPN/SSO/AD logs, firewall/VPN logs
    -Cần thêm dữ liệu: IP, GeoIP, thời gian, thiết bị, user-agent, VPN, lịch sử đăng nhập
    -Incident: Chưaa, có thể người dùng bật VPN, đi du lịch
    -Severity: Medium -> High nếu có dấu hiệu account compromise
    -Cách kiểm soát: Revoke session/token, reset password, MFA, chặn IP nếu cần
    -Escalate cho Senior SOC, Incident Response, IAM

Scenario 3: Kết nối domain đáng ngờ
    -Kiểm tra log: DNS logs, proxy/web logs, firewall logs, EDR logs
    -Cần thêm dữ liệu: Domain, IP đích, DNS query, process tạo connection, hostname, user, thời gian
    -Incident: Chưa, domain có thể hợp lệ nhưng bị đánh giá nhầm
    -Severity: Medium -> Critical nếu phát hiện malware
    -Cách kiểm soát: Block domain, cô lập máy nếu có dấu hiệu của malware
    -Escalate cho Senior SOC, Incident Response, Endpoint, Network team

