# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | phương tiện cơ giới có 4 bánh, thiết kế để chở 2 - 5 người | xe 4 bánh, kiểu dáng 2 hoặc 3 khoang |
| `truck` | xe chuyên dùng để chở hàng hoá, vật liệu hoặc kéo phương tiện khác | tách biệt rõ ràng giữa khoang cabin và thùng xe |
| `bus` | phương tiện cỡ lớn, thiết kế để chở lượng người lớn | dài, hình hộp chữ nhật, có dãy cửa kính chạy dọc xe |
| `van` | xe chở hàng cỡ trung hoặc chở người số lượng vừa, thiết kế dạng khung liền khối | đầu xe ngắn, mũi xe không nhô ra, thân xe có dạng hình hộp |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: box phải chạm sát 4 điểm biên của vật thể, không để lại khoảng thừa
- Vật thể bị che khuất: vật thể bị che bởi vật thể khác, dựa vào phần trăm bị che khuất và đặc điểm của vật thể để đưa ra quyết định có vẽ box hay không
- Vật thể bị cắt bởi rìa ảnh: là vật thể ở mép của ảnh và chỉ hiển thị được một phần của vật thể, không được vẽ box tràn ra ngoài khung hình
- Vật thể rất nhỏ/mơ hồ: vật thể có kích thước quá nhỏ hoặc quá mờ không khiến không thể xác định được thuộc lớp nào

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_16` | ở làn xe phía bên phải có hình ảnh xe mờ và nhỏ, đang phân vân giữa "van" hoặc "car" | bb lớp là van | vì nhận biết theo chiều cao của xe thì nhận ra khả năng class là "van" cao |
| `drive_24` | xe có dạng cabin hộp, hình ảnh khá mờ và có thể bị scale down nên hình ảnh xe bị sai lệch không phân biệt được là class "van" hay "car" | bb là car | vì xe chỉ có 1 kính ở phía hông nên gán nhãn là car |
| `drive_26` | có 2 xe đỗ ở lề bên trái rất nhỏ nên không phân biệt được class | không bb | |
