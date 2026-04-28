# WeaveNote Privacy Policy

**Last updated: 2026-04-28**

WeaveNote ("**we**", "**the app**") is published by **easierlife** (個人品牌, Taiwan; <shiaukai@gmail.com>). This page explains what data the app handles, where it goes, and what choices you have. We try to keep it short and concrete because the app is intentionally minimal in what it collects.

## 1. Data the app handles

| Type | Where it lives |
|------|---------------|
| **Audio recordings (.wav)** of your notes | On your device, in the app's private storage (`/data/data/com.easierlife.weavenote/`) |
| **Transcripts** generated from those recordings | On your device, in the same private storage |
| **Settings** (provider preferences, vocabulary groups, webhook URLs) | On your device |
| **API keys** for OpenAI / Gemini / Claude / AWS Bedrock | On your device, in **Android Keystore / iOS Keychain** (encrypted by the OS) |

**The app itself does not have a server.** We do not run any backend that receives, stores, or analyses your recordings or transcripts.

## 2. What gets sent off your device, and to whom

WeaveNote only sends data to services **you yourself configure**:

1. **The cloud STT provider you choose.** If you select OpenAI Whisper, Gemini, or AWS Bedrock Nova, your recording (or a chunk of it) is sent over HTTPS to that provider's API using **your own** API key. Their privacy policy applies:
   - OpenAI: <https://openai.com/policies/privacy-policy>
   - Google (Gemini): <https://policies.google.com/privacy>
   - Anthropic (Claude — text post-processing only): <https://www.anthropic.com/legal/privacy>
   - AWS: <https://aws.amazon.com/privacy/>
2. **The LLM provider you choose for "AI 整理" (post-processing).** Same as above — text transcripts get sent to your selected LLM API.
3. **Webhook URLs you configure.** If you add a webhook destination, the transcript and/or audio file is POSTed to that URL when the trigger you set fires (per-segment or on note finalize).
4. **Local Whisper.** When you choose the on-device option, the model file (~75 MB – 3 GB depending on your size choice) is downloaded **once** from `huggingface.co/ggerganov/whisper.cpp`. After that, transcription happens fully offline and your audio leaves the device only if you also configure a webhook.
5. **Google AdMob.** The app shows banner ads. AdMob's SDK collects device-level signals to serve ads (ad ID, IP, OS version, etc.) according to <https://policies.google.com/technologies/ads>. We do not transmit your recordings, transcripts, or any personal content to AdMob.

We do not bundle any third-party analytics SDK (no Firebase Analytics, no Crashlytics, no Sentry).

## 3. Permissions

| Permission | Why |
|---|---|
| `RECORD_AUDIO` | Core: capturing your voice notes. |
| `INTERNET` | Sending audio/transcripts to the STT/LLM/webhook services **you configure**, and downloading the local Whisper model on first use. Also used by AdMob. |
| `POST_NOTIFICATIONS` | Showing the persistent "recording in progress" notification so the OS doesn't kill recording when the screen is off. |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_MICROPHONE`, `WAKE_LOCK` | Same — keeps the recording alive in the background. |

## 4. Children

WeaveNote is not directed at children under 13. We do not knowingly collect data from children.

## 5. Your choices

- **Stop using cloud STT/LLM**: switch to "本地 Whisper" in settings to keep recordings on-device.
- **Delete a recording or the entire note**: delete it from the note detail screen — both the audio file and transcript are removed from the device.
- **Reset the app**: uninstall WeaveNote. Android removes all app data including recordings, transcripts, settings, and stored API keys.
- **Opt out of personalised ads**: Android Settings → Privacy → Ads → "Delete advertising ID".

## 6. Contact

Questions or requests: **<shiaukai@gmail.com>**.

## 7. Changes

If we change this policy we will update the date at the top and (if changes are material) note it in the app's release notes on Google Play.
