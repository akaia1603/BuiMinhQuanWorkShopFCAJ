---
title: "Blog 3"
date: 2026-09-15
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# TRÍCH XUẤT CẢM XÚC CHI TIẾT TRONG VĂN BẢN VỚI AMAZON COMPREHEND TARGETED SENTIMENT

Trích xuất từ bài AWS Machine Learning Blog công bố tính năng **Amazon Comprehend Targeted Sentiment** — vượt xa phân tích cảm xúc toàn văn bản để xác định cảm xúc dành riêng cho từng thực thể (người, sản phẩm, thương hiệu, thuộc tính) được nhắc đến trong nội dung.

### Các khái niệm chính:

- **Amazon Comprehend** là dịch vụ NLP được quản lý hoàn toàn, không cần kiến thức ML, mở rộng được với khối lượng dữ liệu lớn và cung cấp API đơn giản cho entities, key phrases, sentiment, document classification và language.
- **Cảm xúc toàn phần (truyền thống):** trả về một nhãn tổng thể — `positive`, `negative`, `neutral` hoặc `mixed` — cho toàn văn bản. Muốn biết cảm xúc theo thực thể trước đây phải dùng cách vòng vo như chia nhỏ văn bản thành các khối logic.
- **Targeted Sentiment:** xác định các **nhóm co-reference của mentions** cùng trỏ về một thực thể thực, trả về cảm xúc cho từng mention và từng nhóm thực thể, đồng thời phân loại thực thể theo danh sách thực thể định sẵn.
- **Kết quả chi tiết:** mỗi kết quả gồm `Entities`, `Mentions`, `DescriptiveMentionIndex`, `GroupScore`, `Text`, `Type`, `Score`, `MentionSentiment`, `Sentiment`, `SentimentScore`, cùng `BeginOffset`/`EndOffset` để định vị mention trong văn bản.

### Các trường hợp sử dụng điển hình:

- Đội marketing theo dõi cảm xúc đối với thương hiệu, chiến dịch hoặc đợt ra mắt tính năng trên mạng xã hội theo thời gian.
- Shop thương mại điện tử hiểu rõ thuộc tính sản phẩm nào được khách hàng đánh giá tốt/xấu nhất.
- Trung tâm chăm sóc khách hàng khai thác bản ghi cuộc gọi để phát hiện vấn đề leo thang và giám sát trải nghiệm; nhà hàng, khách sạn biến thang điểm thành mô tả trải nghiệm tốt/xấu.

### Cách triển khai:

Tạo **Analysis job** trong console Amazon Comprehend với *Analysis type = Targeted sentiment*, trỏ tới dữ liệu văn bản trong **Amazon S3** và đọc trực tiếp kết quả JSON — các nhóm thực thể, cảm xúc của từng thực thể và điểm tin cậy — ngay từ API.

![Amazon Comprehend Targeted Sentiment](/images/3-BlogsPosted/blog3.png)

### Liên kết tham khảo:

- [Bài viết AWS](https://aws.amazon.com/blogs/machine-learning/extract-granular-sentiment-in-text-with-amazon-comprehend-targeted-sentiment/)