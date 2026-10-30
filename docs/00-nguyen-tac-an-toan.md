# Nguyên tắc an toàn, phạm vi và chống suy đoán

## 1. Mục đích

Tài liệu này là ràng buộc cao nhất cho việc học, thiết kế và thực hiện bài tập lớn. Khi tài liệu môn học, chỉ dẫn của giảng viên và giả định cá nhân mâu thuẫn, phải dừng phần bị ảnh hưởng và xin giảng viên xác nhận; không tự chọn cách hiểu thuận tiện.

## 2. Cách phân biệt thông tin

Mọi nội dung trong repo phải thuộc một trong các loại sau:

- **Đã có căn cứ:** ghi nguồn và vị trí cụ thể (tên tài liệu, chương/mục/trang hoặc URL).
- **Đề xuất:** phương án nhóm muốn xin duyệt, không trình bày như yêu cầu chính thức.
- **Cần xác nhận:** thông tin tài liệu chưa nói rõ hoặc nguồn không truy cập được.
- **Kết quả thực nghiệm:** chỉ ghi sau khi chạy trong lab; kèm ngày, cấu hình liên quan và bằng chứng không chứa bí mật.

Không biến tiêu đề URL, tên file, nội dung xem trước hoặc suy đoán thành nội dung của tài liệu chưa đọc. Không trích dẫn một nguồn chưa xác minh như thể đã đọc toàn văn.

## 3. Ranh giới thực hành

- Chỉ sử dụng máy ảo, mạng host-only/internal hoặc môi trường mô phỏng được nhóm kiểm soát; không bridge vào mạng trường, mạng gia đình/công ty hay Internet công cộng khi chưa có phê duyệt rõ ràng.
- Mục tiêu chỉ là kiểm tra chính sách firewall bằng máy khách/máy chủ thử nghiệm do nhóm tạo: kết nối nào được phép, kết nối nào bị từ chối, log nào được ghi.
- Không quét, dò, khai thác, xác thực thử, gây tải, nghe lén hoặc thay đổi hệ thống/địa chỉ IP không thuộc lab và chưa được cho phép bằng văn bản.
- Không tạo hoặc chạy ransomware, worm, trojan, keylogger, backdoor, công cụ đánh cắp thông tin xác thực, trang phishing hay payload phá hoại. Mô phỏng hậu quả bằng dữ liệu giả và sơ đồ/quy trình, không dùng mã độc.
- Không thực hiện DoS/DDoS, flood, spoofing chủ động, session hijacking hoặc khai thác lỗ hổng thật. Nếu cần minh họa, chỉ dùng sơ đồ, log mẫu đã làm sạch hoặc kịch bản giả lập không phát sinh lưu lượng tấn công.
- Không tải/chạy file thực thi từ nguồn tài liệu không rõ xuất xứ. Không dùng bản quyền phần mềm/tài liệu vượt quá quyền truy cập được cấp.

## 4. Dữ liệu và bí mật

- Chỉ dùng dữ liệu tổng hợp/giả lập; tuyệt đối không đưa thông tin cá nhân, mật khẩu, khóa, token, cookie, IP công khai của bên thứ ba hoặc dữ liệu doanh nghiệp vào repo.
- Mọi bí mật cấu hình phải dùng placeholder, ví dụ `<LAB_PASSWORD>`; không commit file cấu hình có secret.
- Chỉ lưu log cần thiết. Làm sạch địa chỉ, định danh và dữ liệu nhạy cảm trước khi đưa vào báo cáo.

## 5. Điều kiện dừng

Dừng thử nghiệm và cô lập lab ngay nếu thấy lưu lượng rời khỏi mạng ảo, phát hiện thiết bị không thuộc nhóm, cấu hình làm ảnh hưởng máy chủ/mạng thật, hoặc xuất hiện dữ liệu không được phép. Ghi lại sự cố không chứa bí mật và báo giảng viên trước khi tiếp tục.

## 6. Phê duyệt trước khi triển khai

Trước khi dựng hoặc chạy lab, cần có xác nhận về: tên đề tài; sơ đồ/phạm vi lab; công cụ và phiên bản; loại kiểm thử được phép; tiêu chí đánh giá; yêu cầu lưu log/minh chứng; và quy định nộp bài. Các nội dung này hiện là **cần xác nhận**, trừ khi tài liệu môn học đã nêu cụ thể.

## 7. Quy tắc Git

- Repo local-only; không thêm remote, push, publish hay chia sẻ công khai trong phạm vi công việc hiện tại.
- Commit nhỏ, theo một mục tiêu rõ, sau khi nội dung được rà soát; ghi đúng những gì đã thay đổi.
- Không ghi hoạt động chưa làm vào nhật ký/commit; không tạo commit giả để lấp ngày trống.
- Giữ working tree có tổ chức, xem `git status` và diff trước khi commit; không commit secrets, bản cài đặt lớn hoặc tài liệu chưa được phép chia sẻ.
