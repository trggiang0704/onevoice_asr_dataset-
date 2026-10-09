# Baseline CER — Mandarin ASR

**Model baseline:** `FunAudioLLM/SenseVoiceSmall`

**Split đánh giá:** dev

**Số clip đánh giá:** 359

**Số clip xử lý thành công:** 359

**Số clip xử lý thất bại:** 0

## 1. CER tổng thể

- **Corpus CER: 0.1043 (10.43%)**
- Mean clip CER: 0.0957
- Median clip CER: 0.0727

## 2. CER theo nguồn

| Nguồn | Số clip | Mean CER |
| --- | --- | --- |
| OneVoice Team | 359 | 0.0957 |

## 3. CER theo độ dài clip

| Khoảng | Số clip | Mean CER |
| --- | --- | --- |
| 10-15s | 113 | 0.0523 |
| 5-10s | 3 | 0.0101 |
| >15s | 243 | 0.1169 |

## 4. CER theo số người nói (speaker_count)

| speaker_count | Số clip | Mean CER |
| --- | --- | --- |
| 1 | 359 | 0.0957 |

## 5. Hard examples (CER >= 0.2)

Tổng: 51 clip. Chi tiết: `G:\pydub\benchmarks\sensevoice_zh_optimized\error_analysis.csv`, `G:\pydub\benchmarks\sensevoice_zh_optimized\hard_examples.jsonl`.

- **zh_000225** (CER=0.483)
  - Reference: `昨天我整理房间的时候，发现了很多以前买但是一直没有使用的东西。看着这些东西，我才发现自己以前经常冲动购物，以后一定要更加理性一些。`
  - Prediction: `昨天我整理房间的时候发现了很多以前买单是一一直啊嗯没有手用的东西看着这些东西我`
- **zh_000081** (CER=0.429)
  - Reference: `我每天都会安排一点时间学习新的东西。可能只是看一篇文章或者学几个新单词，但是长期坚持下来会有很大的变化。`
  - Prediction: `我每天都会安排一点实践学习性的东西可能只是看一遍完成或者写几个圣诞词但是长`
- **zh_000080** (CER=0.386)
  - Reference: `如果和朋友发生了误会，我觉得最好早点解释清楚。拖得时间越长，双方可能越容易产生更多不必要的想法。`
  - Prediction: `如果和朋友发生了误会我觉得最好早点写示进酒拖的时间越长双方可能越如`
- **zh_000232** (CER=0.385)
  - Reference: `如果明天不用上班，我可能会睡到自然醒，然后慢慢准备早餐。吃完以后出去走走，下午看看电影，晚上再找一家喜欢的餐厅吃饭。`
  - Prediction: `如果明天不用上班我可能会睡到自然醒然后慢慢准备炒餐做完了以后出去瞅瞅下午看看`
- **zh_000223** (CER=0.371)
  - Reference: `最近我发现，手机占用了自己很多时间。以前一有空就会打开手机看消息，现在我正在尝试减少使用时间，把更多时间留给阅读、运动和真正重要的事情。`
  - Prediction: `最近我发现手机占用了自己很多时间以前已有空就会打开手机看消息现在我正在尝试减少使终`
- **zh_000239** (CER=0.371)
  - Reference: `有时候生活不会按照我们计划的方向发展，但是这并不一定是一件坏事。也许改变计划以后，我们反而能够遇到新的机会，看到以前没有注意到的东西。`
  - Prediction: `有时候生活不会按照我们计划的方向发展但是这并不一定是一件坏事也许改变计划以后我`
- **zh_000219** (CER=0.351)
  - Reference: `我认为朋友之间最重要的是互相信任。如果遇到什么问题，可以直接说出来，而不是一直把想法放在心里。坦诚的交流能够让关系更加稳定。`
  - Prediction: `我认为朋友之间加最重要的是互相信任如果遇到什么问题可以就接说出来而不受一时把想法放在信`
- **zh_000092** (CER=0.340)
  - Reference: `有时候我们太关注结果，却忘记了享受过程。其实只要认真完成每一步，即使最后的结果不完美，也能学到很多东西。`
  - Prediction: `有时候我们太灌注结果却忘记了享受过程其实只要认真完成每一步其实最后的其`
- **zh_000217** (CER=0.333)
  - Reference: `我最近正在学习一门新的语言，刚开始的时候觉得发音特别困难。虽然每天只能学习一点点，但是坚持一段时间以后，我发现自己已经进步了很多。`
  - Prediction: `我最近正在学习一门性的语言刚开始的时候觉得发音特别混难虽然每天只能学一点点但是见熟一段书现语`
