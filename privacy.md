---
permalink: /privacy.html
layout: bilingual
title: 隱私權政策
title_en: Privacy Policy
---

<div class="lang-zh" lang="zh-Hant" markdown="1">

# WeaveNote 隱私權政策

**最後更新：2026-10-11**

WeaveNote（以下稱「**我們**」、「**本 App**」）由 **easierlife**（個人品牌，台灣；<shiaukai@gmail.com>）發行。本頁說明 App 會處理哪些資料、資料會送到哪裡，以及你有哪些選擇。這個 App 刻意只收集最少的資料，所以我們盡量寫得簡短、具體。

本政策另有英文版（English）；中英文版本內容如有出入，以英文版為準。

## 1. App 處理的資料

| 類型 | 存放位置 |
|------|---------------|
| 筆記的**錄音檔**：麥克風錄的和匯入檔案產生的 `.wav`，以及透過 Discord 語音功能收到、或從 iOS 分享卡片存下的 `.m4a` 片段 | **Android：**共用儲存空間中 App 的媒體資料夾（`/sdcard/Android/media/com.easierlife.weavenote/notes/`）。**iOS：**App 的私有儲存空間。 |
| **逐字稿、摘要、筆記標題和說明**（你可以替筆記寫的描述），以及每個 Discord 片段上說話者的 Discord 顯示名稱 | 你的裝置上，App 的私有儲存空間（`/data/data/com.easierlife.weavenote/`） |
| **你匯入或分享給 App 的檔案**（音訊，或影片的聲音） | 轉檔和轉錄期間放在 App 快取中的暫存複本，完成後刪除。分享到分享卡片的片段，只有在你按「存成筆記」時才會保留（見下文）。 |
| **資料庫備份**：上述逐字稿、摘要與筆記資訊的複本 | **Android：**`/sdcard/Android/media/com.easierlife.weavenote/db_backup/`，在你結束一則筆記或一場 Discord 接收、或在「設定 → 資料備份」按「立即備份」時更新。**iOS：**App 的私有儲存空間。 |
| **設定**（服務商偏好、詞彙群組、webhook 網址、你取名存下的 Discord 語音頻道） | 你的裝置上 |
| OpenAI／Groq／Gemini／Claude／AWS Bedrock 的 **API 金鑰**，以及尚未結束的 Discord 接收的存取權杖 | 你的裝置上，存放在 **Android Keystore／iOS 鑰匙圈**（由作業系統加密）。在 iOS 上，分享卡片會另外保存一份你的轉錄設定和 STT 金鑰，放在只有 App 和它的分享延伸功能共用的鑰匙圈項目中。 |
| **錯誤紀錄**：App 自己最近 30 天的錯誤訊息 | 你的裝置上，App 的快取資料夾（見下文）。在 iOS 上，分享卡片會先把錯誤存在 App 的共用容器，等下次開啟 App 時再移進紀錄。 |

**關於 Android 的媒體資料夾。**錄音檔和資料庫備份存放在 App 的私有儲存空間之外，所以重新安裝後仍會保留：解除安裝 WeaveNote 時，Android **不會**刪除這個資料夾；重新安裝後，App 會從備份還原你的筆記。因為這是共用的媒體儲存空間，你可以用檔案管理工具或透過 USB 開啟這些檔案，而你允許存取音訊的其他 App（例如音樂播放器）也看得到這些錄音檔。

**錯誤紀錄不會離開你的裝置。**App 會記錄自己的錯誤訊息（例如網路連線或轉錄失敗），方便診斷問題。紀錄保留最近 30 天、最多 500 筆，放在 App 的快取資料夾，作業系統可能會清除它（例如儲存空間不足或你清除快取時）。寫入之前會先遮蔽 API 金鑰、存取權杖和下載連結的簽章。你可以在「工程模式 → 錯誤紀錄」檢視、複製或清除紀錄（在「設定 → 關於」連點版本號 10 下即可開啟工程模式）。除非你自己複製並寄給我們，否則我們不會拿到這些紀錄。

