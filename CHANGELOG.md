# Changelog

All notable changes to the MASTERY.md framework will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

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
