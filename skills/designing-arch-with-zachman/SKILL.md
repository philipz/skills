---
name: designing-arch-with-zachman
description: Use when the user wants to design or document a software system's architecture using the Zachman Framework, align on architecture through 5W1H / What-How-Where-Who-When-Why questions, produce an architecture design document under docs/, or update an existing architecture baseline before a change.
---

# Designing architecture with the Zachman Framework

## Overview

Zachman is a **6 × 6 classification grid**, not a process: six interrogatives (Why, What,
How, Who, Where, When) × six perspectives (Scope, Business, System, Technology, Detailed,
Functioning). This skill interviews the user to fill the grid, then writes the document.

Two rules carry the whole skill:

- **Every cell you leave unanswered is an assumption** — an accepted risk of scrap and
  rework. Unfilled cells are recorded, never silently dropped.
- **Never self-authorise.** The user's decisions are theirs; a deferral is not a decision.

**REQUIRED SUB-SKILL:** Use `grilling` for the round mechanics (frontier, rounds, ❓/➡️
question format, facts-vs-decisions split). This skill supplies the grid and the exit test.

## Scope

Fill **Row 1–4 × 6 columns = 24 cells**. Row 5 (detailed specs: DDL, code specs, vendor
product specs) and Row 6 (the functioning system) stay out of scope and are named as
out-of-scope in the document.

If the user wants fewer rows, do fewer — and record **every omitted row as a whole-row
assumption**. A shortened grid is fine; a silently shortened grid is not.

## Rounds

One row per round. Within a row, ask **Why first**, then What → How → Who → Where → When.

| Round | Cells | Notes |
|---|---|---|
| 1 | Row 1 (Scope) | Lists only — no diagrams. Plus the two boundary questions below. |
| 2 | Row 2 (Business) | Owner's business vocabulary. Business rules go in 2.Why. |
| 3 | Row 3 (System) | Same subject, re-expressed as technology-independent mechanisms. |
| 4 | Row 4 (Technology) | Now constrain by actual technology. |
| 5 | Write-up confirmation | Finalise, then ask the user to confirm shared understanding. |

Ask one row's six cells together; do not ask six columns' worth of one row as six rows, and
do not ask across rows in the same round. The next row's answers depend on the current row.

**Row 1 always includes these two, separately from the six cells:**

- Does the system boundary match what this team can actually decide? What part belongs to
  someone else and must be negotiated rather than declared?
- Are What / Where / Why partly shared with other systems or the whole enterprise? Who owns
  that definition?

## The three moves that silently corrupt the grid

These are the observed failure modes. Each has a fixed counter-move.

| Temptation | Why it corrupts | Do this instead |
|---|---|---|
| "I'll just infer R3 and R4 myself and save the user's time." | Skipping a row means its decisions were made by you, unlabelled. | Still interview Rs 3–4. If the user is out of patience, propose answers **one at a time and get explicit "yes"**, recording 🤝. |
| "They said 『你決定就好』 — I'll record my default as [決定] and move on." | A deferral is not an acceptance. | Propose exactly **one** recommended answer, state it plainly, and **wait**. Explicit acceptance → 🤝. Still unknown → ⚠️ assumption with *who decides* and *by when*. |
| "Business rule says >3 days, so the config parameter is 24 hours." | That is a diagonal jump R2 → R4, banned by the framework. | Route it: 2.Why rule → 3.Why rule form → 4.Why/4.When parameter. Write each intermediate cell. |

Also never: add or rename a row/column, put one concept in two cells, or draw a diagonal
relationship. See `references/zachman-rules.md`.

**A blanket go-ahead is not acceptance.** 「你決定就好」, 「剩下的你直接補完」,
「時間很趕」, or a bare 好 to a whole batch authorise you to *propose*, not to sign for
them. The one exception: a 好 in reply to a single, named proposal — "accept (a)?" → 好 —
is an explicit 🤝 for that one cell. When in doubt, narrow it to one cell and ask again.

## Cell status

Every cell carries exactly one marker:

| Marker | Meaning |
|---|---|
| ✅ | The user said it — a decision *or* a fact they supplied |
| 🔍 | You observed it yourself; cite the file path or command |
| 🤝 | The user explicitly accepted your proposed answer |
| ⚠️ | Assumption — deferred or unknown; goes in the risk register |
| ➖ | Not applicable, with the reason |

✅ and 🔍 are not interchangeable: anything the user told you is ✅ even if it is a fact,
and 🔍 without a cited source is really ⚠️. A cell with no marker has not been asked — that
is the check.

## Process

1. **Set up.** Mode is greenfield, or brownfield if docs/code exist. For brownfield,
   dispatch a sub-agent to pre-fill candidate 🔍 facts for Rows 3–4 (stack, data model,
   deployment, integrations) with file paths — facts are your job, decisions are the user's.
   Don't block the interview on it; fill those cells when it reports.
2. **Locate the document.** `docs/architecture/<system-slug>-zachman.md`. If a document for
   this system already exists, go to step 6 (change mode) instead.
3. **Interview one row per round** as described above, using `references/question-bank.md`.
4. **Write after every row.** Create or update the document from
   `templates/architecture-doc.md` with `status: draft`. Never hold the whole document in
   your head until the end — an interrupted interview must not lose work.
5. **Finalise.** All 24 cells carry a marker; matrix, assumption/risk register, and
   traceability table are complete; draw Mermaid diagrams only where a cell has enough
   content (Row 1 has none — it is a list). Then ask the user to confirm shared
   understanding, and only after that set `status: accepted`.
6. **Change mode** (document exists): ask only about the cells being changed, then check the
   cell above and below in the same column and all other cells in the same row — never
   diagonals. Update the revision log with what was re-checked.

## Document skeleton

Use `templates/architecture-doc.md`. Its sections are fixed: frontmatter → 4×6 matrix with
status markers → Rows 1–4 (six subsections each, every cell stating its source) →
boundary/shared → assumption & risk register (cell · assumption · rework risk · who decides,
by when) → traceability (vertical + horizontal only) → out of scope → ADRs (only if the
project has an ADR dir) → interview log → revision log.

Write prose in the user's language. Keep Zachman terms in English (Scope/Business/System/
Technology, Why/What/How/Who/Where/When) — translating the axis names changes their meaning.

## Red flags — you are about to do it wrong

- You are about to say "I'll infer the lower rows myself."
- You are about to write [決定] / "assumed" for a question the user answered 「你決定就好」.
- You are about to derive a technical parameter straight from a business rule.
- You are about to skip the assumption register because "almost everything is settled".
- You are about to set `status: accepted` without asking the user to confirm.
- You are about to widen scope to Row 5/6 because it is easy to add.
- You have written the document but the interview log is empty.

## Files

- `references/zachman-rules.md` — the two axes, the seven rules, the consequences that
  justify this skill's requirements, and where an autonomous agent belongs (C4, with its
  authority boundary and its non-determinism stated). Use it to decide which cell an answer
  belongs to.
- `references/question-bank.md` — the 24 primary questions, follow-ups, and how to record
  each kind of answer.
- `templates/architecture-doc.md` — the output template.
