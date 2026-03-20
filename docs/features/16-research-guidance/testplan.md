# 🧪 Test Plan: Research Guidance

> **Feature**: `16` — Research Guidance
> **Tasks**: [`tasks.md`](tasks.md)
> **Date**: 2026-03-21

---

## Acceptance Criteria

- [ ] Both discussion templates (project + feature) have a "Research & Prior Art" section
- [ ] A new `research.md` template (#17) exists in mastery.md with structured sections
- [ ] `research.md` is listed as conditional (⚡) in all relevant tables
- [ ] Stage 1 (Discuss) has research guidance in the action table
- [ ] `mastery-compact.md` reflects the new document type consistently
- [ ] Quick Reference sections updated to include research.md
- [ ] No existing template numbering or section ordering is broken

---

## Test Cases

### TC-01: Project Discussion Template Research Section

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md Template #1 exists |
| **Steps** | 1. Open mastery.md → 2. Find Template #1 (Project Discussion) → 3. Verify `## Research & Prior Art` section exists before "Open Questions" |
| **Expected Result** | Section has structured sub-sections: Knowledge Gaps, Sources Consulted, Key Findings, Impact on Decisions |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-02: Feature Discussion Template Research Section

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md Template #4 exists |
| **Steps** | 1. Open mastery.md → 2. Find Template #4 (Discussion) → 3. Verify `## Research & Prior Art` section exists before "Open Questions" |
| **Expected Result** | Section has same structured sub-sections as TC-01 |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-03: Research Document Template Exists

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md has templates section |
| **Steps** | 1. Open mastery.md → 2. Find Template #17 (Research Document) → 3. Verify all sections present |
| **Expected Result** | Template includes: header, Overview, Knowledge Gaps, Research Topics (repeatable pattern), Summary & Recommendations |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-04: Document Ecosystem Tables Updated

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md Document Ecosystem section exists |
| **Steps** | 1. Check folder tree → 2. Check Document Roles table → 3. Check Required vs Optional table |
| **Expected Result** | `research.md` appears in all three with correct conditional status |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-05: Stage 1 Discuss Action Updated

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md Stage 1 action table exists |
| **Steps** | 1. Find Stage 1 Discuss action table → 2. Verify research action row exists |
| **Expected Result** | New row guiding teams to research when knowledge gaps exist |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-06: TOC Updated

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md TOC exists |
| **Steps** | 1. Find TOC → 2. Verify Research Doc template link exists |
| **Expected Result** | Link to `#17-research-document` present in TOC under Document Templates |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-07: Quick Reference Updated

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery.md Quick Reference section exists |
| **Steps** | 1. Check "Starting a New Feature" steps → 2. Check Document Quick Reference table |
| **Expected Result** | research.md mentioned as conditional step and in doc reference table |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-08: mastery-compact.md Consistency

| Property | Value |
|---|---|
| **Category** | Happy Path |
| **Precondition** | mastery-compact.md exists |
| **Steps** | 1. Check folder structure → 2. Check Document Roles table → 3. Check Required docs note → 4. Check Stage 1 description |
| **Expected Result** | All four locations mention research.md consistently |
| **Status** | ⬜ Not Run |
| **Notes** | — |

### TC-09: No Broken Template Numbering

| Property | Value |
|---|---|
| **Category** | Edge Case |
| **Precondition** | All templates exist |
| **Steps** | 1. Verify templates #1–#16 are unchanged → 2. Verify #17 is new → 3. Verify TOC links resolve |
| **Expected Result** | Existing template numbers unchanged, new #17 added at end |
| **Status** | ⬜ Not Run |
| **Notes** | — |

---

## Edge Cases

| # | Scenario | Expected Behavior |
|---|---|---|
| 1 | Feature needs no research | Discussion template section filled with "N/A — domain is well-understood" |
| 2 | Research findings are small | Stay in discussion.md section, no separate research.md needed |
| 3 | Research findings are extensive | Extract to separate research.md, link from discussion.md |
| 4 | Lightweight feature | No research.md — if research is needed, feature isn't lightweight |

## Security Tests

No security-sensitive behavior in this feature.

## Performance Considerations

No performance-critical paths in this feature.

---

## Test Summary

| Category | Total | Pass | Fail | Skip |
|---|---|---|---|---|
| Happy Path | 8 | — | — | — |
| Edge Cases | 4 | — | — | — |
| Security | 0 | — | — | — |
| **Total** | 12 | — | — | — |

**Result**: ⬜ NOT RUN
