# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| B2-dense · `adasind_062370.jpg` | 6 missing, 6 spurious và 1 wrong-class trong model/compare; tập trung center | Ưu tiên vì có đồng thời thiếu box, sai lớp Car/Truck và nhiều nhầm ThreeWheeler→Truck/rider→Pedestrian | Ảnh gốc, `r3_diag/model_compare.html`, `evidence_062370_model_reference.png`, box L/R/M và quyết định R7/R8 |
| B2-dense · `adasind_117120.jpg` | 2 missing, 7 spurious theo findings; có L1 sai lớp, L5 trùng và model phát nhiều box chồng | Kiểm tra lỗi một-vật-một-box, Car/Bus/Truck và ảnh hưởng của box nhỏ lồng ở center | Ảnh gốc, `r1_craft/compare.html`, `r3_diag/model_compare.html`, `evidence_117120_duplicates.png`, rule R02–R04 |

Giới hạn của kết luận từ ba frame ADASIND: đây là slice một camera và chỉ có ba frame, không đại diện cho toàn bộ ADASIND hay bốn camera SVM. Các bin center/mid/edge chỉ là bin chẩn đoán; teaching reference chưa phải gold set và các ca model cần thêm frame độc lập trước khi kết luận về miền dữ liệu.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: chia mẫu theo camera và normal/hard, rải frame theo thời gian và cảnh thay vì lấy các frame liên tiếp của một cảnh; giữ timestamp, camera_id, calibration, seam/occlusion và quyết định reviewer cho mỗi mẫu. Kế hoạch giúp ưu tiên ca khó và tìm lỗi có thể bị bỏ sót, nhưng không đo tỷ lệ lỗi vì chưa có mẫu ngẫu nhiên đại diện, chưa có gold đã xác nhận và 200 frame là ngân sách review chứ không phải ước lượng thống kê.
