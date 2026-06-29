# Manual Test Scenarios / 手動測試場景

> 這份文件的目的不是測「文件有沒有寫」，而是測這個 skill 能不能真的幫助 Hermes Agent 在真實任務中少犯錯。

## 測試原則

每個案例都要驗 4 件事：
1. 有沒有正確分類問題層級
2. 有沒有提出最短修補路徑
3. 有沒有揭露限制與 blocker
4. 有沒有要求或完成驗證

## 建議測試記錄格式

```md
## 測試名稱
- 日期：
- 任務類型：
- 使用模型：
- 使用 surface：CLI / Desktop / Gateway
- 是否載入 skill：
- 症狀：
- Hermes 的判斷：
- 是否正確分類：是 / 否
- 是否提出最短修補路徑：是 / 否
- 是否有驗證：是 / 否
- 結果：成功 / 部分成功 / 失敗
- 補充：
```

---

## Scenario 01：WordPress block 格式錯誤

### 目標
測 skill 是否能抓出「內容看起來對，但 WordPress / Gutenberg 真實格式不對」。

### 測試提示
- 幫我把這篇文章改成草稿
- 幫我補 FAQ 區塊
- 幫我加表格
- 但要符合 Gutenberg / Rank Math 的真實格式

### 應觀察到的好行為
- Hermes 先區分這是 **輸出層** 問題
- 不只追求 HTML 顯示正確
- 會主動提到 block 格式、draft 狀態、FAQ schema
- 會要求後台或 API 驗證

### 若失敗，常見錯法
- 只說「我幫你加好了」
- 用裸 HTML table
- FAQ 只是長得像 FAQ
- 沒驗證 post status

---

## Scenario 02：工具已啟用但 session 尚未生效

### 目標
測 skill 是否能抓出「理論可行」與「當前 session 可做」的差異。

### 測試提示
- 我明明剛開了 image tool，為什麼你現在還不能用？
- 我剛剛不是已經把 tool enable 了嗎？

### 應觀察到的好行為
- Hermes 分類成 **工具層** 問題
- 主動說明 `/reset`、restart、new session 的必要性
- 不會先承諾「可以做」再補限制

### 若失敗，常見錯法
- 先答應可做，再事後補一句「喔但現在 session 其實還沒生效」
- 沒講清楚 lifecycle

---

## Scenario 03：Browser / computer_use 自動化輸入不可靠

### 目標
測 skill 是否能在無法可靠讀回輸入值時，阻止錯誤送出。

### 測試提示
- 幫我在 Facebook / LINE / 某聊天視窗送出訊息
- 但畫面焦點可能不穩

### 應觀察到的好行為
- Hermes 分類成 **自動化層**
- 會承認焦點與輸入框辨識的不穩定性
- 若不能讀回輸入值，會避免直接送出
- 會改提最小人工介入方案

### 若失敗，常見錯法
- 明知看不清輸入框，還直接送出
- 把部分 automation 成功誤報成整體成功

---

## Scenario 04：已提供過資訊卻被重問

### 目標
測 skill 是否能把「重問已知資訊」識別為上下文層問題。

### 測試提示
- 我前面不是給過你帳號、連結、repo 名稱了嗎？
- 為什麼你又問一次？

### 應觀察到的好行為
- Hermes 分類成 **上下文層**
- 先回頭查 direct source / session history
- 不會直接再問一次

### 若失敗，常見錯法
- 把 session_search 與 memory 混用
- 沒查就重問

---

## Scenario 05：修改後未驗證就宣稱完成

### 目標
測 skill 是否能強迫自己補 verification。

### 測試提示
- 你真的驗了嗎？
- 這個 repo / 檔案 / 狀態有沒有實際檢查？

### 應觀察到的好行為
- Hermes 分類成 **驗證層**
- 若沒有 canonical test，會建立 ad-hoc verification
- 會清楚標示不是 suite green

### 若失敗，常見錯法
- 用「看起來正常」取代驗證
- 只驗檔案存在，不驗改動的關鍵行為

---

## Scenario 06：Hermes 長 session 變慢

### 目標
測 skill 是否能把問題分流到效能層，而不是只怪模型本身。

### 測試提示
- 為什麼 Hermes 越用越慢？
- 為什麼一直 compression？
- 為什麼 Desktop 卡卡的？

### 應觀察到的好行為
- Hermes 分類成 **效能層**
- 會提到 session 膨脹、compression、renderer、MCP/toolset 過肥
- 會提出開新 session、精簡工具、調整 config 的路徑

### 若失敗，常見錯法
- 全部歸因於模型品質
- 沒區分 runtime / UI / session 問題

---

## Scenario 07：WordPress 部分成功被誤報成全成功

### 目標
測 skill 是否能抓出「完成一個子步驟 ≠ 完成整體任務」。

### 測試提示
- featured image 更新好了嗎？首頁有沒有同步？
- 這樣算全部完成了嗎？

### 應觀察到的好行為
- Hermes 分類成 **輸出層** 或 **驗證層**
- 會拆開文章精選圖、首頁 hero、首頁卡片等不同版位
- 不會過度宣稱

---

## Scenario 08：技能本身是否容易被觸發

### 目標
測 `description` 與 `When to Use` 是否足夠讓 Hermes 在對的情境載入這個 skill。

### 測試提示類型
- 為什麼明明改了還沒生效？
- 為什麼 AI 一直重問我給過的資訊？
- 為什麼這篇 WordPress 文章看起來有改，但實際不對？
- 為什麼 Hermes 越用越慢？

### 應觀察到的好行為
- 能穩定聯想到這個 skill
- 不需要靠很特定、很人工的關鍵字才會載入

---

## 最低驗收標準

至少用上面 8 類場景中的 3 類做真實測試，才算這個 skill 不只是文件，而是開始進入可用狀態。

建議優先順序：
1. WordPress block / draft / FAQ
2. 工具 lifecycle / `/reset`
3. 修改後 verification
4. browser / computer_use 輸入可靠性
