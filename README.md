# Track1_Day20_2A202602797_ThanThiKimChi

* **Họ và tên:** Thân Thị Kim Chi
* **Mã học viên:** 2A202602797
* **Dự án chọn làm:** **StudyMate AI** (Trợ lý AI đồng hành học tập và ôn tập thông minh cho sinh viên)
* **Tệp Metrics Pack chính thức:** [Xem tệp METRICS_PACK.md](./METRICS_PACK.md)
* **Tệp nhật ký sử dụng AI:** [Xem tệp ai-support-log.md](./ai-support-log.md)

---

## Điều tôi mang về áp dụng cho dự án thật

1. **Phân biệt rạch ròi Core Action vs Thao tác UI vs Output hệ thống:**  
   Trong sản phẩm AI, việc người dùng "gõ prompt" hay "AI sinh tóm tắt xong" hoàn toàn chưa chứng minh giá trị được tạo ra. Core Action chỉ thực sự xảy ra khi người dùng tiếp nhận giá trị đó vào công việc/học tập thực tế (ở đây là đọc hiểu và nộp bài kiểm tra kiến thức). Áp dụng vào dự án thật, tôi sẽ không đo "số lượt gọi API/chat" để báo cáo thành tích ảo.

2. **Tôn trọng nhịp tự nhiên (Nature trước, Nurture sau):**  
   Không được ép người dùng vào nhịp Daily chỉ vì dashboard có sẵn DAU hay nhìn số to cho đẹp. Với sản phẩm phục vụ sinh viên, nhịp tự nhiên là chu kỳ tuần học (Weekly). Nurture (thông báo, email) chỉ có tác dụng khuếch đại khi người dùng đã có nhu cầu tự nhiên, không thể dùng notification để bịa ra một thói quen không tồn tại.

3. **North Star Metric bắt buộc phải có Quality Threshold:**  
   Bất kỳ metric nào cũng có thể bị "game" nếu chỉ đo số lượng đơn thuần. Công thức chuẩn `Unit of value + Quality threshold + Frequency` giúp bảo vệ sản phẩm khỏi các lượt tương tác rác, đồng thời luôn cần Counter-metric (như tỷ lệ báo lỗi nội dung và chi phí API) để đảm bảo chất lượng và tính bền vững.

4. **Product Loop phải có Reason to return nội tại:**  
   Một loop bền vững không thể dựa vào push notification mà phải tạo ra **Investment / Saved state** (tích lũy dữ liệu, tài liệu, lịch sử học tập). Càng dùng lâu, giá trị tích lũy càng lớn, chi phí rời bỏ càng cao và người dùng có lý do tự nhiên để tự quay lại.
