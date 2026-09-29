# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 13 | 2 | 2 | 6 | 7 | MISSING (2) |
| mid | 5 | 1 | 1 | 2 | 3 | WRONG_CLASS (1) |
| edge | 2 | 0 | 0 | 1 | 2 | — |

## Nhận xét

- Zone trung tâm (`center`) gãy nhiều nhất: L có 2 `MISSING` và 2 `SPURIOUS`; M có 6 `MISSING` và 7 box thừa, cao hơn `mid` (2/3) và `edge` (1/2). Lỗi chính của L ở zone này là `MISSING` (2).
- Giả thuyết: vùng `center` trong ba frame có nhiều xe ba bánh, xe chồng lấn và rider; model lặp lại nhầm `ThreeWheeler` thành `Truck` hoặc tách rider thành `Pedestrian`, còn một số box L/reference bị sai lớp hoặc lồng nhau. Đây chỉ là giả thuyết theo slice ba frame; `center/mid/edge` là bin chẩn đoán chứ không phải khoảng cách, reference không phải gold set, và cần thêm frame cùng review độc lập trước khi khái quát.
