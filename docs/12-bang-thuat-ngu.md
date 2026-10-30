# Bảng thuật ngữ nền tảng

| Thuật ngữ | Diễn giải dùng trong đề tài | Lưu ý |
| --- | --- | --- |
| Firewall | Kiểm soát lưu lượng giữa các vùng theo chính sách | Không đồng nghĩa với bảo vệ toàn diện |
| Rule/chính sách | Điều kiện và hành động áp dụng lên một luồng mạng | Ghi nguồn, đích, giao thức, dịch vụ, chiều và lý do |
| Stateful inspection | Xét gói tin theo trạng thái/ngữ cảnh kết nối | Cần xác minh cơ chế cụ thể của sản phẩm/phiên bản |
| Stateless filtering | Xét thuộc tính từng gói độc lập | Không gộp với stateful trong báo cáo |
| DMZ | Vùng trung gian cho dịch vụ cần phơi lộ có kiểm soát | DMZ không tự bảo đảm an toàn |
| LAN | Vùng mạng nội bộ theo mô hình lab | Không đại diện cho mạng doanh nghiệp thật |
| WAN/Outside | Giao diện hướng về vùng ngoài | Trong đề tài nên là outside giả lập, không phải Internet |
| VLAN | Phân đoạn logic lớp 2 | Cần ACL/firewall nếu có định tuyến liên vùng |
| ACL | Danh sách điều kiện cho phép/từ chối truy cập | Cách thực thi tùy thiết bị/lớp mạng |
| NAT | Biến đổi địa chỉ mạng/port theo cấu hình | Không thay thế chính sách firewall |
| IDS | Giám sát để phát hiện hoạt động đáng ngờ | Phát hiện không đồng nghĩa tự chặn |
| IPS | Chức năng ngăn chặn hoạt động đáng ngờ | Phạm vi/tính năng phụ thuộc triển khai |
| VPN | Kết nối logic có bảo vệ mật mã qua hạ tầng mạng | Không tự làm endpoint đáng tin cậy |
| Logging | Ghi sự kiện nhằm quan sát/điều tra | Giảm thiểu dữ liệu nhạy cảm và thời gian lưu |
| Default deny | Từ chối luồng chưa được cho phép tường minh | Cần bảo đảm đường quản trị/khôi phục trước |
| Đặc quyền tối thiểu | Chỉ cấp quyền cần thiết cho công việc | Áp dụng cho người dùng và luồng mạng |
| Lab cô lập | Mạng VM không bridge/route ra ngoài phạm vi | Phải kiểm tra thực tế trước mỗi đợt thử |
