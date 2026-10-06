# AI Support Log — Day 20 Lab

**Học viên:** Thân Thị Kim Chi  
**Mã học viên:** 2A202602797  
**Dự án:** StudyMate AI  

---

### 1. AI đã giúp tôi ở đâu?
* **Brainstorm ứng viên Core Action:** AI giúp phân tích và phân định rạch ròi 3 tầng hành vi trong ứng dụng AI: Thao tác giao diện (gõ prompt/hỏi AI) $\rightarrow$ Output hệ thống (AI sinh câu trả lời) $\rightarrow$ Core Action tạo giá trị thực (User hoàn thành phiên ôn tập và trả lời quiz kiểm tra kiến thức).
* **Chuẩn hóa cấu trúc:** Gợi ý danh pháp đặt tên event theo chuẩn `object_action` và cấu trúc 2 tiêu chí nghiệm thu (Acceptance Criteria) kỹ thuật để chống việc bắn event sớm hoặc duplicate event do F5/retry mạng.
* **Đối chiếu rubric:** Hỗ trợ rà soát 6 thành phần của Retention và 5 tiêu chí tự kiểm Core Action.

---

### 2. AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?
* **Đề xuất nhịp Daily sai bản chất tự nhiên (Nature):** Ban đầu, AI có xu hướng đề xuất nhịp đo là **Daily (DAU)** và gợi ý cơ chế duy trì Streak/nhắc nhở mỗi ngày giống như các app EdTech học ngoại ngữ (Duolingo). Đề xuất này **sai lệch nghiêm trọng với bản chất học tập của sinh viên đại học**, vì lịch học và slide bài giảng trên trường phân bổ theo chu kỳ tuần học (mỗi tuần 1-2 buổi/môn), sinh viên không có nhu cầu ôn dồn dập mỗi ngày cùng một môn.
* **Gợi ý loop phụ thuộc Notification:** AI ban đầu đưa Push Notification làm kích hoạt chính cho chu kỳ quay lại tiếp theo (Reason to return). Điều này biến loop thành nurture gượng ép chứ không phải động lực tự nhiên của người dùng.

---

### 3. Tôi đã tự sửa hoặc quyết định lại điều gì?
* **Quyết định chốt nhịp Weekly (2–3 lần/tuần):** Tôi kiên quyết bác bỏ Daily và chọn Weekly dựa trên phân tích nhịp học thực tế theo môn và deadline tuần của sinh viên.
* **Bổ sung Quality Threshold vào North Star Metric:** Tôi tự quyết định đưa điều kiện thời gian đọc $\ge 3$ phút và điểm quiz $\ge 70\%$ vào NSM để đảm bảo NSM phản ánh giá trị thật, ngăn ngừa tình trạng click lướt qua thẻ để "game" số liệu.
* **Tự thiết kế cơ chế Investment trong Loop:** Tôi thay thế sự phụ thuộc vào Notification bằng cơ chế **"Sổ tay kỳ thi" (Knowledge Vault)** tích lũy dần. Càng học nhiều bài, tài sản ôn thi tích lũy càng lớn, tạo ra động lực nội tại để sinh viên tự quay lại ôn tập môn học tiếp theo.
