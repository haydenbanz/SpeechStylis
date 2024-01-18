<div align="center">


## <img src="https://raw.githubusercontent.com/haydenbanz/SpeechStylis/main/speechstylisbanner.png"  />

## 🌐🤖 SpeechStylis AI: The Cutting-Edge in Text-to-Speech Synthesis with Python! 🚀🔊



Hey there, tech enthusiasts! 👋 Are you tired of boring, robotic text-to-speech voices? 😴 Well, we've got some exciting news for you! 🎉 We're introducing SpeechStylis AI, the cutting-edge technology that's revolutionizing the world of text-to-speech synthesis with Python! 🚀

Imagine being able to generate natural-sounding speech from text input, with a tone and style that matches your personality or brand. 💬 That's exactly what SpeechStylis AI does! It uses advanced machine learning algorithms to analyze a large dataset of human speech recordings, and then generates new speech samples that sound like they were recorded by a real person. 🤯

Ready to give it a try? SpeechStylis AI is now available as a Python library, so you can easily integrate it into your own projects. 🛠️ Whether you're building a virtual assistant, creating an audiobook, or developing an accessibility tool, SpeechStylis AI has everything you need to make your vision a reality. 🏡

</div>

[![Discord](https://img.shields.io/badge/Discord-CODE%20GLITCH-%237289DA?style=for-the-badge&logo=discord)](https://discord.gg/ZFTCpAU53U)
[![Mozilla License](https://img.shields.io/badge/License-Mozilla-blue?style=for-the-badge)](https://opensource.org/licenses/MPL-2.0)
[![Python Version](https://img.shields.io/static/v1?label=Python&message=3.6%2B&color=%230078D6&labelColor=%23e3e3e3&style=for-the-badge&logo=python)](https://www.python.org/downloads/)
[![Discord.py library](https://img.shields.io/static/v1?label=Discord.py&message=Library&color=%232A3E87&labelColor=%236A7DA8&style=for-the-badge)](https://pypi.org/project/discord.py/)
[![GitHub Issues](https://img.shields.io/github/issues/haydenbanz/DiscordGloom?style=for-the-badge)](https://github.com/haydenbanz/SpeechStylis/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/haydenbanz/DiscordGloom?style=for-the-badge)](https://github.com/haydenbanz/SpeechStylis/pulls)
[![GitHub Stars](https://img.shields.io/github/stars/haydenbanz/DiscordGloom?style=for-the-badge)](https://github.com/haydenbanz/SpeechStylis/stargazers)
![Profile Views](https://komarev.com/ghpvc/?username=haydenbanz&color=%232A3E87&labelColor=%236A7DA8&style=for-the-badge)


## 💬 Where to ask questions
Please use our dedicated channels for questions and discussion. Help is much more valuable if it's shared publicly so that more people can benefit from it.

| Type                            | Platforms                               |
| ------------------------------- | --------------------------------------- |
| 🐛 **Bug Reports**              | [GitHub Issue Tracker]                  |
| 🎁 **Feature Requests & Ideas** | [GitHub Issue Tracker]                  |
| 💻 **Usage Questions**          | [GitHub Discussions]                    |
| 🗨️ **General Discussion**       | [GitHub Discussions] or [Discord]   |

[GitHub Issue Tracker]: https://github.com/coqui-ai/tts/issues
[GitHub Discussions]: [https://github.com/coqui-ai/TTS/discussions](https://github.com/haydenbanz/SpeechStylis/discussions/1)
[Discord]: https://discord.gg/ZFTCpAU53U
[Tutorials and Examples]: https://github.com/haydenbanz/SpeechStylis/wiki


## 🚀 Features

- **Pretrained Models:** Explore a wide range of pretrained models in over 1100 languages.
  
- **Versatile Tools:** Utilize tools for training new models and fine-tuning existing ones in any language.

- **Dataset Analysis:** Leverage utilities for dataset analysis and curation.

## Model Implementations
### Spectrogram models
- Tacotron: [paper](https://arxiv.org/abs/1703.10135)
- Tacotron2: [paper](https://arxiv.org/abs/1712.05884)
- Glow-TTS: [paper](https://arxiv.org/abs/2005.11129)
- Speedy-Speech: [paper](https://arxiv.org/abs/2008.03802)
- Align-TTS: [paper](https://arxiv.org/abs/2003.01950)
- FastPitch: [paper](https://arxiv.org/pdf/2006.06873.pdf)

## Installation

👩‍💻SpeechStylis AI is tested on Ubuntu 18.04 with **python >= 3.9, < 3.12**.

**Tested Platforms:**
- Ubuntu
- Kali Linux
- Google Cloud


```bash
pip install TTS
```


If you are on Ubuntu (Debian) or Kali Linux, you can also run following commands for installation.

```bash 
git clone https://github.com/haydenbanz/SpeechStylis.git
```

## Modify .py File to Specify Pre-recorded Audio Location

To use your prerecorded audio, locate the `.py` file and find the section where the speaker's WAV file path is defined. Update the `speaker_wav_path` variable with the path to your audio file. Below is an example:

```python
# Original Code
speaker_wav_path = "/content/drive/MyDrive/audio.wav"
```

## run in google collab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Xdzm-Cu1ofbyFv0xp7An-BNiXYYpTchV?usp=sharing)




## Synthesizing speech by SpeechStylis AI



#### Running a multi-speaker and multi-lingual model

```python
import torch
from TTS.api import TTS

# Get device
device = "cuda" if torch.cuda.is_available() else "cpu"

# List available 
print(TTS().list_models())

# Init TTS
tts = TTS("tts_models/multilingual/multi-dataset/xtts_v2").to(device)

# Run TTS
# ❗ Since this model is multi-lingual voice cloning model, we must set the target speaker_wav and language
# Text to speech list of amplitude values as output
wav = tts.tts(text="Hello world!", speaker_wav="my/cloning/audio.wav", language="en")
# Text to speech to a file
tts.tts_to_file(text="Hello world!", speaker_wav="my/cloning/audio.wav", language="en", file_path="output.wav")
```

#### Running a single speaker model

```python
# Init TTS with the target model name
tts = TTS(model_name="tts_models/de/thorsten/tacotron2-DDC", progress_bar=False).to(device)

# Run TTS
tts.tts_to_file(text="Ich bin eine Testnachricht.", file_path=OUTPUT_PATH)

# Example voice cloning with YourTTS in English, French and Portuguese
tts = TTS(model_name="tts_models/multilingual/multi-dataset/your_tts", progress_bar=False).to(device)
tts.tts_to_file("This is voice cloning.", speaker_wav="my/cloning/audio.wav", language="en", file_path="output.wav")
tts.tts_to_file("C'est le clonage de la voix.", speaker_wav="my/cloning/audio.wav", language="fr-fr", file_path="output.wav")
tts.tts_to_file("Isso é clonagem de voz.", speaker_wav="my/cloning/audio.wav", language="pt-br", file_path="output.wav")
```

#### Example voice conversion

Converting the voice in `source_wav` to the voice of `target_wav`

```python
tts = TTS(model_name="voice_conversion_models/multilingual/vctk/freevc24", progress_bar=False).to("cuda")
tts.voice_conversion_to_file(source_wav="my/source.wav", target_wav="my/target.wav", file_path="output.wav")
```

#### Example voice cloning together with the voice conversion model.
This way, you can clone voices by using any model 

```python

tts = TTS("tts_models/de/thorsten/tacotron2-DDC")
tts.tts_with_vc_to_file(
    "Wie sage ich auf Italienisch, dass ich dich liebe?",
    speaker_wav="target/speaker.wav",
    file_path="output.wav"
)
```

#### Example text to speech using **Fairseq models in ~1100 languages** 🤯.
For Fairseq models, use the following name format: `tts_models/<lang-iso_code>/fairseq/vits`.
You can find the language ISO codes [here](https://dl.fbaipublicfiles.com/mms/tts/all-tts-languages.html)
and learn about the Fairseq models [here](https://github.com/facebookresearch/fairseq/tree/main/examples/mms).

```python
# TTS with on the fly voice conversion
api = TTS("tts_models/deu/fairseq/vits")
api.tts_with_vc_to_file(
    "Wie sage ich auf Italienisch, dass ich dich liebe?",
    speaker_wav="target/speaker.wav",
    file_path="output.wav"
)
```

### Command-line `tts`

<!-- begin-tts-readme -->

Synthesize speech on command line.

You can either use your trained model or choose a model from the provided list.

If you don't specify any models, then it uses LJSpeech based English model.


If you have any questions or feedback, please contact the project maintainers:

* 0x_hayden
* Email: t5hlt8zcp@mozmail.com
## Credits

This project is maintained by:

[<img src="https://avatars.githubusercontent.com/u/135024483?s=48&v=4" width="64" height="64" alt="Contributor Name">](https://github.com/code-glitchers)

### Contributors and Developers

[<img src="https://avatars.githubusercontent.com/u/67865621?s=64&v=4" width="64" height="64" alt="Contributor Name">](https://github.com/mindglitchers)
[<img src="https://avatars.githubusercontent.com/u/116929670?s=64&v=4" width="64" height="64" alt="Contributor Name">](https://github.com/AldrinCode)


## Support

If you find this project helpful, consider buying us a coffee:

[![Buy Me a Coffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-%23FFDD00?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/ciph3r#pageMessageModal)


## License

SpeechStylis AI is licensed under the Mozilla License. See the [LICENSE](LICENSE) file for details.



   

[![Python](https://img.shields.io/badge/Python-3.x-brightgreen.svg)](https://www.python.org/)
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](CONTRIBUTING.md)

