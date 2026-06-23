# Reflection — Lab 19

**Tên:** Vũ Quang Vinh
**Cohort:** A20-K2
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

Trên golden set 50 queries, kết quả Precision@10 cho thấy:
- **exact**: hybrid (96.7%) ≈ keyword (96.7%) > semantic (88.7%) — BM25 đã đủ mạnh khi query khớp chính xác từ khóa trong document.
- **paraphrase**: hybrid (32.0%) > keyword (33.3%) > semantic (24.0%) — cả ba mode đều yếu vì corpus tiếng Việt với model tiếng Anh (bge-small-en) không capture semantic tốt; hybrid cứu được một phần nhờ BM25.
- **mixed**: hybrid (100%) > semantic (98.5%) > keyword (97.0%) — hybrid thắng rõ nhất khi query kết hợp cả từ khóa lẫn ngữ nghĩa.

Không nên dùng hybrid khi: (1) latency budget rất chặt và corpus nhỏ — pure BM25 nhanh hơn 3-4x; (2) corpus hoàn toàn structured/keyword-based như product SKU hay mã số — semantic không thêm giá trị; (3) không có GPU và model embedding nặng — chi phí embed mỗi query vượt lợi ích precision.

---

## Điều ngạc nhiên nhất khi làm lab này

Feast online lookup P99 chỉ 1.56ms dù chạy trên SQLite local — nhanh hơn kỳ vọng rất nhiều. Và embedding cache đơn giản giảm hybrid P99 từ 88ms xuống 13ms chỉ bằng một dict.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_