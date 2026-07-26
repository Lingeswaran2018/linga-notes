# Interview Questions regarding TTS development

### 1. Why X-vector is used in TTS development

An X-vector is a fixed-length speaker embedding that represents a speaker's vocal identity. It is extracted from speech using a neural network, typically a TDNN, trained for speaker recognition. The embedding captures characteristics such as pitch, timbre, accent, and speaking style while being independent of the spoken text. In SpeechT5, the X-vector is provided alongside the text input so the model can generate speech in the target speaker's voice. During my project, I used speaker X-vectors during fine-tuning so that the model could preserve speaker identity while learning Tamil and Sinhala pronunciation, resulting in more natural and speaker-consistent synthesized speech.

Typically it is a 512-dimensional vector