# Báo cáo Day 13, Phạm Công Bằng, 2A202603134

## 1. Kết luận trước

Mã số sinh viên 2A202603134, mã nhiệm vụ D13-2A202603134, gồm 10 khung hình: s01f04, s01f55, s02f00, s02f21, s03f07, s03f47, s04f19, s04f47, s05f12, s05f42. Máy chạy Windows, mở CVAT trên trình duyệt Chrome bản 2.74.1, ngồi đổi kiểm cùng bạn mã số 2A202603054.

Bài này mình gán nhãn tổng cộng 97 hộp trên 10 khung hình. Khung hình ít nhất là s05f42 với 6 hộp vì xe phía sau ở xa bị che và ít điểm nên bỏ qua. Chạy tự kiểm không còn cảnh báo nào với 0 trên 97 hộp bị cờ. Các vật trong khoảng 25 m mình tự tin về loại nhãn, hướng đầu xe và đáy chạm đường; các xe xa trên 30 m bị khuất nửa trước thì vẫn hơi phân vân về chiều dài.

Trên CVAT, giữ chuột trái để xoay góc nhìn 3D lên thẳng trên xuống, chuột phải để dời vùng nhìn, cuộn chuột để phóng to thu nhỏ và nháy đúp chỗ trống để về góc ban đầu. Khi vẽ thì chọn công cụ hộp đơn, chọn nhãn rồi nháy đúp vào cụm điểm, chỉnh vị trí và góc quay ở khung trên, hạ đáy chạm mặt đường ở khung cạnh và trước, bật mũi tên hướng căn vạch đỏ về đầu xe rồi lưu và đồng bộ đối chiếu lên ảnh camera.

## 2. Đọc frame

| Frame | Phía trước xe ở cạnh nào của ảnh nhìn từ trên xuống; +x, +y chỉ về đâu | Mặt đường | Vật xa nhất đọc được | Loại vật thấy | Vật phía sau và hai bên | Cụm chưa đọc được |
|---|---|---|---|---|---|---|
| s01f04 | Phía trước ở cạnh trên khớp góc cam01; +x hướng sang trái, +y hướng xuống dưới ra sau | Khá phẳng, cao độ quanh âm 1,67 m, vỉa hè hai bên nhô cao hơn nhẹ | Khoảng 45 đến 50 m dọc đường chính | Car, Truck ở làn ngược chiều bên trái, Bus ở ngã tư phía xa, Cyclist ngay vạch qua đường phía sau | Phía sau trái khoảng 6,7 m có xe con xanh; phía sau khoảng 16 m và 23 m có xe con đi tới; bên trái có xe tải thùng trắng | Vài cụm điểm rời ven hàng cây bên phải và ngoài ngã tư phía sau phải trên 35 m |
| s01f55 | Phía trước ở cạnh trên khớp góc cam01; +x hướng sang trái, +y hướng xuống dưới ra sau | Phẳng, hơi dốc nhẹ lên phía trước, cao độ quanh âm 1,76 m, lề phải cao hơn lòng đường | Khoảng 40 đến 45 m ở hàng xe phía trước | Car nối đuôi nhau phía trước, Bus hoặc xe van cao ở xa phía trước, Pedestrian trên vỉa hè phải | Phía sau khoảng 7 m có hai xe con trắng; bên phải trên vỉa hè có dãy xe đạp dựng không có người | Mấy cụm điểm lẫn giữa tán cây, cột đèn và hàng xe đạp dựng trên vỉa hè phải |

Xem ảnh camera giúp biết màu xe, kiểu dáng phân biệt xe tải thùng với xe con, nhận ra đầu hay đuôi xe, thấy dãy xe đạp dựng không người trên vỉa hè phải ở s01f55 để không gán nhầm, cùng vạch kẻ đường và biển báo. LiDAR cho biết tọa độ và khoảng cách bằng mét, kích thước dài rộng cao thật, độ cao mặt đường và góc nhìn 360 độ cả chỗ camera bị khuất.

| Frame | Phía trước ở cạnh nào của ảnh nhìn từ trên xuống | Điều lạ |
|---|---|---|
| s02f00 | Cạnh trên theo hướng cam01 | Xe buýt đỏ sát bên trái chắn tạo vùng trống phía sau trái nó |
| s02f21 | Cạnh trên theo hướng cam01 | Có người đi xe tay ga sát lề phải và hàng rào hai bên tạo vệt điểm thẳng dài |
| s03f07 | Cạnh trên theo hướng cam01 | Tường quây công trình sát hai bên che khuất ngoài lề, có một điểm lẻ rơi sâu dưới đất ở cao độ âm 4,6 m |
| s03f47 | Cạnh trên theo hướng cam01 | Có xe buýt đi ngang giao lộ ở xa phía trước và người đi xe đạp sau rào bên phải |
| s04f19 | Cạnh trên theo hướng cam01 | Xe đông cả trước lẫn sau, có xe máy chạy ngay chính giữa phía sau |
| s04f47 | Cạnh trên theo hướng cam01 | Hai xe phía trước bên phải đi sát nhau nên phần hông xe ngoài bị che bớt |
| s05f12 | Cạnh trên theo hướng cam01 | Ngã tư rộng có nhiều hướng xe cắt ngang và rẽ qua giao lộ |
| s05f42 | Cạnh trên theo hướng cam01 | Có nhiều điểm nằm thấp hơn hẳn mặt đường về phía bên trái |

