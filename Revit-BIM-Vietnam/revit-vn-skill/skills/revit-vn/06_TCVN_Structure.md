# 06. TCVN Kết cấu (Tải trọng & Bê tông cốt thép)

Nguồn: TCVN 2737:2023 (Tải trọng và tác động) và TCVN 5574:2018 (Kết cấu bê tông và bê tông cốt thép), do người dùng cung cấp. Đây là **nguồn tiêu chuẩn chính thức** — ưu tiên số liệu ở file này hơn các số liệu "quy ước thực hành" xuất hiện trong `01_Modeling_Process.md` (phần lớp bảo vệ cột/dầm/sàn/móng lấy từ tài liệu hướng dẫn phần mềm, chỉ mang tính tham khảo thực hành phổ biến). Khi hai nguồn lệch nhau, dùng số liệu ở file này và báo cho người dùng biết có sự khác biệt.

## 1. TCVN 2737:2023 — Tải trọng và tác động

### Hoạt tải tiêu chuẩn theo loại không gian (qk)
| Loại không gian | qk (kN/m²) | Hệ số tin cậy γf |
|---|---|---|
| Phòng ở, phòng ngủ, phòng khách | 1,5 | 1,3 |
| Văn phòng làm việc, phòng học | 2,0 | 1,3 |
| Sảnh chờ, hành lang, cầu thang nhà ở | 3,0 | 1,2 |
| Sảnh công cộng, tập trung đông người | 4,0 | 1,2 |
| Ban công, logia | 2,0 | 1,3 |
| Mái không sử dụng | 0,75 | 1,3 |

### Tải trọng gió tính toán
Công thức: `Wk = W0 · k(z) · c`
- **W0** (áp lực gió cơ bản theo vùng): Vùng I = 0,65 kPa; Vùng II = 0,95 kPa; Vùng III = 1,25 kPa.
- **k(z)**: hệ số theo chiều cao z và dạng địa hình (A, B, C).
- **c**: hệ số khí động theo hình dạng kiến trúc công trình.
- Hệ số tin cậy tải trọng gió γf = 1,21.

> Khi gán Load trong Revit (Analyze → Loads), dùng đúng bảng này làm Load Case mặc định; nếu hồ sơ thiết kế có giá trị khác (ví dụ công trình ở vùng gió đặc biệt), dùng giá trị hồ sơ và hỏi lại người dùng.

## 2. TCVN 5574:2018 — Kết cấu bê tông và bê tông cốt thép

### Cường độ bê tông
| Cấp độ bền | Rb (nén, MPa) | Rbt (kéo, MPa) |
|---|---|---|
| B15 (C12/15) | 8,5 | 0,75 |
| B20 (C16/20) | 11,5 | 0,90 |
| B25 (C20/25) | 14,5 | 1,05 |
| B30 (C25/30) | 17,0 | 1,20 |

### Cường độ cốt thép tính toán (Rs)
| Loại thép | Rs (MPa) | Ghi chú |
|---|---|---|
| CB240-T | 210 | Thép tròn trơn — dầm/sàn/đai |
| CB300-V | 260 | |
| CB400-V | 350 | Thép gân dọc chịu lực |
| CB500-V | 435 | |

### Lớp bảo vệ cốt thép (acbl) — SỐ LIỆU CHÍNH THỨC
| Vị trí cấu kiện | acbl tối thiểu |
|---|---|
| Sàn, vách trong nhà (khô ráo) | ≥ 15 mm (và ≥ đường kính thép) |
| Dầm, cột (khô ráo) | ≥ 20 mm |
| Cấu kiện ngoài trời, tiếp xúc đất | ≥ 25 mm |
| Móng có bê tông lót | ≥ 35 mm |
| Móng không có bê tông lót | ≥ 70 mm |

### Chiều dài neo & nối chồng cốt thép
- Chiều dài neo cốt thép chịu kéo: `Lan = α · L0,an ≥ 20d` (thông thường Lan ≥ 30d–40d).
- Chiều dài nối chồng: `Lo = α · Lan`, không nhỏ hơn 250 mm; tại một mặt cắt không nối quá 50% tổng diện tích cốt thép chịu lực.

## Áp dụng khi dựng qua MCP
- Khi đặt `Cover` cho cột/dầm/sàn/móng trong Revit (Structure → Cover), dùng bảng lớp bảo vệ ở trên làm mặc định, không dùng số liệu "quy ước thực hành" trong `01_Modeling_Process.md` trừ khi người dùng xác nhận công ty áp dụng quy ước đó.
- Khi gán Load (Analyze → Loads) phục vụ xuất phân tích kết cấu, dùng bảng hoạt tải và tải gió ở trên làm giá trị mặc định, nhưng luôn hỏi lại giá trị thật từ hồ sơ thiết kế khi có.
- Khi chọn Concrete Type cho cột/dầm/sàn, đối chiếu mác bê tông yêu cầu với bảng cường độ ở trên trước khi dựng.
