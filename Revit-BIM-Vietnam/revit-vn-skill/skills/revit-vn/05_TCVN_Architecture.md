# 05. TCVN/QCVN Kiến trúc (Kích thước thiết kế)

Nguồn: QCXDVN 01:2021/BXD và các tiêu chuẩn kích thước kiến trúc liên quan, do người dùng cung cấp. Đây là nguồn tiêu chuẩn chính thức — khi dựng hoặc kiểm tra kích thước kiến trúc trong Revit (cửa, cầu thang, lan can, chiều cao tầng), đối chiếu bảng dưới trước khi xác nhận hợp lệ. Nếu kích thước dự án khác bảng này, hỏi lại người dùng thay vì tự điều chỉnh.

## 1. Khoảng lùi & mật độ xây dựng (QCXDVN 01:2021/BXD)

### 1.1. Khoảng lùi công trình theo chiều cao
| Chiều cao công trình (H) | Khoảng lùi tối thiểu |
|---|---|
| H ≤ 19 m | 0 m (lộ giới < 19 m) hoặc 3 m (lộ giới ≥ 19 m) |
| H = 19–22 m | 3–4 m tùy lộ giới |
| H ≥ 28 m | 6 m so với ranh lộ giới |

### 1.2. Độ vươn tối đa ban công/ô văng theo lộ giới
| Lộ giới | Độ vươn tối đa ban công |
|---|---|
| < 7 m | Không được nhô ra khỏi ranh lộ giới |
| 7–12 m | 0,9 m |
| 12–20 m | 1,2 m |
| > 20 m | 1,4 m |

## 2. Kích thước chi tiết cấu kiện kiến trúc

### 2.1. Cầu thang bộ
- **Chiều rộng vế thang tối thiểu:** nhà ở gia đình ≥ 0,9 m; công trình công cộng/chung cư ≥ 1,2 m.
- **Kích thước bậc thang:**
  - Chiều cao bậc (h): 150–180 mm (nhà ở); 150–165 mm (công cộng).
  - Chiều rộng mặt bậc (b): 250–300 mm.
  - Công thức an toàn: `2h + b = 600–630 mm`.
- **Số bậc liên tiếp tối đa:** 18 bậc trước khi cần chiếu nghỉ. Chiều rộng chiếu nghỉ ≥ chiều rộng vế thang.

### 2.2. Lan can, tay vịn & tấm chắn
| Vị trí | Chiều cao tối thiểu |
|---|---|
| Lô gia/ban công từ tầng 9 trở lên (H ≥ 20 m) | 1,4 m |
| Ban công, mái có người lên từ tầng 8 trở xuống | 1,1 m |
| Cầu thang, vế thang (từ mặt bậc đến đỉnh tay vịn) | 0,9 m |

- **An toàn trẻ em:** khe hở giữa các thanh đứng lan can ≤ 100 mm (10 cm). Không dùng thanh ngang làm lan can (tránh trẻ trèo).

### 2.3. Cửa đi & cửa sổ
- **Chiều cao thông thủy cửa đi:** ≥ 2,1 m (2100 mm).
- **Chiều rộng thông thủy cửa đi:**
  | Loại cửa | Chiều rộng |
  |---|---|
  | Cửa chính nhà ở (1 hoặc 2 cánh) | 1,2–2,4 m |
  | Cửa phòng ngủ | 0,8–0,9 m |
  | Cửa nhà vệ sinh (WC) | 0,7–0,8 m |
- **Chiều cao bệ cửa sổ (Sill Height):** thường 0,8–0,9 m so với mặt sàn hoàn thiện.

## 3. Chiều cao tầng & không gian thông thủy

### 3.1. Chiều cao tầng (Floor-to-Floor)
| Vị trí | Chiều cao |
|---|---|
| Tầng trệt (nhà ở liên kế/biệt thự) | 3,6–4,2 m |
| Các tầng lầu trên | 3,2–3,6 m |
| Tầng hầm/bán hầm | 2,2–3,0 m |

### 3.2. Chiều cao thông thủy không gian (Clear Height)
| Loại không gian | Thông thủy tối thiểu |
|---|---|
| Phòng ở, phòng làm việc | 2,7 m |
| Hành lang, nhà vệ sinh, kho | 2,2 m |

## Áp dụng khi dựng qua MCP
- Khi đặt cửa (Door/Window family) lên tường, kiểm tra chiều rộng/cao đã chọn có khớp loại cửa (chính/phòng ngủ/WC) theo mục 2.3 không.
- Khi dựng Stair, kiểm tra `2h + b` có nằm trong khoảng 600–630mm không trước khi xác nhận; nếu số bậc liên tiếp > 18, phải có chiếu nghỉ.
- Khi dựng Railing, đặt chiều cao theo đúng vị trí sử dụng ở mục 2.2, không dùng một chiều cao mặc định cho mọi loại lan can.
- Khi đặt Level, đối chiếu khoảng cách giữa các cao độ với bảng chiều cao tầng mục 3.1; nếu hồ sơ thiết kế yêu cầu khác, dùng số liệu hồ sơ và hỏi lại người dùng.
- Khi dựng khối nhà theo ranh đất, kiểm tra khoảng lùi và độ vươn ban công theo mục 1 dựa trên chiều cao công trình và lộ giới thực tế — hỏi người dùng thông tin lộ giới nếu chưa có.
