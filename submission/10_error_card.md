# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B2 | MISSING | 8 |
| center | B2 | SPURIOUS | 12 |
| center | C0 | SPURIOUS | 3 |
| edge | B2 | MISSING | 1 |
| edge | B2 | SPURIOUS | 2 |
| edge | B2 | WRONG_CLASS | 1 |
| mid | B2 | MISSING | 3 |
| mid | B2 | SPURIOUS | 4 |
| mid | B2 | WRONG_CLASS | 2 |

## Top defects
- SPURIOUS: 21 (ví dụ frame adasind_019560.jpg)
- MISSING: 12 (ví dụ frame adasind_062370.jpg)
- WRONG_CLASS: 3 (ví dụ frame adasind_102750.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: `SPURIOUS` chiếm nhiều nhất vì có cả lỗi annotator và lỗi model. Ở `adasind_062370.jpg`, model lặp lại nhầm nhiều `ThreeWheeler` thành `Truck` và tách rider thành `Pedestrian`; ở `adasind_117120.jpg`, L1/L5 là sai lớp hoặc box trùng của annotator. Một số khác biệt `R7/R8` ở `adasind_062370.jpg` có dấu hiệu reference lồng/trùng nên đã escalation thay vì kết luận learner sai.
- Cách sửa và ai nhận việc (`owner`): sửa các box L sai lớp/trùng theo R03/R04 ở rework bởi `annotator`; giữ nguyên nhãn đúng và không thêm các box M-only. Gửi các mẫu model nhầm `ThreeWheeler→Truck`, `Car→Truck` và rider→`Pedestrian` cho `ai_team`; QA kiểm tra độc lập các box reference lồng/trùng. Cập nhật guideline patch R12 để làm rõ quy tắc box lồng và rider.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `screenshots/evidence_062370_model_reference.png` và `screenshots/evidence_117120_duplicates.png`; các dòng `r3_diag` tương ứng với `L4`, `R7`, `R8`, `M3/M5/M8/M10`, `L1/L5`; `docs/02-rules-vi.md` R02–R04 và `submission/r3_diag/model_compare.md`.
