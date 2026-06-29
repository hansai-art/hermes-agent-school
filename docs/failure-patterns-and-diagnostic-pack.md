# 失敗模式與診斷包構想

## 一句話定義

`Hermes Agent School` 不是再做一份教學筆記，而是把真實踩過的錯誤、修補流程、驗證方式，以及未來 AI 應避免再犯的規則，整理成一個所有 Hermes Agent 使用者都能安裝或引用的優化包。

## 這份文件要回答什麼

這份文件回答的是：

- 為什麼這個主題值得做成公開 repo
- 高頻錯誤到底集中在哪幾類
- 這份知識最終應該被包裝成什麼產品

## 核心想法

目標不是只讓 Hermes 回答得更漂亮，而是讓它：

1. 先診斷自己是不是有老毛病
2. 再告訴使用者問題在哪一層
3. 必要時直接套用修補 SOP
4. 最後留下可驗證的修復紀錄

所以這個包更像：

- AI 體檢包
- 故障模式資料庫
- 修補建議引擎
- 可安裝 Skill / 操作手冊

## 為什麼要做成公開 repo

如果只是寫成單篇文章，價值只停在「看過」。
如果整理成公開 repo，它才有機會變成：

- 新手的排錯入口
- 老手的快速診斷參考
- 後續 Skill 的 source of truth
- 課程、社群、顧問服務的基礎知識庫

## 目前抽出的 8 大錯誤母題

### 1. 沒先用現有上下文
典型症狀：
- 明明使用者之前給過資訊，Hermes 還重問一次
- 該用 `session_search` 時沒有先用
- 把 memory 跟 session history 的用途混在一起

### 2. 沒驗證就宣稱完成
典型症狀：
- 檔案寫了就說完成
- 有改動，但沒有 fresh verification
- 只回報表面結果，沒有 disk-level 檢查

### 3. 把「原則可行」誤說成「當前 session 可執行」
典型症狀：
- 先說做得到，後來才承認工具沒開或 session 還沒生效
- 把理論可行性與現況可用性混為一談

### 4. 對 Hermes lifecycle 說明太晚
典型症狀：
- 工具已啟用但沒提醒要 `/reset`
- 設定已改，但沒說需要 restart / new session
- 使用者以為改完當下就會生效

### 5. WordPress / Gutenberg / Rank Math 格式錯
典型症狀：
- 裸 HTML 表格，不是 Gutenberg block
- FAQ 看起來像 FAQ，但不是外掛可辨識 block
- 草稿 / 發布狀態控制失準
- SEO 有做，但沒有命中實際評分規則

### 6. 桌面自動化送出前沒辦法可靠確認輸入值
典型症狀：
- UI 焦點不穩
- 送出了錯誤文字或空回覆
- automation 抓到錯視窗、錯 process

### 7. 把部分成功包裝成完整成功
典型症狀：
- 某個子步驟通了，就說整體任務完成
- featured image 更新成功，就說首頁圖片已更新
- 限制條件到最後才補充

### 8. 長 session 與 Desktop renderer 自己就是問題源
典型症狀：
- context 一直膨脹
- repeated compression
- renderer 卡頓
- heavy MCP / notifications / UI 更新拖慢體感

## 5 層問題分類

1. 上下文層：session_search、memory、已給資訊、source-of-truth
2. 執行層：tool 可用性、權限、reset、生效時機、fallback 路徑
3. 輸出層：CMS 格式、block 格式、SEO 規則、內容深度
4. 自動化層：browser、computer_use、焦點、送出可靠性、視窗辨識
5. 效能層：compression、renderer、長 session、MCP、toolset 肥大

## 這份經驗真正想教其他 AI 什麼

不是一句「不要犯錯」而已，而是下面這幾條：

1. 先查，再問
2. 先驗，再報
3. 先分清理論可行與當下可做
4. 先揭露限制，不要事後補限制
5. 送出前若不能讀回，就不要假裝一定成功
6. 慢不一定是模型慢，很多時候是 agent runtime 自己慢

## 這個 repo 未來最像什麼產品

### 版本 1：失敗模式庫
把每次真實錯誤記成：
- 症狀
- 根因
- 修補方式
- 驗證方式
- 未來 guardrail

### 版本 2：Hermes 診斷 Skill
使用者安裝後，可以直接要求：
- 幫我檢查 Hermes 為什麼越用越慢
- 幫我檢查 image_gen 為什麼明明開了還不能用
- 幫我檢查這個 AI 是不是又在沒有驗證就宣稱完成

### 版本 3：Hermes Agent 學校
進一步升級成：
- 教學模組
- 新手排錯入口
- 老手效能優化與工作流修補包
- 社群共用的錯誤模式資料庫

## 當前定位

如果現在就要對外命名，最合適的定位是：

**Hermes Agent 學校：失敗模式庫＋診斷包藍圖**