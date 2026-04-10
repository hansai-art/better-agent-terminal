# Better Agent Terminal

<div align="center">

<img src="assets/icon.png" width="128" height="128" alt="Better Agent Terminal">

![Version](https://img.shields.io/badge/version-2.1.21-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20|%20macOS%20|%20Linux-lightgrey.svg)
![Electron](https://img.shields.io/badge/electron-28.3.3-47848F.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

**一個跨平台的多工作區終端整合工具，內建 AI Agent 協作能力**

你可以把多個專案終端放在同一個視窗中管理，並直接搭配 **Claude Code、Gemini CLI、GitHub Copilot CLI、Codex CLI**，或任何你自己想接的 CLI Agent。它內建檔案瀏覽器、Git 檢視、程式碼片段管理、遠端連線，以及可以同時指揮多個 AI Agent 的 **Supervisor 模式**。

[下載最新版本](https://github.com/tony1223/better-agent-terminal/releases/latest)

</div>

---

## 畫面預覽

<div align="center">

**Claude Code Agent 面板** — 直接在 App 裡和 Agent 對話，還能控制權限與查看串流輸出
<img src="assets/screenshot-claude.png" alt="Claude Code Agent 面板" width="800">

**終端機面板** — 一邊跑長時間指令，一邊和 Agent 協作
<img src="assets/screenshot-terminal.png" alt="終端機面板" width="800">

**檔案瀏覽器** — 不離開 App 就能看專案檔案與預覽內容
<img src="assets/screenshot-files.png" alt="檔案瀏覽器" width="800">

**Git 檢視器** — 快速看提交紀錄與差異
<img src="assets/screenshot-git.png" alt="Git 檢視器" width="800">

</div>

---

## 功能特色

### 工作區管理
- **多工作區**：每個專案資料夾都能變成一個工作區
- **拖曳排序**：側邊欄可以自由調整工作區順序
- **群組整理**：把相似專案放到同一個群組
- **設定檔 Profiles**：可保存本機或遠端的工作狀態
- **分離視窗**：單一工作區可獨立跳出新視窗
- **工作區環境變數**：每個專案可有自己的環境參數
- **活動指示點**：快速看到哪個工作區正在忙

### 終端與檔案
- **多終端機**：一個工作區可以開很多個終端
- **Agent 預設**：快速建立 Claude、Gemini、Codex、Copilot 等 Agent 終端
- **自訂 CLI Agent**：把你自己的 CLI 工具加進來
- **Supervisor 模式**：一個終端負責指揮其他終端
- **Git worktree 隔離**：讓 Agent 在獨立 worktree 工作，降低誤傷主分支風險
- **檔案瀏覽器**：可搜尋、預覽、看語法高亮
- **Git 檢視**：看 commit、diff、變更檔案與分支資訊
- **Snippet 管理**：保存常用程式碼片段

### Claude Agent 整合
- **內建 Claude Code SDK**：不用另外切終端就能聊 Agent
- **串流輸出**：即時看到 Agent 正在做什麼
- **工具權限控制**：每次呼叫工具都能決定要不要放行
- **子任務追蹤**：可看到 sub-agent / task 的進度
- **恢復工作階段**：關掉 App 後下次可接著做
- **分支對話**：從目前進度開一個新的對話分頁
- **狀態列**：可顯示 token、成本、context、分支、回合數等資訊
- **圖片與檔案附加**：把圖片或檔案直接丟給 Agent

---

## 給完全新手的超詳細開始教學

> 這一段故意寫得很慢、很白話。你可以把自己想成「第一次學會用終端機的人」，照著做就好。

### 0. 先搞懂這個 App 在做什麼

想像你在做一個專題：
- **工作區** = 你的專題資料夾
- **終端機** = 你對電腦下指令的黑色視窗
- **Agent** = 會幫你讀程式、改程式、解釋程式的 AI 助手
- **Git** = 幫你記錄程式改過什麼的時間機器

Better Agent Terminal 做的事，就是把這些東西放在同一個地方，讓你不用一直切視窗。

### 1. 安裝 App

#### 方法 A：直接下載安裝檔（最適合新手）
1. 打開 [Releases 頁面](https://github.com/tony1223/better-agent-terminal/releases/latest)
2. 依照你的電腦系統下載：
   - **Windows**：下載安裝程式或 `.zip`
   - **macOS**：下載 `.dmg`
   - **Linux**：下載 `.AppImage`
3. 安裝完成後打開 Better Agent Terminal

#### 方法 B：macOS 用 Homebrew
```bash
brew tap tonyq-org/tap
brew install --cask better-agent-terminal
```

#### 方法 C：自己從原始碼建置
先安裝：
- Node.js 18+
- Claude Code CLI

然後執行：
```bash
git clone https://github.com/tony1223/better-agent-terminal.git
cd better-agent-terminal
npm install
npm run dev
```

---

## 新手第一次打開後，請照這個順序做

### 第一步：新增一個工作區
1. 看左邊側邊欄
2. 點 **「+ 新增工作區」**
3. 選你的專案資料夾
4. 成功後，左邊就會出現你的專案名稱

**這一步的意思：**
你是在告訴 App：「這個資料夾是我要工作的地方。」

### 第二步：看懂主要畫面
選到工作區後，你通常會看到幾個分頁：
- **終端**：拿來下指令
- **檔案**：看專案裡的檔案
- **Git**：看版本變化
- **GitHub**：看 PR / Issue（有設定好 gh CLI 時）

如果你只記一件事：
> **平常大多數時間，你會在「終端」和「Agent 面板」之間來回。**

### 第三步：先學會最基本的終端操作
在終端機裡可以輸入指令，例如：
```bash
pwd
ls
npm install
npm run dev
```

如果你完全不懂這些指令，可以先這樣記：
- `pwd`：我現在站在哪個資料夾？
- `ls`：這個資料夾裡有什麼？
- `npm install`：安裝專案需要的套件
- `npm run dev`：啟動開發模式

### 第四步：開始和 Agent 說話
如果你有建立 Agent 終端或 Claude Agent 面板，就能直接輸入需求，例如：
- 幫我解釋這個專案的檔案結構
- 幫我找登入功能在哪裡
- 幫我修正這個錯誤訊息
- 幫我把這個畫面翻成繁體中文

**新手秘訣：**
不要一次丟太大題。先問小問題，例如：
1. 這個專案入口檔在哪裡？
2. 這個按鈕的文字是在哪個檔案寫的？
3. 改這個功能前我應該先看哪三個檔案？

這樣 Agent 比較容易回答準，自己也比較不會亂掉。

### 第五步：看檔案，不要亂翻資料夾
切到 **檔案** 分頁後：
1. 左邊可以找檔案
2. 右邊可以預覽內容
3. 上方搜尋框可以直接找檔名
4. 右鍵可複製相對路徑或絕對路徑

**什麼時候用檔案分頁？**
- 你知道自己要找哪個檔案
- 你想快速看 README、設定檔、元件檔
- 你想先閱讀，不急著修改

### 第六步：看 Git，不要怕改壞
切到 **Git** 分頁後，你可以看到：
- 最近的提交紀錄
- 哪些檔案有改動
- 某個檔案改了哪些行

這很重要，因為：
> 寫程式不是「一次寫對」，而是「改了以後知道自己改了什麼」。

### 第七步：學會安全地請 Agent 幫忙
你可以這樣下指令：
1. **先問**：請先告訴我你打算改哪些檔案
2. **再做**：確認後再請它修改
3. **最後驗證**：請它幫你跑 build 或 tests

推薦句型：
- 先不要改，先告訴我你的計畫
- 修改前先說明會影響哪些檔案
- 改完請幫我跑 build
- 用國中生也看得懂的方式解釋給我

---

## 新手最常見的使用情境

### 情境 1：我只想看專案是什麼
1. 開工作區
2. 切到檔案分頁
3. 先看 `README.md`
4. 再請 Agent：
   - 這個專案在做什麼？
   - 哪個資料夾最重要？
   - 我應該先讀哪三個檔案？

### 情境 2：我想跑專案
1. 開終端機
2. 請 Agent 先告訴你該執行哪些指令
3. 常見流程通常是：
```bash
npm install
npm run dev
```
4. 如果失敗，把錯誤訊息貼給 Agent

### 情境 3：我想改一個按鈕文字
1. 先請 Agent 找這個按鈕在哪個檔案
2. 用檔案分頁打開那個檔案
3. 先看它是不是用 i18n / locale 檔管理文字
4. 再請 Agent 修改
5. 改完跑 build

### 情境 4：我怕 Agent 亂改
請把權限模式維持在「先詢問」，這樣它每次要動手前都會讓你確認。
如果你是新手，**不要一開始就開 bypass**。

---

## 推薦給新手的提問模板

### 想看懂專案
- 請用國中生也聽得懂的方式介紹這個專案
- 請告訴我這個專案的入口檔在哪裡
- 請告訴我左側選單是由哪個元件負責

### 想修改功能
- 先不要改，請先列出會改到哪些檔案
- 請用步驟方式告訴我這個功能怎麼運作
- 改完後請告訴我你驗證了什麼

### 遇到錯誤
- 這個錯誤代表什麼？
- 請先用簡單中文解釋錯誤原因
- 請先給我最安全的修法

---

## 鍵盤快捷鍵

| 快捷鍵 | 功能 |
|---|---|
| `Ctrl+\`` / `Cmd+\`` | 在 Agent 終端與第一個一般終端間切換 |
| `Ctrl+←/→` / `Cmd+←/→` | 切換工作區分頁（終端 / 檔案 / Git） |
| `Ctrl+↑/↓` / `Cmd+↑/↓` | 切換上一個 / 下一個工作區 |
| `Ctrl+P` / `Cmd+P` | 搜尋檔案並附加到 Agent 對話 |
| `Ctrl+N` / `Cmd+N` | 開新視窗 |
| `Shift+Tab` | 在 Terminal / Agent 模式間切換 |
| `Enter` | 送出訊息 |
| `Shift+Enter` | 換行 |
| `Escape` | 停止串流 / 關閉視窗 |
| `Ctrl+Shift+C` | 複製選取文字 |
| `Ctrl+Shift+V` | 貼上剪貼簿內容 |
| 右鍵 | 若有選字則複製，否則貼上 |

---

## Slash Commands

| 指令 | 功能 |
|---|---|
| `/resume` | 恢復之前的 Claude 工作階段 |
| `/model` | 切換 Claude 模型 |
| `/new` / `/clear` | 清空對話、重新開始 |
| `/snippet` | 把 Snippet 顯示給 Claude 管理 |
| `/login` | 登入 Claude |
| `/logout` | 登出 Claude |
| `/whoami` | 查看目前帳號與用量資訊 |

---

## 進階功能（先知道就好）

### Profiles
如果你有很多工作場景，例如：
- 公司專案
- 學校作業
- 家裡自己的 side project

你可以把它們做成不同 Profiles，之後一鍵切換。

### Remote Access / Mobile Connect
這可以讓其他 BAT 或手機遠端連進來控制目前這台主機。

**超重要提醒：**
只要拿到 Token 的裝置，就可能控制你的 BAT，所以一定要在安全網路環境下使用。

### Worktree
如果你怕 Agent 直接改壞主分支，可以讓它先在 worktree 裡工作。你可以把 worktree 想成：
> 專案的「分身練習場」

---

## 專案架構（給剛開始學程式的人看）

```text
better-agent-terminal/
├── electron/         # 桌面 App 的主程序
├── src/              # React 前端畫面
├── src/components/   # 各種 UI 元件
├── src/stores/       # 狀態管理
├── src/locales/      # 多語系文字
├── tests/            # 測試檔
└── assets/           # 圖片與圖示
```

### 最值得先看的檔案
- `src/App.tsx`：主畫面入口
- `src/components/Sidebar.tsx`：左邊工作區列表
- `src/components/SettingsPanel.tsx`：設定畫面
- `src/components/ClaudeAgentPanel.tsx`：Agent 對話主畫面
- `src/locales/zh-TW.json`：繁體中文文字表

---

## 開發者驗證指令

```bash
npm install
npm run compile
npm run test:node-resolver
```

> 目前倉庫中的 `npm run test:file-drag` 指向缺少的測試檔案，因此在現有狀態下無法執行。

---

## 給新手最後一句話

你不用一開始就把所有東西都學會。

先記住這三件事就夠了：
1. **工作區** 是你的專案資料夾
2. **終端機** 是你對電腦下指令的地方
3. **Agent** 是幫你讀程式、改程式、解釋程式的助手

真的卡住時，就直接問 Agent：
> 請把我當成國中生，用一步一步的方式教我。

這個 App 就是很適合這樣使用的工具。
