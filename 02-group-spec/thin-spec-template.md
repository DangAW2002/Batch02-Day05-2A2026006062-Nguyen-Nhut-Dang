
# Thin SPEC — Trợ Lý AI Tư Vấn & Đặt Lịch Tiêm Chủng (AI Vaccine Assistant)

Thin SPEC không phải PRD đầy đủ. Đây là bản cam kết đủ rõ để sáng Day 06 nhóm build ngay.

## 1. Track, product/app và user

**Track:** HealthTech / Medical Chatbot Assistant
**Product/app thật:** AI Vaccine Assistant (Trợ lý AI tư vấn và Đặt lịch Tiêm chủng FPT Long Châu)
**User cụ thể:**
1.*Khách hàng:* Người có nhu cầu tìm hiểu vaccine, cần tư vấn lịch tiêm và muốn đặt lịch hẹn tiêm nhanh tại trung tâm Long Châu gần nhất.
2.*Dược sĩ / Bác sĩ:* Người tiếp nhận các ca cần tư vấn chuyên sâu, các ca có dấu hiệu cảnh báo y tế/chống chỉ định thông qua hotline hoặc yêu cầu gọi lại (callback).
**Nhóm có phải user thật không? Nếu không, khác ở đâu?**
Nhóm không phải là user thật. Nhóm không có chuyên môn y khoa lâm sàng của bác sĩ/dược sĩ và cũng không trực tiếp trải nghiệm cảm giác sốt ruột khi chờ đợi phản hồi chat hoặc sự bất tiện khi đặt lịch tiêm chủng thủ công.

## 2. Evidence summary

| Evidence                                                                                                                                                                  | Nguồn                                                                            | User/pain nói lên điều gì?                                                                                     | SPEC phải đổi gì?                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dược sĩ trực chat mất 5-10 phút để phản hồi câu hỏi sàng lọc cơ bản do quá tải và quy trình thủ công.                                               | Trải nghiệm thực tế tự dùng app (Self-use) và phỏng vấn sâu Dược sĩ. | Khách hàng cảm thấy nản lòng vì tốc độ phản hồi chậm, dễ bỏ cuộc chat (drop-off).                   | Tích hợp AI tương tác trực tiếp với khách hàng để thu thập hồ sơ và tư vấn tức thì.                                                   |
| Khâu chuyển sang đặt lịch tiêm diễn ra thủ công: Dược sĩ phải check bản đồ, check kho vaccine từng chi nhánh rồi gõ tay giờ trống cho khách chọn. | Trải nghiệm thực tế tự dùng app (Self-use) và phỏng vấn sâu Dược sĩ. | Tỷ lệ đặt lịch thành công thấp do ma sát (friction) cao ở bước chọn chi nhánh và thời gian.         | AI hỗ trợ nhập vị trí/định vị GPS, tự động gợi ý trung tâm Long Châu gần nhất và cho khách chọn lịch hẹn trực quan.                |
| Rủi ro y khoa khi bỏ sót các chống chỉ định nghiêm trọng (như có thai, sốt cao, tiền sử dị ứng vắc-xin).                                                | Hướng dẫn sàng lọc của Bộ Y Tế & Phỏng vấn sâu Dược sĩ.             | Quy trình hỏi đáp thủ công dưới áp lực chat nhiều người dễ dẫn đến sai sót lâm sàng nguy hiểm. | Cài đặt bộ lọc an toàn y khoa cứng (Safety Guardrails) để tự động nhận diện dấu hiệu nguy hiểm và chuyển giao khẩn cấp cho bác sĩ. |

## 3. Pain statement

