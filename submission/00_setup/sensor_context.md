# Sensor context

- Rig: Vị trí camera gắn quanh xe ego (hệ thống SVM 4 camera: trước mặt ca-lăng, sau cốp/biển số, 2 bên gương chiếu hậu). Giới hạn dữ liệu: Slice hiện tại chỉ cung cấp ảnh từ 1 camera đơn lẻ, không kèm ma trận hiệu chuẩn (intrinsic/extrinsic calibration) và không chứng nhận vùng lái xe an toàn tự động.
- `ego_body` nhìn thấy: Vùng thân xe ego nhìn thấy ở góc dưới của một số frame fisheye.
- Vòng kính (lens circle): Vòng kính quang học tạo viền tròn đen (lens border) ở khu vực rìa khung hình.
