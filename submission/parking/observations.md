# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Hai vạch chia ô đã chọn: Vạch phân định ô đỗ tiền cảnh bên trái và vạch chia ô kế cận song song.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Một dấu sơn/biên đã loại: Vạch sơn vàng chỉ lối xe chạy ở giữa làn đường (loại vì là vạch dẫn hướng lối đi, không phải vạch ranh giới ô đỗ riêng lẻ).
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Vùng trống (free_space): Bao trùm mặt đường lối xe chạy, dừng trước mép bánh xe đang đỗ và vỉa hè, không đè lên curb hay vùng khuất bóng cây.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Không có
