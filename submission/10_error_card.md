# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| edge | B2 | ATTRIBUTE | 2 |
| edge | B3 | ATTRIBUTE | 3 |
| edge | C0 | SPURIOUS | 1 |
| mid | B2 | BOX_GEOMETRY | 1 |
| mid | B3 | WRONG_CLASS | 1 |
| unknown | B2 | ATTRIBUTE | 2 |
| unknown | B2 | BOX_GEOMETRY | 1 |
| unknown | B2 | MISSING | 2 |
| unknown | C0 | ATTRIBUTE | 1 |
| unknown | C0 | WRONG_CLASS | 1 |

## Top defects
- ATTRIBUTE: 8 (ví dụ frame adasind_123090.jpg)
- WRONG_CLASS: 2 (ví dụ frame adasind_128310.jpg)
- MISSING: 2 (ví dụ frame adasind_102750.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân gốc rễ: Hiện tượng biến dạng fisheye mạnh ở vùng rìa kính (edge zone) làm giảm độ phân giải thực tế của vật thể, dẫn đến việc annotator dễ bỏ sót xe tải đỗ xa (adasind_102750.jpg) và quên bật thuộc tính `truncated` khi vật chạm mép vòng kính đen (adasind_069450.jpg, adasind_082170.jpg).
- Hiện tượng bóng đổ và xe đỗ sát nhau gây nhầm lẫn ranh giới tiếp xúc mặt đường và trạng thái `occluded`.
- Biện pháp khắc phục: Soát kỹ viền tiếp xúc bánh xe/mặt đường, kiểm tra tọa độ x sát 0px hoặc chạm viền kính để ép thuộc tính `truncated`.
