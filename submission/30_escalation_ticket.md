# Escalation ticket

## Ticket 1

- **Frame:** `adasind_062370.jpg`, các box reference `R7` và `R8`.
- **Ảnh chụp:** `submission/screenshots/evidence_062370_model_reference.png`
- **Expected impact:** Nếu giữ nguyên, reference có thể làm tăng giả tạo số `MISSING` ở zone `center` và làm sai quyết định rework; các thống kê local-quality và đánh giá model sẽ không đáng tin cho frame này.
- **Owner:** `qa`
- **Recommendation:** QA mở lại ảnh gốc và crop bằng chứng, xác nhận R7 có phải vật ThreeWheeler độc lập hay là box lồng trong R5; xác nhận R8 có thực sự là Truck hay là xe ba bánh/box không đủ rõ. Sau review độc lập, sửa teaching reference hoặc ghi rõ quyết định giữ và cập nhật `40_decision_log.csv`.
