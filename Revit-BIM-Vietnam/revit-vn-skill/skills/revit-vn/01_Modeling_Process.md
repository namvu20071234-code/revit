# 01. Quy trình dựng mô hình Revit (Modeling Process)

Nguồn: tổng hợp từ "Tài liệu thực hành Revit 2024" (ThS. Mai Bá Nhẫn), "Hướng dẫn Revit Structure" (Lê Tiến Quang), và các tài liệu quy trình Revit Structure/Architecture đã cung cấp. Đây là thứ tự **bắt buộc tuân theo**, không đảo bước, trừ khi người dùng yêu cầu khác và nói rõ lý do.

## Nguyên tắc chung
- Luôn thiết lập đơn vị dự án trước khi vẽ bất kỳ hình nào.
- Phần kết cấu dựng trước, kiến trúc dựng sau, cốt thép dựng sau cùng khi hình dạng bê tông đã chốt.
- Khi dựng hình phần kết cấu, hạ cao độ xuống 50mm so với cao độ hoàn thiện kiến trúc (quy ước từ tài liệu Mai Bá Nhẫn) — trừ khi quy ước công ty người dùng khác đi.
- Mỗi bước phải kiểm tra bước trước đã đúng (lưới trục, cao độ) trước khi dựng cấu kiện, vì mọi cấu kiện đều neo theo Grid/Level.

## BƯỚC 1 — Lập khung định vị dự án
1. **Project Units (UN):** đặt đơn vị chiều dài (mm hoặc m), diện tích (m²), thể tích (m³), góc (độ). Kiểm tra riêng đơn vị Rebar Diameter về mm.
2. **Level (LL):** mở mặt đứng (East/South) → tạo cao độ từ dưới lên: ví dụ MÓNG → TRỆT (0.000) → LẦU 1 (+3.600) → LẦU 2 (+7.200) → MÁI. Đổi tên theo đúng tên tầng dự án, không để mặc định "Level 1/2".
3. **Grid (GR):** mở mặt bằng, vẽ trục ngang (chữ A, B, C...) và trục dọc (số 1, 2, 3...). Dùng Add Elbow để bẻ đầu trục khi số/chữ bị đè nhau. Thể hiện lưới trục và Level theo đúng family ký hiệu chuẩn TCVN của công ty (xem `03_Family_Standard.md`), không dùng family mặc định của Revit nếu công ty đã có family riêng.

## BƯỚC 2 — Mô hình kết cấu chịu lực (Structure Model)
Thứ tự bắt buộc:
1. **Móng** (Isolated/Wall/Slab Foundation) — đặt tại mặt bằng cao độ móng, dùng At Columns để đặt hàng loạt vào chân cột.
2. **Cột (CL)** — chuyển Options Bar sang Height, nối từ tầng dưới lên tầng trên; dùng At Grids để đặt hàng loạt theo giao lưới trục.
3. **Dầm (BM)** — dùng On Grids để dầm tự chạy theo lưới trục nối các đầu cột.
4. **Sàn kết cấu (SB)** — vẽ biên khép kín bằng Pick Lines (bắt mép dầm/tường) hoặc Rectangle; dùng Shaft Opening để đục lỗ thang máy/hộp kỹ thuật xuyên tầng.
5. **Vách/tường bê tông chịu lực (WA)** — dựng vách thang máy, tường chắn; khai báo Base/Top Constraint.
6. **Dầm móng, bê tông lót, cọc** (nếu có) — dựng sau móng chính, trước khi copy sang các trục tương tự.
7. **Copy/dựng tương tự** cho toàn hệ kết cấu công trình theo hồ sơ thiết kế đính kèm.
8. **Cầu thang BTCT** — Cast-in-Place Stair (Monolithic), khai báo Base/Top Level để Revit tự tính số bậc; dựng xong mới gán lớp hoàn thiện cầu thang.
9. **Ram dốc, lan can.**

