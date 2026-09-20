# OneVoice ASR Dataset (OneVoice-ASR)

## Dataset Description

**OneVoice ASR Dataset** là tập dữ liệu huấn luyện và đánh giá nhận dạng tiếng nói tự động (**Automatic Speech Recognition - ASR**) đa ngôn ngữ chuẩn hóa, tập trung vào hai ngôn ngữ chính:

- Tiếng Anh (**English - en-US**)
- Tiếng Quan Thoại (**Mandarin - zh-CN**)

Tập dữ liệu được xây dựng nhằm giải quyết nhu cầu về dữ liệu âm thanh có độ phân giải cao, nguồn gốc rõ ràng, quyền sở hữu minh bạch và chất lượng phiên âm được kiểm chứng nghiêm ngặt phục vụ nghiên cứu và triển khai mô hình ASR.

Với quy mô **14.296 đoạn âm thanh (~22,40 giờ)** được chuẩn hóa định dạng **WAV PCM 16-bit, 16 kHz Mono**, tập dữ liệu bao quát nhiều điều kiện âm học thực tế từ giọng đọc rõ chuẩn (*scripted speech*), phỏng vấn, họp báo ngoại giao, cho đến môi trường thực địa có tiếng ồn phức tạp.

Dữ liệu thích hợp cho:

- Tiền huấn luyện (*pre-training*)
- Tinh chỉnh (*fine-tuning*)
- Kiểm thử đối chuẩn (*benchmarking*)
- Cân chỉnh lượng tử hóa mô hình (*quantization calibration*)

---

# Dataset Link

**OneVoice ASR Dataset Repository**

---

# Data Card Author(s)

| Name | Role | Organization |
|---|---|---|
| Trần Trường Giang | Owner / Data Lead | AIoT Lab |
| Triệu Quốc Anh | Contributor / English Data Curator | AIoT Lab |
| Nguyễn Văn Huy | Contributor / Mandarin Data Curator | AIoT Lab |

---

# Authorship

## Publishers

### Publishing Organization(s)

- AIoT Lab

### Industry Type(s)

- Academic - Tech
- Corporate - Tech

### Contact Detail(s)

- **Publishing POC:** Trần Trường Giang
- **Affiliation:** AIoT Lab
- **Contact:** trggiang107@gmail.com (hoặc qua Google Drive repository)

---

# Dataset Owners

## Team(s)

**OneVoice Glass–Ear Hub / Speech Data Team (AIoT Lab)**

### Contact Detail(s)

- **Dataset Owner(s):** Trần Trường Giang, Triệu Quốc Anh, Nguyễn Văn Huy
- **Affiliation:** AIoT Lab
- **Contact:** trggiang107@gmail.com

---

# Author(s)

- **Trần Trường Giang**, Data Lead, AIoT Lab, 2026
- **Triệu Quốc Anh**, English Data Curator, AIoT Lab, 2026
- **Nguyễn Văn Huy**, Mandarin Data Curator, AIoT Lab, 2026

---

# Funding Sources

## Institution(s)

**AIoT Lab Internal Research & Development Fund**

## Funding or Grant Summary(ies)

Dự án được tài trợ và hỗ trợ hạ tầng thử nghiệm tính toán bởi AIoT Lab thuộc khuôn khổ nghiên cứu các giải pháp ASR tối ưu hóa cho thiết bị nhúng và thiết bị đeo thông minh (**Glass–Ear Hub Project**).

> **Additional Notes:** Không có can thiệp thương mại hạn chế quyền sử dụng học thuật.

---

# Dataset Overview

## Data Subject(s)

- **Non-Sensitive Data about people:** Giọng nói nơi công cộng, bài giảng, họp báo, thu âm cộng đồng tự nguyện.
- **Data about systems or products and their behaviors:** Thử nghiệm hệ thống ASR nhúng/biên.

---

# Dataset Snapshot

| Category | Data |
|---|---|
| **Size of Dataset** | ~2,400 MB (Toàn bộ Audio 16kHz WAV + JSONL + Manifests) |
| **Total Duration** | 22.40 giờ (80,628.58 giây) |
| **Number of Instances** | 14,296 clips |
| **Number of Fields** | 34 trường metadata trên mỗi clip |
| **Labeled Classes** | 2 ngôn ngữ chính (en, zh) bao gồm 3 biến thể giọng (en-US, zh-CN, zh-TW) |
| **Number of Unique Speakers** | 644 người nói định danh (`speaker_id`) |
| **Average Duration Per Instance** | 5.64 giây (dao động từ 1.004s đến 20.00s) |
| **Algorithmic Labels** | Tự động sinh `duration_ms`, `audio_sha256`, `lang_detected`, `silence_ratio`, `clipping_ratio` |
| **Human Labels** | 100% transcript đã qua kiểm duyệt hai lớp (L1 Annotation + L2 Review) |
| **Other Characteristics** | 16 kHz Mono, 16-bit PCM Signed WAV chuẩn hóa |

> **Above:** Bảng tóm tắt các thuộc tính kỹ thuật snapshot của OneVoice ASR Dataset v1.0.

### Additional Notes

Bộ dữ liệu bao gồm:

- **7,755 clip tiếng Anh** (~11.94 giờ)
- **6,541 clip tiếng Quan Thoại** (~10.45 giờ)

---

# Content Description

Mỗi mẫu dữ liệu bao gồm một file audio clip định dạng `.wav` cắt ngắn (segment 1–20 giây) đi kèm một bản ghi JSONL chi tiết chứa:

