# OneVoice ASR Dataset (OneVoice-ASR)

## Dataset Description

**OneVoice ASR Dataset** is a standardized multilingual dataset for training and evaluating **Automatic Speech Recognition (ASR)** systems, with a primary focus on two languages:

- English (**en-US**)
- Mandarin Chinese (**zh-CN**)

The dataset was developed to address the need for high-quality speech data with clear provenance, transparent usage rights, and rigorously validated transcriptions for ASR research and deployment.

With **14,296 audio clips (~22.40 hours)** standardized to **WAV PCM 16-bit, 16 kHz, Mono**, the dataset covers a variety of real-world acoustic conditions, including scripted speech, interviews, diplomatic press briefings, and field recordings with more complex background noise.

The dataset is suitable for:

- Pre-training
- Fine-tuning
- Benchmarking
- Model quantization calibration

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
- **Contact:** trggiang107@gmail.com (or via the Google Drive repository)

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

The project is funded and supported with experimental computing infrastructure by AIoT Lab as part of its research on ASR solutions optimized for embedded systems and wearable devices under the **Glass–Ear Hub Project**.

> **Additional Notes:** No commercial intervention restricts academic use of the dataset.

---

# Dataset Overview

## Data Subject(s)

- **Non-Sensitive Data about people:** Public speech, lectures, press briefings, and voluntarily contributed community recordings.
- **Data about systems or products and their behaviors:** Experiments involving embedded and edge ASR systems.

---

# Dataset Snapshot

| Category | Data |
|---|---|
| **Size of Dataset** | ~2,400 MB (16 kHz WAV audio + JSONL + manifests) |
| **Total Duration** | 22.40 hours (80,628.58 seconds) |
| **Number of Instances** | 14,296 clips |
| **Number of Fields** | 34 metadata fields per clip |
| **Labeled Classes** | 2 primary languages (en, zh), including 3 language/accent variants (en-US, zh-CN, zh-TW) |
| **Number of Unique Speakers** | 644 identified speakers (`speaker_id`) |
| **Average Duration Per Instance** | 5.64 seconds (ranging from 1.004s to 20.00s) |
| **Algorithmic Labels** | Automatically generated `duration_ms`, `audio_sha256`, `lang_detected`, `silence_ratio`, `clipping_ratio` |
| **Human Labels** | 100% of transcripts reviewed through a two-stage process (L1 Annotation + L2 Review) |
| **Other Characteristics** | Standardized 16 kHz Mono, 16-bit PCM Signed WAV |

> **Above:** Summary of the technical characteristics of the OneVoice ASR Dataset v1.0 snapshot.

### Additional Notes

The dataset contains:

- **7,755 English clips** (~11.94 hours)
- **6,541 Mandarin Chinese clips** (~10.45 hours)

---

# Content Description

Each data sample consists of a segmented `.wav` audio file with a duration of approximately 1–20 seconds, accompanied by a detailed JSONL record containing information such as:

- Speaker identifier (`speaker_id`)
- Source organization (`source_organization`)
- Copyright and licensing status (`license_type`, `commercial_use_status`)
- Verbatim transcript (`text_verbatim`)
- ASR-normalized transcript (`text_normalized`)

> **Additional Notes:** The dataset excludes clips containing third-party content with unclear copyright status, commercial music, or severely corrupted audio such as heavy clipping or full silence.

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

> **Above:** Descriptive statistics for the quantitative fields in the dataset.

### Additional Notes

Approximately 99.8% of clips contain exactly one dominant speaker. Cases involving two or three speakers correspond to interview conversations or short turn-taking segments and are explicitly labeled.

---

# Sensitivity of Data

## Sensitivity Type(s)

- **Anonymous Data:** Community speech recordings from Mozilla that do not preserve personal identity information.
- **Pseudonymous Data:** Speakers are assigned identifiers such as `SPK_001` rather than real names.
- **None:** The dataset does not intentionally contain sensitive personally identifiable information (S/PII), financial information, or medical information.

## Field(s) with Sensitive Data

### Intentional Collected Sensitive Data

No sensitive or personally identifiable information is intentionally collected.

### Unintentionally Collected Sensitive Data

