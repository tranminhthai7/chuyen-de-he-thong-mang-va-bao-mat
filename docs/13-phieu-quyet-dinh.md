# Phiếu quyết định và câu hỏi chưa chốt

Dùng mẫu này để ghi lại quyết định có căn cứ. Mỗi mục quan trọng cần trạng thái: `Đề xuất`, `Đã xác nhận`, `Bác bỏ`, hoặc `Cần xác minh`.

| ID | Câu hỏi/quyết định | Trạng thái | Căn cứ/nguồn | Người xác nhận | Ngày | Hệ quả/việc tiếp theo |
| --- | --- | --- | --- | --- | --- | --- |
| D01 | Tên đề tài làm việc | Nhóm đã chốt; chưa phải tên chính thức được xác nhận | Tên trong đề xuất hiện tại | Người dùng/nhóm | 2026-11-05 | Đối chiếu quy định tên/bìa trước khi nộp |
| D02 | pfSense CE hay FortiGate-VM | Nhóm chọn pfSense CE | S06, đề tài 13 | Người dùng/nhóm | 2026-11-05 | Xác minh phiên bản, yêu cầu máy và điều khoản |
| D03 | Hypervisor | Nhóm chọn VirtualBox | Phương án lab hiện tại | Người dùng/nhóm | 2026-11-05 | Xác minh phiên bản và khả năng chạy trên máy |
| D04 | Kết nối lab ra Internet | Không kết nối Internet thật | Ranh giới an toàn của lab | Người dùng/nhóm | 2026-11-05 | Chỉ dùng mạng ảo cô lập; kiểm tra adapter trước khi chạy |
| D05 | Phân vùng mạng | OUTSIDE, LAN, DMZ dùng các `Internal Network` riêng; MGMT dùng `Host-Only`; không triển khai VLAN trong mô hình tối thiểu | Thiết kế bốn interface trong đề xuất | Người dùng/nhóm | 2026-11-05 | Xác minh topology, không bridge/NAT/route ra ngoài |
| D06 | Slide 4 tối thiểu hay 25-40 | Chưa chốt; tạm chuẩn bị theo mức 25-40 nêu trong S06 | S06 và S07 mâu thuẫn | Nhóm; cần đối chiếu yêu cầu môn | Chưa có | Chưa hoàn thiện slide cuối |
| D07 | Quy mô và ca kiểm thử | Nhóm chọn bốn VM; kiểm tra dịch vụ web bình thường và các luồng cần từ chối | Đề xuất lab hiện tại | Người dùng/nhóm | 2026-11-05 | Chốt dịch vụ/cổng sau khi xác minh; không kiểm thử ngoài lab |
| D08 | Gửi cấu hình/log hay chỉ video/ảnh | Chưa xác định | S07 chưa nêu rõ chi tiết này | Nhóm; đối chiếu hướng dẫn nộp | Chưa có | Chỉ đưa minh chứng đã làm sạch và được phép chia sẻ |
| D09 | Cách quản trị pfSense | Interface MGMT riêng qua Host-Only, truy cập từ máy chủ; không tạo VM quản trị thứ năm | Đề xuất bốn interface | Người dùng/nhóm | 2026-11-05 | Xác minh Host-Only không nối mạng vật lý |
| D10 | Địa chỉ mạng DMZ | Chọn `192.168.10.0/24`; pfSense OPT1 dự kiến `192.168.10.1/24`; DHCP DMZ tạm tắt | Dải riêng, khác LAN `192.168.1.0/24` và MGMT `192.168.56.0/24` | Người dùng | 2026-11-07 | Cấu hình OPT1 trong pfSense rồi xác minh địa chỉ; quyết định IP không đồng nghĩa đã triển khai |

## Mẫu ghi quyết định mới

```text
ID:
Ngày:
Quyết định:
Trạng thái:
Căn cứ (mã nguồn + trang/mục/URL):
Người xác nhận:
Ảnh hưởng:
Việc tiếp theo:
```

Không xóa quyết định cũ; nếu thay đổi, thêm quyết định mới trỏ tới ID trước để giữ dấu vết.
