# Báo cáo Day 13, Phạm Công Bằng, 2A202603134

## 1. Kết luận trước

Mã số sinh viên 2A202603134, mã nhiệm vụ D13-2A202603134, gồm 10 khung hình: s01f04, s01f55, s02f00, s02f21, s03f07, s03f47, s04f19, s04f47, s05f12, s05f42. Máy chạy Windows, mở CVAT trên trình duyệt Chrome, phiên bản CVAT 2.74.1, ngồi cạnh bạn có mã số [điền MSSV bạn đổi kiểm].

Tổng cộng đã vẽ 97 khối hộp 3D dạng hình đơn trên 10 khung hình (s01f04 có 12, s01f55 có 12, s02f00 có 7, s02f21 có 9, s03f07 có 10, s03f47 có 7, s04f19 có 16, s04f47 có 8, s05f12 có 10, s05f42 có 6). Khung hình ít hộp nhất là s05f42 với 6 hộp do có xe ở xa phía sau bị che khuất và ít điểm nên không vẽ. Phiếu tự kiểm báo 0 trên 97 hộp bị cảnh báo. Phần tự tin nhất là xác định đúng loại đối tượng, hướng đầu xe và độ cao đáy chạm đường với các vật trong khoảng 25 m; phần còn phân vân là cạnh khuất của các xe ở xa trên 30 m.

Khi dùng CVAT, giữ chuột trái để xoay khung nhìn 3D lên thẳng trên xuống, giữ chuột phải để dịch chuyển vùng nhìn, cuộn con lăn để phóng to thu nhỏ và nháy đúp chỗ trống để về góc nhìn mặc định. Khi vẽ, chọn công cụ vẽ khối hộp, chọn đúng loại nhãn ở chế độ hình đơn rồi nháy đúp vào cụm điểm của vật, sau đó chỉnh tâm, dài, rộng, góc quay ở khung nhìn trên và chỉnh độ cao đáy chạm đường ở khung nhìn cạnh và trước. Cuối cùng bật mũi tên hướng để căn vạch đỏ về đầu xe, lưu lại và chạy lệnh đồng bộ để đối chiếu lại toàn bộ hộp lên 7 góc máy ảnh.

## 2. Đọc frame

| Frame | Phía trước xe ở cạnh nào của ảnh nhìn từ trên xuống; +x, +y chỉ về đâu | Mặt đường | Vật xa nhất đọc được | Loại vật thấy | Vật phía sau và hai bên | Cụm chưa đọc được |
|---|---|---|---|---|---|---|
| s01f04 | Phía trước nằm ở cạnh trên theo góc cam01; trục +x hướng sang trái, trục +y hướng xuống dưới ra sau | Khá phẳng, cao độ mặt đường quanh âm 1,67 m (phía trước khoảng âm 1,79 m, phía sau khoảng âm 1,62 m), vỉa hè hai bên nhô cao nhẹ | Khoảng 45 đến 50 m dọc theo đường chính | Car, Truck ở làn ngược chiều bên trái, Bus ở ngã tư phía xa, Cyclist ở vạch qua đường phía sau | Phía sau trái khoảng 6,7 m có xe con xanh; phía sau khoảng 16 m và 23 m có xe con đi tới; bên trái có xe tải thùng trắng | Vài cụm điểm rời rạc ven hàng cây bên phải và ngoài ngã tư phía sau phải trên 35 m |
| s01f55 | Phía trước nằm ở cạnh trên theo góc cam01; trục +x hướng sang trái, trục +y hướng xuống dưới ra sau | Phẳng, dốc nhẹ lên về phía trước, cao độ quanh âm 1,76 m (phía trước khoảng âm 1,61 m, phía sau khoảng âm 1,77 m), lề phải cao hơn lòng đường | Khoảng 40 đến 45 m ở các xe xếp hàng phía trước | Car xếp hàng trước sau, Bus hoặc xe van cao ở xa phía trước, Pedestrian trên vỉa hè phải | Phía sau khoảng 7 m có hai xe con trắng; bên phải trên vỉa hè có hàng xe đạp dựng không người | Cụm điểm lẫn giữa tán cây, trụ đèn và hàng xe đạp dựng trên vỉa hè phải |

