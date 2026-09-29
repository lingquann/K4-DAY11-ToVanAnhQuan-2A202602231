# QA review · B3-edge

Mã khóa: 421B-0850

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_123090.jpg | L2 | R06 | Box chạm sát mép trái ảnh (x=0.8px) nhưng chưa kích hoạt thuộc tính truncated. Cần kiểm tra lại class Truck so với kích thước thực tế của xe trên nền đường. |
| adasind_128310.jpg | L1 | R04 | Box L1 được gán nhãn Bus nhưng kích thước tương đương xe van/xe con 5-7 chỗ (W=119px, H=123.9px), cần phân biệt lại giữa Bus và Car theo quy tắc R04. |
| adasind_128310.jpg | L2 | R06 | Đối tượng L2 Pedestrian nằm sát mép biên (x=6.8px), bị cắt một phần thân dưới và viền ngoài, cần bật cờ truncated. |
| adasind_199770.jpg | L2 | R06 | Box chạm hẳn vào mép ngoài cùng của ảnh (x=0.0px), bắt buộc phải có thuộc tính truncated theo R06. |
Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
