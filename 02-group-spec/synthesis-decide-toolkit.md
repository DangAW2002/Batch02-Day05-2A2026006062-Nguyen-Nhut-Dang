
# Toolkit — Từ Evidence Đến Build Slice

Dùng sau khi nhóm đã có evidence. Mục tiêu là chốt một build slice đủ nhỏ cho Day 06.

## 1. Gom evidence thành cụm

Gom theo **workflow/pain**, không gom theo tên feature.

-**Cụm 1: Quy trình hỏi đáp sàng lọc sức khỏe ban đầu bị chậm và rời rạc** (Khách hàng không biết thông tin nào cần cung cấp, Dược sĩ mất nhiều lượt chat lặt vặt kéo dài AHT).
-**Cụm 2: Khâu chuyển sang đặt lịch tiêm dễ bị đứt gãy (drop-off)** (Khách hàng phải tự tìm địa chỉ, Dược sĩ tra cứu tồn kho vaccine và chi nhánh trống thủ công).
-**Cụm 3: Nguy cơ bỏ sót các chống chỉ định lâm sàng nghiêm trọng** (Dược sĩ quá tải dễ quên hỏi dị ứng, sốt hoặc mang thai trước khi tư vấn vaccine sống).

## 2. Viết insight

Form:

```text
Khách hàng cần tư vấn tiêm chủng không chỉ cần biết thông tin cơ bản về loại vắc-xin.
Họ thật ra cần một hành trình liền mạch, an toàn từ khâu sàng lọc y khoa đến lúc chốt được lịch hẹn tiêm chủng tại cơ sở gần nhất mà không gặp ma sát thời gian,
vì các cuộc hội thoại thực tế thường bị kéo dài, đứt gãy ở khâu hỏi đáp sàng lọc sức khỏe và khâu tra cứu cơ sở tiêm chủng thủ công, dẫn đến tỷ lệ drop-off rất cao.
```

## 3. Viết opportunity

Form:

```text
Cơ hội là dùng AI để tự động hóa toàn bộ cuộc trò chuyện thu thập hồ sơ y tế, tư vấn vaccine phù hợp và đặt lịch hẹn tiêm chủng tại trung tâm gần nhất (Happy Path),
giúp khách hàng hoàn tất đặt lịch tiêm nhanh chóng chỉ trong vài phút trò chuyện,
trong khi vẫn kiểm soát rủi ro y khoa bằng cách nhận diện dấu hiệu nguy hiểm/chống chỉ định để lập tức chuyển giao cuộc gọi/yêu cầu gọi lại cho Dược sĩ/Bác sĩ.
```

## 4. Chọn build slice

Build slice tốt phải qua 5 câu hỏi:

| Câu hỏi               | Đạt khi                                             | Hiện trạng của nhóm                                                                                                                         |
| ----------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| User cụ thể chưa?    | Nói được ai dùng, trong bối cảnh nào.         | **Đạt:** Khách hàng cần tiêm vaccine Long Châu muốn đặt lịch nhanh + Dược sĩ/Bác sĩ tiếp nhận ca chuyển giao.          |
| Task đủ hẹp chưa?   | Demo được trong 3-5 phút.                         | **Đạt:** Chatbot UI tương tác từ hỏi thông tin -> đề xuất -> định vị đặt lịch -> xác nhận SMS trong 3 phút.           |
| AI decision rõ chưa?  | AI gợi ý/tự làm một việc cụ thể.              | **Đạt:** AI tự động gợi ý vaccine phù hợp và hiển thị trung tâm gần nhất. Tự động chuyển ca khi phát hiện rủi ro.   |
| Failure path rõ chưa? | Có một case AI không chắc hoặc sai để test.    | **Đạt:** Khách khai báo chống chỉ định (có thai/sốt cao) -> AI chặn tư vấn, hiển thị cảnh báo đỏ và chuyển bác sĩ. |
| Có evidence không?    | Có bằng chứng từ self-use/review/user/competitor. | **Đạt:** Có dữ liệu từ trải nghiệm chat thực tế và phỏng vấn trực tiếp Dược sĩ trực chat của Long Châu.              |

## 5. Quyết định: giữ, giảm scope, hay đổi hướng?

| Tình huống          | Quyết định                                    | Áp dụng vào dự án                                                                                                                                                          |
| --------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ý tưởng quá rộng | Giữ domain, cắt xuống một flow.              | **Áp dụng:** Giữ nguyên domain tư vấn + đặt lịch, tập trung hoàn thiện 1 flow Happy Path trọn vẹn và 1 flow Critical Escalation (chuyển giao khẩn cấp). |
| Rủi ro y khoa cao    | Chọn augmentation hoặc conditional automation. | **Áp dụng:** Chọn **Conditional Automation** - AI tự động xử lý ca thường, lập tức chuyển người thật khi gặp dấu hiệu bệnh lý nguy hiểm.      |

## 6. Câu chốt cuối

Điền câu này trước khi rời lớp:

```text
Dựa trên bằng chứng thực tế cho thấy quy trình sàng lọc và đặt lịch tiêm chủng thủ công rất mất thời gian, dễ gây nản lòng cho khách hàng và tăng nguy cơ bỏ sót chống chỉ định lâm sàng,
nhóm sẽ build prototype AI Vaccine Assistant tương tác trực tiếp với khách hàng để tư vấn và đặt lịch tiêm chủng nhanh tại chi nhánh Long Châu gần nhất,
cho đối tượng khách hàng có nhu cầu tiêm chủng vaccine tự nguyện,
để giải quyết nỗi đau thời gian phản hồi lâu (AHT) và quy trình chọn địa điểm/khung giờ tiêm rườm rà qua chat,
bằng cách AI tự động hóa hoàn toàn cuộc hội thoại từ sàng lọc sức khỏe, đề xuất vaccine an toàn đến định vị chi nhánh và xác nhận đặt lịch hẹn,
và sẽ test failure path khách hàng khai báo mang thai hoặc sốt cao để xem AI có chặn tư vấn tự động và kích hoạt chuyển giao khẩn cấp ngay lập tức hay không.
```

## 7. Backlog

Những thứ **không build trong Day 06**:

- Tích hợp cổng thanh toán online để khách hàng trả tiền mua/giữ vắc-xin trước.
- Đồng bộ lịch trực thực tế theo thời gian thực của bác sĩ tại từng trung tâm Long Châu cụ thể.
- Hệ thống tổng đài tự động gọi điện/nhắn tin SMS/Zalo nhắc lịch tiêm thực tế (Voice bot & SMS Gateway thực).
