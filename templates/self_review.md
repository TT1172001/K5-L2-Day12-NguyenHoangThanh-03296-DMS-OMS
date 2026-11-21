# Tự đánh giá — <Nguyễn Hoàng Thành> · <G04>

## 1. Tự rà soát 4 cảnh


Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
|S04_rgb |frame_meta |Sai giá trị thuộc tính |Sai giá trị thuộc tính (đúng: rgb, sai: ir) |Đã sửa sang rgb |
|D01 |frame_meta |Thiếu tag |Không thêm tag frame_meta cho ảnh |Thêm tag frame_meta với các thuộc tính đúng |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Thiếu tag frame_meta cho ảnh

Vì sao mình mắc: Vội vã làm gán nhãn cho các đối tượng trên ảnh mà không thêm frame_meta bắt buộc cho mỗi ảnh

Lần sau tránh bằng cách: Cần cẩn thận hơn

## 3. Ghi chú về disagreement_log

S04_rgb.png,frame_meta,modality,khác giá trị,ir,rgb,"peer đúng, mine sai",Ảnh rgb sẽ có modality là rgb,Sửa mine

Dòng này tôi sai vì ẩu, để modality mặc định cho frame_meta 