Ba điều chỉ máy ảnh cho biết từ hai khung hình trên gồm màu sắc và kiểu dáng xe (phân biệt xe tải thùng với xe con), phân biệt đầu đuôi xe và nhận biết xe đạp dựng không có người trên vỉa hè phải ở s01f55 để không gán nhãn nhầm, cùng vạch kẻ đường, đèn tín hiệu và biển báo. Ba điều chỉ LiDAR cho biết gồm tọa độ không gian và khoảng cách chính xác bằng mét tới từng vật, kích thước thực dài rộng cao theo mét cùng độ cao mặt đường, và toàn cảnh 360 độ kể cả vùng góc khuất giữa các máy ảnh.

| Frame | Phía trước ở cạnh nào của ảnh nhìn từ trên xuống | Điều lạ |
|---|---|---|
| s02f00 | Cạnh trên theo hướng cam01 | Xe buýt đỏ sát bên trái tạo vùng bóng che lớn phía sau trái nó |
| s02f21 | Cạnh trên theo hướng cam01 | Có người đi xe tay ga sát lề phải và hàng rào hai bên tạo vệt điểm thẳng dài |
| s03f07 | Cạnh trên theo hướng cam01 | Tường quây công trình sát hai bên che khuất ngoài lề, có một điểm lẻ rơi sâu dưới đất ở cao độ âm 4,6 m |
| s03f47 | Cạnh trên theo hướng cam01 | Có xe buýt đi ngang giao lộ ở xa phía trước và người đi xe đạp sau rào bên phải |
| s04f19 | Cạnh trên theo hướng cam01 | Xe đông cả phía trước lẫn phía sau, có xe máy đi ngay chính giữa phía sau |
| s04f47 | Cạnh trên theo hướng cam01 | Hai xe phía trước bên phải đi gần nhau nên phần hông xe ngoài bị che bớt |
| s05f12 | Cạnh trên theo hướng cam01 | Ngã tư rộng có nhiều hướng xe cắt ngang và rẽ qua giao lộ |
| s05f42 | Cạnh trên theo hướng cam01 | Xuất hiện nhiều điểm nằm thấp hơn hẳn mặt đường về phía bên trái |

## 3. Ba cuboid có hướng dẫn

| Vật | Frame, idx | Class | Mũi tên yaw đúng hướng | Đáy chạm đường | Đã kiểm 3 góc nhìn và ảnh | Kích thước trong bảng 4.3 |
|---|---|---|---|---|---|---|
| Xe con gần | s01f04, idx 2 | Car | Có, góc 265,0 độ hướng về đầu xe | Có, độ hở 0,01 m | Có, đã đối chiếu cam05 và cam09 | Dài 4,49 m, rộng 2,09 m gồm gương, cao 1,50 m |
| Xe tải | s01f04, idx 4 | Truck | Có, góc 89,5 độ hướng về đầu xe | Có, độ hở 0,07 m | Có, đã đối chiếu cam05 và cam06 | Dài 5,75 m, rộng 2,25 m, cao 2,97 m |
| Xe hai bánh | s01f04, idx 7 | Cyclist | Có, góc 270,0 độ theo mũi xe | Có, độ hở 0,01 m | Có, đã đối chiếu cam08 và cam09 | Dài 1,81 m, rộng 0,86 m, cao 1,67 m |

Qua đối chiếu quy chuẩn, cần luôn bật mũi tên hướng để kiểm tra chiều đầu xe, mở rộng chiều rộng hộp đủ bao hai gương chiếu hậu và chỉnh đáy chạm đúng cao độ mặt đường tại vị trí đặt vật.

Các vật bỏ qua vì không đủ cơ sở gồm các cụm điểm quá thưa ở mép cây và ngoài ngã tư trên 35 m ở s01f04 do không rõ hình dạng, hàng xe đạp dựng không người trên vỉa hè phải ở s01f55 theo quy tắc không gán xe không người, và xe buýt ở xa phía sau trên 32 m ở s05f42 bị xe phía trước và tán cây che gần hết chỉ còn ít điểm rời.