## 3. Ba cuboid có hướng dẫn

| Vật | Frame, idx | Class | Mũi tên yaw đúng hướng | Đáy chạm đường | Đã kiểm 3 góc nhìn và ảnh | Kích thước trong bảng 4.3 |
|---|---|---|---|---|---|---|
| Xe con gần | s01f04, idx 2 | Car | Có, góc 265,0 độ hướng về đầu xe | Có, độ hở 0,01 m | Có, đã đối chiếu cam05 và cam09 | Dài 4,49 m, rộng 2,09 m gồm gương, cao 1,50 m |
| Xe tải | s01f04, idx 4 | Truck | Có, góc 89,5 độ hướng về đầu xe | Có, độ hở 0,07 m | Có, đã đối chiếu cam05 và cam06 | Dài 5,75 m, rộng 2,25 m, cao 2,97 m |
| Xe hai bánh | s01f04, idx 7 | Cyclist | Có, góc 270,0 độ theo mũi xe | Có, độ hở 0,01 m | Có, đã đối chiếu cam08 và cam09 | Dài 1,81 m, rộng 0,86 m, cao 1,67 m |

Sau khi đối chiếu lại với tài liệu hướng dẫn, mình luôn bật mũi tên hướng để tránh lộn đầu đuôi, kéo rộng hộp để ôm cả hai gương chiếu hậu và kiểm hai khung cạnh, trước để đáy chạm đúng mặt đường.

Những chỗ bỏ qua không vẽ vì thiếu cơ sở gồm mấy cụm điểm rời ven tán cây và ngoài ngã tư trên 35 m ở s01f04, hàng xe đạp dựng không người trên vỉa hè phải ở s01f55, và xe buýt phía sau trên 32 m ở s05f42 bị xe trước với cây che gần hết chỉ còn ít điểm rời.

## 4. Bốn hiện tượng chất lượng

| Hiện tượng | Frame, ảnh, nguồn | Nguyên nhân giả thuyết | Thấy gì trên point cloud | Hệ quả khi gán theo quy chuẩn |
|---|---|---|---|---|
| 1. Bóng che | s02f00, t4-1-bong-che.jpg, frame bản thân | Giả thuyết do thân xe buýt đỏ cao và dài ở khoảng 9,14 m chắn tia quét LiDAR | Phía sau trái xe buýt tạo vùng trống không có điểm trong khi hai bên vẫn dày điểm | Vùng trống là chỗ chưa quan sát được; nếu có vật bị che một phần phía sau cần bật thuộc tính bị che khuất và bao cả phần suy luận được |
| 2. Thưa ở xa | s02f00, t4-2-thua-o-xa.png, frame bản thân | Giả thuyết do các tia quét tách xa nhau dần theo khoảng cách trên 40 m | Xe ở 41,10 m chỉ còn 43 điểm và xe ở 45,23 m chỉ còn 25 điểm ở phần đuôi | Chỉ vẽ khi thấy khoảng 15 đến 20 phần trăm thể tích và nhìn rõ qua ảnh máy ảnh, còn thưa quá không đủ cơ sở thì bỏ qua |
| 3. Phản xạ thấp | s03f07, t4-3-phan-xa-thap.jpg, frame bản thân | Giả thuyết do sơn xe tối màu và kính sẫm hấp thụ hoặc phản xạ lệch tia laser | Xe đen ở 7,93 m chỉ thu được 1466 điểm, ít hơn xe đỏ 7,03 m ở s03f47 có 2053 điểm hay xe trắng 7,26 m ở s01f55 có 1813 điểm | Không thu hẹp hay nới lỏng hộp theo phần thiếu điểm mà dựa thêm ảnh máy ảnh và mép thân dưới để giữ đúng kích thước thật |
| 4. Điểm lạ | s05f42, t4-4-diem-la.jpg, frame bản thân | Giả thuyết do tia laser phản xạ nhiều lần qua kính, thân xe bóng hoặc sai số cảm biến | Có 1881 điểm có cao độ thấp hơn âm 2,6 m, trung vị âm 2,94 m ở phía bên trái, ngoài ra ở s03f07 cũng có điểm lẻ ở âm 4,6 m | Không gán thành vật thể cho các điểm rơi dưới mặt đường hay lơ lửng |

