# Changelog

All notable changes to the MASTERY.md framework will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

---

## [3.5.0] — 2026-04-01

### Added

- **Architecture amendment flexibility** — minor amendments (renamed fields, adjusted signatures) can now be logged in the changelog and applied autonomously. Structural changes still require human approval. Autonomy Boundaries table split into two rows: "Amend architecture (minor)" and "Modify architecture (structural)".
- **Security checkpoint at Ship stage** — new "Security review" row in Stage 5 action table. Covers auth gaps, input validation, hardcoded secrets, PII exposure, injection risks.
- **Compact fallback instruction** — new 🔄 Fallback note in Context Loading Order. If `mastery-compact.md` doesn't exist, agents fall back to reading `mastery.md` directly instead of failing.
- **Rollback & Recovery subsection** — new section after Hotfix Rules covering when to revert vs hotfix, rollback procedure, and post-rollback steps.
- **Reflect-to-Discuss feedback loop** — Stage 6 now includes "Capture lessons for next feature" action. Discussion template (#4) gains "Lessons from Previous Features" section. Review template (#10) gains "Key Lessons to Carry Forward" section.

### Changed

- **Cross-check trigger wording** — "Every ~5 build tasks completed" changed to "Every ~5 build tasks, or after any high-complexity/high-risk task" for complexity-aware triggering.
- **mastery-compact.md** — synced with all applicable changes (architecture flexibility, security checkpoint, compact fallback, cross-check wording, reflect loop).
- **Version bumped** to v3.5.

---

## [3.4.0] — 2026-03-21

### Added

- **Research guidance (hybrid approach)** — structured research support for projects and features where domain knowledge is insufficient
  - **"Research & Prior Art" section** added to both Project Discussion (Template #1) and Feature Discussion (Template #4) templates — always available, can be marked N/A when domain is well-understood
  - **`research.md` document type** — new conditional feature document (Template #17) for deep multi-topic research, created only when findings would overwhelm the discussion doc
  - **Stage 1 (Discuss) action** — new "Research if needed" row guiding teams to investigate knowledge gaps before proceeding
  - **Document Ecosystem updates** — `research.md` added to folder tree, Document Roles table, Required vs Optional table (⚡ Conditional)
  - **Quick Reference updates** — new step in "Starting a New Feature" list, new entry in Document Quick Reference table
  - **Naming Rules update** — `research.md` added to doc filenames list
  - **`mastery-compact.md` updates** — folder structure, Document Roles table, required docs note, and Stage 1 description all updated
- **Ship stage release & README rules** — Stage 5 (Ship) now includes mandatory steps for updating README/public docs and creating versioned releases. Added to Ship action table, Definition of Done, Tasks template Ship checklist, Quick Reference, and mastery-compact.md.

---

## [3.3.0] — 2026-03-16

### Added

- **Optional TC naming convention** in testplan template (Template #7) — Go (`TestTC01_*`), Python (`test_tc01_*`), JS (`it("TC-01: ...")`) patterns for automated traceability between test cases and test code
- **Test Function field** — optional column in TC table to link each test case to its implementation
- **Agent-asks-about-testing** guidance in Build stage — agents ask developers about test runner, naming conventions, and coverage expectations before writing tests
- **Testing awareness** in AI Communication Style — agents ask about test auditing when testplan.md exists (both full and compact variants)

### Philosophy

- Testing conventions are optional and developer-driven. Mastery provides the patterns; developers decide when to use them. Research concluded a standalone test engine is unnecessary (see `docs/research/test-engine.md`).

---

## [3.2.0] — 2026-03-14

### Added

- **`mastery-compact.md` — compact variant** (~5k tokens vs ~25k) — AI-optimized version containing all rules, no templates. 80% token reduction for agents that don't need templates every session.
  - 12 always-needed sections preserved in full (Philosophy, AI Agent Protocol, Feature Lifecycle, etc.)
  - All 16 templates omitted (load from full file on demand)
  - 6 rarely-needed reference sections omitted (Parallel Features, References Directory, etc.)
- **Two-variant loading strategy** in Context Loading Order — agents load compact by default, full file only when templates are needed
- **Document Ecosystem updates** — both files listed in directory tree, Document Roles table, Required vs Optional table
- **AGENTS.md updates** — project structure and loading order reference compact variant
- **README.md updates** — two-variants table, updated Quick Start and Adopting instructions

### Changed

- Resuming Work section now references compact variant
- AI Agent Quick Start updated for compact-first loading
- Project Init and Mid-Project Adoption skeletons include `mastery-compact.md`
- Quick Reference section updated with compact variant mention

---

## [3.1.0] — 2026-03-13

### Added

- **Strict context loading enforcement** — AI agents now MUST re-read `mastery.md` at the start of every new context/session, not just the first one. Added callout box in Context Loading Order section and prepended mastery.md to the Resuming Work → For AI Agents sequence. (#12)
- **Project-level changelog** (`project-changelog.md`) — new required document for tracking shipped features and hotfixes at the project level. Added to Document Ecosystem, Document Roles, Required vs Optional tables. (#12)
- **Template #16 — Project Changelog Document** — Keep a Changelog format for project-wide history
- **Ship stage update** — "Update project-changelog.md" added as a step after merging to main
- **Hotfix workflow update** — project changelog update added to the Document step
- **Autonomy boundary** — AI agents can autonomously update the project changelog
- **Definition of Done update** — project changelog entry added to Documentation Level checklist
- **Project Initialization update** — Step 4.5 added for creating project-changelog.md

### Changed

- **Resuming Work → For AI Agents** — now starts with mastery.md as step 1 (was previously skipped)
- **AI Agent Quick Start** — reinforced "mandatory every session" for mastery.md
- Version footer: v3.0 → v3.1

---

## [3.0.1] — 2026-03-13

### Added

- **Mid-project adoption guide** — new section with 8-step workflow for adopting Mastery into existing projects (#11)
- **Template #15 (Summary Document)** — retroactive feature summary for cataloging past work during mid-project adoption
- **`_archive/` folder** convention for preserving pre-Mastery documentation
- **Mid-Project Adoption checklist** in Quick Reference section
- Updated Document Ecosystem: directory tree, Document Roles table, Required vs Optional table

---

## [3.0.0] — 2026-03-12

### Changed

- **Restructured section order for progressive disclosure** — most critical information (Philosophy, AI Agent Protocol) at top, operational content (Workflow, Templates) in middle, reference material (Git, Definitions) at bottom
- Moved Document Naming Convention before Document Templates (understand naming before reading templates)
- Moved Git Branching Strategy and Commit Message Convention up, directly after Templates (operational — needed when doing work)
- Moved Parallel Features down (edge case, not core flow)
- Moved References Directory down (lookup material)
- Updated Table of Contents to match new section order
- Version bump in footer: v2.0 → v3.0

### Unchanged

- All 16 sections preserved — no content added or removed
- All 10 document templates intact
- AI Agent Protocol content unchanged
- Total: 86 lines moved, 0 lines added or deleted

---

## [2.0.0] — 2026-03-12

### About

Initial public release of the MASTERY.md framework. This version represents the framework as it existed before the v3.0.0 improvement effort began.

### Included

- Complete 7-stage development lifecycle (Discuss → Design → Plan → Approve → Build → Ship → Reflect)
- AI Agent Protocol with autonomy boundaries and context loading rules
- 10+ document templates (project discussion, context, roadmap, feature spec, design doc, task list, etc.)
- Git branching strategy and commit message conventions
- Session handoff and continuity protocols
- Process override mechanism (`process-overrides.md`)

---