| Field Name | Description |
|---|---|
| `speaker_id` | Pseudonymous identifier associated with a speaker's voice characteristics and not linked to real-world personal identity. |
| `text_verbatim` | May contain names of public figures or geographic locations mentioned in public speeches, news programs, or diplomatic press briefings. |

> **Additional Notes:** Personal names appearing in the speech content generally refer to public or political figures mentioned in publicly available material from sources such as the U.S. Department of State or VOA.

---

# Security and Privacy Handling

### Methods

#### Pseudonymization

Real speaker names are removed from metadata and filenames and replaced with pseudonymous identifiers in formats such as `SPK_XXX`.

#### License/Consent Verification

Only sources that permit public sharing or provide participant consent are accepted, including community speech datasets distributed under applicable Mozilla Common Voice consent procedures.

> **Additional Notes:** No biometric reverse-identification or speaker identity reconstruction is performed.

---

# Risk Type(s)

**No Known Risks**

The dataset is constructed entirely from publicly released sources and open contribution datasets.

## Supplemental Link(s)

- **Source Policy:** See `SOURCE_POLICY.md`
- **Data Guideline:** See `DATA_GUIDELINE.md`

## Risk(s) and Mitigation(s)

### Voiceprint Recovery

Potential concern: Speaker identity could theoretically be inferred from voice characteristics.

**Mitigation:** Speakers are represented only through pseudonymous identifiers, and the dataset is intended solely for ASR machine learning purposes.

### Third-Party Copyright Infringement

Potential concern: Internet-collected content may contain copyrighted third-party material.

**Mitigation:** A multi-stage Rights Gate process is applied to exclude clips containing material from third-party news agencies such as AP, Reuters, AFP, or commercial background music.

> **Additional Notes:** The dataset development process is designed to follow responsible AI and research ethics practices.

---

# Dataset Version and Maintenance

## Maintenance Status

**Actively Maintained**

The dataset is actively maintained. The current v1.0 release includes technical corrections, metadata updates, and transcript audit improvements without changing the core dataset structure.

## Version Details

- **Current Version:** v1.0 (transitioned from the `onevoice_asr_dataset_v0.1` pilot)
- **Last Updated:** 09/2026
- **Release Date:** 09/2026

## Maintenance Plan

- **Versioning:** Semantic Versioning is used (`v1.0`, `v1.1`, `v2.0`). Minor versions are incremented for transcript corrections or metadata updates, while major versions are used for significant data expansion or the addition of new languages.
- **Updates:** Missing manifest fields and text normalization issues are reviewed and corrected periodically.
- **Errors:** Transcript error reports are collected through the repository issue tracker or development team email.
- **Feedback:** Feedback is accepted through AIoT Lab communication channels.

> **Additional Notes:** All dataset changes are documented in `CHANGELOG.md`.

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

Complete manual review of all 7,752 records marked `REVIEW_REQUIRED` in the automatic QC report with the goal of achieving a complete `overall_pass` status.

### Updates to Dataset

Add automatic SNR measurement fields and update the calibration manifest for ONNX/QNN quantization workflows.

> **Additional Notes:** The October 2026 update is expected to finalize transcript corrections for difficult samples identified during Whisper and SenseVoice evaluation.

---

# Example of Data Points

## Primary Data Modality

**Audio Data** with corresponding text labels.

## Sampling of Data Points

- **Demo Link:** `Eng_000336.wav` and `zh_000669.wav` in the dataset Drive directory
- **Typical Data Point Link:** See clip `Eng_000336` in `train.jsonl`
- **Outlier Data Point Link:** See clip `Eng_007433` (high WER / difficult sample)

---

# Data Fields

| Field Name | Example Value | Description |
|---|---|---|
| `clip_id` | `"Eng_000336"` | Unique identifier for the audio clip |
| `source_organization` | `"VOA Learning English"` | Organization that published the source audio |
| `license_type` | `"Public Domain"` | Copyright or licensing status of the audio asset |
| `language` | `"en"` | Language code following ISO-639-1 |
| `language_variant` | `"en-US"` | Specific language variant such as en-US or zh-CN |
| `speaker_id` | `"AI_Hallucinate..._SPK1"` | Pseudonymous speaker identifier |
| `speaker_count` | `1` | Number of speakers appearing in the clip |
| `speech_style` | `"formal"` | Speech style such as formal, interview, spontaneous, etc. |
| `duration_ms` | `3660` | Clip duration in milliseconds |
| `text_verbatim` | `"As the year 2023 comes..."` | Verbatim speech transcription |
| `text_normalized` | `"As the year 2023 comes..."` | Normalized transcript used for training and WER/CER evaluation |
| `audio_sha256` | `"1c5e8bc096f3b25a..."` | SHA256 hash for duplicate detection and integrity checking |
| `split` | `"train"` | Dataset partition, such as train or development |

