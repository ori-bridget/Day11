# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? **Cần một quy tắc seam riêng, không tự động gọi là `DUPLICATE`.** Hai box có thể cùng là một vật hợp lệ vì hai camera thật có vùng nhìn chồng; cần timestamp, calibration, vị trí seam và policy output để quyết định giữ box, hợp nhất hay giữ cả hai cho tầng sau.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? **Giữ cùng track ID khi cùng vật còn quan sát được và hình học/động học liên tục; thêm keyframe khi hình dáng hoặc góc nhìn thay đổi đáng kể; dùng `Outside` khi vật ra khỏi vùng nhìn thay vì tạo identity mới tùy tiện.** Trước khi nối track qua hai camera cần timestamp đồng bộ, calibration/extrinsic, homography hoặc BEV, hướng chuyển động, vị trí seam và policy định danh cross-camera.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? **Ở `adasind_062370.jpg`, L4 khác R4 vì learner gán Truck cho xe van; ở `adasind_117120.jpg`, L1/L5 khác reference vì sai lớp/trùng box.** Mình đối chiếu ảnh gốc, overlay và R02–R04, chọn rework cho lỗi annotator và escalation cho R7/R8 khi nghi reference lồng/sai. Nếu làm lại, mình sẽ kiểm rider/box lồng trước khi khóa, ghi evidence ngay khi review và rà các ca center dày trước khi chuyển sang model comparison.
