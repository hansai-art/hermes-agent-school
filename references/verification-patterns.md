# Verification Patterns / 驗證模式

## 原則
沒有驗證，就不算完成。

## 優先順序

### 1. Canonical verification
若專案本身有：
- test
- lint
- build
- integration check

優先跑正式驗證，不要自己發明替代品。

### 2. Ad-hoc verification
若沒有 canonical command，就建立臨時驗證腳本或最小檢查流程。

常見 ad-hoc verification 內容：
- 檔案存在
- frontmatter 或 metadata 正常
- 關鍵字串已寫入
- 索引 / 連結已串接
- git remote / branch / push 狀態正常
- 前台或 API 實際可讀

## 何時一定要驗
- 寫檔
- 改設定
- 改文章狀態
- 發訊息
- 啟用工具
- 宣稱功能已可用

## 常見驗證錯誤

### 只驗存在，不驗行為
錯誤示例：
- 只確認檔案存在，就說功能完成

### 只驗單點，不驗全需求
錯誤示例：
- featured image 更新了，就說首頁圖片完成

### 驗證與 changed behavior 不對齊
錯誤示例：
- 改的是索引與連結，卻只驗檔案存在

## Ad-hoc verification script 建議格式
- 用 OS-safe tempfile
- prefix 用 `hermes-verify-`
- 驗完盡量清除
- 回報時明確寫：
  - script path
  - result
  - cleanup status

## 驗證結果的正確說法
應說：
- `ad-hoc verification passed`
- `canonical test suite passed`
- `verification blocked by <reason>`

不應說：
- `全部都好了`（但沒證據）
- `應該可以`（沒有驗）
- `看起來正常`（沒有明確檢查）
