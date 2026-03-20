# 💬 Discussion: Research Guidance

> **Feature**: `16` — Research Guidance
> **Status**: 🟢 COMPLETE
> **Branch**: `feature/16-research-guidance`
> **Depends On**: None
> **Date Started**: 2026-03-21
> **Date Completed**: 2026-03-21

---

## Summary

Add structured research guidance to the Mastery framework so that teams (human or AI) have a clear place and process for conducting research when they lack sufficient knowledge about a project or feature before designing/building it. This uses a hybrid approach: a lightweight research section in the Discussion template (always available) plus a conditional standalone `research.md` doc for deep research.

---

## Functional Requirements

- When starting a project or feature, the team should have a structured way to identify knowledge gaps and conduct research
- Research findings should be documented and traceable to the decisions they informed
- The solution should NOT add a new lifecycle stage — research happens within the existing Discussion stage
- Lightweight research (a few bullets of findings) should live inside `discussion.md` — no extra file needed
- Deep research (multiple topics, extensive findings) should have a dedicated `research.md` document
- AI agents should be guided on when and how to conduct research (web search, prior art, landscape analysis)

## Current State / Reference

### What Exists
- Discussion template has a single mention of "Reference existing code, legacy system, or prior art" in Stage 1 actions
- `docs/references/` directory supports external specs but has no research guidance
- This repo already has an informal `docs/research/` folder — proving the need exists organically
- No structured process for identifying knowledge gaps before designing

### What Works Well
- The Discussion stage is the natural home for research — it's where understanding is built
- The conditional document pattern (like `api.md`) already exists and is well-understood

### What Needs Improvement
- No guidance on WHEN to research (trigger/criteria)
- No structured format for documenting research findings
- No connection between research findings and design decisions
- AI agents have no rules about researching before designing unfamiliar features

## Proposed Approach

**Hybrid approach (Option C):**

1. **Add a "Research & Prior Art" section to the Discussion template** (both project-level and feature-level)
   - Always available as a section in `discussion.md` / `project-discussion.md`
   - Structured with: Knowledge Gaps Identified, Sources Consulted, Key Findings, Impact on Decisions
   - Lightweight — can be filled with a few bullets or left marked "N/A — domain is well-understood"

2. **Add `research.md` as a conditional feature document**
   - Created only when research is extensive enough to warrant its own document
   - Template with structured sections for multi-topic deep research
   - Listed as ⚡ Conditional in Document Ecosystem tables (like `api.md`)
   - Rule: "If research findings exceed a few paragraphs in discussion.md, extract to `research.md`"

3. **Add research trigger guidance to Stage 1 (Discuss)**
   - New action item: "If knowledge gaps exist, research before proceeding"
   - Guidance on what constitutes a knowledge gap worth researching
   - AI agent rule: "If unfamiliar with the domain, conduct research before designing"

4. **Update mastery-compact.md** to reflect the new conditional doc and guidance

## Dependencies

| Dependency | Type | Status |
|---|---|---|
| None | — | — |

## Open Questions

- [x] Should the research section go in project-discussion AND feature-discussion templates, or just feature? → **Both** — project research is just as important (tech stack decisions, architecture patterns)
- [x] Should `research.md` be its own separate template, or embedded in discussion? → **Separate template** — keeps discussion.md clean when research is extensive
- [x] Should there be a research section in the Lightweight Feature Variant? → **No** — if a feature needs research, it's not "well-understood scope" and doesn't qualify as lightweight

## Decisions Made

| Date | Decision | Rationale |
|---|---|---|
| 2026-03-21 | Hybrid approach (Option C) | Keeps framework lean for simple features while giving structured home for deep research |
| 2026-03-21 | Research lives within Discussion stage, no new lifecycle stage | Avoids adding a 7th stage; research naturally feeds into discussion |
| 2026-03-21 | Both project-level and feature-level discussion templates get research sections | Project decisions (tech stack, architecture) need research too |
| 2026-03-21 | `research.md` is conditional (like `api.md`) | Most features won't need a full research doc — only deep dives warrant it |
| 2026-03-21 | Lightweight features do NOT get research | If you need research, the feature isn't "well-understood" and shouldn't be lightweight |

## Discussion Complete ✅

**Summary**: Add structured research guidance via a hybrid approach — a "Research & Prior Art" section in both Discussion templates (always available, can be N/A) plus a conditional `research.md` template for deep research. Research is part of the Discussion stage, not a new stage. AI agents get guidance on when/how to research.
**Completed**: 2026-03-21
**Next**: Create architecture doc → `architecture.md`
