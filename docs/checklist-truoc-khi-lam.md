# Checklist trước khi bắt đầu

## A. Trước khi chốt đề tài

- [ ] Đã hỏi giảng viên về tên đề tài và phạm vi.
- [ ] Đã xác nhận pfSense có được phép dùng không.
- [ ] Đã xác nhận hypervisor/máy được dùng và yêu cầu tài nguyên.
- [ ] Đã làm rõ yêu cầu slide 4 tối thiểu hay 25-40.
- [ ] Đã thống nhất yêu cầu báo cáo, minh chứng và nội dung gói nộp.

## B. Trước khi dựng lab

- [ ] Có sơ đồ và ma trận luồng được duyệt.
- [ ] Có tài liệu phiên bản/phần mềm từ nguồn chính thức.
- [ ] Tất cả network adapter là internal/host-only; không bridge.
- [ ] Không có route/NAT ra Internet ngoài phê duyệt.
- [ ] Có snapshot/backup và đường khôi phục.
- [ ] Dữ liệu là giả lập, không có secret hoặc dữ liệu cá nhân.
- [ ] Cách quản trị firewall không làm lộ management ra mạng thật.

## C. Trước từng thay đổi/kiểm thử

- [ ] Mục tiêu, căn cứ và kết quả mong đợi đã ghi.
- [ ] Ca kiểm thử nằm trong phạm vi được duyệt và dùng lưu lượng bình thường.
- [ ] Đã backup cấu hình trước thay đổi.
- [ ] Có cách rollback.
- [ ] Không dùng exploit, malware, phishing, credential attacks, scanning/flooding ngoài lab.
- [ ] Có log/bằng chứng cần thiết và đã biết cách làm sạch dữ liệu.

## D. Trước commit/nộp

- [ ] Đã xem `git status`, diff và `git diff --check`.
- [ ] Không có password/token/cookie/private key/dữ liệu cá nhân.
- [ ] Thông điệp commit tiếng Việt theo Conventional Commits và mô tả đúng việc thật.
- [ ] `origin` chỉ trỏ đến repo GitHub Public đã được người dùng duyệt.
- [ ] Đã rà nội dung/metadata public; không có secret hoặc dữ liệu thật.
- [ ] Push đúng nhánh `main`; không thêm remote khác.
- [ ] Báo cáo ghi cả hạn chế và lỗi kiểm thử; không tuyên bố vượt quá bằng chứng.
