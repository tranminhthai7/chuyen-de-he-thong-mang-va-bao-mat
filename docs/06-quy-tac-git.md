# Quy tắc Git local và nhật ký

## 1. Phạm vi repo

- Repo nằm ở `D:\chuyen-de-he-thong-mang-va-bao-mat` và chỉ dùng local theo yêu cầu hiện tại.
- Không thêm `origin`/remote, không push, không tạo repo công khai/riêng trên GitHub.
- Không chia sẻ repo/tài liệu qua cloud hoặc dịch vụ ngoài nếu chưa được nhóm/giảng viên cho phép.
- Nhánh local hiện tại là `main`; repo chưa có commit và chưa có remote.

## 2. Quy tắc commit

- Commit sau mỗi phần việc logic có thể kiểm tra độc lập, chẳng hạn nền tảng lý thuyết, yêu cầu/phạm vi, hoặc thiết kế lab; không đợi tới cuối bài mới commit một lần.
- Mục tiêu là ghi nhận hoạt động thường xuyên khi có thay đổi thật, thường mỗi ngày làm việc có kết quả. Không bắt buộc commit mỗi ngày nếu không có thay đổi; không tạo commit rỗng hay ghi việc chưa làm.
- Mỗi commit nên nhỏ, tập trung một loại thay đổi, và có trạng thái kiểm tra rõ. Không trộn lý thuyết, cấu hình thực nghiệm và sửa định dạng không liên quan.
- Trước commit: xem `git status`, `git diff --check`, `git diff`; rà secret/dữ liệu cá nhân và xác nhận file được phép đưa vào repo.
- Chỉ stage file cụ thể; tránh `git add .` khi chưa rà soát toàn bộ.

## 3. Chuẩn thông điệp commit

Dùng tiền tố Conventional Commits, phần mô tả bằng tiếng Việt, ngắn gọn và nêu hành động:

```text
docs: bổ sung nền tảng lý thuyết về firewall
docs: ghi phạm vi đề tài và câu hỏi cần giảng viên duyệt
chore: thêm khung nhật ký công việc
fix: sửa nhầm lẫn giữa NAT và firewall
```

- `docs`: tài liệu; `feat`: tính năng/lab mới đã duyệt; `fix`: sửa lỗi; `test`: kiểm thử; `chore`: bảo trì repo.
- Dùng động từ ở đầu phần mô tả: `bổ sung`, `cập nhật`, `sửa`, `ghi nhận`, `loại bỏ`.
- Không dùng nội dung mơ hồ như `update`, `done`, `fix stuff`.
- Nếu đề tài chưa được duyệt, commit tài liệu phải diễn đạt là đề xuất/dự thảo, không khẳng định đã triển khai.

## 4. Ví dụ quy trình PowerShell

```powershell
git -C D:\chuyen-de-he-thong-mang-va-bao-mat status --short --branch
git -C D:\chuyen-de-he-thong-mang-va-bao-mat diff --check
git -C D:\chuyen-de-he-thong-mang-va-bao-mat diff -- docs\01-nen-tang-ly-thuyet.md
git -C D:\chuyen-de-he-thong-mang-va-bao-mat add docs\01-nen-tang-ly-thuyet.md
git -C D:\chuyen-de-he-thong-mang-va-bao-mat diff --cached --check
git -C D:\chuyen-de-he-thong-mang-va-bao-mat diff --cached
git -C D:\chuyen-de-he-thong-mang-va-bao-mat commit -m "docs: bổ sung nền tảng lý thuyết về firewall"
```

Không chạy `git push`, `git remote add`, hoặc lệnh xóa/sửa lịch sử. Nếu sau này cần nộp GitHub, phải xin người dùng xác nhận riêng về remote, quyền riêng tư và nội dung được phép công khai.

## 5. Nhật ký

Mỗi ngày làm việc có thay đổi phải ghi vào `docs/10-nhat-ky.md`: ngày, mục tiêu, việc đã làm, file/commit liên quan, kiểm tra đã chạy, kết quả, vướng mắc và việc tiếp theo. Ghi cả điều chưa hoàn thành; không viết lùi ngày để tạo cảm giác hoạt động liên tục.
