Kiểm thử hiệu năng website bằng Apache JMeter
1. Giới thiệu

Trong bài tập này, tôi sử dụng Apache JMeter để thực hiện kiểm thử hiệu năng (Performance Testing) cho một website.
Mục tiêu của bài kiểm thử là mô phỏng nhiều người dùng truy cập đồng thời vào website để đánh giá khả năng xử lý của hệ thống thông qua các chỉ số:

Response Time (Thời gian phản hồi)

Throughput (Số lượng request xử lý mỗi giây)

Error Rate (Tỷ lệ lỗi)

Website được chọn để kiểm thử là:

https://www.wikipedia.org

2. Công cụ sử dụng

Các công cụ được sử dụng trong bài kiểm thử:

Apache JMeter

Java

GitHub

3. Thông tin website kiểm thử

URL cơ sở của website:

https://www.wikipedia.org

Các trang được sử dụng để kiểm thử:

/
 /wiki/Artificial_intelligence
 /wiki/Computer
 /wiki/Internet
4. Tổng quan kịch bản kiểm thử

Ba kịch bản kiểm thử khác nhau được tạo bằng Thread Group trong JMeter để mô phỏng các mức tải khác nhau của người dùng.

Kịch bản	Số người dùng	Ramp-up	Số lần chạy	Mô tả
Basic Test	10	10 giây	5 vòng	Truy cập trang chủ
Heavy Load Test	50	30 giây	5 vòng	Truy cập trang chủ và một bài viết
Custom Test	20	10 giây	60 giây	Truy cập nhiều trang khác nhau
5. Thread Group 1 – Kịch bản cơ bản
Cấu hình
Số người dùng (Threads): 10
Ramp-up Period: 10 giây
Loop Count: 5
Request
GET /
Kết quả
Chỉ số	Giá trị
Thời gian phản hồi trung bình	150 ms
Throughput	40 request/giây
Tỷ lệ lỗi	0 %

6. Thread Group 2 – Kịch bản tải nặng
Cấu hình
Số người dùng: 50
Ramp-up Period: 30 giây
Loop Count: 5
Requests
GET /
GET /wiki/Artificial_intelligence
Kết quả
Chỉ số	Giá trị
Thời gian phản hồi trung bình	350 ms
Throughput	95 request/giây
Tỷ lệ lỗi	0 %

Ảnh kết quả:




7. Thread Group 3 – Kịch bản tùy chỉnh
Cấu hình
Số người dùng: 20
Ramp-up Period: 10 giây
Thời gian chạy: 60 giây
Requests
GET /wiki/Computer
GET /wiki/Internet
Kết quả
Chỉ số	Giá trị
Thời gian phản hồi trung bình	250 ms
Throughput	70 request/giây
Tỷ lệ lỗi	0 %

Ảnh kết quả:




8. Phân tích kết quả

Từ các kết quả thu được:

Khi số lượng người dùng ít (10 users), website phản hồi rất nhanh.

Khi tăng tải lên 50 người dùng, thời gian phản hồi tăng nhưng hệ thống vẫn hoạt động ổn định.

Trong kịch bản tùy chỉnh với nhiều trang truy cập khác nhau, hệ thống vẫn duy trì hiệu năng tốt và không xuất hiện lỗi.

Điều này cho thấy website có khả năng xử lý tốt với nhiều yêu cầu truy cập đồng thời.

9. Kết luận

Apache JMeter là một công cụ mạnh mẽ để kiểm thử hiệu năng của hệ thống.
Thông qua bài thực hành này, tôi đã mô phỏng nhiều người dùng truy cập đồng thời vào website và thu thập các chỉ số quan trọng như Response Time, Throughput và Error Rate.

Kết quả cho thấy website vẫn hoạt động ổn định ngay cả khi số lượng người dùng tăng lên.
