# 如何使用這個包 / How to Use This Pack

## 中文說明（臺灣）

這個 repo 目前是 **Hermes Agent School** 的公開知識庫初版。
你可以把它理解成：

- 給新手的少踩坑地圖
- 給進階使用者的故障模式庫
- 給未來 Skill 的 source of truth

### 你可以怎麼用

#### 1. 當作閱讀型知識庫
先讀：
- [`README.md`](../README.md)
- [`docs/failure-patterns-and-diagnostic-pack.md`](./failure-patterns-and-diagnostic-pack.md)
- [`docs/diagnostic-pack-blueprint.md`](./diagnostic-pack-blueprint.md)

適合：
- 想理解 Hermes 常見錯誤母題的人
- 想整理課程、社群文章、顧問內容的人

#### 2. 當作案例庫
讀：
- [`cases/30-error-cards.md`](../cases/30-error-cards.md)

適合：
- 想把錯誤整理成教學案例的人
- 想把故障模式轉成 issue / SOP / lesson learned 的人

#### 3. 當作正式 Skill 母稿
讀：
- [`SKILL.md`](../SKILL.md)
- [`references/error-taxonomy.md`](../references/error-taxonomy.md)
- [`references/verification-patterns.md`](../references/verification-patterns.md)
- [`references/wordpress-failure-modes.md`](../references/wordpress-failure-modes.md)
- [`docs/install-and-use-as-hermes-skill.md`](./install-and-use-as-hermes-skill.md)
- [`tests/manual-test-scenarios.md`](../tests/manual-test-scenarios.md)

適合：
- 想把這份知識做成 Hermes Skill 的人
- 想測試「診斷型 Skill」能不能實際改善 AI 行為的人

### 使用建議順序

1. 先看 README，建立全貌
2. 再看失敗模式文件，理解為什麼這些坑會反覆發生
3. 再看診斷包藍圖，理解如何做成可執行流程
4. 再看 `SKILL.md`，確認技能主檔如何收斂
5. 最後看 error cards 與 references，開始實作與擴充
6. 若要落地測試，直接跑 manual test scenarios

### 目前最值得擴充的方向

- 增加更多真實案例卡片
- 把 30 張卡片收斂成 10 個診斷模組
- 增加驗證腳本範例
- 讓 `SKILL.md` 真正進入 Hermes 測試循環

---

## English Support

This repository is the first public knowledge-base version of **Hermes Agent School**.

You can use it as:
- a beginner-friendly map of common Hermes pitfalls
- a failure-pattern library for advanced users
- the source of truth for a future installable Hermes troubleshooting skill

### Recommended reading order

1. `README.md` for the big picture
2. `docs/failure-patterns-and-diagnostic-pack.md` for the problem framing
3. `docs/diagnostic-pack-blueprint.md` for the implementation design
4. `SKILL.md` for the skill-facing structure
5. `docs/install-and-use-as-hermes-skill.md` for local usage guidance
6. `tests/manual-test-scenarios.md` for real-world validation
7. `cases/30-error-cards.md` and `references/` for grounded operational content

### Best use cases

- teaching Hermes Agent users
- designing a troubleshooting course or starter pack
- converting real failures into reusable guardrails
- building a future Hermes skill from grounded cases

### Important note

The primary language and thinking model of this repository is **Traditional Chinese for Taiwan**.
English is included only as supporting guidance, not as the main authoring language.
