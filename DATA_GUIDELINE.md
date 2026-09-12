# OneVoice ASR Dataset — Data Guideline

**Project:** OneVoice Glass–Ear Hub
**Dataset:** OneVoice ASR Dataset
**Languages:** English và Mandarin (普通话)
**Pilot target:** 10 giờ English + 10 giờ Mandarin ở trạng thái `RELEASED`
**Dataset version:** `onevoice_asr_dataset_v0.1`

---

## 1. Mục đích

Tài liệu này quy định các tiêu chuẩn thống nhất cho quá trình thu thập, xử lý, segmentation, transcription, metadata, kiểm soát chất lượng (QC) và chia tập dữ liệu của OneVoice ASR Dataset.

Mục tiêu của Data Guideline là đảm bảo dữ liệu:

* Có nguồn gốc rõ ràng và có thể truy xuất.
* Có quyền sử dụng phù hợp.
* Có chất lượng audio đạt yêu cầu.
* Có transcript được kiểm tra độc lập.
* Có metadata đầy đủ.
* Không chứa duplicate hoặc data leakage.
* Có cấu trúc thống nhất để phục vụ training, evaluation và calibration cho ASR.

> **Chỉ tiêu chính là số giờ dữ liệu ở trạng thái `RELEASED`, không phải số giờ đã tải xuống.**

---

# 2. Phạm vi dữ liệu

Dataset bao gồm:

* **English**
* **Mandarin / 普通话**

Mandarin phải được phân biệt với các biến thể/ngôn ngữ khác, đặc biệt là Cantonese.

Dữ liệu có thể bao gồm nhiều loại speech:

* Clean / scripted speech
* Interview
* Press briefing
* Question & Answer
* Spontaneous speech
* Panel / discussion
* Field interview
* Noisy speech
* Dialogue

---

# 3. Quy định về nguồn dữ liệu

## 3.1. Nguyên tắc chung

Mỗi asset phải được kiểm tra quyền sử dụng trước khi được đưa vào quá trình xử lý.

Quy trình:

```text
SOURCE FOUND
    ↓
RIGHTS_REVIEW
    ↓
RIGHTS_APPROVED
    ↓
ACQUIRED
```

Không được đưa dữ liệu trực tiếp vào training dataset nếu chưa qua `RIGHTS_REVIEW`.

## 3.2. YouTube

YouTube chỉ được sử dụng để:

* Tìm kiếm channel.
* Tìm kiếm playlist.
* Xác định episode/video.
* Tham khảo nguồn.

File huấn luyện phải được lấy từ website chính thức hoặc phương thức được chủ sở hữu cho phép.

Không sử dụng Standard YouTube License làm căn cứ mặc định để đưa dữ liệu vào dataset training.

## 3.3. Phân loại quyền sử dụng

Mỗi asset được phân loại thành một trong ba trạng thái:

```text
CORE_APPROVED
RND_NONCOMMERCIAL
REJECTED
```

### CORE_APPROVED

Dữ liệu được phép đưa vào tập lõi theo chính sách quyền sử dụng của dự án.

### RND_NONCOMMERCIAL

Dữ liệu chỉ được sử dụng trong kho nghiên cứu phi thương mại.

Không trộn dữ liệu này vào tập lõi nếu dataset/checkpoint có định hướng thương mại.

### REJECTED

Không được đưa vào dataset.

Các trường hợp cần loại:

* Quyền sử dụng không rõ.
* Nội dung bên thứ ba chưa rõ quyền.
* Nội dung không phù hợp với chính sách nguồn.
* Asset không vượt qua Rights Gate.

## 3.4. Third-party content

Các nội dung có:

* AP
* Reuters
* AFP
* Nhạc thương mại
* Nội dung bên thứ ba chưa rõ quyền

phải được xác định và loại khỏi tập lõi nếu chưa có quyền sử dụng phù hợp.

---

# 4. Quy tắc đặt tên file

## 4.1. Audio file

### English

Tên file sử dụng format:

```text
Eng_[STT].wav
```

Ví dụ:

```text
Eng_1.wav
Eng_2.wav
Eng_1007.wav
```

`STT` là số thứ tự duy nhất của file trong dataset English.

