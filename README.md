# Online Machine Learning for Real-Time Credit Card Fraud Detection

## 1. Giới thiệu đề tài

Đề tài của nhóm tập trung vào việc nghiên cứu **Online Machine Learning trên dữ liệu dòng (Streaming Data)** cho bài toán **phát hiện gian lận thẻ tín dụng trong thời gian thực**.

Khác với cách học máy truyền thống, trong đó mô hình thường được huấn luyện trên một tập dữ liệu có sẵn, Online Machine Learning cho phép mô hình tiếp nhận và học từ dữ liệu mới liên tục.

## 2. Vấn đề nghiên cứu

Trong bài toán phát hiện gian lận thẻ tín dụng, dữ liệu giao dịch có thể phát sinh liên tục theo thời gian. Đặc điểm của dữ liệu và hành vi gian lận cũng có thể thay đổi theo thời gian, dẫn đến hiện tượng **Concept Drift**.

Vì vậy, mô hình cần có khả năng cập nhật và thích nghi khi dữ liệu mới xuất hiện.

## 3. Công cụ và tài liệu

Nhóm sử dụng Python và thư viện **River** để nghiên cứu và triển khai các thuật toán Online Machine Learning.

Nguồn tham khảo chính:

- River: https://riverml.xyz/latest/

## 4. Các hướng thuật toán đang nghiên cứu

Nhóm đang tìm hiểu một số thuật toán có khả năng xử lý dữ liệu dòng:

- Adaptive Random Forest (ARF)
- Hoeffding Tree / Very Fast Decision Tree (VFDT)
- Online Isolation Forest / Half-Space Trees
- Stochastic Gradient Descent (SGD) kết hợp Logistic Regression


