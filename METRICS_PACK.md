# StudyMate AI — Metrics Pack

> **Học viên:** Thân Thị Kim Chi  
> **Mã học viên:** 2A202602797  
> **Dự án:** StudyMate AI (Trợ lý học tập thông minh cho sinh viên)  

---

## 00 — DỰ ÁN, PERSONA, CORE JOB

* **1. Dự án:**  
  **StudyMate AI** — Trợ lý AI đồng hành học tập dành cho sinh viên, hỗ trợ tự động tóm tắt slide bài giảng (PDF), trích xuất kiến thức trọng tâm và tạo bộ câu hỏi trắc nghiệm/flashcard ôn tập nhanh theo môn học.
* **2. Persona:**  
  **Hồng Nhung** — Mỗi kỳ học 5–6 môn, thường xuyên đối mặt với 40–80 trang slide bài giảng mỗi tuần kèm bài tập định kỳ; quỹ thời gian tự học có hạn và dễ bị ngợp trước khối lượng tài liệu lớn.
* **3. Core job (JTBD):**  
  > *"Mỗi khi nhận hàng chục slide bài giảng và tài liệu dài dằng dặc trước buổi học hoặc kỳ thi, tôi muốn nhanh chóng nắm được các ý cốt lõi và tự kiểm tra xem mình đã hiểu đúng chưa, để không bị trễ hạn bài tập và không phải thức trắng đêm ôn thi trong hoang mang."*

---

## 01 — CORE ACTION CARD

### 1. Phân biệt bốn khái niệm cốt lõi

| Khái niệm | Câu hỏi | Câu trả lời cho StudyMate AI |
| :--- | :--- | :--- |
| **Core job** | User đang cố hoàn thành việc gì? | Hiểu nhanh nội dung bài giảng cốt lõi và kiểm tra mức độ hiểu trước buổi học/bài thi. |
| **Core action** | User làm gì trong sản phẩm để tiến tới giá trị? | **Hoàn thành một phiên học tập/ôn tập từ slide (Complete Study Session: Đọc tóm tắt + nộp quiz ôn tập)**. |
| **Core value** | User nhận được lợi ích gì? | Nắm chắc kiến thức trọng tâm chỉ trong 10-15 phút, tự tin vượt qua bài kiểm tra mà không bị ngợp tài liệu. |
| **Core value event** | Sự kiện nào chứng minh value đã xảy ra? | `study_set_completed` |

### 2. Core Action Card

| Thành phần | Nội dung chi tiết |
| :--- | :--- |
| **Target user** | Sinh viên đại học đang học các môn có nhiều slide bài giảng. |
| **Core job** | Nhanh chóng nắm kiến thức trọng yếu và tự đánh giá độ hiểu bài từ đống slide dài. |
| **Core action** | **Hoàn thành phiên ôn tập tài liệu bài giảng (Complete Study Session)**. |
| **Object** | Bộ tài liệu học tập được AI xử lý (*Study Set*: gồm tóm tắt ý chính + 3-5 câu hỏi trắc nghiệm kiểm tra). |
| **Preconditions** | User đã tải lên slide bài giảng (PDF/Docx) và hệ thống đã tạo xong Study Set tương ứng. |
| **Completion rule** | User duyệt qua toàn bộ các thẻ tóm tắt và **bấm nút nộp bài kiểm tra trắc nghiệm nhanh (Submit Quiz)** có kết quả phản hồi từ hệ thống. |
| **Core value** | Tiết kiệm 70% thời gian đọc slide dài, nắm chắc kiến thức và an tâm trước buổi học/kỳ thi. |
| **Evidence of value** | User hoàn thành toàn bộ thẻ ôn tập, trả lời các câu hỏi kiểm tra kiến thức và đạt điểm bài kiểm tra. |
| **Candidate event** | `study_set_completed` (với properties: `set_id`, `read_duration_sec`, `quiz_score_pct`). |