**匯入和分享錄音。**你可以匯入音訊或影片檔（匯入錄音檔），或從其他 App 把檔案分享給 WeaveNote，例如 LINE 的語音訊息。檔案會在你的裝置上讀取和轉檔；影片只會用到聲音，畫面不會離開裝置。分享的檔案會開啟**分享卡片**，在你分享的那個 App 上方顯示逐字稿：它會把音訊送到你選擇的雲端 STT 服務商（第 2 節第 1 項），除非你按「存成筆記」，否則什麼都不保留；關閉卡片就會刪除暫存複本。在 Android 上，卡片會得知是哪個 App 分享了檔案，並把那個 App 的名稱用在筆記標題；除此之外不會從那個 App 收到任何東西（沒有聊天內容、傳送者或聯絡人資料）。在 iOS 上，卡片是 App 內附的分享延伸功能，只會使用雲端 STT 服務商。

**我們只營運一台伺服器，而且只用於 Discord 語音功能**（第 2 節第 5 項）。它把 Discord 的語音轉送給 App，最多保留 24 小時。你的麥克風錄音、逐字稿、摘要和設定都不會送到這台伺服器；如果你不使用 Discord 功能，App 完全不會連線到它。

## 2. 哪些資料會離開你的裝置，送給誰

你的錄音和逐字稿只會送到**你自己設定**的服務；使用 Discord 語音功能時，還會經過我們的 Discord bot：

1. **你選擇的雲端 STT（語音轉文字）服務商。**如果你選擇 OpenAI Whisper、Groq、Gemini 或 AWS Bedrock Nova，你的錄音（或你匯入、分享的檔案的音訊，或其中一段）會用**你自己的** API 金鑰，透過 HTTPS 送到該服務商的 API。如果你替 OpenAI 相容服務填入自己的伺服器位址，則會送到那台伺服器。各服務商的隱私權政策：
   - OpenAI：<https://openai.com/policies/privacy-policy>
   - Groq：<https://groq.com/privacy-policy/>
   - Google（Gemini）：<https://policies.google.com/privacy>
   - Anthropic（Claude，只用於文字的後製整理）：<https://www.anthropic.com/legal/privacy>
   - AWS：<https://aws.amazon.com/privacy/>

   短片段（10 秒以下）送到雲端 STT 服務商之前，App 會**在你的裝置上**用兩個隨 App 附帶的小模型（Silero VAD 和 CED-tiny 聲音分類器）檢查裡面有沒有人在說話。沒有人說話的片段，例如靜音、呼吸聲或 Discord 的通知音效，不會送出；你仍然可以按 ↻ 自己送出。這項檢查離線執行，不會傳送任何資料。分享卡片不做這項檢查：你分享片段就是為了轉錄它。
2. **你為「AI 整理」（後製整理）和摘要選擇的 LLM 服務商。**同上：文字逐字稿會送到你選的 LLM API（OpenAI、Groq、Gemini、Claude 或 AWS Bedrock）；如果你替筆記寫了說明，也會一起送出，讓 AI 知道是誰在說話、錄音的主題是什麼。
3. **你設定的 webhook 網址。**如果你新增了 webhook，筆記完成時會把逐字稿和／或錄音檔 POST 到該網址；逐字稿、標題或摘要變更時會再送一次。Discord 頻道 webhook 只會收到文字（逐字稿和摘要），不會收到音訊。
4. **本地 Whisper。**選擇在裝置上轉錄時，模型檔（依你選的大小約 75 MB～3 GB）會從 `huggingface.co/ggerganov/whisper.cpp` 下載**一次**。之後轉錄完全離線進行；除非你另外設定了 webhook，否則麥克風錄音不會離開裝置。
5. **我們的 Discord bot（Discord 語音功能）。**開始 Discord 語音筆記時，你會貼上 Discord 語音頻道的連結，App 會請我們的 bot 服務（`weavenote.life.easier.tw`）加入該頻道，並傳送該頻道的 Discord 伺服器 ID 和頻道 ID。bot 在頻道中時：
   - 它會收到**頻道中每一位說話者**的語音，依說話者分開，並附上每位說話者的 Discord 使用者 ID 和顯示名稱。
   - 它會在伺服器上自動偵測語音，丟棄沒有人說話的片段。
   - 它把其餘每個片段轉成 `.m4a`，存放在 Amazon S3（AWS），並透過 WebSocket 通知 App。App 透過短效連結下載檔案，再用你在第 1 項選擇的 STT 服務商轉錄。**bot 不會轉錄或分析說話的內容。**
   - 片段以及該場接收的說話者名單，會在上傳後 **24 小時自動刪除**。
   - bot 的伺服器紀錄會記下技術事件（Discord 伺服器、頻道和使用者 ID、顯示名稱、時間），用來維持服務運作和修正問題。紀錄中沒有音訊，也沒有逐字稿。

   bot 在頻道中時，會出現在頻道的成員列表。你錄的是別人的聲音，請先告訴他們。你對 Discord 的使用適用 Discord 的隱私權政策：<https://discord.com/privacy>。
