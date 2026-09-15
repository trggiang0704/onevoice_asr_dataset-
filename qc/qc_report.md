# QC Report — Automatic Checks

**Nguồn dữ liệu:** `qc/automatic_checks.csv`
**Người phụ trách:** Thành viên 2 (Data Engineer / Automatic QC)
**Phạm vi:** Toàn bộ clip tiếng Anh trong `audio/Processed_16k`

---

## 1. Tóm tắt kết quả

| Chỉ số | Giá trị |
|---|---:|
| Tổng số clip | 7,759 |
| Clip PASS | 7,755 (99.95%) |
| Clip FAIL | 4 (0.05%) |
| Tổng thời lượng audio | ~11.94 giờ |
| Độ dài clip trung bình | 5.54 giây |
| Độ dài clip ngắn nhất | 1.00 giây |
| Độ dài clip dài nhất | 14.99 giây |
| Số episode | 255 |
| Episode PASS 100% clip | 252 / 255 |

**Kết luận nhanh:** Batch đạt chất lượng rất cao — 99.95% clip qua được toàn bộ 10 tiêu chí QC tự động. 4 clip lỗi đều cùng 1 nguyên nhân kỹ thuật (file audio hỏng), không phải lỗi hệ thống lan rộng.

---

## 2. Kết quả theo từng tiêu chí

| # | Tiêu chí | Số clip FAIL | Ghi chú |
|---|---|---:|---|
| 1 | File mở được (`opens_ok`) | 4 | Trùng với 4 clip lỗi chung |
| 2 | Đúng WAV 16kHz mono (`format_ok`) | 4 | Không đọc được nên không xác minh được format |
| 3 | Không rỗng (`empty_ok`) | 4 | Cùng 4 clip trên |
| 4 | Độ dài trong ngưỡng 1–20s (`duration_ok`) | 4 | Cùng 4 clip trên |
| 5 | Transcript không rỗng (`transcript_present`) | 4 | Cùng 4 clip trên |
| 6 | Encoding transcript hợp lệ (`transcript_encoding_ok`) | 4 | Cùng 4 clip trên |
| 7 | Không trùng checksum (`duplicate_ok`) | 4 | Cùng 4 clip trên (không phát sinh duplicate thật nào khác) |
| 8 | Silence ratio hợp lệ (`silence_ok`) | 4 | Cùng 4 clip trên |
| 9 | Không clipping nghiêm trọng (`clipping_ok`) | 4 | Cùng 4 clip trên |
| 10 | Language-ID phù hợp (`lang_ok`) | 4 | Cùng 4 clip trên; 7,755 clip còn lại đều detect đúng `en` |

**Nhận xét:** Cả 10 tiêu chí đều fail đồng thời trên đúng 4 clip — vì bản thân file audio không mở được (`opens_ok = False`), nên toàn bộ các phép đo phía sau (format, duration, silence, clipping...) không thể thực hiện và bị đánh fail theo. Đây **không phải 4 lỗi độc lập**, mà là 1 loại lỗi duy nhất: file hỏng.

Không có clip nào fail vì lý do silence bất thường, clipping nghiêm trọng, ngôn ngữ sai, hay transcript rỗng/lỗi encoding trong số các clip mở được — cho thấy pipeline transcribe và VAD đang hoạt động ổn định.

---

## 3. Danh sách 4 clip FAIL — chi tiết

| Clip | Lỗi |
|---|---|
| `Birds_of_a_Feather_0016.wav` | `System error` khi mở file — nghi ngờ file bị ghi dở/hỏng |
| `How_Do_You_Define_Success_0040.wav` | `System error` khi mở file — nghi ngờ file bị ghi dở/hỏng |
| `State_of_the_Art_Is_the_Best_of_Its_Time_0003.wav` | `System error` khi mở file — nghi ngờ file bị ghi dở/hỏng |
| `State_of_the_Art_Is_the_Best_of_Its_Time_0031.wav` | `System error` khi mở file — nghi ngờ file bị ghi dở/hỏng |

**Nguyên nhân khả dĩ:**
- File bị dừng ghi giữa chừng khi chạy `preprocess_audio.py` (ví dụ máy sleep, mất điện, script bị Ctrl+C giữa lúc `sf.write()`).
- File bị chương trình khác khóa (locked) tại thời điểm QC chạy (ví dụ antivirus quét, hoặc file đang mở bởi ứng dụng khác).

**Hành động đề xuất:** Xóa 4 file lỗi này, chạy lại `preprocess_audio.py` riêng cho 2 episode `Birds_of_a_Feather`, `How_Do_You_Define_Success`, và `State_of_the_Art_Is_the_Best_of_Its_Time` để tái tạo lại clip, sau đó chạy lại QC cho 3 episode này để xác nhận PASS.

---

## 4. Kết quả theo episode

- **252 / 255 episode (98.8%)** có 100% clip PASS.
- **3 episode** có clip FAIL (đều do 4 file lỗi ở mục 3):

| Episode | Clip PASS / Tổng |
|---|---:|
| `State_of_the_Art_Is_the_Best_of_Its_Time` | 43 / 45 |
| `Birds_of_a_Feather` | 35 / 36 |
| `How_Do_You_Define_Success` | 52 / 53 |

Không có episode nào bị loại hoàn toàn (`REJECTED`) — chỉ cần sửa lại đúng các clip lỗi cụ thể.

---

## 5. Chỉ số chất lượng kỹ thuật khác

| Chỉ số | Giá trị trung bình |
|---|---:|
| Tỷ lệ silence trong clip | 21.0% |
| Tỷ lệ sample bị clipping | ~0.0001% (không đáng kể) |
| Ngôn ngữ phát hiện | 100% `en` (trên các clip đọc được) |
| Duplicate (trùng checksum) thật sự | 0 (ngoài 4 clip lỗi không tính) |

Tỷ lệ silence trung bình ~21% là hợp lý với audio dạng bài giảng/đọc kịch bản (VOA Learning English) — có khoảng dừng tự nhiên giữa các câu, không vượt ngưỡng cảnh báo 85%.

---

## 6. Kết luận và bước tiếp theo

- [x] Batch đạt tiêu chuẩn kỹ thuật để chuyển sang bước **kiểm tra thủ công (QC 13.2)** và **REVIEWED_L2**.
- [ ] Cần xử lý 4 clip lỗi trước khi coi 3 episode liên quan là `AUTO_QC_PASSED`.
- [ ] Sau khi sửa xong 4 clip, chạy lại `check_audio_qc.py` để xác nhận 100% PASS trước khi chuyển trạng thái Kanban sang `AUTO_QC_PASSED`.

**Người lập báo cáo:** Thành viên 2
**Ngày:** _(điền ngày chạy QC)_
