# 02. Chuẩn BIM nội bộ (Naming, LOD, Coordination, QC)

Nguồn: "ENG REVIT Manual Interno" (BIM Execution Plan & Modeling Manual) do người dùng cung cấp. Đây là quy chuẩn mẫu — nếu công ty người dùng có mã bộ môn hoặc cú pháp khác, **ưu tiên theo quy định thực tế của công ty**, không áp cứng mẫu dưới đây.

## 1. Quy tắc đặt tên file dự án
Cú pháp bắt buộc:
```
[Mã Dự Án]_[Bộ Môn]_[Giai Đoạn]_[Khối/Tòa Nhà].rvt
```
- Mã Dự Án: tối đa 4–6 ký tự chữ/số.
- Mã Bộ Môn: `ARC` (Kiến trúc), `STR` (Kết cấu), `MEP` (Cơ điện), `SIT` (Địa hình/Quy hoạch).
- Ví dụ: `PRJX_ARC_DD_BLKA.rvt` = Dự án X – Kiến trúc – Thiết kế thi công – Tháp A.

## 2. Quy tắc đặt tên Family & Vật liệu
- Family tùy chỉnh: `[Tên Công ty]_[Hạng mục]_[Tên Chi tiết]`, ví dụ `ENG_Door_DoubleGlass`.
- Vật liệu: `[Mã Bộ Môn]_[Loại vật liệu]_[Màu sắc/Bề mặt]`, ví dụ `ARC_Conc_ExposedGray`.
- Chi tiết hơn về family xem `03_Family_Standard.md`.

## 3. Phối hợp liên bộ môn & tọa độ chung
- File `SIT` (Site) giữ gốc tọa độ trắc địa thực (Survey Point). Các bộ môn ARC/STR/MEP khởi tạo từ template chuẩn công ty, **không di chuyển Project Base Point** sau khi đã chốt.
- Link file Kiến trúc vào bộ môn khác: `Auto - Internal Origin to Internal Origin`, hoặc `Auto - By Shared Coordinates` nếu đã gán tọa độ chung.
- Copy/Monitor (`Collaborate → Copy/Monitor → Select Link`): áp dụng cho Grid Lines, Levels, Columns/Walls chịu lực — các cấu kiện dùng chung giữa các bộ môn. Khi file gốc đổi vị trí trục/tầng, Revit cảnh báo Coordination Review để đồng bộ lại.

## 4. Mức độ phát triển mô hình (LOD) theo giai đoạn
| Giai đoạn | LOD | Yêu cầu mô hình hóa |
|---|---|---|
| Thiết kế cơ sở | LOD 200 | Cấu kiện dạng khối tổng quát, đúng vị trí và cao độ cơ bản, chưa chi tiết cấu tạo lớp. |
| Thiết kế kỹ thuật | LOD 300 | Tường, sàn có đầy đủ lớp cấu tạo (Composite Layers); dầm, cột đúng tiết diện danh định. |
| Thiết kế thi công | LOD 350/400 | Đầy đủ chi tiết gờ nhô, lỗ mở kỹ thuật (MEP openings), vạt góc, vị trí chờ kết cấu. |

Khi dựng mô hình, luôn hỏi người dùng dự án đang ở giai đoạn nào nếu chưa rõ, vì mức độ chi tiết cần dựng khác nhau hoàn toàn.

## 5. Kiểm soát chất lượng mô hình (Model Audit) — bắt buộc trước khi giao file
1. **Interference Check:** `Collaborate → Interference Check → Run Interference Check`, chọn nhóm đối tượng cần kiểm tra xung đột (ví dụ MEP Pipes/Ducts vs. Structural Beams/Walls), xuất báo cáo `.html`.
2. **Purge Unused:** `Manage → Purge Unused`, thực hiện 2–3 lần liên tiếp đến khi không còn gì để xóa.
3. **Review Warnings:** `Manage → Warnings`, sửa triệt để các cảnh báo (tường chồng lấn, phòng không khép kín...).
4. **Save with Audit:** đóng file → Open → tích `Audit` trước khi mở, để Revit tự sửa lỗi hệ thống file.

## 6. Quy ước đánh số bản vẽ (Sheet Numbering)
- `A-101`: Mặt bằng Kiến trúc
- `S-101`: Mặt bằng Kết cấu
- `M-101`: Mặt bằng Cơ điện

## 7. Xuất file DWG chuẩn hóa
- `File → Export → CAD Formats → DWG`.
- Tại `Modify DWG Export Setup`: gán đúng layer Revit tương ứng layer AutoCAD của công ty.
- Đổi nét vẽ sang `Preserve overriding - graphics view` để giữ nguyên nét đậm/nhạt đã thiết lập trong Revit.

## 8. TCVN 5570:2012 — Tiêu chuẩn thể hiện bản vẽ xây dựng và kết cấu
Nguồn chính thức, dùng khi tạo family ký hiệu trục/cao độ, thiết lập Line Weight, hoặc dàn trang Sheet.

**Ký hiệu trục (Grid Bubble):** đường kính vòng tròn trục 8–10 mm trên bản vẽ. Trục dọc đánh số (1, 2, 3...), trục ngang đánh chữ hoa (A, B, C...).

**Nét vẽ (Line Weight):**
| Loại nét | Bề dày |
|---|---|
| Nét thấy / khung bao | 0,35–0,5 mm (đậm) |
| Nét cắt cấu kiện | 0,5–0,7 mm (rất đậm) |
| Nét dóng, nét kích thước, nét khuất | 0,13–0,18 mm (mảnh) |

**Tỷ lệ bản vẽ tiêu chuẩn:**
| Loại bản vẽ | Tỷ lệ |
|---|---|
| Mặt bằng tổng thể | 1:500, 1:200 |
| Mặt bằng/mặt đứng/mặt cắt kiến trúc, kết cấu | 1:100, 1:50 |
| Chi tiết cấu kiện (dầm, cột, thép) | 1:20, 1:10, 1:5 |

**Khung tên bản vẽ:** đặt ở góc dưới bên phải trang giấy. Bắt buộc có: tên dự án, tên bản vẽ, mã ký hiệu bản vẽ (ví dụ `ARC-FL01`, `STR-BE01` — khớp quy tắc Sheet Numbering ở mục 6), tỷ lệ, lần sửa đổi (Revision), chữ ký tác giả và người phê duyệt.

## Áp dụng khi thao tác qua MCP
- Trước khi tạo file/element mới, kiểm tra tên đã theo đúng cú pháp ở mục 1–2 chưa; nếu người dùng không cho biết mã dự án/bộ môn, hỏi lại thay vì tự đặt tên.
- Trước khi báo "xong", luôn chạy tối thiểu bước Review Warnings (mục 5.3) trên phần vừa dựng và báo lại cho người dùng nếu có cảnh báo mới phát sinh.