## 5. Số từ cuboid của tôi

| Cuboid | z (m) | h (m) | z đáy (m) | dist_m (m) | r (m) | yaw_deg (độ) | Nhận xét |
|---|---|---|---|---|---|---|---|
| s01f04, idx 1, Car | -1.067 | 1.509 | -1.821 | 11.61 | 11.66 | 266.5 | Chạm đường |
| s02f00, idx 1, Bus | -0.142 | 3.463 | -1.873 | 9.14 | 9.14 | 270.0 | Chạm đường |
| s01f55, idx 9, Pedestrian | -0.537 | 1.587 | -1.331 | 21.48 | 21.49 | 270.0 | Chạm mặt vỉa hè nâng cao |

Hộp gần nhất là xe con ở s03f07 idx 1 với dist_m bằng 3,51 m và khoảng cách 3D r bằng 3,66 m. Hộp xa nhất là xe con ở s02f00 idx 6 với dist_m bằng 45,23 m và r bằng 45,25 m.

So với bảng 4.3, người đi bộ ở s02f21 idx 6 có ba chiều nằm gọn trong mức chuẩn; xe con ở s01f04 idx 2 có chiều dài và chiều cao đúng chuẩn, riêng chiều rộng là 2,087 m vượt mức 1,90 m nhẹ do phải bao cả hai gương chiếu hậu.

Xe chạy cùng chiều phía trước ở s03f07 idx 3 có yaw_deg bằng 274,5 độ, gần mốc 270 độ; xe ngược chiều ở s01f04 idx 3 có yaw_deg bằng 92,5 độ, gần mốc 90 độ.

| Cuboid | dist_m (m) | Số điểm |
|---|---:|---:|
| s03f07, idx 1, Car | 3.51 | 2151 |
| s01f55, idx 3, Car | 10.26 | 1013 |
| s01f04, idx 9, Car | 23.29 | 350 |
| s01f04, idx 12, Car | 37.05 | 35 |

Khi khoảng cách tăng từ 10,26 m lên 37,05 m, số điểm trên xe con giảm từ 1013 xuống còn 35 điểm, khớp với xu hướng giảm điểm theo khoảng cách trong bài giảng từ 1968 điểm ở 0 đến 10 m xuống 72 điểm ở 30 đến 40 m.

Sau khi xem ảnh đối chiếu và tự kiểm, mình sửa lại 2 hộp trên CVAT rồi đồng bộ lại. Hộp Bus ở s02f00 idx 1 được dời nhẹ tâm và thu hẹp bề ngang cho sát gương phải, bỏ phần trống bên trái. Hộp Pedestrian ở s02f21 idx 6 được thu nhỏ lại cho ôm sát cụm điểm người đi bộ. Sau khi sửa, cả 97 hộp đều không có cảnh báo; 3 hộp ở xa trên 35 m để trống độ hở mặt đường do xung quanh ít điểm đất nhưng khớp ảnh nên mình giữ nguyên.

Mình đổi kiểm trực tiếp trên màn hình với bạn mã số 2A202603054, kiểm tra 2 giá trị trên bảng A là dist_m của s03f07 idx 1 bằng 3,51 m và yaw_deg của s03f07 idx 3 bằng 274,5 độ, cả hai đều khớp.

## 6. Ý nghĩa của nhãn, cách dùng AI và điều còn chưa chắc

Nhãn 3D dùng đơn vị mét thay vì điểm ảnh vì mô hình cần học khoảng cách và kích thước thật ngoài thực tế không đổi theo góc nhìn để dự đoán đường đi và tránh va chạm. Vật thưa điểm phải thấy ít nhất khoảng 15 đến 20 phần trăm thể tích mới vẽ để tránh tạo hộp đoán sai tâm và kích thước làm nhiễu lúc huấn luyện mô hình.

Khi làm bài, mình dùng Gemini để hỏi giải thích hệ tọa độ của dữ liệu, quy ước hướng đầu xe trong tài liệu hướng dẫn, bảng 4.3 phân biệt 5 loại vật thể và ý nghĩa bốn hiện tượng chất lượng rồi tự áp dụng vào lúc gán nhãn và soát lại số liệu.

Điều còn chưa chắc là mấy xe ở xa trên 30 m tại s01f04 idx 11, idx 12 và s02f00 idx 5, idx 6 chỉ thấy phần đuôi nên chiều dài phía trước phải ước lượng theo cỡ xe phổ thông trong bảng 4.3.
