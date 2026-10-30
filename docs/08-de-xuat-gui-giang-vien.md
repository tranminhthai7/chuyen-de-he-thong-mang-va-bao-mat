# Đề xuất đề tài gửi giảng viên

**Kính gửi Thầy,**

Nhóm em xin phép đề xuất đề tài bài tập lớn:

## Thiết kế và đánh giá mô hình tường lửa pfSense cho mạng doanh nghiệp nhỏ với phân vùng LAN/DMZ và kiểm soát truy cập

### 1. Lý do chọn đề tài

Các slide môn học có nội dung về bảo mật hệ thống mạng, firewall, phân vùng DMZ, kiểm soát truy cập, chính sách từ chối mặc định và phòng thủ nhiều lớp. Danh sách đề tài thầy cung cấp cũng có đề tài triển khai NGFW bằng pfSense hoặc FortiGate-VM, cùng đề tài VLAN/ACL. Nhóm muốn thu hẹp thành một mô hình firewall ảo nhỏ để có thể giải thích cơ sở lý thuyết, trình bày sơ đồ, kiểm tra chính sách và đánh giá log trong môi trường học tập.

### 2. Mục tiêu dự kiến

- Trình bày cơ sở lý thuyết về firewall, LAN/DMZ, chính sách truy cập và giám sát.
- Thiết kế một lab ảo tách biệt gồm vùng ngoài mô phỏng, DMZ và LAN.
- Đề xuất và kiểm thử các chính sách cho phép/từ chối một số luồng dịch vụ bình thường.
- Đối chiếu kết quả với log và nêu giới hạn của mô hình.

### 3. Công nghệ dự kiến

- Firewall: pfSense, do danh sách đề tài môn học nêu pfSense/FortiGate-VM.
- Máy ảo hóa: VirtualBox hoặc VMware, tùy cấu hình máy và yêu cầu của Thầy.
- Máy chủ/máy khách: VM dùng dữ liệu giả; không chứa thông tin thật.

Các phiên bản và cấu hình cụ thể chưa chốt, sẽ được xác minh từ tài liệu chính thức và xin ý kiến trước khi triển khai.

### 4. Phạm vi an toàn

Toàn bộ mô hình dự kiến chạy trong mạng ảo cô lập, không bridge vào mạng trường/Internet và không kiểm thử hệ thống của bên thứ ba. Demo chỉ kiểm tra kết nối dịch vụ bình thường theo các quy tắc firewall đã duyệt; không thực hiện khai thác lỗ hổng, mã độc, phishing, dò thông tin xác thực hay DoS/DDoS.

### 5. Sản phẩm dự kiến

- Sơ đồ mạng và ma trận chính sách truy cập.
- Lab ảo có hướng dẫn khởi động/dừng và khôi phục.
- Bảng ca kiểm thử, kết quả, log đã làm sạch và nhận xét.
- Báo cáo Word và slide theo yêu cầu cuối cùng của Thầy.

### 6. Kính nhờ Thầy xác nhận

1. Tên đề tài và phạm vi LAN/DMZ/firewall nêu trên có phù hợp không?
2. Nhóm có được chọn pfSense và VirtualBox/VMware hay phải dùng nền tảng cụ thể?
3. Mạng lab có bắt buộc tuyệt đối không nối Internet không? Nhóm đề xuất cô lập hoàn toàn.
4. Có cần triển khai VLAN/ACL hay firewall với nhiều interface là đủ?
5. Yêu cầu slide áp dụng là tối thiểu 4 slide theo quy định hình thức hay 25-40 slide theo danh sách đề tài?
6. Thầy yêu cầu minh chứng nào: log, video demo, file cấu hình hay ảnh chụp lab?
7. Có giới hạn/tiêu chí nào khác về công cụ, phiên bản, thời gian hoặc quy mô báo cáo không?

Nhóm sẽ chỉ triển khai phần lab sau khi được Thầy xác nhận đề tài và phạm vi.

**Trân trọng,**

Nhóm: `<Mã nhóm>`

Thành viên: `<Họ tên - MSSV>`

Lớp: `<Lớp>`

Ngày gửi: `<Ngày/tháng/năm>`
