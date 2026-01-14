# Domain Specification

> **Client:** [Client Name]
> **Brain:** [Brain Name]
> **Version:** [1.0]
> **Last Updated:** [Date]
> **Author:** [Your Name]

---

## Purpose

This document captures all domain knowledge required to build the Cortex (system prompt). Everything here will be encoded into the brain's intelligence layer.

---

## Terminology

### Core Terms

| Term | Client's Definition | Common Confusion | Example |
|------|---------------------|------------------|---------|
| | | | |

### Status Values

| Status | Meaning | When Used | Includes/Excludes |
|--------|---------|-----------|-------------------|
| | | | |

### Acronyms

| Acronym | Full Name | Context |
|---------|-----------|---------|
| | | |

---

## Business Rules

### [Domain Area 1]

#### Rule: [Rule Name]
- **Statement:** [Clear rule statement]
- **Why it exists:** [Business reason]
- **Example:** [Concrete example]
- **Anti-pattern:** [What NOT to do and why]

#### Rule: [Rule Name]
...

### [Domain Area 2]
...

---

## Data Semantics

### [Data Source / Table 1]

| Field | Type | Meaning | Valid Values | Gotchas |
|-------|------|---------|--------------|---------|
| | | | | |

#### Field Details

##### [Field Name]
- **What it represents:**
- **How it's populated:**
- **Common misinterpretation:**
- **Correct usage:**
- **Example values:**

### [Data Source / Table 2]
...

---

## Known Entities

### [Entity Type 1] (e.g., Locations, Statuses, Categories)

| ID/Code | Name | Notes |
|---------|------|-------|
| | | |

### [Entity Type 2]
...

---

## Edge Cases

### [Edge Case 1]
- **Scenario:** [When this happens]
- **Why it's tricky:** [What makes it confusing]
- **Correct handling:** [What to do]
- **Example:** [Concrete example]

### [Edge Case 2]
...

---

## Anti-Patterns

### [Anti-Pattern 1]
- **Wrong approach:** [What people mistakenly do]
- **Why it's wrong:** [What goes wrong]
- **Correct approach:** [What to do instead]
- **Detection:** [How to recognize this mistake]

### [Anti-Pattern 2]
...

---

## Calculations

### [Calculation 1]
- **Name:** [What it's called]
- **Formula:** [Exact calculation]
- **Inputs:** [What data is needed]
- **Gotchas:** [Common mistakes]
- **Example:**
  - Input: [values]
  - Output: [result]

### [Calculation 2]
...

---

## Query Templates

### [Common Query Type 1]
```sql
-- Description: [What this query does]
-- When to use: [Scenario]
-- Gotchas: [What to watch for]

[Actual query template]
```

### [Common Query Type 2]
...

---

## Relationships

### Entity Relationships
```
[Entity A] ---(relationship)---> [Entity B]
                                      |
                                      v
                               [Entity C]
```

### Data Flow
```
[Source] --> [Transformation] --> [Storage] --> [Query]
```

---

## Validation Rules

### [Validation 1]
- **What to validate:**
- **Valid condition:**
- **Invalid condition:**
- **Error message:**

---

## User Mental Models

### How [User Type 1] Thinks About This
[Describe their mental model - how they conceptualize the domain]

### Common User Misconceptions
| Misconception | Reality | How to Handle |
|---------------|---------|---------------|
| | | |

---

## Historical Context

### Why Things Are This Way
[Context that explains seemingly odd rules or structures]

### Past Decisions That Matter
| Decision | When | Why | Impact |
|----------|------|-----|--------|
| | | | |

---

## Open Questions

- [ ] [Question needing client clarification]
- [ ] [Ambiguity to resolve]

---

## Validation Log

| Section | Validated By | Date | Notes |
|---------|--------------|------|-------|
| Terminology | | | |
| Business Rules | | | |
| Data Semantics | | | |
| Edge Cases | | | |

---

## Change History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | | | Initial version |
