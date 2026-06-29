# WordPress Failure Modes / WordPress 常見失誤

## 目的
這份檔案聚焦在 Hermes / AI 幫忙操作 WordPress 時最容易踩到的坑。

## 常見失誤

### 1. 裸 HTML 表格
症狀：
- 前台看起來有表格
- 但不符合 Gutenberg 編輯器標準

建議：
- 優先輸出 `wp:table` block
- 不要只用裸 `<table>`

### 2. FAQ 只是長得像 FAQ
症狀：
- 有問答內容
- 但 SEO 外掛不一定認得

建議：
- 使用目標外掛支援的 FAQ block
- 不要只憑肉眼覺得像 FAQ

### 3. draft / publish 狀態失準
症狀：
- 使用者要求存草稿
- 結果文章被直接發布

建議：
- 將內容狀態視為硬限制
- 修改後立即回查 status

### 4. SEO 有做，但不是工具規則導向
症狀：
- title、description 看似有寫
- 但外掛檢查分數仍不好

建議：
- 區分一般 SEO 原則與插件具體規則
- 回查 focus keyword、slug、首段、小標、meta

### 5. 部分成功誤報成完整成功
症狀：
- 只更新 featured image，就說首頁圖位已完成

建議：
- 分清文章精選圖、首頁 hero、首頁卡片是否是不同版位
- 每個版位分開驗證

## 診斷時要先問自己
1. 我現在驗的是後台狀態、前台渲染，還是版位映射？
2. 我操作的是 WordPress 核心格式，還是外掛規則？
3. 這次完成的是整體需求，還是其中一個子步驟？