### Mandarin

Tên file sử dụng format:

```text
Zh_[STT].wav
```

Ví dụ:

```text
Zh_1.wav
Zh_2.wav
Zh_1007.wav
```

## 4.2. Quy tắc chung

* Không sử dụng khoảng trắng trong filename.
* Không sử dụng ký tự đặc biệt không cần thiết.
* Không thay đổi filename tùy ý sau khi file đã được đưa vào manifest.
* `clip_id` phải là duy nhất.
* Filename phải ánh xạ 1-1 với `clip_id` hoặc có quy tắc ánh xạ được ghi rõ trong metadata.
* Không sử dụng tên thật của speaker trong filename.

---

# 5. Quy định về Audio

## 5.1. File canonical

Audio sau preprocessing phải có:

```text
Format: WAV
Codec: PCM signed 16-bit
Sample rate: 16 kHz
Channel: Mono
```

Cấu trúc:

```text
audio/
├── raw/
└── processed_16k/
```

File gốc phải được giữ nguyên trong `audio/raw/`.

Không được ghi đè file raw bằng file đã preprocessing.

## 5.2. Audio preprocessing

Các bước chuẩn hóa có thể bao gồm:

1. Kiểm tra file có thể đọc được.
2. Convert sample rate về 16 kHz.
3. Convert channel về mono.
4. Convert về PCM signed 16-bit WAV.
5. Kiểm tra duration.
6. Kiểm tra silence.
7. Kiểm tra clipping.
8. Tạo checksum.

Không áp dụng noise reduction mạnh lên file canonical.

Nếu cần thực hiện noise reduction hoặc các preprocessing khác cho thí nghiệm, phải tạo file dẫn xuất riêng.

---

# 6. Quy tắc Segmentation

Audio dài phải được chia thành các clip phù hợp cho ASR.

## 6.1. Độ dài

| Quy định            |       Giá trị |
| ------------------- | ------------: |
| Tối thiểu           | khoảng 1 giây |
| Độ dài mục tiêu     |     3–12 giây |
| Tối đa thông thường |       20 giây |

## 6.2. Quy tắc cắt

* Không cắt giữa từ.
* Ưu tiên cắt tại ranh giới tự nhiên của speech.
* Giữ khoảng **150–300 ms context** trước và sau speech.
* Mỗi clip ưu tiên có một speaker chính.
* Không ghép lời của hai speaker khác nhau vào cùng một clip.
* Đoạn có overlap phải được gắn nhãn.
* Không sử dụng đoạn overlap như clean ground truth nếu chưa được xác nhận phù hợp.

## 6.3. Segment metadata

Mỗi clip phải lưu:

```text
start_time_ms
end_time_ms
duration_ms
```

Timestamps phải tham chiếu tới audio nguồn.

---

# 7. Quy tắc Speaker

Mỗi speaker phải có một `speaker_id` duy nhất trong dataset.

Ví dụ:

```text
SPK_001
SPK_002
SPK_003
```

Không sử dụng tên thật của speaker làm `speaker_id`.

Metadata phải ghi:

```text
speaker_id
speaker_count
```

Nếu không xác định được speaker, sử dụng giá trị thống nhất do nhóm quy định, ví dụ:

```text
unknown
```

Không tự suy đoán danh tính speaker khi không có bằng chứng.

---

# 8. Quy tắc Transcript

Mỗi clip phải có transcript tương ứng.

Transcript phải phản ánh nội dung speech thực tế trong audio.

## 8.1. Hai phiên bản transcript

Mỗi clip cần có:

```text
text_verbatim
text_normalized
```

### `text_verbatim`

Phản ánh lời nói thực tế trong audio.

Không tự ý thêm hoặc bỏ nội dung speech.

### `text_normalized`

Phiên bản được chuẩn hóa để phục vụ:

* WER
* CER
* Training
* Evaluation

Quy tắc normalization phải được áp dụng thống nhất cho toàn bộ dataset.

---

# 9. Transcript L1 và L2 Review

Mỗi transcript phải trải qua hai lớp:

```text
L1 Annotation
      ↓
L2 Independent Review
      ↓
APPROVED
```

