# Bài tập lớn An ninh mạng

## Trạng thái

- Tên đề tài đang xin ý kiến giảng viên: **Thiết kế và đánh giá mô hình tường lửa pfSense cho mạng doanh nghiệp nhỏ với phân vùng LAN/DMZ và kiểm soát truy cập**.
- Tên đề tài và phạm vi vẫn là đề xuất, chưa được giảng viên phê duyệt.
- Repo local tại `D:\chuyen-de-he-thong-mang-va-bao-mat`; GitHub public: https://github.com/tranminhthai7/chuyen-de-he-thong-mang-va-bao-mat. Nhánh `main` đã được push và theo dõi `origin/main`.
- Giai đoạn hiện tại: đọc tài liệu, xây nền tảng lý thuyết, chốt phạm vi và xin duyệt. Chưa có cấu hình firewall hay thử nghiệm.

## Nguyên tắc bắt buộc

Đọc [nguyên tắc an toàn và chống suy đoán](docs/00-nguyen-tac-an-toan.md) trước khi thêm hướng dẫn thực hành. Mọi hoạt động kỹ thuật phải nằm trong lab ảo do nhóm tự quản lý, có phạm vi được giảng viên chấp thuận và không tác động đến mạng thật.

## Thứ tự tài liệu

1. [Nền tảng lý thuyết](docs/01-nen-tang-ly-thuyet.md)
2. [Phạm vi, mục tiêu và yêu cầu](docs/02-pham-vi-va-yeu-cau.md)
3. [Mô hình lab và thiết kế](docs/03-mo-hinh-lab.md)
4. [Nguyên tắc bảo mật và quy tắc cấu hình](docs/04-nguyen-tac-bao-mat.md)
5. [Quy trình thực hiện và kiểm chứng](docs/05-quy-trinh-thuc-hien.md)
6. [Quy tắc Git và nhật ký công việc](docs/06-quy-tac-git.md)
7. [Nguồn tài liệu và trạng thái xác minh](docs/07-nguon-tham-khao.md)
8. [Đề xuất gửi giảng viên xin duyệt](docs/08-de-xuat-gui-giang-vien.md)
9. [Cấu trúc gói nộp](docs/09-cau-truc-goi-nop.md)
10. [Nhật ký công việc](docs/10-nhat-ky.md)
11. [Ma trận yêu cầu](docs/11-ma-tran-yeu-cau.md)
12. [Bảng thuật ngữ](docs/12-bang-thuat-ngu.md)
13. [Phiếu quyết định](docs/13-phieu-quyet-dinh.md)
14. [Kế hoạch báo cáo](docs/14-ke-hoach-bao-cao.md)
15. [Checklist xác minh nguồn](docs/15-checklist-nguon.md)

Checklist trước khi dựng lab/kiểm thử: `docs/checklist-truoc-khi-lam.md`.

## Cách dùng repo

- Ghi căn cứ nguồn trước khi ghi kết luận kỹ thuật.
- Ghi quyết định, thay đổi và kết quả kiểm thử vào tài liệu/nhật ký tương ứng.
- Không ghi mật khẩu, token, dữ liệu thật, địa chỉ nội bộ nhạy cảm hoặc thông tin cá nhân.
- Chỉ chuyển sang dựng lab sau khi giảng viên xác nhận đề tài/phạm vi và các yêu cầu chưa rõ đã được giải đáp.