### 3. Tự kiểm 5 tiêu chí

1. **Gần core value (Đạt - 5/5):** Khi hoàn thành phiên học tập, sinh viên đã thực sự tiếp thu kiến thức và tự kiểm tra xong, không phải chỉ đứng nhìn màn hình.
2. **Có thể lặp lại (Đạt - 5/5):** Lặp lại theo mỗi môn học, mỗi tuần học và mỗi đợt kiểm tra.
3. **Có thể quan sát (Đạt - 5/5):** Đo lường chính xác bằng event `study_set_completed` khi user hoàn tất quiz kiểm tra.
4. **Có ý nghĩa (Đạt - 5/5):** Số lượng session hoàn thành tăng trực tiếp chứng minh sinh viên đang thực sự dùng sản phẩm để học tập hiệu quả, không phải vào dạo chơi rồi thoát.
5. **Có thể tác động (Đạt - 5/5):** Team có thể tối ưu giao diện đọc thẻ dễ hiểu hơn, sinh câu hỏi sát đề cương hơn, chia nhỏ bài học giúp sinh viên dễ hoàn thành hơn.

> **Kết luận Gate 1:** Đạt 5/5 tiêu chí. Core action tách biệt hoàn toàn với *thao tác UI* ("mở app", "gõ prompt") và *output hệ thống* ("AI sinh ra bản tóm tắt").

---

## 02 — ACTION NATURE CARD & KẾT LUẬN CADENCE

### 1. Action Nature Card

| Thành phần | Câu hỏi | Câu trả lời cho StudyMate AI |
| :--- | :--- | :--- |
| **Actor** | Ai thực hiện? | **User cá nhân (Sinh viên)** — tài khoản học tập cá nhân. |
| **Intent** | Hành vi bắt đầu từ nhu cầu gì? | Nhu cầu chuẩn bị bài trước buổi học trên lớp, làm bài tập tuần, hoặc ôn tập trước bài kiểm tra định kỳ. |
| **Trigger** | Kích hoạt bởi điều gì? | **Sự kiện bên ngoài (External trigger):** Lịch học trên thời khóa biểu, giảng viên giao slide mới, hoặc deadline bài tập sắp đến hạn. |
| **Effort** | Mất bao nhiêu công sức? | Mất khoảng **1–2 phút** tải slide lên và **8–12 phút** tập trung đọc tóm tắt & trả lời câu hỏi tự kiểm tra. |
| **Value timing** | Value xuất hiện khi nào? | **Xuất hiện ngay (Immediate):** Nắm được ý chính ngay sau khi đọc; đồng thời **Tích lũy (Cumulative):** Bộ kiến thức tích lũy dần cho kỳ thi cuối kỳ. |
| **State** | Dữ liệu nào được giữ lại? | Trạng thái buổi học đổi thành `completed`; điểm số quiz tự kiểm tra được lưu lại; tóm tắt được lưu vào "Sổ tay kỳ thi" (Knowledge Vault). |
| **Dependency** | Phụ thuộc vào yếu tố nào? | Phụ thuộc vào **nguồn cung tài liệu**: sinh viên phải có slide/giáo trình từ giảng viên hoặc trường. |
| **Repeat condition** | Điều kiện lặp lại là gì? | **Tuần học mới bắt đầu** (có bài giảng mới của các môn) hoặc **kỳ thi/bài kiểm tra giữa kỳ, cuối kỳ đến hạn**. |

### 2. Kết luận cadence

* **Dạng hành vi chính:** **Theo chu kỳ (Cyclical rhythm)** gắn liền với lịch học của học kỳ sinh viên (mỗi tuần có 3–5 môn học luân phiên).
* **Kết luận chuẩn theo template:**
  > *"Đối với **sinh viên đại học**, core action **hoàn thành phiên ôn tập tài liệu bài giảng (Complete Study Session)** thường xuất hiện **hàng tuần (Weekly: 2–3 lần/tuần)** vì **lịch học tại giảng đường và bài tập được giảng viên giao theo chu kỳ tuần học (mỗi tuần có slide bài mới cho từng môn học)**. Do đó, nhịp đo phù hợp là **Weekly (7 ngày)** ở cấp **User cá nhân**."*

