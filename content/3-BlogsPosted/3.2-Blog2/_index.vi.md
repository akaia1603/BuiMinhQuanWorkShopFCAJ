---
title: "Blog 2"
date: 2026-09-13
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# PHÂN TÍCH CẢM XÚC KHÁCH HÀNG THEO THỜI GIAN THỰC VỚI AWS

Trích xuất case study trên AWS Machine Learning Blog: pipeline phân tích cảm xúc đánh giá khách hàng theo thời gian gần thực và trích xuất ý kiến ở mức thực thể bằng **Amazon Comprehend**, thay thế quy trình xử lý batch mất 2–3 ngày bằng dữ liệu có trong vài phút.

### Các thành phần kiến trúc chính:

- **Thu thập & đệm dữ liệu:** Đánh giá từ website/app được đưa qua **Amazon API Gateway** vào hàng đợi **Amazon SQS** — đóng vai trò buffer, kèm dead-letter queue xử lý tin lỗi.
- **Điều phối:** Hàm **AWS Lambda** kích hoạt state machine **AWS Step Functions** cho từng đánh giá, tách biệt luồng phân tích và tăng độ tin cậy với cơ chế retry.
- **Phân tích cảm xúc toàn phần & theo thực thể:** Step Functions gọi **Amazon Comprehend** (`detect_sentiment`) để lấy cảm xúc tổng thể và `detect_targeted_sentiment` để lấy cảm xúc theo từng thực thể (công ty, sản phẩm, thương hiệu), lưu kết quả vào **Amazon DynamoDB**.
- **Cảnh báo & sự kiện:** Khi cảm xúc tiêu cực hoặc lẫn lộn, **Amazon SNS** gửi email cho đội marketing/CS và **Amazon EventBridge** chuyển sự kiện tới hệ thống downstream.
- **Phân tích & dashboard:** **DynamoDB Streams → Amazon Kinesis Data Streams → Kinesis Data Firehose → Amazon S3**, sau đó **Amazon QuickSight** trực quan hóa kết quả gần thời gian thực mà không cần SQL.

### Lợi ích:

- Có thông tin cảm xúc trong vài phút thay vì nhiều ngày.
- Hoàn toàn serverless — tự mở rộng, không quản lý hạ tầng.
- Không cần kiến thức AI/ML hay NLP vì mọi thứ do **Amazon Comprehend** quản lý.
- Sẵn sàng triển khai qua template **AWS CloudFormation** phía sau mọi ứng dụng hướng khách hàng.

![Kiến trúc phân tích cảm xúc khách hàng theo thời gian thực](/images/3-BlogsPosted/blog2.png)

### Liên kết tham khảo:

- [Bài viết AWS](https://aws.amazon.com/blogs/machine-learning/real-time-analysis-of-customer-sentiment-using-aws/)