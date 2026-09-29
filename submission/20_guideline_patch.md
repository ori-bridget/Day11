# Guideline patch

- **Rule mới đề xuất:** **R12 — Một vật một box trong cùng camera:** nếu một box đã bao trọn phần nhìn thấy của vật và rider đi cùng xe hai bánh, không tạo thêm box con cho rider hoặc một box nhỏ lồng bên trong. Rider + xe hai bánh giữ một box `Bike`; chỉ tách `Pedestrian` + `Bike` khi người đó đang dắt xe và hai phần có ranh giới quan sát được. Khi hai box lồng nhau nhưng không có vật độc lập thứ hai trên ảnh, đánh dấu box nhỏ là `DUPLICATE` để xoá hoặc escalation.
- **Áp dụng cho:** `Bike`, `Pedestrian`, `ThreeWheeler` và mọi box rectangle trong cùng một frame; đặc biệt các vùng chồng lấn/rìa fisheye ở `center` và `edge`. Không áp dụng để tự động hợp nhất box giữa hai camera SVM.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R03 đã nói về rider nhưng chưa nêu rõ cách xử lý box rider lồng trong box xe; R09/R02 cũng chưa có tiêu chí một-vật-một-box để phân biệt box nhỏ lồng là vật độc lập hay trùng. Các ca `M3/M4/M6` và `L5/R7` cho thấy cần tiêu chí hình học và bằng chứng vật độc lập.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** vòng `rework` sau khi được QA phê duyệt; dùng thử trên các round tiếp theo, không sửa hồi tố `docs/02-rules-vi.md` trong bài này.