## BƯỚC 3 — Dựng kiến trúc (Architecture Model)
1. **Tường kiến trúc (WA)** — tường bao, tường ngăn; khai báo Base/Top Constraint theo Level kiến trúc (không phải Level kết cấu đã hạ 50mm).
2. **Cửa đi (DR), cửa sổ (WN)** — đặt lên tường có sẵn, Spacebar đổi chiều mở.
3. **Đặt tên phòng, chia/gộp phòng, đổi màu phòng** — dùng công cụ Room, Revit tự tính diện tích.
4. **Vách kính (Curtain Wall)** — chia Curtain Grid, gán Mullion.
5. **Lam (Louver)** — vẽ lam, chỉnh tiết diện khung đố.
6. **Mái** — mái đơn giản (Roof by Footprint, khai báo Slope Angle từng cạnh), mái cong/phức tạp (Roof by Extrusion), mái kính, lam che.
7. **Trần** — trần khung nổi, trần giật cấp, Automatic Ceiling để phủ kín phòng (Height Offset theo thiết kế, ví dụ 2700mm).
8. **Hoàn thiện:** len chân tường, cắt ron tường, sơn tường, tạo hốc tường, lát sàn, ốp/trát tường, đóng trần thạch cao.
9. **Nội thất** — load family Furniture/Plumbing/Lighting và bố trí.
10. **Visibility/Graphics (VV)** — tùy chỉnh hiển thị đối tượng trong từng mặt bằng.

## BƯỚC 4 — Bố trí cốt thép chi tiết (Rebar Modeling)
Chỉ thực hiện sau khi hình dạng bê tông (Bước 2) đã chốt, không đổi nữa.
1. **Thiết lập lớp bảo vệ (Cover)** theo cấu kiện — xem bảng giá trị quy ước trong `06_TCVN_Structure.md`.
2. **Thép cột:** cắt Section ngang cột → đặt thép đai (Shape 51/M_01, Placement Plane = Parallel to Work Plane, Maximum Spacing) → đặt thép dọc (Placement Orientation = Perpendicular to Cover, chọn đường kính, Rebar Set = Fixed Number).
3. **Thép dầm:** Section dọc + Section ngang dầm → thép đai (spacing khác nhau ở đầu dầm gần gối và giữa nhịp) → thép dọc lớp trên/dưới, Hook at Start/End = Standard 90 độ để neo vào cột.
4. **Thép sàn:** Area Reinforcement (rải nhanh lưới 2 phương, khai báo Major/Minor Layer, Top Major/Minor nếu cần lớp trên) và Path Reinforcement (thép gia cường/thép mũ gối).
5. **Thép cầu thang:** Section dọc vế thang, Cover riêng cho bản thang, thép dọc bẻ móc neo vào dầm chiếu nghỉ/sàn, thép phân bố ngang.

## BƯỚC 4B — Dựng hệ thống Cơ điện (MEP, nếu dự án có yêu cầu)
Thực hiện sau khi kiến trúc và kết cấu đã dựng xong, vì ống/máng cáp cần biết vị trí dầm/sàn/tường để đi tránh.
1. **Ống cấp thoát nước (Pipe):** đi ống cấp nước sạch và thoát nước thải; đặt độ dốc và vận tốc theo đúng bảng ở `07_TCVN_MEP.md` mục 1 (không dùng độ dốc mặc định cố định cho mọi đường kính ống).
2. **Ống gió điều hòa (Duct):** đi đường ống gió lạnh, đặt miệng gió (Diffuser/Grille); chọn tiết diện ống sao cho vận tốc gió nằm trong khoảng ở `07_TCVN_MEP.md` mục 2.
3. **Máng cáp & dây điện (Conduit/Cable Tray):** đi hệ thống dây điện chiếu sáng; đối chiếu độ rọi yêu cầu và mật độ công suất ở `07_TCVN_MEP.md` mục 3 khi bố trí đèn.
4. Family MEP đặt tên theo đúng cú pháp ở `03_Family_Standard.md` (ví dụ `[Mã_Công_Ty]_MEP_Diffuser_Square`).
5. Sau khi đi xong hệ MEP, chạy lại Interference Check (`02_BIM_Standard.md` mục 5.1) giữa MEP và Kết cấu để phát hiện xung đột trước khi giao hồ sơ.

