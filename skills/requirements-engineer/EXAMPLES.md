# Requirements Engineering — Worked Example

End-to-end example demonstrating the full requirements workflow for a **User Authentication Module**.

---

## Step 1: Scope & Plan

**Problem**: The existing application uses password-only authentication. Regulatory audit requires multi-factor authentication (MFA) by Q3 2025.

**Stakeholders identified**:

| Name/Role | Category | Interest | Influence |
|-----------|----------|----------|-----------|
| CISO | Decision Maker | High | High |
| End Users | Primary User | Medium | Low |
| DevOps Team | Influencer | Medium | Medium |
| Compliance Officer | Influencer | High | High |

**Methodology**: Adaptive (2-week sprints)

---

## Step 2: Elicit

**Techniques used**:
- Structured interview with CISO → security requirements, compliance timeline
- Workshop with DevOps → infrastructure constraints, deployment concerns
- Survey to 200 end users → UX preferences for MFA methods
- Document analysis → regulatory standard (e.g., PCI DSS 4.0 Req 8.4)

**Key findings**:
- Users prefer push notifications over SMS OTP
- System must support hardware security keys for admin accounts
- Legacy API clients cannot use MFA; need alternative mechanism

---

## Step 3: Analyze & Model

### Requirements Hierarchy

```
BR-001: Achieve regulatory compliance for authentication (PCI DSS 4.0)
  └── StR-001: Users can authenticate with a second factor
      ├── SyR-001: System shall support TOTP-based authentication
      ├── SyR-002: System shall support push notification authentication
      ├── SyR-003: System shall support FIDO2 hardware security keys
      └── SyR-004: System shall provide API key auth for legacy clients
  └── StR-002: Admins can manage MFA policies per user group
      ├── SyR-005: Admin panel shall allow MFA method assignment by group
      └── SyR-006: System shall enforce MFA policy on next login
```

### Conflict Resolution

| Conflict | Resolution |
|----------|------------|
| Users want "remember device" vs. CISO wants MFA every login | Compromise: remember trusted devices for 30 days, re-auth for sensitive actions |
| Legacy API clients cannot do MFA | Approved exception: API key + IP allowlisting for service accounts |

---

## Step 4: Specify

### Example: Well-Formed System Requirement

| Attribute | Value |
|-----------|-------|
| **ID** | SyR-001 |
| **Title** | TOTP-based second factor authentication |
| **Description** | The system shall verify a 6-digit TOTP code (RFC 6238) during login when the user's MFA policy requires TOTP. The code shall have a 30-second validity window with ±1 step tolerance. |
| **Type** | Functional |
| **Level** | System |
| **Priority** | Must |
| **Status** | Approved |
| **Source** | CISO Interview 2025-01-15; PCI DSS 4.0 Req 8.4 |
| **Rationale** | Regulatory mandate for multi-factor authentication |
| **Risk** | High — non-compliance leads to audit failure |
| **Dependencies** | SyR-005 (MFA policy management) |
| **Verification Method** | Test |
| **Owner** | Security Team Lead |

### Example: Non-Functional Requirement

| Attribute | Value |
|-----------|-------|
| **ID** | SyR-NFR-P01 |
| **Title** | MFA verification response time |
| **Description** | The MFA verification API shall respond within 500ms at the 95th percentile under 5,000 concurrent authentication requests. |
| **Type** | Non-Functional (Performance) |
| **Priority** | Should |
| **Verification Method** | Test (load testing with k6) |

### Example: User Story with Acceptance Criteria

```markdown
### US-001: Login with TOTP

**As a** registered user with TOTP enabled,
**I want to** enter a 6-digit code from my authenticator app after my password,
**So that** my account is protected by multi-factor authentication.

#### Acceptance Criteria

**Given** I have entered valid credentials
**When** I submit a valid TOTP code within the 30-second window
**Then** I am logged in and redirected to my dashboard

**Given** I have entered valid credentials
**When** I submit an expired or invalid TOTP code
**Then** I see an error "Invalid code. Please try again."
**And** I can retry up to 5 times before being locked out for 15 minutes

#### Attributes
- **Priority**: Must
- **Story Points**: 5
- **Risk**: High
- **Dependencies**: US-003 (MFA setup flow)
- **DoR**: [x] Criteria clear [x] Testable [x] Estimated [x] Independent
- **DoD**: [ ] Code complete [ ] Tests pass [ ] Reviewed [ ] Documented
```

---

## Step 5: Validate & Verify

| Req ID | Method | Activity | Result |
|--------|--------|----------|--------|
| SyR-001 | Test | Unit tests for TOTP validation logic | ✅ Pass |
| SyR-001 | Demonstration | Prototype shown to CISO | ✅ Approved |
| SyR-002 | Demonstration | Push notification flow demo | ✅ Approved with feedback |
| SyR-NFR-P01 | Test | Load test with k6 (5000 concurrent) | ✅ p95 = 320ms |
| All | Inspection | Requirements review with compliance officer | ✅ No gaps found |

---

## Step 6: Baseline & Manage

**Baseline v1.0** established on 2025-02-01 after stakeholder sign-off.

### Example Change Request

```
CR-003: Add biometric authentication support
  Requestor: Product Manager
  Impact Analysis:
    - Scope: +2 new system requirements (SyR-007, SyR-008)
    - Cost: +3 story points
    - Schedule: No impact (fits within Sprint 5)
    - Risk: Medium — depends on device capability detection
    - Affected artifacts: StRS v1.1, SRS v1.1, RTM v1.1, Test Plan v1.1
  Decision: Approved by Product Owner (2025-02-15)
  Baseline updated: v1.1
```

---

## Step 7: Publish as Work Items

```
create epic "User Authentication MFA" --type epic --link BR-001
  create story "Login with TOTP" --type story --link SyR-001
  create story "Login with Push Notification" --type story --link SyR-002
  create story "Admin MFA Policy Management" --type story --link SyR-005,SyR-006
  create story "Legacy API Key Authentication" --type story --link SyR-004

plan --priority Must --sprint "Sprint 3" --owner "Auth Team"
run
```

---

## RTM Snapshot

| Req ID | Source | Business Req | Stakeholder Req | System Req | Test Case | Status |
|--------|--------|-------------|-----------------|-----------|-----------|--------|
| SyR-001 | CISO Interview | BR-001 | StR-001 | SyR-001 | TC-001, TC-002 | Verified |
| SyR-002 | CISO Interview | BR-001 | StR-001 | SyR-002 | TC-003 | Implemented |
| SyR-005 | Workshop | BR-001 | StR-002 | SyR-005 | TC-007 | Approved |
| SyR-NFR-P01 | SLA Agreement | BR-001 | StR-001 | SyR-NFR-P01 | TC-PERF-001 | Verified |
