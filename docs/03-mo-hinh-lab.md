# Mô hình lab và thiết kế dự kiến

> Đây là phương án thiết kế nhóm đã chọn ngày 2026-11-05, chưa phải cấu hình triển khai. Địa chỉ DMZ đã được chọn ngày 2026-11-07; cần xác minh và ghi nhận sau khi cấu hình thực tế. Phiên bản phần mềm, luật firewall và lệnh triển khai vẫn cần hoàn thiện.

## 1. Mục đích

Tạo một môi trường ảo có thể quan sát ranh giới giữa vùng ngoài mô phỏng, DMZ và LAN; kiểm tra các chính sách truy cập nhóm đã chốt mà không gửi lưu lượng tới mạng thật.

## 2. Sơ đồ khái niệm

```text
Máy khách ngoài mô phỏng
          |
  Switch ảo Outside (internal)
          |
  WAN [pfSense]------ Host-Only (quản trị từ máy chủ)
       /       \
    DMZ         LAN
     |            |
Switch ảo     Switch ảo
DMZ (internal) LAN (internal)
     |            |
Máy chủ demo   Máy khách demo
```

Nhóm chọn VirtualBox. OUTSIDE, LAN và DMZ là ba mạng `Internal Network` riêng biệt; WAN chỉ nối vào OUTSIDE mô phỏng, không phải Internet thật. Giao diện quản trị đi qua interface thứ tư của pfSense nối với mạng `Host-Only` riêng để truy cập từ máy chủ; không tạo VM quản trị riêng. Mọi adapter phải được kiểm tra để chắc chắn không ở chế độ Bridged và không có NAT/route ra ngoài.

## 3. Thành phần dự kiến

- Một VM firewall pfSense CE với bốn giao diện ảo: OUTSIDE/WAN, LAN, DMZ và MGMT.
- Một VM máy khách LAN với dữ liệu giả.
- Một VM máy chủ demo trong DMZ, chỉ chạy dịch vụ cần thiết cho ca kiểm thử.
- Một VM máy khách Outside để kiểm tra từ vùng ngoài mô phỏng.
- Hypervisor: VirtualBox; phiên bản cụ thể và yêu cầu tài nguyên cần xác minh trước khi cài.

Không cần tải hoặc lưu ảnh cài đặt trong repo trước khi lựa chọn được phiên bản, nguồn tải chính thức, giấy phép và yêu cầu phần cứng.

## 4. Nguyên tắc kết nối

- OUTSIDE, LAN và DMZ phải là các mạng `Internal Network` tách biệt; MGMT dùng một mạng `Host-Only` riêng. Không tạo bridge ra mạng thật.
- Kế hoạch địa chỉ hiện tại: LAN `192.168.1.0/24` (pfSense `192.168.1.1`), DMZ `192.168.10.0/24` (pfSense `192.168.10.1`), MGMT Host-Only `192.168.56.0/24` (pfSense `192.168.56.2`). Mạng MGMT được chọn sau khi kiểm tra DHCP VirtualBox; DHCP của pfSense tắt trên MGMT. Chưa cấu hình IP cho DMZ cho đến khi xác nhận địa chỉ thực tế trên console.
- Không bật chia sẻ clipboard, thư mục, USB hoặc chế độ NAT ra Internet nếu chưa đánh giá và duyệt.
- Dùng địa chỉ thuộc dải riêng dành cho lab, nhưng chỉ chốt dải sau khi kiểm tra không trùng các mạng đang sử dụng.
- Không ghi mật khẩu quản trị thật trong tài liệu; dùng placeholder và lưu bí mật ngoài Git.
- Có bản sao/ảnh chụp VM sạch và quy trình khôi phục trước khi bắt đầu cấu hình.

## 5. Ma trận luồng dự kiến

| Nguồn | Đích | Dịch vụ | Hành động dự kiến | Trạng thái |
| --- | --- | --- | --- | --- |
| Outside mô phỏng | LAN | Không có nhu cầu công khai | Từ chối | Nhóm đã chọn; cần kiểm chứng |
| Outside mô phỏng | Máy chủ DMZ | Web demo (HTTP/HTTPS tùy cấu hình được xác minh) | Chỉ cho phép dịch vụ demo | Nhóm đã chọn luồng; cần chốt dịch vụ/cổng |
| DMZ | LAN | Không có nhu cầu trong demo | Từ chối mặc định | Nhóm đã chọn; cần kiểm chứng |
| LAN | Máy chủ DMZ | Chưa xác định nhu cầu | Từ chối cho tới khi có lý do và ca kiểm thử | Chưa chốt |
| Máy chủ (host) qua MGMT | pfSense | Giao diện quản trị | Chỉ cho phép trên Host-Only; các vùng khác không được quản trị | Nhóm đã chọn cách quản trị; cần xác minh cấu hình |

Bảng này mô tả chính sách dự kiến, chưa phải luật cấu hình. Cần xác minh dịch vụ, chiều khởi tạo kết nối, logging và yêu cầu thiết yếu trước khi tạo rule.

## 6. Kiểm tra cô lập trước khi chạy

1. Xác nhận từng adapter của VM gắn đúng switch ảo internal/host-only.
2. Xác nhận không adapter nào ở chế độ Bridged và không có route ra mạng vật lý/Internet.
3. Chụp lại cấu hình mạng ảo và lưu minh chứng đã loại bỏ thông tin cá nhân.
4. Nếu có dấu hiệu kết nối ra ngoài lab, dừng VM và hỏi giảng viên.

## 7. Việc cần xác minh trước khi cài đặt

Tra cứu tài liệu chính thức để xác minh phiên bản, yêu cầu CPU/RAM/dung lượng, khả năng dùng bốn interface ảo, xem log, snapshot/rollback và điều khoản sử dụng. Ghi nguồn/ngày kiểm tra; nếu cấu hình máy không đáp ứng, điều chỉnh số VM/mô hình và cập nhật quyết định trước khi cài đặt.