Người thực hiện L1 không được tự duyệt toàn bộ transcript của chính mình ở L2.

## 9.1. English

```text
Member 2 → English L1
Member 3 → English L2
```

## 9.2. Mandarin

```text
Member 3 → Mandarin L1
Member 1 → Mandarin L2
```

Nếu không có ít nhất hai người có khả năng nghe hiểu Mandarin:

* Transcript Mandarin không được coi mặc định là gold label.
* Dữ liệu chỉ nên được xem là weakly labeled training data.
* Development/test cần có người kiểm tra Mandarin độc lập trước khi sử dụng để báo cáo CER.

---

# 10. Transcript Tags

Các tag được sử dụng thống nhất:

```text
[noise]
[music]
[laughter]
[overlap]
[inaudible]
[foreign]
```

Tag phải được sử dụng nhất quán theo quy định của nhóm.

Không tự ý tạo thêm tag mới trong một batch mà không cập nhật Data Guideline.

---

# 11. Metadata

Mỗi clip tối thiểu phải có:

```text
clip_id
source_id
source_organization
source_program
official_asset_url
youtube_reference_url
rights_holder
license_type
license_evidence_path
collection_date

third_party_content
commercial_use_status
redistribution_status

language
language_variant
accent_region

speaker_id
speaker_count
speech_style
environment
noise_level
overlap
code_switching

start_time_ms
end_time_ms
duration_ms

text_verbatim
text_normalized
transcript_source

annotation_status
reviewer_id

audio_sha256
split
dataset_version
```

Các metadata có thể sinh tự động phải được sinh bằng script thay vì nhập thủ công khi có thể.

Ví dụ:

* duration
* sample rate
* channels
* file size
* SHA256
* timestamps
* filename

---

# 12. Quality Control (QC)

QC được chia thành:

```text
Automatic QC
       +
Manual QC
       +
Rights QC
       +
Dataset-level QC
```

Một clip chỉ được chuyển sang `RELEASED` khi vượt qua các bước QC bắt buộc.

---

## 12.1. Rights QC

100% asset phải được kiểm tra.

Kiểm tra:

* Có source rõ ràng.
* Có rights holder.
* Có license information.
* Có license evidence.
* Có official source URL.
* Có xác định được trạng thái commercial use.
* Có xác định được redistribution status.
* Không có quyền sử dụng mơ hồ.

Asset không vượt qua Rights QC:

```text
→ REJECTED
```

hoặc:

```text
→ RND_NONCOMMERCIAL
```

nếu phù hợp.

---

# 13. Automatic Audio QC

Automatic QC phải được chạy trên **100% clip**.

## 13.1. File integrity

Kiểm tra:

* File tồn tại.
* File mở được.
* File không corrupt.
* Audio có duration > 0.
* Có waveform/audio data hợp lệ.

Nếu không đạt:

```text
QC_STATUS = FAIL
```

---

## 13.2. Audio format

Kiểm tra:

```text
Format = WAV
Codec = PCM signed 16-bit
Sample rate = 16000 Hz
Channel = Mono
```

Nếu không đúng:

```text
→ FAIL
```

và phải preprocessing lại hoặc loại clip.

---

## 13.3. Duration QC

Kiểm tra:

* Duration không nhỏ hơn ngưỡng tối thiểu khoảng 1 giây.
* Duration mục tiêu nằm trong khoảng 3–12 giây.
* Duration tối đa thông thường không vượt quá 20 giây.

Các clip nằm ngoài khoảng mục tiêu cần được kiểm tra.

Clip vượt quá giới hạn tối đa thông thường phải:

* segmentation lại, hoặc
* loại nếu không thể segmentation phù hợp.

> **Lưu ý:** kế hoạch hiện tại chưa quy định cách xử lý chính xác đối với clip dưới 1 giây hoặc các trường hợp ngoại lệ >20 giây. Nhóm cần chốt tiêu chí `REJECT / RESEGMENT / ACCEPT_EXCEPTION`.

---

# 14. Silence QC

Kiểm tra tỷ lệ silence của từng clip.

Mục tiêu:

