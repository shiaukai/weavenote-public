---
permalink: /privacy.html
---

# WeaveNote Privacy Policy

**Last updated: 2026-10-10**

WeaveNote ("**we**", "**the app**") is published by **easierlife** (個人品牌, Taiwan; <shiaukai@gmail.com>). This page explains what data the app handles, where it goes, and what choices you have. We try to keep it short and concrete because the app is intentionally minimal in what it collects.

## 1. Data the app handles

| Type | Where it lives |
|------|---------------|
| **Audio recordings** of your notes: `.wav` from the microphone, `.m4a` segments received through the Discord voice feature | **Android:** the app's media folder on shared storage (`/sdcard/Android/media/com.easierlife.weavenote/notes/`). **iOS:** the app's private storage. |
| **Transcripts, summaries and note titles**, plus the speaker's Discord display name on each Discord segment | On your device, in the app's private storage (`/data/data/com.easierlife.weavenote/`) |
| **Database backup**: a copy of the transcripts, summaries and note details above | **Android:** `/sdcard/Android/media/com.easierlife.weavenote/db_backup/`, refreshed when you finish a note or a Discord session, or when you tap 立即備份 in 設定 → 資料備份. **iOS:** the app's private storage. |
| **Settings** (provider preferences, vocabulary groups, webhook URLs) | On your device |
| **API keys** for OpenAI / Groq / Gemini / Claude / AWS Bedrock, and the access token of a Discord session that hasn't finished yet | On your device, in **Android Keystore / iOS Keychain** (encrypted by the OS) |
| **Error log**: the app's own error messages from the last 30 days | On your device, in the app's cache folder (see below) |

**About the Android media folder.** Audio files and the database backup are kept outside the app's private storage so they survive a reinstall: Android does **not** delete this folder when you uninstall WeaveNote, and if you reinstall, the app restores your notes from the backup. Because it is shared media storage, you can open the files with a file manager or over USB, and Android makes the audio files visible to other apps you have allowed to access audio (for example a music player).

**The error log never leaves your device.** The app records its own error messages (for example a failed network request or transcription) so problems can be diagnosed. It keeps the last 30 days, at most 500 entries, in the app's cache folder, which the OS may clear (for example when storage runs low or you clear the cache). API keys, access tokens and download-link signatures are masked before anything is written. You can view, copy or clear the log in 工程模式 → 錯誤紀錄 (工程模式 is unlocked by tapping the version number 10 times in 設定 → 關於). It only reaches us if you copy it and send it to us yourself.

**We run one server, and only for the Discord voice feature** (§2, item 5). It relays Discord voice audio to the app and keeps it for at most 24 hours. Your microphone recordings, transcripts, summaries and settings never go to it, and if you don't use the Discord feature the app doesn't contact it at all.

## 2. What gets sent off your device, and to whom

Your recordings and transcripts only go to services **you yourself configure**, and through our Discord bot if you use the Discord voice feature:

1. **The cloud STT provider you choose.** If you select OpenAI Whisper, Groq, Gemini, or AWS Bedrock Nova, your recording (or a chunk of it) is sent over HTTPS to that provider's API using **your own** API key. If you enter your own server address for an OpenAI-compatible service, it goes to that server instead. Their privacy policy applies:
   - OpenAI: <https://openai.com/policies/privacy-policy>
   - Groq: <https://groq.com/privacy-policy/>
   - Google (Gemini): <https://policies.google.com/privacy>
   - Anthropic (Claude — text post-processing only): <https://www.anthropic.com/legal/privacy>
   - AWS: <https://aws.amazon.com/privacy/>

   Before a short segment (under 10 seconds) goes to a cloud STT provider, the app checks **on your device** whether anyone is speaking in it, using two small models bundled with the app (Silero VAD and the CED-tiny sound classifier). Segments with no speech, such as silence, breathing or Discord notification sounds, are not sent; you can still send one yourself with ↻. This check runs offline and sends nothing anywhere.
