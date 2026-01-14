# Reference Implementation: The Primula Brain

> This document analyzes the Primula Data Assistant as the reference implementation of the WADL Brain methodology. Use this to understand what a complete brain looks like in practice.

---

## Overview

**Client:** Primula / ALG Management (Childcare EMS company)
**Brain:** Primula Data Assistant
**Status:** Production ($3,000/month)
**Users:** School directors (non-technical)
**Purpose:** Natural language analytics for school operations data

---

## The Problem Solved

**Before the brain:**
- Directors had to log into Primula's web app
- Navigate multiple screens to find data
- Export to Excel, manually calculate
- Ask IT for custom reports (days of wait time)
- Simple questions took hours to answer

**After the brain:**
- Ask in plain English: "What's our occupancy rate this month?"
- Get instant answer with visualization
- Follow-up naturally: "What about compared to last month?"
- Self-service analytics without IT bottleneck

**ROI:** Directors answer their own questions in seconds instead of days. Estimated 60-120 hours/year saved per director.

---

## Phase Evidence Map

### Phase 1: Discovery
**Location:** `/Clients/Primula/Research/`

Evidence:
- `EMS_Deep_Dive.md` - 20+ page analysis of PEMS system
- `Current_Understanding.md` - Latest state summary
- `Questions_Archive.md` - Q&A history with client

**What was captured:**
- All data sources (PEMS modules, API endpoints)
- Pain points (manual reporting, IT bottleneck)
- Users (school directors, regional managers)
- Success criteria (self-service analytics)

---

### Phase 2: Domain Capture
**Location:** `/Clients/Primula/Knowledge-Base/` + System Prompt

Evidence:
- `01_PEMS_TECHNICAL_REFERENCE.md` - System documentation
- `03_BUSINESS_CONTEXT.md` - Stakeholders, pain points
- `06_LEADS_LIST_IMPLEMENTATION_SPEC.md` - Business rules with code examples
- The 32KB system prompt itself

**What was captured:**

#### Terminology
| Term | Definition |
|------|------------|
| Active student | Student with status = 'active' (excludes hold) |
| Total students | Active + hold students |
| Available space | Marketing intent (can accept enrollment) |
| Open space | Physical occupancy (seat is empty) |
| Enrolled capacity | Seats marked for enrollment |
| Licensed capacity | Maximum allowed by license |

#### Business Rules (Examples)
- "Payments have NEGATIVE amounts in database - must use ABS()"
- "Family balance requires deduplication by family_id first"
- "Never SUM rooms_raw.capacity - inflates by rooms × months"
- "Default to current calendar month when timeframe unspecified"

#### Known Entities
```
School IDs (hardcoded):
- Macland Pointe: [exact UUID]
- Castle Rock: [exact UUID]
- East Cobb at Sprayberry: [exact UUID]
- Lone Tree: [exact UUID]
- Manhattan at East 82nd Street: [exact UUID]
```

#### Edge Cases
- "stage_inquiry_call_completed is BOOLEAN but stage_tour_completed is TEXT"
- "Procare vs EMS dates can differ by 7+ days"
- "If student roster returns nothing, re-query leads_raw before saying no record"

---

### Phase 3: Architecture
**Location:** `/Clients/Primula/Knowledge-Base/01_PEMS_TECHNICAL_REFERENCE.md`

**Data Layer:**
```
Primula REST API
      ↓
ingest_sql.py (Python script)
      ↓
Parquet files (staged snapshots)
      ↓
DuckDB database + Views
```

- 13 DuckDB views created from Parquet files
- Daily refresh via systemd timer
- Hive partitioning for time-series data

**Domain Layer:**
- 32KB system prompt
- GPT-4 / GPT-4o with fallback
- LlamaIndex FunctionAgent
- Single tool: sql_query
- Max 4 function calls per request
- Temperature: 0 (deterministic)

**Interface Layer:**
- Flask frontend (proxy)
- Chat UI for natural language queries
- Server-sent events for streaming responses
- Chart.js for visualizations
- Session-based authentication

**Guardrails:**
- Read-only DuckDB connections
- SQL validation (whitelist SELECT/EXPLAIN, blacklist mutations)
- Bounded queries (requires school_id/room_id scope)
- Output limits (50 rows, 60 data points)
- Identifier stripping (no IDs in output)

---

### Phase 4: Build
**Location:** `/Clients/Primula/Primula-Pilot-main/`

**Key Files:**
| File | Purpose | Size/Complexity |
|------|---------|-----------------|
| `backend/app.py` | Core FastAPI app | 2,500+ lines |
| `backend/prompts/system_prompt_sql.md` | The Cortex | 32KB |
| `agent/sql_runtime.py` | Read-only SQL execution | Semantic guardrails |
| `scripts/ingest_sql.py` | Data ingestion | Primula API → Parquet |
| `db/init_views_duck.sql` | DuckDB view definitions | 13 views |
| `config/semantic_catalog.yaml` | Column access control | Tags + budget |
| `frontend/app.py` | Flask proxy | Streaming support |

**Deployment:**
- Ubuntu server
- Nginx reverse proxy
- Systemd services
- Blue-green deployment support
- Sentry monitoring

---