* Clip phải chứa speech.
* Không được là đoạn silence hoàn toàn.
* Không được có tỷ lệ silence bất thường làm ảnh hưởng đến ASR.

Các trường hợp:

```text
Full silence
→ REJECT
```

```text
Excessive silence
→ REVIEW / RESEGMENT
```

> **Thiếu trong kế hoạch hiện tại:** chưa có ngưỡng silence cụ thể, ví dụ `silence_ratio > X%`. Nhóm cần thống nhất ngưỡng trước khi triển khai automatic QC chính thức.

---

# 15. Clipping QC

Kiểm tra amplitude để phát hiện clipping nghiêm trọng.

Nếu audio bị clipping nghiêm trọng:

```text
→ REVIEW
→ REPROCESS hoặc REJECT
```

Không cố gắng sửa clipping bằng preprocessing nếu việc sửa làm thay đổi đáng kể nội dung audio.

> **Thiếu trong kế hoạch:** chưa quy định ngưỡng clipping cụ thể. Cần chốt metric và threshold nếu muốn tự động hóa hoàn toàn.

---

# 16. Duplicate QC

Mỗi audio phải được tạo checksum:

```text
audio_sha256
```

Kiểm tra duplicate trên toàn bộ dataset.

Nếu hai file có cùng checksum:

```text
→ DUPLICATE
```

Chỉ giữ một bản theo quy tắc dedup của dataset.

Ngoài checksum, nếu cần phát hiện cùng nội dung nhưng khác encoding, nhóm có thể bổ sung audio-level similarity check.

---

# 17. Transcript QC

Transcript phải được kiểm tra:

* Không rỗng.
* Khớp nội dung audio.
* Không thiếu từ quan trọng.
* Không tự ý thêm nội dung không xuất hiện trong audio.
* Không có lỗi encoding.
* Đúng ngôn ngữ.
* Đúng speaker.
* Tag được sử dụng đúng.
* `text_verbatim` và `text_normalized` được tạo đúng quy tắc.

Subtitle hoặc auto-caption của YouTube chỉ được dùng làm bản nháp.

**Không sử dụng YouTube auto-caption làm ground truth.**

---

# 18. Language QC

Kiểm tra ngôn ngữ của clip.

English phải là:

```text
language = en
```

Mandarin phải là:

```text
language = zh
language_variant = Mandarin
```

Không đưa:

* Cantonese
* Ngôn ngữ khác
* Đoạn foreign speech không được đánh dấu

vào Mandarin dataset nếu không đáp ứng guideline.

Các đoạn code-switching phải được gắn:

```text
code_switching = true
```

nếu phù hợp.

---

# 19. Speaker / Overlap QC

Kiểm tra:

* `speaker_id` hợp lệ.
* `speaker_count` phù hợp với audio.
* Speaker annotation không mâu thuẫn.
* Không ghép hai speaker khác nhau vào một clip clean.
* Overlap phải được đánh dấu.

Nếu phát hiện speaker khác xuất hiện trong clip:

```text
→ REVIEW
→ RESEGMENT
```

hoặc loại clip nếu không thể sửa.

---

# 20. Metadata QC

100% clip phải có các metadata bắt buộc.

Kiểm tra:

* Không thiếu `clip_id`.
* Không duplicate `clip_id`.
* Filename hợp lệ.
* `audio_sha256` tồn tại.
* `language` hợp lệ.
* `speaker_id` hợp lệ.
* `start_time_ms < end_time_ms`.
* `duration_ms` khớp với timestamps.
* Transcript tồn tại.
* Rights metadata tồn tại.
* `dataset_version` được gán.

---

# 21. Manual QC / Human Audit

Ngoài Automatic QC, phải thực hiện kiểm tra thủ công.

## Training set

* 100% clip có annotation L1.
* Ít nhất 20% clip được kiểm tra L2.
* 100% hard examples phải được nghe lại.
* Các clip có WER/CER bất thường phải được kiểm tra.

Nếu mẫu audit cho thấy chất lượng không đạt, phạm vi audit phải được mở rộng, có thể kiểm tra toàn bộ batch.

## Development set

Development set phải:

* Được kiểm tra L2 **100%**.
* Không sử dụng transcript tự động chưa xác nhận.
* Không chỉnh ground truth chỉ để làm prediction của model tốt hơn.

