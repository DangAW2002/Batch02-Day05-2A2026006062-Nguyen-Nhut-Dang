
# Evidence Pack — AI Vaccine Assistant (Tư vấn & Đặt lịch Tiêm chủng Long Châu)

Nộp kèm thin SPEC cuối Day 05.

## 1. Nhóm và track

**Tên nhóm:** Nhóm 02
**Track:** HealthTech / Medical Chatbot Assistant
**Product/app đã chọn:** AI Vaccine Assistant (Trợ lý AI tư vấn và Đặt lịch Tiêm chủng FPT Long Châu)
**Build slice đang nghĩ:** Chatbot AI tương tác trực tiếp với khách hàng để thu thập hồ sơ y tế (tuổi, giới tính, sức khỏe hiện tại, tiền sử dị ứng, nhu cầu tiêm chủng), phân loại an toàn y khoa. Nếu phát hiện rủi ro, AI tự động kích hoạt chuyển giao (escalate) sang Dược sĩ/Bác sĩ kèm hotline hoặc form gọi lại. Nếu an toàn, AI đề xuất vắc-xin phù hợp + giải thích lịch tiêm, sau đó hướng dẫn khách hàng định vị tìm trung tâm Long Châu gần nhất, chọn ngày/giờ và hoàn tất đặt lịch hẹn trực tiếp (gửi SMS/Email xác nhận và nhắc lịch).

## 2. Self-use evidence

Nhóm tự đóng vai khách hàng nhắn tin cho fanpage tư vấn và đặt lịch tiêm chủng thực tế để kiểm tra quy trình:

| Observation                                                                                                                                                                                                                                                                                               | Screenshot/link                                                                                                                                 | Path liên quan          | Điều học được                                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gửi câu hỏi "Bé 9 tháng tiêm được cúm chưa?". Dược sĩ trực chat mất 5-10 phút để phản hồi câu đầu tiên hỏi về số tháng tuổi chi tiết, cân nặng, tình trạng sức khỏe của bé.                                                                                        | [Mẫu hội thoại 01](file:///c:/Users/HungNguyen/Documents/AITHUCCHIEN/Batch02-Day05-AI-Product-Labs/02-group-spec/evidence-logs/chat_log_01.png) | Happy Path               | Quy trình tư vấn thủ công bị trễ do tốc độ phản hồi của con người, khách hàng phải chờ lâu dẫn đến trải nghiệm kém.                                                              |
| Sau khi tư vấn xong vaccine cúm, khách hàng đồng ý tiêm và hỏi "Đặt lịch tiêm ở đâu gần quận 7?". Dược sĩ phải đi tìm thủ công danh sách chi nhánh, check tình trạng vaccine còn/hết trên hệ thống nội bộ, rồi gõ tay từng khung giờ trống để khách chọn. | [Mẫu hội thoại 02](file:///c:/Users/HungNguyen/Documents/AITHUCCHIEN/Batch02-Day05-AI-Product-Labs/02-group-spec/evidence-logs/chat_log_02.png) | Low-confidence / Failure | Khâu chuyển đổi từ "tư vấn" sang "đặt lịch" rất thủ công và dễ bị gãy (drop-off). Dược sĩ mất quá nhiều thời gian xử lý thủ tục hành chính thay vì tập trung chuyên môn. |

## 3. User / review / social evidence

Nguồn thu thập từ các hội nhóm phụ huynh và khảo sát phỏng vấn nhanh dược sĩ trực chat:

| Quote / review / observation                                                                                                                                                                                                                                  | Nguồn                                 | User là ai?                                   | Pain/failure mode                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "Nhiều khi nhắn tin hỏi vaccine cho con xong, muốn đặt lịch luôn mà nhân viên cứ hỏi đi hỏi lại địa chỉ rồi bảo để check xem chi nhánh đó còn thuốc không. Chờ lâu quá mình tắt chat đi chỗ khác tiêm luôn cho nhanh." | Hội làm cha mẹ trên Facebook       | Phụ huynh cần tư vấn và đặt lịch tiêm | Tỷ lệ bỏ ngang (drop-off) cao do quy trình tìm kiếm địa điểm và đặt lịch qua chat quá rườm rà, thiếu tính năng định vị tự động. |
| "Một ca trực vừa phải tư vấn y tế vừa phải mở tab khác để tra bản đồ xem chi nhánh nào gần khách nhất, rồi tra cứu tồn kho vaccine. Rất dễ nhầm lẫn thông tin giữa các chi nhánh hoặc quên nhắc lịch hẹn cho khách."    | Phỏng vấn sâu Dược sĩ trực chat | Dược sĩ tư vấn online                     | Quá tải do phải kiêm nhiệm tác vụ hành chính (tra cứu trung tâm, đặt lịch, nhắc hẹn), dẫn đến giảm năng suất và dễ sai sót.       |

## 4. Competitor / analog evidence

| App / mô hình tham khảo                                | Họ xử lý task này thế nào?                                                                                                                                       | Pattern học được                                                                                                                                          | Có áp dụng trong 1 ngày không?                                                                                                          |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **ADA Health** (Symptom Checker)                    | Sử dụng chatbot hội thoại thông minh hỏi từng bước về sức khỏe, phân tích rủi ro rõ ràng trước khi đưa ra kết luận hoặc kết nối chuyên gia. | - Thu thập thông tin y tế từng bước một cách tự nhiên.**`<br>`**- Phân loại mức độ rủi ro (tự tư vấn hay chuyển bác sĩ).        | **Có:** Áp dụng luồng thu thập hồ sơ khách hàng và phân tích dấu hiệu cần bác sĩ tư vấn (sàng lọc trước tiêm). |
| **Hệ thống đặt xe/đồ ăn (Grab, ShopeeFood)** | Sử dụng GPS/định vị địa lý hoặc nhập địa chỉ để gợi ý ngay các cửa hàng gần nhất kèm theo khoảng cách.                                        | Tích hợp tính năng định vị và tìm kiếm cơ sở gần nhất trực tiếp trong luồng trải nghiệm của người dùng để giảm ma sát đặt lịch. | **Có:** Tích hợp bộ lọc tìm kiếm trung tâm tiêm chủng Long Châu gần nhất dựa trên vị trí người dùng nhập vào.    |

## 5. Evidence -> Insight

```text
Evidence nổi bật nhất:
Quy trình tư vấn tiêm chủng thực tế thường bị kéo dài và đứt gãy ở hai điểm: một là khâu hỏi đáp sàng lọc sức khỏe ban đầu bị chậm, hai là khâu tra cứu trung tâm gần nhất để đặt lịch tiêm quá thủ công, khiến khách hàng dễ nản lòng và bỏ ngang cuộc chat.

Insight:
Khách hàng cần một hành trình khép kín, nhanh chóng từ tư vấn sang đặt lịch. Họ muốn được phản hồi tức thì về loại vắc-xin phù hợp và muốn việc chọn địa điểm tiêm, thời gian tiêm diễn ra mượt mà ngay trong cửa sổ chat, thay vì phải chờ dược sĩ tra cứu hệ thống thủ công.

Opportunity:
Xây dựng AI Vaccine Assistant tương tác trực tiếp với khách hàng để tự động hóa toàn bộ luồng tư vấn và đặt lịch: thu thập thông tin sàng lọc, phân tích tính an toàn, gợi ý vaccine, định vị trung tâm Long Châu gần nhất, đặt lịch hẹn và gửi tin nhắn xác nhận. Đồng thời, kiểm soát rủi ro y khoa bằng cách tự động chuyển ca cho Dược sĩ/Bác sĩ khi phát hiện dấu hiệu chống chỉ định hoặc bất thường.
```

## 6. Evidence đổi SPEC như thế nào?

- [X] Đổi user chính.
- [X] Đổi pain statement.
- [X] Đổi build slice.
- [X] Đổi Auto/Aug decision.
- [X] Đổi 4 paths.
- [X] Đổi failure mode.
- [ ] Đổi owner/test plan.

Ghi rõ 1-2 thay đổi quan trọng:

```text
Trước evidence, nhóm định:
Xây dựng AI dưới dạng Data Gathering Agent chỉ để thu thập thông tin y khoa ban đầu và hiển thị tóm tắt trên màn hình của Dược sĩ (Dược sĩ vẫn là người chat chính với khách hàng).

Sau evidence, nhóm đổi thành:
AI Vaccine Assistant sẽ chat trực tiếp với khách hàng (Client-facing Agent), tự động hoàn thành từ khâu sàng lọc, tư vấn đề xuất vaccine đến khâu định vị trung tâm Long Châu gần nhất và hoàn tất lịch hẹn đặt tiêm chủng (Happy Path). AI chỉ chuyển giao cho Dược sĩ/Bác sĩ trong trường hợp phát hiện dấu hiệu cảnh báo y tế nguy hiểm (Failure Path) hoặc khách hàng cần hỗ trợ chuyên sâu (Low-confidence Path).

Lý do:
Tối ưu hóa trải nghiệm khách hàng, giảm thiểu tỷ lệ rớt đơn (drop-off) khi chuyển giao giữa các bước, giải phóng hoàn toàn thời gian trực chat của dược sĩ đối với các ca tiêm chủng thông thường, trong khi vẫn đảm bảo an toàn y khoa tối đa thông qua cơ chế lọc cảnh báo và chuyển giao thông minh.
```
