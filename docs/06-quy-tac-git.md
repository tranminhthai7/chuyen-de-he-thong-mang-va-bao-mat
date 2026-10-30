# Quy tắc Git local và nhật ký

## 1. Phạm vi repo

- Repo local nằm ở `D:\chuyen-de-he-thong-mang-va-bao-mat`; remote được người dùng duyệt là `https://github.com/tranminhthai7/chuyen-de-he-thong-mang-va-bao-mat` (Public).
- Chỉ dùng `origin` trỏ tới URL trên; không thêm remote khác, không đổi visibility hoặc đẩy sang nơi khác nếu chưa được xác nhận riêng.
- Trước mỗi push, kiểm tra status, diff, secrets và xác nhận nhánh đích là `main`.
- Nhánh hiện tại là `main`; đã có ba commit local. Remote GitHub vừa được tạo và chưa nhận lịch sử local.

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

Không xóa/sửa lịch sử. Trước khi push, phải xác nhận `origin` đúng URL đã duyệt và rà soát nội dung vì repo Public. Không đưa secret hoặc dữ liệu thật vào commit.

## 5. Nhật ký

Mỗi ngày làm việc có thay đổi phải ghi vào `docs/10-nhat-ky.md`: ngày, mục tiêu, việc đã làm, file/commit liên quan, kiểm tra đã chạy, kết quả, vướng mắc và việc tiếp theo. Ghi cả điều chưa hoàn thành; không viết lùi ngày để tạo cảm giác hoạt động liên tục.