---

# 22. QC Batch

Dữ liệu được xử lý theo batch khoảng:

```text
30–60 phút audio đã qua Rights Gate
```

Mỗi batch phải có:

```text
source_manifest.csv
rights_evidence/
raw_audio/
processed_audio/
segments.jsonl
transcript_l1.jsonl
transcript_l2.jsonl
qc_report.csv
```

Không chờ đến khi hoàn thành toàn bộ dataset mới QC.

Batch phải được kiểm tra và xử lý lỗi trước khi tiếp tục mở rộng dữ liệu.

---

# 23. Trạng thái QC / Kanban

Mỗi asset/episode sử dụng các trạng thái:

```text
NEW_SOURCE
→ RIGHTS_REVIEW
→ RIGHTS_APPROVED
→ ACQUIRED
→ SEGMENTED
→ ANNOTATED_L1
→ REVIEWED_L2
→ AUTO_QC_PASSED
→ ASR_CHECKED
→ RELEASED
```

Các trạng thái loại:

```text
REJECTED_LICENSE
REJECTED_THIRD_PARTY
REJECTED_AUDIO_QUALITY
REJECTED_TRANSCRIPT
REJECTED_DUPLICATE
REJECTED_LANGUAGE
```

Không asset nào được bỏ qua:

```text
RIGHTS_REVIEW
```

hoặc:

```text
REVIEWED_L2
```

để đi thẳng tới:

```text
RELEASED
```

---

# 24. Tiêu chí RELEASED

Một clip/batch chỉ được `RELEASED` khi:

* [ ] Rights đã được xác nhận.
* [ ] Source có thể truy xuất.
* [ ] License evidence tồn tại.
* [ ] Audio đọc được.
* [ ] Audio đúng WAV PCM16.
* [ ] Sample rate = 16 kHz.
* [ ] Channel = Mono.
* [ ] Duration hợp lệ.
* [ ] Không có silence bất thường chưa được xử lý.
* [ ] Không có clipping nghiêm trọng chưa được xử lý.
* [ ] Không duplicate.
* [ ] Language đúng.
* [ ] Speaker metadata hợp lệ.
* [ ] Transcript L1 hoàn thành.
* [ ] Transcript L2 hoàn thành.
* [ ] Transcript không có lỗi nghiêm trọng.
* [ ] Metadata đầy đủ.
* [ ] SHA256 được tạo.
* [ ] Dataset version được gán.

---

# 25. Train / Development Split

## 25.1. Tỷ lệ

Dataset được chia:

```text
TRAIN = 80%
DEVELOPMENT = 20%
```

Không sử dụng tỷ lệ 90/10.

## 25.2. Nguyên tắc chia

Việc chia dataset phải được thực hiện theo:

* Episode
* Speaker

Không chia ngẫu nhiên từng clip độc lập.

Mục tiêu là tránh:

```text
Speaker A → TRAIN
Speaker A → DEV
```

và:

```text
Episode X → TRAIN
Episode X → DEV
```

trong cùng một ngữ cảnh dữ liệu.

## 25.3. Ví dụ

Không hợp lệ:

```text
Episode A
├── Clip 001 → TRAIN
├── Clip 002 → TRAIN
└── Clip 003 → DEV
```

Hợp lệ:

```text
Episode A
├── Clip 001 → TRAIN
├── Clip 002 → TRAIN
└── Clip 003 → TRAIN

Episode B
├── Clip 004 → DEV
├── Clip 005 → DEV
└── Clip 006 → DEV
```

Nếu dataset có thể đảm bảo speaker-disjoint:

```text
Speaker 001 → TRAIN
Speaker 002 → TRAIN
Speaker 003 → TRAIN

Speaker 004 → DEV
Speaker 005 → DEV
```

## 25.4. Calibration Set

Calibration set phục vụ ONNX/QNN quantization phải được lấy từ:

```text
TRAIN
```

Không lấy calibration data từ Development set.

Calibration set nên đại diện cho nhiều điều kiện:

* Clean speech
* Interview
* Dialogue
* Noisy speech
* Short clips
* Long clips
* Các speaker khác nhau
* Các speech style khác nhau

