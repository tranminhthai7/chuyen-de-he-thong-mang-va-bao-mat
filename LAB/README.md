# Khung LAB

## Trạng thái

Đây là khung thư mục cho mô hình pfSense/LAN/DMZ dự kiến. Đề tài và lab chưa được giảng viên phê duyệt; chưa có VM, cấu hình hay dữ liệu thử nghiệm.

## Cây thư mục

```text
LAB/
|-- topology/       # Sơ đồ và mô tả vùng mạng đã duyệt
|-- firewall/       # Phiên bản, thiết kế rule và ghi chú cấu hình
|   `-- private/    # Cấu hình riêng/nhạy cảm, local-only
|-- hosts/          # Vai trò máy khách/máy chủ giả lập
|-- tests/          # Ca kiểm thử bình thường và tiêu chí pass/fail
|-- evidence/       # Minh chứng đã làm sạch
|   |-- raw/        # Log/capture thô, local-only
|   `-- screenshots/ # Ảnh chụp thô, local-only
|-- local-data/     # Dữ liệu tổng hợp phục vụ lab, local-only
`-- exports/        # Bản xuất/cấu hình tạm, local-only
```

## Trước khi thêm nội dung

1. Được giảng viên duyệt tên đề tài, sơ đồ và phạm vi.
2. Hoàn thành checklist cô lập trong `../docs/checklist-truoc-khi-lam.md`.
3. Chỉ dùng lưu lượng và dữ liệu giả trong mạng ảo cô lập.
4. Kiểm tra `.gitignore` với `git check-ignore -v <đường-dẫn>` trước khi lưu artefact nhạy cảm.
5. Không xem `.gitignore` là cơ chế bảo mật: file đã tracked vẫn có thể được commit và push.

Không lưu image VM, secret, mật khẩu, dữ liệu cá nhân hoặc capture từ mạng thật trong Git.
