# gstack

[English](README.md) | **繁體中文**

> 「我想我大概從十二月起就幾乎沒有親自打過任何程式碼了，這是一個非常巨大的轉變。」—— [Andrej Karpathy](https://fortune.com/2026/03/21/andrej-karpathy-openai-cofounder-ai-agents-coding-state-of-psychosis-openclaw/)，No Priors podcast，2026年3月

聽到 Karpathy 說這話時，我想弄清楚他是怎麼辦到的。一個人怎麼能像二十人的團隊一樣出貨？Peter Steinberger 幾乎是靠自己、借助 AI 代理人建立了 [OpenClaw](https://github.com/openclaw/openclaw)——GitHub 上獲得了247,000顆星。革命已經來臨。一個擁有正確工具的獨立開發者，可以比傳統團隊移動得更快。

我是 [Garry Tan](https://x.com/garrytan)，[Y Combinator](https://www.ycombinator.com/) 的總裁兼執行長。我曾與數千家新創公司合作——Coinbase、Instacart、Rippling——當時他們只是一兩個人在車庫裡。在加入 YC 之前，我是 Palantir 最早的工程師/PM/設計師之一，共同創辦了 Posterous（後來被 Twitter 收購），並建立了 YC 的內部社群網路 Bookface。

**gstack 是我的答案。** 我做產品已經二十年了，而現在我比以往任何時候都出貨更多程式碼。在過去60天裡：**超過60萬行的生產程式碼**（35% 為測試），**每天一萬到兩萬行**，兼職進行，同時全職運作 YC。這是我在3個專案中執行 `/retro` 的最新結果：**新增了140,751行，362次提交，一週內淨增約115K行**。

**2026年——1,237次貢獻，還在增加中：**

![2026年 GitHub 貢獻——1,237次貢獻，一到三月急劇加速](docs/images/github-2026.png)

**2013年——當我在 YC 建立 Bookface 時（772次貢獻）：**

![2013年 GitHub 貢獻——在 YC 建立 Bookface 時772次貢獻](docs/images/github-2013.png)

同一個人。不同的時代。差異在於工具。

**gstack 就是我的方法。** 它將 Claude Code 轉化為一支虛擬工程團隊——一位重新思考產品的執行長、一位確認架構的工程主管、一位找出 AI 劣質作品的設計師、一位找到生產環境 bug 的審查員、一位開啟真實瀏覽器的 QA 主管、一位執行 OWASP + STRIDE 安全稽核的資安長，以及一位負責出貨 PR 的發布工程師。二十位專家和八個強力工具，全部都是斜線指令，全部都是 Markdown，全部免費，MIT 授權。

這是我的開源軟體工廠。我每天都在用它。我分享它，因為這些工具應該讓所有人都能使用。

Fork 它。改進它。讓它變成你的。如果你想批評免費開源軟體——你當然可以，但我更希望你先試試看。

**這是為誰而設計的：**
- **創辦人和執行長**——尤其是還想自己出貨的技術型人才
- **初次使用 Claude Code 的用戶**——有結構的角色，而不是空白的提示詞
- **技術主管和資深工程師**——每個 PR 都有嚴謹的審查、QA 和發布自動化

## 快速開始

1. 安裝 gstack（30秒——詳見下方）
2. 執行 `/office-hours`——描述你正在建立的東西
3. 對任何功能想法執行 `/plan-ceo-review`
4. 對任何有變更的分支執行 `/review`
5. 對你的測試環境 URL 執行 `/qa`
6. 停在這裡。你會知道這是否適合你。

## 安裝——30秒

**需求：** [Claude Code](https://docs.anthropic.com/en/docs/claude-code)、[Git](https://git-scm.com/)、[Bun](https://bun.sh/) v1.0+、[Node.js](https://nodejs.org/)（僅限 Windows）

### 第一步：安裝到你的電腦

開啟 Claude Code 並貼上以下內容。Claude 會完成其餘的工作。

> 安裝 gstack：執行 **`git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`**，然後在 CLAUDE.md 中新增一個「gstack」章節，說明要使用 gstack 的 /browse skill 進行所有網頁瀏覽，絕不使用 mcp\_\_claude-in-chrome\_\_\* 工具，並列出可用的 skills：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、/design-consultation、/design-shotgun、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、/connect-chrome、/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、/investigate、/document-release、/codex、/cso、/autoplan、/careful、/freeze、/guard、/unfreeze、/gstack-upgrade。然後詢問使用者是否也想將 gstack 新增到目前的專案，讓團隊成員都能使用。

### 第二步：新增到你的 repo，讓團隊成員也能使用（可選）

> 將 gstack 新增到此專案：執行 **`cp -Rf ~/.claude/skills/gstack .claude/skills/gstack && rm -rf .claude/skills/gstack/.git && cd .claude/skills/gstack && ./setup`**，然後在這個專案的 CLAUDE.md 中新增一個「gstack」章節，說明要使用 gstack 的 /browse skill 進行所有網頁瀏覽，絕不使用 mcp\_\_claude-in-chrome\_\_\* 工具，列出可用的 skills：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、/design-consultation、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、/investigate、/document-release、/codex、/cso、/autoplan、/careful、/freeze、/guard、/unfreeze、/gstack-upgrade，並告訴 Claude 如果 gstack skills 無法運作，執行 `cd .claude/skills/gstack && ./setup` 來建立二進位檔並註冊 skills。

真實檔案會被提交到你的 repo（不是子模組），所以 `git clone` 就能直接運作。所有內容都在 `.claude/` 裡面。不會碰你的 PATH，也不會在背景執行任何東西。

> **要貢獻或需要完整歷史？** 上述指令使用 `--depth 1` 來快速安裝。如果你打算貢獻或需要完整的 git 歷史，請改做完整複製：
> ```bash
> git clone https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
> ```

### Codex、Gemini CLI 或 Cursor

gstack 可以在任何支援 [SKILL.md 標準](https://github.com/anthropics/claude-code)的代理人上運作。Skills 存放在 `.agents/skills/` 並自動被發現。

安裝到單一 repo：

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .agents/skills/gstack
cd .agents/skills/gstack && ./setup --host codex
```

當 setup 從 `.agents/skills/gstack` 執行時，它會將生成的 Codex skills 安裝在同一個 repo 的旁邊，不會寫入 `~/.codex/skills`。

安裝一次供你的用戶帳戶使用：

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host codex
```

`setup --host codex` 會在 `~/.codex/skills/gstack` 建立執行時根目錄，並在頂層連結生成的 Codex skills。這可避免來源 repo 複製和技能目錄重複發現技能的問題。

或讓 setup 自動偵測你已安裝的代理人：

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host auto
```

對於 Codex 相容的主機，setup 現在同時支援 `.agents/skills/gstack` 的 repo 本地安裝和 `~/.codex/skills/gstack` 的使用者全域安裝。所有29個技能可在所有支援的代理人上運作。基於 hook 的安全技能（careful、freeze、guard）在非 Claude 主機上使用內嵌安全提示語句。

### Factory Droid

gstack 可與 [Factory Droid](https://factory.ai) 搭配使用。Skills 安裝到 `.factory/skills/`，並自動被發現。敏感技能（ship、land-and-deploy、guard）使用 `disable-model-invocation: true`，所以 Droids 不會自動調用它們。

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup --host factory
```

Skills 安裝到 `~/.factory/skills/gstack-*/`。重新啟動 `droid` 以重新掃描 skills，然後輸入 `/qa` 開始使用。

## 看它運作

```
你：    我想為我的行事曆建立一個每日簡報應用程式。
你：    /office-hours
Claude：[詢問痛點——具體的例子，而不是假設]

你：    多個 Google 日曆、事件資訊過時、地點錯誤。
        準備工作花了太長時間，而且結果還不夠好……

Claude：我要挑戰一下你的框架。你說的是「每日簡報應用程式」。
        但你實際上描述的是一個個人 AI 參謀長。
        [提取了5個你沒意識到自己在描述的功能]
        [挑戰了4個前提——你同意、不同意或調整]
        [生成了3個實作方法及估算工作量]
        建議：明天先出貨最小可行版本，從實際使用中學習。
        完整願景是3個月的專案——先從真正有效的每日簡報開始。
        [撰寫設計文件 → 自動饋送到下游技能]

你：    /plan-ceo-review
        [閱讀設計文件，挑戰範疇，執行10個章節的審查]

你：    /plan-eng-review
        [資料流、狀態機、錯誤路徑的 ASCII 圖表]
        [測試矩陣、失敗模式、安全考量]

你：    批准計畫。退出計畫模式。
        [在11個檔案中撰寫2,400行。約8分鐘。]

你：    /review
        [已自動修復] 2個問題。[請確認] 競爭條件 → 你批准修復。

你：    /qa https://staging.myapp.com
        [開啟真實瀏覽器，點擊流程，找到並修復一個 bug]

你：    /ship
        測試：42 → 51（新增9個）。PR：github.com/you/app/pull/42
```

你說「每日簡報應用程式」。代理人說「你在建立一個 AI 參謀長」——因為它傾聽了你的痛點，而不是你的功能需求。八個指令，端到端。這不是一個副駕駛，這是一支團隊。

## 衝刺

gstack 是一個流程，而不只是工具的集合。Skills 按照衝刺的順序執行：

**思考 → 計畫 → 建立 → 審查 → 測試 → 出貨 → 回顧**

每個技能都饋送到下一個。`/office-hours` 撰寫 `/plan-ceo-review` 閱讀的設計文件。`/plan-eng-review` 撰寫 `/qa` 使用的測試計畫。`/review` 發現 `/ship` 驗證已修復的 bug。沒有任何東西會被遺漏，因為每個步驟都知道之前發生了什麼。

| 技能 | 你的專家 | 他們做什麼 |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | 從這裡開始。六個強迫性問題，在你寫程式碼之前重新框架你的產品。挑戰你的框架，質疑前提，生成實作替代方案。設計文件饋送到每個下游技能。 |
| `/plan-ceo-review` | **執行長/創辦人** | 重新思考問題。找到請求中隱藏的十星產品。四種模式：擴展、選擇性擴展、維持範疇、縮減。 |
| `/plan-eng-review` | **工程主管** | 確認架構、資料流、圖表、邊界情況和測試。將隱藏的假設帶到表面。 |
| `/plan-design-review` | **資深設計師** | 對每個設計維度評分0-10，解釋10分是什麼樣子，然後編輯計畫以達到那個標準。AI 劣質偵測。互動式——每個設計選擇一個 AskUserQuestion。 |
| `/design-consultation` | **設計夥伴** | 從頭建立完整的設計系統。研究格局，提出創意風險，生成你實際產品的真實模型。 |
| `/review` | **資深工程師** | 找到通過 CI 但在生產環境中爆炸的 bug。自動修復明顯的問題。標記完整性缺口。 |
| `/investigate` | **除錯工程師** | 系統性的根本原因除錯。鐵律：沒有調查就沒有修復。追蹤資料流，測試假設，3次修復失敗後停止。 |
| `/design-review` | **會寫程式的設計師** | 與 /plan-design-review 相同的稽核，然後修復找到的問題。原子提交，前後截圖。 |
| `/design-shotgun` | **設計探索者** | 生成多個 AI 設計變體，在瀏覽器中開啟比較板，反覆迭代直到你批准一個方向。品味記憶偏向你的偏好。 |
| `/qa` | **QA 主管** | 測試你的應用程式，找到 bug，用原子提交修復它們，重新驗證。自動為每次修復生成回歸測試。 |
| `/qa-only` | **QA 報告員** | 與 /qa 相同的方法論，但只報告。純粹的 bug 報告，不修改程式碼。 |
| `/cso` | **資安長** | OWASP Top 10 + STRIDE 威脅模型。零雜訊：17個誤報排除，8/10以上信心門檻，獨立發現驗證。每個發現都包含具體的攻擊情境。 |
| `/ship` | **發布工程師** | 同步 main，執行測試，稽核覆蓋率，推送，開啟 PR。如果你沒有測試框架，會自動建立一個。 |
| `/land-and-deploy` | **發布工程師** | 合併 PR，等待 CI 和部署，驗證生產環境健康狀況。從「已批准」到「在生產環境中驗證」，一個指令搞定。 |
| `/canary` | **SRE** | 部署後監控迴圈。監看控制台錯誤、效能回退和頁面失敗。 |
| `/benchmark` | **效能工程師** | 基準頁面載入時間、Core Web Vitals 和資源大小。在每個 PR 上比較前後差異。 |
| `/document-release` | **技術文件工程師** | 更新所有專案文件以匹配你剛出貨的內容。自動發現過時的 README。 |
| `/retro` | **工程主管** | 具備團隊意識的每週回顧。每人明細、出貨連勝、測試健康趨勢、成長機會。`/retro global` 跨所有你的專案和 AI 工具（Claude Code、Codex、Gemini）執行。 |
| `/browse` | **QA 工程師** | 給代理人眼睛。真實的 Chromium 瀏覽器，真實的點擊，真實的截圖。每個指令約100毫秒。`$B connect` 以有頭模式啟動你的真實 Chrome——即時觀看每個動作。 |
| `/setup-browser-cookies` | **Session 管理員** | 從你的真實瀏覽器（Chrome、Arc、Brave、Edge）匯入 cookies 到無頭 session。測試需要驗證的頁面。 |
| `/autoplan` | **審查流程** | 一個指令，完整審查的計畫。自動執行 CEO → 設計 → 工程審查，並帶有編碼的決策原則。只將品味決策呈現給你批准。 |

### 強力工具

| 技能 | 做什麼 |
|-------|-------------|
| `/codex` | **第二意見**——來自 OpenAI Codex CLI 的獨立程式碼審查。三種模式：審查（通過/失敗門檻）、對抗性挑戰，以及開放諮詢。當 `/review` 和 `/codex` 都執行過同一個分支時，進行跨模型分析。 |
| `/careful` | **安全護欄**——在破壞性指令（rm -rf、DROP TABLE、force-push）之前發出警告。說「be careful」以啟用。可覆蓋任何警告。 |
| `/freeze` | **編輯鎖定**——將檔案編輯限制在一個目錄。防止除錯時在範疇外意外變更。 |
| `/guard` | **完整安全**——一個指令同時啟用 `/careful` + `/freeze`。生產工作的最大安全性。 |
| `/unfreeze` | **解鎖**——移除 `/freeze` 邊界。 |
| `/connect-chrome` | **Chrome 控制器**——使用側邊面板擴充功能以 gstack 控制你的真實 Chrome。即時觀看每個動作。 |
| `/setup-deploy` | **部署設定器**——`/land-and-deploy` 的一次性設定。偵測你的平台、生產 URL 和部署指令。 |
| `/gstack-upgrade` | **自我更新器**——將 gstack 升級到最新版本。偵測全域與vendored安裝，同步兩者，顯示變更內容。 |

**[每個技能的深度解析，含範例和理念 →](docs/skills.md)**

## 並行衝刺

gstack 在一個衝刺中運作良好。在十個同時運行時變得有趣起來。

**設計是核心。** `/design-consultation` 不只是選字體。它研究你領域中已有的東西，提出安全選擇和創意風險，生成你實際產品的真實模型，並寫出 `DESIGN.md`——然後 `/design-review` 和 `/plan-eng-review` 會讀取你的選擇。設計決策流遍整個系統。

**`/qa` 是一個巨大的解鎖。** 它讓我從6個並行工作者增加到12個。Claude Code 說 *「我看到問題了」*，然後實際修復它、生成回歸測試並驗證修復——這改變了我的工作方式。代理人現在有眼睛了。

**智慧審查路由。** 就像在運作良好的新創公司：執行長不必查看基礎設施 bug 修復，設計審查不需要用於後端變更。gstack 追蹤執行了哪些審查，找出什麼是合適的，然後做聰明的事。審查就緒儀表板在你出貨前告訴你你的狀況。

**測試一切。** `/ship` 如果你的專案沒有測試框架，會從頭建立一個。每次 `/ship` 執行都會產生覆蓋率稽核。每次 `/qa` bug 修復都會生成回歸測試。100% 測試覆蓋率是目標——測試讓 vibe coding 變得安全，而不是 yolo coding。

**`/document-release` 是你從未擁有過的工程師。** 它讀取你專案中的每個文件檔案，交叉參考 diff，並更新所有偏離的內容。README、ARCHITECTURE、CONTRIBUTING、CLAUDE.md、TODOS——全部自動保持最新。現在 `/ship` 自動調用它——文件不需要額外指令就能保持最新。

**真實瀏覽器模式。** `$B connect` 以有頭視窗啟動你的真實 Chrome，由 Playwright 控制。你觀看 Claude 點擊、填寫和導航，都是即時的——同一個視窗，同一個螢幕。頂部邊緣的微妙綠色光暈告訴你 gstack 控制哪個 Chrome 視窗。所有現有的 browse 指令都能不變地運作。`$B disconnect` 回到無頭模式。Chrome 擴充功能側邊面板顯示每個指令的即時活動饋送和一個你可以指揮 Claude 的聊天側邊欄。這是共同存在——Claude 不是在遠端控制一個隱藏的瀏覽器，它就坐在你旁邊，在同一個駕駛艙裡。

**側邊欄代理人——你的 AI 瀏覽器助手。** 在 Chrome 側邊面板中輸入自然語言指令，一個子 Claude 實例會執行它們。「導航到設定頁面並截圖。」「用測試資料填寫這個表單。」「瀏覽這個列表中的每個項目並提取價格。」每個任務最多5分鐘。側邊欄代理人在隔離的 session 中運行，所以它不會干擾你的主要 Claude Code 視窗。就像在瀏覽器中有了第二雙手。

**個人自動化。** 側邊欄代理人不只是為開發工作流程。例如：「瀏覽我孩子學校的家長入口網站，並將所有其他家長的姓名、電話號碼和照片加入我的 Google 聯絡人。」兩種方式取得驗證：（1）在有頭瀏覽器中登入一次——你的 session 會持續；或（2）執行 `/setup-browser-cookies` 從你的真實 Chrome 匯入 cookies。一旦驗證，Claude 就導航目錄、提取資料並建立聯絡人。

**當 AI 卡住時的瀏覽器移交。** 遇到 CAPTCHA、驗證牆或 MFA 提示？`$B handoff` 在完全相同的頁面上開啟一個可見的 Chrome，帶有你所有的 cookies 和標籤頁。解決問題，告訴 Claude 你完成了，`$B resume` 從中斷的地方繼續。在連續3次失敗後，代理人甚至會自動建議這個方式。

**多 AI 第二意見。** `/codex` 從 OpenAI 的 Codex CLI 獲得獨立審查——一個完全不同的 AI 看同一個 diff。三種模式：帶通過/失敗門檻的程式碼審查、主動嘗試破壞你程式碼的對抗性挑戰，以及帶有 session 連續性的開放諮詢。當 `/review`（Claude）和 `/codex`（OpenAI）都審查了同一個分支，你會得到一個跨模型分析，顯示哪些發現重疊，哪些是各自獨有的。

**按需安全護欄。** 說「be careful」，`/careful` 會在任何破壞性指令前發出警告——rm -rf、DROP TABLE、force-push、git reset --hard。`/freeze` 在除錯時將編輯鎖定在一個目錄，所以 Claude 不會意外「修復」不相關的程式碼。`/guard` 同時啟用兩者。`/investigate` 自動凍結到正在調查的模組。

**主動技能建議。** gstack 注意到你處於哪個階段——腦力激盪、審查、除錯、測試——並建議正確的技能。不喜歡？說「stop suggesting」，它會在各 session 中記住這個設定。

## 10-15個並行衝刺

gstack 在一個衝刺中很強大。在十個同時運行時是變革性的。

[Conductor](https://conductor.build) 在並行中執行多個 Claude Code session——每個都在自己的隔離工作空間中。一個 session 對新想法執行 `/office-hours`，另一個對 PR 執行 `/review`，第三個實作功能，第四個對測試環境執行 `/qa`，另外六個在其他分支上。全部同時進行。我定期執行10-15個並行衝刺——這是目前的實際最大值。

衝刺結構是使並行工作的原因。沒有流程，十個代理人就是十個混亂來源。有了流程——思考、計畫、建立、審查、測試、出貨——每個代理人確切知道該做什麼以及何時停下來。你管理它們的方式就像執行長管理團隊：關注重要的決策，讓其餘的自行運行。

---

免費，MIT 授權，開源。沒有付費層級，沒有候補名單。

我開源了我建立軟體的方式。你可以 fork 它並讓它成為你自己的。

> **我們正在招聘。** 想每天出貨10K+行程式碼並幫助強化 gstack？
> 來 YC 工作吧——[ycombinator.com/software](https://ycombinator.com/software)
> 極具競爭力的薪資和股權。舊金山，Dogpatch 區。

## 文件

| 文件 | 涵蓋內容 |
|-----|---------------|
| [技能深度解析](docs/skills.md) | 每個技能的理念、範例和工作流程（包含 Greptile 整合） |
| [開發者理念](ETHOS.md) | 開發者哲學：煮沸湖泊、先搜尋後建立、三層知識 |
| [架構](ARCHITECTURE.md) | 設計決策和系統內部結構 |
| [瀏覽器參考](BROWSER.md) | `/browse` 的完整指令參考 |
| [貢獻](CONTRIBUTING.md) | 開發設定、測試、貢獻者模式和開發模式 |
| [更新日誌](CHANGELOG.md) | 每個版本的新功能 |

## 隱私與遙測

gstack 包含**選擇加入**的使用遙測，以協助改進專案。以下是確切發生的事情：

- **預設是關閉的。** 除非你明確同意，否則不會向任何地方發送任何內容。
- **第一次執行時，** gstack 詢問你是否想分享匿名使用資料。你可以說不。
- **如果你選擇加入，發送的內容：** 技能名稱、持續時間、成功/失敗、gstack 版本、作業系統。就這樣。
- **從不發送的內容：** 程式碼、檔案路徑、repo 名稱、分支名稱、提示詞或任何使用者生成的內容。
- **隨時可變更：** `gstack-config set telemetry off` 立即停用所有內容。

資料存儲在 [Supabase](https://supabase.com)（開源 Firebase 替代品）。架構在 [`supabase/migrations/`](supabase/migrations/)——你可以精確驗證收集了什麼內容。repo 中的 Supabase 可發布密鑰是一個公開密鑰（就像 Firebase API 密鑰）——行級安全策略拒絕所有直接存取。遙測通過驗證過的 edge functions 流動，這些函數強制執行架構檢查、事件類型允許列表和欄位長度限制。

**本地分析始終可用。** 執行 `gstack-analytics` 從本地 JSONL 檔案查看你的個人使用儀表板——不需要遠端資料。

## 疑難排解

**技能沒有顯示？** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` 失敗？** `cd ~/.claude/skills/gstack && bun install && bun run build`

**安裝過時？** 執行 `/gstack-upgrade`——或在 `~/.gstack/config.yaml` 中設定 `auto_upgrade: true`

**想要更短的指令？** `cd ~/.claude/skills/gstack && ./setup --no-prefix`——從 `/gstack-qa` 切換到 `/qa`。你的選擇會被記憶以供未來升級。

**想要命名空間指令？** `cd ~/.claude/skills/gstack && ./setup --prefix`——從 `/qa` 切換到 `/gstack-qa`。如果你與其他技能包一起執行 gstack，這很有用。

**Codex 說「由於無效的 SKILL.md 而跳過載入技能」？** 你的 Codex 技能描述已過時。修復：`cd ~/.codex/skills/gstack && git pull && ./setup --host codex`——或對 repo 本地安裝：`cd "$(readlink -f .agents/skills/gstack)" && git pull && ./setup --host codex`

**Windows 使用者：** gstack 透過 Git Bash 或 WSL 在 Windows 11 上運作。除了 Bun 之外還需要 Node.js——Bun 在 Windows 上的 Playwright 管道傳輸有一個已知 bug（[bun#4253](https://github.com/oven-sh/bun/issues/4253)）。browse 伺服器會自動回退到 Node.js。確保 `bun` 和 `node` 都在你的 PATH 中。

**Claude 說它看不到技能？** 確保你的專案 `CLAUDE.md` 有一個 gstack 章節。加入這個：

```
## gstack
使用 gstack 的 /browse 進行所有網頁瀏覽。絕不使用 mcp__claude-in-chrome__* 工具。
可用技能：/office-hours、/plan-ceo-review、/plan-eng-review、/plan-design-review、
/design-consultation、/review、/ship、/land-and-deploy、/canary、/benchmark、/browse、
/qa、/qa-only、/design-review、/setup-browser-cookies、/setup-deploy、/retro、
/investigate、/document-release、/codex、/cso、/autoplan、/careful、/freeze、/guard、
/unfreeze、/gstack-upgrade。
```

## 授權

MIT。永久免費。去建立一些東西吧。
