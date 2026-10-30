# Phạm vi, mục tiêu và yêu cầu

## 1. Tên đề tài tạm

**Thiết kế và đánh giá mô hình tường lửa pfSense cho mạng doanh nghiệp nhỏ với phân vùng LAN/DMZ và kiểm soát truy cập.**

Trạng thái: đề xuất của sinh viên, **chưa được giảng viên duyệt**. Không dùng tên này trên bìa chính thức cho tới khi được xác nhận.

## 2. Căn cứ và loại yêu cầu

### Yêu cầu có trong tài liệu đã nhận

- Danh sách đề tài: Nhóm 2, đề tài 13 đề cập NGFW, pfSense/FortiGate-VM, DMZ, lọc ứng dụng và kiểm soát băng thông.
- Danh sách đề tài: Nhóm 3, đề tài 21 đề cập phân đoạn VLAN và ACL.
- Quy định báo cáo: nộp gói nén với SETUP, SOURCE, THESIS, SOFT và HUONGDAN.PDF; báo cáo Word tối thiểu 20 trang; PowerPoint tối thiểu 4 slide.
- Yêu cầu chung của danh sách đề tài: báo cáo lý thuyết, mô hình lab, demo kiểm thử/phòng thủ/đánh giá lại và kết luận.
- Danh sách đề tài còn nêu slide 25-40 trang. Quy định này khác mức tối thiểu 4 slide trong tài liệu hình thức báo cáo; **cần hỏi giảng viên xác nhận yêu cầu áp dụng cho BTL này**. Tạm dự kiến tuân theo yêu cầu cụ thể hơn 25-40 slide nếu giảng viên không hướng dẫn khác.

### Đề xuất cần duyệt

- Dùng pfSense làm firewall ảo, thay cho phương án FortiGate-VM.
- Lab có các vùng WAN mô phỏng, LAN, DMZ và (nếu khả thi) vùng quản trị.
- Đánh giá chính sách bằng các luồng dịch vụ bình thường được tạo bên trong lab, không khai thác hệ thống thật.
- Dùng nhật ký firewall và bảng kiểm thử làm minh chứng.

## 3. Mục tiêu

1. Trình bày cơ sở lý thuyết về firewall, phân vùng mạng, DMZ, chính sách truy cập và log.
2. Thiết kế một mô hình ảo nhỏ thể hiện được ranh giới giữa vùng ngoài mô phỏng, DMZ và LAN.
3. Đề xuất bộ chính sách truy cập có lý do, áp dụng nguyên tắc từ chối mặc định và đặc quyền tối thiểu.
4. Kiểm tra một tập ca cho phép/từ chối lưu lượng bình thường, đối chiếu với log và tiêu chí đã định trước.
5. Ghi rõ giới hạn của lab, rủi ro cấu hình và biện pháp khôi phục.

## 4. Câu hỏi nghiên cứu đề xuất

- Mô hình vùng mạng và tập quy tắc nào đáp ứng nhu cầu dịch vụ giả lập nhưng vẫn giới hạn luồng không cần thiết?
- Log và các ca kiểm thử nào giúp chứng minh quy tắc đã hoạt động đúng trong lab?
- Những hạn chế nào của mô hình lab khiến kết quả không thể khái quát thành bảo đảm an toàn cho mạng thật?

## 5. Trong phạm vi

- Lý thuyết firewall, kiểm tra trạng thái, chính sách truy cập, DMZ, phân đoạn mạng, NAT và giám sát ở mức cần cho mô hình.
- Thiết kế lab ảo và ma trận luồng dự kiến.
- Kiểm tra kết nối hợp lệ/không hợp lệ bằng lưu lượng ứng dụng bình thường trong môi trường cô lập.
- Phân tích log, lưu minh chứng đã làm sạch và đưa ra khuyến nghị.
- Tài liệu cài đặt/chạy demo chỉ sau khi phiên bản/công cụ được xác minh và giảng viên duyệt.

## 6. Ngoài phạm vi

- Quét hoặc kiểm thử mạng trường, mạng công cộng, tổ chức thật hay thiết bị không thuộc nhóm.
- Khai thác lỗ hổng, tạo mã độc, phishing, đánh cắp thông tin xác thực, chiếm phiên, DoS/DDoS hoặc né tránh phát hiện.
- Đánh giá chứng nhận/tuân thủ doanh nghiệp, triển khai production, cam kết rằng thiết kế “an toàn tuyệt đối”.
- Mở Internet trực tiếp từ lab, trừ khi có phê duyệt riêng và thiết kế cô lập phù hợp.
- Mở rộng sang IDS/SIEM/VPN/NAC nếu chưa có câu hỏi nghiên cứu, thời gian và sự chấp thuận tương ứng.

## 7. Tiêu chí thành công đề xuất

- Sơ đồ và ma trận chính sách thống nhất, mọi luồng có lý do và chủ sở hữu.
- Lab được chứng minh cô lập trước khi thử nghiệm.
- Mỗi ca kiểm thử có kết quả mong đợi, kết quả quan sát và log/bằng chứng tương ứng.
- Không có thử nghiệm ngoài phạm vi hoặc dữ liệu thật trong repo.
- Tài liệu nộp đáp ứng yêu cầu giảng viên đã xác nhận; các mâu thuẫn về số trang/slide được giải quyết trước khi hoàn thiện.

## 8. Câu hỏi cần giảng viên xác nhận

- Tên đề tài và việc sử dụng pfSense có được chấp thuận không?
- Có bắt buộc phải dùng FortiGate-VM/Cisco hay được chọn firewall ảo khác?
- Có cần VLAN/ACL thật trong mô phỏng, hay chỉ cần các interface vùng mạng?
- Lab có được kết nối Internet/NAT ra ngoài không? Đề xuất an toàn hiện tại: không.
- Quy định slide nào áp dụng: tối thiểu 4 hay 25-40? Có yêu cầu mẫu UTH và size chữ riêng không?
- Nhóm cần nộp phiên bản phần mềm, log, video demo hay chỉ báo cáo và slide?
- Giảng viên có yêu cầu phạm vi firewall cụ thể (lọc gói, stateful, proxy, DMZ) hay tiêu chí đo nào không?
