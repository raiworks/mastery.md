# 🏗️ Architecture: Research Guidance

> **Feature**: `16` — Research Guidance
> **Discussion**: [`discussion.md`](discussion.md)
> **Status**: 🟡 DRAFT
> **Date**: 2026-03-21

---

## Overview

This feature adds structured research guidance to the Mastery framework via two mechanisms: (A) a "Research & Prior Art" section embedded in both Discussion templates, and (B) a conditional standalone `research.md` template for deep research. It also updates the Stage 1 lifecycle actions, Document Ecosystem tables, Quick Reference, TOC, and `mastery-compact.md` to reflect the new document type.

## File Structure

```
(root)/
├── mastery.md              # MODIFY — 11 changes (details below)
└── mastery-compact.md      # MODIFY — 5 changes (details below)
```

No new files are created in the framework itself — the templates live inside `mastery.md`.

## Data Model

N/A — this feature does not introduce data models.

## Component Design

### Changes to `mastery.md`

**1. TOC — Add research.md template link**
- Location: Table of Contents, under Document Templates list
- Add: `- [Research Doc](#17-research-document)` after the Project Changelog entry

**2. Document Ecosystem — folder structure**
- Location: Document Ecosystem → folder tree
- Add: `│   │   ├── research.md              # (only when deep research is needed)` in the feature folder listing

**3. Document Ecosystem — Document Roles table**
- Location: Document Roles table
- Add row: `research.md | Feature | Structured research findings for unfamiliar domains | When knowledge gaps are significant`

**4. Document Ecosystem — Required vs Optional table**
- Location: "Which Docs Are Required vs Optional?" table
- Add row: `research | ⚡ Conditional | Feature domain is well-understood, no significant knowledge gaps`

**5. Stage 1 (Discuss) — action table**
- Location: Feature Lifecycle → Stage 1 — Discuss action table
- Add row after "Understand current state": `Research if needed | If knowledge gaps exist, conduct web search / landscape analysis before proceeding. Document findings in discussion.md or a separate research.md`

**6. Project Discussion Template (#1) — add Research section**
- Location: Template #1 (Project Discussion Document)
- Add a `## Research & Prior Art` section before "Open Questions"

**7. Feature Discussion Template (#4) — add Research section**
- Location: Template #4 (Discussion Document)
- Add a `## Research & Prior Art` section before "Open Questions"

**8. New Template #17 — Research Document**
- Location: After Template #16 (Project Changelog), before Git Branching Strategy
- Add full `research.md` template with: Overview, Knowledge Gaps, Research Topics (repeatable), Summary & Recommendations

**9. Quick Reference — Starting a New Feature**
- Location: Quick Reference → "Starting a New Feature" numbered list
- Add step for `research.md` (conditional) alongside `api.md`

**10. Naming Rules table — doc filenames**
- Location: Document Naming Convention → Naming Rules table → Doc filenames example
- Add `research.md` to the filenames list

**11. Version bump — footer**
- Location: Footer at end of mastery.md
- Bump `v3.3` → `v3.4`

### Changes to `mastery-compact.md`

**1. Document Ecosystem — folder structure**
- Add `research.md (if needed)` in the feature folder listing

**2. Document Roles table**
- Add row: `research.md | Structured research findings (conditional) | When significant knowledge gaps exist`

**3. Required docs note**
- Add `research.md` to the conditional docs list

**4. Stage 1 (Discuss) description**
- Add research guidance to the Discuss stage description

**5. Version bump — footer**
- Bump `v3.3 (Compact)` → `v3.4 (Compact)`

## Data Flow

```
Knowledge Gap Identified (Discussion stage)
    │
    ├── Small gap → Research section in discussion.md
    │                   (few bullets of findings)
    │
    └── Large gap → Dedicated research.md created
                        (multi-topic deep research)
                            │
                            └── Findings feed back into Discussion decisions
                                    │
                                    └── Discussion marked COMPLETE
                                            │
                                            └── Architecture informed by research
```

## Configuration

No configuration changes required.

## Security Considerations

No security implications for this feature.

## Trade-offs & Alternatives

| Approach | Pros | Cons | Verdict |
|---|---|---|---|
| **Option C — Hybrid** (chosen) | Lean for simple features; structured for deep research; no new lifecycle stage | Two places research can live (discussion section vs research.md) | ✅ Selected |
| New lifecycle stage (Stage 0: Research) | Clear, always visible | Adds weight; breaks 6-stage flow; overkill for most features | ❌ Too heavy |
| Research section in discussion only | Simplest; no new doc type | Insufficient for deep research; clutters discussion.md | ❌ Too limited |
| `research.md` only (no discussion section) | Clean separation | Forces a separate doc even for trivial research; higher friction | ❌ Too much friction |

## Next

Create tasks doc → `tasks.md`
