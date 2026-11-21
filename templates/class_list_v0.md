# Danh sách lớp v0 — Nguyễn Hoàng Thành · G04

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**
Xóa 2 dòng ví dụ trước khi nộp.

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_left/eye_right | open / closed / unknown | Theo dõi mắt nhắm để phát hiện dấu hiệu buồn ngủ, cần chuỗi thời gian để phân biệt nhắm lâu với chớp mắt | Có, nhưng kính, phản xạ, góc mặt và ảnh tối có thể làm trạng thái không rõ |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Nhận biết tài xế đang nhìn đường hay chuyển hướng chú ý khỏi đường | Một phần, hướng mắt khó thấy trên NIR, nhất là khi đeo kính hoặc quay mặt |
| 3 | glasses | none / clear / sun / unknown | Diễn giải độ tin cậy của mắt và gaze, tránh coi mắt bị kính che là mắt bình thường | Thường thấy hình kính, nhưng loại kính có thể không phân biệt được trên NIR |
| 4 | seatbelt | worn_correct / worn_incorrect / not_worn / unknown | Nhắc thắt dây an toàn và phát hiện cách thắt sai | Có thể thấy dải dây, màu không đáng tin trên IR, dây tối hoặc bị che cần unknown |
| 5 | hand | on_wheel no/unknown/yes | Cảnh báo hoặc ghi nhận tay rời vô lăng, có ích khi đánh giá mức độ sẵn sàng điều khiển | Thường thấy vị trí bàn tay, nhưng tay hoặc vô lăng có thể bị khuất, tập Drive&Act có thể không có tay trên vô lăng |
| 6 | phone | held / mounted / lap | Phát hiện tương tác với điện thoại để cảnh báo mất tập trung | Có thể nhận ra hình dạng và vị trí, vật tối hoặc bị che không đủ căn cứ thì unknown |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person/seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định vị trí người/vật để đưa cảnh báo đúng ghế | Ghế và người thường thấy được, góc camera có thể che khuất, cần giữ quy ước trái/phải theo xe |
| 2 | person/seatbelt | unknown / worn_correct / worn_incorrect / not_worn | Nhắc thắt dây an toàn và phát hiện cách thắt sai | Có thể thấy dải dây, màu không đáng tin trên IR, dây tối hoặc bị che cần unknown |
| 3 | child_seat/occupied | no / unknown / yes | Nhận ra ghế trẻ em đang trống hay có vật thể/ trẻ em ngồi trên | Chỉ thấy được nếu vùng bên trong không bị che khuất |
| 4 | child_seat/seat | driver / front_passenger / rear_left / rear_middle / rear_right | Xác định vị trí ghế trẻ em để đưa cảnh báo | Ghế trẻ em thấy được, góc camera có thể che khuất, cần giữ quy ước trái/phải theo xe |
| 5 | infant_seat | facing: rear / front | Nhận biết nôi em bé và hướng lắp để hỗ trợ cảnh báo an toàn, gồm nhắc kiểm tra trẻ bị bỏ quên | Hình dạng và hướng thường thấy, vật che hoặc góc nhìn có thể gây unknown |
| 6 | object | bag / box / cup / other | Phát hiện đồ vật để ghi nhận vật có thể gây vướng hoặc trở thành vật bay khi xe phanh gấp | Thường nhận dạng được qua hình dạng/vị trí, IR không giữ màu nên không dùng màu để phân loại |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Muốn cảnh báo buồn ngủ, guideline/model cần ngưỡng thời gian mắt đóng bao lâu và xử lý chớp mắt thế nào? Guideline v1.0 chỉ định nghĩa trạng thái ở từng khung, chưa có quy tắc theo thời gian.
   Khung ví dụ: G04/D01.png (khung DMS minh họa; cần xem chuỗi liền kề để kết luận thời lượng).
   Bạn tạm gán thế nào và vì sao: Gán `eye_left` và `eye_right` độc lập theo đúng khung; mắt không nhìn rõ thì `unknown`. Không kết luận buồn ngủ từ một khung vì nhãn hiện tại không mã hóa thời lượng.
2. Câu hỏi: Khi OMS thấy ghế trẻ em nhưng không nhìn rõ bên trong, đầu ra sản phẩm cần là “có ghế, tình trạng trẻ chưa rõ” hay được phép dự đoán có trẻ? Guideline hiện không có giá trị occupied=yes.
   Khung ví dụ: G04/S01_ir.png (khung IR-sim minh họa; cần đối chiếu ảnh thực tế nếu lòng ghế bị che).
   Bạn tạm gán thế nào và vì sao: Gán `child_seat` với `occupied = unknown` nếu không thấy rõ bên trong; không tạo nhãn có trẻ vì guideline cấm `yes` và ảnh IR-sim không đủ căn cứ để suy đoán.
