# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): vạch chéo trắng ở tiền cảnh giữa ảnh (xấp xỉ từ (407,653) đến (529,719)) và vạch chéo trắng ở tiền cảnh bên phải (xấp xỉ từ (700,624) đến (959,684)). Cả hai đều là cạnh phân chia các ô đỗ riêng lẻ và phần sơn nhìn thấy liên tục.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: dải sơn gần ngang chạy từ mép trái sang mép phải ở khoảng y=541 xuống y=508. Dải này là biên cuối hàng/lối xe chạy liên tục, không phải cạnh của một ô đỗ riêng lẻ, nên không gán `parking_line`.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: vùng nằm trên mặt đường trống của lối xe chạy ở dải giữa–tiền cảnh, phía dưới hàng vạch đỗ và phía trên vùng vạch/biên tiền cảnh; polygon dừng tại các vạch sơn nhìn thấy và mép ảnh, không đi xuyên xe, curb, cây hoặc hàng rào. Không có phần bị che trong vùng đã chọn.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): không có.
