---
permalink: /custom-ai/
layout: bilingual
title: 自定 AI 帳號設定說明
title_en: Setting up a custom AI account
---

<!--
  App 連到這頁：自定帳號對話框的「設定說明與範例」、範本的「怎麼拿到這些資料」
  （weavenote/lib/features/settings/custom_endpoint_form.dart 的 kCustomAiGuide、
  ai-presets.json 的 guide），網址和各範例的 {#id} 不要改。
  App 的「從官網範本建立」讀的是 /ai-presets.json；這頁的 JSON 範例要跟它一致，
  改一邊就改另一邊。各家服務的網址、免費額度改了要回來更新。
-->

<div class="lang-zh" lang="zh-Hant" markdown="1">

# 自定 AI 帳號

WeaveNote 內建 OpenAI、Groq、Gemini、Claude 這幾家。其他服務只要支援 **OpenAI 相容格式**（大多數都支援），就能用「自定」帳號接上，例如 Cloudflare Workers AI、OpenRouter、自己電腦上的 Ollama 或 LM Studio、公司的 Azure OpenAI。

## 最簡單：從官網範本建立

1. 設定 → AI 帳號 → **從官網範本建立**
2. 選一個服務
3. 填它要的那幾格（例如 API Key）→ 建立
4. 設定 → AI 模型：校稿 / 摘要選這個帳號和模型

範本放在官網上，服務改網址或出了新的免費模型時，只要更新官網，不用更新 App。

## 貼上設定

在「從官網範本建立」頁按 **貼上設定（JSON）**，貼上下面範例的設定，或別人分享給你的設定。像 `{API_KEY}` 這種用大括號包起來的地方，下一步會請你填。

| 設定裡的欄位 | 對應 App 的 | 說明 |
|---|---|---|
| `name` | 名稱 | |
| `fields` | — | 大括號空格的說明文字，例如 `{"API_KEY": "API Token"}` |
| `chatUrl` | 對話網址 | 校稿和摘要用的**完整網址**，結尾通常是 `/v1/chat/completions` |
| `sttUrl` | 轉錄網址 | 選填，要轉錄才填，結尾通常是 `/v1/audio/transcriptions` |
| `auth` | 認證方式 | `bearer`（大部分服務）、`header`（再用 `authHeader` 指定 header 名稱，例如 Azure 的 `api-key`）、`none`（不需要 key） |
| `apiKey` | API Key | 通常寫 `{API_KEY}`，讓 App 問你 |
| `headers` | 其他 Headers | 選填，每個請求都會帶上 |
| `extraBody` | 額外參數 | 選填，會合併進校稿和摘要的請求內容，例如 `{"max_tokens": 16384}` |
| `chatModels`、`sttModels` | 對話模型、轉錄模型 | 「AI 模型」頁會列出來讓你直接選 |
| `modelsUrl` | 模型清單網址 | 選填，「從 API 更新清單」從這裡抓。沒填就用對話網址旁邊的 `/models`。OpenAI、Cloudflare、Ollama 格式的回應都看得懂 |

## 手動填

設定 → AI 帳號 → 新增帳號，服務商選「**自定（OpenAI 相容）**」，欄位跟上表一樣。其他 Headers 一行一個「名稱: 值」，因為可能放密碼，會加密存在手機上。

自己電腦上的服務可以用 `http://`；網路上的服務請用 `https://`（iOS 不允許用 http 連到網路上的伺服器）。

## 範例

### Cloudflare Workers AI {#cloudflare}

每天有 10,000 Neurons 的免費額度，台灣時間早上 8 點重置。

要準備：登入 [dash.cloudflare.com](https://dash.cloudflare.com)，到 **Workers AI** 頁面按 **Use REST API**，複製 **Account ID**；再按 **Create a Workers AI API Token** → **Create API Token** → **Copy API Token**。

```json
{
  "name": "Cloudflare Workers AI",
  "fields": { "ACCOUNT_ID": "帳戶 ID", "API_KEY": "API Token" },
  "chatUrl": "https://api.cloudflare.com/client/v4/accounts/{ACCOUNT_ID}/ai/v1/chat/completions",
  "modelsUrl": "https://api.cloudflare.com/client/v4/accounts/{ACCOUNT_ID}/ai/models/search?task=Text%20Generation&hide_experimental=true&per_page=200",
  "auth": "bearer",
  "apiKey": "{API_KEY}",
  "extraBody": { "max_tokens": 16384 },
  "chatModels": ["@cf/openai/gpt-oss-120b", "@cf/zai-org/glm-4.7-flash"]
}
```

`max_tokens` 要留著：Cloudflare 沒指定時，gpt-oss 只輸出 256 tokens（大約兩三百字），校稿和摘要都會被截斷。

### OpenRouter {#openrouter}

一把 key 就能用很多家的模型，其中有免費模型（名稱結尾是 `:free`）。`openrouter/free` 會自動挑一個免費模型。

要準備：到 [openrouter.ai/keys](https://openrouter.ai/keys) 建立 API Key。

```json
{
  "name": "OpenRouter",
  "fields": { "API_KEY": "API Key" },
  "chatUrl": "https://openrouter.ai/api/v1/chat/completions",
  "auth": "bearer",
  "apiKey": "{API_KEY}",
  "headers": { "HTTP-Referer": "https://weavenote.easier.tw", "X-OpenRouter-Title": "WeaveNote" },
  "chatModels": ["openrouter/free"]
}
```

- 免費模型每分鐘最多 20 次；帳號累積儲值不到 10 美元時每天 50 次，儲值過 10 美元以上每天 1,000 次。校稿一段、摘要一份各算一次。
- 免費模型的名單常常變，想挑別的就到「AI 模型」頁按「從 API 更新清單」，或到 [openrouter.ai/models](https://openrouter.ai/models) 找。
- 部分免費模型的供應商可能會保留或拿你送出的內容訓練模型，請看 OpenRouter 帳號裡的隱私設定。
- OpenRouter 不能轉錄。

### Ollama（自己的電腦） {#ollama}

模型跑在你自己的電腦上，錄音和逐字稿不會離開你家的網路。手機和電腦要連同一個 Wi-Fi，電腦要開著、不能睡眠。

1. 電腦安裝 [Ollama](https://ollama.com)，下載模型，例如 `ollama pull qwen3:8b`。
2. **讓手機連得到**：Ollama 預設只接受電腦自己的連線，要把 `OLLAMA_HOST` 設成 `0.0.0.0:11434`。macOS 在終端機執行 `launchctl setenv OLLAMA_HOST "0.0.0.0:11434"`，再重開 Ollama；Windows 在「環境變數」新增 `OLLAMA_HOST`，再重開 Ollama。
3. **加大上下文**：Ollama 預設只看 4096 tokens，校稿一段就超過，後面會被截掉。把 `OLLAMA_CONTEXT_LENGTH` 設成 `16384` 以上（macOS：`launchctl setenv OLLAMA_CONTEXT_LENGTH 16384`），電腦記憶體夠的話設 `32768`。
4. 查電腦的區域網路 IP，例如 `192.168.1.20`。

```json
{
  "name": "Ollama",
  "fields": { "HOST": "電腦的區域網路 IP" },
  "chatUrl": "http://{HOST}:11434/v1/chat/completions",
  "auth": "none"
}
```

建好後到「AI 模型」頁按「從 API 更新清單」，就會列出你下載過的模型。iPhone / iPad 第一次連線時會問要不要允許 WeaveNote 存取「區域網路」，要按允許。

### LM Studio（自己的電腦） {#lm-studio}

1. 在 [LM Studio](https://lmstudio.ai) 下載模型，載入時把上下文長度（Context Length）設成 16384 以上。
2. 到 **Developer** 頁開啟伺服器，並打開 **Serve on Local Network**。
3. 查電腦的區域網路 IP，例如 `192.168.1.20`。

```json
{
  "name": "LM Studio",
  "fields": { "HOST": "電腦的區域網路 IP" },
  "chatUrl": "http://{HOST}:1234/v1/chat/completions",
  "auth": "none"
}
```

建好後到「AI 模型」頁按「從 API 更新清單」選模型。如果你在 LM Studio 開了驗證，把 `auth` 改成 `bearer`，再加上 `"apiKey": "{API_KEY}"`。

### Azure OpenAI {#azure}

要準備：資源名稱（`xxx.openai.azure.com` 的 `xxx`）、部署名稱、API Key（Azure 入口網站 → 你的資源 → 金鑰與端點）。

```json
{
  "name": "Azure OpenAI",
  "fields": { "RESOURCE": "資源名稱", "DEPLOYMENT": "部署名稱", "API_KEY": "API Key" },
  "chatUrl": "https://{RESOURCE}.openai.azure.com/openai/v1/chat/completions",
  "auth": "header",
  "authHeader": "api-key",
  "apiKey": "{API_KEY}",
  "chatModels": ["{DEPLOYMENT}"]
}
```

- 模型名稱填的是**部署名稱**，不是模型名稱。
- 要用 Whisper 轉錄的話，加上 `"sttUrl": "https://{RESOURCE}.openai.azure.com/openai/deployments/{WHISPER}/audio/transcriptions?api-version=2024-06-01"` 和 `"sttModels": ["{WHISPER}"]`，`{WHISPER}` 是 Whisper 的部署名稱。
- 如果部署的是 o 系列或 GPT-5 這類推理模型，而部署名稱不是 `o` 或 `gpt-5` 開頭，請加上 `"extraBody": {"temperature": 1}`（這類模型不接受其他溫度）；要限制輸出長度時用 `max_completion_tokens`，不要用 `max_tokens`。

## 常見問題

- **連不上自己電腦上的服務**：確認手機和電腦在同一個 Wi-Fi、IP 沒填錯、電腦防火牆允許那個 port、Ollama 有設 `OLLAMA_HOST`、iOS 有允許「區域網路」。
- **校稿或摘要被截斷**（結果最後出現「AI 輸出達到長度上限」）：在額外參數加大 `max_tokens`，或加大本機模型的上下文長度。
- **401 / 403**：API Key 錯了，或認證方式選錯。
- **404**：網址或模型名稱錯了。

錄音和逐字稿會直接從你的手機送到你填的網址，不會經過我們，詳見[隱私權政策](/privacy.html)。

</div>

<div class="lang-en" lang="en" markdown="1">

# Custom AI accounts

WeaveNote has OpenAI, Groq, Gemini and Claude built in. Any other service that speaks the **OpenAI-compatible format** (most do) can be added as a custom account — for example Cloudflare Workers AI, OpenRouter, Ollama or LM Studio on your own computer, or your company's Azure OpenAI.

## Easiest: from a website template

1. Settings → AI 帳號 (AI accounts) → **從官網範本建立** (create from a website template)
2. Pick a service
3. Fill in the few fields it asks for (e.g. your API key) → 建立 (create)
4. Settings → AI 模型 (AI models): pick this account and a model for 校稿 / summaries

The templates live on this website, so when a service changes its address or adds a free model, we update the website — no app update needed.

## Pasting a setup

On the template screen, tap **貼上設定（JSON）** (paste a setup) and paste one of the setups below, or one someone shared with you. Anything in braces, like `{API_KEY}`, is asked for in the next step.

| Setup field | In the app | What it is |
|---|---|---|
| `name` | Name | |
| `fields` | — | Labels for the brace placeholders, e.g. `{"API_KEY": "API Token"}` |
| `chatUrl` | Chat address | The **full URL** for 校稿 and summaries, usually ending in `/v1/chat/completions` |
| `sttUrl` | Transcription address | Optional, only to transcribe; usually ends in `/v1/audio/transcriptions` |
| `auth` | Authentication | `bearer` (most services), `header` (name the header in `authHeader`, e.g. Azure's `api-key`), `none` (no key) |
| `apiKey` | API key | Usually `{API_KEY}`, so the app asks you |
| `headers` | Other headers | Optional, sent with every request |
| `extraBody` | Extra parameters | Optional, merged into every 校稿 and summary request, e.g. `{"max_tokens": 16384}` |
| `chatModels`, `sttModels` | Chat / transcription models | Listed on the AI 模型 page for you to pick |
| `modelsUrl` | Models list address | Optional; where 從 API 更新清單 (update the list from the API) fetches from. Without it, `/models` next to the chat address. OpenAI-, Cloudflare- and Ollama-style answers are all understood |

## Filling it in by hand

Settings → AI 帳號 → 新增帳號 (add account), provider **自定（OpenAI 相容）** (custom, OpenAI-compatible); the fields are the ones above. Other headers go one `Name: value` per line; they may hold secrets, so they're stored encrypted on your phone.

A service on your own computer can use `http://`; anything on the internet needs `https://` (iOS doesn't allow plain http to internet servers).

## Examples

### Cloudflare Workers AI {#cloudflare-en}

The free plan gives 10,000 Neurons a day, reset at 00:00 UTC.

You'll need: sign in at [dash.cloudflare.com](https://dash.cloudflare.com), open **Workers AI**, click **Use REST API** and copy the **Account ID**; then **Create a Workers AI API Token** → **Create API Token** → **Copy API Token**.

```json
{
  "name": "Cloudflare Workers AI",
  "fields": { "ACCOUNT_ID": "Account ID", "API_KEY": "API Token" },
  "chatUrl": "https://api.cloudflare.com/client/v4/accounts/{ACCOUNT_ID}/ai/v1/chat/completions",
  "modelsUrl": "https://api.cloudflare.com/client/v4/accounts/{ACCOUNT_ID}/ai/models/search?task=Text%20Generation&hide_experimental=true&per_page=200",
  "auth": "bearer",
  "apiKey": "{API_KEY}",
  "extraBody": { "max_tokens": 16384 },
  "chatModels": ["@cf/openai/gpt-oss-120b", "@cf/zai-org/glm-4.7-flash"]
}
```

Keep `max_tokens`: without it, Cloudflare stops gpt-oss after 256 tokens and 校稿 and summaries come back cut off.

### OpenRouter {#openrouter-en}

One key for models from many providers, including free ones (names ending in `:free`). `openrouter/free` picks a free model for you.

You'll need: an API key from [openrouter.ai/keys](https://openrouter.ai/keys).

```json
{
  "name": "OpenRouter",
  "fields": { "API_KEY": "API Key" },
  "chatUrl": "https://openrouter.ai/api/v1/chat/completions",
  "auth": "bearer",
  "apiKey": "{API_KEY}",
  "headers": { "HTTP-Referer": "https://weavenote.easier.tw", "X-OpenRouter-Title": "WeaveNote" },
  "chatModels": ["openrouter/free"]
}
```

- Free models allow 20 requests a minute, and 50 a day — or 1,000 a day once you've bought at least US$10 of credits in total. Each 校稿 chunk or summary is one request.
- The free models change often; to pick another, tap 從 API 更新清單 on the AI 模型 page, or browse [openrouter.ai/models](https://openrouter.ai/models).
- Some free models' providers may keep your inputs or train on them; check the privacy settings in your OpenRouter account.
- OpenRouter doesn't transcribe.

### Ollama (your own computer) {#ollama-en}

The model runs on your computer, so recordings and transcripts never leave your home network. Your phone and computer need to be on the same Wi-Fi, and the computer must be on and awake.

1. Install [Ollama](https://ollama.com) and download a model, e.g. `ollama pull qwen3:8b`.
2. **Let your phone reach it**: by default Ollama only accepts connections from the computer itself. Set `OLLAMA_HOST` to `0.0.0.0:11434` — on macOS run `launchctl setenv OLLAMA_HOST "0.0.0.0:11434"` in Terminal and restart Ollama; on Windows add `OLLAMA_HOST` under environment variables and restart Ollama.
3. **Give it a bigger context**: Ollama reads only 4096 tokens by default, less than one 校稿 chunk, so the rest gets cut off. Set `OLLAMA_CONTEXT_LENGTH` to `16384` or more (macOS: `launchctl setenv OLLAMA_CONTEXT_LENGTH 16384`), or `32768` if the computer has the memory.
4. Find your computer's local IP address, e.g. `192.168.1.20`.

```json
{
  "name": "Ollama",
  "fields": { "HOST": "Your computer's local IP" },
  "chatUrl": "http://{HOST}:11434/v1/chat/completions",
  "auth": "none"
}
```

Then tap 從 API 更新清單 on the AI 模型 page to list the models you've downloaded. The first time, your iPhone or iPad asks whether WeaveNote may access the local network — allow it.

### LM Studio (your own computer) {#lm-studio-en}

1. Download a model in [LM Studio](https://lmstudio.ai) and set its context length to 16384 or more when loading it.
2. On the **Developer** tab, start the server and turn on **Serve on Local Network**.
3. Find your computer's local IP address, e.g. `192.168.1.20`.

```json
{
  "name": "LM Studio",
  "fields": { "HOST": "Your computer's local IP" },
  "chatUrl": "http://{HOST}:1234/v1/chat/completions",
  "auth": "none"
}
```

Then tap 從 API 更新清單 on the AI 模型 page to pick a model. If you turned on authentication in LM Studio, change `auth` to `bearer` and add `"apiKey": "{API_KEY}"`.

### Azure OpenAI {#azure-en}

You'll need: the resource name (the `xxx` in `xxx.openai.azure.com`), your deployment name, and an API key (Azure portal → your resource → Keys and Endpoint).

```json
{
  "name": "Azure OpenAI",
  "fields": { "RESOURCE": "Resource name", "DEPLOYMENT": "Deployment name", "API_KEY": "API Key" },
  "chatUrl": "https://{RESOURCE}.openai.azure.com/openai/v1/chat/completions",
  "auth": "header",
  "authHeader": "api-key",
  "apiKey": "{API_KEY}",
  "chatModels": ["{DEPLOYMENT}"]
}
```

- The model name is your **deployment name**, not the model's name.
- To transcribe with Whisper, add `"sttUrl": "https://{RESOURCE}.openai.azure.com/openai/deployments/{WHISPER}/audio/transcriptions?api-version=2024-06-01"` and `"sttModels": ["{WHISPER}"]`, where `{WHISPER}` is your Whisper deployment name.
- If you deployed a reasoning model (o-series, GPT-5) under a name that doesn't start with `o` or `gpt-5`, add `"extraBody": {"temperature": 1}` (those models accept no other temperature), and limit output with `max_completion_tokens`, not `max_tokens`.

## Troubleshooting

- **Can't reach a service on your computer**: check that phone and computer are on the same Wi-Fi, the IP is right, the computer's firewall allows the port, Ollama has `OLLAMA_HOST` set, and on iOS that local network access is allowed.
- **校稿 or a summary is cut off** (it ends with 「AI 輸出達到長度上限」): raise `max_tokens` in the extra parameters, or the local model's context length.
- **401 / 403**: wrong API key or authentication type.
- **404**: wrong address or model name.

Recordings and transcripts go straight from your phone to the address you entered, never through us — see the [privacy policy](/privacy.html?lang=en).

</div>
