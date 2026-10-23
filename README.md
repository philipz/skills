# Philipz Skills

[![skills.sh](https://skills.sh/b/philipz/skills)](https://skills.sh/philipz/skills)

Agent skills for software engineering, architecture design, and requirements engineering.

## Quickstart

Install skills using the skills CLI:

```bash
npx skills@latest add philipz/skills
```

Pick the skills you want to install on your coding agent (Claude Code, Codex, etc.).

## Skills

### 1. [requirements-engineer](./skills/requirements-engineer/SKILL.md)

Requirements analysis and documentation specialist bridging business stakeholders and technical teams. Aligned with **IEEE 29148** and **BABOK v3**.

- **Purpose**: Structure requirements gathering, business analysis, user story definition, and specification authoring.
- **Key Capabilities**:
  - Author Agile User Stories with Definition of Ready (DoR), Definition of Done (DoD), and Gherkin-style Acceptance Criteria.
  - Create standard requirement specifications: Business Requirements Specification (BRS), System Requirements Specification (SRS), Product Requirements Document (PRD), and Business Requirements Document (BRD).
  - Map stakeholder needs to functional and non-functional requirements with complete traceability.

### 2. [designing-arch-with-zachman](./skills/designing-arch-with-zachman/SKILL.md)

Design and document software system architecture using the **Zachman Framework** (6 × 6 classification grid).

- **Purpose**: Systematically explore and align on system architecture through structured 5W1H questions (Why, What, How, Who, Where, When) across multiple perspectives.
- **Key Capabilities**:
  - Interview-driven architecture exploration covering Scope, Business, System, and Technology rows.
  - Prevent silent assumptions by explicitly tracking unfilled cells and risks.
  - Generate comprehensive architecture documentation grounded in enterprise architecture discipline.

### 3. [lean-formal-verification](./skills/lean-formal-verification/SKILL.md)

Formal verification workflow for program logic, business rules, algorithms, and state machines using **Lean 4**, implementing Carl M. Kadie's 2026 nine rules ("Vibe Validation").

- **Purpose**: Verify that code correctly implements owner-confirmed business rules without shortcutting proofs (`sorry`, unauthorized axioms, or false green builds).
- **Key Capabilities**:
  - Structured 8-phase verification workflow producing reviewable artifacts (`RULES.md`, `MODEL-MAP.md`, and machine-checked Lean proofs).
  - Enforce strict verification gates and guardrails (`verify-lean.sh`) to detect `sorry`, axioms, and metric regressions.
  - Model extraction and abstraction guidance across Java, TypeScript, Rust, and Python.

