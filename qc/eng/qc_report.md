# QC Report

## 1. Tổng quan

- File nguồn: `automatic_checks.csv`
- Tổng số record: **7,752**
- Số trường: **24**
- Duplicate toàn dòng: **0**
- PASS: **0**
- REVIEW_REQUIRED: **7,752**

## 2. Quy tắc audit

Record được đánh dấu `REVIEW_REQUIRED` nếu:
- Có ít nhất một trường bị thiếu.
- Bị duplicate toàn dòng.
- Có trường status/result/check thể hiện trạng thái lỗi.
- Có trường issue/error/fail chứa nội dung lỗi.

Các record còn lại được đánh dấu `PASS`.

## 3. Missing values

| Field | Missing |
|---|---:|
| `clip_path` | 0 |
| `clip_name` | 0 |
| `opens_ok` | 0 |
| `sample_rate` | 0 |
| `channels` | 0 |
| `format_ok` | 0 |
| `duration_s` | 0 |
| `empty_ok` | 0 |
| `duration_ok` | 0 |
| `transcript_present` | 0 |
| `transcript_encoding_ok` | 0 |
| `sha256` | 0 |
| `duplicate_ok` | 0 |
| `duplicate_of` | 7,752 |
| `silence_ratio` | 0 |
| `silence_ok` | 0 |
| `clipping_ratio` | 0 |
| `clipping_ok` | 0 |
| `lang_detected` | 0 |
| `lang_ok` | 0 |
| `overall_pass` | 0 |
| `notes` | 7,752 |
| `mtime` | 0 |
| `size` | 0 |

## 4. Duplicate

Có **0** dòng duplicate toàn bộ.

## 5. File `annotation_audit.csv`

File audit giữ nguyên toàn bộ cột gốc và thêm:

- `audit_missing_fields`: số trường thiếu trong record.
- `audit_duplicate_row`: record có bị duplicate hay không.
- `audit_status_issue`: phát hiện status/result/check báo lỗi.
- `audit_explicit_issue`: phát hiện trường issue/error/fail có nội dung.
- `annotation_audit_status`: kết quả cuối cùng của automatic audit.

## 6. Manual review

Các record `REVIEW_REQUIRED` cần được kiểm tra thủ công trước khi đưa vào dataset chính thức. Đặc biệt kiểm tra:
- Transcript có khớp audio.
- Timestamp có cắt giữa từ hay không.
- Speaker và speaker count.
- Noise/overlap.
- Audio có mở được và đúng chuẩn dataset.
- Source/license evidence.
- Duplicate.
- Các lỗi annotation.

## 7. Giới hạn

Đây là **automatic audit**, không phải đánh giá chất lượng transcript bằng con người. `PASS` chỉ có nghĩa record không kích hoạt các điều kiện audit tự động; không chứng minh transcript hoàn toàn chính xác.

