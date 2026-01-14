# The WADL Brain Methodology

## What This Is

WADL builds **intelligent systems that capture organizational knowledge and make it operational**.

We take:
- Tribal knowledge trapped in people's heads
- Business rules nobody wrote down
- Data scattered across systems
- Non-technical users waiting on IT for answers

And turn it into:
- Explicit rules encoded in system prompts
- Connected, queryable data layers
- Natural language interfaces anyone can use
- Systems that improve over time

**We're not in the AI chatbot business. We're in the organizational intelligence capture and operationalization business.**

---

## Core Philosophy

These principles govern how we build:

| Principle | What It Means |
|-----------|---------------|
| **System > Intelligence** | Scaffolding matters more than model smarts. A well-designed system with a mediocre model beats a bad system with the best model. |
| **Context is the Moat** | The value is in deep context capture, not AI cleverness. Spend 90% of effort on context, 10% on AI. |
| **Explicit > Implicit** | Don't hope the AI figures it out. Write down exactly what to do AND what not to do. Anti-patterns are as important as patterns. |
| **Structure Forces Change** | For users with the knowing-doing gap, structure matters more than insight. Build systems that force action, not systems that explain things. |
| **Code Before Prompts** | Anything you CAN do in code, DO in code. 80% deterministic logic, 20% AI. Saves tokens, ensures consistency. |
| **Action > Analysis** | Systems should DO things, not just explain things. Bias toward outputs over insights. |
| **Simplicity Saves** | Complexity is the enemy. No features for features' sake. The right amount of complexity is the minimum needed. |
| **Proactivity > Reactivity** | The best systems initiate, not just respond. Don't wait for users to ask. |
| **Corrections are Truth** | When users correct the system, that becomes highest-priority truth. Never argue with corrections. |
| **Memory Must Compress** | Don't store everything. Consolidate to patterns. Daily becomes weekly becomes monthly. |

---

## The Brain Stack

Every WADL Brain has three layers. Same structure, different content per client.

```
┌─────────────────────────────────────────────────────────────┐
│                     INTERFACE LAYER                         │
│                                                             │
│  How users interact with the brain.                         │
│  Examples: Chat UI, Search UI, Dashboard, API, Telegram     │
│                                                             │
│  Design principle: Remove friction. Non-technical users     │
│  should be able to get value without training.              │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                      DOMAIN LAYER                           │
│                                                             │
│  The intelligence. Also called "The Cortex."                │
│  Contains:                                                  │
│  • System prompt with all business rules                    │
│  • Field-by-field definitions and semantics                 │
│  • Anti-patterns (what NOT to do)                           │
│  • Copy-paste templates for common operations               │
│  • Known entities (IDs, codes, mappings)                    │
│  • Guardrails (read-only, bounded queries, limits)          │
│                                                             │
│  Design principle: Explicit over implicit. If you can       │
│  write it down, write it down. Don't hope the AI knows.     │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                       DATA LAYER                            │
│                                                             │
│  Connections to client's systems. Also called "Synapses."   │
│  Contains:                                                  │
│  • API integrations to source systems                       │
│  • Data transformations (raw → queryable)                   │
│  • Storage (databases, file stores)                         │
│  • Refresh/sync mechanisms                                  │
│                                                             │
│  Design principle: Single source of truth. Data comes       │
│  from authoritative sources, not copies or exports.         │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    CLIENT'S SYSTEMS                         │
│                                                             │
│  The existing world. APIs, databases, files, spreadsheets.  │
│  We connect to these. We don't replace them.                │
└─────────────────────────────────────────────────────────────┘
```

---

## Unified Terminology

Use these terms consistently across all projects:

| Term | Definition | Example |
|------|------------|---------|
| **Brain** | The complete intelligent system we deliver | "The Primula Brain" |
| **Cortex** | The system prompt that IS the intelligence. Contains all business rules, definitions, anti-patterns. | The 32KB prompt in Primula |
| **Synapses** | Data connections to client systems | Primula API integration |
| **Interface** | How users interact with the brain | Chat UI, search, dashboard |
| **Domain Spec** | Document capturing all business rules before encoding into Cortex | Field definitions, edge cases |
| **Guardrails** | Safety mechanisms preventing bad outputs | Read-only queries, bounded filters |
| **Discovery Doc** | Output of Phase 1 - understanding client's world | Kane Law Firm Brainstorm |
| **Iteration Log** | Ongoing record of changes, decisions, refinements | Meeting history, bug fixes |

