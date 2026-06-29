# 診斷包藍圖

## 這份文件的主責任

把真實踩過的 Hermes Agent 錯誤，整理成一個所有使用者可安裝的診斷包 / Skill。

這份文件不偏情緒復盤，而偏執行設計。
如果未來真的要做成 Skill、starter pack、課程附贈包、或社群排錯入口，應以這份為主。

## 目標定義

這個包安裝後，至少要做到 4 件事：

1. 診斷：檢查 Hermes / AI 是否有常見老毛病
2. 分流：指出問題是在上下文、工具、輸出格式、自動化，還是效能層
3. 修補：提供最短修補路徑，而不是抽象建議
4. 驗證：要求修補後一定留下一次可驗證的結果

## 產品定位

它不是單一教學，而是：
- 技術體檢包
- 故障模式資料庫
- 自動排錯 Skill
- guardrail 套件

## 建議的 repo / skill 輸出結構

### A. 一份主 Skill
候選名：
- `hermes-agent-school`
- `hermes-diagnostic-pack`
- `hermes-failure-patterns`

目前最推薦：
**`hermes-diagnostic-pack`**

原因：
- 新手一看就知道用途
- 比「學校」更像可安裝工具
- 「Hermes Agent 學校」更適合當品牌名或課程名

### B. Skill 應包含 5 個模組

#### 1. 上下文診斷模組
要檢查：
- AI 是否跳過 session_search
- 是否重問已經提供過的資訊
- 是否把 memory、session history、direct source 用錯

輸出：
- 問題症狀
- 可能根因
- 應先查哪個來源

#### 2. 驗證習慣診斷模組
要檢查：
- 是否有修改卻沒有 verification
- 是否只有口頭宣稱完成
- 是否需要 ad-hoc verification script

輸出：
- 已改檔案
- 缺少哪種驗證
- 最小可行驗證方法

#### 3. 工具與 lifecycle 診斷模組
要檢查：
- 工具是否真的啟用
- 是否需要 `/reset` / restart 才會生效
- 是否把理論可行與當下可做混為一談

輸出：
- 目前狀態
- 卡在哪一層
- 下一步精準指令

#### 4. 輸出品質診斷模組
要檢查：
- WordPress / Gutenberg / Rank Math 格式是否正確
- FAQ / table / draft state / meta 是否符合真實外掛規則
- 是否把部分成功誤說成完整成功

輸出：
- 可通過
- 有風險
- 明確失敗

#### 5. 效能與長 session 診斷模組
要檢查：
- context 是否膨脹
- compression 是否過早 / 過頻
- renderer / notifications / heavy MCP 是否拖慢體感

輸出：
- 問題級別：低 / 中 / 高
- 可立即做的減肥動作
- 需要新 session還是需要改 config

## 診斷包的標準輸入格式

未來 Skill 應盡量要求使用者提供以下其中一種：

1. 症狀描述
2. 錯誤訊息
3. 操作情境
4. 截圖 / log / session 片段

## 診斷包的標準輸出格式

每次診斷都應固定輸出：

### 1. 問題分類
- 上下文層
- 驗證層
- 工具層
- 輸出層
- 自動化層
- 效能層

### 2. 最可能根因
只列 1 到 3 個，不要一次列太多猜測。

### 3. 最短修補路徑
給使用者能直接做的順序，不要只講概念。

### 4. 驗證方式
明確說：
- 要看哪個 log
- 要跑哪個 command
- 要檢查哪個前台結果
- 要不要新開 session

### 5. 若無法完成，必須明講 blocker
這是最重要的規矩之一：
- 不可以假裝成功
- 不可以把部分成功說成全成功
- 不可以寫一段看起來很像完成的敘述來混過去

## 建議的案例卡片格式

```md
## 案例：<短標題>
- 症狀：
- 真正過錯：
- 根因分類：
- 修補方式：
- 驗證方式：
- 應提煉成的規則：
```

## 優先收錄的 10 類診斷題目

1. 已給過資訊卻被重問
2. 修改後未驗證就宣稱完成
3. 工具已開但 session 尚未生效
4. image_gen / plugin / OAuth 說能用但當前其實不能用
5. WordPress 表格與 FAQ block 不合格
6. draft / publish 狀態誤改
7. browser / computer_use 焦點錯亂導致送錯訊息
8. 視窗抓錯 process
9. 部分成功被誤報成完整成功
10. Hermes 越用越慢其實是 session / renderer / MCP 問題

## 建議的 Skill.md 骨架

### Overview
- 這個 Skill 用於診斷 Hermes 常見老毛病
- 根據真實踩坑案例設計，不是理論清單

### When to Use
- 使用者說「為什麼不能用」「為什麼越用越慢」「為什麼明明改了還沒生效」
- 使用者懷疑 AI 沒驗證、亂承諾、亂 fallback
- 遇到 WordPress、gateway、image_gen、browser automation 等高風險任務

### Core Workflow
1. 先判斷症狀屬於哪一層
2. 先查 direct source，再查 session history
3. 若涉及 tool/config，先確認是否需要 `/reset` 或 restart
4. 若涉及輸出結果，先做 verification
5. 若無法驗證，直接回報 blocker

### Common Pitfalls
- 不要把理論可行當成當前可做
- 不要補問已知資訊
- 不要在不能讀回輸入值時強行送出
- 不要把部分成功誤報成完整成功
- 不要跳過驗證

### Verification Checklist
- 是否有 direct evidence
- 是否有實際命令 / 檔案 / log 支撐
- 是否標明當前 session 是否需要重啟
- 是否區分完全成功 / 部分成功 / 未完成

## 建議落地順序

### 第 1 階段
先把 30 筆個案卡片化，形成 source note。

### 第 2 階段
把相似個案收斂成 10 個診斷模組。

### 第 3 階段
做成 Hermes Skill，建立 `SKILL.md` + 必要 references。

### 第 4 階段
拿真實任務測，至少覆蓋：
- WordPress 發文
- image_gen 啟用
- browser / computer_use 發訊息
- Hermes 變慢 / 長 session

## Done definition

只有在下面都成立時，才算真的完成：

- 有整理好的個案卡片
- 有收斂好的診斷模組
- 有可安裝 Skill 初版
- 有至少 3 個真實案例測過
- 有 verification，不只是文件看起來漂亮