# Nền tảng lý thuyết

> Bản nền để học và xin duyệt đề tài. Đây là phần diễn giải, không thay thế giáo trình. Mỗi nội dung cần đối chiếu mã nguồn trong `docs/07-nguon-tham-khao.md`; những thông số triển khai chưa xác minh được giữ ở trạng thái cần tra cứu.

## 1. Bài toán và mục tiêu bảo vệ

Mạng doanh nghiệp kết nối người dùng, máy chủ và dịch vụ qua nhiều vùng có mức độ tin cậy khác nhau. Firewall là một điểm thực thi chính sách giữa các vùng: nó quyết định luồng mạng nào được đi qua theo quy tắc đã định. Mục tiêu không phải “chặn mọi thứ” một cách mù quáng mà là chỉ cho phép luồng cần thiết, giảm bề mặt phơi lộ và ghi nhận đủ thông tin để kiểm tra.

Mục tiêu an ninh nền tảng là bộ ba CIA:

- **Confidentiality - Bảo mật:** chỉ chủ thể được phép mới đọc được thông tin.
- **Integrity - Toàn vẹn:** dữ liệu và cấu hình không bị thay đổi trái phép.
- **Availability - Sẵn sàng:** dịch vụ vẫn dùng được với người dùng hợp pháp.

Các thuộc tính bổ sung thường cần cân nhắc gồm xác thực danh tính/nguồn dữ liệu và trách nhiệm giải trình (khả năng quy hành động về chủ thể qua log). Các mục tiêu này có thể xung đột: quy tắc kiểm soát chặt tăng bảo vệ nhưng cấu hình sai có thể làm gián đoạn dịch vụ.

## 2. Mối đe dọa, lỗ hổng, rủi ro và kiểm soát

- **Mối đe dọa:** tác nhân hoặc sự kiện có khả năng gây ảnh hưởng xấu.
- **Lỗ hổng:** điểm yếu trong thiết kế, cấu hình, phần mềm hoặc quy trình.
- **Rủi ro:** khả năng một mối đe dọa khai thác lỗ hổng và mức ảnh hưởng có thể xảy ra.
- **Kiểm soát:** biện pháp giảm xác suất, giảm tác động, phát hiện hoặc hỗ trợ phục hồi.

Trong đề tài này, ví dụ rủi ro cần khảo sát là dịch vụ nội bộ bị mở ra không cần thiết, máy chủ công khai bị xâm nhập rồi tạo đường sang mạng LAN, quy tắc firewall quá rộng, quản trị thiết bị firewall không được giới hạn, và log không đủ để giải thích vì sao một luồng bị cho phép/từ chối. Đây là ví dụ phân tích, không phải kết luận về một tổ chức thật.

## 3. Mô hình vùng mạng

- **WAN/Outside:** vùng ngoài, trong lab được biểu diễn bằng một máy khách hoặc mạng ảo riêng; không đồng nghĩa phải kết nối Internet thật.
- **LAN/Inside:** vùng thiết bị nội bộ được bảo vệ.
- **DMZ:** vùng trung gian dành cho dịch vụ giả lập cần được truy cập từ vùng ngoài. DMZ giảm khả năng một máy chủ công khai trở thành cầu nối trực tiếp vào LAN; bản thân việc có DMZ không tự bảo đảm an toàn.
- **Management:** đường quản trị thiết bị. Nên giới hạn vào máy quản trị được chỉ định; chưa chốt cách triển khai cho tới khi giảng viên duyệt sơ đồ.

Phân vùng mạng có thể thực hiện bằng các giao diện vật lý hoặc VLAN. VLAN tạo phân đoạn lớp 2; ACL/firewall kiểm soát luồng lớp 3/4 theo chính sách. VLAN riêng không tự tạo chính sách bảo vệ nếu định tuyến giữa VLAN vẫn mở.

## 4. Firewall và cơ chế lọc

Firewall có thể là phần mềm, phần cứng hoặc kết hợp. Các cách phân loại phổ biến trong giáo trình:

- **Packet filtering/stateless:** đánh giá từng gói dựa trên trường gói tin như địa chỉ nguồn/đích, giao thức và cổng; không nhất thiết hiểu trạng thái phiên.
- **Stateful inspection:** theo dõi trạng thái kết nối và dùng ngữ cảnh phiên để xét gói tin tiếp theo.
- **Application proxy/gateway:** trung gian ở cấp ứng dụng, có thể hiểu sâu hơn giao thức ứng dụng nhưng cần cấu hình và tài nguyên phù hợp.
- **Circuit-level gateway:** theo dõi việc thiết lập phiên/kết nối ở mức mạch, không nhất thiết kiểm tra nội dung ứng dụng.

Các sản phẩm hiện đại có thể kết hợp nhiều cơ chế. Không được suy ra tính năng/khả năng của một bản pfSense cụ thể chỉ từ tên loại firewall; phải kiểm tra tài liệu chính thức và phiên bản thực sự dùng.

