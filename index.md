---
layout: bilingual
langs: [zh-Hant, zh-Hans, en, ja]
---

<!--
  首頁有四種語言（其他頁只有繁中和英文，見 _includes/lang-select.html），改內容時四段一起改。
  - 用語照 App 的介面（weavenote/docs/i18n.md 的用語對照、lib/l10n/app_*.arb），
    LINE 會議記錄頁上的按鈕名稱照 bot 的 nodejs/src/line/liff_i18n.ts。
  - 功能跟商店頁文字（weavenote/docs/store-listing.md）一致；還沒開放給一般使用者的
    功能不寫（例如工程模式裡的「網址匯入」）。官網不是 App Store 的頁面，可以寫
    「Bedrock 只有 Android 版」。
  - 「不做的事」要跟隱私權政策（privacy.md、weavenote/PRIVACY.md）一致。
  - 橫幅是 store-graphics-src/feature*.html 輸出的（見那裡的 README）。
-->

<style>
  .wn-banner { display: block; width: 100%; height: auto; border-radius: 12px; margin-bottom: 24px; }
  .wn-visually-hidden {
    position: absolute !important; width: 1px; height: 1px; overflow: hidden;
    clip: rect(0 0 0 0); white-space: nowrap;
  }
  .wn-stores { display: grid; grid-template-columns: repeat(2, minmax(0, 200px)); gap: 16px; }
  .wn-store {
    display: flex; flex-direction: column; align-items: center; gap: 2px;
    padding: 14px 14px 12px; border: 1px solid #e0e0e0; border-radius: 12px;
    color: #111 !important; text-decoration: none !important;
  }
  .wn-store:hover { border-color: #2a7a78; box-shadow: 0 2px 10px rgba(42, 122, 120, .18); }
  .wn-store img { width: 100%; max-width: 160px; height: auto; margin-bottom: 8px; }
  .wn-store span { font-size: 14px; color: #666; }
  .wn-stores-hint { margin-top: 10px; font-size: 14px; color: #666; }
</style>

<img class="wn-banner lang-zh" src="/assets/banner-zh.jpg" width="2048" height="1000" loading="lazy" alt="WeaveNote：段落式語音筆記，邊錄邊轉文字，AI 幫你整理重點">
<img class="wn-banner lang-zh-hans" src="/assets/banner-zh-hans.jpg" width="2048" height="1000" loading="lazy" alt="WeaveNote：段落式语音笔记，边录边转文字，AI 帮你整理重点">
<img class="wn-banner lang-en" src="/assets/banner-en.jpg" width="2048" height="1000" loading="lazy" alt="WeaveNote: voice notes in segments, transcribed as you record, tidied up by AI">
<img class="wn-banner lang-ja" src="/assets/banner-ja.jpg" width="2048" height="1000" loading="lazy" alt="WeaveNote：セグメントで録る音声ノート。録音しながら文字起こしし、AI が要点を整理">

<div class="lang-zh" lang="zh-Hant" markdown="1">

# WeaveNote
{: .wn-visually-hidden}

極簡的語音筆記 App，支援 Android 和 iOS（iPhone 與 iPad）：邊錄邊轉成逐字稿，再讓 AI 校稿、整理成摘要。轉文字和 AI 用的是你自己選的服務和 API 金鑰，也可以完全離線。由 **easierlife**（台灣）發行。

## 功能

- **邊錄邊轉文字**：自動切段，偵測到停頓或到了設定的時間就切一段，前一段馬上送去轉文字。螢幕關閉、切到其他 App 也會繼續錄。
- **沒人說話的段落不送出**：送去雲端轉文字之前，先在手機上檢查有沒有人說話。只有靜音、呼吸聲或通知音的段落不會送出，不浪費轉錄額度。
- **轉成文字**，用你選擇的服務：
  - **本地 Whisper**（在裝置上執行，模型下載一次之後就能完全離線）。
  - **雲端 STT**：Groq、OpenAI Whisper、Google Gemini 或 AWS Bedrock Nova（Bedrock 只有 Android 版），使用你自己的 API 金鑰。
  - **自定帳號**：其他支援 OpenAI 相容格式的服務（Cloudflare Workers AI、OpenRouter、自己電腦上的 Ollama 等）也能接，App 裡有現成的範本：[自定 AI 帳號設定說明](/custom-ai/)。
  - 轉錄語言可以每則筆記不同；常常中英夾雜的話，還能加上夾雜的語言。
- **AI 校稿**：把逐字稿送到 OpenAI／Groq／Gemini／Claude／Bedrock 或自定帳號，補標點、修正錯字和同音字。校稿放在原文旁邊，不會蓋掉原文。
- **摘要**：用摘要模版整理成重點摘要、會議記錄、學習筆記等，也能自己寫模版；一則筆記可以有好幾份摘要。可以排好幾個模型，前一個失敗就換下一個。摘要能匯出成 PDF 或圖片，也能直接分享、列印。
- **同步到其他 App**：筆記完成後，自動把摘要和逐字稿送到 Discord 的文字頻道或論壇頻道；之後改了逐字稿、標題或摘要，會直接更新原本那則訊息。也可以把錄音和／或逐字稿 POST 到你設定的任何網址（webhook）。
- **LINE 群組會議記錄**：把 WeaveNote 官方帳號邀進 LINE 群組，群組就有一個只有成員打得開的「會議記錄」頁面。你選擇同步的筆記，摘要和逐字稿會自動放上去，之後修改也會跟著更新，大家在 LINE 裡就能看。在群組裡 @WeaveNote 拿到連結，打開後複製「我的上傳網址」，貼到 App 的「同步到其他 App」→「LINE 群組會議記錄」就能開始。
- **Discord 語音筆記**：讓我們的 bot 加入 Discord 語音頻道，每位說話者的聲音會分段傳到 App、標上他們的 Discord 名稱，再由 App 用你選擇的服務轉成文字。[把 bot 加進你的伺服器](/discord/)。
- **自訂詞彙**：把人名、品牌和專有名詞提供給轉文字服務和 AI 校稿，讓它們寫對；你改了錯字，App 會建議加進詞彙。
- **匯入錄音**：把音訊檔或影片的聲音變成一則筆記。
- **分享卡片**：從 LINE 或其他 App 把語音訊息分享給 WeaveNote，不用離開那個 App 就能直接看逐字稿；想保留的話可以存成筆記。
- **說明和與會人**：記下誰在說話、錄音的主題，AI 校稿和摘要會參考這些內容；Discord 語音筆記的說話者會自動列進與會人。
- **介面語言**：繁體中文、简体中文、English、日本語，跟著手機的語言。

## 不做的事

- **筆記留在你的裝置上。**錄音、逐字稿、設定和 API 金鑰都在你的裝置上。我們的伺服器只用在兩個選用功能：Discord 語音筆記（把 Discord 的語音轉送給 App，24 小時內刪除），以及 LINE 群組會議記錄（只存你選擇同步到群組的筆記文字，不含錄音，保留到筆記被刪除為止）。
- **沒有分析 SDK。**沒有 Firebase Analytics、Crashlytics 或 Sentry。
- **不用帳號。**不需要註冊 WeaveNote 帳號，也沒有訂閱費。

App 透過 Google AdMob 顯示橫幅廣告，以維持免費。詳情請見隱私權政策。

## 下載

{% include store-links.html lang="zh" %}

## 連結

- [隱私權政策](/privacy.html)
- [把 WeaveNote 加進 Discord 伺服器](/discord/)
- 聯絡：<shiaukai@gmail.com>

</div>

<div class="lang-zh-hans" lang="zh-Hans" markdown="1">

# WeaveNote
{: .wn-visually-hidden}

极简的语音笔记 App，支持 Android 和 iOS（iPhone 和 iPad）：边录边转成逐字稿，再让 AI 校对、整理成摘要。转写和 AI 用的是你自己选的服务和 API key，也可以完全离线。由 **easierlife**（台湾）发行。

## 功能

- **边录边转文字**：自动切段，检测到停顿或到了设定的时间就切一段，前一段马上送去转写。屏幕关闭、切到其他 App 也会继续录音。
- **没人说话的段落不发送**：发送到云端转写之前，先在手机上检查有没有人说话。只有静音、呼吸声或通知音的段落不会发送，不浪费转写额度。
- **转成文字**，用你选择的服务：
  - **本地 Whisper**（在设备上运行，模型下载一次之后就能完全离线使用）。
  - **云端 STT**：Groq、OpenAI Whisper、Google Gemini 或 AWS Bedrock Nova（Bedrock 仅限 Android 版），使用你自己的 API key。
  - **自定义账号**：其他支持 OpenAI 兼容格式的服务（Cloudflare Workers AI、OpenRouter、自己电脑上的 Ollama 等）也能接入，App 里有现成的模板：[自定义 AI 账号设置说明](/custom-ai/)。
  - 每条笔记可以设置不同的转写语言；经常中英夹杂的话，还能加上夹杂的语言。
- **AI 校对**：把逐字稿发送到 OpenAI／Groq／Gemini／Claude／Bedrock 或自定义账号，补标点、改正错字和同音字。校对结果放在原文旁边，不会覆盖原文。
- **摘要**：用摘要模板整理成重点摘要、会议记录、学习笔记等，也可以自己写模板；一条笔记可以有好几份摘要。可以排好几个模型，前一个失败就换下一个。摘要可以导出成 PDF 或图片，也能直接分享、打印。
- **同步到其他 App**：笔记完成后，自动把摘要和逐字稿发送到 Discord 的文字频道或论坛频道；之后修改了逐字稿、标题或摘要，会直接更新原来那条消息。也可以把录音和／或逐字稿 POST 到你设置的任意网址（webhook）。
- **LINE 群组会议记录**：把 WeaveNote 官方账号邀请进 LINE 群组，群组就有一个只有成员能打开的“会议记录”页面。你选择同步的笔记，摘要和逐字稿会自动发布上去，之后修改也会跟着更新，大家在 LINE 里就能看。在群组里 @WeaveNote 获取链接，打开后复制“我的上传链接”，粘贴到 App 的“同步到其他 App”→“LINE 群组会议记录”就能开始使用。
- **Discord 语音笔记**：让我们的 bot 加入 Discord 语音频道，每位说话人的声音会分段传到 App、标上他们的 Discord 名称，再由 App 用你选择的服务转成文字。[把 bot 添加到你的服务器](/discord/)。
- **自定义词汇**：把人名、品牌和专有名词提供给转写服务和 AI 校对，让它们写对；你改正错字后，App 会建议加进词汇。
- **导入录音**：把音频文件或视频里的声音变成一条笔记。
- **分享卡片**：从 LINE 或其他 App 把语音消息分享给 WeaveNote，不用离开那个 App 就能直接看逐字稿；想保留的话可以保存为笔记。
- **说明和与会人**：记下谁在说话、录音的主题，AI 校对和摘要会参考这些内容；Discord 语音笔记的说话人会自动列入与会人。
- **界面语言**：繁體中文、简体中文、English、日本語，跟随手机的语言。

## 不做的事

- **笔记留在你的设备上。**录音、逐字稿、设置和 API key 都在你的设备上。我们的服务器只用于两个可选功能：Discord 语音笔记（把 Discord 的语音转发给 App，24 小时内删除），以及 LINE 群组会议记录（只保存你选择同步到群组的笔记文字，不含录音，保留到笔记被删除为止）。
- **没有分析 SDK。**没有 Firebase Analytics、Crashlytics 或 Sentry。
- **不用账号。**不需要注册 WeaveNote 账号，也没有订阅费。

App 通过 Google AdMob 显示横幅广告，以保持免费。详情请见隐私政策。

## 下载

{% include store-links.html lang="zh-Hans" %}

## 链接

- [隐私政策](/privacy.html)
- [把 WeaveNote 添加到 Discord 服务器](/discord/)
- 联系我们：<shiaukai@gmail.com>

</div>

<div class="lang-en" lang="en" markdown="1">

# WeaveNote
{: .wn-visually-hidden}

A minimal voice-note app for Android and iOS (iPhone and iPad): it transcribes as you record, then AI proofreads the transcript and sums it up. Transcription and AI run on services and API keys you choose — or fully offline. Published by **easierlife** (Taiwan).

## What it does

- **Transcribed as you record** — auto-split starts a new segment at each pause or after a set time, and sends the last one off to be transcribed right away. Recording carries on with the screen off or in another app.
- **Silent segments stay on your phone** — before a segment goes to a cloud transcription service, the app checks on your phone whether anyone is speaking. Segments with only silence, breathing or a notification sound aren't sent, so they don't use up your quota.
- **Transcribe** with the provider you choose:
  - **On-device Whisper** (runs on your device, fully offline after the model downloads once).
  - **Cloud STT** — Groq, OpenAI Whisper, Google Gemini, or AWS Bedrock Nova (Bedrock on Android only), using your own API key.
  - **Custom accounts** — any other OpenAI-compatible service (Cloudflare Workers AI, OpenRouter, Ollama on your own computer, …) works too, with ready-made templates in the app: [setting up a custom AI account](/custom-ai/).
  - Set the transcription language per note, plus a second language if you often mix two.
- **AI proofreading** — send the transcript to OpenAI / Groq / Gemini / Claude / Bedrock or a custom account to add punctuation and fix mistakes and homophones. The proofread version is kept beside the original, which is never overwritten.
- **Summaries** — summary templates turn a note into key points, meeting minutes, study notes and more, or write your own; a note can have several summaries. List more than one model and the next takes over if one fails. Export summaries as PDF or images, or share and print them.
- **Sync to other apps** — when a note is finished, its summary and transcript are sent to a Discord text or forum channel, and later changes to the transcript, title or summary update those messages in place. You can also POST the audio and/or transcript to any URL you configure (a webhook).
- **LINE group meeting records** — add the WeaveNote official account to a LINE group and the group gets a Meeting records page that only its members can open. The summaries and transcripts of the notes you choose to sync are posted there and kept up to date when you edit them, so everyone can read them right inside LINE. Mention @WeaveNote in the group to get the link, open it, copy "My upload URL" and paste it into the app under Sync to other apps → LINE group meeting records.
- **Discord voice notes** — have our bot join a Discord voice channel; each speaker's audio reaches the app as separate segments labelled with their Discord name, and the app transcribes them with the provider you chose. [Add the bot to your server](/discord/).
- **Custom vocabulary** — give names, brands and jargon to the transcription service and AI proofreading so they come out right; when you correct a word, the app suggests adding it.
- **Import recordings** — turn an audio file, or a video's soundtrack, into a note.
- **Share card** — share a voice message to WeaveNote from LINE or any other app and read its transcript right there, without leaving that app. Save it as a note if you want to keep it.
- **Description and attendees** — note who's talking and what the recording is about; AI proofreading and summaries take it into account. In a Discord voice note, the speakers are added as attendees for you.
- **App languages** — 繁體中文, 简体中文, English and 日本語, following your phone's language.

## What it doesn't do

- **Your notes stay on your device.** Recordings, transcripts, settings, and API keys live on your device. Our server is used by two optional features only: Discord voice notes (it relays Discord audio to the app and deletes it within 24 hours) and LINE group meeting records (it keeps the text of the notes you choose to sync to a group, never audio, until they're deleted).
- **No analytics SDK.** No Firebase Analytics, no Crashlytics, no Sentry.
- **No account.** No WeaveNote account to sign up for, and no subscription.

The app shows banner ads via Google AdMob to keep it free. See the privacy policy for details.

## Get it

{% include store-links.html lang="en" %}

## Links

- [Privacy Policy](/privacy.html)
- [Add WeaveNote to your Discord server](/discord/)
- Contact: <shiaukai@gmail.com>

</div>

<div class="lang-ja" lang="ja" markdown="1">

# WeaveNote
{: .wn-visually-hidden}

Android と iOS（iPhone・iPad）に対応した、シンプルな音声ノートアプリです。録音しながら文字起こしし、AI が校正して要約にまとめます。文字起こしと AI には自分で選んだサービスと API key を使い、完全オフラインでも使えます。発行元は **easierlife**（台湾）です。

## 機能

- **録音しながら文字起こし**：自動分割で、間が空いたときや設定した時間ごとにセグメントを区切り、直前のセグメントをすぐ文字起こしに送ります。画面を消しても、ほかのアプリに切り替えても録音は続きます。
- **無音のセグメントは送信しない**：クラウドの文字起こしに送る前に、発話があるかをスマートフォン上でチェックします。無音や息づかい、通知音だけのセグメントは送らないので、利用枠を無駄にしません。
- **文字起こし**：使うサービスを選べます。
  - **端末内 Whisper**（端末上で動作。モデルを一度ダウンロードすれば、完全にオフラインで使えます）。
  - **クラウド STT**：Groq、OpenAI Whisper、Google Gemini、AWS Bedrock Nova（Bedrock は Android 版のみ）。ご自身の API key を使います。
  - **カスタムアカウント**：OpenAI 互換の形式に対応したほかのサービス（Cloudflare Workers AI、OpenRouter、自分のパソコンで動かす Ollama など）にも接続でき、アプリにはすぐ使えるテンプレートがあります：[カスタム AI アカウントの設定方法](/custom-ai/)（英語）。
  - 文字起こしの言語はノートごとに設定でき、2 つの言語が混ざる場合はもう 1 つの言語も指定できます。
- **AI 校正**：文字起こしを OpenAI／Groq／Gemini／Claude／Bedrock またはカスタムアカウントに送り、句読点を補って誤字や同音異義語を直します。校正結果は原文の横に保存され、原文は上書きされません。
- **要約**：要約テンプレートで要点まとめ・議事録・学習ノートなどにまとめられ、テンプレートを自分で作ることもできます。1 つのノートに複数の要約を作れます。モデルを複数並べておけば、1 つが失敗しても次のモデルに切り替わります。要約は PDF や画像で書き出したり、そのまま共有・印刷したりできます。
- **他のアプリと同期**：ノートが完成すると、要約と文字起こしを Discord のテキストチャンネルまたはフォーラムチャンネルに自動で送ります。あとで文字起こし・タイトル・要約を変更すると、そのメッセージがそのまま更新されます。録音や文字起こしを、設定した任意の URL に POST する（Webhook）こともできます。
- **LINE グループ議事録**：WeaveNote の公式アカウントを LINE グループに招待すると、メンバーだけが開ける「議事録」ページがそのグループにできます。同期を選んだノートの要約と文字起こしが自動で投稿され、編集するとそちらも更新されるので、みんな LINE の中で読めます。グループで @WeaveNote にメンションしてリンクを受け取り、開いた画面で「自分専用のアップロード URL」をコピーして、アプリの「他のアプリと同期」→「LINE グループ議事録」に貼り付ければ始められます。
- **Discord 音声ノート**：Discord のボイスチャンネルに bot を参加させると、話者ごとの音声がセグメントに分かれ、Discord の名前付きでアプリに届きます。文字起こしは、選んだサービスを使ってアプリが行います。[bot をサーバーに追加](/discord/)（英語）。
- **カスタム語彙**：人名やブランド名、専門用語を文字起こしサービスと AI 校正に渡して、正しく書けるようにします。誤字を直すと、アプリが語彙への追加を提案します。
- **録音をインポート**：音声ファイルや動画の音声をノートにします。
- **共有カード**：LINE などのアプリから音声メッセージを WeaveNote に共有すると、そのアプリを離れずに文字起こしを読めます。残しておきたいときはノートとして保存できます。
- **説明と参加者**：誰が話しているか、何の録音かを書いておくと、AI 校正や要約がそれを参考にします。Discord 音声ノートでは、話者が自動で参加者に追加されます。
- **表示言語**：繁體中文、简体中文、English、日本語。スマートフォンの言語に合わせて切り替わります。

## しないこと

- **ノートは端末の中に。**録音、文字起こし、設定、API key はすべて端末に保存されます。私たちのサーバーを使うのは、次の 2 つのオプション機能だけです：Discord 音声ノート（Discord の音声をアプリに中継し、24 時間以内に削除）と、LINE グループ議事録（グループへの同期を選んだノートのテキストだけを保存。録音は含まず、ノートが削除されるまで保持）。
- **分析 SDK なし。**Firebase Analytics、Crashlytics、Sentry は使っていません。
- **アカウント不要。**WeaveNote のアカウント登録は不要で、サブスクリプションもありません。

無料で提供するため、アプリには Google AdMob のバナー広告が表示されます。詳しくはプライバシーポリシーをご覧ください。

## ダウンロード

{% include store-links.html lang="ja" %}

## リンク

- [プライバシーポリシー](/privacy.html)（英語）
- [WeaveNote を Discord サーバーに追加](/discord/)（英語）
- お問い合わせ：<shiaukai@gmail.com>

</div>
