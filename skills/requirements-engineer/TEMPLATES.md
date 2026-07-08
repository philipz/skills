# Requirements Document Templates

Ready-to-use templates for requirements documentation. Copy and fill in for each project.

---

## Business Requirements Specification (BRS)

```markdown
# Business Requirements Specification
## Project: [Project Name]
## Version: [x.x] | Date: [YYYY-MM-DD] | Status: [Draft/Approved]

### 1. Business Objectives
- **Objective**: [What business outcome is expected]
- **Success Metrics**: [Measurable KPIs]
- **Target Date**: [When value must be realized]

### 2. Background & Context
[Problem statement, current state (As-Is), market drivers]

### 3. Scope
- **In Scope**: [What is included]
- **Out of Scope**: [What is explicitly excluded]
- **Constraints**: [Budget, timeline, technology, regulatory]

### 4. Stakeholders
| Name/Role | Category | Interest | Influence |
|-----------|----------|----------|-----------|
| [Name]    | Decision Maker / User / Influencer | High/Med/Low | High/Med/Low |

### 5. Business Requirements
| ID | Requirement | Priority | Rationale |
|----|-------------|----------|-----------|
| BR-001 | [Statement] | Must/Should/Could/Won't | [Why] |

### 6. Assumptions & Dependencies
- **Assumptions**: [What is assumed to be true]
- **Dependencies**: [External systems, teams, decisions]

### 7. Risks
| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| [Risk description] | High/Med/Low | High/Med/Low | [Strategy] |

### 8. Approval
| Role | Name | Signature | Date |
|------|------|-----------|------|
```

---

## Stakeholder Requirements Specification (StRS)

```markdown
# Stakeholder Requirements Specification
## Project: [Project Name]
## Version: [x.x] | Date: [YYYY-MM-DD] | Status: [Draft/Approved]
## Parent: [Link to BRS]

### 1. User Classes & Characteristics
| User Class | Description | Volume | Frequency | Technical Level |
|------------|-------------|--------|-----------|-----------------|
| [Class A]  | [Who they are] | [Count] | [Daily/Weekly] | [Novice/Expert] |

### 2. Operational Scenarios
#### Scenario: [Scenario Name]
- **Actor**: [User class]
- **Goal**: [What the user wants to achieve]
- **Precondition**: [What must be true before]
- **Main Flow**:
  1. [Step 1]
  2. [Step 2]
  3. [Step 3]
- **Postcondition**: [What is true after success]
- **Alternative Flows**: [Variations]
- **Exception Flows**: [Error paths]

### 3. Stakeholder Requirements
| ID | Requirement | Source | Priority | Business Req |
|----|-------------|--------|----------|-------------|
| StR-001 | [Statement] | [Who/what] | Must/Should/Could | BR-001 |

### 4. Non-Functional Stakeholder Needs
| ID | Quality | Requirement | Priority |
|----|---------|-------------|----------|
| StR-NFR-001 | Usability | [Statement] | Must |

### 5. Constraints & Assumptions
[Stakeholder-level constraints and assumptions]
```

---

## System / Software Requirements Specification (SyRS / SRS)

```markdown
# System Requirements Specification
## Project: [Project Name]
## Version: [x.x] | Date: [YYYY-MM-DD] | Status: [Draft/Approved]
## Parent: [Link to StRS]

### 1. System Overview
[High-level system description, context diagram reference]

### 2. System Context
[External systems, interfaces, data flows — reference context diagram]

### 3. Functional Requirements
| ID | Requirement | Source | Priority | Verification | Status |
|----|-------------|--------|----------|-------------|--------|
| SyR-001 | The system shall [behavior] when [condition] | StR-001 | Must | Test | Draft |

### 4. Non-Functional Requirements

#### 4.1 Performance
| ID | Requirement | Metric | Target | Verification |
|----|-------------|--------|--------|-------------|
| SyR-NFR-P01 | [Statement] | Response time | ≤ 200ms | Test |

#### 4.2 Security
| ID | Requirement | Standard | Verification |
|----|-------------|----------|-------------|
| SyR-NFR-S01 | [Statement] | [e.g., OWASP] | Test |

#### 4.3 Reliability
| ID | Requirement | Metric | Target | Verification |
|----|-------------|--------|--------|-------------|
| SyR-NFR-R01 | [Statement] | Availability | 99.95% | Analysis |

#### 4.4 Other Quality Attributes
[Maintainability, Portability, Compatibility — as needed]

### 5. Interface Requirements
| ID | Interface | Type | Protocol | Data Format |
|----|-----------|------|----------|-------------|
| SyR-IF-001 | [System name] | REST API / Message Queue / File | HTTPS / AMQP | JSON / XML |

### 6. Data Requirements
[Data entities, retention policies, migration needs]

### 7. Transition Requirements
| ID | Requirement | Duration | Dependencies |
|----|-------------|----------|-------------|
| TR-001 | [Temporary capability] | [Time period] | [What it depends on] |

### 8. Traceability Matrix
| System Req | Stakeholder Req | Business Req | Test Case |
|-----------|-----------------|-------------|-----------|
| SyR-001   | StR-001         | BR-001      | TC-001    |
```

---

## User Story Template

```markdown
### [Story ID]: [Short Title]

**As a** [user role/persona],
**I want to** [action/capability],
**So that** [business value/benefit].

#### Acceptance Criteria

**Given** [precondition/context]
**When** [action/trigger]
**Then** [expected outcome]

**Given** [alternative precondition]
**When** [action/trigger]
**Then** [alternative outcome]

#### Attributes
- **Priority**: Must / Should / Could / Won't
- **Story Points**: [estimate]
- **Risk**: High / Medium / Low
- **Dependencies**: [related story IDs]
- **DoR**: [ ] Criteria clear [ ] Testable [ ] Estimated [ ] Independent
- **DoD**: [ ] Code complete [ ] Tests pass [ ] Reviewed [ ] Documented
```

---

## Epic Template

```markdown
### [Epic ID]: [Epic Title]

**Business Objective**: [Link to BR-xxx]
**Description**: [High-level capability this epic delivers]
**Success Metrics**: [How we know this epic succeeded]

#### Stories
| Story ID | Title | Priority | Status |
|----------|-------|----------|--------|
| [ID]     | [Title] | Must   | To Do  |

#### Acceptance Criteria (Epic-level)
- [ ] [High-level criterion 1]
- [ ] [High-level criterion 2]

#### Dependencies & Risks
- [Dependency / Risk description]
```

---

## Requirements Traceability Matrix (RTM) Template

```markdown
# Requirements Traceability Matrix
## Project: [Project Name] | Version: [x.x] | Date: [YYYY-MM-DD]

| Req ID | Type | Source | Business Req | Stakeholder Req | System Req | Design | Test Case | Status |
|--------|------|--------|-------------|-----------------|-----------|--------|-----------|--------|
| [ID] | FR/NFR | [Source] | BR-xxx | StR-xxx | SyR-xxx | [Module] | TC-xxx | [Status] |

### Legend
- **Type**: FR = Functional, NFR = Non-Functional, TR = Transition, CON = Constraint
- **Status**: Draft → In Review → Approved → Implemented → Verified
```
