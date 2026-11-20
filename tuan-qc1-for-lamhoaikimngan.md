# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): lamhoaikimngan        Người kiểm (học viên): tuan (Đặng Gia Tuấn - 2A202603067)  
Ngày: 20/11/2026                               Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `lamhoaikimngan-front.zip` & `lamhoaikimngan-fisheye.zip` (revision 1)  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)       Số nhãn đã kiểm (shape + tag): 58  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 17 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 17 | 4 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 17 | 1 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 17 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 12 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 4 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 6 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 2 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 15 | 3 | chính |
| QC1-12 file | lỗi file | 58 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-02 | A03 | lane | nặng | Thiếu vạch L1 bên trái làn đang đi (chỉ có R1 và R2, làn xe nhìn thấy rõ) |
| 2 | QC1-04 | A02 | lane#1@(563,397) | chính | Điểm đầu cao hơn điểm cuối (y=397.09 -> y=718.69): vẽ ngược chiều từ xa về gần |
| 3 | QC1-04 | A02 | lane#2@(548,397) | chính | Điểm đầu cao hơn điểm cuối (y=397.22 -> y=588.40): vẽ ngược chiều từ xa về gần |
| 4 | QC1-04 | A03 | lane#0@(647,386) | chính | Điểm đầu cao hơn điểm cuối (y=385.90 -> y=574.90): vẽ ngược chiều từ xa về gần |
| 5 | QC1-04 | A03 | lane#3@(586,376) | chính | Điểm đầu cao hơn điểm cuối (y=376.21 -> y=672.70): vẽ ngược chiều từ xa về gần |
| 6 | QC1-05 | A01 | lane#6, lane#8 | chính | 2 polyline cùng mang thuộc tính position=L2: vạch đứt bị tách hoặc vẽ đè lặp lại |
| 7 | QC1-11 | B02 | traffic_light#0@(104,104) | chính | Box cụm đèn có tâm cách tâm ảnh 594 px (> 80% bán kính 512 px) nhưng edge_zone=false (quên bật) |
| 8 | QC1-11 | B02 | traffic_light#1@(1073,74) | chính | Box cụm đèn có tâm cách tâm ảnh 592 px (> 80% bán kính 512 px) nhưng edge_zone=false (quên bật) |
| 9 | QC1-11 | B04 | traffic_sign#2@(1061,171) | chính | Box biển báo có tâm cách tâm ảnh 526 px (> 80% bán kính 512 px) nhưng edge_zone=false (quên bật) |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A03 | Vạch L1 ở A03 bị xe phía trước che một phần lớn, có được miễn lỗi QC1-02 nếu học viên nối qua chỗ che không? | Theo Guideline 3: Đoạn bị che ngắn nối qua và bật occluded. Trường hợp này học viên bỏ không vẽ là phạm QC1-02. |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 8 / 58 nhãn = 13.79 %   Lỗi nhẹ: 6 (tag source=simulated)   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): Rework  
Lý do (theo luật của phiếu):  
1. Lô tồn tại 1 lỗi nặng (Mã QC1-02: thiếu vạch L1 trên ảnh A03).  
2. Tỉ lệ lỗi chính là 13.79% (8/58 nhãn), vượt quá ngưỡng cho phép 5% theo luật của phiếu QC 1 (các lỗi chính gồm: 4 vạch vẽ ngược chiều từ xa về gần ở A02, A03; 1 lỗi tách vạch đứt ở A01; 3 lỗi quên bật checkbox edge_zone trên ảnh fisheye B02, B04).  

---
Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
