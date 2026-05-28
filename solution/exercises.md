# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature

Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)

> Khi temperature càng thấp (0.0), phản hồi của mô hình càng ổn định, chính xác và ít thay đổi giữa các lần gọi. Khi tăng temperature lên 0.5 và 1.0, câu trả lời trở nên đa dạng và tự nhiên hơn. Với temperature 1.5, mô hình có xu hướng sáng tạo hơn nhưng đôi khi lan man hoặc kém chính xác hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**

> Tôi sẽ đặt temperature khoảng 0.2–0.5 cho chatbot hỗ trợ khách hàng vì cần phản hồi ổn định, chính xác và nhất quán. Temperature thấp giúp hạn chế việc chatbot trả lời quá sáng tạo hoặc đưa ra thông tin không cần thiết.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**

> 10.000 người dùng × 3 lần gọi API/ngày × 350 token ≈ 10.500.000 token mỗi ngày.
> Theo bảng giá, GPT-4o khoảng $10 / 1M output tokens còn GPT-4o-mini khoảng $0.60 / 1M output tokens.
> Vì vậy GPT-4o đắt hơn khoảng 16–17 lần so với GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**

> GPT-4o phù hợp cho các tác vụ cần chất lượng cao như phân tích tài liệu chuyên môn, trợ lý AI doanh nghiệp hoặc xử lý dữ liệu đa phương thức vì độ chính xác và khả năng suy luận tốt hơn.
> GPT-4o-mini phù hợp cho chatbot chăm sóc khách hàng, FAQ tự động hoặc các ứng dụng có lượng request lớn vì chi phí thấp và tốc độ phản hồi nhanh hơn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)

> Streaming quan trọng nhất trong các ứng dụng chatbot thời gian thực vì người dùng có thể thấy phản hồi xuất hiện ngay lập tức thay vì phải chờ toàn bộ câu trả lời hoàn thành, giúp trải nghiệm tự nhiên và nhanh hơn. Điều này đặc biệt hữu ích với các phản hồi dài hoặc khi tốc độ mạng chậm. Ngược lại, non-streaming phù hợp hơn khi cần xử lý hoàn chỉnh trước khi hiển thị, ví dụ như trả về JSON, báo cáo cố định hoặc dữ liệu cần kiểm tra đầy đủ trước khi gửi cho người dùng.

## Danh Sách Kiểm Tra Nộp Bài

* [x] Tất cả tests pass: `pytest tests/ -v`
* [x] `call_openai` đã triển khai và kiểm thử
* [x] `call_openai_mini` đã triển khai và kiểm thử
* [x] `compare_models` đã triển khai và kiểm thử
* [x] `streaming_chatbot` đã triển khai và kiểm thử
* [x] `retry_with_backoff` đã triển khai và kiểm thử
* [x] `batch_compare` đã triển khai và kiểm thử
* [x] `format_comparison_table` đã triển khai và kiểm thử
* [x] `exercises.md` đã điền đầy đủ
* [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định

