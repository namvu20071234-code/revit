# 03. Chuẩn Family và tham số nội bộ (Shared Parameters)

Nguồn: quy chuẩn nội bộ do người dùng cung cấp. Thay `[Mã_Công_Ty]` bằng mã thật của công ty bạn trước khi áp dụng (ví dụ dùng "ABC" dưới đây chỉ là mẫu minh họa).

## 1. Quy tắc đặt tên Family
Cú pháp bắt buộc:
```
[Mã_Công_Ty]_[Bộ_Môn]_[Tên_Cấu_Kiện]_[Biến_Thể]
```
Ví dụ:
- Cột bê tông: `ABC_STR_Column_Rectangular`
- Cửa đi 2 cánh: `ABC_ARC_Door_Double_Flush`
- Miệng gió âm trần: `ABC_MEP_Diffuser_Square`

(Bộ môn dùng đúng mã đã định nghĩa ở `02_BIM_Standard.md`: ARC/STR/MEP/SIT.)

## 2. Shared Parameters chuẩn công ty
Dùng chung một file Shared Parameters để mọi Family xuất Schedule đồng bộ.

### 2.1. Nhóm tham số quản lý (Identity Data)
| Tên tham số | Kiểu | Instance/Type | Ý nghĩa |
|---|---|---|---|
| `SEN_Code` | Text | Instance | Mã quản lý cấu kiện nội bộ |
| `SEN_Manufacturer` | Text | Type | Tên nhà sản xuất/thương hiệu |
| `SEN_Model` | Text | Type | Mã hiệu sản phẩm |

### 2.2. Nhóm tham số kích thước (Dimensions)
| Tên tham số | Kiểu | Instance/Type | Ý nghĩa |
|---|---|---|---|
| `SEN_Width` | Length | Type/Instance | Chiều rộng thông thủy/bao phủ |
| `SEN_Height` | Length | Type/Instance | Chiều cao cấu kiện |
| `SEN_Thickness` | Length | Type | Độ dày cấu kiện (tấm/vách/sàn) |

## 3. Nguyên tắc dựng Family chuẩn BIM
- **Reference Planes:** mọi kích thước hình học phải khóa (Dimension Lock) vào Reference Plane, tuyệt đối không khóa trực tiếp vào đường nét hình học (Geometry) — nếu không, family sẽ vỡ hình khi đổi tham số.
- **Điểm đặt Family (Origin Point):** điểm giao giữa 2 mặt phẳng Center (Front/Back) và Center (Left/Right) phải nằm ở tâm hoặc góc chân gốc của cấu kiện, để tránh lệch tọa độ khi chèn vào dự án.
- **Mức độ chi tiết (LOD hiển thị):**
  | Mức | Hiển thị | Dùng cho |
  |---|---|---|
  | Coarse (Thô) | Khối đơn giản | Quy hoạch/mặt bằng tỷ lệ nhỏ |
  | Medium (Trung bình) | Hình dáng thực tế | Bản vẽ 1:100, 1:50 |
  | Fine (Mịn) | Đầy đủ vát góc, phụ kiện, chi tiết lắp ráp | Bản vẽ chi tiết 1:20, 1:10 |

  (Không nhầm với LOD 200/300/350/400 ở `02_BIM_Standard.md` — đó là mức phát triển mô hình theo giai đoạn dự án, còn đây là mức chi tiết hiển thị của riêng family.)

## Áp dụng khi dựng/tạo Family qua MCP
- Trước khi tạo Family mới, kiểm tra tên dự định đặt có đúng cú pháp mục 1 không; nếu người dùng chưa cho biết Mã_Công_Ty, hỏi lại thay vì tự bịa mã.
- Khi Family cần xuất hiện trong Schedule, gắn đủ các Shared Parameter ở mục 2 tương ứng với loại cấu kiện.
- Khi dựng hình trong Family Editor, luôn tạo Reference Plane trước, khóa Dimension vào đó rồi mới vẽ Extrusion/Sweep/Revolve — không vẽ hình trước rồi khóa sau.
