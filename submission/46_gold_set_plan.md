# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Loá sáng ngược chiều và vật thể chuyển động nhanh | Vùng chiếu sáng không đều, độ tương phản giảm mạnh | Giữ nguyên bounding box 2D trên mặt phẳng ảnh, đối chiếu thông số calib pitch/yaw | Double-blind review với 2 annotator độc lập; nếu IoU < 0.7 Data Lead phân xử |
| rear | Điểm mù góc thấp và bụi bẩn bám ống kính | Đuôi xe che khuất một phần góc nhìn thấp, khó xác định chân bánh xe | Ghi nhận vùng lens_border và phần che khuất bởi đuôi xe (ego_body) | Double-blind review với 2 annotator độc lập; nếu IoU < 0.7 Data Lead phân xử |
| left | Vật thể bị cắt vùng seam và che khuất liên tục | Biến dạng fisheye cực đại ở vùng viền (edge distortion), mất mát thông tin góc | Giữ nguyên bounding box riêng trên từng ảnh fisheye gốc, bắt buộc cờ truncated | Double-blind review với 2 annotator độc lập; nếu IoU < 0.7 Data Lead phân xử |
| right | Biến dạng fisheye cực đại và khuất tầm nhìn vỉa hè | Cấu trúc vật thể bị thay đổi, góc nhìn sát sườn xe che lấp một số điểm neo | Giữ nguyên bounding box riêng trên từng ảnh fisheye gốc, đối chiếu vị trí tiếp xúc | Double-blind review với 2 annotator độc lập; nếu IoU < 0.7 Data Lead phân xử |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): Cập nhật định kỳ 10% tập Gold Set mỗi chu kỳ release model lớn hoặc khi thay đổi cấu hình rig camera, hoặc tinh chỉnh tham số hiệu chuẩn.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: Vùng Seam: Định nghĩa chính sách gán nhãn ở vùng chồng lấn (overlap). Đối tượng xuất hiện ở 2 camera phải giữ bounding box riêng trên từng ảnh fisheye gốc trước khi ghép 360 BEV.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: Đánh giá độc lập trên một camera không tính tới độ tương đồng không gian (spatial consistency) và thời gian (temporal consistency) khi ghép ảnh BEV, có thể dẫn đến lệch vị trí khi fuse 360 độ. Mọi trường hợp xung đột nhãn sẽ do Data Lead chủ trì phân xử (adjudication).
