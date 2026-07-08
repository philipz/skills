# Requirements Engineering Reference

Comprehensive reference aligned with **IEEE 29148:2018**, **IIBA BABOK v3**, and **ISO 25010**.

---

## Core Responsibilities

- **Requirements Analysis**: Gather, analyze, and document functional and non-functional requirements
- **Stakeholder Communication**: Bridge business stakeholders and technical teams effectively
- **Documentation**: Create comprehensive specifications, user stories, and acceptance criteria
- **Requirements Management**: Track requirements through complete development lifecycle
- **Business Analysis**: Understand business processes and translate to technical requirements
- **Strategy & Gap Analysis**: Evaluate current state (As-Is), define future state vision (To-Be), and perform gap analysis to formulate change strategies
- **Solution Evaluation**: Measure post-implementation solution performance against business objectives to ensure actual value realization
- **Conflict Resolution**: Identify and resolve conflicting requirements among stakeholders through negotiation and facilitation

---

## Elicitation Techniques

Select techniques based on stakeholder availability, project complexity, and domain:

| Technique | Best For | Effort |
|-----------|----------|--------|
| **Structured Interviews** | Deep-dive with individual stakeholders | Medium |
| **Workshops / JAD Sessions** | Cross-functional consensus building | High |
| **Surveys / Questionnaires** | Large stakeholder groups, quantitative data | Low |
| **Observation / Job Shadowing** | Understanding actual workflows vs. stated processes | Medium |
| **Document Analysis** | Existing systems, regulations, legacy documentation | Low |
| **Prototyping** (Low-fi / High-fi) | UI-heavy systems, validating user expectations | High |
| **Brainstorming / Mind Mapping** | Exploring solution space, ideation | Low |
| **Use Case / User Story Mapping** | Functional scope definition, journey mapping | Medium |
| **Benchmarking** | Competitive analysis, industry best practices | Medium |
| **Focus Groups** | User preference validation, usability insights | Medium |
| **Interface Analysis** | System integration points, API contracts | Medium |
| **Reverse Engineering** | Undocumented legacy systems | High |

### Facilitation Guidelines

- Prepare agenda and ground rules before workshops
- Use visual aids (whiteboards, sticky notes, wireframes)
- Document decisions and action items in real-time
- Follow up within 48 hours with minutes and open items

---

## Requirements Hierarchy (IEEE 29148)

```
Business Requirements (BRS)
  ├── WHY: Business objectives, success criteria, constraints
  └── Audience: Sponsors, executives, portfolio managers

Stakeholder Requirements (StRS)
  ├── WHAT (user perspective): Operational scenarios, user needs, constraints
  └── Audience: End-users, operators, support staff

System / Software Requirements (SyRS / SRS)
  ├── WHAT (technical perspective): Functional behavior, interfaces, data, NFRs
  └── Audience: Architects, developers, testers, integrators
```

Each level refines the previous. Traceability links MUST connect all three levels.

---

## Well-Formed Requirement Qualities

Every individual requirement MUST satisfy these characteristics (IEEE 29148):

| Quality | Description | Test |
|---------|-------------|------|
| **Necessary** | Essential to meet a stakeholder need | Can you trace it to a business objective? |
| **Implementation-free** | Describes WHAT, not HOW | Does it avoid prescribing technology or design? |
| **Unambiguous** | Only one possible interpretation | Can two people read it and agree on meaning? |
| **Consistent** | Does not conflict with other requirements | Cross-check against full requirement set |
| **Complete** | Fully specifies the behavior or constraint | No TBDs, no implicit assumptions |
| **Singular** | Expresses exactly one requirement | Contains no "and" / "or" joining separate needs |
| **Feasible** | Achievable within project constraints | Confirmed by technical team |
| **Traceable** | Linked to source and forward to design/test | RTM entry exists |
| **Verifiable** | Can be confirmed through inspection, analysis, demo, or test | Verification method assigned |
| **Bounded** | Clearly defined scope and limits | Boundary conditions specified |
| **Affordable** | Deliverable within agreed cost | Cost estimate available |

### Set-Level Qualities

The complete requirements set MUST also be:

- **Complete** — All requirements captured, no gaps
- **Consistent** — No contradictions between requirements
- **Affordable** — Total scope within budget
- **Bounded** — System boundary clearly defined

---

## Requirement Attributes

Every requirement MUST carry these attributes:

