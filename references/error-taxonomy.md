# Error Taxonomy / 錯誤分類地圖

## 目的
這份檔案用來保存 Hermes Diagnostic Pack 的錯誤分類地圖，避免把所有細節塞回 `SKILL.md`。

## 六大分類

### 1. 上下文層 / Context
典型問題：
- 重問已提供的資訊
- 沒先用 `session_search`
- memory、session history、direct source 用錯順序

診斷重點：
- 資訊原本是不是已經存在？
- 原始來源是否可直接讀取？
- AI 是否跳過最有證據力的來源？

### 2. 驗證層 / Verification
典型問題：
- 改了就說完成
- 沒有 fresh verification
- 只驗表面結果，不驗實際行為

診斷重點：
- 是否存在 canonical test / lint / build？
- 若沒有，是否有 ad-hoc verification？
- 驗證是否對準 changed behavior？

### 3. 工具層 / Tool Lifecycle
典型問題：
- 工具明明開了但當前 session 不能用
- 忘了 `/reset`、restart、new session
- 把理論可行當成現在可做

診斷重點：
- toolset / plugin / auth 是否真的就緒
- surface 是 CLI、Desktop 還是 gateway
- session lifecycle 是否已說清楚

### 4. 輸出層 / Output Quality
典型問題：
- WordPress block 錯
- FAQ / SEO / 草稿狀態不符合真實規則
- 部分成功被說成完整成功

診斷重點：
- 是否符合目標系統的真實格式
- 是否把所有子需求都驗完
- 是否正確揭露限制

### 5. 自動化層 / Automation
典型問題：
- 焦點不穩
- 抓錯視窗 / process
- 不能讀回輸入值卻硬送出

診斷重點：
- 此任務適合 browser automation 還是 computer_use
- 是否能讀回輸入狀態
- 是否需要最小人工介入

### 6. 效能層 / Performance
典型問題：
- session 膨脹
- repeated compression
- renderer 卡頓
- MCP / toolset 過肥

診斷重點：
- 慢是模型慢，還是 runtime 慢
- 是否應開新 session
- 是否應拆 profile / 精簡工具

## 建議輸出方式
診斷時先輸出：
1. 問題分類
2. 最可能根因
3. 最短修補路徑
4. 驗證方式
5. blocker（若有）