6. **Firebase App Check（Google／Apple）。**為了只讓正版的 WeaveNote 能開始 Discord 接收，App 使用 Firebase App Check。開始 Discord 語音筆記時，App 會請 Google Play Integrity（Android）或 Apple App Attest（iOS）確認這是在真實裝置上、未經修改的 WeaveNote，從 Firebase 取得一次性的權杖，再把權杖送給我們的 bot，由 bot 向 Firebase 驗證。Google 和 Apple 會依各自的政策收到裝置完整性的訊號（<https://firebase.google.com/support/privacy>、<https://www.apple.com/legal/privacy/>）。這個權杖不包含你的錄音、逐字稿或其他內容。
7. **Google AdMob。**App 會顯示橫幅廣告。AdMob 的 SDK 會依 <https://policies.google.com/technologies/ads> 收集裝置層級的訊號來投放廣告（廣告 ID、IP、作業系統版本等）。我們不會把你的錄音、逐字稿或任何個人內容傳給 AdMob。

App 沒有內建任何第三方分析 SDK（沒有 Firebase Analytics、Crashlytics 或 Sentry）。App Check（第 6 項）是 App 唯一使用的 Firebase 服務。

## 3. 權限

| 權限 | 用途 |
|---|---|
| `RECORD_AUDIO` | 核心功能：錄下你的語音筆記。 |
| `INTERNET` | 把音訊／逐字稿送到**你設定**的 STT／LLM／webhook 服務、使用 Discord 語音功能時和我們的 Discord bot 連線，以及第一次使用時下載本地 Whisper 模型。AdMob 也會用到。 |
| `POST_NOTIFICATIONS` | 顯示常駐的「錄音中」通知，讓作業系統在螢幕關閉時不會中止錄音。 |
| `FOREGROUND_SERVICE`、`FOREGROUND_SERVICE_MICROPHONE`、`WAKE_LOCK` | 同上：讓錄音在背景持續進行。 |
| `FOREGROUND_SERVICE_DATA_SYNC` | App 在背景時，讓 Discord 語音筆記繼續接收、AI 整理繼續執行。 |

## 4. 兒童

WeaveNote 不是以 13 歲以下的兒童為對象。我們不會在知情的情況下收集兒童的資料。

## 5. 你的選擇

- **不使用雲端 STT／LLM**：在設定中改用「本地 Whisper」，讓錄音留在裝置上。（分享卡片一定會使用雲端服務商；請改從 App 內匯入檔案。）
- **說明留白**：如果你不想讓逐字稿以外的內容送到 LLM 服務商。
- **不使用 Discord 語音功能**：如果你不希望音訊經過我們的 bot。除非你開始 Discord 語音筆記，否則不會有任何資料送到 bot。
- **刪除錄音或整則筆記**：在筆記詳情畫面刪除，錄音檔和逐字稿都會從裝置上移除。在 Android 上，資料庫備份會在下一次備份時更新，所以在那之前，已刪除筆記的文字可能還留在備份中。我們 bot 儲存空間裡的 Discord 音訊，無論如何都會在 24 小時內刪除。
- **清除錯誤紀錄**：「工程模式 → 錯誤紀錄 → 清除」，或在系統設定中清除 App 的快取。
- **重設 App**：解除安裝 WeaveNote。在 iOS 上會移除所有 App 資料。在 Android 上會移除 App 的私有資料（逐字稿、設定、儲存的 API 金鑰、錯誤紀錄），但**不會**移除存放錄音檔和資料庫備份的媒體資料夾 `/sdcard/Android/media/com.easierlife.weavenote/`；要一併移除，請用檔案管理工具刪除這個資料夾。
- **停用個人化廣告**：Android 設定 → 隱私權 → 廣告 →「刪除廣告 ID」。iOS 不需要另外設定：App 不會跟你要求「允許追蹤」的權限（App 追蹤透明度），所以 AdMob 拿不到你裝置的廣告識別碼。