---

## 03 — METRIC SYSTEM

### 1. Activation Metric
* **Start event:** `account_created` (User đăng ký tài khoản thành công).
* **Activation event:** `first_study_set_completed` (Lần đầu tiên user đọc hết tóm tắt bài giảng và nộp quiz kiểm tra hiểu bài với điểm số $\ge 60\%$).
* **Time window:** Trong vòng **48 giờ** kể từ khi tạo tài khoản.
  *(Lý do: Sinh viên đăng ký app khi đang có nhu cầu giải quyết tài liệu ngay; nếu quá 48h không hoàn tất phiên đầu tiên, rủi ro drop-off là rất lớn).*

### 2. Engagement Metric
* **Frequency (Tần suất):** **Weekly Study Sessions / Active User (WSS/WAU):** Số phiên học hoàn thành trung bình của một sinh viên trong một tuần (Mục tiêu: 2–3 phiên/tuần, tương ứng với số môn học).
* **Depth (Độ sâu / Chất lượng):** **Quiz Mastery Rate:** Tỷ lệ phiên học có điểm kiểm tra đạt từ **$70\%$ câu trả lời đúng trở lên** (chứng minh việc đọc tóm tắt mang lại sự hiểu bài sâu).

### 3. North Star Metric (NSM), Leading Indicators & Counter-Metrics

#### North Star Metric (NSM)
$$\mathbf{NSM} = \text{Weekly High-Quality Completed Study Sessions (WHQCS)}$$
> **Định nghĩa:** *"Tổng số phiên học tập được hoàn thành hàng tuần có thời gian đọc $\ge 3$ phút và đạt điểm bài kiểm tra quiz tự động $\ge 70\%$."*  
> - **Unit of value:** Completed Study Session (Phiên học hoàn thành).  
> - **Quality threshold:** Thời gian đọc $\ge 3$ phút & Điểm quiz $\ge 70\%$.  
> - **Frequency:** Weekly (Hàng tuần).

#### Leading Indicators (Tối đa 3 chỉ số dự báo)
1. **Slide-to-Study-Set Conversion Rate (%):** Tỷ lệ slide tải lên được chuyển đổi thành phiên học hoàn thành trong vòng 24h (Dự báo core action lặp lại vì giải quyết đúng nhu cầu cấp bách).
2. **Weekly Study Plan Setup Rate (%):** Tỷ lệ sinh viên ghim $\ge 2$ môn học cần ôn tập trong tuần (Dự báo việc quay lại học thường xuyên gấp 3 lần).
3. **Session Save/Export Rate (%):** Tỷ lệ sinh viên bấm lưu tóm tắt vào sổ tay cá nhân hoặc tải về (Dự báo giá trị tích lũy cao và cam kết gắn bó lâu dài).

#### Counter-Metrics (Chỉ số cảnh báo rủi ro)
1. **AI Hallucination / Report Rate (%):** Tỷ lệ sinh viên bấm báo cáo tóm tắt sai kiến thức hoặc câu hỏi quiz không đúng trọng tâm (Ngưỡng cảnh báo: $> 3\%$). Ngăn chặn việc AI sinh ẩu để tăng số lượng nhưng làm giảm chất lượng.
2. **AI Cost per Completed Session ($/session):** Chi phí token API trung bình trên mỗi phiên học hoàn tất. Ngăn ngừa chi phí leo thang làm mất tính khả thi của sản phẩm.

---

## 04 — RETENTION DEFINITION (Đủ 6 thành phần)

