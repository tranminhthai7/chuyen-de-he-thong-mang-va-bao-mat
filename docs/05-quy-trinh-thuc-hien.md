# Quy trình thực hiện và kiểm chứng

> Mỗi giai đoạn có cổng dừng. Phương án công nghệ và phạm vi lab đã được nhóm tự chốt; không coi đó là xác nhận chính thức của giảng viên. Không chuyển giai đoạn nếu yêu cầu môn học, tài nguyên hoặc điều kiện cô lập chưa được xác minh.

## Giai đoạn 0 - Ghi nhận phương án nhóm

- Ghi lựa chọn của nhóm: VirtualBox, pfSense CE, bốn VM, OUTSIDE/LAN/DMZ qua `Internal Network`, MGMT qua `Host-Only`, không nối Internet thật.
- Đối chiếu yêu cầu môn học và ghi riêng những nội dung chưa rõ, như mâu thuẫn về số slide.
- Ghi ngày, căn cứ và hệ quả của quyết định vào phiếu quyết định.

**Cổng 0:** phương án nhóm và các yêu cầu môn học đã biết được ghi rõ; mọi mâu thuẫn ảnh hưởng trực tiếp tới phạm vi phải được làm rõ trước khi thực hiện phần liên quan.

## Giai đoạn 1 - Đọc và lập cơ sở lý thuyết

- Đọc slide môn học đã nhận, giáo trình/trang học thuật truy cập hợp lệ và tài liệu chính thức của công cụ.
- Ghi từng mệnh đề cần dùng vào sổ nguồn; ghi trang/mục hoặc URL và ngày truy cập.
- Đánh dấu nội dung chưa mở được, lỗi thời, không chính thức hoặc chỉ là tin tức.

**Cổng 1:** thuật ngữ, mục tiêu, mô hình, giới hạn và nguồn được rà soát; không dùng nguồn chưa đọc để kết luận.

## Giai đoạn 2 - Đặc tả yêu cầu và thiết kế

- Chuyển yêu cầu môn học đã ghi nhận và lựa chọn nhóm thành bảng: mã yêu cầu, nguồn, lý do, vùng nguồn/đích, dịch vụ, hành động mong đợi, log, ca xác minh.
- Vẽ sơ đồ lab và ghi rõ interface, mạng ảo, đường quản trị và điểm cô lập.
- Xác định yêu cầu tài nguyên, phiên bản phần mềm, backup và khôi phục từ tài liệu chính thức.

**Cổng 2:** sơ đồ, ma trận, phiên bản dự kiến và phương án khôi phục đã được ghi; không nhập địa chỉ/cấu hình nếu chưa xác minh trùng lặp và tính phù hợp.

## Giai đoạn 3 - Chuẩn bị lab an toàn

- Dựng VM/switch ảo theo sơ đồ nhóm đã chốt.
- Kiểm tra kỹ không có bridged adapter, route ra mạng thật hoặc Internet ngoài phê duyệt.
- Chụp trạng thái sạch, xác nhận console/rollback, dùng dữ liệu giả.

**Cổng 3:** checklist cô lập đạt hoàn toàn. Nếu không chứng minh được, không chạy thử nghiệm.

## Giai đoạn 4 - Cấu hình có kiểm soát

- Sao lưu trước thay đổi.
- Cấu hình từng nhóm rule nhỏ theo ma trận đã chốt; ghi lý do và thứ tự.
- Không sao chép lệnh/config từ blog/forum nếu chưa đối chiếu tài liệu chính thức và phiên bản.
- Ghi lại thay đổi và cách quay về trạng thái trước.

**Cổng 4:** cấu hình quản trị và đường khôi phục được kiểm tra; rule khớp đặc tả.

## Giai đoạn 5 - Kiểm thử lưu lượng bình thường

Mỗi ca kiểm thử ghi: mã ca, mục tiêu, nguồn/đích, dịch vụ, điều kiện trước, hành động hợp lệ trong lab, kết quả mong đợi, kết quả thực tế, log/bằng chứng đã làm sạch, pass/fail và ghi chú.

- Thử ca được phép và ca cần bị từ chối bằng kết nối ứng dụng bình thường do nhóm tạo.
- Không dùng traffic flood, exploit, scanning ngoài scope, credential attack, malware hoặc kỹ thuật né tránh.
- Lặp lại ca quan trọng sau khi sửa rule.

**Cổng 5:** mọi sai lệch được ghi nhận; không che kết quả thất bại.

## Giai đoạn 6 - Phân tích và hoàn thiện

- So sánh kết quả với mục tiêu và tài liệu; giải thích lỗi/hạn chế.
- Viết kết luận có phạm vi: chỉ lab, phiên bản và ca đã thử.
- Rà soát nguồn, hình/log, bản quyền, bí mật, thông tin cá nhân và các yêu cầu định dạng.
- Tạo hướng dẫn chạy demo và kiểm tra trên máy sạch/ảnh snapshot nếu được phép.

## Giai đoạn 7 - Nộp bài

Theo quy định BTL đã nhận: chuẩn bị thư mục nộp SETUP/SOURCE/THESIS/SOFT/HUONGDAN.PDF, báo cáo Word tối thiểu 20 trang và slide. Danh sách đề tài nêu 25-40 slide trong khi quy định hình thức nêu tối thiểu 4 slide; phải xác nhận yêu cầu cụ thể với giảng viên và làm theo xác nhận mới nhất.
