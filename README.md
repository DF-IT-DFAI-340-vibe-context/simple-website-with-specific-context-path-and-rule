# simple-website-with-specific-context-path-and-rule

一個使用 Vite + Vue + SCSS 建立的簡單網站，支援環境變數配置來區分正式與測試環境的網址前綴。

## 專案建置的 prompt

### 初始化專案

詳見 pull request #1

```
用 vite + vue + scss 建立一個簡單的網站

有登入頁、登入後的歡迎頁、關於我們這三個頁面

使用 .env.production 和 .env.development 來區分正測試環境設定

環境設定先設置一個環境變數：`CONTEXT_PATH` 作為網址前綴（正式區為`/foo/bar`；測試區為`/`）

在 package.json 的 script 中，要提供 `dev:production` 的 `script` 用以執行正式環境檔
```

### 建立規範

在專案建置完畢後，處理以下 prmopt

<pre>
新增 `replit.md` 和 `.github/copilot-instructions.md`

將以下規範寫入這兩個檔案

```
1. **程式碼品質**
   - 所有程式碼必須包含函式級註解（說明用途、參數、回傳值）
   - 註解使用**繁體中文**撰寫

2. **Plan 模式要求**
   - 完成所有子任務後，將完成報告記錄至 `./report.md`
   - 需包含：任務描述、完成時間、遇到的問題、解決方案

3. **規格文件要求**
   - Plan 模式結束時產生 spec.md（技術規格文件）
   - Plan 模式結束時產生 todolist.md（任務清單）
   - spec.md 必須包含：
     * 系統流程圖 (Flow Chart)
     * 循序圖 (Sequence Diagram)
     * 類別圖/物件關聯圖 (Class/ER Diagram)
     * API 規格定義
     * 資料結構設計
     * 模組架構說明

4. **Build 模式要求**
   - 嚴格遵循 spec.md 進行開發
   - 每次修改程式前必須確認 spec.md 的相關規格
   - 每完成一個任務後更新 todolist.md 的進度狀態

5. **專案完成文檔**
   - 撰寫完整的 README.md，必須包含：
     * 專案描述與目標
     * 完整檔案結構樹狀圖
     * 使用的技術棧清單
     * 所有檔案清單與簡短說明
     * 安裝步驟
     * 執行方式
     * 環境需求

6. **版本控制**
   - 每個重要任務完成後建立 checkpoint
   - checkpoint 訊息必須有意義且描述清楚（例如：「✅ 完成用戶登入功能與 JWT 驗證」）

7. **語言要求**
   - 所有對話、文檔、註解皆使用繁體中文
```

兩份文件要照這種格式撰寫：
  
```
{{ 專案名稱 }} {{AI 名稱}}規範


## 開發規範
```  
</pre>


## 功能特色

### 頁面
- **登入頁** - 使用者登入介面
- **歡迎頁** - 登入後的歡迎頁面，顯示使用者資訊和環境配置
- **關於我們** - 公司資訊介紹頁面

### 環境配置
專案使用環境變數來區分正式與測試環境：

- **測試環境** (`.env.development`)
  
- **正式環境** (`.env.production`)

## 技術棧

- **Vite** - 快速的前端建構工具
- **Vue 3** - 使用 Composition API 的前端框架
- **Vue Router** - 支援 context path 的路由管理
- **SCSS** - CSS 預處理器
- **環境變數** - 開發與正式環境分離配置

## 專案設置

### 安裝依賴

```bash
npm install
```

### 開發模式

啟動測試環境開發伺服器（context path: `/`）：

```bash
npm run dev
```

啟動正式環境開發伺服器（context path: `/foo/bar`）：

```bash
npm run dev:production
```

### 建置專案

建置正式環境版本：

```bash
npm run build
```

### 預覽建置結果

```bash
npm run preview
```

## 專案結構

```
├── .env.development        # 測試環境配置
├── .env.production         # 正式環境配置
├── src/
│   ├── views/             # 頁面元件
│   ├── router/            # 路由配置
│   │   └── index.js       # Vue Router 設定
│   ├── App.vue            # 根元件
│   └── main.js            # 應用程式入口
├── vite.config.js         # Vite 配置
└── package.json           # 專案配置
```

## 環境變數說明

本專案使用 `VITE_CONTEXT_PATH` 環境變數來設定應用程式的基礎路徑：

- 在 Vite 配置中，這個變數會被用作 `base` 選項
- 在 Vue Router 中，這個變數會被用作 history 的 base path
- 所有的路由和靜態資源都會相對於這個路徑

## 路由結構

- `/` - 登入頁面
- `/welcome` - 歡迎頁面（需要登入）
- `/about` - 關於我們頁面


