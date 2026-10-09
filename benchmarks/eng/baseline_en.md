# Baseline WER — English ASR

**Model baseline:** openai/whisper-small
**Split đánh giá:** dev
**Số clip đánh giá:** 776 / 776 (0 thiếu audio)

## 1. WER tổng thể

- **Corpus WER: 0.0398 (3.98%)**
- Mean clip WER: 0.0436
- Median clip WER: 0.0000

## 2. WER theo nguồn

| Nguồn | Số clip | Mean WER |
|---|---:|---:|
| U.S. Department of State | 267 | 0.0674 |
| NASA | 137 | 0.0635 |
| VOA Learning English | 372 | 0.0191 |

## 3. WER theo độ dài clip

| Khoảng | Số clip | Mean WER |
|---|---:|---:|
| 10-15s | 87 | 0.0375 |
| 5-10s | 277 | 0.0343 |
| <5s | 412 | 0.0511 |

## 4. WER theo số người nói (speaker_count)

| speaker_count | Số clip | Mean WER |
|---:|---:|---:|
| 1 | 754 | 0.0434 |
| 2 | 20 | 0.0529 |
| 3 | 2 | 0.0000 |

## 5. Hard examples (WER >= 0.5)

Tổng: 11 clip. Chi tiết: `results/baseline_en/hard_examples.csv`, template QC: `benchmarks/error_analysis.csv`.

- **Eng_007433** (WER=2.000)
  - Reference: `at learningenglishatvauscom`
  - Prediction: `at learning english at voanewscom`
- **Eng_002558** (WER=0.778)
  - Reference: `that might one time not see i really see`
  - Prediction: `not much long time no see long time no see`
- **Eng_005757** (WER=0.750)
  - Reference: `most highness terrif regime`
  - Prediction: `the most heinous terrorist regime`
- **Eng_005331** (WER=0.714)
  - Reference: `its about 3 to 3 vs terry`
  - Prediction: `its about freedom versus tyranny`
- **Eng_001241** (WER=0.667)
  - Reference: `and excal paint`
  - Prediction: `and exculpate`