- **zh_000220** (CER=0.333)
  - Reference: `每个人都会有觉得累的时候，这很正常。重要的是知道什么时候应该停下来休息，而不是一直逼自己坚持。照顾好自己的状态，才能走得更远。`
  - Prediction: `每个人都会有觉得累的时候就很正常重要的是气到什么时候应该停下来休息而不是一直逼自己`
- **zh_000083** (CER=0.327)
  - Reference: `我以前觉得学习只能坐在书桌前进行，后来发现坐公交车的时候也可以听录音或者复习单词，这样可以利用零碎时间。`
  - Prediction: `我以前觉得学习只能坐在书桌前进行后来发现坐公共汽车的时候也可以听录音或者`
- **zh_000229** (CER=0.322)
  - Reference: `有时候我们会因为害怕失败，而不敢尝试新的事情。但是如果永远停留在原来的位置，就很难看到新的可能。所以我觉得适当冒险也是一种成长。`
  - Prediction: `有时候我们会因为害怕失败而不敢强试性的事情但是如果永远停留在原来的位置就很难看到新的`
- **zh_000238** (CER=0.316)
  - Reference: `我认为学习最重要的不是一次记住很多知识，而是能够长期坚持。每天学习一点新的内容，慢慢积累下来，最后一定会看到比较明显的变化。`
  - Prediction: `我认为学习最重要的不是一次溢出很多知识而是能够长期建筑每天学习一点新的内容慢慢积累下来`
- **zh_000091** (CER=0.289)
  - Reference: `我觉得现在的生活节奏越来越快，很多人每天都有很多事情要做。所以学会安排时间是一件非常重要的事情。`
  - Prediction: `我觉得现在的生活节凑越来越坏很多人每天都有很多事情要做所以谁会安排实践是一`
- **zh_000040** (CER=0.286)
  - Reference: `如果一个地方的公共交通很方便，我觉得旅行会轻松很多。这样即使第一次去，也可以比较容易地找到自己想去的地方。`
  - Prediction: `如果一个地方的公工交通很方便我觉得旅行会轻松很多这样即手地数据也可以比较容易的找到救集`
- **zh_000222** (CER=0.286)
  - Reference: `我很喜欢在下午喝一杯咖啡，尤其是在需要集中注意力工作的时候。咖啡的味道和香气能够让我感觉更加清醒，也更容易进入工作状态。`
  - Prediction: `我很喜欢在下午喝一杯咖啡尤其是在去要集中注意力工作的时候咖啡的味道和相机能够让我感觉更`
- **zh_000053** (CER=0.282)
  - Reference: `我最喜欢的早餐是鸡蛋、面包和牛奶。有时候时间比较充足，我还会自己煮一碗面，再加一些蔬菜。`
  - Prediction: `我最喜欢的炒菜是鸡蛋面包和牛奶有时候时时间比较充足我还会自己煮一`
- **zh_000235** (CER=0.279)
  - Reference: `今天在路上遇到了一位很久没有见面的朋友，我们站在街边聊了十几分钟。虽然只是一次偶然的见面，但是让我想起了很多以前一起经历过的事情。`
  - Prediction: `今天在路上要到了一位很久没有见面的朋友我们站在架边聊了十几分钟虽然只是一次偶然的见面但是让我`
- **zh_000020** (CER=0.277)
  - Reference: `我认为学习一门语言最重要的是坚持。每天学习十几分钟虽然不多，但是只要长期坚持，也可以看到很明显的进步。`
  - Prediction: `我认为学习一门语言最重要的是建筑每天学习十几分钟虽然不多但是主要长期建筑也可以`
- **zh_000034** (CER=0.271)
  - Reference: `上个月我去了一个以前没有去过的城市。那里的人很热情，当地的食物也很好吃，所以我希望以后还有机会再去一次。`
  - Prediction: `上个月我去了一个以前没有去过的城市那里的人很热情当地的食物也很好做所以我`

## 6. Thiết lập đánh giá

- Framework: FunASR
- Language: `zh`
- ITN: `False`
- Device: `cuda:0`
- VAD: `True`
- Batch size: `60s`
- VAD maximum segment: `30.0s`
- VAD merge length: `20s`
- Hard-example threshold: `20%`
- CER normalization: Unicode NFKC, chuyển chữ Hán phồn thể sang giản thể, loại bỏ khoảng trắng và dấu câu.

## 7. Tốc độ xử lý

- Total audio duration: 6129.35 giây
- Total inference time: 92.87 giây
- Corpus RTF: 0.0152

RTF = tổng thời gian suy luận / tổng thời lượng âm thanh.

- RTF < 1.0: nhanh hơn thời gian thực.
- RTF = 1.0: xấp xỉ thời gian thực.
- RTF > 1.0: chậm hơn thời gian thực.

## 8. Output files

- `predictions_zh.jsonl`
- `error_analysis.csv`
- `hard_examples.jsonl`
- `baseline_hz.md`
