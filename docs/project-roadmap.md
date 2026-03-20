# 🗺️ Project Roadmap

> **Project**: MASTERY.md — Universal AI Development Process Framework
> **Current Milestone**: v3.4.0
> **Last Updated**: 2026-03-21

---

## Progress Overview

| Metric | Count |
|---|---|
| Total Features | 16 |
| ✅ Complete & Merged | 13 |
| 🟡 In Progress | 2 |
| 🔴 Not Started | 1 |
| ⏸️ On Hold | 0 |

**Overall Progress**: ████████░░ 80%

---

## Feature List

| # | Feature | Status | Depends On | Branch | Notes |
|---|---|---|---|---|---|
| 01 | Repo infrastructure (README, LICENSE, CHANGELOG) | ✅ Complete | — | `main` | README, LICENSE (MIT), CHANGELOG committed to main |
| 02 | AGENTS.md for this repo | ✅ Complete | #01 | `main` | 83-line orientation doc, merged to main |
| 03 | Progressive disclosure | ✅ Complete | — | `main` | Section reorder for progressive disclosure, v2.0→v3.0, merged to main |
| 04 | AI Agent Protocol improvements | ✅ Complete | — | `main` | Verification cross-checks + MCP-enhanced workflow, merged to main |
| 05 | Lightweight feature variant | ✅ Complete | #04 | `main` | Single-doc lifecycle for docs-only / config-only / trivial changes |
| 06 | Framework verbosity reduction | ✅ Complete | #03, #04, #05 | `main` | Cross-check audit: fixed duplicate emoji, added lightweight.md to tables, completed TOC sub-sections, added lightweight quick ref note |
| 07 | AGENTS.md generation guidance | ✅ Complete | #02 | `main` | Template #12, Step 3.5 in init, document ecosystem entries |
| 08 | SKILL.md + llms.txt | ✅ Complete | #03 | `main` | Templates #13 (SKILL.md) and #14 (llms.txt), document ecosystem entries |
| 09 | Cross-tool config generation guidance | ✅ Complete | #07 | `main` | Cross-Tool Configuration section with source mapping table, derivation principles, MCP alternative note |
| 10 | Feedback web application | 🔴 Not Started | #01 | — | Community feedback, issue reporting, improvement requests (deferred to v3.1.0) |
| 11 | Mid-project adoption guide | ✅ Complete | — | `main` | 8-step adoption workflow, _archive/ folder, summary.md template (#15), Quick Reference checklist |
| 12 | Framework improvements (v3.1) | ✅ Complete | — | `feature/12-framework-improvements` | Strict context loading + project-changelog.md document type + Template #16 |
| 13 | Context optimization | ✅ Complete | #12 | `feature/13-context-optimization` | mastery-compact.md (AI-optimized, ~5k tokens vs ~25k) + mastery.md updates |
| 14 | Test engine (optional testing conventions) | 🟡 In Progress | #13 | `feature/14-test-engine` | Optional TC naming convention, agent-asks-about-testing, no standalone tooling |
| 15 | gstack Mastery skill (distribution) | 🟡 In Progress | #08, #13 | `gstack-fork:mastery-status` | /mastery-status skill for garrytan/gstack — PR #112 submitted |
| 16 | Research guidance | ✅ Complete | — | `feature/16-research-guidance` | Hybrid approach: research section in discussion templates + conditional research.md, v3.4.0 |

---

## Dependency Map

```
01 [Repo Infrastructure]
 ├── 02 [AGENTS.md] ──── 07 [AGENTS.md Generation] ──── 09 [Cross-tool Config]
 └── 10 [Feedback Web App]

03 [Progressive Disclosure]
 ├── 06 [Verbosity Reduction] (also needs #04, #05)
 └── 08 [SKILL.md + llms.txt]

04 [Agent Protocol Improvements]
 ├── 05 [Lightweight Feature Variant]
 └── 06 [Verbosity Reduction] (also needs #03, #05)

11 [Mid-Project Adoption] (standalone — no dependencies)
12 [Framework Improvements v3.1] (standalone — no dependencies)
```

---

## Milestones

### v3.0.0 — Industry Standard Release

**Target**: When features 01–09 complete
**Features Included**: #01, #02, #03, #04, #05, #06, #07, #08, #09, #11

| Criterion | Status |
|---|---|
| All included features coded and merged | ✅ 10/10 merged (#01–#09, #11) |
| Framework version bumped to 3.0.0 | ✅ Done (bumped during Feature #03) |
| README complete and repo public-ready | ✅ Done (Feature #01) |
| CHANGELOG documents all changes from v2.0–v3.0 | ✅ Done (entries for v2.0.0 and v3.0.0 exist) |
| Progressive disclosure via section ordering | ✅ Done (Feature #03 — reordered sections for progressive flow) |

### v3.1.0 — Community & Ecosystem

**Target**: After v3.0.0 stable
**Features Included**: #10, #12

| Criterion | Status |
|---|---|
| Feedback web app deployed | ⬜ |
| Community contribution flow documented | ⬜ |
| Strict context loading enforcement | ✅ Done (Feature #12) |
| Project changelog document type added | ✅ Done (Feature #12) |

---

## Backlog

| Feature Idea | Priority | Notes |
|---|---|---|
| Contributing guide (CONTRIBUTING.md) | Medium | How others propose changes |
| Examples / case studies | Medium | Real-world usage patterns |
| Stage transition hooks | Low | Automated checks at lifecycle transitions |
| Multi-agent workflow guidance | Low | How Mastery handles multiple AI agents on same project |
| Cross-tool CLI (generate configs) | Low | Deferred to v4.0 — CLI that generates .cursorrules etc. from Mastery docs |
| Mastery MCP Server | Medium | In-scope for ecosystem, separate Go repo. Spec: `docs/references/mastery-mcp-server.md` |
| Documentation website (GitHub Pages) | Low | Full docs site — not needed until adoption grows |

---

## Brainstorm → Feature Mapping

How the 21 brainstorm items from `project-discussion.md` map to roadmap features and backlog:

| Brainstorm Item | Mapped To |
|---|---|
| README, LICENSE, CHANGELOG, .gitignore | Feature #01 (Complete) |
| AI Agent Protocol improvements | Feature #04 |
| Progressive disclosure | Feature #03 |
| AGENTS.md for this repo | Feature #02 |
| AGENTS.md generation guidance | Feature #07 |
| Lightweight feature variant | Feature #05 |
| Process-overrides improvements | Absorbed into Feature #04 + #05 |
| SKILL.md packaging | Feature #08 |
| llms.txt | Feature #08 |
| Feedback web application | Feature #10 |
| Cross-tool config generation | Feature #09 |
| Reduce framework verbosity | Feature #06 |
| "Getting Started" quick guide | Absorbed into Feature #03 (progressive disclosure) |
| Versioning strategy docs | Absorbed into Feature #01 (CHANGELOG) |
| Contributing guide | Backlog — CONTRIBUTING.md |
| Examples / case studies | Backlog |
| Stage transition hooks | Backlog |
| Multi-agent workflow guidance | Backlog |
| Mastery MCP Server spec | Backlog — separate repo |
| Framework CHANGELOG.md | Feature #01 (Complete) |

---