```text
Khách hàng có nhu cầu tiêm chủng đang gặp khó khăn ở cả 2 khâu: (1) Khai báo thông tin y tế rời rạc và không rõ loại vaccine/lịch tiêm phù hợp với mình, (2) Khâu đặt lịch tiêm (tìm kiếm cơ sở gần nhất, kiểm tra tình trạng thuốc, chọn ngày giờ) diễn ra rườm rà qua chat thủ công với Dược sĩ, dẫn đến tỷ lệ bỏ ngang (drop-off) cao. Dược sĩ trực chat cũng bị quá tải vì phải xử lý các tác vụ hành chính lặp đi lặp lại thay vì tập trung chuyên môn.
Bằng chứng chính là các cuộc hội thoại thực tế cho thấy dược sĩ mất nhiều thời gian tra cứu hệ thống để tìm trung tâm gần nhất còn thuốc cho khách hàng, và khách hàng thường im lặng nếu thời gian chờ phản hồi quá 5 phút.
```

## 4. Build slice

```text
Cho khách hàng truy cập trang tư vấn vắc-xin Long Châu,
prototype sẽ xây dựng một chatbot AI tương tác trực tiếp giúp thu thập hồ sơ y tế (tuổi, giới tính, đối tượng, sức khỏe, mối quan tâm), phân tích dấu hiệu cảnh báo y tế. Nếu phát hiện rủi ro, AI tự động chuyển ca (escalate) sang Dược sĩ/Bác sĩ kèm hotline hoặc form gọi lại. Nếu an toàn, AI đề xuất vaccine + giải thích lịch tiêm phù hợp, sau đó hỗ trợ khách hàng tìm kiếm trung tâm Long Châu gần nhất dựa trên vị trí nhập vào, chọn ngày giờ trống và hoàn tất đặt lịch tiêm chủng, mô phỏng gửi SMS xác nhận và nhắc lịch.
```

## 5. Auto/Aug decision

Chọn một:

- [ ] **Augmentation:** AI gợi ý/draft/phân loại, user quyết cuối.
- [X] **Conditional automation:** AI tự làm trong case hẹp; case mơ hồ/rủi ro chuyển người.
- [ ] **Automation:** AI tự quyết và tự hành động.

**Lý do chọn:** Việc thu thập thông tin, tư vấn vaccine thông thường và đặt lịch tiêm (Happy Path) được tự động hóa hoàn toàn để tối ưu hóa trải nghiệm khách hàng và giảm tải 90% công việc hành chính cho dược sĩ. Tuy nhiên, nếu phát hiện bất kỳ dấu hiệu rủi ro y khoa hoặc trường hợp phức tạp (như phụ nữ có thai, người có tiền sử phản vệ nặng), AI sẽ lập tức dừng quy trình tự động và chuyển sang nhân viên y tế để đảm bảo an toàn tính mạng.
**Human role:** decider / rescuer (Dược sĩ/Bác sĩ lâm sàng tiếp nhận cuộc gọi/ca chuyển giao để tư vấn trực tiếp và chỉ định chuyên môn cuối cùng).

## 6. Four paths

