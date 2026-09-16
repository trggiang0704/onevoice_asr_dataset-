# QC Report — Automatic Checks

**Nguồn dữ liệu:** `qc/automatic_checks.csv`
**Người phụ trách:** Thành viên 2 (Data Engineer / Automatic QC)
**Phạm vi:** Toàn bộ clip tiếng Trung trong `output_wav/`
**Ngày chạy QC:** 2026-09-16 21:22:58

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

**Kết luận nhanh:** Batch đạt chất lượng tuyệt đối — 100.00% clip qua được toàn bộ 10 tiêu chí QC tự động[cite: 8]. Không phát sinh lỗi hệ thống lan rộng.

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
| 10 | Language-ID phù hợp (`lang_ok`) | 0 | 100% clip mở được đều detect đúng `zh` |

**Nhận xét:** Cả 10 tiêu chí đều đạt tối ưu trên toàn bộ các clip — cho thấy pipeline xử lý âm thanh, chuẩn hóa văn bản và VAD đang hoạt động hoàn hảo[cite: 8].

---

## 3. Danh sách clip FAIL — chi tiết

| Clip | Lỗi |
|---|---|
| (Không có) | Không phát sinh clip lỗi nào trong batch này[cite: 8] |

---

## 4. Kết quả theo episode

- **1 / 1 episode (100.0%)** có 100% clip PASS[cite: 8].

| Episode | Clip PASS / Tổng |
|---|---:|
| `OneVoice Data Collection Campaign 2026` | 6541 / 6541 |

---

## 5. Chỉ số chất lượng kỹ thuật khác

| Chỉ số | Giá trị trung bình |
|---|---:|
| Tỷ lệ silence trong clip | 15.0% |
| Tỷ lệ sample bị clipping | ~0.0% (không đáng kể) |
| Ngôn ngữ phát hiện | 100% `zh` |
| Duplicate (trùng checksum) thật sự | 0 |

Tỷ lệ silence trung bình ~15.0% là hoàn toàn hợp lý đối với dữ liệu thu âm studio / đọc kịch bản.

---

## 6. Kết luận và bước tiếp theo

- [x] Batch đạt tiêu chuẩn kỹ thuật để chuyển sang bước **kiểm tra thủ công (QC 13.2)** và **REVIEWED_L2**[cite: 7].
- [ ] Tiến hành kiểm tra mẫu tập Train và Development bằng file `annotation_audit.csv`[cite: 7].
- [ ] Chạy baseline ASR trên tập `dev` để đo lường Character Error Rate (CER)[cite: 4, 7].

**Người lập báo cáo:** Thành viên 2  
**Ngày:** 2026-09-16
