# Cấu trúc gói nộp và cây thư mục dự kiến

## 1. Căn cứ

Quy định hình thức BTL do người dùng cung cấp yêu cầu file nén có thư mục gốc `Mã nhóm_Tên đề tài`, gồm SETUP, SOURCE, THESIS, SOFT và `HUONGDAN.PDF`. Cấu trúc chính thức phải đối chiếu lại với giảng viên, đặc biệt tên đề tài và slide.

## 2. Cây gói nộp dự kiến

```text
<Mã nhóm>_<TEN_DE_TAI>/
|-- SETUP/
|   |-- README.md
|   `-- (chỉ file cần để cài/chạy demo, sau khi duyệt)
|-- SOURCE/
|   |-- README.md
|   `-- (mã nguồn/dữ liệu giả; hiện chưa có code)
|-- THESIS/
|   |-- Bao_cao.docx
|   |-- Bao_cao.pdf
|   `-- Slide_bao_cao.pptx
|-- SOFT/
|   |-- README.md
|   `-- (chỉ phần mềm được phép phân phối; còn lại ghi link chính thức)
`-- HUONGDAN.PDF
```

Không tạo/đưa binary cài đặt, sách có bản quyền hoặc file lớn lên Git nếu chưa xác minh quyền phân phối. Tài liệu nguồn có thể nằm ngoài kho; repo lưu danh sách nguồn, không lưu bản sao trái phép.

## 3. Cây repo local dự kiến

```text
chuyen-de-he-thong-mang-va-bao-mat/
|-- README.md
|-- docs/
|   |-- 00-nguyen-tac-an-toan.md
|   |-- 01-nen-tang-ly-thuyet.md
|   |-- 02-pham-vi-va-yeu-cau.md
|   |-- 03-mo-hinh-lab.md
|   |-- 04-nguyen-tac-bao-mat.md
|   |-- 05-quy-trinh-thuc-hien.md
|   |-- 06-quy-tac-git.md
|   |-- 07-nguon-tham-khao.md
|   |-- 08-de-xuat-gui-giang-vien.md
|   |-- 09-cau-truc-goi-nop.md
|   `-- 10-nhat-ky.md
|-- SETUP/       (tạo khi có demo được duyệt)
|-- SOURCE/      (tạo khi có nội dung được duyệt)
|-- THESIS/      (tạo khi bắt đầu soạn báo cáo chính thức)
`-- SOFT/        (chỉ tạo nếu có tài liệu/phần mềm được phép)
```

## 4. Quy tắc phân loại

- `docs/`: tài liệu định hướng và quy trình của repo.
- `SETUP/`: hướng dẫn cài/chạy lab, không lưu secret.
- `SOURCE/`: mã nguồn do nhóm viết và dữ liệu tổng hợp.
- `THESIS/`: báo cáo, slide và phụ lục.
- `SOFT/`: danh mục/phần mềm được phép; ưu tiên link nhà cung cấp và checksum nếu yêu cầu.

Các thư mục giao nộp chỉ tạo khi có nội dung thật; không điền file giả để làm cây thư mục có vẻ hoàn chỉnh.
