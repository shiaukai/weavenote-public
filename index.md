---
layout: bilingual
---

<div class="lang-zh" lang="zh-Hant" markdown="1">

# WeaveNote

極簡的語音筆記 App，支援 Android 和 iOS（iPhone 與 iPad）：按下錄音，就能得到乾淨的逐字稿，也可以讓 LLM 幫你整理。由 **easierlife**（台灣）發行。

## 功能

- **錄製語音筆記**，可以在背景錄音：螢幕關閉時，系統也不會中止錄音。
- **轉成文字**，用你選擇的服務：
  - **本地 Whisper**（在裝置上執行，模型下載一次之後就能完全離線）。
  - **雲端 STT**：OpenAI Whisper、Groq、Google Gemini 或 AWS Bedrock Nova，使用你自己的 API 金鑰。
- **AI 整理**（選用的後製整理）：把逐字稿送到 OpenAI／Groq／Gemini／Claude／Bedrock 整理、摘要或改寫格式，同樣使用你自己的 API 金鑰。
- **Webhooks**：把錄音和／或逐字稿 POST 到你設定的任何網址（每一段完成時，或整則筆記完成時）。
- **Discord 語音筆記**：讓我們的 bot 加入 Discord 語音頻道，每位說話者的聲音會分段傳到 App、標上他們的 Discord 名稱，再由 App 用你選擇的服務轉成文字。[把 bot 加進你的伺服器](/discord/)。
- **自訂詞彙**：把專有名詞提供給 STT 服務，讓人名和術語寫對。
- **匯入錄音**：把音訊檔或影片的聲音變成一則筆記。
- **分享卡片**：從 LINE 或其他 App 把語音訊息分享給 WeaveNote，不用離開那個 App 就能直接看逐字稿；想保留的話可以存成筆記。
- **說明**：記下誰在說話、錄音的主題，AI 整理和摘要會參考這些內容。

## 不做的事

- **沒有存放筆記的後端。**錄音、逐字稿、設定和 API 金鑰都在你的裝置上。我們唯一營運的伺服器，是選用的 Discord 語音功能背後的 bot：它把 Discord 的語音轉送給 App，並在 24 小時內刪除。
- **沒有分析 SDK。**沒有 Firebase Analytics、Crashlytics 或 Sentry。
- **不用帳號。**不需要註冊，也不需要登入。

App 透過 Google AdMob 顯示橫幅廣告，以維持免費。詳情請見隱私權政策。

## 下載

- **Google Play**：<https://play.google.com/store/apps/details?id=com.easierlife.weavenote>
- **App Store**：<https://apps.apple.com/tw/app/weavenote/id6765639488>

## 連結

- [隱私權政策](/privacy.html)
- [把 WeaveNote 加進 Discord 伺服器](/discord/)
- 聯絡：<shiaukai@gmail.com>

</div>

<div class="lang-en" lang="en" markdown="1">

# WeaveNote

A minimal voice-note app for Android and iOS (iPhone and iPad): hit record, get a clean transcript, optionally let an LLM tidy it up. Published by **easierlife** (Taiwan).

## What it does

- **Record voice notes** in the background — the OS won't kill recording when your screen is off.
- **Transcribe** with the provider you choose:
  - **Local Whisper** (on-device, fully offline after the model downloads once).
  - **Cloud STT** — OpenAI Whisper, Groq, Google Gemini, or AWS Bedrock Nova, using your own API key.
- **AI 整理** (optional post-processing) — send the transcript to OpenAI / Groq / Gemini / Claude / Bedrock to clean it up, summarise, or reformat. Again, your own API key.
- **Webhooks** — POST the audio and/or transcript to any URL you configure (per-segment or when the note is finalised).
- **Discord voice notes** — have our bot join a Discord voice channel; each speaker's audio reaches the app as separate segments labelled with their Discord name, and the app transcribes them with the provider you chose. [Add the bot to your server](/discord/).
- **Vocabulary groups** — feed domain-specific terms to the STT provider so names and jargon come out right.
- **Import recordings** — turn an audio file, or a video's soundtrack, into a note.
- **Share card** — share a voice message to WeaveNote from LINE or any other app and read its transcript right there, without leaving that app. Save it as a note if you want to keep it.
- **說明 (description)** — note who's talking and what the recording is about; AI 整理 and summaries take it into account.

## What it doesn't do

- **No backend for your notes.** Recordings, transcripts, settings, and API keys live on your device. The only server we run is the bot behind the optional Discord voice feature, which relays Discord audio to the app and deletes it within 24 hours.
- **No analytics SDK.** No Firebase Analytics, no Crashlytics, no Sentry.
- **No account.** No sign-up, no login.

The app shows banner ads via Google AdMob to keep it free. See the privacy policy for details.

## Get it

- **Google Play**: <https://play.google.com/store/apps/details?id=com.easierlife.weavenote>
- **App Store**: <https://apps.apple.com/tw/app/weavenote/id6765639488>

## Links

- [Privacy Policy](/privacy.html)
- [Add WeaveNote to your Discord server](/discord/)
- Contact: <shiaukai@gmail.com>

</div>