## BƯỚC 5 — Thống kê khối lượng (Schedules / Material Takeoff)
1. Áp dụng đúng quy tắc khấu trừ bê tông cột/vách/dầm/sàn theo tương quan mác bê tông (xem tài liệu gốc Bài 1, Phần 3) trước khi xuất khối lượng.
2. Áp dụng quy tắc Join đúng thứ tự ưu tiên (cọc ưu tiên so với móng và bê tông lót); dùng công cụ Join thủ công hoặc add-in tự động nếu công ty đã trang bị.
3. Tạo Schedule/Quantities cho thép (Type, Bar Diameter, Total Bar Length, Quantity, Reinforcement Volume + Calculated Parameter khối lượng kg) và Material Takeoff cho bê tông (Material: Name, Material: Volume), tường, cửa, cửa sổ.
4. Shared Parameter dùng cho nhiều dự án: tạo ở `Manage → Shared Parameters`, lưu file text riêng, load vào từng dự án để đồng bộ.

## BƯỚC 6 — Lập hồ sơ & xuất bản vẽ (Documentation & Sheet)
1. Thiết lập nét in (Line Weight, Line Patterns, Line Styles) trước khi tạo Sheet.
2. Tạo Sheet theo đúng khổ giấy và mã số theo `02_BIM_Standard.md`.
3. Kéo View (mặt bằng, mặt đứng, mặt cắt, 3D, bảng khối lượng) vào Sheet.
4. Ghi kích thước (Aligned Dimension) và dán nhãn tự động (Tag by Category / Tag All Not Tagged) cho cột, dầm, thép.
5. Xuất file: CAD (DWG), PDF, Schedule ra Excel, hoặc IFC khi cần trao đổi với bên tính toán kết cấu/thẩm tra.

## BƯỚC 7 — Diễn họa (tùy chọn, làm sau cùng)
Gán Material Appearance, đặt Camera, bật Sun Path/Shadows nếu cần nghiên cứu hướng nắng, Render xuất ảnh phối cảnh.

## BƯỚC 2C — Kỹ thuật nâng cao khi dựng kiến trúc (bổ sung từ Revit 2026)
- **Location Line khi dựng tường:** chọn `Core Centerline` (theo tim) khi dựng kết cấu, hoặc `Finish Face: Exterior` khi dựng tường kiến trúc cần khớp mặt ngoài hoàn thiện — xác nhận với người dùng loại nào áp dụng cho dự án trước khi dựng hàng loạt.
- **Tạo Grid nhanh:** vẽ 1 trục trước, dùng lệnh `CO` (Copy) để nhân bản song song theo đúng khoảng cách nhịp (ví dụ 7200mm); Revit tự tăng số/chữ cho trục tiếp theo.
- **Roof by Footprint:** nhập `Overhang` (độ vươn mái, ví dụ 600mm) khi Pick các cạnh tường bao; tích `Defines Slope` cho cạnh cần tạo độ dốc, bỏ tích cho mái bằng. Sau khi Finish, chọn các tường bên dưới → `Attach Top/Base` → click mái để tường tự ăn khớp vào đáy mái, tránh hở khe hoặc tường xuyên qua mái.
- **Gán vật liệu:** `Edit Type → Structure → Edit`, bấm ô `...` ở cột Material để mở Material Browser; tùy chỉnh màu ở tab Graphics, ảnh bề mặt ở tab Appearance.