| Thành phần | Câu hỏi | Định nghĩa cho StudyMate AI |
| :--- | :--- | :--- |
| **1. Unit** | Ai/cái gì được theo dõi? | **User cá nhân (Sinh viên)** — định danh bằng `user_id`. |
| **2. Cohort entry** | Event nào đưa unit vào cohort? | **Activated User:** User thực hiện `first_study_set_completed` trong tuần $W_0$. |
| **3. Return event** | Core action nào phải lặp lại? | `study_set_completed` (với điều kiện điểm quiz $\ge 60\%$). |
| **4. Window** | Nhịp đo là gì? | **Weekly (theo tuần học):** Đo theo các bracket tuần $W_1, W_2, W_4, W_8$ (khớp hoàn toàn với Cadence ở mục 02). |
| **5. Threshold** | Bao nhiêu lần trong window? | **$\ge 2$ lần/tuần** (phản ánh nhịp học tự nhiên 2–3 môn/tuần). |
| **6. Segment** | Áp dụng cho ai? | **Sinh viên chính quy trong kỳ học** (loại trừ tài khoản thử nghiệm và giai đoạn nghỉ hè). |

---

## 05 — PRODUCT LOOP

### 1. Bản vẽ Product Loop 2 chu kỳ

```
[Chu kỳ 1: Bài học tuần hiện tại]
Natural trigger: Lịch học tuần mới / Giảng viên gửi slide bài giảng môn A
      ↓
Core action: Upload slide & Hoàn thành phiên học tóm tắt + làm quiz kiểm tra
      ↓
Immediate value: Nắm trọn ý chính bài học chỉ trong 10 phút, tự tin đi học/làm bài tập tuần
      ↓
Saved state / Investment: Bộ câu hỏi, ghi chú và kết quả quiz môn A được tự động lưu vào "Sổ tay kỳ thi" (Knowledge Vault)
      ↓
[Chu kỳ 2: Bài học tuần kế tiếp & Chu kỳ ôn thi]
Next natural trigger: Giảng viên giao slide bài tiếp theo HOẶC thông báo kiểm tra giữa kỳ môn A
      ↓
Core action tiếp theo: Mở lại Sổ tay ôn tập (đã lưu từ trước) & Hoàn thành phiên học tóm tắt cho bài giảng mới
      ↓
Repeat value: Tiết kiệm thời gian ôn bài lũy tiến, kết quả học tập cải thiện rõ rệt, không bị dồn ứ kiến thức trước kỳ thi
```

* **Loại loop chính:** **Progress Loop (Vòng lặp tiến trình tích lũy)** kết hợp **Habit Loop**.
* **Reason to return nội tại (Nếu bỏ Notification):** Sinh viên quay lại vì **"Sổ tay kỳ thi" (Knowledge Vault)** tích lũy dữ liệu học tập qua từng tuần. Càng học nhiều, tài sản ôn thi càng đầy đủ và áp lực thi cử càng giảm.

### 2. Metric Hypothesis
> *"Nếu **Progress Loop (tích lũy sổ tay ôn tập)** này hoạt động, metric **Weekly High-Quality Completed Study Sessions (North Star Metric)** sẽ thay đổi theo hướng **tăng ít nhất 25% ở nhóm cohort đã tích lũy từ $\ge 3$ môn học** trong vòng **4 tuần đầu của học kỳ**, vì **sinh viên cảm nhận được giá trị tích lũy giảm tải áp lực ôn thi rõ rệt so với việc tự đọc slide rời rạc**."*

---

## 06 — TRACKINg

### 1. Bảng 5 Core Events (Map 100% về Metric)

