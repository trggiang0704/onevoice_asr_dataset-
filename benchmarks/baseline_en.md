# Baseline WER — English ASR

> ⚠️ **PROVISIONAL** — 509/776 clip đang dùng transcript L1 (chưa qua review L2). Theo mục 13.2 của kế hoạch, dev set cần kiểm tra L2 100% mới được coi là ground truth chính thức. Số WER dưới đây là ước lượng tạm thời, KHÔNG dùng để công bố kết quả cuối cùng cho tới khi hoàn thành review L2.

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

- **What_Good_Comes_from_Casting_a_Wide_Net_0059** (WER=2.000)
  - Reference: `at learningenglishatvauscom`
  - Prediction: `at learning english at voanewscom`
- **Moonbound_Episode_1_Charting_the_Course_0052** (WER=0.778)
  - Reference: `that might one time not see i really see`
  - Prediction: `not much long time no see long time no see`
- **This_Week_at_State_July_3_2020_0003** (WER=0.750)
  - Reference: `most highness terrif regime`
  - Prediction: `the most heinous terrorist regime`
- **This_Week_At_State_December_4_2020_A_rev_0025** (WER=0.714)
  - Reference: `its about 3 to 3 vs terry`
  - Prediction: `its about freedom versus tyranny`
- **For_When_You_Do_Something_Wrong_Mea_Culp_0027** (WER=0.667)
  - Reference: `and excal paint`
  - Prediction: `and exculpate`
