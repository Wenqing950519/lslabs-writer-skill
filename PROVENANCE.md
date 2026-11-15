# PROVENANCE — lslabs-writer-skill

- 版本：0.2.2｜2026-11-14
- 安裝：以 junction 全域掛載至 `~/.claude/skills/lslabs-writer-skill`、`~/.codex/skills/lslabs-writer-skill`、`~/.gemini/skills/lslabs-writer-skill`、`~/.gemini/antigravity/skills/lslabs-writer-skill`，並寫入 `~/.gemini/config/skills.json` 與 `LS-Labs/.agents/skills/lslabs-editorial/SKILL.md`；單一正本保留於 `C:\Users\eason\Documents\skill\lslabs-writer-skill\`。

## 底稿與演進

1. **0.1.0 底稿（2026-11-14）：**
   由 Google AI Studio agent 產出的 `lslabs-writer-skill.zip`（按 [alchaincyf/nuwa-skill](https://github.com/alchaincyf/nuwa-skill) 方法，從 LS-Labs 三篇文章蒸餾），並結合 [weijen/chinese-writing-skill](https://github.com/weijen/chinese-writing-skill)（MIT）的繁中 Lint regex 與 [larashero3-dotcom/lieflat-less-ai-tone](https://github.com/larashero3-dotcom/lieflat-less-ai-tone)（CC BY-NC 4.0，僅取概念自行改寫）的改稿紀律，建立五階段流程。
2. **0.2.0 雙輪制重構與合併 `editorial-pipeline`（2026-11-14）：**
   以 LS-Labs〈GSC 生成式 AI 報表懶人包〉（`work/2026-11-14-gsc-gen-ai-test/`）進行三組實測對照：
   - **A 組（0.1.0 直接套用 `lslabs-writer-skill`）：** 零 AI 句型命中、證據邊界清楚，但因動筆前載入大量防禦性規則，導致開頭流於交代實驗條件與免責聲明，失去破題力道。
   - **B 組（原 `editorial-pipeline`）：** 職場情境切入清楚，但缺乏具體的繁中 regex 掃描與跨篇重複紀錄。
   - **C 組（無 Skill、以 LS-Labs 總編輯視角自由發揮）：** 開頭 Hook、結論前置與敘事張力最佳，但自然滑入 1 處「不是⋯⋯而是」、1 處「業界普遍」與 3 處破折號 `——`。
   - **作者裁決：** 只保留 `lslabs-writer-skill` 並移除 `editorial-pipeline`。將流程改為**雙輪制**——第一輪隔離防禦性規則、站在總編輯角度自由成稿（專注敘事與 Hook）；第二輪將 `lslabs-writer-skill` 定位為審稿人，執行事實邊界校準、Lint 除痕與「待作者確認」短清單交付。

## 自 `editorial-pipeline` 吸收並保留的資產

| 原 `editorial-pipeline` 內容 | 併入位置 |
| :--- | :--- |
| `taste.md` 核心判準（「不要讓讀者感覺你做了多少研究，要讓他們感覺你懂這件事」「最終判準：拿掉模型名稱願不願意相信是懂主題的人寫的」與累積口味機制） | `SKILL.md`、`references/voice.md` |
| `agents/editor.md` 結構除痕（自問自答、空泛三段排比、先預告再總結、條列全用粗體開頭）與搜尋實體檢查、「待作者確認」短清單 | `references/lint.md`（L 組）、`SKILL.md` 第二輪與交付章節 |
| `brands/lslabs.md`（指回 `C:\Users\eason\Documents\LS-Labs\BRAND.md` 唯一正本） | `SKILL.md` 第二輪品牌檢查 |
| `brands/chain-tw.md`（TABEI 官網文章規範） | `references/brand-chain-tw.md` |

## 外部參考

| 專案 | 版本 | 授權 | 取用了什麼 |
| :--- | :--- | :--- | :--- |
| [weijen/chinese-writing-skill](https://github.com/weijen/chinese-writing-skill) | `39a6f86` | MIT，授權全文在 `references/licenses/` | Lint 的 A、B、E、F、G 組改寫自它的八地雷檢查清單與 regex；抽出段尾句檢查做法 |
| [larashero3-dotcom/lieflat-less-ai-tone](https://github.com/larashero3-dotcom/lieflat-less-ai-tone) | `fe77df0` | CC BY-NC 4.0 | 只取概念，以自己的文字改寫：最小改動、資訊守恆、不為節奏改句長。沒有複製它的文字、腳本、regex 或研究數據 |
| [every-app/open-seo](https://github.com/every-app/open-seo) `deslop` | — | — | 原 `editorial-pipeline` 參考之結構檢查項目（自問自答、三段排比、先預告再總結、粗體開頭清單），以自己的文字併入 `references/lint.md` L 組 |

## 檢查與驗證紀錄

- Lint 的十一組 regex 以 34 個繁體正例與 5 個反例測試通過（2026-11-14）。
- 2026-11-14 完成〈GSC 生成式 AI 報表〉A/B/C 三組對照與 C 組第二輪審稿除痕實測（`work/2026-11-14-gsc-gen-ai-test/`）。

## 變更歷史

- 2026-11-14｜0.1.0｜由 AI Studio 底稿改寫為五階段流程
- 2026-11-14｜0.2.0｜吸收 `editorial-pipeline` 並改為「第一輪總編自由成稿 → 第二輪審稿除痕」雙輪制，移除獨立的 `editorial-pipeline`
- 2026-11-14｜0.2.1｜依作者回饋放寬 `references/lint.md` K 組與 `SKILL.md` 的冒號（`：`）約束：保留標題、小標與正常語義的冒號，僅針對「粗體標籤＋冒號」條列、戲劇化停頓冒號、「結論／結語：」前綴與單段過密堆疊做局部改寫；破折號仍原則上排除
- 2026-11-14｜0.2.2｜依作者回饋區分證據嚴謹度：`research` 維持完整分母與 `〔待查〕` 底線；`growth`／`news` 等一般文章沿用具名公開論文與報告時可直接採用數據，無可靠出處或不必要細節則直接刪減
