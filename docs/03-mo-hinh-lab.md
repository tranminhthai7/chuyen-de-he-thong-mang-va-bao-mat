# Mô hình lab và thiết kế dự kiến

> Đây là thiết kế khái niệm để xin duyệt, không phải hướng dẫn cấu hình. Chưa có địa chỉ IP, phiên bản phần mềm, luật firewall hoặc lệnh triển khai nào được chốt.

## 1. Mục đích

Tạo một môi trường ảo có thể quan sát ranh giới giữa vùng ngoài mô phỏng, DMZ và LAN; kiểm tra các chính sách truy cập được duyệt mà không gửi lưu lượng tới mạng thật.

## 2. Sơ đồ khái niệm

```text
Máy khách ngoài mô phỏng
          |
  Switch ảo Outside (internal)
          |
     WAN [pfSense]
       /       \
   DMZ         LAN
    |            |
Switch ảo     Switch ảo
DMZ (internal) LAN (internal)
    |            |
Máy chủ demo   Máy khách demo
```

Mỗi switch ảo phải là mạng internal/host-only không bridge tới card mạng vật lý. WAN trong sơ đồ là “outside” giả lập, không phải Internet thật. Giao diện quản trị chỉ được dùng qua console của VM hoặc một đường quản trị riêng được giảng viên duyệt.

## 3. Thành phần dự kiến

- Một VM firewall pfSense với các giao diện ảo riêng cho Outside/WAN, LAN và DMZ.
- Một VM máy khách LAN với dữ liệu giả.
- Một VM máy chủ demo trong DMZ, chỉ chạy dịch vụ cần thiết cho ca kiểm thử.
- Một VM máy khách Outside để kiểm tra từ vùng ngoài mô phỏng.
- Hypervisor: VirtualBox hoặc VMware; chưa chốt vì cần kiểm tra cấu hình máy và yêu cầu môn học.

Không cần tải hoặc lưu ảnh cài đặt trong repo trước khi lựa chọn được phiên bản, nguồn tải chính thức, giấy phép và yêu cầu phần cứng.

## 4. Nguyên tắc kết nối

- Ba vùng mạng phải là các mạng ảo tách biệt; không tạo bridge ra mạng thật.
- Không bật chia sẻ clipboard, thư mục, USB hoặc chế độ NAT ra Internet nếu chưa đánh giá và duyệt.
- Dùng địa chỉ thuộc dải riêng dành cho lab, nhưng chỉ chốt dải sau khi kiểm tra không trùng các mạng đang sử dụng.
- Không ghi mật khẩu quản trị thật trong tài liệu; dùng placeholder và lưu bí mật ngoài Git.
- Có bản sao/ảnh chụp VM sạch và quy trình khôi phục trước khi bắt đầu cấu hình.

## 5. Ma trận luồng dự kiến

| Nguồn | Đích | Dịch vụ | Hành động dự kiến | Trạng thái |
| --- | --- | --- | --- | --- |
| Outside mô phỏng | LAN | Không có nhu cầu công khai đã xác nhận | Từ chối | Đề xuất; cần duyệt |
| Outside mô phỏng | Máy chủ DMZ | Chỉ dịch vụ demo được duyệt | Cho phép đúng dịch vụ | Cần xác định dịch vụ |
| DMZ | LAN | Không cần luồng quản trị/dữ liệu trong demo | Từ chối mặc định | Đề xuất; cần duyệt |
| LAN | Máy chủ DMZ | Chỉ luồng phục vụ kiểm thử | Theo chính sách cụ thể | Cần xác định |
| Máy quản trị | pfSense | Giao diện quản trị | Chỉ cho phép nguồn quản trị được duyệt | Cần chốt cách quản trị |

Bảng này mô tả ý định, chưa phải luật cấu hình. Cần xác định dịch vụ, chiều khởi tạo kết nối, logging và yêu cầu thiết yếu trước khi tạo rule.

## 6. Kiểm tra cô lập trước khi chạy

1. Xác nhận từng adapter của VM gắn đúng switch ảo internal/host-only.
2. Xác nhận không adapter nào ở chế độ Bridged và không có route ra mạng vật lý/Internet.
3. Chụp lại cấu hình mạng ảo và lưu minh chứng đã loại bỏ thông tin cá nhân.
4. Nếu có dấu hiệu kết nối ra ngoài lab, dừng VM và hỏi giảng viên.

## 7. Tiêu chí chọn công cụ, chưa chốt phiên bản

Đánh giá pfSense và hypervisor theo: hỗ trợ nhiều interface ảo; tài liệu chính thức; khả năng xuất/xem log; yêu cầu CPU/RAM/dung lượng; khả năng snapshot/rollback; điều khoản sử dụng; và khả năng vận hành trên máy nhóm. Ghi nguồn/ngày kiểm tra trước khi quyết định.
