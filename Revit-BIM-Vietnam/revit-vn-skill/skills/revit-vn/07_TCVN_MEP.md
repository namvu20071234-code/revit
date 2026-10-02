# 07. TCVN/QCVN Cơ điện lạnh (MEP)

Nguồn: TCVN 4513, TCVN 4474, TCVN 5687:2024, TCVN 7114, QCVN 12:2014/BXD, do người dùng cung cấp. Đây là nguồn tiêu chuẩn chính thức — khi dựng hoặc kiểm tra hệ thống MEP trong Revit, đối chiếu với bảng dưới trước khi xác nhận hợp lệ.

## 1. Hệ thống cấp thoát nước (TCVN 4513 & TCVN 4474)

**Tiêu chuẩn dùng nước sinh hoạt (TCVN 4513):**
| Loại công trình | Định mức |
|---|---|
| Nhà chung cư thương mại | 150–200 lít/người/ngày-đêm |
| Văn phòng, công sở | 15–25 lít/người/ca |

**Độ dốc đường ống thoát nước (TCVN 4474):**
| Đường kính ống | Độ dốc tối thiểu (i) |
|---|---|
| D ≤ 50 mm | 3% |
| D = 75–110 mm | 2% |
| D ≥ 150 mm | 1% |

**Vận tốc nước chảy tối đa:**
- Ống cấp nước sinh hoạt: Vmax ≤ 1,5–2,0 m/s.
- Ống thoát nước tự chảy: Vmax ≤ 1,0–2,5 m/s.

## 2. Thông gió và điều hòa không khí (TCVN 5687:2024)

**Lượng khí tươi cấp tối thiểu:**
| Loại không gian | Định mức |
|---|---|
| Văn phòng làm việc | 30 m³/giờ/người |
| Phòng họp, hội trường | 20–25 m³/giờ/người |
| Nhà hàng, trung tâm thương mại | 20 m³/giờ/người |

**Vận tốc gió trong đường ống:**
| Vị trí | Vận tốc |
|---|---|
| Ống gió chính — cấp gió | 6–8 m/s |
| Ống gió chính — hút gió | 4–6 m/s |
| Ống gió nhánh | 3–4,5 m/s |
| Cửa gió (Diffuser/Grille) | 1,5–2,5 m/s (tránh ồn) |

## 3. Cấp điện và chiếu sáng (QCVN 12:2014/BXD & TCVN 7114)

**Độ chiếu sáng tối thiểu (TCVN 7114):**
| Loại không gian | Độ rọi |
|---|---|
| Phòng ở, phòng ngủ | 150 Lux |
| Văn phòng làm việc, phòng học | 300–500 Lux |
| Hành lang, cầu thang, khu vệ sinh | 100–150 Lux |

**An toàn công suất điện (QCVN 12:2014):**
- Mật độ công suất chiếu sáng tối đa cho văn phòng: ≤ 11 W/m².
- Hệ số đồng thời cho căn hộ chung cư: Kđt = 0,6–0,8.
- Dây dẫn điện trong nhà bắt buộc dùng dây lõi đồng cách điện chống cháy/chậm cháy, đi ngầm trong ống Gen luồng bảo vệ.

## Áp dụng khi dựng qua MCP
- Khi dựng hệ ống nước, gán độ dốc đúng bảng mục 1 theo đường kính ống, không mặc định một độ dốc cố định cho mọi loại ống.
- Khi dựng hệ thống gió, chọn tiết diện ống sao cho vận tốc gió tính toán nằm trong khoảng ở mục 2; nếu vượt ngưỡng, báo lại cho người dùng thay vì tự nới tiết diện mà không hỏi.
- Khi bố trí đèn/tính công suất chiếu sáng, đối chiếu độ rọi yêu cầu theo loại phòng ở mục 3 trước khi xác nhận số lượng đèn là đủ.
- Family MEP (diffuser, van, đèn...) đặt tên theo đúng cú pháp `[Mã_Công_Ty]_MEP_[Tên]_[Biến_Thể]` ở `03_Family_Standard.md`.
