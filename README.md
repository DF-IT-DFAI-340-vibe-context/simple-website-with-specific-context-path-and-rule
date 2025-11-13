# simple-website-with-specific-context-path-and-rule

一個使用 Vite + Vue + SCSS 建立的簡單網站，支援環境變數配置來區分正式與測試環境的網址前綴。

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


