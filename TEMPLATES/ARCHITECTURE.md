# Architecture Document

> **Client:** [Client Name]
> **Brain:** [Brain Name]
> **Version:** [1.0]
> **Last Updated:** [Date]
> **Author:** [Your Name]

---

## Overview

### What We're Building
[One paragraph describing the brain and its purpose]

### Success Criteria
[Link to Discovery Doc success criteria]

---

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                     INTERFACE LAYER                         │
│  [Describe: Chat UI / Search / Dashboard / API / etc.]      │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                      DOMAIN LAYER                           │
│  [Describe: Cortex approach, guardrails, intelligence]      │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                       DATA LAYER                            │
│  [Describe: Sources, transformations, storage]              │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    CLIENT'S SYSTEMS                         │
│  [List: APIs, databases, files being connected]             │
└─────────────────────────────────────────────────────────────┘
```

---

## Data Layer Design

### Data Sources

| Source | Type | Connection Method | Refresh Frequency | Owner |
|--------|------|-------------------|-------------------|-------|
| | | | | |

### Data Flow

```
[Source A] ──┐
             ├──> [Transformation] ──> [Storage] ──> [Query Layer]
[Source B] ──┘
```

### Transformations Required

| Source | Transformation | Reason | Output |
|--------|----------------|--------|--------|
| | | | |

### Storage Design

**Primary Storage:** [DuckDB / PostgreSQL / etc.]
**Why:** [Rationale]

**Schema:**
```sql
-- Key tables/views
```

### Data Refresh Strategy

| Data Type | Refresh Method | Frequency | Latency Tolerance |
|-----------|----------------|-----------|-------------------|
| | | | |

---

## Domain Layer Design

### Cortex Approach

**Prompt Size Estimate:** [X KB]
**Structure:**
```
1. Core Rule
2. Available Resources
3. Schema Reference
4. Business Rules by Domain
5. Known Entities
6. Guardrails
7. Response Format
```

### Guardrails

| Guardrail | Implementation | Reason |
|-----------|----------------|--------|
| Read-only | [How] | Prevent data mutation |
| Bounded queries | [How] | Prevent runaway queries |
| Output limits | [How] | Prevent overwhelming responses |
| | | |

### LLM Selection

**Model:** [GPT-4 / Claude / etc.]
**Why:** [Rationale]
**Fallback:** [Backup model if primary fails]

### Memory Strategy

| Memory Type | Storage | Retention | Purpose |
|-------------|---------|-----------|---------|
| Session | | | |
| Long-term | | | |
| Corrections | | | |

---

## Interface Layer Design

### Interface Type
[Chat / Search / Dashboard / API / Multi-channel]

### User Experience Flow
```
1. User does [action]
2. System responds with [response]
3. User can then [next actions]
```

### Key Screens/Endpoints

| Screen/Endpoint | Purpose | Key Features |
|-----------------|---------|--------------|
| | | |

### Authentication
**Method:** [Session / Token / SSO / etc.]
**Implementation:** [Details]

### Access Control
| Role | Permissions | Notes |
|------|-------------|-------|
| | | |

---

## Tech Stack

### Backend
| Component | Technology | Rationale |
|-----------|------------|-----------|
| Runtime | | |
| Framework | | |
| Database | | |
| AI/LLM | | |

### Frontend
| Component | Technology | Rationale |
|-----------|------------|-----------|
| Framework | | |
| Styling | | |
| State | | |

### Infrastructure
| Component | Technology | Rationale |
|-----------|------------|-----------|
| Hosting | | |
| CI/CD | | |
| Monitoring | | |
| Logging | | |

---

## Integration Points

### External APIs
| API | Purpose | Auth Method | Rate Limits |
|-----|---------|-------------|-------------|
| | | | |

### Webhooks/Events
| Event | Trigger | Action |
|-------|---------|--------|
| | | |

---

## Security Considerations

### Data Security
- [ ] Data encrypted at rest
- [ ] Data encrypted in transit
- [ ] PII handling defined
- [ ] Access logging enabled

### API Security
- [ ] Authentication required
- [ ] Rate limiting implemented
- [ ] Input validation
- [ ] Output sanitization

### Operational Security
- [ ] Secrets management
- [ ] Audit logging
- [ ] Backup strategy
- [ ] Incident response plan

---

## Deployment Strategy

### Environments
| Environment | Purpose | URL | Notes |
|-------------|---------|-----|-------|
| Development | | | |
| Staging | | | |
| Production | | | |

### Deployment Process
```
1. [Step 1]
2. [Step 2]
3. [Step 3]
```

### Rollback Plan
[How to rollback if deployment fails]

---

## Monitoring & Observability

### Health Checks
| Check | Endpoint | Frequency | Alert Threshold |
|-------|----------|-----------|-----------------|
| | | | |

### Metrics to Track
| Metric | Source | Alert Condition |
|--------|--------|-----------------|
| Response time | | |
| Error rate | | |
| Query volume | | |
| | | |

### Logging Strategy
| Log Type | Retention | Purpose |
|----------|-----------|---------|
| | | |

---

## Risks & Mitigation

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| | High/Med/Low | High/Med/Low | |

---

## Open Decisions

| Decision | Options | Recommendation | Status |
|----------|---------|----------------|--------|
| | | | Pending/Decided |

---

## Dependencies

### External Dependencies
| Dependency | Type | Risk if Unavailable |
|------------|------|---------------------|
| | | |

### Internal Dependencies
| Dependency | Owner | Status |
|------------|-------|--------|
| | | |

---

## Timeline

| Phase | Deliverable | Estimate | Dependencies |
|-------|-------------|----------|--------------|
| Data Layer | | | |
| Domain Layer | | | |
| Interface Layer | | | |
| Testing | | | |
| Deployment | | | |

---

## Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Client | | | |
| Technical Lead | | | |
