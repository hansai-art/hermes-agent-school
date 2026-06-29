# Install and Use as a Hermes Skill / 安裝與使用指南

## 中文說明（臺灣）

這個 repo 目前是 **Hermes Diagnostic Pack** 的公開母稿。
雖然它還不是正式上架到 skills hub 的版本，但你已經可以用以下方式把它當成一個 skill 來源來整理、安裝或改造。

## 使用方式 1：直接閱讀 repo 內容
適合：
- 想先整理內容
- 想先做課程 / 顧問 / 社群文章
- 想先用人工方式測 skill 結構

建議閱讀順序：
1. `README.md`
2. `SKILL.md`
3. `references/`
4. `cases/30-error-cards.md`
5. `tests/manual-test-scenarios.md`

## 使用方式 2：本地當作 skill 草稿使用
若你想把這份內容搬進 Hermes 本地 skills 目錄，可參考這種做法：

```bash
mkdir -p ~/.hermes/skills/hermes-diagnostic-pack
cp SKILL.md ~/.hermes/skills/hermes-diagnostic-pack/SKILL.md
cp -R references ~/.hermes/skills/hermes-diagnostic-pack/
```

之後可在 Hermes 內：

```bash
/skill hermes-diagnostic-pack
```

或啟動時預載：

```bash
hermes -s hermes-diagnostic-pack
```

> 注意：如果你改了 skill 內容，通常需要重新載入 skills，必要時再 `/reset` 開新 session。

## 使用方式 3：未來發布成正式 skill
未來若要更正式地分享，可往這幾個方向走：

- 補更多真實案例測試
- 強化 install path 與 examples
- 依 Hermes skill 發布流程整理 metadata
- 發布到 skills hub 或作為 repo-based skill source

## 目前最適合拿來測什麼

這份 skill 最適合先測：
- WordPress 格式與狀態錯誤
- 工具啟用 / `/reset` / lifecycle 問題
- 修改後驗證不足
- browser / computer_use 送出可靠性
- Hermes 長 session / compression / renderer 變慢

---

## English Support

This repository is currently a **public draft/source repo** for the Hermes Diagnostic Pack.

It is not yet positioned as a polished published Hub skill, but you can already use it in three practical ways:

### 1. Read it as a skill source repo
Recommended order:
1. `README.md`
2. `SKILL.md`
3. `references/`
4. `cases/30-error-cards.md`
5. `tests/manual-test-scenarios.md`

### 2. Load it locally as a draft skill
A practical local approach is:

```bash
mkdir -p ~/.hermes/skills/hermes-diagnostic-pack
cp SKILL.md ~/.hermes/skills/hermes-diagnostic-pack/SKILL.md
cp -R references ~/.hermes/skills/hermes-diagnostic-pack/
```

Then load it with:

```bash
/skill hermes-diagnostic-pack
```

or preload it with:

```bash
hermes -s hermes-diagnostic-pack
```

### 3. Evolve it into a publishable skill
Before publishing, it should gain:
- more real-world tests
- clearer examples
- stronger install/distribution metadata
- validation from real Hermes task runs

## Important note

The primary authoring language is **Traditional Chinese for Taiwan**.
English is included as supporting guidance only.