## 4. Bốn hiện tượng chất lượng

| Hiện tượng | Frame, ảnh, nguồn | Nguyên nhân giả thuyết | Thấy gì trên point cloud | Hệ quả khi gán theo quy chuẩn |
|---|---|---|---|---|
| 1. Bóng che | s02f00, t4-1-bong-che.png, frame bản thân | Giả thuyết do thân xe buýt đỏ cao và dài ở khoảng 9,14 m chắn tia quét LiDAR | Phía sau trái xe buýt tạo thành một vùng trống hoàn toàn không có điểm trong khi hai bên vẫn dày điểm | Vùng trống là chỗ chưa quan sát được; nếu có vật bị che một phần phía sau cần bật thuộc tính bị che khuất và bao cả phần suy luận được |
| 2. Thưa ở xa | s02f00, t4-2-thua-o-xa.png, frame bản thân | Giả thuyết do các tia quét tách xa nhau dần theo khoảng cách trên 40 m | Xe ở 41,10 m chỉ còn 43 điểm và xe ở 45,23 m chỉ còn 25 điểm ở phần đuôi | Chỉ vẽ khi thấy khoảng 15 đến 20 phần trăm thể tích và nhìn rõ qua ảnh máy ảnh, còn thưa quá không đủ cơ sở thì bỏ qua |
| 3. Phản xạ thấp | s03f07, t4-3-phan-xa-thap.png, frame bản thân | Giả thuyết do sơn xe tối màu và kính sẫm hấp thụ hoặc phản xạ lệch tia laser | Xe đen ở 7,93 m chỉ thu được 1466 điểm, ít hơn xe đỏ 7,03 m ở s03f47 có 2053 điểm hay xe trắng 7,26 m ở s01f55 có 1813 điểm | Không thu hẹp hay nới lỏng hộp theo phần thiếu điểm mà dựa thêm ảnh máy ảnh và mép thân dưới để giữ đúng kích thước thật |
| 4. Điểm lạ | s05f42, t4-4-diem-la.png, frame bản thân | Giả thuyết do tia laser phản xạ nhiều lần qua kính, thân xe bóng hoặc sai số cảm biến | Có 1881 điểm có cao độ thấp hơn âm 2,6 m, trung vị âm 2,94 m ở phía bên trái (tương tự s03f07 có điểm đơn lẻ ở âm 4,6 m) | Không gán thành vật thể cho các điểm rơi dưới mặt đường hay lơ lửng |

## 5. Số từ cuboid của tôi

| Cuboid | z (m) | h (m) | z đáy (m) | dist_m (m) | r (m) | yaw_deg (độ) | Nhận xét |
|---|---|---|---|---|---|---|---|
| s01f04, idx 1, Car | -1.067 | 1.509 | -1.821 | 11.61 | 11.66 | 266.5 | Chạm đường |
| s02f00, idx 1, Bus | -0.142 | 3.463 | -1.873 | 9.14 | 9.14 | 270.0 | Chạm đường |
| s01f55, idx 9, Pedestrian | -0.537 | 1.587 | -1.331 | 21.48 | 21.49 | 270.0 | Chạm mặt vỉa hè nâng cao |

Hộp gần nhất là s03f07 idx 1 (Car) có dist_m bằng 3,51 m và khoảng cách 3D r bằng 3,66 m. Hộp xa nhất là s02f00 idx 6 (Car) có dist_m bằng 45,23 m và r bằng 45,25 m.

So với bảng 4.3, người đi bộ ở s02f21 idx 6 có kích thước dài 0,750 m, rộng 0,700 m, cao 1,740 m nên cả ba chiều đều nằm gọn trong khoảng chuẩn của người lớn (dài 0,4 đến 0,9 m, rộng 0,5 đến 0,9 m, cao 1,50 đến 1,95 m). Xe con ở s01f04 idx 2 có dài 4,488 m, rộng 2,087 m, cao 1,496 m; chiều dài và chiều cao nằm trong khoảng chuẩn xe con (dài 3,8 đến 5,0 m, cao 1,40 đến 1,60 m), riêng chiều rộng lớn hơn mức 1,90 m khoảng 0,19 m do phải bao trọn cả hai gương chiếu hậu hai bên.

