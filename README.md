# Hermes Agent School

把真實 Hermes Agent 踩坑案例，整理成給所有使用者的診斷與修補知識庫。

## 這是什麼

`Hermes Agent School` 的目標很直接：

- 讓 Hermes 新手少走彎路
- 讓進階使用者更快定位問題在哪一層
- 把真實踩坑經驗，變成可重用的 guardrails、診斷流程與未來 Skill

這個 repo 目前是 **公開知識庫初版 + 正式 Skill 母稿**。
後續會逐步長成：

1. 失敗模式庫
2. 診斷包藍圖
3. 可安裝的 Hermes Skill
4. 社群共用的排錯 starter pack

## 核心主張

很多人以為 AI 出錯只是「模型不夠聰明」，但我自己實際踩坑後發現，真正高頻的問題常常是：

- 沒先用現有上下文
- 沒驗證就宣稱完成
- 把理論可行誤說成當前可做
- 不知道 tool / plugin / config 改完要不要 `/reset`
- WordPress / Gutenberg / FAQ / SEO block 格式錯
- browser / computer_use 焦點不穩，送出錯訊息
- 把部分成功包裝成完整成功
- Hermes 自己因為長 session、compression、renderer、MCP 太肥而越用越慢

換句話說，這不是單一 bug 清單，而是一組 **AI agent 常見故障模式**。

## 目前內容

### 1. [失敗模式與診斷包構想](docs/failure-patterns-and-diagnostic-pack.md)
整理這個專案為什麼值得做、最主要的錯誤母題是什麼、以及它未來最像哪種產品。

### 2. [診斷包藍圖](docs/diagnostic-pack-blueprint.md)
定義未來如果做成 Skill / starter pack，應包含哪些模組、怎麼輸入、怎麼輸出、怎麼驗證。

### 3. [SKILL.md](SKILL.md)
正式的 Hermes Skill 母稿，已補 frontmatter、觸發條件、核心流程與驗證要求。

### 4. [30 Error Cards](cases/30-error-cards.md)
30 筆真實踩坑案例卡片，是未來擴充規則與 references 的主要來源。

### 5. [How to Use This Pack](docs/how-to-use-this-pack.md)
中英雙語的使用導覽頁，說明如何閱讀、如何引用、如何擴充。

## 目前抽出的 8 大錯誤母題

1. 沒先用現有上下文
2. 沒驗證就宣稱完成
3. 把原則可行誤說成當前 session 可執行
4. 對 Hermes lifecycle 說明太晚
5. WordPress / Gutenberg / Rank Math 格式錯
6. 桌面自動化送出前無法可靠確認輸入值
7. 把部分成功包裝成完整成功
8. 長 session 與 Desktop renderer 本身就是問題源

## 這個 repo 未來會長成什麼

### Phase 1
公開失敗模式庫與整理方法。

### Phase 2
把失敗模式整理成標準案例卡片。

### Phase 3
實作成 Hermes 可安裝的 Skill，例如：
- `hermes-diagnostic-pack`

### Phase 4
做成社群可下載、課程可附贈、顧問可直接套用的優化包。

## 想解決的核心問題

不是只回答：
- 「Hermes 為什麼怪怪的？」

而是要回答：
- 問題到底出在上下文、工具、輸出格式、自動化，還是效能層？
- 哪些錯誤可以直接修？
- 哪些情況應該老實承認 blocker？
- 哪些 guardrail 應該提前裝上，避免下次再踩同一個坑？

## 對未來 Skill 的一句話描述草稿

> 把真實 Hermes Agent 踩坑案例整理成可安裝的診斷與修補包，用於檢查上下文使用、驗證習慣、工具生效時機、桌面自動化可靠性、WordPress 格式錯誤與效能膨脹等常見問題。

## 狀態

目前是 v0.2：
- 公開知識庫初版
- 案例卡片庫
- 正式 Skill 母稿
- bilingual usage guide

## 授權

先採用 MIT，方便後續公開分享、再利用與擴寫。