# Nguyên tắc bảo mật và nguyên tắc cấu hình

## 1. Quy tắc thiết kế

1. **Phạm vi rõ ràng:** chỉ bảo vệ các vùng, VM và dịch vụ đã ghi trong sơ đồ được duyệt.
2. **Từ chối mặc định:** luồng không có lý do/ủy quyền rõ ràng bị từ chối; ngoại lệ phải được ghi, giải thích và rà soát.
3. **Đặc quyền tối thiểu:** chỉ cấp quyền mạng và quyền quản trị cần thiết cho từng vai trò.
4. **Phân tách vùng:** Outside mô phỏng, DMZ, LAN và quản trị là các vùng khác nhau; không xem VLAN/interface tách biệt là đủ nếu chính sách định tuyến vẫn cho phép mọi thứ.
5. **Phòng thủ nhiều lớp:** firewall là một kiểm soát, không thay thế cập nhật, bảo vệ máy chủ, sao lưu, quản lý danh tính hay ứng cứu sự cố.
6. **Quản trị an toàn:** giới hạn giao diện quản trị, dùng tài khoản riêng, mật khẩu mạnh do người dùng tự quản và không lưu secret trong Git.
7. **Quan sát được:** quy tắc quan trọng có log phù hợp; tránh ghi dữ liệu thừa hoặc bí mật.
8. **Có thể phục hồi:** backup cấu hình trước thay đổi, ghi cách rollback, kiểm tra bản backup có thể dùng được.
9. **Có căn cứ:** mỗi rule liên kết đến yêu cầu/ca kiểm thử; tránh cấu hình theo suy đoán.
10. **Có thể lặp lại:** ghi phiên bản phần mềm, sơ đồ, thay đổi và kết quả để người khác có thể tái hiện trong cùng lab.

## 2. Nguyên tắc viết script nếu phát sinh

Chưa có code demo được phê duyệt. Nếu sau này cần script hỗ trợ báo cáo:

- Chỉ xử lý log/dữ liệu tổng hợp của lab; không tự động quét hoặc tương tác với host ngoài danh sách cho phép.
- Không chứa exploit, payload, chức năng persistence, thu thập thông tin xác thực, phá hoại hay gửi dữ liệu ra ngoài.
- Kiểm tra đầu vào, xử lý lỗi an toàn, dùng thư viện chuẩn khi phù hợp; không gọi shell với dữ liệu chưa kiểm tra.
- Không lưu secret, token, cookie, địa chỉ cá nhân hoặc nội dung traffic thật.
- Mỗi script cần mục đích, nguồn dữ liệu, cách chạy, giới hạn và ca kiểm thử ghi trong README riêng.
- Chỉ chạy sau khi giảng viên duyệt cách sử dụng và đã xác nhận lab cô lập.

## 3. Bảo vệ cấu hình firewall

- Đặt tên rule theo mục tiêu nghiệp vụ/ca kiểm thử, ghi lý do và chủ sở hữu.
- Hạn chế nguồn, đích, dịch vụ và chiều kết nối; không dùng quy tắc rộng chỉ để “demo chạy được”.
- Kiểm tra thứ tự/ưu tiên rule và state behavior theo tài liệu đúng phiên bản sản phẩm.
- Tách quản trị khỏi lưu lượng demo; tránh tự khóa đường console/khôi phục.
- Không cho phép DMZ truy cập LAN theo mặc định; mọi ngoại lệ phải có lý do được duyệt.
- NAT chỉ là xử lý địa chỉ, không được mô tả như một lớp kiểm soát truy cập thay cho firewall.

## 4. Quy trình thay đổi

Trước thay đổi: nêu mục tiêu, căn cứ, ảnh hưởng dự kiến, cách backup/rollback và ca xác nhận.

Sau thay đổi: kiểm tra kết quả mong đợi, kiểm tra luồng không mong đợi vẫn bị chặn, xem log, ghi phiên bản/cấu hình đã khử bí mật và cập nhật nhật ký. Nếu kết quả khác dự kiến, dừng và khôi phục trạng thái an toàn trước khi thử cách khác.