Xe chạy cùng chiều phía trước ở s03f07 idx 3 có yaw_deg bằng 274,5 độ, gần với mốc 270 độ. Xe chạy ngược chiều ở s01f04 idx 3 có yaw_deg bằng 92,5 độ, gần với mốc 90 độ.

| Cuboid | dist_m (m) | Số điểm |
|---|---:|---:|
| s03f07, idx 1, Car | 3.51 | 2151 |
| s01f55, idx 3, Car | 10.26 | 1013 |
| s01f04, idx 9, Car | 23.29 | 350 |
| s01f04, idx 12, Car | 37.05 | 35 |

Khi khoảng cách tăng gấp khoảng 3,6 lần (từ 10,26 m lên 37,05 m), số điểm trên xe con giảm từ 1013 điểm xuống còn 35 điểm, tức chỉ còn khoảng 1 phần 29, phù hợp với quy luật suy giảm mật độ theo khoảng cách trên bài giảng (khoảng 1968 điểm ở 0 đến 10 m, 718 ở 10 đến 20 m, 214 ở 20 đến 30 m và 72 ở 30 đến 40 m).

Sau khi xem ảnh đối chiếu và phiếu tự kiểm, đã sửa lại 2 hộp trên CVAT rồi đồng bộ lại: tại s02f00 idx 1 (Bus) dịch tâm x từ 3,443 m về 3,350 m và thu chiều rộng từ 2,800 m về 2,620 m để vẫn bao sát gương phải nhưng bỏ phần thừa ở cạnh trái bị che; tại s02f21 idx 6 (Pedestrian) thu gọn dài và rộng từ 0,900 x 0,900 m về 0,750 x 0,700 m cho ôm sát cụm 144 điểm của người đi bộ. Sau lần đồng bộ cuối, phiếu tự kiểm có 0 trên 97 hộp bị cảnh báo (3 hộp ở xa trên 35 m để trống độ hở mặt đường do xung quanh thưa điểm mặt đường nhưng vẫn khớp ảnh nên giữ nguyên).

Đổi kiểm với bạn có mã số [điền MSSV bạn đổi kiểm]: đối chiếu hai giá trị [điền 2 số đã kiểm] trên bảng A, kết quả khớp hoàn toàn.

## 6. Ý nghĩa của nhãn, cách dùng AI và điều còn chưa chắc

Nhãn 3D đo bằng mét thay vì điểm ảnh vì mô hình cần học vị trí, khoảng cách và kích thước vật lý không đổi theo góc nhìn để dự đoán quỹ đạo và tránh va chạm chính xác trong không gian thực. Vật thưa điểm phải có quy tắc tối thiểu khoảng 15 đến 20 phần trăm thể tích mới vẽ để tránh đưa các hộp đoán mò sai tâm, sai kích thước vào làm nhiễu dữ liệu huấn luyện.

Dùng AI:
Công cụ: Gemini.
Câu hỏi chính: Nhờ giải thích hệ tọa độ dữ liệu, cách đọc các quy tắc gán nhãn, bảng 4.3 phân biệt 5 loại đối tượng và ý nghĩa bốn hiện tượng chất lượng trong tài liệu đề bài.
Cách sử dụng kết quả: Dùng làm tài liệu tra cứu nhanh để tự đọc cảnh, tự kiểm tra hướng đầu xe, bao trọn gương chiếu hậu và đối chiếu số liệu bảng A với phiếu tự kiểm khi viết báo cáo.

Điều còn chưa chắc: một số xe đi xa trên 30 m ở s01f04 (idx 11, 12) và s02f00 (idx 5, 6) chỉ nhìn thấy phần đuôi nên cạnh dài và rộng khuất phía trước ước lượng theo kích thước phổ thông trong bảng 4.3, có thể lệch nhẹ so với kích thước từng mẫu xe cụ thể.