- Định danh người nói (`speaker_id`)
- Nguồn gốc xuất xứ (`source_organization`)
- Trạng thái bản quyền (`license_type`, `commercial_use_status`)
- Văn bản phiên âm nguyên văn (`text_verbatim`)
- Văn bản chuẩn hóa ASR (`text_normalized`)

> **Additional Notes:** Tập dữ liệu loại bỏ hoàn toàn các clip chứa nội dung bên thứ 3 không rõ bản quyền, âm nhạc thương mại hoặc clip có chất lượng âm thanh lỗi (clipping nặng, full silence).

---

# Descriptive Statistics

| Statistic | duration_ms | duration_s | speaker_count | start_time_ms | end_time_ms |
|---|---:|---:|---:|---:|---:|
| **count** | 14,296 | 14,296 | 14,282 | 14,296 | 14,296 |
| **mean** | 5,639.94 | 5.64 | 1.01 | 0.00 | 5,639.94 |
| **std** | 3,222.01 | 3.22 | 0.10 | 0.00 | 3,222.01 |
| **min** | 1,004.00 | 1.00 | 1.00 | 0.00 | 1,004.00 |
| **25%** | 3,436.00 | 3.44 | 1.00 | 0.00 | 3,436.00 |
| **50%** | 4,876.00 | 4.88 | 1.00 | 0.00 | 4,876.00 |
| **75%** | 6,828.00 | 6.83 | 1.00 | 0.00 | 6,828.00 |
| **max** | 20,000.00 | 20.00 | 3.00 | 0.00 | 20,000.00 |
| **mode** | 3,660.00 | 3.66 | 1.00 | 0.00 | 3,660.00 |

> **Above:** Phân phối thống kê mô tả của các trường giá trị định lượng trong tập dữ liệu.

### Additional Notes

99.8% các clip có chính xác 1 người nói chủ đạo; các trường hợp 2–3 người nói là các đoạn hội thoại phỏng vấn hoặc turn-taking ngắn đã được gắn thẻ.

---

# Sensitivity of Data

## Sensitivity Type(s)

- **Anonymous Data:** Giọng đọc cộng đồng Mozilla không lưu danh tính cá nhân.
- **Pseudonymous Data:** Gán ID người nói như `SPK_001`, không dùng tên thật.
- **None:** Không chứa thông tin định danh cá nhân nhạy cảm S/PII, tài chính hay y tế.

## Field(s) with Sensitive Data

### Intentional Collected Sensitive Data

Không chủ đích thu thập bất kỳ trường thông tin S/PII nào.

### Unintentionally Collected Sensitive Data

| Field Name | Description |
|---|---|
| `speaker_id` | Mã giả danh định danh đặc trưng giọng nói (voiceprint) của người nói, không liên kết với thông tin cá nhân đời thực. |
| `text_verbatim` | Có thể xuất hiện tên nhân vật của công chúng hoặc địa danh trong các bài phát biểu/tin tức họp báo ngoại giao (ví dụ: tên Tổng thống, Bộ trưởng). |

> **Additional Notes:** Toàn bộ tên cá nhân xuất hiện trong bài nói là nhân vật chính trị/công chúng trong họp báo công khai (U.S. Department of State, VOA).

---

# Security and Privacy Handling

### Methods

#### Pseudonymization

Tên thật của diễn giả bị loại bỏ hoàn toàn khỏi metadata và filename, thay bằng định danh dạng `SPK_XXX`.

#### License/Consent Verification

Chỉ tiếp nhận các nguồn cho phép chia sẻ công khai hoặc nguồn có sự đồng ý của người tham gia (Mozilla Common Voice Voice Consent).

> **Additional Notes:** Không thực hiện bất kỳ hoạt động dò quét sinh trắc học để nhận dạng ngược danh tính người nói.

---

# Risk Type(s)

**No Known Risks**

Dữ liệu hoàn toàn dựa trên nguồn phát hành công cộng và nguồn đóng góp mở.

## Supplemental Link(s)

- **Source Policy:** Tham chiếu tài liệu `SOURCE_POLICY.md`
- **Data Guideline:** Tham chiếu tài liệu `DATA_GUIDELINE.md`

## Risk(s) and Mitigation(s)

### Voiceprint Recovery

Diễn giả lo ngại nhận diện giọng nói → Giữ nguyên mã giả danh, chỉ trích xuất cho mục đích huấn luyện học máy ASR.

### Third-Party Copyright Infringement

Rủi ro vi phạm bản quyền khi thu thập từ internet → Áp dụng quy trình Rights Gate đa lớp, loại bỏ các clip chứa hãng thông tấn thứ 3 (AP, Reuters, AFP) và nhạc nền thương mại.

> **Additional Notes:** Dữ liệu hoàn toàn tuân thủ đạo đức nghiên cứu AI.

---

# Dataset Version and Maintenance

## Maintenance Status

**Actively Maintained**

Tập dữ liệu duy trì chủ động; phiên bản hiện tại v1.0 được sửa lỗi kỹ thuật, cập nhật metadata, bổ sung audit transcript và không thay đổi cấu trúc cốt lõi.

## Version Details

- **Current Version:** v1.0 (Giai đoạn chuyển tiếp từ Pilot `onevoice_asr_dataset_v0.1`)
- **Last Updated:** 09/2026
- **Release Date:** 09/2026

## Maintenance Plan

