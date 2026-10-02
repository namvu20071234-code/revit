---
name: revit-vn-skill
description: Dùng khi dựng, kiểm tra, hoặc chỉnh sửa mô hình Revit cho công trình tại Việt Nam - bao gồm quy trình dựng (lưới trục, cao độ, cột, dầm, tường, sàn, mái, cửa), chọn vật liệu và cấu tạo lớp, đặt tên family/tham số theo chuẩn công ty, và tuân thủ TCVN/QCVN. Kích hoạt khi người dùng nhắc đến Revit, mặt bằng/mặt cắt/mặt đứng kiến trúc, kết cấu (cột/dầm/sàn/móng), MEP, hoặc yêu cầu kiểm tra theo TCVN/QCVN.
---

# Revit BIM Vietnam

Skill này chứa quy trình dựng mô hình, thư viện vật liệu, chuẩn family và các tiêu chuẩn TCVN/QCVN dùng cho mọi dự án Revit tại Việt Nam. Đây là nguồn tham chiếu bắt buộc, ưu tiên hơn kiến thức mặc định hoặc phỏng đoán.

## Nguyên tắc bắt buộc

- Luôn đọc file tham chiếu liên quan trước khi dựng hoặc chỉnh sửa mô hình, không dựng theo trí nhớ hoặc thông lệ chung chung.
- Nếu tài liệu không nói rõ một thông số (kích thước, lớp vật liệu, cao độ, tên tham số...), phải hỏi lại người dùng. Không tự giả định để lấp chỗ trống.
- Khi dựng cấu kiện mới (tường, sàn, cột, dầm, mái), đối chiếu với loại đã có sẵn trong file Revit trước, tránh tạo trùng loại.
- Đơn vị làm việc mặc định: milimét (mm) cho kích thước cấu kiện, mét (m) cho cao độ và diện tích.
- Mọi phần tử do Claude tự thêm/giả định khi chưa đủ căn cứ phải được đánh dấu rõ (ví dụ ghi "CLAUDE-GIẢ ĐỊNH" vào Comments) để người dùng dễ nhận diện và duyệt lại.

## Bản đồ tài liệu - đọc file nào khi nào

| Tình huống | Đọc file |
|---|---|
| Bắt đầu dựng mô hình mới, cần biết thứ tự các bước (trục, cao độ, cột, dầm, tường, sàn, mái...) | `01_Modeling_Process.md` |
| Cần quy ước đặt tên, tổ chức Workset, phân chia file, LOD theo từng giai đoạn | `02_BIM_Standard.md` |
| Tạo hoặc chỉnh family (cửa, cột, thiết bị...), đặt tên family/type, cấu trúc tham số | `03_Family_Standard.md` |
| Cần biết vật liệu, cấu tạo lớp của tường/sàn/mái (loại, độ dày từng lớp) | `04_Material_Library.md` |
| Kiểm tra kích thước, khoảng lùi, cầu thang, lan can, chiếu sáng, thông gió theo kiến trúc | `05_TCVN_Architecture.md` |
| Kiểm tra kích thước, bố trí cột/dầm/sàn/móng, lớp bê tông bảo vệ theo kết cấu | `06_TCVN_Structure.md` |
| Kiểm tra hệ thống điện, nước, điều hòa, thông gió (MEP) | `07_TCVN_MEP.md` |
| Kiểm tra yêu cầu về PCCC (lối thoát hiểm, khoảng cách, vật liệu chống cháy) | `08_QCVN_Fire.md` |
| Gắn Shared Parameters vào family hoặc dự án | `SharedParameters.txt` |
| Cần file mẫu family hoặc mẫu vật liệu để không dựng lại từ đầu | `Family_Template/`, `Material_Template/` |

## Quy trình làm việc gợi ý

1. Xác định người dùng đang ở bước nào (dựng mới, kiểm tra, hay chỉnh sửa) và cấu kiện liên quan (kiến trúc, kết cấu, hay MEP).
2. Đọc `01_Modeling_Process.md` để xác định đúng thứ tự thao tác.
3. Đọc file cấu tạo/tiêu chuẩn tương ứng trong bảng trên trước khi đưa ra kích thước, lớp vật liệu, hoặc thông số kỹ thuật cụ thể.
4. Nếu thao tác trên Revit (qua công cụ MCP), đối chiếu loại tường/sàn/family đã tồn tại trong file trước khi tạo mới, và đặt tên type theo đúng `03_Family_Standard.md`.
5. Sau khi dựng xong, nêu rõ phần nào lấy đúng theo tài liệu, phần nào còn thiếu căn cứ và cần người dùng xác nhận thêm.
