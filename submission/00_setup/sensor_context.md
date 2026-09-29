# Sensor context

- Quan sát rig: ảnh là camera fisheye gắn trên một phương tiện đang chạy và hướng về phía trước; thấy người lái/chi tiết phương tiện ở mép dưới, nhưng repo không cung cấp tài liệu để khẳng định vị trí gắn chính xác.
- `ego_body` nhìn thấy ở phần dưới và góc trái frame: tay/người lái, tay lái/ốp xe và vùng thân xe tối ở đáy; phần này được coi là vùng cần ignore khi xuất hiện.
- Vòng kính (lens circle) gần chiếm toàn bộ chiều rộng ảnh, bắt đầu khoảng dưới mép trên và kết thúc trước mép dưới; viền đen cong rõ ở bốn phía, đặc biệt dày ở góc và đáy ảnh.
