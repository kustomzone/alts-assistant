<h1 align="center">alts</h1>
<p align="center">
  <a href="https://github.com/alxpez/alts" target="_blank">
    <img width="180" src="logo.png">
  </a>
</p>
<p align="center">( <strong>a</strong>ssistant: <strong>l</strong>istent | <strong>t</strong>hink | <strong>s</strong>peak )</p>

</br>

## 💬 about
100% free, local and offline assistant with speech recognition and talk-back functionalities.

## ✅ get it running
clone the repo
```ssh
git clone https://github.com/alxpez/alts.git
```

go to the main folder
```ssh
cd alts/
```

install the project dependencies
```ssh
pip install -r requirements.txt
```
> see the [pre-requisites](#pre-requisites) section, to make sure your machine is ready to start the ALTS

start up the assistant
```ssh
sudo python assistant.py
```
> the `keyboard` package requires to be run as admin (in macOS and Linux), it's not the case on Windows

## 🤖 default usage
<!-- 
TODO: FUTURE FEATURES:
- voice-to-clipboard: talk to take notes, write emails... paste raw or parsed text.
(Use the LLM to reshape/process/parse the whisper result to get a refined result)
(research if possible to paste automatically in the focused text-box)

- task-bar-icon: make the python script into a proper app
(or a simple installable package at least)
(include interface to text too)
-->
ALTS runs in the background and waits for you to press `ctrl+space` (you can modify the hotkey combination in `config.yaml`).
- While holding the hotkey, your voice will be recorded by your default input sound device.
- Once you release, the recording stops and its transcript is sent to your configured LLM.
- The LLM response then gets synthesized and played back to you.

You can also write your query directly into your terminal (if you don't wanna talk), the assistant will still speak back to you.

> ALL this processes happen locally by _default_ and NONE of your recordings or any other information is shared with anyone; it's ALL PRIVATE by _default_. ALL recordings are also deleted as soon as they are used.

> Be aware that if you configure ALTS with external providers (eg. OpenAI) your queries will be sent to their servers.

## ⚙️ pre-requisites
- ### python
  > Tested: version \>=3.11 on macOS and version \>= 3.8 on windows

- ### llm
  By default, the project is configured to work with [Ollama](https://ollama.ai/), running the [`dolphin-phi` model](https://ollama.ai/library/dolphin-phi) (an uncensored, very tiny and quick model). This setup makes the whole system completely free to run locally and great for low resource machines.

  However, we use [LiteLLM](https://github.com/BerriAI/litellm) in order to be provider agnostic, so you have full freedom to pick and choose your own combinations.
  Take a look at the supported [Models/Providers](https://docs.litellm.ai/docs/providers) for more details on LLM configuration.
  > See `.env.template` and `config.yaml` for customizing your setup

<!-- TODO: Include extra information and examples of LLM configurations -->


- ### stt
  We use `whisper` to transcribe your voice queries. It's a general-purpose speech recognition model - [setup](https://github.com/openai/whisper?tab=readme-ov-file#setup)
  > You might need to manually download a whisper model before running the assistant


- ### tts
  We use `TTS` for ALTS to talk-back to you. It's a library for advanced Text-to-Speech generation - [setup](https://github.com/coqui-ai/TTS/tree/dev#installation)
  > You might need to manually download a TTS model before running the assistant

<!-- TODO: Include extra requirements for windows installation -->
