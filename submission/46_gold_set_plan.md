# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Seam góc trước, xe/người chồng lấn, vật cắt mép, glare | Méo fisheye và vùng giao nhau dễ gây box lỏng, trùng hoặc sai class | Giữ camera_id, timestamp, calibration/extrinsic, ảnh gốc và mapping sang BEV; review trên ảnh gốc trước BEV | Hai reviewer độc lập gán box/attribute/Outside; adjudicator xem ảnh gốc + calibration, chỉ gọi gold sau khi đồng thuận và ghi quyết định |
| rear | Xe tiến gần, đèn ngược sáng, occlusion và vật ra khỏi khung | Kích thước thay đổi nhanh, dễ nhầm truncated với occluded và đứt track | Giữ timestamp liên tiếp, ego pose nếu có, calibration và trạng thái Outside | Review độc lập theo chuỗi frame; adjudication xác nhận identity, attribute và điểm bắt đầu/kết thúc track |
| left | Méo ở rìa, rider/xe máy dày, seam trái | Nhiều vật nhỏ chồng nhau và góc nhìn thay đổi làm tăng lỗi rider/box lồng | Giữ ảnh gốc, vùng ignore/ego_body, calibration trái và seam map | Hai reviewer rà scope/class/geometry; adjudicator xử lý bất đồng bằng ảnh liền kề và calibration |
| right | Xe lớn che vật nhỏ, ánh sáng thay đổi, seam phải | Occlusion và khác biệt giữa ảnh gốc/BEV dễ làm box không nhất quán | Giữ timestamp, exposure, calibration phải, seam map và annotation space ảnh gốc | Review độc lập rồi adjudication; kiểm tra cross-camera trước khi hợp nhất identity |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): refresh khi thay camera/lens/mount, thay calibration hoặc BEV transform, thay guideline/taxonomy, phát hiện drift ánh sáng/traffic, hoặc recurring error mới làm thay đổi tiêu chí review; giữ phiên bản cũ để so sánh.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: một xe máy xuất hiện đồng thời ở seam front-left với hai box khác kích thước; chỉ ghép khi có timestamp đồng bộ, calibration/extrinsic, vị trí seam/BEV và policy rõ về output giữ một box hay hai box.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: agreement chỉ cho biết hai người đồng ý trên cùng ảnh/luật, còn không kiểm tra calibration, seam, timestamp và biến dạng của camera khác; quality report một camera cũng không đo coverage hay identity xuyên camera.
