# examples/

實際由本 repo 兩個 skill 產出格式所生成的範例 HTML（手動依 SKILL.md 規格產出，非 skill 自動執行結果，但完全依規格逐項對照）。

## 內容

| 檔案 | Skill | 內容 |
|---|---|---|
| `bilingual-doc-annotator/einstein-1905-emc2-excerpt.html` | bilingual-doc-annotator | DOC_TYPE=academic，DE → 繁體中文，節錄 Einstein 1905 論文開篇句與結論句各一段 |
| `study-visual-generator/einstein-1905-emc2-quiz.html` | study-visual-generator (TYPE_A) | 對應上述兩段的理解題，折疊答案卡，以 `對應Qn` 雙向連結 |

## 來源與授權（使用前必讀）

- 原文：Albert Einstein, *Ist die Trägheit eines Körpers von seinem Energieinhalt abhängig?*, Annalen der Physik 18 (1905), 639–641。
- **著作權狀態**：Einstein 1955 年逝世。EU 著作權年限為 death+70（計至該年年底），即 **2025/12/31 到期**。以生成時間點（2026）判斷，德文原文文字已進入公有領域，可自由重製。
- **未採用之素材**：未直接下載／重製 [Uni Augsburg Annalen der Physik Historic Papers](https://myweb.rz.uni-augsburg.de/~eckern/adp/history/Einstein-in-AdP.htm) 站上的期刊掃描 PDF ——掃描檔本身的排版／影像可能存在獨立於原文之外的權利歸屬，該站也未標示明確的重製授權條款。
- **實際採用之素材**：僅節錄兩句經多方獨立來源交叉驗證、逐字一致的公有領域原文（開篇句、結論句），非全文轉載。完整全文請自行取用上述 Uni Augsburg 連結，或 [de.Wikisource / Internet Archive](https://de.wikisource.org/wiki/Albert_Einstein) 掃描檔。
- **翻譯／問答內容**：中文譯文、批注文字、理解題與答案，均為本次示範原創撰寫，非引用任何第三方譯本或教材。

## 已知問題（阻斷項，建議優先處理）

目前 `skills/` 資料夾下的兩個檔案 `bilingual-doc-annotator`、`study-visual-generator` 是**沒有副檔名的純文字檔**，不是 `skills/<name>/SKILL.md` 的資料夾結構。

README 裡的安裝指令：
```
cp -r bilingual-annotator-toolkit/skills/* .claude/skills/
```
會把這兩個檔案原樣複製成 `.claude/skills/bilingual-doc-annotator`、`.claude/skills/study-visual-generator`（仍是無副檔名純文字檔），而不是 Claude Skills 載入器預期的：
```
.claude/skills/bilingual-doc-annotator/SKILL.md
.claude/skills/study-visual-generator/SKILL.md
```
**結果：目前的檔案結構下，這兩個 skill 在 Claude Code / claude.ai 中都無法被正確辨識載入。** 修法：
```bash
mkdir -p skills/bilingual-doc-annotator skills/study-visual-generator
git mv skills/bilingual-doc-annotator skills/bilingual-doc-annotator/SKILL.md
git mv skills/study-visual-generator skills/study-visual-generator/SKILL.md
```
建議在補 `examples/` 的同一個 PR 一併修正，否則範例做得再完整，使用者複製指令後仍無法實際跑起來。

## GitHub Pages 靜態預覽（非阻斷，可延後）

之後要做的話，最省事路徑：`/docs` 資料夾直接放這些 HTML，repo Settings → Pages → Source 選 `main /docs`，不需要 build step。
