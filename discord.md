---
permalink: /discord/
layout: bilingual
title: 把 WeaveNote 加進 Discord
title_en: Add WeaveNote to Discord
---

<!--
  App 和這頁都不寫 bot 的 client_id：按鈕和 QR 都連正式機 server 的 /invite，
  它會轉址到 server 目前登入的 bot 的邀請連結，換 bot 時這頁不用改。
  QR（assets/discord-invite-qr.svg）是用 macOS CoreImage 的 CIQRCodeGenerator
  產生的，內容就是 https://weavenote.life.easier.tw/invite。
-->

<style>
  .wn-invite {
    display: inline-block;
    padding: 12px 22px;
    border-radius: 8px;
    background: #5865f2;
    color: #fff !important;
    font-weight: 600;
    text-decoration: none !important;
  }
  .wn-invite:hover { background: #4752c4; }
  .wn-qr { display: none; }
  @media (min-width: 800px) {
    .wn-qr { display: flex; gap: 16px; align-items: center; margin-top: 16px; }
    .wn-qr img { width: 176px; height: 176px; }
  }
</style>

<div class="lang-zh" lang="zh-Hant" markdown="1">

# 把 WeaveNote 加進 Discord 伺服器

WeaveNote 的「Discord 語音筆記」會請 WeaveNote bot 進語音頻道收音，把每個人說的話分開轉成文字。使用前要先把 bot 加進你的 Discord 伺服器，每個伺服器只要加一次。

</div>

<div class="lang-en" lang="en" markdown="1">

# Add WeaveNote to your Discord server

WeaveNote's Discord voice notes have the WeaveNote bot join a voice channel and listen, so what each person says is transcribed separately. Before you start, add the bot to your Discord server — once per server.

</div>

<p><a class="wn-invite" href="https://weavenote.life.easier.tw/invite"><span class="lang-zh">把 WeaveNote 加進伺服器</span><span class="lang-en">Add WeaveNote to a server</span></a></p>

<div class="wn-qr">
  <img src="/assets/discord-invite-qr.svg" alt="QR code">
  <p><span class="lang-zh">在電腦上看這頁的話，也可以用手機掃描，在手機上把 WeaveNote 加進伺服器。</span><span class="lang-en">Reading this on a computer? Scan this with your phone to add WeaveNote from there.</span></p>
</div>

<div class="lang-zh" lang="zh-Hant" markdown="1">

## 誰可以加

要在那個伺服器有 **「管理伺服器」權限** 才能加 bot，通常是伺服器擁有者或管理員。

如果你只是一般成員，請把這個頁面的連結轉給管理員：<https://weavenote.easier.tw/discord/>

## 加入步驟

1. 點上面的按鈕。手機上會打開 Discord App 或瀏覽器，沒登入的話先登入 Discord。
2. 選擇要加入的伺服器，按「繼續」。
3. 確認 bot 要的權限（檢視頻道、連線、說話），按「授權」。

## 私人語音頻道

如果要錄的是私人語音頻道（不是每個成員都看得到的頻道），還要另外給 bot 權限：在該頻道按「編輯頻道」→「權限」，加入 WeaveNote（或它所在的身分組），開啟 **檢視頻道**、**連線**、**說話**。

## 也可以從 bot 的個人檔案加

在 Discord 裡看到 WeaveNote 時（例如在已經加了它的伺服器），點它的頭像，在個人檔案按「新增應用程式」，也能直接把它加進自己的伺服器。

## 加好之後

1. 在 Discord 對要錄的語音頻道按右鍵（手機上長按），選「複製連結」。
2. 打開 WeaveNote，在首頁按「Discord 語音筆記」，貼上連結，按「開始接收」。bot 會進入頻道收音，頻道裡的人都看得到它。
3. 講完在 App 按「結束筆記」，bot 會離開頻道，整場內容存成一則筆記。

開始錄之前，請先告訴頻道裡的人。bot 收什麼、存多久，請看[隱私權政策](/privacy.html)第 2 節第 5 項。

</div>

<div class="lang-en" lang="en" markdown="1">

## Who can add it

You need the **Manage Server** permission on that server, which usually means the server owner or an admin.

If you're a regular member, send this page to an admin: <https://weavenote.easier.tw/discord/?lang=en>

## Steps

1. Tap the button above. On a phone it opens the Discord app or your browser; sign in to Discord if asked.
2. Choose the server to add it to and tap **Continue**.
3. Check the permissions the bot asks for (View Channels, Connect, Speak) and tap **Authorize**.

## Private voice channels

For a private voice channel (one that not every member can see), the bot needs permission in that channel too: open the channel's **Edit Channel → Permissions**, add WeaveNote (or a role it has), and allow **View Channel**, **Connect** and **Speak**.

## Or from the bot's profile

Wherever you see WeaveNote in Discord (for example in a server that already has it), tap its avatar and choose **Add App** on its profile to add it to your own server.

## After that

1. In Discord, right-click the voice channel you want to record (long-press on a phone) and choose **Copy Link**.
2. In WeaveNote, tap **Discord 語音筆記** (Discord voice note) on the home screen, paste the link and tap **開始接收** (start). The bot joins the channel to listen; everyone in it can see it.
3. When you're done, tap **結束筆記** (finish) in the app. The bot leaves and the whole session is saved as one note.

Tell the people in the channel before you start recording. What the bot collects and how long it's kept: [Privacy Policy](/privacy.html), section 2, item 5.

</div>
