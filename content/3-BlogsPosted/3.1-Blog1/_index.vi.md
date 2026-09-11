---
title: "Blog 1"
date: 2026-09-12
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# GIỚI THIỆU GUARDRAILS TRONG AMAZON BEDROCK KNOWLEDGE BASES

Trích xuất case study kiến trúc RAG Chatbot cho Enterprise trên AWS Machine Learning Blog. Giải pháp giải quyết trọn vẹn bài toán tra cứu dữ liệu nội bộ quy mô lớn với hạ tầng Serverless hoàn toàn.

Hệ thống được thiết kế hoàn toàn theo tư duy Serverless với 3 thành phần trọng yếu:

### Thành phần kiến trúc chính:

- **Tự động hóa Ingestion & Vector DB:** Dữ liệu thô từ Amazon S3 được tự động phân tách, biến đổi thành vector qua Amazon Bedrock Titan Embeddings và lưu trữ tại Amazon OpenSearch Serverless.
- **Luồng xử lý trung tâm:** Knowledge Bases for Amazon Bedrock đóng vai trò truy xuất ngữ cảnh và điều phối câu hỏi sang Anthropic Claude 3 để tổng hợp phản hồi.
- **Kiểm soát rủi ro:** Tích hợp Bedrock Guardrails nhằm chặn lọc các dữ liệu cá nhân nhạy cảm và giảm thiểu hiện tượng ảo giác của mô hình LLM.

### Lợi ích:

- Hệ thống đạt thời gian phản hồi dưới 2 giây mỗi truy vấn.
- Cắt giảm hoàn toàn chi phí duy trì hạ tầng khi nhàn rỗi nhờ cơ chế On-Demand.
- Việc sử dụng Managed Services giúp đội ngũ phát triển giản lược tối đa chi phí vận hành Vector Database thủ công.

![RAG Chatbot Architecture](/images/3-BlogsPosted/blog1.png)

### Liên kết tham khảo:

- [Bài đăng Facebook](https://aws.amazon.com/blogs/machine-learning/introducing-guardrails-in-knowledge-bases-for-amazon-bedrock/?fbclid=IwY2xjawURPZlwZG9mBWV4dG4DYWVtAjEwAGJyaWQRMWhyYk9KczFxVDF0cGJhUnJzcnRjBmFwcF9pZBAyMjIwMzkxNzg4MjAwODkyAAEeqpCHORwGtxwsHoPrJQKgvbUBUnE0KZh2yUTMQDtq60v12CvrbNssxJ6NmM4_aem_u1Me9mNwOgxTyCPdcEr6zg)
- [Bài viết AWS](https://aws.amazon.com/blogs/machine-learning/introducing-guardrails-in-knowledge-bases-for-amazon-bedrock/)