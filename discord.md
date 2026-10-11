---
permalink: /discord/
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

# 把 WeaveNote 加進 Discord 伺服器

WeaveNote 的「Discord 語音筆記」會請 WeaveNote bot 進語音頻道收音，把每個人說的話分開轉成文字。使用前要先把 bot 加進你的 Discord 伺服器，每個伺服器只要加一次。

<p><a class="wn-invite" href="https://weavenote.life.easier.tw/invite">把 WeaveNote 加進伺服器</a></p>

<div class="wn-qr">
  <img src="/assets/discord-invite-qr.svg" alt="邀請連結的 QR code">
  <p>在電腦上看這頁的話，也可以用手機掃描，在手機上把 WeaveNote 加進伺服器。</p>
</div>

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

## In English

Add WeaveNote to your Discord server with the button above. You need the **Manage Server** permission on that server; if you don't have it, send this page to a server admin. For a private voice channel, also give the bot **View Channel**, **Connect** and **Speak** in that channel's permissions. You can also add it from the bot's profile in Discord (**Add App**). What the bot collects and how long it's kept: [Privacy Policy](/privacy.html), section 2, item 5.
