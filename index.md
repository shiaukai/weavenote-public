# WeaveNote

A minimal voice-note app for Android: hit record, get a clean transcript, optionally let an LLM tidy it up. Published by **easierlife** (Taiwan).

## What it does

- **Record voice notes** in the background — the OS won't kill recording when your screen is off.
- **Transcribe** with the provider you choose:
  - **Local Whisper** (on-device, fully offline after the model downloads once).
  - **Cloud STT** — OpenAI Whisper, Google Gemini, or AWS Bedrock Nova, using your own API key.
- **AI 整理** (optional post-processing) — send the transcript to OpenAI / Gemini / Claude / Bedrock to clean it up, summarise, or reformat. Again, your own API key.
- **Webhooks** — POST the audio and/or transcript to any URL you configure (per-segment or when the note is finalised).
- **Vocabulary groups** — feed domain-specific terms to the STT provider so names and jargon come out right.

## What it doesn't do

- **No backend for your notes.** Recordings, transcripts, settings, and API keys live on your device. The only server we run is the bot behind the optional Discord voice feature, which relays Discord audio to the app and deletes it within 24 hours.
- **No analytics SDK.** No Firebase Analytics, no Crashlytics, no Sentry.
- **No account.** No sign-up, no login.

The app shows banner ads via Google AdMob to keep it free. See the privacy policy for details.

## Get it

- **Google Play**: search for "WeaveNote" by easierlife.

## Links

- [Privacy Policy](/privacy.html)
- Contact: <shiaukai@gmail.com>