## 6. 聯絡我們

問題或請求：**<shiaukai@gmail.com>**。

## 7. 政策變更

如果我們修改本政策，會更新頁首的日期；如果是重大變更，也會在 Google Play 和 App Store 的版本資訊中說明。

</div>

<div class="lang-en" lang="en" markdown="1">

# WeaveNote Privacy Policy

**Last updated: 2026-10-11**

WeaveNote ("**we**", "**the app**") is published by **easierlife** (個人品牌, Taiwan; <shiaukai@gmail.com>). This page explains what data the app handles, where it goes, and what choices you have. We try to keep it short and concrete because the app is intentionally minimal in what it collects.

This policy is also available in Traditional Chinese (中文); if the two versions differ, the English version prevails.

## 1. Data the app handles

| Type | Where it lives |
|------|---------------|
| **Audio recordings** of your notes: `.wav` from the microphone and from files you import, `.m4a` segments received through the Discord voice feature or saved from the iOS share card | **Android:** the app's media folder on shared storage (`/sdcard/Android/media/com.easierlife.weavenote/notes/`). **iOS:** the app's private storage. |
| **Transcripts, summaries, note titles and 說明 (the description you can write for a note)**, plus the speaker's Discord display name on each Discord segment | On your device, in the app's private storage (`/data/data/com.easierlife.weavenote/`) |
| **Files you import or share to the app** (audio, or a video's soundtrack) | A temporary copy in the app's cache while it's converted and transcribed, deleted afterwards. A clip shared to the share card is kept only if you tap 存成筆記 (see below). |
| **Database backup**: a copy of the transcripts, summaries and note details above | **Android:** `/sdcard/Android/media/com.easierlife.weavenote/db_backup/`, refreshed when you finish a note or a Discord session, or when you tap 立即備份 in 設定 → 資料備份. **iOS:** the app's private storage. |
| **Settings** (provider preferences, vocabulary groups, webhook URLs, the Discord voice channels you save under a name) | On your device |
| **API keys** for OpenAI / Groq / Gemini / Claude / AWS Bedrock, and the access token of a Discord session that hasn't finished yet | On your device, in **Android Keystore / iOS Keychain** (encrypted by the OS). On iOS, the share card gets its own copy of your transcription settings and STT keys, in a Keychain item shared only between the app and its share extension. |
| **Error log**: the app's own error messages from the last 30 days | On your device, in the app's cache folder (see below). On iOS the share card keeps its errors in the app's shared container until the app next opens and moves them into the log. |

**About the Android media folder.** Audio files and the database backup are kept outside the app's private storage so they survive a reinstall: Android does **not** delete this folder when you uninstall WeaveNote, and if you reinstall, the app restores your notes from the backup. Because it is shared media storage, you can open the files with a file manager or over USB, and Android makes the audio files visible to other apps you have allowed to access audio (for example a music player).

**The error log never leaves your device.** The app records its own error messages (for example a failed network request or transcription) so problems can be diagnosed. It keeps the last 30 days, at most 500 entries, in the app's cache folder, which the OS may clear (for example when storage runs low or you clear the cache). API keys, access tokens and download-link signatures are masked before anything is written. You can view, copy or clear the log in 工程模式 → 錯誤紀錄 (工程模式 is unlocked by tapping the version number 10 times in 設定 → 關於). It only reaches us if you copy it and send it to us yourself.

**Importing and sharing recordings.** You can import an audio or video file (匯入錄音檔), or share one to WeaveNote from another app, for example a LINE voice message. The file is read and converted on your device; for a video only the soundtrack is used, and the picture never leaves the device. A shared file opens the **share card**, which shows the transcript over the app you shared from: it sends the audio to the cloud STT provider you chose (§2, item 1) and keeps nothing unless you tap 存成筆記 — closing the card deletes its temporary copy. On Android the card is told which app shared the file and uses that app's name in the note's title; it receives nothing else from that app (no chat, sender or contact details). On iOS the card is a share extension that's part of the app, and it only uses cloud STT providers.

**We run one server, and only for the Discord voice feature** (§2, item 5). It relays Discord voice audio to the app and keeps it for at most 24 hours. Your microphone recordings, transcripts, summaries and settings never go to it, and if you don't use the Discord feature the app doesn't contact it at all.

## 2. What gets sent off your device, and to whom

Your recordings and transcripts only go to services **you yourself configure**, and through our Discord bot if you use the Discord voice feature:

1. **The cloud STT provider you choose.** If you select OpenAI Whisper, Groq, Gemini, or AWS Bedrock Nova, your recording — or the audio of a file you import or share — (or a chunk of it) is sent over HTTPS to that provider's API using **your own** API key. If you enter your own server address for an OpenAI-compatible service, it goes to that server instead. Their privacy policy applies:
   - OpenAI: <https://openai.com/policies/privacy-policy>
   - Groq: <https://groq.com/privacy-policy/>
   - Google (Gemini): <https://policies.google.com/privacy>
   - Anthropic (Claude — text post-processing only): <https://www.anthropic.com/legal/privacy>
   - AWS: <https://aws.amazon.com/privacy/>

   Before a short segment (under 10 seconds) goes to a cloud STT provider, the app checks **on your device** whether anyone is speaking in it, using two small models bundled with the app (Silero VAD and the CED-tiny sound classifier). Segments with no speech, such as silence, breathing or Discord notification sounds, are not sent; you can still send one yourself with ↻. This check runs offline and sends nothing anywhere. The share card skips it: you shared the clip to have it transcribed.
2. **The LLM provider you choose for "AI 整理" (post-processing) and summaries.** Same as above — text transcripts get sent to your selected LLM API (OpenAI, Groq, Gemini, Claude, or AWS Bedrock), together with the note's 說明 if you wrote one, so the AI knows who is speaking and what the recording is about.
3. **Webhook URLs you configure.** If you add a webhook destination, the transcript and/or audio file is POSTed to that URL when a note is finished, and sent again when its transcript, title or summary changes. Discord channel webhooks receive text only (transcript and summary), never audio.
4. **Local Whisper.** When you choose the on-device option, the model file (~75 MB – 3 GB depending on your size choice) is downloaded **once** from `huggingface.co/ggerganov/whisper.cpp`. After that, transcription happens fully offline and your microphone recordings leave the device only if you also configure a webhook.
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
| `INTERNET` | Sending audio/transcripts to the STT/LLM/webhook services **you configure**, talking to our Discord bot when you use the Discord voice feature, and downloading the local Whisper model on first use. Also used by AdMob. |
| `POST_NOTIFICATIONS` | Showing the persistent "recording in progress" notification so the OS doesn't kill recording when the screen is off. |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_MICROPHONE`, `WAKE_LOCK` | Same — keeps the recording alive in the background. |
| `FOREGROUND_SERVICE_DATA_SYNC` | Keeps a Discord voice note receiving, and AI 整理 running, while the app is in the background. |

## 4. Children

WeaveNote is not directed at children under 13. We do not knowingly collect data from children.

## 5. Your choices

- **Stop using cloud STT/LLM**: switch to "本地 Whisper" in settings to keep recordings on-device. (The share card always uses a cloud provider; import the file from inside the app instead.)
- **Leave the 說明 empty** if you don't want anything beyond the transcript sent to your LLM provider.
- **Don't use the Discord voice feature** if you don't want audio to pass through our bot. Nothing is sent to it unless you start a Discord voice note.
- **Delete a recording or the entire note**: delete it from the note detail screen — both the audio file and transcript are removed from the device. On Android, the database backup is refreshed the next time a backup runs, so a deleted note's text can stay in the backup until then. Discord audio on our bot's storage is deleted within 24 hours either way.
- **Clear the error log**: 工程模式 → 錯誤紀錄 → 清除, or clear the app's cache in the system settings.
- **Reset the app**: uninstall WeaveNote. On iOS this removes all app data. On Android it removes the app's private data (transcripts, settings, stored API keys, error log) but **not** the media folder `/sdcard/Android/media/com.easierlife.weavenote/` with your audio files and database backup; delete that folder with a file manager to remove them too.
- **Opt out of personalised ads**: Android Settings → Privacy → Ads → "Delete advertising ID". On iOS there's nothing to switch off: the app never asks for permission to track you (App Tracking Transparency), so AdMob doesn't get your device's advertising identifier.

## 6. Contact

Questions or requests: **<shiaukai@gmail.com>**.

## 7. Changes

If we change this policy we will update the date at the top and (if changes are material) note it in the app's release notes on Google Play and the App Store.

</div>