2. **The LLM provider you choose for "AI 整理" (post-processing) and summaries.** Same as above — text transcripts get sent to your selected LLM API (OpenAI, Groq, Gemini, Claude, or AWS Bedrock).
3. **Webhook URLs you configure.** If you add a webhook destination, the transcript and/or audio file is POSTed to that URL when a note is finished, and sent again when its transcript, title or summary changes. Discord channel webhooks receive text only (transcript and summary), never audio.
4. **Model downloads.** When you choose Local Whisper, the model file (~75 MB – 3 GB depending on your size choice) is downloaded **once** from `huggingface.co/ggerganov/whisper.cpp`. After that, transcription happens fully offline and your microphone recordings leave the device only if you also configure a webhook. The first time you use the Discord voice feature, the app also downloads a speech model (SenseVoice, ~237 MB) from `huggingface.co`, over Wi-Fi only. Nothing from your notes is uploaded for these downloads.
5. **Our Discord bot (the Discord voice feature).** When you start a Discord voice note (開始 Discord 語音筆記), you paste a Discord voice channel link and the app asks our bot service (`weavenote.life.easier.tw`) to join that channel, sending it the channel's Discord server and channel IDs. While the bot is in the channel:
   - It receives the voice audio of **everyone who speaks in the channel**, separated per speaker, along with each speaker's Discord user ID and display name.
   - It runs automatic speech detection on the server and discards segments with no speech.
   - It converts each remaining segment to `.m4a`, stores it in Amazon S3 (AWS), and notifies the app over a WebSocket. The app downloads the file through a short-lived link and transcribes it with the STT provider you chose in item 1. **The bot does not transcribe or analyse what is said.**
   - Segments, and the session's list of speaker names, are **deleted automatically 24 hours** after upload.
   - The bot's server logs record technical events (Discord server, channel and user IDs, display names, timestamps) to keep the service running and fix problems. They contain no audio and no transcripts.

   The bot shows up in the channel's member list while it's there. You're recording other people, so let them know. Your use of Discord is covered by Discord's privacy policy: <https://discord.com/privacy>.
6. **Firebase App Check (Google / Apple).** So that only genuine copies of WeaveNote can start Discord sessions, the app uses Firebase App Check. When you start a Discord voice note, the app asks Google Play Integrity (Android) or Apple App Attest (iOS) to confirm it's an unmodified copy of WeaveNote on a genuine device, receives a single-use token from Firebase, and sends that token to our bot, which verifies it with Firebase. Google and Apple receive device-integrity signals for this under their own policies (<https://firebase.google.com/support/privacy>, <https://www.apple.com/legal/privacy/>). The token carries none of your recordings, transcripts or other content.
7. **Google AdMob.** The app shows banner ads. AdMob's SDK collects device-level signals to serve ads (ad ID, IP, OS version, etc.) according to <https://policies.google.com/technologies/ads>. We do not transmit your recordings, transcripts, or any personal content to AdMob.

We do not bundle any third-party analytics SDK (no Firebase Analytics, no Crashlytics, no Sentry). App Check (item 6) is the only Firebase service the app uses.

## 3. Permissions

| Permission | Why |
|---|---|
| `RECORD_AUDIO` | Core: capturing your voice notes. |
| `INTERNET` | Sending audio/transcripts to the STT/LLM/webhook services **you configure**, talking to our Discord bot when you use the Discord voice feature, and downloading on-device models on first use. Also used by AdMob. |
| `POST_NOTIFICATIONS` | Showing the persistent "recording in progress" notification so the OS doesn't kill recording when the screen is off. |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_MICROPHONE`, `WAKE_LOCK` | Same — keeps the recording alive in the background. |
| `FOREGROUND_SERVICE_DATA_SYNC` | Keeps a Discord voice note receiving, and AI 整理 running, while the app is in the background. |

## 4. Children

WeaveNote is not directed at children under 13. We do not knowingly collect data from children.

## 5. Your choices

- **Stop using cloud STT/LLM**: switch to "本地 Whisper" in settings to keep recordings on-device.
- **Don't use the Discord voice feature** if you don't want audio to pass through our bot. Nothing is sent to it unless you start a Discord voice note.
- **Delete a recording or the entire note**: delete it from the note detail screen — both the audio file and transcript are removed from the device. On Android, the database backup is refreshed the next time a backup runs, so a deleted note's text can stay in the backup until then. Discord audio on our bot's storage is deleted within 24 hours either way.
- **Clear the error log**: 工程模式 → 錯誤紀錄 → 清除, or clear the app's cache in the system settings.
- **Reset the app**: uninstall WeaveNote. On iOS this removes all app data. On Android it removes the app's private data (transcripts, settings, stored API keys, error log) but **not** the media folder `/sdcard/Android/media/com.easierlife.weavenote/` with your audio files and database backup; delete that folder with a file manager to remove them too.
- **Opt out of personalised ads**: Android Settings → Privacy → Ads → "Delete advertising ID".

## 6. Contact

Questions or requests: **<shiaukai@gmail.com>**.

## 7. Changes

If we change this policy we will update the date at the top and (if changes are material) note it in the app's release notes on Google Play.