## BƯỚC 2D — Kỹ thuật nâng cao khi dựng kết cấu (Analytical Model & chi tiết hóa)
Dùng khi dự án cần xuất dữ liệu tính toán sang phần mềm kết cấu chuyên dụng (Robot, ETABS, SAP2000), không bắt buộc cho mô hình kiến trúc thuần túy.
1. **Thiết lập mô hình phân tích:** `VV → Analytical Model Categories` để bật hiển thị; `Analyze → Analytical Adjust` để kéo các nút giao của Dầm/Cột/Vách về đúng tim kết cấu — bắt buộc làm trước khi xuất dữ liệu, nếu không mô hình phân tích sẽ gãy nút và tính toán sai.
2. **Điều kiện biên:** `Analyze → Boundary Conditions`, chọn loại gối (`Fixed`/`Pinned`/`Roller`), gán vào chân cột hoặc đáy móng.
3. **Gán tải trọng:** `Analyze → Loads`, chọn loại tải (`Point`/`Line`/`Area` Load) và Load Case (Tĩnh tải/Hoạt tải/Tải gió), nhập giá trị theo trục X, Y, Z. Giá trị tải cụ thể phải lấy từ hồ sơ thiết kế thật, không tự đặt.
4. **Hệ dầm phụ tự động (Beam System):** `Structure → Beam System`, chọn `Beam Type` và `Rule` (`Fixed Distance` hoặc `Fixed Number`), rê chuột vào ô sàn giữa các dầm chính để Revit tự rải dầm phụ.
5. **Dàn thép & giằng:** `Structure → Truss` (chọn mẫu Howe/Pratt/Warren, gán tiết diện cánh trên/dưới/thanh bụng ở Edit Type); `Structure → Brace` để tạo hệ giằng X/K/V giữa các nút giao dầm-cột.
6. **Thép tự do (Free Form Rebar):** dùng cho cấu kiện cong/nghiêng — `Structure → Rebar → Free Form`, chọn mặt đỉnh/đáy/các mặt bên để Revit tự uốn thép bám theo hình dạng 3D.
7. **Nối thép bằng Coupler:** `Structure → Rebar Coupler`, click 2 đầu thanh thép dọc cần nối để chèn ống ren chịu lực thay vì nối chồng thủ công.
8. **Bảng thống kê thép (BBS) nâng cao:** thêm trường `Bar Mark`, `A/B/C` (kích thước đoạn uốn móc), `Total Weight`; gom nhóm theo Tầng (`Partition`) hoặc theo cấu kiện (`Host Mark`) tại tab Sorting/Grouping.
9. **Tag All:** `Annotate → Tag All`, tích `Structural Framing Tags`, `Structural Column Tags`, `Structural Rebar Tags` để dán nhãn toàn bộ bản vẽ trong 1 lần.
10. **Xuất IFC:** `File → Export → IFC`, chọn `IFC2x3 Structural Model` hoặc `IFC4 Design Transfer View` khi cần gửi file cho đơn vị thẩm tra/tính toán kết cấu.

## Bảng lệnh tắt nhanh Revit (tham khảo khi thao tác giao diện/ghi chú trong model)
| Lệnh | Chức năng |
|---|---|
| `UN` | Project Units |
| `LL` | Level |
| `GR` | Grid |
| `CL` | Column |
| `BM` | Beam / đà kiềng |
| `SB` | Floor (Slab) |
| `WA` | Wall |
| `DR` | Door |
| `WN` | Window |
| `ST` | Stair |
| `RA` | Railing |
| `RM` | Room |
| `CM` | Component (nội thất, thiết bị) |
| `PI` | Pipe |
| `DT` | Duct |
| `ME` | Mechanical Equipment / miệng gió |
| `CN` | Conduit / Cable Tray |
| `SEC` | Section |
| `DI` | Dimension |
| `TG` | Tag by Category |

Lưu ý: đây là phím tắt mặc định phổ biến, một số công ty tùy biến lại phím tắt riêng trong `KeyboardShortcuts.xml` — nếu người dùng nói phím tắt khác, dùng theo người dùng.

## Việc cần làm khi thực thi qua Revit API / MCP
Khi Claude dựng các bước trên bằng `execute_revit_code`, với mỗi bước phải:
- Kiểm tra Level/Grid cần thiết đã tồn tại chưa trước khi tạo cấu kiện neo vào đó.
- Tìm loại tường/sàn/family đã có trong dự án (đúng tên theo `02_BIM_Standard.md`) trước khi tạo loại mới.
- Nếu thiếu thông tin kích thước/cao độ cụ thể cho dự án đang làm, dừng lại và hỏi người dùng, không tự suy đoán.