> **Above:** Representative fields available in `train.jsonl` and `dev.jsonl`.

> **Additional Notes:** Each record contains 34 attributes supporting traceability back to its original source URL and licensing evidence.

---

# Typical Data Point

A typical data point is a single-speaker clip approximately 3–8 seconds long, with clean audio, clear pronunciation, and a transcript that accurately matches the spoken content.

## JSON

```json
{
  "clip_id": "Eng_000336",
  "source_id": "voa-learning-english-youtube",
  "source_organization": "VOA Learning English",
  "source_program": "AI_Hallucinate_Authentic_or_Rizz_for_Wor",
  "official_asset_url": "https://learningenglish.voanews.com/",
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

An atypical or difficult sample may contain turn-taking between speakers, have a longer duration (>12 seconds), or include specialized terminology that makes recognition more difficult.

## JSON

```json
{
  "clip_id": "Eng_000430",
  "source_id": "voa-learning-english-youtube",
  "source_organization": "VOA Learning English",
  "source_program": "An_Eye_for_an_Eye",
  "official_asset_url": "https://learningenglish.voanews.com/",
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

- **Research:** Research on compact multilingual ASR models.
- **Production:** Support ASR integration into AIoT edge and smart devices.

### Domain(s) of Application

- Automatic Speech Recognition
- Edge AI
- Speech-to-Text
- Acoustic Modeling
- Quantization Calibration

### Motivating Factor(s)

- Address the shortage of bilingual English–Mandarin ASR datasets with clear licensing evidence, explicit speaker separation, and data leakage controls.
- Provide a reliable calibration dataset for ASR model quantization in INT8/FP16 formats on NPU/DSP hardware, including Qualcomm QNN and ONNX Runtime.

---

# Intended Use

## Dataset Use(s)

- Safe for production use where the corresponding source licenses permit such use
- Safe for research use

## Suitable Use Case(s)

- **Suitable Use Case:** Training and fine-tuning English and Mandarin ASR systems such as Whisper, Conformer, and SenseVoice.
- **Suitable Use Case:** Benchmarking recognition accuracy using WER and CER on realistic speech conditions.
- **Suitable Use Case:** Building calibration datasets for hardware-accelerated inference and model quantization.

> **Additional Notes:** The dataset is primarily intended for near-field and medium-field speech recognition scenarios.

## Unsuitable Use Case(s)

- **Unsuitable Use Case:** Voice biometric authentication systems, because speakers are pseudonymized and the dataset was not designed for identity verification.
- **Unsuitable Use Case:** Proprietary commercial applications involving any future dataset partition distributed under a non-commercial license.

> **Additional Notes:** The dataset must not be used for voice spoofing or deepfake generation.

---

# Research and Problem Space(s)

The dataset is intended to support research on improving bilingual ASR accuracy under limited hardware resources and low-latency edge deployment constraints, including reducing hallucination and recognition errors involving homophones in English and Mandarin.

---

# Citation Guidelines

## Guidelines & Steps

When using OneVoice ASR Dataset in academic publications or technical products, please cite the dataset using the following BibTeX entry:

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

The dataset is accessible through a Google Drive repository with controlled download permissions.

### Documentation Link(s)

- **Dataset Storage:** Google Drive Workspace
- **Internal Guidelines:** `DATA_GUIDELINE.md` and `SOURCE_POLICY.md`

### Prerequisite(s)

Users must read and comply with copyright and source licensing requirements documented in `SOURCE_POLICY.md` and `ATTRIBUTION.md`.

### Policy Link(s)

- Creative Commons Attribution 4.0 International (CC BY 4.0)
- U.S. Government Work Public Domain Policy

### Access Control List(s)

**Public Read Access:** Researchers may download dataset manifests and audio for permitted research and training purposes.

---

# Retention

## Duration

The dataset is retained indefinitely for academic research and benchmark maintenance.

## Policy Summary

- **Retention Plan ID:** `RET-AIOT-ASR-V1`
- **Summary:** Canonical data and official releases are stored on AIoT Lab storage infrastructure with cloud backups.

## Process Guide

Canonical dataset files are maintained as read-only. Any changes to an official release must go through a pull request and QC review process.

---

# Exception(s) and Exemption(s)

**Exemption Code:** `PUBLIC_DATA / ANONYMOUS_DATA`

---

# Wipeout and Deletion

## Duration

Valid removal requests from copyright holders or speakers are processed within 30 days.

## Deletion Event Summary

Sequence of deletion and processing events:

1. Receive and verify the takedown request.
2. Identify the relevant `clip_id`, `speaker_id`, or source asset URL.
3. Remove the corresponding audio file from the released dataset and delete the associated manifest entry in the next dataset update.

## Acceptable Means of Deletion

Permanently remove the physical audio file from storage and add its SHA256 hash to an exclusion blacklist.

## Post-Deletion Obligations

Notify the requesting party and document the removal in the next dataset release notes.

---

# Provenance

## Collection Method(s) Used

- API
- Taken from other existing datasets such as Mozilla Common Voice
- Scraped or crawled from official public portals including VOA, U.S. Department of State, and NASA

## Methodology Detail(s)

- **Collection Type:** Collection from public broadcasting portals and open speech repositories.
- **Platform:** VOA Learning English, U.S. Department of State Briefings, Mozilla Data Collective, NASA Media Portal.
- **Dates of Collection:** 08/2026 – 09/2026
- **Primary Modality:** Audio Data
- **Update Frequency:** Static within each official dataset release

---

# Source Description(s)

### VOA Learning English

Educational English broadcasts with standard American pronunciation, moderate speaking rate, and generally clean audio.

### U.S. Department of State

Diplomatic press briefings containing natural interaction, turn-taking, and a range of international accents.

### Mozilla Data zh-CN

Community-contributed Mandarin speech recordings with transcriptions.

### NASA Media

Technical and aerospace-related audio recordings.

---

# Collection Cadence

**Static:** The data included in v1.0 is frozen after completion of the collection and QC process.

---

# Data Integration

### Included Fields

All 34 standardized metadata fields, including:

- `clip_id`
- `speaker_id`
- `text_verbatim`
- `text_normalized`
- `license_type`
- `audio_sha256`
- etc.

### Excluded Fields

- Personal identity information of speakers
- Cookies
- User account information from source platforms

---

# Data Processing

## Collection Method

Canonical assets are downloaded directly from official sources rather than from unofficial mirrors or re-uploads.

## Tools Used

- `ffmpeg`
- `pydub`
- `librosa`
- Python scripts

## Process

1. Resample audio to **16,000 Hz**.
2. Convert audio to **Mono**.
3. Convert audio to **16-bit signed PCM WAV**.
4. Generate a **SHA256 checksum** for each file.

---

# Collection Criteria

## Data Selection

Audio is selected based on clarity, limited over-compression, acceptable background noise levels, and the availability of reliable reference transcripts.

## Data Inclusion

- Standard English or Mandarin Chinese speech.
- Public Domain or compatible Creative Commons material that permits the intended research or commercial use.
- Segmented utterances between 1 and 20 seconds long.

## Data Exclusion

- Clips shorter than 1 second or longer than 20 seconds.
- Recordings with abnormal silence ratios or severe amplitude clipping.
- Cantonese speech or unannotated third-language content.
- Embedded third-party copyrighted content from Reuters, AP, AFP, or commercial music.

---

# Relationship to Source

## Use & Utility(ies)

The dataset transforms heterogeneous open speech sources into a standardized structure suitable for direct use with deep learning data loaders such as:

- PyTorch
- Hugging Face Datasets
- FunASR

## Benefit and Value(s)

Compared with raw long-form broadcasts, OneVoice ASR provides accurately segmented utterances, reduced excess silence, and both verbatim and normalized transcripts that have undergone two-stage human review.

## Limitation(s) and Trade-Off(s)

Overlapping multi-speaker speech accounts for less than 1% of the dataset because the initial release prioritizes relatively clean ASR training examples.

---

# Version and Maintenance

## First Version

- **Release Date:** 09/2026
- **Dataset:** `onevoice_asr_dataset_v0.1` (Pilot release)
- **Status:** Deprecated, replaced by v1.0
- **Size of Dataset:** ~1.3 GB (initial English pilot subset)
- **Number of Instances:** 7,752 clips

### Note(s) and Caveat(s)

The pilot release primarily focused on automated validation of English audio formatting. Version 1.0 expands the dataset into a bilingual English–Mandarin resource and introduces standardized speaker-disjoint Train/Dev splitting.

---

# Cadence

**Monthly**

Maintenance updates are scheduled approximately once per month according to the dataset QC cycle.

## Last and Next Update(s)

- **Date of Last Update:** 09/09/2026
- **Total Data Points Affected:** 14,296 clips
- **Date of Next Update:** 15/10/2026

---

# Human and Other Sensitive Attributes

## Sensitive Human Attribute(s)

- **Language:** English, Mandarin
- **Geography / Accent Region:** United States, Mainland China, etc.
- **Gender:** Gender-related characteristics may naturally exist in speech but are not published as explicit labels.

## Intentionality

### Intentionally Collected Attributes

- Language (`language`)
- Language variant and accent region (`language_variant`, `accent_region`)

### Unintentionally Collected Attributes

- Age-related vocal characteristics
- Gender-related vocal characteristics
- Individual prosodic characteristics

## Rationale

Collecting speech from diverse accents and pronunciation patterns is important for reducing ASR bias against speakers with less represented regional or linguistic characteristics.

---

# Distribution(s)

| Human Attribute | Class / Label | Count | Percentage |
|---|---|---:|---:|
| Language | English (en) | 7,755 | 54.25% |
| Language | Mandarin (zh) | 6,541 | 45.75% |
| Accent Region | US / North America | 7,755 | 54.25% |
| Accent Region | Mainland China (zh-CN) | 6,161 | 43.10% |
| Accent Region | Others / Unknown | 380 | 2.65% |

> **Above:** Distribution of language and accent-region characteristics in OneVoice ASR Dataset v1.0.

---

# Risk(s) and Mitigation(s)

## Biased Recognition Performance

Potential risk: The resulting ASR model may perform worse on underrepresented accents or speech varieties.

**Mitigation:** The dataset maintains a relatively balanced distribution between English (~12 hours) and Mandarin (~10.5 hours) and is intended to incorporate greater source and accent diversity in future releases.

---

# Extended Use

## Use with Other Data

**Safety Level:** Safe to use with other compatible ASR datasets, subject to the respective licensing requirements of each dataset.

### Known Safe Dataset(s) or Data Type(s)

- **Mozilla Common Voice**
- **LibriSpeech ASR Corpus**
- **AISHELL-1**

### Best Practices

When merging OneVoice ASR with other datasets, SHA256 hashes should be checked to identify duplicate recordings, and text normalization conventions should be aligned across datasets.

---

# Forking & Sampling

## Safety Level

**Safe to fork and/or sample**

## Acceptable Sampling Method(s)

- Stratified Sampling
- Random Sampling

## Best Practice(s)

When creating subsets, data should be split by `speaker_id` or `source_program` to reduce the risk of speaker or source leakage between training and evaluation sets.

---

# Use in ML or AI Systems

## Dataset Use(s)

- Training
- Testing
- Validation
- Fine-tuning

## Notable Feature(s)

The dataset is divided into two main partitions:

- `train.jsonl`: **13,161 samples**
- `dev.jsonl`: **1,135 samples**

The split follows **Speaker-disjoint** and **Episode-disjoint** principles.

---

# Distribution(s) & Split Statistics

| Split | Number of Clips | Total Duration | Percentage of Clips | Percentage of Duration |
|---|---:|---:|---:|---:|
| **Train** | 13,161 | 19.50h (70,201.28s) | 92.06% | 87.07% |
| **Development (Dev)** | 1,135 | 2.90h (10,427.30s) | 7.94% | 12.93% |
| **Total** | **14,296** | **22.40h (80,628.58s)** | **100.0%** | **100.0%** |

> **Above:** Distribution of samples and audio duration between the Train and Development partitions.

> **Additional Notes:** The Development set is fully preserved through the L2 manual review process and serves as the benchmark gold-standard evaluation set.

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
- **Source Field:** Original audio in multiple formats such as MP3, M4A, WebM, and WAV with varying sample rates
- **Target Field:** WAV PCM signed 16-bit, 16,000 Hz, Mono

## Text Normalization

- **Source Field:** `text_verbatim`, which may contain arbitrary capitalization, punctuation, and numeric representations
- **Target Field:** `text_normalized`, standardized for ASR training and WER/CER calculation

---

# Library(ies) and Method(s) Used

- **FFmpeg / pydub:** Audio format conversion and channel standardization.
- **unicodedata:** Unicode NFKC normalization and Chinese character normalization.
- **jiwer / whisper-normalizer:** English transcript normalization for WER calculation.

---

# Breakdown of Transformations

## Audio Format Conversion

### Method

Audio is resampled to 16 kHz Mono using FFmpeg resampling to maximize compatibility with common speech feature extraction methods such as Mel-spectrograms and filterbanks.

### Residual Risk

Frequency content above approximately 8 kHz is discarded when resampling to 16 kHz. This is generally acceptable for ASR because the most important speech information is concentrated below this range.

---

# Cleaning Missing & Mismatched Values

### Method

All records are automatically checked for required fields such as:

- `clip_id`
- `audio_sha256`
- `language`

Missing optional fields are assigned explicit default values where appropriate, for example:

```text
environment: "unknown"
```

---

# Annotations & Labeling

## Annotation Workforce Type

- **Human Annotations:** In-house Core Team Members
- **Machine-Generated Seeds:** Models may be used only to generate initial draft transcriptions before human verification.

---

# Annotation Characteristic(s)

| Characteristic | Value |
|---|---|
| **Total Number of Annotations** | 14,296 completed transcripts |
| **Annotation Passes per Sample** | 2 independent stages (L1 Annotation + L2 Independent Review) |
| **Annotator Pool Type** | In-house Data Curators (AIoT Lab) |

---

# Annotation Task(s)

### Task Description

Annotators listen to each audio clip and produce a faithful verbatim transcription, including hesitation, filler words, and pronunciation errors when present.

### Task Instructions

Standard annotation tags are used for non-speech acoustic events:

- `[noise]`
- `[music]`
- `[laughter]`
- `[overlap]`
- `[inaudible]`
- `[foreign]`

### Inter-rater Adjudication Policy

The annotator responsible for L1 annotation is not allowed to approve their own record during L2 review.

---

# Human Annotators

## Annotator Description(s)

The annotation team consists of **three in-house speech data specialists from AIoT Lab** with English and Mandarin language expertise.

Independent cross-review is applied:

- English L1 annotations are reviewed by another team member during L2.
- The same independent review principle applies to Mandarin annotations.

---

# Validation Types

## Method(s)

- Data Type Validation
- Range and Constraint Validation
- Audio Integrity Validation
- Silence and Clipping Validation
- Duplicate Validation using SHA256

### Constraints

- Duration: 1–20 seconds
- Sample rate: 16,000 Hz

## Description(s)

Automated scripts scan all **14,296 audio files and corresponding manifest records** to identify:

- Corrupted files
- Empty files
- Invalid sample rates
- Duplicate content
- Audio quality anomalies

Validation results are recorded in:

- `automatic_checks.csv`
- `annotation_audit.csv`

---

# Sampling Methods

## Method(s) Used

- Stratified Sampling by language and source organization
- Speaker-disjoint Filtering

## Sampling Criteria

The Development set is selected to represent multiple acoustic conditions, including:

- Clean educational speech from VOA
- Diplomatic press briefings from the U.S. Department of State
- Mandarin conversational or read speech

Speakers in the Development set do not appear in the Training set, reducing the risk of speaker leakage.

---

# Known Applications & Benchmarks

## ML Application(s)

- Speech Recognition
- End-to-End ASR
- Multilingual Speech Processing
- Low-latency Inference

---

# Evaluation Result(s)

The following baseline results were obtained on the OneVoice ASR Dataset v1.0 Development set (`dev.jsonl`).

## 1. English ASR Benchmark

**Model:** `openai/whisper-small`

### Evaluation Set

- **Evaluation subset:** English Dev Set
- **Number of clips:** 776
- **Successful inference:** 100%
- **Corpus WER:** 3.98% (0.0398)
- **Mean Clip WER:** 4.36% (0.0436)
- **Median Clip WER:** 0.00%

### Performance by English Source

| Source | Number of Clips | Mean WER |
|---|---:|---:|
| VOA Learning English | 372 | 1.91% |
| NASA | 137 | 6.35% |
| U.S. Department of State | 267 | 6.74% |

---

## 2. Mandarin Chinese ASR Benchmark

**Model:** `FunAudioLLM/SenseVoiceSmall`

### Evaluation Set

- **Evaluation subset:** Mandarin Dev Set
- **Number of clips:** 359
- **Successful inference:** 100%
- **Total audio duration:** 6,129.35 seconds
- **Corpus CER:** 23.59% (0.2359)
- **Macro CER:** 23.98% (0.2398)
- **Real-Time Factor (RTF):** 0.0105
- **Inference Time:** 64.55 seconds for all 359 clips

An RTF of 0.0105 corresponds to processing approximately 95 times faster than real time on the reported GTX 1650 GPU environment.

> **Above:** Official baseline ASR benchmark results for OneVoice ASR Dataset v1.0.

---

# Description(s) and Statistic(s)

## Whisper-small (English)

Whisper-small is a multilingual Transformer encoder-decoder ASR model with approximately 244 million parameters. It performs well on longer sentences and formal speech.

## SenseVoiceSmall (Mandarin)

SenseVoiceSmall is a high-speed non-autoregressive ASR model from FunAudioLLM/Alibaba designed for multilingual and Chinese speech recognition.

---

# Expected Performance and Known Caveats

### English

Recognition accuracy is high on clean educational recordings such as VOA, where WER is below 2% in the reported benchmark.

Recognition becomes more difficult for rapid connected speech and military, diplomatic, or technical terminology occurring in U.S. Department of State briefings.

### Mandarin

The approximately 23.5% CER observed with SenseVoiceSmall is partly associated with punctuation conventions, spacing differences, and short utterances with limited contextual information in community-recorded speech.

---

# Terms of Art

## Concepts and Definitions Referenced in this Data Card

### ASR (Automatic Speech Recognition)

**Definition:** Technology that automatically converts spoken audio signals into corresponding written text.

### WER (Word Error Rate)

**Definition:** A standard ASR metric measuring the proportion of word-level errors in a hypothesis transcript relative to the reference transcript.

$$
\text{WER} = \frac{S + D + I}{N}
$$

Where:

- `S`: Number of substitutions
- `D`: Number of deletions
- `I`: Number of insertions
- `N`: Total number of words in the reference transcript

### CER (Character Error Rate)

**Definition:** A character-level recognition error metric commonly used for languages such as Mandarin Chinese where word segmentation based on whitespace is not naturally available.

### Real-Time Factor (RTF)

**Definition:** Ratio between inference processing time and the duration of the processed audio.

$$
\text{RTF} = \frac{T_{\text{inference}}}{T_{\text{audio}}}
$$

An RTF below 1.0 indicates processing faster than real time.

### Speaker-Disjoint

**Definition:** A dataset splitting strategy in which speakers appearing in the evaluation set do not appear in the training set, providing a stronger measure of generalization to unseen speakers.

### Verbatim vs. Normalized Transcript

**Definition:**

- `text_verbatim` represents the spoken content as faithfully as possible.
- `text_normalized` represents a normalized version used for machine learning training and standardized WER/CER evaluation.

---

# Reflections on Data

## Representation and Linguistic Diversity

The dataset combines:

- Educational and relatively standardized English broadcasts from VOA Learning English.
- More natural and acoustically diverse public briefings from the U.S. Department of State.
- Community-contributed Mandarin speech from Mozilla-related sources.

This combination is intended to provide a balance between clean acoustic conditions and realistic speech variability.

## Intellectual Property and Responsible AI Considerations

All data assets included in OneVoice ASR must pass a licensing and provenance review process referred to as the **Rights Gate**.

The project avoids indiscriminate mass scraping of online platforms when licensing status cannot be clearly established.

The objective is to maintain clear provenance, licensing evidence, and responsible data governance throughout the dataset lifecycle.
