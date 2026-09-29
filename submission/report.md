# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: K4
- Tên nhóm: Nhóm 3 (Thạch - Minh - Quân)
- Repo Public: <https://github.com/lingquann/K4-DAY11-ToVanAnhQuan-2A202602231>
- Máy giữ hồ sơ chính / người quản lý: Tô Văn Anh Quân
- Slice chung lấy từ mode.json: B2-edge
- Tên định danh vai A dùng cho --self: thach
- Kênh trao đổi nội bộ: Zalo / Discord Nhóm
- Đại diện nộp (vai C): Tô Văn Anh Quân, MSSV: 2A202602231
- Commit chốt bài: HEAD (cập nhật sau khi git push commit cuối)

## 2. Ba vai chính

| Vai | Họ và tên | MSSV | Tên định danh trong mode | Trách nhiệm | Bằng chứng đóng góp |
| --- | --- | --- | --- | --- | --- |
| A · Gán nhãn | Cầm Vũ Ngọc Thạch | 02067 | thach | Parking/C0/slice, self-QC, lock, rework | Thực hiện gán nhãn slice B2-edge, tạo lock.txt ban đầu và export rework bản v2 |
| B · QA độc lập | Minh | | minh | Review trước reference, finding QA, kiểm lại ca sửa | Thực hiện QA mù slice B2-edge, tạo mã khóa B28A-2C10 và ghi nhận xét trong qa_review.md |
| C · Chẩn đoán & điều phối | Tô Văn Anh Quân | 02231 | quan | Báo cáo, phân xử, kế hoạch, tích hợp, check và nộp | Chạy compare, model, local-quality, hoàn thiện findings.csv, lập kế hoạch 4 camera và check nộp bài |

Bảng này xác định vai của nhóm. Vòng QA tự sinh trong team.json thuộc quy trình nhiều hồ sơ của CLI; nhóm dùng một slice chung và quy trình A → B → C đã nêu trong hướng dẫn.

## 3. Bàn giao theo pha

| Mốc | Người giao → nhận | File / commit / mã khóa | Người nhận đã kiểm gì? | Trạng thái / vướng mắc |
| --- | --- | --- | --- | --- |
| P0 · Chốt môi trường và vai | C → A, B | mode.json, slice B2-edge | Đã kiểm tra môi trường doctor.txt, xác nhận slice B2-edge | Hoàn thành |
| P2 · Khóa bản đầu | A → B, C | annotations.xml, lock.txt (Mã: B28A-2C10) | Đã kiểm tra selfqc.md đủ 9 tiêu chí và tính toàn vẹn file export | Hoàn thành |
| P3 · Chốt QA mù | B → C, A | qa_review.md, findings.csv (4 findings) | Đã kiểm tra 4 nhận xét trên adasind_069450, 082170, 102750 chưa mở reference | Hoàn thành |
| P4 · Quyết định sửa | C → A, B | findings.csv, decision log (D1-D4) | Đã đối chiếu compare.html, xác nhận 4 ca cần rework (P1/P2) | Hoàn thành |
| P5 · Kiểm bản sửa | A → B → C | annotations-v2.xml, lock2.txt, delta.md | Đã kiểm tra độ lệch delta.md: giảm lỗi missing và sửa thuộc tính truncated | Hoàn thành |
| P6 · Chốt nộp | A, B → C | Toàn bộ thư mục submission/, check exit 0 | Đã chạy lab11.py check, không còn lỗi gate | Sẵn sàng nộp |

## 4. Bất đồng và phối hợp

- Một ca đã phân xử: Ca đối tượng Truck ở lề trái frame `adasind_102750.jpg`. Nhãn ban đầu của vai A bỏ sót do xe nằm trong vùng tối bóng râm. Vai B (QA) phát hiện chiều cao vật ~105 px (vượt ngưỡng H=40px theo R01). Vai C đã đối chiếu với ảnh gốc và quyết định bổ sung box Truck với cờ `occluded=true`, đồng thời kéo sát chân bánh xe bên phải (L3) theo quy tắc R02.
- Ca còn mở: Không còn ca mở chưa giải quyết; các trường hợp nhấp nhô bóng râm đã ghi nhận vào ticket escalation và guideline patch.
- Đóng góp của A/B/C vào kế hoạch và exit ticket:
  - Vai A: Đóng góp nhận định về khó khăn khi vẽ box sát mép vành kính fisheye cho mục 46_gold_set_plan.md.
  - Vai B: Đóng góp phân tích về việc phân định nhầm xe và cờ truncated/occluded trong 10_error_card.md.
  - Vai C: Xây dựng toàn bộ phân bổ 200 frame trong 45_sampling_plan.csv, trả lời 3 câu hỏi exit ticket (vùng seam, identity tracking và bất đồng thực tế).
- Thay đổi phân công nếu có: Không có thay đổi, các thành viên thực hiện đúng theo tiến độ phân vai ban đầu.

## 5. Xác nhận trước khi nộp

- [x] A xác nhận nhãn và export đúng phiên bản: Cầm Vũ Ngọc Thạch - Đã kiểm tra bản rework v2.
- [x] B xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: Minh - Đã kiểm tra 4 ca sửa đạt yêu cầu.
- [x] C xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: Tô Văn Anh Quân - Đã chạy python lab11.py check thành công.
- [x] manifest.json tại commit chốt có failed_gates rỗng.
- [x] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [x] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.