- **Versioning:** Áp dụng Semantic Versioning (`v1.0`, `v1.1`, `v2.0`). Tăng minor version khi sửa lỗi transcript hoặc cập nhật metadata; tăng major version khi mở rộng số giờ hoặc thêm ngôn ngữ.
- **Updates:** Rà soát và cập nhật định kỳ các trường manifest bị thiếu hoặc có lỗi chuẩn hóa văn bản.
- **Errors:** Thu nhận phản hồi lỗi phiên âm thông qua repository issue tracker hoặc qua email nhóm phát triển.
- **Feedback:** Tiếp nhận qua kênh liên hệ của AIoT Lab.

> **Additional Notes:** Mọi thay đổi phiên bản đều được ghi chép vào `CHANGELOG.md`.

---

# Next Planned Update(s)

| Field | Value |
|---|---|
| **Version affected** | v1.0 |
| **Next data update** | 10/2026 |
| **Next version** | v1.1 |
| **Next version update** | 10/2026 |

## Expected Change(s)

### Updates to Data

Hoàn tất rà soát thủ công 100% đối với 7,752 bản ghi có cảnh báo `REVIEW_REQUIRED` từ automatic QC report để đưa tỷ lệ `overall_pass` lên tuyệt đối.

### Updates to Dataset

Bổ sung thêm các trường đo lường SNR tự động và cập nhật calibration manifest phục vụ ONNX/QNN quantization.

> **Additional Notes:** Bản cập nhật T10/2026 sẽ chốt danh sách lỗi transcript của các clip khó (*hard examples*) phát hiện trong đợt thử nghiệm Whisper và SenseVoice.

---

# Example of Data Points

## Primary Data Modality

**Audio Data** (kèm nhãn văn bản Text tương ứng)

## Sampling of Data Points

- **Demo Link:** `Eng_000336.wav` & `zh_000669.wav` trong thư mục Drive
- **Typical Data Point Link:** Tham khảo clip `Eng_000336` trong `train.jsonl`
- **Outlier Data Point Link:** Tham khảo clip `Eng_007433` (WER cao, mẫu khó)

---

# Data Fields

| Field Name | Field Value (Ví dụ) | Description |
|---|---|---|
| `clip_id` | `"Eng_000336"` | Mã định danh duy nhất của audio clip |
| `source_organization` | `"VOA Learning English"` | Tổ chức phát hành nguồn âm thanh |
| `license_type` | `"Public Domain"` | Giấy phép bản quyền của tài sản âm thanh |
| `language` | `"en"` | Mã ngôn ngữ theo chuẩn ISO-639-1 (en hoặc zh) |
| `language_variant` | `"en-US"` | Biến thể ngôn ngữ chi tiết (en-US, zh-CN) |
| `speaker_id` | `"AI_Hallucinate..._SPK1"` | Mã định danh người nói |
| `speaker_count` | `1` | Số lượng người nói xuất hiện trong clip |
| `speech_style` | `"formal"` | Phong cách nói (formal, interview, spontaneous, ...) |
| `duration_ms` | `3660` | Độ dài clip tính theo mili-giây |
| `text_verbatim` | `"As the year 2023 comes..."` | Lời thoại phiên âm nguyên văn |
| `text_normalized` | `"As the year 2023 comes..."` | Lời thoại đã qua chuẩn hóa phục vụ huấn luyện/tính WER |
| `audio_sha256` | `"1c5e8bc096f3b25a..."` | Mã băm SHA256 chống trùng lặp dữ liệu |
| `split` | `"train"` | Tập phân chia dữ liệu (train hoặc development) |

> **Above:** Danh mục các trường dữ liệu tiêu biểu trong file manifest `train.jsonl` và `dev.jsonl`.

> **Additional Notes:** Mỗi bản ghi gồm 34 thuộc tính hỗ trợ truy xuất nguồn gốc đến từng URL và văn bản bằng chứng cấp phép.

---

# Typical Data Point

Một điểm dữ liệu điển hình là clip đơn thoại, thời lượng từ 3–8 giây, âm thanh sạch, phát âm chuẩn, phiên âm khớp chính xác với âm thanh.

## JSON

```json
{
  "clip_id": "Eng_000336",
  "source_id": "voa-learning-english-youtube",
  "source_organization": "VOA Learning English",
  "source_program": "AI_Hallucinate_Authentic_or_Rizz_for_Wor",
  "official_asset_url": "https://learningenglish.voanews.org/",
  "rights_holder": "Voice of America (VOA)",
  "license_type": "Public Domain",
  "license_evidence_path": "licenses/voa_learning_english/license_evidence.txt",
  "language": "en",
  "language_variant": "en-US",
  "accent_region": "US",
  "speaker_id": "AI_Hallucinate_Authentic_or_Rizz_for_Wor_SPK1",
  "speaker_count": 1,
  "speech_style": "formal",
  "noise_level": "low",
  "overlap": false,
  "code_switching": false,
  "duration_ms": 3660,
  "text_verbatim": "As the year 2023 comes to a close,",
  "text_normalized": "As the year 2023 comes to a close,",
  "split": "train",
  "dataset_version": "v1"
}
```

---

# Atypical Data Point

Một điểm dữ liệu dị biệt (*atypical/hard outlier*) là đoạn âm thanh có chứa hiện tượng turn-taking (nhiều người nói xen kẽ), thời lượng dài (>12s), hoặc chứa nhiều thuật ngữ khó gây lỗi nhận dạng.

## JSON