| Path                     | Prototype phải thể hiện gì?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Happy**          | Khách hàng nhắn "Tôi muốn tư vấn vaccine cúm cho con". AI chào hỏi và hỏi thông tin: bé 12 tháng tuổi, khỏe mạnh, giới tính nam. AI đề xuất vaccine cúm phù hợp (Vaxigrip Tetra), giải thích lý do, số mũi tiêm và lịch tiêm. Khi khách hàng đồng ý, AI gợi ý đặt lịch, yêu cầu nhập vị trí. Khách hàng nhập "Quận 7", AI hiển thị danh sách trung tâm Long Châu gần nhất tại Quận 7. Khách chọn Trung tâm A, chọn ngày 05/06/2026 lúc 9:00 sáng. Hệ thống xác nhận thành công và hiển thị giao diện mô phỏng tin nhắn SMS xác nhận lịch hẹn đã được gửi. |
| **Low-confidence** | Khách hàng trả lời mơ hồ hoặc hỏi câu hỏi phức tạp nằm ngoài cơ sở dữ liệu (ví dụ: "Con tôi đang uống thuốc điều trị viêm da cơ địa thì tiêm vaccine cúm được không?"). AI phát hiện độ tự tin thấp, giải thích rằng đây là trường hợp cần chuyên môn sâu và tự động hiển thị form đăng ký gọi lại (nhập Số điện thoại + Tên) để Dược sĩ liên hệ tư vấn trực tiếp.                                                                                                                                                                                                |
| **Failure**        | Khách hàng khai báo các triệu chứng khẩn cấp hoặc chống chỉ định y tế nghiêm trọng (ví dụ: "Bé đang sốt 39.2 độ", "Có thai được 3 tháng và muốn tiêm sởi", hoặc "Từng bị sốc phản vệ ở mũi tiêm trước"). Hệ thống nhận diện từ khóa nguy hiểm, ngay lập tức dừng luồng chat tự động, hiển thị cảnh báo đỏ nổi bật yêu cầu khách hàng không tự ý tiêm chủng và hiển thị số Hotline tư vấn khẩn cấp hoặc nút tạo cuộc gọi khẩn cấp từ Bác sĩ.                                                                                                                |
| **Correction**     | Trong quá trình đặt lịch, sau khi đã hiển thị danh sách địa điểm, khách hàng muốn thay đổi thông tin (ví dụ: đổi từ Quận 7 sang Quận 1, hoặc đã chọn 9:00 sáng nhưng muốn đổi sang 3h chiều). AI linh hoạt cập nhật thông tin vị trí mới, tìm kiếm lại chi nhánh tương ứng và cập nhật lịch hẹn chính xác theo yêu cầu mới của khách hàng mà không bắt người dùng nhập lại từ đầu.                                                                                                                                                                                          |

## 7. Failure mode nguy hiểm nhất

```text
Nếu user khai báo tình trạng chống chỉ định nghiêm trọng (như đang mang thai) nhưng sử dụng từ lóng hoặc cách diễn đạt mơ hồ (ví dụ: "đang nuôi em bé trong bụng" hoặc "chuẩn bị làm mẹ"),
AI có thể không nhận diện được và tiếp tục đề xuất loại vaccine sống giảm độc lực (chống chỉ định cho phụ nữ mang thai),
hậu quả là gây nguy hiểm nghiêm trọng đến sức khỏe của thai nhi và người mẹ.
Prototype sẽ xử lý bằng cách: (1) Thiết lập bộ lọc từ khóa/ngữ nghĩa mở rộng (Semantic Safety Guardrails) chuyên biệt cho các chống chỉ định y khoa lớn trước khi chuyển tiếp thông tin cho bộ máy đề xuất, (2) Luôn hiển thị Tuyên bố từ chối trách nhiệm y khoa (Medical Disclaimer) rõ ràng ở chân trang và trước khi đặt lịch, khẳng định đề xuất chỉ mang tính tham khảo và khách hàng sẽ được bác sĩ sàng lọc trực tiếp tại phòng tiêm trước khi thực hiện.
Owner kiểm thử path này là [Thành viên D].
```

## 8. Owner plan cho sáng Day 06

| Thành viên   | Việc phụ trách                | Bằng chứng cần có trong repo                                                                                                                      |
| -------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Thành viên A | Khảo sát & dữ liệu           | File JSON danh mục vaccine (chỉ định, lịch tiêm, chống chỉ định) và danh sách trung tâm Long Châu mô phỏng.                           |
| Thành viên B | Thiết kế prompt & AI Logic     | Hệ thống Prompt của AI Vaccine Assistant và sơ đồ ra quyết định sàng lọc y khoa.                                                          |
| Thành viên C | Phát triển Prototype           | Mã nguồn ứng dụng (React/Vite hoặc Node.js) bao gồm giao diện chat tư vấn, bản đồ chọn trung tâm Long Châu và màn hình đặt lịch. |
| Thành viên D | Kiểm thử & Kịch bản an toàn | Tài liệu bộ dữ liệu test (test suite) chứa các câu hỏi kiểm thử cho cả 4 paths, đặc biệt là các case lách luật y tế.              |
| Thành viên E | Demo & Repo                      | Kịch bản demo, video quay màn hình chạy thử nghiệm và cấu trúc thư mục repo chuẩn hóa.                                                  |