---

## The Five Phases

Every engagement follows these phases. Same names. Same artifacts. Same thinking.

### Phase 1: Discovery

**Question:** What's the client's world?

**Activities:**
- Map existing data sources (what systems do they have?)
- Identify pain points (what's broken? what's slow?)
- Profile users (who needs the brain? technical level?)
- Define success (what does "working" look like? ROI?)
- Assess AI opportunity tiers (quick wins vs. big builds)

**Artifact:** `DISCOVERY.md`

**Phase is complete when:**
- [ ] All data sources identified and access confirmed
- [ ] Pain points documented with severity/frequency
- [ ] User profiles defined (who, technical level, needs)
- [ ] Success criteria agreed with client
- [ ] AI opportunity tiers mapped (1-5 scale)
- [ ] Recommendation for which tier to pursue

---

### Phase 2: Domain Capture

**Question:** What does the brain need to know?

**Activities:**
- Extract business rules (how do THEY think about their domain?)
- Map terminology (what does "enrolled" mean HERE?)
- Document edge cases (what breaks? what's weird?)
- Identify known entities (IDs, codes, status values)
- Capture anti-patterns (common mistakes to avoid)
- Define field-by-field semantics (what each data point means)

**Artifact:** `DOMAIN_SPEC.md`

**Phase is complete when:**
- [ ] All key terms defined in client's language
- [ ] Business rules documented with examples
- [ ] Edge cases listed with how to handle each
- [ ] Known entities catalogued (IDs, codes, mappings)
- [ ] Anti-patterns documented ("never do X because Y")
- [ ] Field definitions complete for all data sources
- [ ] Client has reviewed and validated accuracy

---

### Phase 3: Architecture

**Question:** How will the brain work?

**Activities:**
- Design Data Layer (what sources, what transformations, what storage)
- Design Domain Layer (prompt structure, guardrail approach)
- Design Interface Layer (chat? search? dashboard? API?)
- Define integration points (auth, deployment, monitoring)
- Plan technical stack (languages, frameworks, services)
- Identify risks and mitigation

**Artifact:** `ARCHITECTURE.md`

**Phase is complete when:**
- [ ] Data Layer design documented (sources, transforms, storage)
- [ ] Domain Layer approach defined (prompt structure, guardrails)
- [ ] Interface Layer designed (UI, UX, access patterns)
- [ ] Tech stack selected with rationale
- [ ] Integration points mapped (auth, deploy, monitor)
- [ ] Risks identified with mitigation plans
- [ ] Client has approved architecture

---

### Phase 4: Build

**Question:** Make it real.

**Activities:**
- Implement Data Layer (ingestion, transformation, storage)
- Write the Cortex (system prompt with full domain knowledge)
- Build Interface Layer (UI, API, access controls)
- Add Guardrails (safety, validation, limits)
- Test with real queries and real users
- Deploy to production environment

**Artifact:** Working Brain + `CORTEX.md` (the actual system prompt)

**Phase is complete when:**
- [ ] Data Layer ingesting and transforming correctly
- [ ] Cortex written with all domain rules encoded
- [ ] Interface functional and tested
- [ ] Guardrails preventing bad outputs
- [ ] Real users have tested with real questions
- [ ] Deployed to production
- [ ] Monitoring and logging operational

---

### Phase 5: Iterate

**Question:** What's still wrong?

**Activities:**
- Gather user feedback (what's confusing? what's wrong?)
- Refine Cortex (add rules for discovered edge cases)
- Expand capabilities (new data sources, new features)
- Fix bugs and improve performance
- Document learnings (update Domain Spec)
- Track decisions chronologically

**Artifact:** `ITERATION_LOG.md`

**Phase is ongoing. Checklist per iteration:**
- [ ] User feedback collected
- [ ] Issues triaged by severity
- [ ] Cortex updated for new edge cases
- [ ] Domain Spec updated with learnings
- [ ] Changes tested before deploy
- [ ] Iteration documented in log

---

## The Cortex: How to Write It

The Cortex (system prompt) is the heart of the brain. Here's the structure:

```markdown
# [Client] Brain - System Prompt

## Core Rule
State the single most important rule. Repeat it throughout the prompt.
Example: "MUST execute sql_query tool for EVERY quantitative question"

## Available Resources
List what the brain has access to (tables, APIs, tools).

## Schema Reference
[Insert actual schema with field definitions]

## Business Rules

### [Domain Area 1]
- Rule with explanation
- Anti-pattern: "NEVER do X because Y"
- Template: [Copy-paste example]

### [Domain Area 2]
...

## Known Entities
Hardcode IDs, codes, mappings that should never be guessed.

## Guardrails
- Safety constraints (read-only, bounded queries)
- Output limits (max rows, max data points)
- Forbidden operations

## Response Format
Lock in the exact output structure expected.
```

**Key principles for Cortex writing:**
1. **Repeat critical rules** - Important things appear multiple times
2. **Show anti-patterns** - What NOT to do is as important as what to do
3. **Provide templates** - Copy-paste examples for common operations
4. **Hardcode known entities** - Don't let AI guess IDs or codes
5. **Be exhaustively specific** - Field-by-field definitions, not summaries

---

## Reference Implementation: Primula

The Primula Brain is the reference implementation for this methodology.

**Phase 1 Evidence:** `/Clients/Primula/Research/` - EMS deep dive, questions archive
**Phase 2 Evidence:** 32KB system prompt with field-by-field definitions
**Phase 3 Evidence:** `/Clients/Primula/Knowledge-Base/01_PEMS_TECHNICAL_REFERENCE.md`
**Phase 4 Evidence:** `/Clients/Primula/Primula-Pilot-main/` - full working system
**Phase 5 Evidence:** `/Clients/Primula/Knowledge-Base/04_MEETING_HISTORY.md` - 5 meetings of iteration

See `REFERENCE/PRIMULA_ANALYSIS.md` for detailed breakdown.

---

## Pricing Model

Pricing tied to phases, not hours:

| Phase | Deliverable | Typical Range |
|-------|-------------|---------------|
| Discovery | Discovery Doc + Recommendation | $2,000 - $5,000 |
| Domain Capture | Domain Spec | $3,000 - $8,000 |
| Architecture | Architecture Doc | $2,000 - $5,000 |
| Build | Working Brain | $15,000 - $50,000 |
| Iterate | Ongoing Refinement | $2,000 - $5,000/month |

**Full engagement (Phases 1-4):** $25,000 - $75,000
**Ongoing (Phase 5):** $2,000 - $5,000/month

Adjust based on:
- Data complexity (how many sources, how messy)
- Domain complexity (how many rules, how many edge cases)
- Interface complexity (chat vs. dashboard vs. multi-channel)
- User volume (single user vs. organization-wide)

---

## What Makes This Different

| Generic AI Agency | WADL Brain |
|-------------------|--------------|
| "We'll build you an AI chatbot" | "We'll capture your organizational intelligence" |
| 500-word system prompt | 10,000-30,000 word Cortex |
| Hope AI figures it out | Explicit rules, anti-patterns, templates |
| One-size-fits-all | State-aware, context-adaptive |
| Reactive to user requests | Proactive where appropriate |
| Store all data | Compress to patterns |
| Feature-heavy | Minimum viable complexity |

---

## Next Steps for WADL

1. **Validate this methodology** against Kane Law Firm engagement (upcoming)
2. **Create templates** for each artifact (Discovery, Domain Spec, Architecture, Cortex, Iteration Log)
3. **Package Primula** as the reference implementation others can learn from
4. **Decide vertical focus** - Childcare (Primula), Legal (Kane), or Recruiting (Merraine)
5. **Build second brain in chosen vertical** to prove repeatability