```json
{
  "clip_id": "Eng_000430",
  "source_id": "voa-learning-english-youtube",
  "source_organization": "VOA Learning English",
  "source_program": "An_Eye_for_an_Eye",
  "official_asset_url": "https://learningenglish.voanews.org/",
  "rights_holder": "Voice of America (VOA)",
  "license_type": "Public Domain",
  "language": "en",
  "language_variant": "en-US",
  "speaker_id": "An_Eye_for_an_Eye_SPK2",
  "speaker_count": 1,
  "speech_style": "formal",
  "noise_level": "low",
  "overlap": false,
  "duration_ms": 12460,
  "text_verbatim": "Well, he scratched up the paint on her car last week. I'm still friends with Diana and she told me a security camera caught him doing it. It cost her hundreds of dollars to repaint her car.",
  "split": "train",
  "dataset_version": "v1"
}
```

---

# Motivations & Intentions

## Motivations

### Purpose(s)

- **Research:** Nghiên cứu mô hình ASR gọn nhẹ đa ngôn ngữ.
- **Production:** Phục vụ tích hợp ASR trên thiết bị thông minh AIoT Edge.

### Domain(s) of Application

- Automatic Speech Recognition
- Edge AI
- Speech-to-Text
- Acoustic Modeling
- Quantization Calibration

### Motivating Factor(s)

- Khắc phục sự thiếu hụt các tập dữ liệu ASR song ngữ Anh - Trung có kèm chứng chỉ bản quyền sạch, phân tách speaker rõ ràng và không bị rò rỉ dữ liệu (*data leakage*).
- Cung cấp tập dữ liệu hiệu chuẩn chuẩn xác cho quá trình lượng tử hóa mô hình ASR (INT8/FP16) trên chip NPU/DSP (Qualcomm QNN / ONNX Runtime).

---

# Intended Use

## Dataset Use(s)

- Safe for production use (Các nhánh sử dụng nguồn Public Domain và CC BY tương thích)
- Safe for research use

## Suitable Use Case(s)

- **Suitable Use Case:** Huấn luyện và tinh chỉnh các mô hình nhận dạng giọng nói ASR tiếng Anh và tiếng Trung (như Whisper, Conformer, SenseVoice).
- **Suitable Use Case:** Đánh giá benchmark độ chính xác nhận dạng (WER/CER) trên dữ liệu hội thoại thực tế.
- **Suitable Use Case:** Tạo tập cân chỉnh lượng tử hóa (*Calibration dataset*) cho bộ suy luận tăng tốc phần cứng.

> **Additional Notes:** Sử dụng tối ưu cho các bài toán nhận dạng giọng nói từ trường gần đến trường trung bình.

## Unsuitable Use Case(s)

- **Unsuitable Use Case:** Hệ thống xác thực sinh trắc học cá nhân dựa trên giọng nói (Voice Biometrics Authentication) vì dữ liệu đã bị ẩn danh/giả danh hóa.
- **Unsuitable Use Case:** Ứng dụng thương mại độc quyền đối với các phân vùng dữ liệu thuộc giấy phép phi thương mại (R&D Non-Commercial) nếu có phát sinh trong tương lai.

> **Additional Notes:** Không sử dụng cho các mục đích giả mạo giọng nói (voice spoofing/deepfake).

---

# Research and Problem Space(s)

Tối ưu hóa độ chính xác ASR song ngữ trong điều kiện tài nguyên phần cứng giới hạn (*low-latency edge devices*), giảm hiện tượng hallucination và nhận diện sai từ đồng âm trong tiếng Trung/tiếng Anh.

---

# Citation Guidelines

## Guidelines & Steps

Khi sử dụng tập dữ liệu OneVoice ASR trong các công bố khoa học hoặc sản phẩm kỹ thuật, vui lòng trích dẫn theo định dạng BibTeX dưới đây:

### BibTeX

```bibtex
@misc{onevoice_asr_2026,
  title={OneVoice ASR Dataset: A Bilingual Benchmark for English and Mandarin Edge Speech Recognition},
  author={Tran, Truong Giang and Trieu, Quoc Anh and Nguyen, Van Huy},
  institution={AIoT Lab},
  year={2026},
  url={https://drive.google.com/drive/folders/1NN5T3LlRT_WRkqtf65XMKGygPhmNEGhG}
}
```

---

# Access, Retention, & Wipeout

## Access

### Access Type

**External - Open Access**

Truy cập mở thông qua Google Drive repository có kiểm soát quyền tải.

### Documentation Link(s)

- **Dataset Storage:** Google Drive Workspace
- **Tài liệu quy chuẩn nội bộ:** `DATA_GUIDELINE.md` và `SOURCE_POLICY.md`

### Prerequisite(s)

Đọc và tuân thủ các điều khoản về quyền tác giả và nguồn gốc giấy phép ghi trong `SOURCE_POLICY.md` và `ATTRIBUTION.md`.

### Policy Link(s)

- Creative Commons Attribution 4.0 International (CC BY 4.0)
- U.S. Government Work Public Domain Policy

### Access Control List(s)

**Public Read Access:** Cho phép nhà nghiên cứu tải manifest và audio phục vụ huấn luyện phi lợi nhuận.

---

# Retention

## Duration

Lưu trữ vĩnh viễn (*Indefinite*) cho mục đích nghiên cứu học thuật và duy trì đối chuẩn benchmark.

## Policy Summary

- **Retention Plan ID:** `RET-AIOT-ASR-V1`
- **Summary:** Tập dữ liệu gốc và các bản phát hành được lưu trữ trên hệ thống lưu trữ phân tán của AIoT Lab kèm bản sao lưu trên cloud storage.

## Process Guide

Dữ liệu canonical được khóa quyền ghi (read-only), toàn bộ thay đổi phiên bản phải thông qua pull request và thẩm định QC.

---

