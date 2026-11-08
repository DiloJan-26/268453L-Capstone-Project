## 📊 **Resource-Efficient Adaptation of Automatic Speech Recognition under Realistic Noise Conditions**

## 01. Research question and rationale

**Primary question:** Can updating a limited subset of a pretrained speech recognition network increase robustness under controlled acoustic interference while using less adaptation capacity and measurable compute than more extensive tuning?

**RQ1 — robustness:** Does multi-condition noisy-speech adaptation reduce held-out WER and CER relative to the unchanged checkpoint, and at which noise levels/categories?  
**RQ2 — adaptation capacity:** Does updating more layers produce sufficiently better robustness to justify extra parameters, memory, and time?  
**RQ3 — generalization:** Do gains survive when evaluated on noise recordings not used for training, without unacceptable clean-speech regression?  
**RQ4 — resource evidence:** What are the measured peak GPU memory, wall-clock training duration, GPU-hours, trainable parameter fractions, and throughput for each training configuration?

===============================================================

## 02. Literature Review

| ID | Year | Authors | Paper | Model(s) | Method or evidence | Relevance | Primary URL |
|---|---|---|---|---|---|---|---|
| R1 | 2020 | Baevski et al. | wav2vec 2.0 | Wav2Vec2 | Self-supervised speech pretraining and CTC ASR | Foundation; not noisy-efficiency baseline | [View Paper](https://arxiv.org/abs/2006.11477) |
| R2 | 2021 | Hsu et al. | Robust wav2vec 2.0 | Wav2Vec2 | Domain-shift robust pretraining | Motivates unseen-domain testing | [View Paper](https://www.isca-archive.org/interspeech_2021/hsu21_interspeech.pdf) |
| R3 | 2022 | Chen et al. | WavLM | WavLM | Denoising-enhanced speech pretraining | Context for noise robustness | [View Paper](https://doi.org/10.1109/JSTSP.2022.3188113) |
| R4 | 2024 | ELP-Adapters authors | ELP-Adapters | WavLM and others | Adapter PEFT; 90% fewer trainable parameters in reported tests | Resource metrics precedent; different backbone/tasks | [View Paper](https://doi.org/10.1109/TASLP.2024.3434445) |
| R5 | 2024 | Prasad et al. | Speech and Language Recognition with Low-rank Adaptation | XLS-R and Whisper | Low-rank adaptations and model-size/resource trade-offs | Alternative PEFT context | [View Paper](https://www.isca-archive.org/interspeech_2024/prasad24_interspeech.html) |
| R6 | 2024 | Kim et al. | Convolution-Augmented Parameter-Efficient Fine-Tuning for Speech Recognition | HuBERT | Convolution-augmented PEFT | Speech-specific PEFT context | [View Paper](https://www.isca-archive.org/interspeech_2024/kim24s_interspeech.html) |
| R7 | 2025 | Attia et al. | CPT-Boosted Wav2vec2.0 | Wav2Vec2 | Continued pretraining for noisy classroom domain | Noise robustness example, not same method | [View Paper](https://ieeexplore.ieee.org/document/10890830/) |
| R8 | 2025 | Ng et al. | Thinking Fast and Slow: Deep Filter-Tuning | WavLM+ | PEFT in noisy environments, 0.38% weights modified | Closest theme: noise robustness and efficiency | [View Paper](https://www.isca-archive.org/interspeech_2025/ng25_interspeech.html) |
| R9 | 2026 | Andrade et al. | Less can be More | Wav2Vec2 XLSR | Selective freezing for low-resource Creole ASR | Layer freezing comparison precedent | [View Paper](https://aclanthology.org/2026.rail-1.7/) |
| R10 | 2026 | Yadla | A survey of PEFT for audio foundation models | Multiple | Survey of PEFT and benchmarking gaps | Methodology context | [View Paper](https://doi.org/10.1007/s10772-025-10245-6) |

====================================================================

## 3. Datasets and Model

| ID | Type | Reference / Resource | Description | Primary Link | Additional Link |
|---|---|---|---|---|---|
| D1 | Dataset | Panayotov, V., et al. (2015). *LibriSpeech: An ASR Corpus Based on Public Domain Audio Books*. ICASSP. | Original LibriSpeech corpus for automatic speech recognition (ASR). | [Research Paper](https://doi.org/10.1109/ICASSP.2015.7178964) | [Original Corpus – OpenSLR](https://www.openslr.org/12/) |
| D2 | Dataset | Snyder, D., Chen, G., & Povey, D. (2015). *MUSAN: A Music, Speech, and Noise Corpus*. | Music, speech, and noise dataset for audio augmentation and robustness evaluation. | [Research Paper](https://arxiv.org/abs/1510.08484) | [Original Corpus – OpenSLR](https://www.openslr.org/17/) |
| M1 | Model Checkpoint | `facebook/wav2vec2-base-960h` | Pretrained Wav2Vec 2.0 ASR checkpoint. | [Hugging Face Model Card](https://huggingface.co/facebook/wav2vec2-base-960h) | [Model Configuration](https://huggingface.co/facebook/wav2vec2-base-960h/blob/main/config.json) |
| E1 | Evaluation Metric | Hugging Face `evaluate` – Word Error Rate (WER) | Evaluation metric for measuring ASR transcription errors. | [WER Metric Documentation](https://github.com/huggingface/evaluate/blob/main/metrics/wer/README.md) | — |
| B1 | Optional Benchmark (only for referencing) | CHiME-4: Real and Simulated Noisy Speech | Potential external noisy-speech benchmark. Not directly comparable with LibriSpeech–MUSAN without checking task alignment and licensing. | [CHiME-4 Dataset](https://www.chimechallenge.org/challenges/chime4/data) | — |
