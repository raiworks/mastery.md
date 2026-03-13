# Feature 12 — Framework Improvements (v3.1.0)

## Status: � COMPLETE

## Overview

A collection of improvements to the MASTERY.md framework itself. These are process and documentation enhancements — no code changes (mastery.md is the product).

---

## Item 1 — Strict Context Loading Enforcement

### Problem

The current AI Agent Protocol says agents "MUST read documents in this exact order" when starting a session. However, the **Resuming Work** section gives a different, abbreviated order that **skips mastery.md entirely**:

> 1. Read `project-context.md`
> 2. Read `project-roadmap.md`
> 3. Open that feature's `changelog.md`
> 4. ...

This creates ambiguity. In practice, AI agents often skip mastery.md on subsequent sessions because the Resuming Work protocol doesn't reference it. The result: agents forget the process rules, autonomy boundaries, and verification requirements.

### Current State

- **Context Loading Order**: Lists mastery.md as step 1 with "MUST" language
- **Resuming Work → For AI Agents**: Starts at project-context.md — no mention of mastery.md
- **AI Agent Quick Start**: Lists mastery.md as step 1, but it's a convenience guide, not enforceable
- **Net effect**: Agents load mastery.md on first session, then never again

### Proposed Change

Add explicit language making mastery.md loading **mandatory on every new context**, not just the first session. Two changes needed:

1. **Context Loading Order section** — Add a callout box:
   ```
   > ⚠️ **Every new context**: AI agents MUST re-read `docs/mastery.md` at the 
   > start of every new context window or session — not just the first one. 
   > The framework rules, autonomy boundaries, and verification requirements 
   > must be fresh in context before any work begins.
   ```

2. **Resuming Work → For AI Agents** — Prepend mastery.md as step 0 or 1:
   ```
   1. Read `docs/mastery.md` — reload the process framework (mandatory every session)
   2. Read `docs/project-context.md` — refresh on what this project is
   3. Read `docs/project-roadmap.md` — find the feature marked 🟡 IN PROGRESS
   ...
   ```

### Discussion Points

- **Should we distinguish "first session" vs "resuming"?** Or just make every session start the same way? A single mandatory sequence is simpler to follow and harder to get wrong.
- **Performance concern**: mastery.md is ~2000 lines. Should we add a note saying "scan for familiarity, read in full if needed" — or keep it strict "MUST read" every time?
- **AGENTS.md already points to mastery.md** — does that need updating too?

---

## Item 2 — Project-Level Changelog

### Problem

The framework defines per-feature `changelog.md` files that track what happens during each feature's build phase. But there is **no project-level changelog** — no single document that captures the high-level history of the project across all features.

Currently:
- Each feature has its own `changelog.md` (granular, implementation-focused)
- The `CHANGELOG.md` at project root is for the framework's version history (not for consuming projects)
- There is no template or guidance for projects using Mastery to maintain their own project changelog
- When someone asks "what changed in the last 3 months?", the answer is scattered across 10+ feature changelog files

### Current Document Ecosystem (relevant gap)

| Document | Scope | Purpose |
|---|---|---|
| Feature `changelog.md` | Feature | Running log of changes during implementation |
| `references/hotfix-log.md` | Project | Record of hotfixes applied |
| **Project changelog** | **Project** | **❌ Missing** |

### Proposed Change

Add a **project-level changelog** to the document ecosystem. This would be:

- **Filename**: `docs/project-changelog.md`
- **Purpose**: High-level record of all shipped features, hotfixes, and significant changes — the project's history at a glance
- **Format**: Based on [Keep a Changelog](https://keepachangelog.com/) with sections for Added, Changed, Fixed, Removed
- **When updated**: After each feature is merged to main (Ship stage) and after hotfixes
- **Scope**: Project-wide — one entry per feature/hotfix, not per-commit

Changes needed in mastery.md:
1. **Document Ecosystem** — Add `project-changelog.md` to the directory tree and Document Roles table
2. **Document Templates** — Add a template for the project changelog
3. **Feature Lifecycle → Ship stage** — Add "Update project-changelog.md" as a step
4. **Hotfix Workflow** — Add "Update project-changelog.md" as a step
5. **Quick Reference** — Add entry to the Document Quick Reference table
6. **Required vs Optional table** — Add entry (Required? Always)

### Proposed Template

```markdown
# 📋 Project Changelog

> **Project**: [Project Name]
> **Format**: Based on [Keep a Changelog](https://keepachangelog.com/)
> **Updated**: After each feature merge and hotfix

---

## [Unreleased]

### Added
### Changed
### Fixed
### Removed

---

## [Version] — YYYY-MM-DD

### Added
- **Feature #XX — Feature Name** — Brief description of what was added

### Changed
- **Feature #XX — Feature Name** — Brief description of what changed

### Fixed
- **Hotfix — Description** — What was fixed and why

### Removed
- **Feature #XX — Feature Name** — What was removed and why
```

### Discussion Points

- **Should it be required or optional?** Strong argument for required — every project benefits from a single changelog.
- **Should it replace Keep a Changelog at the root?** No — `CHANGELOG.md` at root is convention for the published artifact. `docs/project-changelog.md` is the Mastery-managed development history. Projects may choose to sync them.
- **Granularity**: One entry per feature merge? Per version? Per sprint? Recommendation: per feature merge, grouped by version when applicable.
- **Who writes it?** AI agents should update it autonomously during the Ship stage (add to autonomy boundaries).
- **Relationship to feature changelogs**: Feature changelogs are granular (session notes, task progress). Project changelog is high-level ("Feature X shipped — adds Y capability").

---

## Item 3+ — Additional Improvements (To Be Discussed)

*Space reserved for additional improvements the user wants to discuss.*

Potential areas to explore:
- Version bump strategy (when does v3.0.0 → v3.1.0?)
- Any other gaps noticed while using the framework
- Template improvements based on real-world usage

---

## Decisions

| # | Decision | Rationale |
|---|---|---|
| 1 | Make mastery.md loading mandatory on every new context | Agents lose process rules after first session; the Resuming Work section currently skips mastery.md entirely |
| 2 | Unify the Resuming Work sequence with Context Loading Order — prepend mastery.md as step 1 | One consistent path is simpler than two divergent sequences |
| 3 | Keep it strict "MUST read" — no "scan for familiarity" hedge | The framework is ~2000 lines but agents benefit from having it fully in context; weakening the language invites shortcuts |
| 4 | Add project-changelog.md as a required document | Every project benefits from a single high-level history; scattered feature changelogs don't give the big picture |
| 5 | AI agents autonomously update project changelog during Ship stage | This is a natural extension of what agents already do (update feature changelogs, check off tasks) |
| 6 | One entry per feature merge, grouped by version when applicable | Right granularity — not per-commit (too detailed) and not per-sprint (too vague) |
| 7 | Version bump to v3.1.0 | Item 2 adds a new required document type + template — that's a minor version bump, not a patch |
| 8 | No separate project architecture doc | Tech stack and architecture overview already live in project-context.md; feature details go in per-feature architecture.md |

## Open Questions

*All resolved — discussion complete.*

## Discussion Complete ✅

**Summary**: Two improvements to the mastery.md framework: (1) enforce mandatory mastery.md loading on every new AI agent context/session, not just the first one, and (2) add a project-level changelog document to the ecosystem with template, lifecycle integration, and autonomy rules. Version bump to v3.1.0.
**Completed**: 2026-03-13
**Next Steps**:
1. Create tasks for all mastery.md edits
2. Build the changes
3. Update CHANGELOG.md and roadmap
