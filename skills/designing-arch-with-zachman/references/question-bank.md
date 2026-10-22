# Question bank — 24 cells (Row 1–4 × six columns)

One primary question per cell. Ask the row's **Why first**, then What → How → Who →
Where → When. Use follow-ups only when the answer is vague or contradicts another cell.

Rule of thumb: at Row 1 the answers are **lists**. At Row 2 they are the owner's business
language. At Row 3 the same subject is re-expressed as technology-independent mechanisms.
At Row 4 it is constrained by the chosen technology. Do not let a lower row restate the
upper row in the same words — if it does, the cell has not actually been transformed.

## Row 1 — Scope (Planner)

| Cell | Question |
|---|---|
| 1.Why | 這個系統存在的商業理由是什麼？用什麼可量測的成果判斷它成功？ |
| 1.What | 業務上哪些「事物」必須被管理？請列清單（名詞），不用畫關係。 |
| 1.How | 業務上有哪些主要流程？請列清單（動詞），不用畫流程圖。 |
| 1.Who | 哪些組織單位與利害關係人會使用、被影響、或必須被知會？ |
| 1.Where | 營運涵蓋哪些地點／區域／法規管轄範圍？ |
| 1.When | 有哪些關鍵業務事件與週期（日／月／年、結帳、旺季）？ |

**Always also ask in Row 1 (fixed, do not skip):**
- 這個系統的邊界，和你們團隊實際能決定（管轄）的範圍一致嗎？有沒有哪一塊屬於別人的權責、必須跟對方協商？
- What／Where／Why 這三欄有沒有部分必須與其他系統或全企業共用？共用的話，誰是那個定義的擁有者？

## Row 2 — Business model (Owner)

| Cell | Question |
|---|---|
| 2.Why | 業務目標與策略是什麼？有哪些業務規則（含例外）在約束這件事？（目標=end，策略=means） |
| 2.What | 業務實體有哪些、彼此的關係是什麼？（用業務人員的詞彙，不是資料表） |
| 2.How | 業務流程實際怎麼跑？每個流程的輸入與輸出是什麼？ |
| 2.Who | 每個角色負責什麼工作、產出什麼？（工作流，而不是權限） |
| 2.Where | 業務據點之間如何連結？哪些業務在哪個地點發生？ |
| 2.When | 業務事件、週期、時限與 SLA？什麼事必須在什麼之前完成？ |

## Row 3 — System model (Designer, logical)

| Cell | Question |
|---|---|
| 3.Why | 這些業務規則要用什麼結構性／行為性規則來表達？哪些是必須由系統強制、哪些留給人判斷？ |
| 3.What | 邏輯資料模型是什麼？每個實體的概念擁有者（source of truth）是誰？ |
| 3.How | 系統分成哪些應用元件／模組？各自的邊界與對外介面是什麼？ |
| 3.Who | 人機介面長什麼樣？角色如何對應到權限與可見範圍？ |
| 3.Where | 邏輯節點與整合點在哪？什麼東西要跨網路邊界？ |
| 3.When | 有哪些系統事件與處理結構？哪些同步、哪些非同步？狀態機長什麼樣？ |

## Row 4 — Technology model (Builder, physical)

| Cell | Question |
|---|---|
| 4.Why | 規則實際用什麼機制落地（程式碼／規則引擎／設定／外部服務）？哪些非功能需求與法遵約束在限制技術選擇？ |
| 4.What | 實際的資料儲存選型與實體結構是什麼？保存與歸檔策略？ |
| 4.How | 實際的技術棧、框架、程式庫與建置方式是什麼？ |
| 4.Who | 身分認證與授權實際怎麼實作？用哪個 IdP／群組／憑證？ |
| 4.Where | 實際部署在哪（雲端／地端／區域）？網路與環境（dev/staging/prod）怎麼切？ |
| 4.When | 排程、逾時、重試、備份與清理的實際參數是什麼？ |

## Follow-ups that commonly surface hidden assumptions

Use these when an answer sounds settled but has an unknown dependency behind it:

- 「這件事是誰決定的？他們在不在這個房間？」（決策權歸屬）
- 「如果這個假設不成立，會影響哪幾格？」（連接假設與風險）
- 「有沒有一個既有的東西你必須跟它對齊／整合？」（整合邊界）
- 「這個答案是現況還是期望？」（as-is vs to-be；brownfield 尤其重要）
- 「有沒有你不希望我做的決定？哪些部分你明確不要由 agent 決定？」
- 「誰會讀這份文件、拿它來做什麼？」（決定文件的深度，不是決定內容）

## Handling answers (per the agreed interview contract)

| User response | Record as |
|---|---|
| Gives a concrete answer | ✅ 使用者決策 |
| Says 「你決定就好」 / 「不知道」 | Propose ONE recommended answer, ask for explicit confirmation. If accepted → 🤝 已接受建議. If still unknown → ⚠️ 假設與風險 (with who decides and by when) |
| Contradicts an earlier answer | Stop, point out the specific earlier cell, resolve before continuing |
| Answers a different column's question | Note it in the correct cell, then re-ask the current cell |