---

# 26. Data Leakage

Không được để cùng một nội dung hoặc speaker xuất hiện ở cả TRAIN và DEV theo cách tạo leakage.

Phải kiểm tra:

```text
Speaker leakage
Episode leakage
Duplicate leakage
Source-content leakage
```

Đặc biệt phải kiểm tra SHA256 và metadata trước khi cố định split.

---

# 27. Dataset Release

Trước khi phát hành:

1. Chạy final automatic QC.
2. Hoàn thành manual audit.
3. Kiểm tra duplicate.
4. Kiểm tra speaker/episode leakage.
5. Kiểm tra train/dev split.
6. Kiểm tra rights manifest.
7. Kiểm tra metadata.
8. Chạy baseline ASR.
9. Tính WER English.
10. Tính CER Mandarin.
11. Phân tích lỗi.
12. Cố định calibration manifest.
13. Cập nhật Data Card.
14. Cập nhật Attribution.
15. Cập nhật Changelog.
16. Tạo release report.
17. Tạo checksum cho release.

Version pilot:

```text
onevoice_asr_dataset_v0.1
```

---

# 28. QC Metrics cần lưu

File QC nên lưu tối thiểu:

```text
clip_id
filename
file_readable
format_valid
sample_rate_valid
channel_valid
duration_valid
silence_check
clipping_check
duplicate_check
language_check
transcript_present
transcript_l1_status
transcript_l2_status
metadata_complete
rights_status
qc_status
rejection_reason
reviewer_id
```

Mỗi clip phải có kết quả:

```text
PASS
```

hoặc:

```text
FAIL
```

Nếu `FAIL`, phải ghi rõ:

```text
rejection_reason
```

---

# 29. Rejection Criteria

Clip phải được xem xét loại nếu thuộc một trong các trường hợp:

### Rights

* Không xác định được quyền sử dụng.
* License không phù hợp.
* Có third-party content chưa rõ quyền.

### Audio

* File corrupt.
* Không có speech.
* Silence bất thường.
* Duration không phù hợp và không thể segmentation lại.
* Clipping nghiêm trọng.
* Không thể chuẩn hóa về canonical format.

### Transcript

* Transcript không khớp audio.
* Transcript không thể xác minh.
* Có lỗi nghiêm trọng không thể sửa.

### Language

* Sai ngôn ngữ.
* Không phải Mandarin nhưng được gắn Mandarin.
* Foreign speech không được xử lý theo guideline.

### Duplicate

* Trùng audio.
* Trùng nội dung đã tồn tại trong dataset.

### Metadata

* Thiếu thông tin bắt buộc và không thể bổ sung.

---

# 30. Những trường hợp cần REVIEW thay vì tự động REJECT

Không phải mọi lỗi đều phải loại ngay.

Các trường hợp cần human review:

* Noise cao nhưng speech vẫn rõ.
* Một phần silence dài.
* Có overlap.
* Có laughter.
* Có music background.
* Code-switching.
* Clip dài hơn mục tiêu nhưng vẫn có thể sử dụng.
* Clipping nhẹ.
* Speaker không chắc chắn.
* Transcript có từ không rõ.

Reviewer phải quyết định:

```text
ACCEPT
RESEGMENT
REANNOTATE
REPROCESS
REJECT
```

---

# 31. Những điều cấm

1. Không tải nguồn rồi đưa thẳng vào thư mục train.
2. Không scrape YouTube hàng loạt để thay cho quy trình quyền sử dụng.
3. Không dùng YouTube auto-caption làm ground truth.
4. Không trộn CC BY-NC vào tập lõi có định hướng thương mại.
5. Không để một người vừa gán nhãn vừa tự duyệt toàn bộ batch của mình.
6. Không chia train/dev ngẫu nhiên theo clip.
7. Không xóa file gốc sau khi chuẩn hóa.
8. Không sửa transcript để prediction của ASR trở nên tốt hơn.
9. Không dùng tên thật làm `speaker_id`.
10. Không tính số giờ đã tải là số giờ hoàn thành.
11. Không fine-tune trên dataset chưa được đóng phiên bản.
12. Không thay calibration set giữa các lần benchmark mà không ghi nhận.

