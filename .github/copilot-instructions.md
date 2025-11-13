# simple-website-with-specific-context-path-and-rule GitHub Copilot 規範

## 開發規範

1. **程式碼品質**
   - 所有程式碼必須包含函式級註解（說明用途、參數、回傳值）
   - 註解使用繁體中文撰寫

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