# Exception(s) and Exemption(s)

**Exemption Code:** `PUBLIC_DATA / ANONYMOUS_DATA`

---

# Wipeout and Deletion

## Duration

Thực hiện trong vòng 30 ngày kể từ khi nhận được yêu cầu hợp lệ từ chủ sở hữu bản quyền hoặc người nói.

## Deletion Event Summary

Sequence of deletion and processing events:

1. Tiếp nhận và thẩm tra yêu cầu gỡ bỏ (*Takedown request*).
2. Xác định `clip_id`, `speaker_id` hoặc URL tài sản liên quan.
3. Xóa bỏ file âm thanh khỏi thư mục phát hành và loại bỏ dòng dữ liệu trong file manifest của bản cập nhật tiếp theo.

## Acceptable Means of Deletion

Xóa vĩnh viễn file vật lý trên lưu trữ máy chủ và cập nhật blacklist loại trừ trong mã băm SHA256.

## Post-Deletion Obligations

Thông báo cho bên yêu cầu; phát hành thông cáo phiên bản mới cập nhật loại trừ mẫu dữ liệu bị khiếu nại.

---

# Provenance

## Collection Method(s) Used

- API
- Taken from other existing datasets (Mozilla Common Voice)
- Scraped or Crawled (Official portals VOA, U.S. State Dept, NASA)

## Methodology Detail(s)

- **Collection Type:** Thu thập từ cổng thông tin phát thanh công cộng và kho dữ liệu tiếng nói mở.
- **Platform:** VOA Learning English, US State Dept Briefings, Mozilla Data Collective, NASA Media Portal.
- **Dates of Collection:** 08/2026 – 09/2026
- **Primary modality of collection data:** Audio Data
- **Update Frequency for collected data:** Static (được cố định theo từng bản release)

---

# Source Description(s)

### VOA Learning English

Nguồn phát thanh tiếng Anh giọng Mỹ chuẩn, tốc độ vừa phải, âm thanh sạch.

### U.S. Department of State

Họp báo ngoại giao, chứa đối thoại tương tác tự nhiên, turn-taking, nhiều ngữ điệu quốc tế.

### Mozilla Data zh-CN

Dữ liệu thu âm tiếng Quan Thoại cộng đồng có gán nhãn.

### NASA Media

Các bản ghi kỹ thuật âm thanh hàng không vũ trụ.

---

# Collection Cadence

**Static:** Dữ liệu của phiên bản v1.0 được đóng băng sau khi hoàn thành quy trình thu thập và QC.

---

# Data Integration

### Included Fields

Toàn bộ 34 trường siêu dữ liệu chuẩn hóa:

- `clip_id`
- `speaker_id`
- `text_verbatim`
- `text_normalized`
- `license_type`
- `audio_sha256`
- v.v.

### Excluded Fields

- Thông tin định danh cá nhân của người đọc
- Cookie
- Thông tin tài khoản người dùng của các nền tảng nguồn

---

# Data Processing

## Collection Method

Tải file canonical trực tiếp từ nguồn chính thức (không dùng bản tải lậu re-upload).

## Tools Used

- `ffmpeg`
- `pydub`
- `librosa`
- Python scripts

## Process

1. Chuyển đổi sample rate về **16.000 Hz**.
2. Chuyển đổi kênh về **Mono**.
3. Định dạng **16-bit signed PCM WAV**.
4. Tạo checksum **SHA256** cho từng file.

---

# Collection Criteria

## Data Selection

Chọn lọc các bản thu có độ rõ cao, không bị nén âm quá mức (*over-compression*), không chứa tạp âm nền vượt ngưỡng cho phép và có văn bản đối chiếu đáng tin cậy.

## Data Inclusion

- Bản thu tiếng Anh chuẩn hoặc tiếng Quan Thoại phổ thông.
- Bản quyền thuộc phạm vi Public Domain hoặc Creative Commons có quyền thương mại/nghiên cứu phù hợp (CC BY).
- Độ dài câu nói sau khi segment nằm trong khoảng từ 1 đến 20 giây.

## Data Exclusion

- Loại bỏ các clip dưới 1 giây hoặc dài trên 20 giây.
- Loại bỏ các đoạn thu âm có tỷ lệ câm (silence) bất thường hoặc bị clipping biên độ nghiêm trọng.
- Loại bỏ các bản ghi chứa tiếng Quảng Đông (Cantonese) hoặc ngôn ngữ thứ ba không được chú thích.
- Loại bỏ các nội dung nhúng bản quyền của Reuters, AP, AFP hoặc nhạc nền thương mại.

---

# Relationship to Source

## Use & Utility(ies)

Tập dữ liệu kế thừa và chuẩn hóa các nguồn tri thức mở thành dạng cấu trúc thống nhất, phù hợp trực tiếp cho quy trình nạp dữ liệu (*data loader*) của các thư viện học sâu như:

- PyTorch
- Hugging Face Datasets
- FunASR

## Benefit and Value(s)

So với nguồn phát thanh thô dài hàng giờ, OneVoice ASR cung cấp các segment cắt gọt chuẩn xác theo ranh giới âm tiết/từ, loại bỏ khoảng lặng thừa và đi kèm nhãn phiên âm kép (*verbatim* và *normalized*) đã qua thẩm tra 2 lớp.

## Limitation(s) and Trade-Off(s)

Tỷ lệ các mẫu có nhiều người nói cùng lúc (*overlap*) còn thấp (chiếm dưới 1% tập dữ liệu) nhằm ưu tiên độ sạch cho pha nhận dạng cơ bản.

---