| Attribute | Description | Example |
|-----------|-------------|---------|
| **ID** | Unique identifier | `REQ-AUTH-001` |
| **Title** | Short descriptive name | "User login with MFA" |
| **Description** | Full requirement statement | See templates |
| **Type** | Functional / Non-functional / Constraint / Transition | Functional |
| **Level** | Business / Stakeholder / System | Stakeholder |
| **Priority** | MoSCoW (Must/Should/Could/Won't) or numeric | Must |
| **Status** | Draft → In Review → Approved → Implemented → Verified | Draft |
| **Source** | Who/what originated this requirement | "CTO interview 2024-03-15" |
| **Rationale** | Why this requirement exists | "Regulatory compliance mandate" |
| **Risk** | Risk if not implemented or if implemented poorly | High / Medium / Low |
| **Dependencies** | Other requirements this depends on | `REQ-AUTH-003` |
| **Verification Method** | Inspection / Analysis / Demonstration / Test | Test |
| **Owner** | Responsible stakeholder | "Product Owner" |

---

## Non-Functional Requirements Framework (ISO 25010)

Systematically address all quality characteristics:

| Quality Characteristic | Sub-characteristics | Example Requirement |
|------------------------|--------------------|--------------------|
| **Functional Suitability** | Completeness, correctness, appropriateness | "System shall calculate interest per IFRS 9" |
| **Performance Efficiency** | Time behavior, resource utilization, capacity | "API response ≤ 200ms at 1000 concurrent users" |
| **Compatibility** | Co-existence, interoperability | "System shall exchange data via ISO 20022 messages" |
| **Usability** | Learnability, operability, accessibility | "New user completes onboarding in < 5 min" |
| **Reliability** | Maturity, availability, fault tolerance, recoverability | "99.95% uptime; RTO ≤ 15 min, RPO ≤ 5 min" |
| **Security** | Confidentiality, integrity, authenticity, accountability | "All PII encrypted at rest (AES-256)" |
| **Maintainability** | Modularity, reusability, analyzability, modifiability, testability | "Code coverage ≥ 80%; all modules independently deployable" |
| **Portability** | Adaptability, installability, replaceability | "Run on Linux and Windows without code changes" |

---

## Verification & Validation (V&V)

### Verification Methods (IEEE 29148)

| Method | Description | When to Use |
|--------|-------------|-------------|
| **Inspection** | Formal review of requirement documents | All requirements — mandatory |
| **Analysis** | Mathematical/logical reasoning, simulation | Complex algorithms, safety-critical |
| **Demonstration** | Show system behavior (prototype, staging) | UI/UX, workflow requirements |
| **Test** | Execute system and compare to expected results | Functional, performance, security |

### Validation Activities

- **Stakeholder Reviews**: Walk through requirements with business owners
- **Prototyping**: Validate user expectations before implementation
- **Model Validation**: Verify models against real-world behavior
- **Acceptance Testing**: Confirm delivered solution meets stakeholder needs

### V&V Checklist

- [ ] Every requirement has an assigned verification method
- [ ] Inspection review completed with stakeholders
- [ ] Ambiguity detected and resolved
- [ ] Conflicting requirements identified and resolved
- [ ] Acceptance criteria defined and testable
- [ ] Traceability links verified (source ↔ requirement ↔ test)

---

## Requirements Traceability Matrix (RTM)

### Purpose

Bidirectional traceability ensures:
- **Forward**: Business need → Stakeholder req → System req → Design → Test case
- **Backward**: Test case → System req → Stakeholder req → Business need

### RTM Structure

| Req ID | Source | Business Req | Stakeholder Req | System Req | Design Element | Test Case | Status |
|--------|--------|-------------|-----------------|------------|----------------|-----------|--------|
| REQ-001 | CTO Interview | BR-01 | StR-01 | SyR-01, SyR-02 | Module A | TC-001, TC-002 | Verified |

### Maintenance Rules

- Update RTM whenever a requirement is added, changed, or removed
- Flag orphan requirements (no source) and orphan test cases (no requirement)
- Review RTM at each milestone / sprint boundary
- Use automated tools when possible (Jira, Azure DevOps, DOORS)

---

## Baseline & Change Management

### Baseline Process

1. **Draft baseline** — All requirements documented and reviewed
2. **Review & approval** — Stakeholders formally sign off
3. **Freeze** — Baseline version locked; no changes without change control
4. **Version control** — Each baseline is a numbered snapshot (v1.0, v1.1, ...)

### Change Control Process

```
Change Request Submitted
  → Impact Analysis (scope, cost, schedule, risk, dependencies)
  → Review by Change Control Board (CCB) or Product Owner
  → Decision: Approve / Reject / Defer
  → If Approved: Update requirements, RTM, and baseline version
  → Notify all affected stakeholders
```

### Impact Analysis Checklist

- [ ] Which requirements are affected?
- [ ] What is the effort/cost impact?
- [ ] Does this affect the schedule?
- [ ] Are there new risks?
- [ ] Which downstream artifacts need updating (design, tests, docs)?
- [ ] Which stakeholders need to be informed?

---

## Business Analysis Planning (BABOK KA1)

### Planning Activities

- **Approach selection** — Predictive (waterfall), Adaptive (agile), or hybrid
- **Stakeholder engagement plan** — Who, when, how to communicate
- **Requirements management plan** — Tools, naming conventions, storage, review cadence
- **Governance** — Decision authority, escalation paths, approval workflows

### Stakeholder Analysis

| Category | Examples | Engagement Level |
|----------|----------|-----------------|
| **Decision Makers** | Sponsors, executives, product owners | Manage closely |
| **Primary Users** | End-users who interact daily | Keep satisfied |
| **Secondary Users** | Occasional users, administrators | Keep informed |
| **Influencers** | Regulators, architects, domain experts | Monitor |
| **Impacted Parties** | Support teams, downstream systems | Keep informed |

### Stakeholder Map

Classify stakeholders on a **Power × Interest** grid:

```
High Power, High Interest  → Manage closely (co-create)
High Power, Low Interest   → Keep satisfied (regular updates)
Low Power, High Interest   → Keep informed (workshops, demos)
Low Power, Low Interest    → Monitor (newsletters)
```

---

## Risk-Based Requirements Analysis

### Risk Categories

| Category | Examples |
|----------|----------|
| **Ambiguity Risk** | Vague requirements, multiple interpretations |
| **Volatility Risk** | Requirements likely to change frequently |
| **Complexity Risk** | Requirements involving complex integrations or algorithms |
| **Dependency Risk** | Requirements dependent on external systems or third parties |
| **Compliance Risk** | Regulatory requirements with legal consequences |

### Mitigation Strategies

- **High-risk requirements first** — Prioritize elicitation, prototyping, and validation
- **Spike / PoC** — De-risk technical uncertainty early
- **Frequent validation** — Short feedback loops with stakeholders
- **Contingency requirements** — Define fallback behaviors
- **Traceability** — Ensure all risk items have corresponding test coverage

---

## Documentation Standards

### Requirement Types

- **Functional Requirements**: Clear, testable, traceable specifications of system behavior
- **Non-Functional Requirements**: Quality attributes per ISO 25010 (see above)
- **User Stories**: Well-formed with acceptance criteria (see [TEMPLATES](TEMPLATES.md))
- **Business Rules**: Constraints, policies, business logic
- **Transition Requirements**: Temporary capabilities for state transition (data migration, training, business continuity)
- **Constraints**: Technical, regulatory, or organizational limitations

### Requirements Modeling Techniques

| Model Type | Purpose | Tool |
|------------|---------|------|
| **Context Diagram** | System boundary and external actors | Draw.io, Mermaid |
| **Use Case Diagram** | Functional scope and actor interactions | UML |
| **Data / Information Model** | Entities, relationships, attributes | ERD |
| **Process / Activity Model** | Workflow and decision flows | BPMN, Activity Diagram |
| **State Diagram** | Object lifecycle and state transitions | UML State Machine |
| **User Story Map** | User journeys and release planning | Physical board, Miro |

---

## Acceptance Criteria Formats

### Given-When-Then (Gherkin)

```gherkin
Given [precondition / context]
When  [action / trigger]
Then  [expected outcome]
And   [additional outcome]
```

### Checklist-Based

```markdown
- [ ] User can log in with valid credentials
- [ ] Error message shown for invalid password
- [ ] Account locked after 5 failed attempts
- [ ] Audit log records all login attempts
```

### Rule-Based

```markdown
Rule: Order discount calculation
- Orders over $100 receive 10% discount
- Orders over $500 receive 15% discount
- Discount does not apply to clearance items
- Only one discount code per order
```
