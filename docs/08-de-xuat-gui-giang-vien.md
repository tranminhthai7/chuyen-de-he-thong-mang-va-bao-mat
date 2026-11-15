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

- **Nền tảng ảo hóa:** Oracle VirtualBox 7.x, dùng các mạng `Internal Network` để tách vùng `OUTSIDE`, `LAN`, `DMZ`; dùng `Host-Only` riêng cho quản trị từ máy chủ. Chọn VirtualBox vì có thể tạo nhiều card mạng ảo và snapshot để quay lại cấu hình trước.
- **Firewall:** pfSense Community Edition (CE), chạy trong một VM có 4 card mạng ảo: WAN/OUTSIDE, LAN, DMZ và MGMT. WAN chỉ nối vào mạng `Internal Network` mô phỏng, không nối Internet thật.
- **Máy khách kiểm thử:** Debian Stable tối giản, một VM trong vùng OUTSIDE và một VM trong LAN. Dùng trình duyệt hoặc `curl` để kiểm tra dịch vụ web bình thường.
- **Máy chủ DMZ:** Debian Stable tối giản chạy Nginx, chỉ cung cấp trang web thử nghiệm tĩnh, không chứa dữ liệu thật.
- **Ghi nhận kết quả:** Firewall logs của pfSense và bảng test case; ảnh chụp/log đưa vào báo cáo phải được rà soát và loại thông tin nhạy cảm.
- **Quản lý file:** cấu hình xuất, log thô, capture và dữ liệu thử nghiệm chỉ lưu local trong các thư mục bị `.gitignore`; GitHub chỉ nhận tài liệu/code thực hành đã được phép chia sẻ.

**Mô hình tối thiểu:** 4 VM (1 pfSense, 2 máy khách, 1 máy chủ DMZ). Phiên bản chính xác, yêu cầu RAM/CPU, cách truy cập giao diện quản trị và giấy phép phải được kiểm tra theo tài liệu chính thức trước khi cài; nếu máy không đủ tài nguyên, nhóm sẽ giảm số VM sau khi điều chỉnh mô hình và ghi rõ giới hạn.

### 4. Phạm vi an toàn

Toàn bộ mô hình dự kiến chạy trong mạng ảo cô lập, không bridge vào mạng trường/Internet và không kiểm thử hệ thống của bên thứ ba. Demo chỉ kiểm tra kết nối dịch vụ bình thường theo các quy tắc firewall đã duyệt; không thực hiện khai thác lỗ hổng, mã độc, phishing, dò thông tin xác thực hay DoS/DDoS.

### 5. Kịch bản demo và tiêu chí đánh giá dự kiến

Trong lab cô lập, nhóm dự kiến kiểm tra các luồng bình thường sau:

1. Máy khách OUTSIDE truy cập trang Nginx trong DMZ qua dịch vụ web được cho phép: kết nối thành công và log thể hiện đúng rule.
2. Máy khách OUTSIDE thử truy cập máy khách LAN: kết nối bị từ chối theo chính sách.
3. Máy chủ DMZ thử mở kết nối tới LAN: bị từ chối mặc định.
4. Máy khách LAN truy cập trang demo DMZ: chỉ được phép nếu ma trận chính sách xác định nhu cầu này.
5. Máy quản trị từ mạng MGMT mở giao diện quản trị pfSense; các vùng khác không được phép quản trị.

Tiêu chí: kết quả từng ca khớp kỳ vọng; log xác định được hành động/rule liên quan; cấu hình có thể khôi phục bằng snapshot/backup. Không đánh giá bằng cách chạy tấn công, quét mạng hay tạo tải.

### 6. Sản phẩm dự kiến

- Sơ đồ 4 vùng mạng, bảng interface và ma trận chính sách truy cập.
- Lab ảo pfSense CE, hai máy khách Debian và một máy chủ Debian/Nginx, kèm hướng dẫn khởi động/dừng và khôi phục.
- Bảng ca kiểm thử, kết quả thực tế, log/ảnh đã làm sạch và nhận xét.
- Báo cáo Word và slide theo yêu cầu mà Thầy xác nhận.

### 7. Kính xin duyệt

Kính mong Thầy xem xét và cho phép nhóm thực hiện đề tài với phạm vi, mô hình VirtualBox/pfSense CE và các ca kiểm thử an toàn nêu trên. Nếu Thầy yêu cầu nền tảng hoặc phạm vi khác, nhóm sẽ điều chỉnh trước khi dựng lab.

**Trân trọng,**

Nhóm: `<Mã nhóm>`

Thành viên: `<Họ tên - MSSV>`

Lớp: `<Lớp>`

Ngày gửi: `<Ngày/tháng/năm>`