---

# 32. Checklist cuối cùng

## Source & Rights

* [ ] Source được xác định.
* [ ] Official source URL tồn tại.
* [ ] Rights holder được xác định.
* [ ] License được xác định.
* [ ] License evidence được lưu.
* [ ] Third-party content được kiểm tra.
* [ ] Asset vượt Rights Gate.

## Audio

* [ ] WAV.
* [ ] PCM signed 16-bit.
* [ ] 16 kHz.
* [ ] Mono.
* [ ] File đọc được.
* [ ] Duration hợp lệ.
* [ ] Không full silence.
* [ ] Không clipping nghiêm trọng.

## Segmentation

* [ ] Segment không cắt giữa từ.
* [ ] Duration phù hợp.
* [ ] Context 150–300 ms.
* [ ] Speaker chính được xác định.
* [ ] Overlap được đánh dấu.

## Transcript

* [ ] L1 hoàn thành.
* [ ] L2 hoàn thành.
* [ ] `text_verbatim`.
* [ ] `text_normalized`.
* [ ] Language đúng.
* [ ] Không lỗi nghiêm trọng.
* [ ] Tags được sử dụng đúng.

## Metadata

* [ ] `clip_id`.
* [ ] Source information.
* [ ] Rights information.
* [ ] Language.
* [ ] Speaker.
* [ ] Speech condition.
* [ ] Timestamps.
* [ ] Transcript.
* [ ] SHA256.
* [ ] Split.
* [ ] Dataset version.

## Dataset

* [ ] Duplicate check.
* [ ] Speaker leakage check.
* [ ] Episode leakage check.
* [ ] Train = 80%.
* [ ] Dev = 20%.
* [ ] Calibration set lấy từ Train.
* [ ] Development set được L2 review 100%.

## Release

* [ ] 10h English `RELEASED`.
* [ ] 10h Mandarin `RELEASED`.
* [ ] WER English.
* [ ] CER Mandarin.
* [ ] Error analysis.
* [ ] Calibration manifest.
* [ ] Data Card.
* [ ] Attribution.
* [ ] Changelog.
* [ ] Release report.
* [ ] Release checksum.

---

# 33. Các quy định cần nhóm chốt bổ sung

Kế hoạch hiện tại đã đủ để xây dựng quy trình tổng thể, nhưng **chưa quy định một số threshold kỹ thuật cụ thể**. Trước khi viết script QC chính thức, nhóm nên chốt:

1. **Silence threshold**

   * Bao nhiêu % silence thì `REVIEW`?
   * Bao nhiêu % thì `REJECT`?

2. **Clipping threshold**

   * Metric nào sử dụng?
   * Bao nhiêu % samples bị clipping thì reject?

3. **Duration exception**

   * Clip <1 giây xử lý thế nào?
   * Clip >20 giây có cho phép exception không?

4. **Transcript accuracy threshold**

   * Mẫu audit bao nhiêu %?
   * Bao nhiêu lỗi trong mẫu thì phải audit lại toàn batch?
   * Thế nào được coi là “lỗi nghiêm trọng”?

5. **Noise threshold**

   * Noise level chỉ annotate `low/medium/high` hay có metric SNR cụ thể?

6. **Speaker policy**

   * Có cho phép clip có `speaker_count > 1` không?
   * Nếu có, overlap xử lý thế nào?

7. **Normalization rules**

   * Cách xử lý số.
   * Abbreviation.
   * Punctuation.
   * Proper nouns.
   * Contractions trong English.
   * Simplified/Traditional Chinese.
   * English words xuất hiện trong Mandarin.

8. **Dataset-wide speaker split**

   * Có bắt buộc speaker-disjoint 100% giữa Train/Dev không?
   * Hay chỉ bắt buộc episode-disjoint?

9. **Duplicate detection nâng cao**

   * Chỉ dùng SHA256?
   * Hay thêm audio fingerprint để phát hiện cùng nội dung nhưng khác encoding?

Các mục trên **chưa được quy định đủ rõ trong file kế hoạch gốc**, vì vậy nên chốt trước khi triển khai QC tự động.