### Phase 5: Iterate
**Location:** `/Clients/Primula/Knowledge-Base/04_MEETING_HISTORY.md`

**Meeting Log:**
- Dec 18, 2025 - Initial requirements
- Dec 24, 2025 - MVP review
- Dec 28, 2025 - Bug fixes, edge cases
- Dec 29, 2025 (AM) - Analysis mode feature
- Dec 29, 2025 (PM) - Final refinements

**Iteration Examples:**
1. **Edge case discovered:** Family balance double-counting
   - **Fix:** Added deduplication CTE to prompt templates
   - **Added to Domain Spec:** Yes

2. **User feedback:** "Enrolled" vs "active" confusion
   - **Fix:** Added explicit terminology section
   - **Added to Domain Spec:** Yes

3. **Bug found:** stage fields have mixed types
   - **Fix:** Added type handling guidance to prompt
   - **Added to Domain Spec:** Yes

---

## Cortex Analysis

The Primula Cortex is a masterclass in domain encoding. Here's what makes it work:

### Structure (32KB)
```
1. Core Rule (repeated 4 times throughout)
2. Available Views (13 tables listed)
3. Schema Reference (inserted dynamically)
4. Exemplar Queries (5 copy-paste examples)
5. Non-Negotiables (execution rules, counting rules, isolation rules)
6. Safety Checklist (joins, aggregations, sources, visualization)
7. Schema-Specific Field Guidance (room transitions, dates, balances, billing, revenue)
8. Query Craft & Narration (formatting, DuckDB syntax, casting)
9. Known Schools (5 UUIDs hardcoded)
10. Response Format (JSON mandate)
```

### Key Techniques

**1. Repetition for Emphasis**
The core rule appears 4 times:
- Line 5: Initial statement
- Line 49: Execution rules section
- Line 52: Reinforcement
- Line 53: Another reinforcement

**2. Anti-Patterns with Explanations**
Not just "don't do X" but "don't do X because Y happens":
```
NEVER join to rooms_raw.capacity and sum it—this inflates by rooms × months
```

**3. Copy-Paste SQL Templates**
Full CTEs provided, not just concepts:
```sql
WITH family_dedup AS (
  SELECT DISTINCT family_id, ...
  FROM students_raw
  WHERE ...
)
SELECT ...
```

**4. Field-by-Field Semantics**
Every important field has:
- What it represents
- Common misinterpretation
- Correct usage
- Gotchas

**5. Known Entity Hardcoding**
School IDs listed directly - no resolution, no hallucination risk:
```
Macland Pointe: abc-123-def-456
Castle Rock: xyz-789-...
```

**6. Response Format Lock-In**
Exact JSON structure mandated:
```json
{
  "response": "...",
  "visualizations": [...]
}
```

---

## Metrics

**Prompt Size:** 32KB (~25,000 tokens)
**Query Success Rate:** High (specific % would need measurement)
**Average Response Time:** 2-5 seconds (depending on query complexity)
**User Satisfaction:** Client renewed at $3,000/month

---

## Lessons Learned

### What Worked
1. **Exhaustive domain capture** - Field-by-field definitions prevented hallucination
2. **Anti-patterns in prompt** - Explicitly stating what NOT to do was as valuable as stating what to do
3. **Copy-paste templates** - Reduced agent creativity in favor of correctness
4. **Hardcoded known entities** - Eliminated guessing
5. **Meeting-driven iteration** - Regular feedback loops caught issues early

### What Was Challenging
1. **Mixed data types** - Fields with inconsistent types (BOOLEAN vs TEXT) required explicit handling
2. **Multiple truth sources** - Different tables for current vs historical data needed priority rules
3. **Terminology confusion** - "Enrolled" vs "active" required very explicit definitions
4. **Dual date systems** - Procare vs EMS dates differing by days

### What We'd Do Differently
1. **Earlier user testing** - Some edge cases only found when real users asked real questions
2. **Regression test suite from start** - Would have caught regressions faster
3. **Version control for prompt** - Prompt changes should be tracked like code

---

## How to Use This Reference

When building a new brain:

1. **Review the Cortex structure** - Use similar organization
2. **Match the depth** - Aim for similar specificity (32KB is not unusual)
3. **Copy the techniques** - Repetition, anti-patterns, templates, hardcoding
4. **Expect iteration** - Even with great domain capture, real usage reveals gaps
5. **Document everything** - The Knowledge Base made iteration possible

---

## File Locations

| Artifact | Location |
|----------|----------|
| Knowledge Base | `/Clients/Primula/Knowledge-Base/` |
| System Prompt | `/Clients/Primula/Primula-Pilot-main/backend/prompts/system_prompt_sql.md` |
| Backend Code | `/Clients/Primula/Primula-Pilot-main/backend/` |
| Data Ingestion | `/Clients/Primula/Primula-Pilot-main/scripts/ingest_sql.py` |
| DuckDB Views | `/Clients/Primula/Primula-Pilot-main/db/init_views_duck.sql` |
| Meeting History | `/Clients/Primula/Knowledge-Base/04_MEETING_HISTORY.md` |
| Test Cases | `/Clients/Primula/Primula-Pilot-main/tests/test_cases/qa_unit_test.json` |