| Tên event | Ý nghĩa (Điều đã xảy ra) | Thời điểm ghi nhận (Trigger) | Metric sử dụng |
| :--- | :--- | :--- | :--- |
| `account_created` | User tạo tài khoản mới thành công | Ngay khi DB xác nhận tạo tài khoản và chuyển hướng vào dashboard | **Activation (Start Event)** |
| `slide_upload_succeeded` | Tài liệu slide PDF được tải lên và parse thành công | Khi backend xử lý xong file và sinh ra dữ liệu tóm tắt thô | **Leading Indicator 1** (Slide-to-Study-Set Conversion) |
| `study_set_completed` | User hoàn thành toàn bộ thẻ tóm tắt và nộp bài quiz | Khi user ấn nút "Nộp bài quiz" và backend trả về kết quả điểm số | **Activation Event**, **North Star Metric (NSM)**, **Wn Retention (Return Event)**, **Engagement (WSS/WAU)** |
| `study_set_saved_to_vault` | Tóm tắt và câu hỏi được user lưu/ghim vào Sổ tay môn học | Khi user bấm lưu/tải tóm tắt về thiết bị thành công | **Leading Indicator 3** (Session Save/Export Rate) |
| `ai_content_reported` | Sinh viên bấm gắn cờ báo lỗi tóm tắt sai hoặc câu hỏi ảo | Khi modal báo lỗi gửi thành công về hệ thống kiểm duyệt | **Counter-Metric 1** (AI Hallucination / Report Rate) |

### 2. Tiêu chí nghiệm thu (Acceptance Criteria)

* **Tiêu chí 1 (Chỉ bắn event khi hành vi hoàn tất thật sự):**  
  > *"Hệ thống chỉ được bắn event `study_set_completed` khi người dùng đã duyệt qua $100\%$ các thẻ tóm tắt chính và đã bấm nộp câu trả lời bài quiz kiểm tra có kết quả trả về từ máy chủ. Tuyệt đối không bắn khi người dùng chỉ mới mở màn hình xem slide hoặc mới trả lời 1 phần câu hỏi rồi thoát ra."*

* **Tiêu chí 2 (Chống trùng lặp khi reload/retry):**  
  > *"Đối với mỗi cặp `user_id` và `study_set_id`, hệ thống chỉ ghi nhận duy nhất $01$ event `study_set_completed` trong một phiên học. Việc người dùng tải lại trang (F5), mở lại thẻ để xem lại tóm tắt, hoặc mạng bị chập chờn gửi lại request (network retry) không được phép tạo thêm event `study_set_completed` trùng lặp."*

---

## 07 — TỰ SOI LỖI & RATIONALE CHỈNH SỬA

| STT | Tiêu chí tự soi | Đánh giá | Rationale & Quyết định |
| :---: | :--- | :---: | :--- |
| **1** | Core action không phải thao tác giao diện hay output hệ thống? | ĐẠT | Chọn `Complete Study Session` (hành vi nhận giá trị). Không chọn "mở app", "hỏi AI" (UI) hay "AI tóm tắt xong" (output). |
| **2** | Activation không phải "xem tour" hay "đăng nhập"? | ĐẠT | Yêu cầu `first_study_set_completed` đạt quiz $\ge 60\%$ trong 48h. |
| **3** | Frequency không cao hơn nhu cầu thật? | ĐẠT | Chọn Weekly (2-3 lần/tuần) khớp thời khóa biểu môn học. Không ép Daily. |
| **4** | Loop có reason to return ngoài notification? | ĐẠT | Reason to return là tài sản tích lũy trong "Sổ tay kỳ thi" (Knowledge Vault). |
| **5** | Retention không dùng chung một window cho mọi cadence? | ĐẠT | Dùng Weekly Bracket Retention ($W_1, W_2, W_4, W_8$), khớp hoàn toàn nhịp Weekly. |
| **6** | Mọi event đều map về một metric? | ĐẠT | 5/5 event map 1-1 về các metric ở mục 03 & 04. |
| **7** | Metric nào cũng có event để tính nó? | ĐẠT | Toàn bộ metric đều có event và property cụ thể để truy vấn. |
