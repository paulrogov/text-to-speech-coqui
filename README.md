# Free text-to-speech model by Coqui

Models:
* https://huggingface.co/coqui/XTTS-v2 `XTTSv2` is the best free production text-to-speech model by coqui.ai
* https://github.com/coqui-ai/TTS/discussions/1891 discussion about decent small model/vocoder combinations (`fast_pitch`/`hifigan_v2`) *(but they all are worse comparing to `XTTSv2`)*

Docs:
* https://docs.coqui.ai/en/latest/inference.html

## Setup and using to synthesize speech 

1. Install dependencies into a conda environment
```bash
conda env list
conda create -n coqui-tts python=3.10.4
conda activate coqui-tts
pip install TTS # ~ 8GB of packages
```

2. Download and launch text-to-speech models (CLI interface)
```bash
# available coqui models
tts --list_models

# fast_pitch/hifigan_v2
tts --text "Brandreport is an ultimate phishing and fraud ad scanner" \
    --model_name "tts_models/en/ljspeech/fast_pitch" \
    --vocoder_name "vocoder_models/en/ljspeech/hifigan_v2" \
    --out_path "output/file1.wav"

# xtts_v2
tts --text "Many users come to your company website from search engines." \
    --model_name "tts_models/multilingual/multi-dataset/xtts_v2" \
    --speaker_wav speech_en.wav \
    --language_idx en \
    --use_cuda true \
    --out_path "output/xtts2.wav"

tts --text "Я люблю бананы" \
    --model_name tts_models/multilingual/multi-dataset/xtts_v2 \
    --speaker_wav speech_ru.wav \
    --language_idx ru \
    --use_cuda true
    --out_path "output/xtts2.wav"
```

#### Usage variants:  
1. CLI
2. demo-server (slow)
3. api (python library)

#### Usage: demo-server
Beware, that CLI inference is faster than this tts-server
```bash
conda activate coqui-tts
tts-server

http://localhost:5002/
```
