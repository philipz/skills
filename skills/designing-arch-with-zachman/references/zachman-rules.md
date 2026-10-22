# Zachman Framework — working reference

Paraphrased summary for classifying answers into cells. Source: John A. Zachman,
*The Zachman Framework for Enterprise Architecture: Primer for Enterprise Engineering
and Manufacturing* (2003). Do not quote the source verbatim in generated documents.

## The two axes

**Columns = the six primitive interrogatives (abstractions).** Each column describes ONE
independent variable of the system. Each column's generic model is the variable related
to itself:

| Column | Interrogative | Describes | Generic model | Typical artifact |
|---|---|---|---|---|
| C1 | What | Things / data (bill of materials) | Thing — relationship — Thing | Entity / data model |
| C2 | How | Processes / functions (transformations) | Process — input/output — Process | Process / function model |
| C3 | Where | Locations / network (connectivity) | Node — link — Node | Logistics / topology model |
| C4 | Who | People / roles (who does what work) | Role — work product — Role | Workflow / interface model |
| C5 | When | Time / events (dynamics) | Event — cycle — Event | Schedule / state / timing model |
| C6 | Why | Motivation (ends and means) | End — means — End | Goals / strategy / business-rule model |

Event = a point in time; cycle = a length of time. End = a desired state (objective);
means = a course of action to reach it (strategy). At the System row, ends become
*structural* business rules and means become *action* business rules.

**Rows = the perspectives (audiences).** Each row is a different model of a different
thing, NOT a more detailed version of the row above.

| Row | Perspective | Name | What it captures | In scope for this skill |
|---|---|---|---|---|
| R1 | Planner | Scope (contextual) | Lists: the boundary and the relevant constituents | ✅ |
| R2 | Owner | Business model (conceptual) | How the owner will use the result; business language | ✅ |
| R3 | Designer | System model (logical) | Technology-independent mechanisms that realise R2 | ✅ |
| R4 | Builder | Technology model (physical) | R3 constrained by chosen technology | ✅ |
| R5 | Sub-contractor | Detailed representations (out-of-context) | Product/vendor-level specs: DDL, code specs | ❌ out of scope |
| R6 | — | Functioning system | The running thing itself (not a representation) | ❌ out of scope |

"Conceptual / logical / physical" do NOT mean high / medium / low detail. Conceptual =
what the owner can think of wanting; logical = unconstrained designer mechanisms;
physical = those mechanisms constrained by technology.

## The rules (apply when classifying and tracing)

1. **Never add, remove, or rename rows or columns.** Keep the names: Why, What, How, Who,
   Where, When and Scope / Business / System / Technology. Renaming changes meaning.
2. **Each column has one simple generic model** (table above). If an answer does not fit
   the column's generic model, it belongs in another column.
3. **Each cell specialises its column's model in its row's vocabulary.** Level of detail is
   a property of a cell, not of a column: any cell can be sketched or detailed. Moving down
   a column is a *transformation* (different audience, different constraints), not
   "add more detail". The same word ("employee") means different things in different rows.
4. **One fact in one cell.** A concept classified into two cells means the analysis is
   denormalised; pick the single correct cell and link from the others.
5. **No diagonal relationships.** Relate a cell only to the cell above/below in its column
   and to the other cells in its row. A link like "R2 Owner goal → R4 database choice" must
   be expressed through R3 (vertical) — never directly.
6. **Names are fixed** (see rule 1). Translate explanations, not the axis labels.
7. **The logic is recursive.** The same grid can describe an enterprise, one system, or one
   component. The analyst — not the framework — sets the boundary.

## Key consequences for architecture work

- **Every cell you do not make explicit is an assumption** — i.e. accepted risk of scrap
  and rework. Unfilled cells must be recorded as assumptions, never silently skipped.
- **Boundary vs jurisdiction.** Draw the boundary wider than what the team controls and the
  models must be *negotiated* with other owners; draw it narrower and the system becomes
  a future legacy that does not integrate.
- **What (C1), Where (C3), Why (C6) need enterprise-wide attention** even for one system:
  inconsistent data meaning, fragile connectivity, and inconsistently enforced business
  rules are fixable after implementation only by scrap and rework.
- **Data meaning is frozen once implemented.** After the fact you can only fix cosmetic
  mismatches (names, formats) by interfacing, not meaning.
- **Change management.** When a cell changes, check impact on the cell above, the cell
  below, and every other cell in the same row; infer anything further from those.
- **Levels of detail differ by column:** What = bill of materials, How = hierarchical,
  Where = geometric, Who = matrix, When = cyclical, Why = network. Only How decomposes
  hierarchically — avoid forcing other columns into trees.
