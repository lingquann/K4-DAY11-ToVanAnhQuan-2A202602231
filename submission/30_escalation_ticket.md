# Escalation Ticket

- Frame gặp ca khó: `adasind_102750.jpg`.
- Vấn đề: Xe tải cabin đỏ ở lề đường bên trái có độ tương phản thấp với bóng râm cây cối, kích thước xấp xỉ ngưỡng lọc (H ~ 105px nhưng ở rìa xa).
- Tác động (Impact): Ảnh hưởng đến độ nhạy phát hiện chướng ngại vật tĩnh (recall) của hệ thống SVM khi xe chuyển hướng vào ngõ/lề.
- Đề xuất (Recommendation): Cần sự phân xử của AI Lead / Data Ops về việc có gắn thêm nhãn ignore_region cho các vùng cây cối/bóng râm phức tạp ở rìa ảnh hay giữ box Truck có cờ occluded=true.
- Owner: data_ops.
