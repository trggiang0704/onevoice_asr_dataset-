# QC Report — Automatic Checks

**Nguồn dữ liệu:** `qc/automatic_checks.csv`
**Người phụ trách:** Thành viên 2 (Data Engineer / Automatic QC)
**Phạm vi:** Toàn bộ clip tiếng Trung trong `output_wav/`
**Ngày chạy QC:** 2026-09-16 16:50:36

---

## 1. Tóm tắt kết quả

| Chỉ số | Giá trị |
|---|---:|
| Tổng số clip | 6,541 |
| Clip PASS | 6,541 (100.00%) |
| Clip FAIL | 0 (0.00%) |
| Tổng thời lượng audio | ~10.45 giờ |
| Độ dài clip trung bình | 5.75 giây |
| Độ dài clip ngắn nhất | 1.48 giây |
| Độ dài clip dài nhất | 20.00 giây |
| Số episode | 1 |
| Episode PASS 100% clip | 1 / 1 |

**Kết luận nhanh:** Batch xử lý hoàn tất. Có 0 clip gặp lỗi.

---

## 2. Kết quả theo từng tiêu chí

| # | Tiêu chí | Số clip FAIL | Ghi chú |
|---|---|---:|---|
| 1 | File mở được (`opens_ok`) | 0 | |
| 2 | Đúng WAV 16kHz mono (`format_ok`) | 0 | |
| 3 | Không rỗng (`empty_ok`) | 0 | |
| 4 | Độ dài trong ngưỡng 1–20s (`duration_ok`) | 0 | |
| 5 | Transcript không rỗng (`transcript_present`) | 0 | |
| 6 | Encoding transcript hợp lệ (`transcript_encoding_ok`) | 0 | |
| 7 | Không trùng checksum (`duplicate_ok`) | 0 | |
| 8 | Silence ratio hợp lệ (`silence_ok`) | 0 | |
| 9 | Không clipping nghiêm trọng (`clipping_ok`) | 0 | |
| 10 | Language-ID phù hợp (`lang_ok`) | 0 | |

---

## 3. Danh sách clip FAIL — chi tiết

| Clip | Lỗi |
|---|---|

---
## 4. Kết quả theo episode