Một quy tắc firewall thường xét vùng/giao diện, chiều lưu lượng, nguồn, đích, giao thức, cổng/dịch vụ và hành động. Thứ tự quy tắc, cơ chế state tracking, NAT và các mặc định phụ thuộc sản phẩm/phiên bản. Các chi tiết đó phải được xác minh trước khi viết cấu hình.

## 5. Chính sách mặc định từ chối và đặc quyền tối thiểu

**Default deny/discard** nghĩa là từ chối luồng không được cho phép rõ ràng. Quy tắc này hỗ trợ fail-safe defaults, nhưng không có nghĩa là xóa hoặc chặn tùy tiện mọi luồng: cần xác định trước các nhu cầu thiết yếu, đường quản trị, DNS/DHCP nếu sử dụng, lưu log và phương thức khôi phục để không tự khóa khỏi thiết bị.

**Đặc quyền tối thiểu** áp dụng cho cả người dùng và luồng mạng: chỉ cấp đúng quyền cần cho vai trò/dịch vụ. **Phân tách đặc quyền** hạn chế một tài khoản hoặc vùng có thể kiểm soát toàn hệ thống. Các quyết định này phải có lý do và tiêu chí kiểm chứng trong ma trận chính sách.

## 6. DMZ, NAT, VPN và IDS/IPS

- **DMZ:** phân vùng dịch vụ có mức phơi lộ cao hơn; chính sách LAN↔DMZ và WAN↔DMZ cần được xét riêng.
- **NAT:** biến đổi địa chỉ nguồn/đích theo cấu hình. NAT không thay thế firewall, xác thực, phân đoạn hay chính sách truy cập.
- **VPN:** tạo kết nối có bảo vệ mật mã giữa các điểm cuối; không tự làm cho thiết bị đầu cuối đáng tin cậy.
- **IDS:** phát hiện và cảnh báo hành vi đáng ngờ.
- **IPS:** có thể chủ động ngăn chặn theo chức năng và cấu hình sản phẩm. Firewall, IDS và IPS có vai trò liên quan nhưng không đồng nhất.

Các thành phần này chỉ đưa vào thiết kế nếu phục vụ câu hỏi nghiên cứu và nằm trong năng lực/phạm vi được phê duyệt; không đưa thêm công cụ chỉ để làm đề tài trông rộng hơn.

## 7. Log, giám sát và kiểm chứng

Log hỗ trợ trả lời: thời điểm, nguồn/đích, giao thức/dịch vụ, hành động chính sách và lý do/nhãn quy tắc nếu thiết bị cung cấp. Log có thể chứa thông tin nhạy cảm nên cần tối thiểu hóa, làm sạch trước khi đưa vào báo cáo và không công khai.

Kiểm thử phải dùng các luồng bình thường, được tạo từ máy ảo trong lab. Mỗi ca cần nêu giả thuyết, nguồn, đích, dịch vụ, hành động mong đợi, kết quả thực tế và bằng chứng đã khử nhạy cảm. Chỉ tuyên bố “đạt” khi kết quả quan sát khớp tiêu chí đã định trước; kiểm tra một luồng không chứng minh hệ thống an toàn trước mọi tấn công.

## 8. pfSense trong đề xuất

pfSense được đề xuất làm nền tảng firewall ảo vì đề tài thầy đưa nêu rõ pfSense hoặc FortiGate-VM cho mô hình NGFW/DMZ. Đây là lựa chọn tạm thời, chưa phải quyết định cuối: cần xác minh phiên bản, yêu cầu tài nguyên, giấy phép/điều kiện sử dụng, khả năng chạy trên hypervisor sẵn có, các tính năng cần cho bài và quy định của giảng viên. Nếu chưa xác minh, ghi rõ “chưa chốt”, không bịa cấu hình hoặc phiên bản.

## 9. Giới hạn kết luận

Kết quả trong một lab nhỏ chỉ cho biết các ca kiểm thử đã định có hoạt động như mong đợi trong đúng cấu hình/phiên bản đó. Không được khái quát thành chứng minh an toàn cho doanh nghiệp thật, mọi phiên bản, mọi lưu lượng hay mọi loại tấn công. Hạn chế, giả định và sai số phải được ghi trong báo cáo.

## 10. Nguồn lý thuyết chính

- [S01-S05] Slide môn học Chương 1-5 do người dùng cung cấp; xem mục nguồn để biết nội dung đã nhận được.
- [S06] Danh sách 40 đề tài và yêu cầu chung của đề tài do giảng viên cung cấp.
- [S07] Quy định hình thức báo cáo BTL do người dùng cung cấp.
- [S08-S15] Giáo trình/trang khóa học liên quan; trạng thái truy cập ghi ở sổ nguồn.
- [S16-S17] Văn bản chính thức liên quan khung năng lực số/AI; chỉ dùng khi nội dung báo cáo thực sự cần.
- [S18-S20] Tài liệu nền và tình huống thực tế; không thay thế tài liệu học thuật/chính thức.
