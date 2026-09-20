# OneVoice Mandarin ASR Baseline - SenseVoiceSmall

## Mô hình

* Mô hình: `FunAudioLLM/SenseVoiceSmall`
* Framework: FunASR
* Ngôn ngữ: Tiếng Trung (`zh`)
* ITN: `False`
* Thiết bị: `cuda:0`

## Phần cứng

* GPU: NVIDIA GeForce GTX 1650
* VRAM: 4 GB
* RAM: 16 GB

## Dataset

* Manifest: `G:\pydub\manifests\dev.jsonl`
* Thư mục audio: `G:\pydub\output_wav`
* Số bản ghi được đánh giá: 359
* Thành công: 359
* Thất bại: 0

## Đánh giá

* Chỉ số: Character Error Rate (CER) - Tỷ lệ lỗi ký tự
* Chuẩn hóa CER:

  * Unicode NFKC
  * Chuyển đổi chữ Hán phồn thể sang giản thể
  * Loại bỏ khoảng trắng
  * Giữ nguyên dấu câu
* Ngưỡng mẫu lỗi nghiêm trọng: 20%

## Kết quả

| Chỉ số                                    |      Giá trị |
| ----------------------------------------- | -----------: |
| CER trung bình theo từng mẫu (Macro CER)  |     23.9759% |
| CER trên toàn bộ tập dữ liệu (Corpus CER) |     23.5854% |
| Tổng thời lượng audio                     | 6129.35 giây |
| Thời gian suy luận                        |   64.55 giây |
| RTF trên toàn bộ tập dữ liệu              |       0.0105 |
| Số mẫu lỗi nghiêm trọng                   |          134 |
| Thành công                                |          359 |
| Thất bại                                  |            0 |

## Diễn giải

CER được tính trên các ký tự tiếng Trung sau khi áp dụng cùng một quy trình chuẩn hóa cho cả văn bản tham chiếu (reference) và văn bản dự đoán (hypothesis).

RTF được tính theo công thức:

`RTF = tổng thời gian suy luận / tổng thời lượng audio`

Do đó:

* RTF < 1.0: hệ thống xử lý nhanh hơn thời gian thực.
* RTF = 1.0: hệ thống xử lý xấp xỉ thời gian thực.
* RTF > 1.0: hệ thống xử lý chậm hơn thời gian thực.

## Các file đầu ra

* `error_analysis.csv`
* `baseline_zh.md`
