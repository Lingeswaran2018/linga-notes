
Can a Tamil phonology-aware representation (Uyir–Mey) improve the text representation learned by a TTS model?


We propose a phonology-aware representation layer for the acoustic model of a Tamil TTS system. The proposed layer replaces conventional token embeddings with linguistically informed Uyir–Mey representations while leaving the downstream acoustic architecture and neural vocoder unchanged.

# Codebase
| Rank | Codebase        | Use for your research? | Reason                                                                                                                                               |
| ---- | --------------- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🥇 1 | **ESPnet2**     | **Excellent**          | The strongest research toolkit. It has reproducible recipes, active academic maintenance, and is widely used in speech research papers. ([arXiv][1]) |
| 🥈 2 | **Coqui-TTS**   | **Excellent**          | Easier to understand and modify than ESPnet, with good modularity and support for multiple TTS architectures. ([Coqui Docs][2])                      |
| 🥉 3 | **NVIDIA NeMo** | Good                   | Powerful, but more complex if you only want to replace the frontend representation.                                                                  |

What your preprocessing pipeline should look like
## Baseline
```
Dataset

↓

Text

↓

Tokenizer

↓

Token IDs

↓

Model
```
## Proposed
```
Dataset

↓

Text

↓

Orthographic Parser

↓

Uyir–Mey Representation

↓

Model
```

# ###########################################

```

Layer 1: Immutable Ground Truth
─────────────────────────────────────────────────────────────
• IndicVoices-R Audio (22.05 kHz WAV)
• Raw Text Transcriptions (Tamil Unicode)

                              │
                              ▼

Layer 2: Pre-computed Audio Features (Frame-Level Invariants)
─────────────────────────────────────────────────────────────
• Mel-Spectrograms (80-band STFT)
• Continuous Pitch / F0 Contour (PyWORLD / YAAPT)
• Frame Energy (L2-norm of STFT frames)

                              │
                              ▼

Layer 3: Experimental Branching (The Research Variable)
─────────────────────────────────────────────────────────────
          ┌───────────────────────────────────┐
          │                                   │
   [ Baseline Branch ]                 [ Proposed Branch ]
   Standard Tokenizer                  Orthographic Parser
   (Unicode / Phonemes)                (Uyir–Mei Decomposer)
          │                                   │
          ▼                                   ▼
   MFA Alignment A                     MFA Alignment B
   (Durations for Base Tokens)         (Durations for Uyir-Mei)
          │                                   │
          ▼                                   ▼
   Base Embedding                      Uyir–Mei Representation Layer
          │                                   │
          └─────────────────┬─────────────────┘
                            │
                            ▼

Layer 4: Acoustic Model & Synthesis
─────────────────────────────────────────────────────────────
• FastSpeech 2 Encoder ──► Variance Adaptor ──► Mel Decoder
• Predicted Mel-Spectrogram
• Pretrained Frozen BigVGAN ──► Audio Waveform
```