# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 6 | 1 | 1 | 1 | 3 | SPURIOUS (1) |
| mid | 6 | 0 | 0 | 4 | 8 | — |
| edge | 6 | 2 | 0 | 4 | 1 | MISSING (2) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Người (L) gặp khó khăn nhất ở zone edge (2 lỗi MISSING), trong khi model (M) gãy nhiều nhất ở zone mid (4 lỗi MISSING và 8 lỗi thừa/SPURIOUS).
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Nguyên nhân ở zone edge do độ méo fisheye rất lớn và xe khuất bóng râm khiến người vẽ bỏ sót. Ở zone mid, model bị lừa bởi các chi tiết nhiễu hoặc sai lệch bối cảnh cục bộ. Tuy nhiên, kết luận này bị giới hạn do kích thước tập mẫu quá nhỏ (chỉ 3 frames).
