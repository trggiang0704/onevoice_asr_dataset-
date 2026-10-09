# OneVoice ASR Dataset (v1.0)

[![License](https://img.shields.io/badge/License-Public%20Domain%20%7C%20CC%20BY%204.0-blue.svg)](https://drive.google.com/drive/folders/1NN5T3LlRT_WRkqtf65XMKGygPhmNEGhG)
[![Languages](https://img.shields.io/badge/Languages-English%20%7C%20Mandarin-green.svg)]()
[![Format](https://img.shields.io/badge/Format-16kHz%20WAV%20PCM-orange.svg)]()

## Overview
The **OneVoice ASR Dataset** is a standardized, bilingual speech recognition dataset designed for training, fine-tuning, benchmarking, and quantization calibration of Automatic Speech Recognition (ASR) systems. Developed by the Speech Data Team at **AIoT Lab**, the dataset features highly auditable, rights-cleared acoustic data in English (`en-US`) and Mandarin Chinese (`zh-CN`).

With **14,296 audio segments** totaling **22.40 hours**, the dataset encompasses a diverse spectrum of acoustic conditions—from scripted educational speech and press conferences to community-contributed voice data—optimized specifically for edge AI deployment and embedded inference engines.

## Dataset Structure

### Data Splits
The dataset is explicitly partitioned into **speaker-disjoint** and **episode-disjoint** Train and Development sets to prevent data leakage during model evaluation.

| Split | Utterances (Clips) | Total Duration (Hours) | Percentage (Duration) |
| --- | ---: | ---: | ---: |
| **Train** | 13,161 | 19.50h | 87.07% |
| **Development (Dev)** | 1,135 | 2.90h | 12.93% |
| **Total** | **14,296** | **22.40h** | **100.00%** |

### Audio Specifications
- **Format:** `WAV`
- **Sample Rate:** `16,000 Hz` (16 kHz)
- **Bit Depth:** `16-bit` signed PCM
- **Channels:** `1` (Mono)
- **Segment Length:** 1 to 20 seconds (Average: 5.64s)

## Data Fields
Each audio segment is paired with a comprehensive JSONL metadata record containing 34 attributes. The primary fields include:

- `clip_id` (string): Unique identifier for the audio segment.
- `source_organization` (string): The originating organization (e.g., VOA Learning English, U.S. Department of State, Mozilla).
- `license_type` (string): Governing copyright license (e.g., Public Domain, CC BY).
- `language` (string): ISO-639-1 language code (`en` or `zh`).
- `speaker_id` (string): Pseudonymous identifier for the speaker (real names are anonymized).
- `duration_ms` (int): Duration of the segment in milliseconds.
- `text_verbatim` (string): Exact spoken transcript including hesitations and non-lexical markers.
- `text_normalized` (string): Cleaned and standardized text optimized for model training and WER/CER evaluation.
- `audio_sha256` (string): Cryptographic hash for file integrity and deduplication.
- `split` (string): Dataset partition (`train` or `development`).

## Sources & Licensing
All assets have passed a rigorous **Rights Gate** policy to ensure compliance and zero third-party copyright encumbrances (such as commercial music or third-party news agencies).

| Language | Source Organization | Primary Domain | License |
| :--- | :--- | :--- | :--- |
| **English** | VOA Learning English | Scripted / Broadcast | Public Domain |
| **English** | U.S. Department of State | Diplomatic / Spontaneous | Public Domain |
| **English** | NASA | Technical / Aerospace | Public Domain |
| **Mandarin** | Mozilla Data (zh-CN) | Read / Community Voice | CC BY 4.0 |

*Note: All data is cleared for both open academic research and commercial production integration under their respective licenses.*

## Benchmarks & Evaluation
The dataset includes official baseline evaluations conducted on the `dev` split (100% human-audited L2 ground truth).

### English Baseline (`openai/whisper-small`)
- **Corpus WER:** **3.98%**
- **Mean Clip WER:** 4.36%
- **Performance by Source:**
  - VOA Learning English: 1.91% WER
  - NASA: 6.35% WER
  - U.S. Department of State: 6.74% WER

### Mandarin Chinese Baseline (`FunAudioLLM/SenseVoiceSmall`)
- **Corpus CER:** **10.43%**
- **Real-Time Factor (RTF):** **0.0105** (on NVIDIA GTX 1650 4GB)
- **Total Inference Time:** 64.55 seconds (for 359 test clips)

## Getting Started
You can load the dataset metadata using standard Python libraries such as `json` or `pandas`:

```python
import json
import pandas as pd

# Load the train split
with open("manifests/train.jsonl", "r", encoding="utf-8") as f:
    train_data = [json.loads(line) for line in f]

df_train = pd.DataFrame(train_data)

# Display a typical data point
print(df_train[['clip_id', 'language', 'text_normalized']].head())
