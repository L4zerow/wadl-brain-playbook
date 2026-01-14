# Playbook Evolution

> This document tracks the state, gaps, and evolution of the WADL Playbook.
> Update this whenever the playbook changes.

---

## Current State

**Version:** 1.0
**Last Updated:** 2026-01-14
**Status:** Ready for use

**Completeness:**
- Core methodology: Complete
- Templates: Complete
- Checklists: Complete
- Reference implementations: 1 of 3 documented

---

## What Exists

### Core Documents

| File | Status | Notes |
|------|--------|-------|
| `README.md` | Complete | Index and quick start |
| `METHODOLOGY.md` | Complete | Philosophy, stack, phases, pricing |
| `EVOLUTION.md` | Complete | This file |

### Templates

| File | Status | Notes |
|------|--------|-------|
| `TEMPLATES/DISCOVERY.md` | Complete | Phase 1 artifact template |
| `TEMPLATES/DOMAIN_SPEC.md` | Complete | Phase 2 artifact template |
| `TEMPLATES/ARCHITECTURE.md` | Complete | Phase 3 artifact template |
| `TEMPLATES/CORTEX.md` | Complete | Phase 4 artifact template |
| `TEMPLATES/ITERATION_LOG.md` | Complete | Phase 5 artifact template |

### Checklists

| File | Status | Notes |
|------|--------|-------|
| `CHECKLISTS/PHASE_1_DISCOVERY.md` | Complete | Exit criteria for Phase 1 |
| `CHECKLISTS/PHASE_2_DOMAIN_CAPTURE.md` | Complete | Exit criteria for Phase 2 |
| `CHECKLISTS/PHASE_3_ARCHITECTURE.md` | Complete | Exit criteria for Phase 3 |
| `CHECKLISTS/PHASE_4_BUILD.md` | Complete | Exit criteria for Phase 4 |
| `CHECKLISTS/PHASE_5_ITERATE.md` | Complete | Exit criteria for Phase 5 |

### Reference Implementations

| File | Status | Notes |
|------|--------|-------|
| `REFERENCE/PRIMULA_ANALYSIS.md` | Complete | Childcare/EMS vertical |
| `REFERENCE/KANE_ANALYSIS.md` | Not started | Legal vertical (after Jan 17 call) |
| `REFERENCE/MERRAINE_ANALYSIS.md` | Not started | Recruiting vertical |

---

## What's Missing

### P0: Critical (Before Next Client)

*None - playbook is ready for Kane Law Firm engagement*

### P1: Important (After Kane / Before Scaling)

| Gap | Why It Matters | When to Address |
|-----|----------------|-----------------|
| **Second reference implementation** | Need n>1 to see patterns | After Kane engagement |
| **Sales/positioning document** | No external-facing materials | Before serious sales push |
| **Tool recommendations** | Tech decisions are implicit | Before second build |
| **Domain Spec → Cortex guidance** | Hardest transformation isn't guided | After more builds |

### P2: Nice to Have (For Team Scaling)

| Gap | Why It Matters | When to Address |
|-----|----------------|-----------------|
| **Team delegation guidance** | Can't hand off phases to others | When hiring/partnering |
| **Training materials** | Can't onboard new people | When hiring/partnering |
| **Vertical-specific patterns** | Childcare vs Legal vs Recruiting | After picking vertical |
| **Failure mode documentation** | What if discovery finds no opportunity? | After experiencing failures |
| **Client communication templates** | How to present findings, handle objections | When scaling sales |

### P3: Future (Platform/Productization)

| Gap | Why It Matters | When to Address |
|-----|----------------|-----------------|
| **Automated template generation** | Manual copy/paste doesn't scale | If building platform |
| **Brain quality assessment rubric** | No objective quality measure | If licensing methodology |
| **Case studies for marketing** | Need proof points for sales | When doing outbound |

---

## Reference Implementation Tracker

| Client | Vertical | Brain Status | Analysis Status | Notes |
|--------|----------|--------------|-----------------|-------|
| Primula | Childcare/EMS | Production ($3k/mo) | Complete | Reference implementation |
| Kane Law Firm | Legal/Eviction | Discovery (Jan 17 call) | Not started | Second reference |
| Merraine | Recruiting | Active development | Not started | Thin domain layer |
| lifeos | Personal/Accountability | Production | Not started | Personal project |

---

## Evolution Log

| Date | Change | Reason |
|------|--------|--------|
| 2026-01-14 | Initial playbook created | Extracted methodology from existing work (Primula, Merraine, Kane, lifeos). Created METHODOLOGY.md, 5 templates, 5 checklists, Primula reference analysis. |
| 2026-01-14 | Added EVOLUTION.md | Track playbook state and gaps over time |

---

## Next Priorities

### Immediate (This Week)

1. **Prepare for Kane call (Jan 17)**
   - Copy `TEMPLATES/DISCOVERY.md` to Kane folder
   - Review `CHECKLISTS/PHASE_1_DISCOVERY.md`
   - Review existing Kane research (Brainstorm folder)

### After Kane Call

2. **Document Kane as reference implementation**
   - Create `REFERENCE/KANE_ANALYSIS.md`
   - Compare patterns with Primula

3. **Decide vertical focus**
   - Childcare (Primula) vs Legal (Kane) vs Recruiting (Merraine)
   - Pick one to go deep

### Blocked By

| Priority | Blocked By |
|----------|------------|
| Kane reference implementation | Kane engagement completing |
| Vertical-specific patterns | Picking a vertical |
| Team delegation guidance | Decision to scale with people |

---

## How to Update This File

When the playbook changes:

1. **Add to Evolution Log** - Date, what changed, why
2. **Update What Exists** - Mark new files as Complete/Draft/Stub
3. **Update What's Missing** - Remove completed gaps, add new ones
4. **Update Reference Tracker** - As clients progress through phases
5. **Update Next Priorities** - Based on current focus

---

*Last reviewed: 2026-01-14*
