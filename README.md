# Voice-Cloned Translator

A speech-translation project that explores transcription, translation and voice synthesis.

The repository now has two clearly separated modes:

1. a **live browser demo** that works without heavyweight model infrastructure,
2. the original **local voice-cloning pipeline** using Whisper, Ollama and XTTS-style voice synthesis.

## Live demo

**https://voice-cloned-translator-demo.vercel.app/**

The public demo lets a reviewer:

- record a short reference voice sample,
- play the recording back,
- enter English text,
- translate the text to a selected language,
- synthesize the translated text using a browser-installed voice.

## What the live demo does not claim

Browser text-to-speech is **not voice cloning**.

The hosted version is intentionally labelled as a safe translation-and-speech demo.

Actual voice cloning requires the local model stack or another dedicated model service.

Only use voice cloning with a voice you own or have permission to use.

## Original local pipeline

The full local project explores this flow:

```text
Audio
  ↓
Whisper transcription
  ↓
Text translation with Gemma through Ollama
  ↓
XTTS-style speech synthesis
  ↓
Translated audio
```

Main technologies include:

- Python
- Flask
- OpenAI Whisper
- Ollama
- Gemma
- Coqui TTS / XTTS
- NumPy / SciPy
- browser audio recording

## Why the full pipeline is not hosted on Vercel

The original pipeline depends on:

- large downloaded model files,
- a long-running Ollama server,
- significant RAM/VRAM,
- heavyweight speech models,
- file-based audio processing.

A normal serverless deployment is not a suitable runtime for that architecture.

So the live web demo provides an immediately usable portfolio experience while preserving the real local model code in the repository.

## Run the browser demo locally

```bash
cd web
python -m http.server 8000
```

Open:

```text
http://localhost:8000
```

Allow microphone access if you want to record a voice sample.

## Run the full local pipeline

The exact source is under the repository's local deployment/application folders.

Typical setup:

1. Install Python dependencies.
2. Install and start Ollama.
3. Pull the configured Gemma model.
4. Allow the speech model to download its required weights.
5. Start the Flask application.

The repository's model stack can require several gigabytes of storage and substantial memory.

## Project scope

This project is a prototype for experimenting with:

- speech-to-text,
- multilingual translation,
- text-to-speech,
- speaker-conditioned synthesis,
- browser audio capture,
- multi-stage AI pipelines.

It is not presented as a production voice-authentication or impersonation system.

## Author

**Sankalp Gupta**

- GitHub: https://github.com/Sankalp-gupta1
- LinkedIn: https://www.linkedin.com/in/sankalp-gupta-rishi-8617302b0/


## Run the web demo locally

The hosted portfolio version is a static web demo, so it does not need an API key or database for local preview.

### Step 1 — clone the repository

```bash
git clone https://github.com/Sankalp-gupta1/Voice-Cloned-Translator.git
cd Voice-Cloned-Translator
```

### Step 2 — open the deployable web folder

```bash
cd web
```

### Step 3 — start a small local server

```bash
python -m http.server 8000
```

### Step 4 — open the app

```text
http://localhost:8000
```

Production demo: **https://voice-cloned-translator-demo.vercel.app/**

The original project files are kept in the repository. The `web/` version is the browser-friendly deployment made for easy review.
