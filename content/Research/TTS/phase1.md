# Phase 1 Research Stack


| Component      | Final Choice              | Reason                                                                 |
| -------------- | ------------------------- | ---------------------------------------------------------------------- |
| Framework      | **ESPnet2**               | Strongest academic support, actively maintained, recipe-based training |
| Acoustic Model | **FastSpeech2**           | Clean text-to-mel architecture for controlled experiments              |
| Vocoder        | **BigVGAN (Frozen)**      | Keeps waveform generation constant                                     |
| Dataset        | **IndicVoices-R (Tamil)** | Large, modern multilingual corpus                                      |
| Backend        | **PyTorch**               | Native support                                                         |
| Language       | **Python**                | Standard research environment                                          |


# phase 1 flow
```
Tamil Unicode Text
        │
        ▼
Character Frontend
        │
        ▼
FastSpeech2
        │
        ▼
Mel Spectrogram
        │
        ▼
BigVGAN
        │
        ▼
Speech

```

# phase 2 flow

```
Tamil Unicode
        │
        ▼
Orthographic Parser
        │
        ▼
Uyir–Mei Representation Layer
        │
        ▼
FastSpeech2
        │
        ▼
Mel Spectrogram
        │
        ▼
BigVGAN

```