# Version and Maintenance

## First Version

- **Release date:** 09/2026
- **Link to dataset:** `onevoice_asr_dataset_v0.1` (Pilot release)
- **Status:** Deprecated (Đã được nâng cấp toàn diện lên v1.0)
- **Size of Dataset:** ~1.3 GB (Phần English pilot ban đầu)
- **Number of Instances:** 7.752 clips

### Note(s) and Caveat(s)

Phiên bản pilot trước đây chỉ tập trung vào tự động kiểm tra định dạng audio tiếng Anh; bản v1.0 đã tích hợp đầy đủ song ngữ Anh - Trung và phân bổ tập Train/Dev chuẩn hóa theo người nói.

---

# Cadence

**Monthly**

Cập nhật định kỳ hàng tháng theo từng chu kỳ kiểm tra dữ liệu.

## Last and Next Update(s)

- **Date of last update:** 09/09/2026
- **Total data points affected:** 14.296 clips
- **Date of next update:** 15/10/2026

---

# Human and Other Sensitive Attributes

## Sensitive Human Attribute(s)

- **Language:** English, Mandarin
- **Geography / Accent Region:** US, Mainland China, v.v.
- **Gender:** Được mã hóa ẩn trong tập đặc trưng giọng nói, không công bố nhãn công khai theo yêu cầu bảo mật thông tin.

## Intentionality

### Intentionally Collected Attributes

- Ngôn ngữ (`language`)
- Phương ngữ/vùng giọng (`language_variant`, `accent_region`)

### Unintentionally Collected Attributes

- Độ tuổi
- Giới tính
- Đặc điểm ngữ điệu cá nhân tự nhiên của diễn giả

## Rationale

Việc thu thập đa dạng vùng ngữ âm và biến thể phát âm là bắt buộc để mô hình ASR không bị thiên kiến (*bias*) đối với người nói bản ngữ hoặc người nói có ngữ điệu địa phương.

---

# Distribution(s)

| Human Attribute | Class / Label | Count | Percentage |
|---|---|---:|---:|
| Language | English (en) | 7,755 | 54.25% |
| Language | Mandarin (zh) | 6,541 | 45.75% |
| Accent Region | US / North America | 7,755 | 54.25% |
| Accent Region | Mainland China (zh-CN) | 6,161 | 43.10% |
| Accent Region | Others / Unknown | 380 | 2.65% |

> **Above:** Phân bố đặc tính ngôn ngữ và vùng giọng của tập dữ liệu OneVoice ASR v1.0.

---

# Risk(s) and Mitigation(s)

## Biased Recognition Performance

Mô hình có thể nhận diện kém hơn trên các giọng hiếm → Giữ nguyên tỷ lệ cân bằng giữa 2 ngôn ngữ (~12h tiếng Anh và ~10.5h tiếng Trung) và liên tục bổ sung đa dạng nguồn nói.

---

# Extended Use

## Use with Other Data

**Safety Level:** Safe to use with other data (An toàn tuyệt đối khi kết hợp với các bộ dữ liệu ASR công cộng khác như LibriSpeech, Common Voice, AISHELL).

### Known Safe Dataset(s) or Data Type(s)

- **Dataset:** Mozilla Common Voice (Cùng chuẩn cấp phép CC BY / CC0).
- **Dataset:** LibriSpeech ASR Corpus (Public Domain / CC BY 4.0).
- **Dataset:** AISHELL-1 (Apache 2.0).

### Best Practices

Khi ghép nối (*merge*) với các tập dữ liệu khác, cần kiểm tra mã băm SHA256 để loại trừ các bản ghi trùng lặp và đảm bảo quy tắc chuẩn hóa văn bản đồng nhất (*Text Normalization*).

---

# Forking & Sampling

## Safety Level

**Safe to fork and/or sample**

## Acceptable Sampling Method(s)

- Stratified Sampling (Lấy mẫu phân tầng theo ngôn ngữ và người nói)
- Random Sampling

## Best Practice(s)

Khi trích xuất tập con (*subset*), bắt buộc phải phân chia theo cấp độ người nói (`speaker_id`) hoặc tập tập phim (`source_program`) để tránh hiện tượng rò rỉ thông tin người nói giữa tập train và test.

---

# Use in ML or AI Systems

## Dataset Use(s)

- Training
- Testing
- Validation
- Fine Tuning

## Notable Feature(s)

Dữ liệu đã được phân tách rành mạch thành 2 tập riêng biệt:

- `train.jsonl`: **13.161 mẫu**
- `dev.jsonl`: **1.135 mẫu**

Tuân thủ nghiêm ngặt nguyên tắc **Speaker-disjoint** và **Episode-disjoint**.

---

# Distribution(s) & Split Statistics

| Split | Số lượng clips | Tổng thời lượng | Tỷ lệ số clips | Tỷ lệ thời lượng |
|---|---:|---:|---:|---:|
| **Train** | 13,161 | 19.50h (70,201.28s) | 92.06% | 87.07% |
| **Development (Dev)** | 1,135 | 2.90h (10,427.30s) | 7.94% | 12.93% |
| **Total** | **14,296** | **22.40h (80,628.58s)** | **100.0%** | **100.0%** |

> **Above:** Bảng phân bổ dữ liệu thực tế giữa tập Train và tập Development.

> **Additional Notes:** Toàn bộ dữ liệu Development set được bảo toàn 100% qua quy trình kiểm duyệt L2 thủ công để làm căn cứ đánh giá đối chuẩn (Benchmark Gold Standard).

---

# Transformations

## Synopsis

