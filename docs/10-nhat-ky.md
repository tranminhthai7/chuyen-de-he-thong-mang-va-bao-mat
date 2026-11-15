# Nhật ký công việc

Chỉ ghi việc đã thực hiện thật. Mỗi lần cập nhật nêu kiểm tra/kết quả; không ghi lùi ngày, không tạo commit rỗng để giả lập hoạt động.

## 2026-10-30

- **Mục tiêu:** khởi tạo repo local và tập hợp căn cứ để xin duyệt đề tài.
- **Đã làm:** tạo `D:\chuyen-de-he-thong-mang-va-bao-mat`; khởi tạo Git local; xem nội dung PDF Chương 1-5, danh sách đề tài và quy định báo cáo do người dùng dán; kiểm tra trang web truy cập được và ghi trạng thái link trong sổ nguồn.
- **Chưa làm:** chưa gửi đề xuất cho giảng viên; chưa dựng lab; chưa cấu hình firewall; chưa chạy kiểm thử; chưa có code.
- **Kiểm tra:** xác nhận repo chưa có commit/remote; kiểm tra README và nguyên tắc an toàn có các ranh giới local-only/lab-only.
- **Việc tiếp theo:** rà soát bộ tài liệu, sau đó người dùng/nhóm gửi đề xuất xin duyệt và cập nhật kết quả phản hồi.

## Cập nhật 2026-10-30

- **Đã làm:** người dùng đổi yêu cầu từ local-only sang tạo repo GitHub Public; repo `tranminhthai7/chuyen-de-he-thong-mang-va-bao-mat` đã được tạo rỗng.
- **Đã hoàn thành:** tạo repo GitHub Public, cấu hình `origin` đúng URL đã duyệt và push nhánh `main`; upstream là `origin/main`.
- **Lưu ý:** lịch sử commit sử dụng email author do người dùng cung cấp; repo Public khiến metadata này có thể xem công khai.
- **Kiểm tra tiếp theo:** xác nhận working tree sạch và repo local đồng bộ với remote.

## Cập nhật 2026-11-05

- **Mục tiêu:** ghi nhận phương án lab do nhóm tự chọn.
- **Đã làm:** chốt phương án làm việc gồm VirtualBox, pfSense CE, bốn VM; OUTSIDE/LAN/DMZ qua các mạng `Internal Network`, MGMT qua `Host-Only`, không nối Internet thật; cập nhật tài liệu phạm vi, mô hình, quy trình, ma trận yêu cầu, phiếu quyết định và checklist liên quan.
- **Trạng thái:** đây là quyết định nội bộ, không phải xác nhận chính thức từ giảng viên. Chưa cài VM, chưa cấu hình firewall và chưa chạy kiểm thử.
- **Kiểm tra:** rà các tài liệu đã cập nhật để bảo đảm phân biệt lựa chọn nhóm với yêu cầu chính thức; không commit hoặc push.
- **Việc tiếp theo:** xác minh phiên bản, điều khoản và yêu cầu tài nguyên từ nguồn chính thức; kiểm tra cấu hình máy và hoàn tất thiết kế mạng trước khi cài đặt.
