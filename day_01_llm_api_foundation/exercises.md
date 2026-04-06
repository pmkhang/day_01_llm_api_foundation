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
> Khi temperature tăng, phản hồi trở nên sáng tạo và đa dạng hơn nhưng cũng kém ổn định hơn. Ở mức 0.0, câu trả lời thường ngắn gọn và lặp lại giống nhau, trong khi ở mức 1.5, câu chữ có thể trở nên lộn xộn hoặc xuất hiện các ý tưởng kỳ lạ.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature thấp (khoảng 0.0 - 0.2). Trong hỗ trợ khách hàng, tính chính xác và nhất quán là quan trọng nhất; chatbot cần cung cấp các thông tin thực tế giống nhau cho cùng một câu hỏi thay vì sáng tạo quá mức dẫn đến hiểu lầm.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o ($0.010/1k) so với GPT-4o-mini ($0.0006/1k) đắt hơn khoảng 16.67 lần. Với 10.000 người x 3 lần x 350 token = 10.5 triệu token mỗi ngày, sự chênh lệch chi phí này là cực kỳ đáng kể (khoảng $105 so với $6.3 mỗi ngày).

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi cần lập luận logic phức tạp, giải quyết các bài toán toán học hóc búa hoặc viết code chuyên sâu. GPT-4o-mini tốt hơn cho các tác vụ phân loại email, tóm tắt văn bản ngắn, hoặc chatbot FAQ đơn giản nơi chi phí và tốc độ là ưu tiên hàng đầu.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming cực kỳ quan trọng đối với các ứng dụng chatbot tương tác (như ChatGPT) vì nó giúp cải thiện trải nghiệm người dùng bằng cách hiển thị văn bản ngay lập tức, giảm cảm giác phải chờ đợi. Ngược lại, non-streaming phù hợp hơn cho các hệ thống backend gọi API để xử lý dữ liệu tự động, trích xuất thông tin có cấu trúc (JSON), hoặc khi phản hồi quá ngắn khiến thời gian chờ đợi là không đáng kể.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