### Transformation(s) Applied

- Cleaning Missing Values
- Converting Data Types / Audio Resampling
- Redaction or Anonymization
- Data Aggregation & Manifest Construction

---

# Field(s) Transformed

## Audio Format Standardization

- **Transformation Type:** Audio Format Standardization
- **Source Field:** Âm thanh gốc đa định dạng (mp3, m4a, webm, wav nhiều tần số lấy mẫu)
- **Target Field:** WAV PCM signed 16-bit, 16.000 Hz, Mono channel.

## Text Normalization

- **Source Field:** `text_verbatim` (chứa dấu câu, viết hoa tự do, số dạng chữ số)
- **Target Field:** `text_normalized` (chuẩn hóa viết hoa/thường, chuẩn hóa số, dấu câu phù hợp tính WER/CER).

---

# Library(ies) and Method(s) Used

- **FFmpeg / pydub:** Chuyển đổi định dạng audio và chuẩn hóa kênh âm thanh.
- **unicodedata:** Chuẩn hóa Unicode NFKC, quy đổi chữ Hán phồn thể sang giản thể cho tiếng Trung.
- **jiwer / whisper-normalizer:** Chuẩn hóa văn bản tiếng Anh phục vụ tính điểm WER.

---

# Breakdown of Transformations

## Audio Format Conversion

### Method

Ép xung tần số lấy mẫu về 16 kHz mono bằng bộ lọc đa pha chất lượng cao của FFmpeg để đảm bảo tính tương thích tối đa với các bộ trích xuất đặc trưng âm học (Mel-spectrogram / Filterbanks).

### Residual Risk

Mất mát dải tần số cực cao trên 8 kHz (không ảnh hưởng đến dải tần số tiếng nói của con người trong nhận dạng ASR).

---

# Cleaning Missing & Mismatched Values

### Method

100% bản ghi được rà soát trường khóa tự động (`clip_id`, `audio_sha256`, `language`).

Các trường thiếu được bổ sung giá trị mặc định rõ ràng (ví dụ: `environment: "unknown"`).

---

# Annotations & Labeling

## Annotation Workforce Type

- **Human Annotations:** In-house Core Team Members
- **Machine-Generated Seeds:** Chỉ sử dụng mô hình tạo bản nháp ban đầu trước khi thẩm định.

---

# Annotation Characteristic(s)

| Characteristic | Số liệu |
|---|---|
| **Total Number of Annotations** | 14.296 phiên âm hoàn chỉnh |
| **Annotation Passes per Sample** | 2 lượt độc lập (L1 Annotation + L2 Independent Review) |
| **Annotator Pool Type** | In-house Data Curators (AIoT Lab) |

---

# Annotation Task(s)

### Task Description

Nghe trực tiếp từng đoạn audio clip và tiến hành phiên âm trung thực (*verbatim transcript*) bao gồm cả các hiện tượng ngập ngừng, từ đệm hoặc lỗi phát âm.

### Task Instructions

Quy chuẩn gắn thẻ bắt buộc đối với các hiện tượng âm thanh không lời:

- `[noise]`
- `[music]`
- `[laughter]`
- `[overlap]`
- `[inaudible]`
- `[foreign]`

### Inter-rater Adjudication Policy

Người thực hiện gán nhãn L1 không được phép tự phê duyệt (*approve*) bản ghi của mình tại vòng thẩm định L2.

---

# Human Annotators

## Annotator Description(s)

Đội ngũ gồm **3 chuyên viên xử lý dữ liệu tiếng nói nội bộ của AIoT Lab**, thông thạo tiếng Anh và tiếng Quan Thoại.

Đảm bảo kiểm tra chéo độc lập:

- Thành viên phụ trách L1 tiếng Anh được kiểm tra L2 bởi thành viên độc lập.
- Tương tự cho phân vùng tiếng Quan Thoại.

---

# Validation Types

## Method(s)

- Data Type Validation
- Range and Constraint Validation (Duration 1–20s, sample rate = 16000)
- Audio Integrity & Silence / Clipping Validation
- Duplicate Validation (SHA256 checksum)

## Description(s)

Chạy script tự động hóa quét trên toàn bộ **14.296 file audio và manifest** để phát hiện:

- File hỏng
- File rỗng
- Sai định dạng tần số lấy mẫu
- Trùng lặp nội dung

Kết quả tự động ghi nhận tại:

- `automatic_checks.csv`
- `annotation_audit.csv`

---

# Sampling Methods

## Method(s) Used

- Stratified Sampling (Phân tầng theo ngôn ngữ và tổ chức nguồn để tạo tập Dev)
- Speaker-disjoint Filtering

## Sampling Criteria

Tập Development (Dev) được chọn lọc đại diện sao cho phản ánh đầy đủ các điều kiện âm học:

- Giọng đọc chuẩn (VOA)
- Giọng họp báo ngoại giao (State Dept)
- Giọng hội thoại/đọc tiếng Trung

Đảm bảo toàn bộ người nói trong tập Dev không xuất hiện trong tập Train nhằm chống rò rỉ dữ liệu.

---

# Known Applications & Benchmarks

## ML Application(s)

- Speech Recognition
- End-to-End ASR
- Multilingual Speech Processing
- Low-latency Inference

---

# Evaluation Result(s)

Dưới đây là kết quả kiểm thử đối chuẩn baseline thực tế trên tập kiểm thử Development (`dev.jsonl`) của bộ dữ liệu OneVoice ASR v1.0.

## 1. English ASR Benchmark

**Model:** `openai/whisper-small`

### Evaluation Set

