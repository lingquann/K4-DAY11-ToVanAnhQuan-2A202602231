# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| Lát cắt điều kiện ánh sáng gắt ngược chiều làm lóa viền vật thể | 3 ca ATTRIBUTE, MISSING | Dễ gây lỗi mô hình trong phát hiện vật thể tĩnh | Giữ cờ occluded và bbox cẩn thận |
| Lát cắt vùng rìa mép kính quang học nơi đối tượng bị biến dạng méo hình học cực đại | 4 ca BOX_GEOMETRY, TRUNCATED | Vật thể bị thay đổi hình dạng mạnh | Giữ nguyên bbox trên raw fisheye và cờ truncated |

Giới hạn của kết luận từ ba frame ADASIND: Số lượng mẫu quá nhỏ, không đại diện đầy đủ cho các kịch bản thời tiết hay giao thông đa dạng.

## Chuyển sang kế hoạch bốn camera giả lập

Kiểm tra phân bổ đồng đều giữa 4 vị trí gắn camera (front, rear, left, right) và cân bằng tỉ lệ mẫu bình thường (normal) với mẫu phức tạp (hard) để tránh thiên lệch (bias) dữ liệu. Việc review 200 frame chỉ giúp tìm ra các ca cần soi, chưa đủ lớn để đo được tỷ lệ lỗi thống kê đại diện cho toàn bộ 50,000 frames.
