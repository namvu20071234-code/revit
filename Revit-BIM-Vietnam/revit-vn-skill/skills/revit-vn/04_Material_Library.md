# 04. Thư viện vật liệu & bảng cấu tạo lớp (Material Library)

Nguồn: do người dùng cung cấp trực tiếp (bảng cấu tạo nội bộ). Đây là số liệu **thực hành/thiết kế mẫu**, không phải trích dẫn nguyên văn từ TCVN — khi có hồ sơ thiết kế thật của dự án, số liệu trong hồ sơ đó luôn được ưu tiên hơn bảng này.

## 1. Cấu kiện kết cấu bê tông cốt thép

### 1.1. Cột BTCT (300x300 mm)
| Lớp (trong → ngoài) | Vật liệu | Mã | Dày |
|---|---|---|---|
| Lõi chịu lực | Bê tông C25/30 | `STR_Concrete_C25` | 240 mm |
| Bảo vệ cốt thép (mỗi bên) | Bê tông đá 1x2 | `STR_Concrete_Cover` | 30 mm |
| Vữa hoàn thiện (mỗi mặt) | Vữa xi măng M75 | `ARC_Plaster_Interior` | 15 mm |

### 1.2. Dầm BTCT (200x400 mm)
| Lớp (theo bề rộng) | Vật liệu | Mã | Dày |
|---|---|---|---|
| Bảo vệ ngoài | Bê tông đá 1x2 | `STR_Concrete_Cover` | 25 mm |
| Lõi chịu lực | Bê tông C25/30 | `STR_Concrete_C25` | 150 mm |
| Bảo vệ còn lại | Bê tông đá 1x2 | `STR_Concrete_Cover` | 25 mm |

### 1.3. Đà kiềng / Dầm móng (200x300 mm)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Bê tông lót đáy móng | Đá 4x6 M100 | `STR_Concrete_Lean` | 100 mm |
| Bảo vệ cốt thép móng | Bê tông đá 1x2 | `STR_Concrete_Cover` | 35 mm |
| Lõi chịu lực đà kiềng | Bê tông C25/30 | `STR_Concrete_C25` | 130 mm |
| Bảo vệ mặt còn lại | Bê tông đá 1x2 | `STR_Concrete_Cover` | 35 mm |

### 1.4. Vách BTCT / Vách thang máy (200 mm)
| Lớp (ngoài → trong) | Vật liệu | Mã | Dày |
|---|---|---|---|
| Vữa/sơn hoàn thiện ngoài | Vữa M75 | `ARC_Plaster_Exterior` | 15 mm |
| Bảo vệ mặt ngoài | Bê tông đá 1x2 | `STR_Concrete_Cover` | 25 mm |
| Lõi chịu lực | Bê tông C30 | `STR_Concrete_C30` | 120 mm |
| Bảo vệ mặt trong | Bê tông đá 1x2 | `STR_Concrete_Cover` | 25 mm |
| Vữa/sơn hoàn thiện trong | Vữa M75 | `ARC_Plaster_Interior` | 15 mm |

## 2. Sàn, mái, cầu thang

### 2.1. Sàn nội thất chuẩn (150 mm, trên → dưới)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Hoàn thiện | Gạch Ceramic 600x600 / gỗ công nghiệp | `ARC_Finish_Tile` | 10 mm |
| Vữa đệm tạo phẳng | Vữa M75 | `ARC_Mortar_Bed` | 20 mm |
| Kết cấu chịu lực | Bê tông C20/25 | `STR_Concrete_C20` | 110 mm |
| Hoàn thiện đáy sàn | Vữa trát trần M75 + sơn nước | `ARC_Plaster_Ceiling` | 10 mm |

### 2.2. Sàn mái / ban công chống thấm (200 mm, trên → dưới)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Gạch bảo vệ/chống nóng | Gạch lá nem 300x300 | `ARC_Tile_Roof` | 20 mm |
| Vữa lót gạch | Vữa M75 | `ARC_Mortar_Bed` | 15 mm |
| Vữa tạo dốc (i = 1,5–2%) | Vữa M75 | `ARC_Mortar_Slope` | 35 mm |
| Chống thấm | Màng Polymer / Sika Topseal 107 | `ARC_Waterproofing` | 5 mm |
| Kết cấu chịu lực | Bê tông C25 | `STR_Concrete_C25` | 115 mm |
| Trát đáy mái | Vữa M75 chống ẩm | `ARC_Plaster_Ceiling` | 10 mm |

### 2.3. Cầu thang BTCT (bản xiên 120 mm)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Mặt bậc | Đá Granite/Marble | `ARC_Stair_Stone` | 20 mm |
| Vữa lót gắn đá | Vữa M75 | `ARC_Mortar_Bed` | 20 mm |
| Xây cổ bậc (chiều cao bậc) | Gạch thẻ/gạch đệm | `ARC_Brick_Stair` | 150 mm |
| Kết cấu bản đáy | Bê tông C20/25 | `STR_Concrete_C20` | 120 mm |
| Trát đáy bản thang | Vữa M75 + sơn nước | `ARC_Plaster_Ceiling` | 15 mm |

## 3. Tường bao & tường ngăn

### 3.1. Tường ngoài chịu lực (220 mm, ngoài → trong)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Sơn ngoại thất chống thấm | 2 lớp | `ARC_Paint_Exterior` | 2 mm |
| Vữa trát ngoài chống nứt | Vữa M75 | `ARC_Plaster_Exterior` | 18 mm |
| Gạch xây chính (xây đôi) | Gạch tuynel 80x80x180 | `ARC_Brick_Common` | 180 mm |
| Vữa trát trong | Vữa M75 | `ARC_Plaster_Interior` | 18 mm |
| Sơn nội thất | 2 lớp | `ARC_Paint_Interior` | 2 mm |

### 3.2. Tường ngăn phòng (110 mm, mặt A → mặt B)
| Lớp | Vật liệu | Mã | Dày |
|---|---|---|---|
| Sơn nội thất mặt A | 2 lớp | `ARC_Paint_Interior` | 2 mm |
| Vữa trát mặt A | Vữa M75 | `ARC_Plaster_Interior` | 13 mm |
| Gạch xây chính (xây đơn) | Gạch tuynel 4 lỗ 80x80x180 | `ARC_Brick_Hollow` | 80 mm |
| Vữa trát mặt B | Vữa M75 | `ARC_Plaster_Interior` | 13 mm |
| Sơn nội thất mặt B | 2 lớp | `ARC_Paint_Interior` | 2 mm |

## Áp dụng khi dựng qua MCP
- Khi tạo Wall/Floor Type mới trong Revit, đặt layer đúng thứ tự và độ dày ở bảng trên, đặt tên Type theo mã (`STR_...`/`ARC_...`) để khớp `02_BIM_Standard.md`.
- Nếu dự án có hồ sơ thiết kế riêng với số liệu khác bảng này, dùng số liệu hồ sơ và hỏi người dùng có muốn cập nhật bảng mẫu này không.