- **Tập đánh giá:** Dev Set English (776 clips, 100% thành công)
- **Corpus WER:** 3.98% (0.0398)
- **Mean clip WER:** 4.36% (0.0436)
- **Median clip WER:** 0.00% (Đa số các clip nhận dạng chính xác hoàn hảo)

### Hiệu năng theo nguồn tiếng Anh

| Source | Clips | Mean WER |
|---|---:|---:|
| VOA Learning English | 372 | 1.91% |
| NASA | 137 | 6.35% |
| U.S. Department of State | 267 | 6.74% |

---

## 2. Mandarin Chinese ASR Benchmark

**Model:** `FunAudioLLM/SenseVoiceSmall`

### Evaluation Set

- **Tập đánh giá:** Dev Set Mandarin (359 clips, 100% thành công, 6,129.35s audio)
- **Corpus CER:** 23.59% (0.2359)
- **Macro CER:** 23.98% (0.2398)
- **Real-Time Factor (RTF):** 0.0105 (Xử lý nhanh gấp ~95 lần thời gian thực trên GPU GTX 1650)
- **Thời gian suy luận (Inference time):** 64.55 giây cho toàn bộ 359 clips

> **Above:** Bảng kết quả đối chuẩn Baseline ASR chính thức của OneVoice ASR Dataset v1.0.

---

# Description(s) and Statistic(s)

## Whisper-small (English)

Mô hình Transformer mã hóa - giải mã đa ngôn ngữ gọn nhẹ (~244M tham số), xử lý tốt câu từ dài và giọng đọc trang trọng.

## SenseVoiceSmall (Mandarin)

Mô hình ASR kiến trúc non-autoregressive tốc độ siêu cao từ FunAudioLLM/Alibaba, tối ưu hóa cho tiếng Trung đa phương ngữ.

---

# Expected Performance and Known Caveats

### Tiếng Anh

Hiệu năng rất cao trên các bản thu chuẩn (WER < 2% với VOA); độ phức tạp tăng lên khi gặp các từ nối nhanh, thuật ngữ quân sự/ngoại giao trong họp báo của Bộ Ngoại Giao Mỹ.

### Tiếng Trung

Tỷ lệ CER ~23.5% của SenseVoiceSmall chủ yếu do sự nhạy cảm về định dạng ngắt câu, khoảng trắng và các mẫu câu ngắn không có ngữ cảnh từ bộ thu âm cộng đồng mở.

---

# Terms of Art

## Concepts and Definitions referenced in this Data Card

### ASR (Automatic Speech Recognition)

**Definition:** Công nghệ nhận dạng tiếng nói tự động, chuyển đổi tín hiệu sóng âm thanh thành văn bản tương ứng.

### WER (Word Error Rate)

**Definition:** Thước đo đánh giá độ lỗi nhận dạng từ trong ASR, tính bằng tổng số lỗi chèn (*insertion*), xóa (*deletion*), thay thế (*substitution*) chia cho tổng số từ tham chiếu:

$$
\text{WER} = \frac{S + D + I}{N}
$$

Trong đó:

- `S`: Substitution
- `D`: Deletion
- `I`: Insertion
- `N`: Tổng số từ trong transcript tham chiếu

### CER (Character Error Rate)

**Definition:** Thước đo đánh giá độ lỗi ký tự, tiêu chuẩn đánh giá chính cho các ngôn ngữ tượng hình không có khoảng trắng tự nhiên như tiếng Trung (Mandarin).

### Real-Time Factor (RTF)

**Definition:** Tỷ số giữa thời gian máy tính suy luận mô hình và tổng thời lượng âm thanh được xử lý:

$$
\text{RTF} = \frac{T_{\text{inference}}}{T_{\text{audio}}}
$$

RTF < 1.0 biểu thị tốc độ xử lý nhanh hơn thời gian thực.

### Speaker-Disjoint

**Definition:** Nguyên tắc phân chia dữ liệu đảm bảo toàn bộ người nói trong tập kiểm thử (Dev/Test) không hề xuất hiện trong tập huấn luyện (Train) nhằm kiểm tra khả năng khái quát hóa tổng quát của mô hình.

### Verbatim vs Normalized Transcript

**Definition:**

- `text_verbatim` là văn bản phản ánh chính xác từng âm phát ra trong audio thực tế.
- `text_normalized` là văn bản đã được chuẩn hóa ngữ pháp, ký hiệu số và dấu câu để phục vụ huấn luyện máy học.

---

# Reflections on Data

## Tính đại diện và đa dạng văn hóa

Tập dữ liệu kết hợp hài hòa giữa:

- Các bài phát thanh mang tính giáo dục, chuẩn mực ngôn ngữ cao (VOA Learning English).
- Các bài phát biểu thực tế nhiều sắc thái ngữ điệu (U.S. State Department).
- Giọng nói tự nhiên của cộng đồng người bản xứ Trung Quốc (Mozilla Project).

Điều này mang lại sự cân bằng giữa độ sạch âm học và tính ứng dụng thực tiễn.

## Đảm bảo quyền sở hữu trí tuệ và đạo đức AI

Mọi tài sản dữ liệu đưa vào OneVoice ASR đều phải vượt qua bài kiểm tra bản quyền ngặt nghèo (**Rights Gate**).

Nhóm kiên quyết từ chối việc cào dữ liệu đại trà (*mass scraping*) từ YouTube nếu không có giấy phép rõ ràng, qua đó bảo đảm tối đa an toàn pháp lý cho các cá nhân và tổ chức ứng dụng bộ dữ liệu.