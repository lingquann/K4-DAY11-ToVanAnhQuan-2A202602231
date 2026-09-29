# Exit Ticket

**Câu 1 (Seam & 2 box): Tại vùng nhìn chồng giữa 2 camera, một vật thể xuất hiện trên cả 2 góc nhìn fisheye cần được gán nhãn như thế nào?**
-> Trả lời: Trên không gian ảnh gốc (raw fisheye), mỗi camera phải gán nhãn một bounding box độc lập ôm sát phần nhìn thấy của vật trên camera đó (gắn cờ truncated nếu bị cắt mép). Chỉ khi đưa lên không gian Bird's-Eye-View (BEV) hoặc không gian 3D thống nhất sau khi calibrate hệ SVM thì mới thực hiện hợp nhất (fuse/nms) thành một vật thể duy nhất.

**Câu 2 (Identity, keyframe/Outside & điều kiện nối track):**
-> Trả lời: Để liên kết track của một đối tượng qua nhiều camera, cần: (1) Đồng bộ timestamp chính xác giữa 4 camera; (2) Thông số hiệu chuẩn ngoại suy/nội suy (camera calibration matrices) để ước lượng vị trí vật thể trên mặt phẳng mặt đất; (3) Sử dụng keyframe định kỳ và gán trạng thái Outside khi đối tượng tạm thời rời khỏi góc nhìn của một camera nhưng vẫn tồn tại trong hệ thống.

**Câu 3 (Bất đồng thực tế & cách xử lý):**
-> Trả lời: Trình bày ca bất đồng về xe ThreeWheeler bị cắt viền tại adasind_069450.jpg giữa bản nháp (để truncated=false) và phản hồi QA (yêu cầu truncated=true). Cách xử lý: Đối chiếu quy tắc R05/R06, nhận thấy mép bánh xe chạm viền vành kính quang học, do đó chấp nhận rework bật truncated=true để đảm bảo tính nhất quán dữ liệu.
