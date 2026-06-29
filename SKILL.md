---
name: hermes-diagnostic-pack
description: 把真實 Hermes Agent 踩坑案例整理成可安裝的診斷與修補包。用於檢查上下文使用、驗證習慣、工具生效時機、WordPress 輸出格式、自動化送出可靠性與長 session 效能膨脹等常見問題。
---

# Hermes Diagnostic Pack

## Overview

Hermes Diagnostic Pack is a reusable troubleshooting skill for Hermes Agent.

它的任務不是只列 bug，而是把真實踩坑經驗整理成：
- 診斷流程
- 修補順序
- 驗證要求
- 可重用 guardrails

主語言以繁體中文（臺灣）為主，必要時可補英文說明。

## When to Use

Load this skill when the task involves any of the following:

- 使用者說：「為什麼不能用」、「為什麼明明改了還沒生效」、「為什麼越用越慢」
- 使用者懷疑 AI 跳過驗證、亂承諾、亂 fallback、重問已給資訊
- 任務涉及 WordPress、Gutenberg、Rank Math、browser automation、computer_use、image generation、tool lifecycle、session bloat
- 需要把症狀迅速分流到上下文層、工具層、輸出層、自動化層或效能層

Do not load this skill for simple one-off writing tasks that do not involve diagnosis or troubleshooting.

## Core Workflow

### 1. Classify the symptom first
先判斷問題最像哪一層：
- 上下文層
- 驗證層
- 工具層
- 輸出層
- 自動化層
- 效能層

詳細分類見：`references/error-taxonomy.md`

### 2. Check direct evidence before theorizing
優先順序：
1. direct source
2. current files / logs / tool outputs
3. session history
4. memory

不要跳過原始證據，直接進入猜測模式。

### 3. Separate “theoretically possible” from “currently executable”
每次診斷都要清楚區分：
- 原理上 Hermes 會不會做
- 當前這個 session / surface / toolset 能不能做

如果工具、plugin、權限、OAuth、session lifecycle 還沒確認，就不能直接承諾能做。

### 4. Propose the shortest repair path
每次修補建議應只列最短可行路徑：
- 先確認什麼
- 再改什麼
- 改完如何驗證
- 若失敗，下一個替代方案是什麼

### 5. Verify before claiming done
如果有改檔、改設定、改狀態、發訊息、發文、切換工具：
- 必須驗證
- 若沒有 canonical test，就做 ad-hoc verification
- 若無法驗證，明講 blocker，不可假裝完成

詳細驗證模式見：`references/verification-patterns.md`

## Diagnostic Output Format

每次診斷建議固定輸出：

### 問題分類 / Problem class
- 上下文層 / Context
- 驗證層 / Verification
- 工具層 / Tool lifecycle
- 輸出層 / Output quality
- 自動化層 / Automation
- 效能層 / Performance

### 最可能根因 / Most likely root cause
只列 1 到 3 個，不要一次列 10 個猜測。

### 最短修補路徑 / Shortest repair path
列出具體步驟，不要只講抽象建議。

### 驗證方式 / Verification
明確指出：
- 要看哪個檔案
- 要看哪個 log
- 要跑哪個 command
- 要不要 `/reset` 或 restart

### Blocker
若無法完成，必須直說：
- 目前缺什麼
- 為什麼這會阻擋修復
- 是否有替代路徑

## Common Pitfalls

- 重問已經提供過的資訊
- 沒驗證就宣稱完成
- 把理論可行講成當前可做
- 太晚說需要 `/reset`
- 不能讀回輸入值還硬送出
- 把部分成功包裝成完整成功
- 把慢全部怪給模型，忽略 renderer / session / MCP

WordPress 類詳細坑位見：`references/wordpress-failure-modes.md`

## Reference Cases

Source case library: `cases/30-error-cards.md`

Especially important recurring problems:
1. 重問已提供資訊
2. 未驗證就宣稱完成
3. 工具已開但 session 尚未生效
4. 說 image/plugin/OAuth 能用但當前不能用
5. WordPress 表格與 FAQ block 不合格
6. draft/publish 狀態誤改
7. 自動化焦點錯亂導致送錯訊息
8. 視窗抓錯 process
9. 部分成功誤報成完整成功
10. Hermes 變慢其實是 session / renderer / MCP 問題

## Verification Checklist

Before finishing a diagnosis or repair, check:

- [ ] 我是否先看了 direct evidence，而不是直接猜
- [ ] 我是否區分了原理可行與當前可執行
- [ ] 我是否指出問題層級
- [ ] 我是否提供最短修補路徑
- [ ] 我是否真的驗證，而不是口頭說完成
- [ ] 若仍無法驗證，我是否明確標示 blocker

## Contribution Direction

This skill should evolve from real failures, not hypothetical examples.

When adding new rules:
1. record the symptom
2. identify the actual mistake
3. capture the repair path
4. define the verification step
5. extract a reusable rule
