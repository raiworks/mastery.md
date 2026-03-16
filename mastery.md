# 🏛️ MASTERY — Development Process Framework

> **A universal, tech-agnostic framework for building software with discipline.**
> Every feature starts as a discussion, gets designed, becomes a plan, and ships as clean, tested code.
> Works for any project. Any language. Any stack. Any team size. Human or AI-driven.
>
> ⚠️ **THIS FILE IS READ-ONLY** in every project that uses this framework. The copy at `docs/mastery.md` must never be edited — it stays identical across all projects. The only place this file is developed and improved is in its **origin repository**. Project-specific decisions belong in `project-context.md`. Feature-specific decisions belong in feature docs. If you need to customize the process, document overrides in `docs/references/process-overrides.md`.

---

## 📋 Table of Contents

- [Philosophy](#-philosophy)
- [AI Agent Protocol](#-ai-agent-protocol)
  - [Context Loading Order](#context-loading-order)
  - [Determining Current State](#determining-current-state)
  - [Autonomy Boundaries](#autonomy-boundaries)
  - [Verification Cross-Checks](#verification-cross-checks)
  - [MCP-Enhanced Workflow](#mcp-enhanced-workflow)
  - [Session Handoff Protocol](#session-handoff-protocol)
  - [AI Communication Style](#ai-communication-style)
- [Project Initialization](#-project-initialization)
- [Adopting Mastery Mid-Project](#-adopting-mastery-mid-project)
- [Document Ecosystem](#-document-ecosystem)
- [The Workflow — Feature Lifecycle](#-the-workflow--feature-lifecycle)
- [Hotfix Workflow](#-hotfix-workflow)
- [Lightweight Feature Variant](#-lightweight-feature-variant)
- [Document Naming Convention](#-document-naming-convention)
- [Document Templates](#-document-templates)
  - [Project Discussion Doc](#1-project-discussion-document)
  - [Project Context Doc](#2-project-context-document)
  - [Project Roadmap Doc](#3-project-roadmap-document)
  - [Discussion Doc](#4-discussion-document)
  - [Architecture Doc](#5-architecture-document)
  - [Tasks Doc](#6-tasks-document)
  - [Test Plan Doc](#7-test-plan-document)
  - [API Spec Doc](#8-api-spec-document)
  - [Changelog Doc](#9-changelog-document)
  - [Review Doc](#10-review-document)
  - [Lightweight Feature Doc](#11-lightweight-feature-document)
  - [AGENTS.md](#12-agentsmd-ai-agent-orientation)
  - [SKILL.md](#13-skillmd-ai-agent-skill)
  - [llms.txt](#14-llmstxt-machine-readable-summary)
  - [Summary Doc](#15-summary-document-retroactive-feature)
  - [Project Changelog Doc](#16-project-changelog-document)
- [Git Branching Strategy](#-git-branching-strategy)
- [Commit Message Convention](#-commit-message-convention)
- [Parallel Features](#-parallel-features)
- [References Directory](#-references-directory)
- [Cross-Tool Configuration](#-cross-tool-configuration)
- [Resuming Work](#-resuming-work)
- [Definition of Done](#-definition-of-done)
- [Quick Reference](#-quick-reference)

---

## 💡 Philosophy

### Core Principles

1. **Think before you type.** No code is written until the discussion is complete.
2. **Design before you build.** Architecture decisions are documented, not improvised.
3. **Plan before you execute.** Every task is written down and checkable.
4. **Test before you ship.** Every feature has a test plan.
5. **Document as you go.** Changes are logged, not remembered.
6. **Review when you're done.** Reflect, learn, improve.
7. **Never edit the framework in consuming projects.** The `docs/mastery.md` copy is read-only — it stays identical across every project. Improvements happen only in the framework's origin repository.

### Why This Framework Exists

Most projects fail not because of bad code, but because of:
- Features built without understanding the full picture
- Architecture decisions made on the fly and forgotten
- Tasks that live in someone's head instead of a checklist
- Bugs shipped because no one defined what "working" means
- The same mistakes repeated because no one wrote them down
- AI agents making changes without understanding project context or current state

**Mastery** solves this by making the process as important as the product — whether the builder is human, AI, or both.

---

## 🤖 AI Agent Protocol

This section defines how AI agents (copilots, coding assistants, autonomous agents) should interact with this framework. Every AI agent working on a project using Mastery MUST follow these rules.

### Context Loading Order

When an AI agent starts a session on this project, it MUST read documents in this exact order:

```
1. docs/mastery-compact.md      → Framework rules (compact — all rules, no templates)
2. docs/project-discussion.md   → Understand WHY the project exists and key decisions
3. docs/project-context.md      → Understand WHAT the project is (formalized)
4. docs/project-roadmap.md      → Understand WHERE the project stands
5. docs/features/ (active)      → Understand the current feature state
```

**Rule**: Never write code until you have read at minimum `project-context.md` and `project-roadmap.md`. Read `project-discussion.md` when you need deeper context on WHY decisions were made.

> ⚠️ **Every new context**: AI agents MUST re-read `docs/mastery-compact.md` at the start of every new context window or session — not just the first one. The framework rules, autonomy boundaries, and verification requirements must be fresh in context before any work begins.

> 💡 **Token optimization**: `mastery-compact.md` contains all framework rules without templates (~5k tokens vs ~25k for the full file). Load specific templates from the full `mastery.md` only when creating new documents — search for the template heading (e.g., "### 4. Discussion Document").

### Determining Current State

To figure out what's in progress:

1. Check `project-roadmap.md` — look for features marked 🟡 IN PROGRESS
2. Open that feature's docs in order: `discussion → architecture → tasks → changelog`
3. In the tasks doc, find the last checked checkbox — that's where work stopped
4. In the changelog doc, read the most recent entries — that's what happened last
5. Check the git branch — `git log --oneline -10` on the feature branch shows recent commits

### Autonomy Boundaries

AI agents MUST follow these rules about what they can and cannot do independently:

| Action | AI Can Do Autonomously? | Requires Human Approval |
|---|---|---|
| Read any project document | ✅ Yes | — |
| Write code within an active task | ✅ Yes | — |
| Check off completed tasks | ✅ Yes | — |
| Log entries in changelog | ✅ Yes | — |
| Create commits on feature branch | ✅ Yes | — |
| Push to feature branch | ✅ Yes | — |
| Update project changelog | ✅ Yes | — |
| Create a new feature's discussion doc | ✅ Yes | — |
| Modify architecture after finalization | ❌ No | ✅ Must discuss first |
| Skip any lifecycle stage | ❌ No | ✅ Never — no exceptions |
| Merge to main | ❌ No | ✅ Always human-approved |
| Delete any branch | ❌ No | ✅ Always human-approved |
| Delete or overwrite existing docs | ❌ No | ✅ Always human-approved |
| Change project-context.md | ❌ No | ✅ Always human-approved |
| Reorder features in roadmap | ❌ No | ✅ Always human-approved |
| Add new dependencies/packages | ❌ No | ✅ Always human-approved |
| Edit docs/mastery.md | ❌ No | ✅ Never — the project copy is read-only, no exceptions |
| Perform verification cross-check | ✅ Yes | — |
| Skip a required cross-check | ❌ No | ✅ Never — no exceptions |

### Verification Cross-Checks

AI agents MUST verify their work against planning docs — not just check that tests pass. A cross-check is a structured self-audit that catches drift between what was planned and what was built.

#### When to Cross-Check

| Trigger | What to Verify |
|---|---|
| After planning docs created | Discussion ↔ architecture ↔ tasks ↔ testplan alignment |
| Every ~5 build tasks completed | Code matches architecture, tasks checked off, changelog current |
| Before requesting merge | Full cross-check — all items below |

#### What to Verify

1. **Architecture ↔ Code** — Does the implementation match the architecture doc? Are deviations documented?
2. **Tasks ↔ Code** — Are completed tasks reflected in code? Are checkboxes updated?
3. **Testplan ↔ Tests** — Do testplan cases have corresponding tests? Are statuses filled in?
4. **Changelog ↔ Session** — Does the changelog reflect what happened this session?
5. **Dependencies ↔ Architecture** — Are only approved dependencies used?

#### Handling Gaps

- Fix gaps autonomously — update checkboxes, fill testplan statuses, log deviations
- Log the cross-check in the changelog: "Cross-check performed: N gaps found, N fixed"
- Escalate to human for architectural deviations or blocking issues

### MCP-Enhanced Workflow

If an MCP server is configured for a Mastery project, AI agents can use structured tool calls as an alternative to reading raw files. MCP is **optional** — the file-based workflow in Context Loading Order remains fully functional without it.

| Task | Without MCP | With MCP |
|---|---|---|
| Load project context | Read markdown files in order | Call status/overview tools for structured data |
| Find active feature | Parse roadmap for 🟡 markers | Call roadmap tool for parsed feature list |
| Check task progress | Read task file, count checkboxes | Call task tool for structured status |
| Search across docs | Grep through files | Call search tools with queries |

**Guidance**: Prefer MCP tools for status overviews and navigation. Always verify against raw docs when making changes — the files are the source of truth, not the MCP responses.

### Session Handoff Protocol

When ending a session (human-to-AI, AI-to-human, or AI-to-AI), the outgoing party MUST:

1. **Update the changelog** — log what was done in this session
2. **Update task checkboxes** — mark completed items, note partial progress
3. **Leave a "Session Note"** at the top of the changelog:

```markdown
### Session Note — YYYY-MM-DD
- **Who**: [Human / AI Agent Name]
- **Duration**: [Approximate time or "async"]
- **Worked On**: [Brief description]
- **Stopped At**: [Exact task ID, e.g., "B.3 — halfway through validation logic"]
- **Blockers**: [Any issues preventing progress, or "None"]
- **Next Steps**: [What the next session should pick up]
```

### AI Communication Style

When an AI agent is working within this framework:
- **Ask before assuming** — if a requirement is ambiguous, ask. Don't guess.
- **Reference docs** — when making decisions, cite which doc informed the choice.
- **Explain deviations** — if you deviate from the architecture or tasks, log WHY in the changelog before proceeding.
- **Never silently skip** — if a step seems unnecessary, say so and get confirmation. Don't just skip it.
- **Ask about testing** — if a `testplan.md` exists for the active feature, ask the developer if they want test auditing (TC coverage check) during the build stage. Don't assume.

---

## 🚀 Project Initialization

When starting a new project with Mastery, the very first thing you do is **discuss the project** — just like every feature starts with a discussion. No code, no architecture, no planning until the project itself is fully understood.

### Step 1 — Set Up the Docs Skeleton

Create the basic documentation structure:

```
docs/
├── mastery.md                  # Copy the full framework file
├── mastery-compact.md          # Copy the compact variant (for AI agent loading)
├── project-discussion.md       # Create first — discuss the project
├── features/                   # Empty — features go here
└── references/                 # Empty — ADRs, specs, guides go here
```

### Step 2 — Discuss the Project 💬

This is the most important step. Create `docs/project-discussion.md` using the template below and have a thorough conversation (human + AI, or human alone) to answer:

- What is this project? What problem does it solve?
- Who is it for? What are the use cases?
- What tech stack should we use and why?
- What are the architectural patterns and conventions?
- What are the constraints, boundaries, and non-goals?
- What features are needed? In what order?
- What does "done" look like for v1.0 / MVP?

**This conversation IS the project's foundation. Take it seriously. Don't rush it.**

Update `project-discussion.md` iteratively as the conversation evolves. It's a living document until marked COMPLETE.

### Step 3 — Create Project Context

Once the discussion is marked COMPLETE, distill the decisions into `docs/project-context.md` using the template below. This becomes the single source of truth for "what is this project?"

The project-context doc is a **formalized output** of the discussion — structured, clean, and reference-ready.

### Step 3.5 — Generate AGENTS.md

Create `AGENTS.md` at the **project root** (not inside `docs/`) using Template #12. This file is the AI agent entry point — every AI tool (Copilot, Cursor, Claude, etc.) looks for it when entering a project.

**AGENTS.md is a derived artifact** — its content comes from `project-context.md` and `mastery.md` conventions. When `project-context.md` changes, update AGENTS.md to stay in sync.

### Step 4 — Build the Roadmap

Based on the project context, create `docs/project-roadmap.md` using the template below:
- List all features needed to reach v1.0 (or the current milestone)
- Order them by dependency (what must exist before what)
- Assign sequence numbers (01, 02, 03...)
- Mark initial status (all 🔴 NOT STARTED)

### Step 4.5 — Create the Project Changelog

Create `docs/project-changelog.md` using Template #16. Start with an empty `[Unreleased]` section — it will be populated as features ship.

### Step 5 — Start Feature 01

Follow the Feature Lifecycle (below) starting with the Discussion stage.

### Initialization Flow

```
┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐    ┌──────────────┐
│   1. DISCUSS     │    │  2. FORMALIZE    │    │   3. PLAN        │    │  4. BUILD    │
│   the project    │───▶│  project-context │───▶│  project-roadmap │───▶│  Feature 01  │
│                  │    │                  │    │                  │    │              │
│ project-         │    │ project-         │    │ project-         │    │ Feature      │
│ discussion.md    │    │ context.md       │    │ roadmap.md       │    │ Lifecycle    │
└──────────────────┘    └──────────────────┘    └──────────────────┘    └──────────────┘
```

---

## 🔀 Adopting Mastery Mid-Project

If you're adopting Mastery into a project that already has code, history, and decisions made — this section is for you. Instead of starting from scratch, you'll **reconstruct** the project's foundation from what already exists and set up the framework for all future work.

> **When to use this**: Your project has existing code and you want to start using Mastery going forward. For brand-new projects, use [Project Initialization](#-project-initialization) instead.

### Step 1 — Archive Existing Docs

Move any pre-existing project documentation (design docs, wiki exports, specs, meeting notes, etc.) into `docs/_archive/`:

```
docs/
└── _archive/                       # Pre-Mastery documentation (read-only reference)
    ├── original-design-spec.md
    ├── api-notes.md
    └── ...                         # Whatever existed before adoption
```

These files are preserved as historical reference but are **not part of the active Mastery structure**. Don't delete them — they're valuable context for reconstructing decisions.

### Step 2 — Set Up the Docs Skeleton

Same as a new project — create the Mastery folder structure:

```
docs/
├── mastery.md                  # Copy the full framework file
├── mastery-compact.md          # Copy the compact variant (for AI agent loading)
├── project-discussion.md       # Will be reconstructed (Step 3)
├── _archive/                   # From Step 1
├── features/                   # Empty — features go here
└── references/                 # Empty — ADRs, specs, guides go here
```

### Step 3 — Reconstruct the Project Discussion

Create `docs/project-discussion.md` using the template, but instead of having a fresh conversation, **reconstruct the decisions from existing sources**:

- Read the codebase — what patterns, conventions, and architecture are already in place?
- Read git history — what were the major milestones and pivots?
- Read archived docs — what design decisions were documented before?
- Talk to the team — what tribal knowledge needs to be captured?

Document decisions as if they were made today, citing the evidence. Mark the discussion **COMPLETE immediately** — these decisions have already been made.

### Step 4 — Create Project Context

Distill the reconstructed discussion into `docs/project-context.md`. This captures the project as it exists **right now** — its identity, stack, architecture, conventions, and scope.

### Step 5 — Generate AGENTS.md

Create `AGENTS.md` at the project root using Template #12, derived from the new project-context.md. Same as the standard initialization flow.

### Step 6 — Catalog Completed Work

For each major piece of work already completed, create a **retroactive feature folder** with a single `summary.md`:

```
docs/features/
├── 01-user-authentication/
│   └── summary.md              # Retroactive — what was built, key decisions
├── 02-payment-integration/
│   └── summary.md              # Retroactive — what was built, key decisions
├── 03-admin-dashboard/
│   └── summary.md              # Retroactive — what was built, key decisions
└── 04-next-feature/
    ├── discussion.md           # ← Full lifecycle starts here
    ├── architecture.md
    └── ...
```

**Do NOT create full lifecycle docs** (discussion.md, architecture.md, tasks.md, etc.) for past work — those would be fiction. A single `summary.md` captures what matters without pretending the process was followed at the time. Use Template #15 for the format.

> **Granularity tip**: Don't try to retroactively document every commit. Group past work into logical features — major milestones, epics, or functional areas. 3–8 retroactive features is typical.

### Step 7 — Build the Roadmap

Create `docs/project-roadmap.md` with:
- Retroactive features already marked ✅ Complete with "(retroactive)" notes
- Future features marked 🔴 Not Started
- Feature numbering continues sequentially (e.g., if 3 retroactive features exist as #01–#03, the next new feature is #04)

### Step 8 — Start the Next Feature Normally

From here on, the full [Feature Lifecycle](#-the-workflow--feature-lifecycle) applies. The first new feature follows the complete Discuss → Design → Plan → Build → Ship → Reflect cycle.

### Mid-Project Adoption Flow

```
┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐    ┌──────────────┐
│  1. ARCHIVE      │    │  2. RECONSTRUCT  │    │  3. CATALOG      │    │  4. BUILD    │
│  existing docs   │───▶│  discussion +    │───▶│  past work as    │───▶│  next feature│
│                  │    │  context         │    │  summary.md      │    │  (full cycle)│
│ docs/_archive/   │    │ project-         │    │ features/        │    │ Feature      │
│                  │    │ discussion.md    │    │ XX/summary.md    │    │ Lifecycle    │
│                  │    │ project-         │    │ project-         │    │              │
│                  │    │ context.md       │    │ roadmap.md       │    │              │
└──────────────────┘    └──────────────────┘    └──────────────────┘    └──────────────┘
```

---

## 📂 Document Ecosystem

Every project using Mastery has this documentation structure:

```
AGENTS.md                           # 🤖 AI agent orientation (at project root — derived from project-context.md)
SKILL.md                            # ⚡ AI agent skill (at project root — optional, when project has domain expertise)
llms.txt                            # ⚡ Machine-readable project summary (at project root — optional, for discoverability)
docs/
├── mastery.md                  # 🏛️ Full process framework (with all templates)
├── mastery-compact.md          # 📦 Compact framework (rules only — no templates, for AI loading)
├── project-discussion.md       # 💬 Project-level discussion — WHY and WHAT (created first)
├── project-context.md          # 🎯 Project identity, stack, architecture, scope (from discussion)
├── project-roadmap.md          # 🗺️ Feature list, priorities, dependencies, progress (from discussion)
├── project-changelog.md        # 📝 Project history — high-level log of shipped features and changes
│
├── _archive/                   # 📁 Pre-Mastery docs (mid-project adoption only)
│   └── ...                        # Historical docs preserved as reference
│
├── features/                   # 📁 Per-feature folders (one folder per feature)
│   ├── XX-feature-name/           # Folder named by sequence + feature
│   │   ├── discussion.md
│   │   ├── architecture.md
│   │   ├── tasks.md
│   │   ├── testplan.md
│   │   ├── api.md                 # (only for features with API/interface contracts)
│   │   ├── changelog.md
│   │   └── review.md
│   └── ...
│
└── references/                 # 📁 Standalone references (ADRs, specs, guides)
    ├── ADR-001-title.md           # Architecture Decision Records
    ├── style-guide.md             # Coding conventions
    ├── glossary.md                # Domain-specific terminology
    └── ...                        # Any reference material
```

### Document Roles

| Document | Scope | Purpose | When Created |
|---|---|---|---|
| **AGENTS.md** | Project | AI agent orientation — quick-start guide for any AI tool | After project-context.md is created (project init) |
| **SKILL.md** | Project | AI agent skill — domain knowledge packaging for AI tools | When project has domain expertise worth packaging |
| **llms.txt** | Project | Machine-readable summary — LLM-parseable project overview | When project is publicly discoverable |
| **mastery.md** | Universal | Full process framework with templates — HOW you work | Once (project init) |
| **mastery-compact.md** | Universal | Compact framework for AI agent loading — rules only, no templates | Once (project init) |
| **project-discussion.md** | Project | Project-level conversation — WHY and WHAT | First (project init), before anything else |
| **project-context.md** | Project | Project identity — WHAT you're building | After project discussion is COMPLETE |
| **project-roadmap.md** | Project | Feature plan — WHEN you build it | After project discussion is COMPLETE, updated continuously |
| **project-changelog.md** | Project | Project history — high-level log of shipped features and changes | After first feature ships, updated every merge and hotfix |
| **discussion.md** | Feature | Requirements & design conversation | Start of every feature |
| **architecture.md** | Feature | Technical design & file structure | After discussion, before coding |
| **tasks.md** | Feature | Phased implementation checklist | After architecture is designed |
| **testplan.md** | Feature | Test cases & acceptance criteria | Alongside or after tasks |
| **api.md** | Feature | Interface contracts (APIs, CLIs, protocols, events) | When feature has external interfaces |
| **changelog.md** | Feature | Running log of changes during implementation | During build phase |
| **review.md** | Feature | Post-implementation retrospective | After merge to main |
| **summary.md** | Feature | Retroactive feature summary (mid-project adoption) | During mid-project adoption for already-completed work |
| **lightweight.md** | Feature | Single combined doc for lightweight-eligible features | When feature meets ALL lightweight eligibility criteria |

### Which Docs Are Required vs Optional?

| Document | Required? | Skip When... |
|---|---|---|
| **AGENTS.md** | ✅ Always | Never skip — ensures any AI tool can orient itself in the project |
| **SKILL.md** | ⚡ Conditional | Project has no domain expertise worth packaging as an agent skill |
| **llms.txt** | ⚡ Conditional | Project is not publicly discoverable or doesn't need machine-readable summary |
| **mastery-compact.md** | ✅ Always | Never skip — this is what AI agents load each session instead of the full file |
| **project-discussion** | ✅ Always | Never skip — this is the project's foundation conversation |
| **project-context** | ✅ Always | Never skip — this is the project's identity |
| **project-roadmap** | ✅ Always | Never skip — this is the project's plan |
| **project-changelog** | ✅ Always | Never skip — this is the project's shipped history |
| **discussion** | ✅ Always | Never skip — this is the foundation |
| **architecture** | ✅ Always | Never skip — even simple features need structure planning |
| **tasks** | ✅ Always | Never skip — this is your execution plan |
| **testplan** | ✅ Always | Never skip — define "done" before you start |
| **api** | ⚡ Conditional | Feature has no external interfaces (HTTP, CLI, events, protocols) |
| **changelog** | ✅ Always | Never skip — tracks what actually happened vs what was planned |
| **review** | ✅ Always | Never skip — learning compounds over time |
| **summary** | ⚡ Conditional | Only for retroactive features during mid-project adoption |
| **lightweight** | ⚡ Conditional | Feature does NOT meet all lightweight eligibility criteria |

> **Lightweight features**: Features meeting ALL lightweight eligibility criteria use a single `lightweight.md` instead of individual docs. See [Lightweight Feature Variant](#-lightweight-feature-variant).

---

## 🔄 The Workflow — Feature Lifecycle

Every feature flows through **6 stages**. Each stage has a clear entry condition and exit condition.

```
┌────────────────────────────────────────────────────────────────────────────┐
│                         FEATURE LIFECYCLE                                  │
│                                                                            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────────┐  │
│  │    1.    │  │    2.    │  │    3.    │  │    4.    │  │     5.     │  │
│  │ DISCUSS  │─▶│ DESIGN   │─▶│  PLAN    │─▶│  BUILD   │─▶│   SHIP     │  │
│  │          │  │          │  │          │  │          │  │            │  │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘  └────────────┘  │
│       │              │             │             │              │          │
│   discussion    architecture     tasks      changelog       review        │
│   doc created   doc created    doc created   updated        doc created   │
│                                testplan                                   │
│                                doc created                                │
│                                api doc                                    │
│                                (if needed)                                │
│                                                                           │
│                         ┌──────────┐                                      │
│                         │    6.    │                                       │
│                         │ REFLECT  │                                       │
│                         └──────────┘                                       │
│                          review doc                                        │
│                          completed                                         │
└────────────────────────────────────────────────────────────────────────────┘
```

### Stage 1 — Discuss 💬

> **Entry**: Feature identified in roadmap
> **Exit**: Discussion doc marked COMPLETE

| Action | Detail |
|---|---|
| Create `XX-feature-name/discussion.md` | Use the discussion template |
| Define WHAT the feature does | Functional requirements, user stories |
| Understand current state | Reference existing code, legacy system, or prior art |
| Identify the approach | High-level "how" — not detailed yet |
| Surface edge cases | What can go wrong? What's tricky? |
| List dependencies | What must exist before this feature? |
| Discuss until confident | Update doc iteratively — it's a living conversation |
| Mark COMPLETE | Add summary at top, note the date |

### Stage 2 — Design 🏗️

> **Entry**: Discussion marked COMPLETE
> **Exit**: Architecture doc reviewed and finalized

| Action | Detail |
|---|---|
| Create `XX-feature-name/architecture.md` | Use the architecture template |
| Define file structure | Every file to create/modify, with paths |
| Design data models | Schema, relationships, constraints (if applicable) |
| Design interfaces | Function signatures, class APIs, contracts |
| Draw data flow | How data moves through the system |
| Document trade-offs | Why this approach over alternatives |
| Define config changes | Environment variables, settings (if applicable) |

### Stage 3 — Plan 📋

> **Entry**: Architecture doc finalized
> **Exit**: Tasks doc + test plan + API spec (if needed) created

| Action | Detail |
|---|---|
| Create `XX-feature-name/tasks.md` | Break architecture into granular, checkable tasks |
| Organize into phases | Group logically for your project type (see phase guidance below) |
| Add checkpoints | Verification points between phases |
| Create `XX-feature-name/testplan.md` | Define test cases, acceptance criteria |
| Create `XX-feature-name/api.md` | If feature has external interfaces — define contracts |
| Create `XX-feature-name/changelog.md` | Empty — ready for build phase logging |
| Create feature branch | `feature/XX-feature-name` from main |

#### Phase Organization Guidance

Phases in the tasks doc should be organized logically for your project type. The framework does NOT prescribe fixed phases — adapt them to your domain:

| Project Type | Suggested Phases |
|---|---|
| **Web Application** | Data Layer → Business Logic → HTTP/API → UI/Frontend → Testing → Docs |
| **CLI Tool** | Core Logic → Command Parsing → Input/Output → Error Handling → Testing → Docs |
| **Library/SDK** | Core API → Internal Utilities → Public Interface → Testing → Docs |
| **Data Pipeline** | Ingestion → Transformation → Validation → Output/Storage → Testing → Docs |
| **Mobile App** | Data/State → Core Logic → UI Components → Navigation → Testing → Docs |
| **Embedded/IoT** | Hardware Interface → Core Logic → Communication → Testing → Docs |
| **ML/AI Project** | Data Preparation → Model Design → Training → Evaluation → Deployment → Docs |
| **Infrastructure** | Resource Definition → Configuration → Networking → Security → Testing → Docs |

**Rule**: Always end with a Testing phase and a Documentation/Cleanup phase regardless of project type.

### Stage 4 — Build 🔨

> **Entry**: Branch created, all planning docs done
> **Exit**: All task checkboxes checked, all tests pass

| Action | Detail |
|---|---|
| Execute tasks phase by phase | Check off items as you go |
| Log changes in changelog | What was built, what deviated from plan, decisions made |
| Add session notes | If working across multiple sessions (see AI Agent Protocol) |
| Commit frequently | Clear messages following convention |
| Run tests at checkpoints | Verify before moving to next phase |
| Ask about testing approach | Before writing tests, ask the developer: test runner, naming conventions, coverage expectations. If a testplan.md exists, follow it. |
| Push to feature branch | Keep remote in sync |

### Stage 5 — Ship 🚀

> **Entry**: All tasks complete, all tests pass
> **Exit**: Feature merged to main (human-approved)

| Action | Detail |
|---|---|
| Self-review all changes | Read your own diff |
| Final test pass | Full test plan one last time |
| Human approval | AI agents MUST get human sign-off before merge |
| Merge to main | PR or direct merge (human executes or approves) |
| Update project changelog | Add entry to `project-changelog.md` for the shipped feature |
| Push main | Deploy pipeline triggers (if configured) |
| Keep the feature branch | Never delete — historical reference |

### Stage 6 — Reflect 🪞

> **Entry**: Feature merged
> **Exit**: Review doc completed

| Action | Detail |
|---|---|
| Create/complete `XX-feature-name/review.md` | Use the review template |
| What went well? | Patterns to repeat |
| What went wrong? | Issues encountered, time sinks |
| What was learned? | New knowledge to carry forward |
| Update roadmap | Mark feature as complete in `project-roadmap.md` |

---

## 🚑 Hotfix Workflow

Not everything can go through the full 6-stage lifecycle. Critical bugs in production need an abbreviated path.

### When to Use Hotfix

- Production is broken or degraded
- Security vulnerability discovered
- Data corruption or loss risk
- The fix is small and well-understood

### Hotfix Lifecycle (Abbreviated)

```
┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
│ IDENTIFY │─▶│   FIX    │─▶│  VERIFY  │─▶│  MERGE   │
└──────────┘  └──────────┘  └──────────┘  └──────────┘
```

1. **Identify** — Describe the bug in one paragraph. What's broken? What's the impact?
2. **Branch** — Create `hotfix/brief-description` from `main`
3. **Fix** — Make the minimal change needed. No refactoring. No "while I'm here" changes.
4. **Verify** — Test the fix. Confirm the bug is resolved. Confirm nothing else broke.
5. **Merge** — Human-approved merge to `main`. Push immediately.
6. **Document** — Add a hotfix entry to the changelog of the most relevant feature, or create a standalone entry in `references/hotfix-log.md`. Update `project-changelog.md` with the fix.

### Hotfix Rules

- Hotfixes skip Discussion, Architecture, and Tasks docs
- Hotfixes NEVER skip testing
- Hotfixes MUST be documented after the fact
- If the fix is complex or touches multiple systems, it's NOT a hotfix — use the full lifecycle
- After the hotfix is merged, consider whether a follow-up feature is needed to address the root cause

---

## 🪶 Lightweight Feature Variant

Not every feature needs the full 6-doc lifecycle. For planned changes that are docs-only, config-only, or trivially simple, the Lightweight Feature Variant provides an abbreviated path using a **single combined document** instead of six separate ones.

> **Key difference from Hotfix**: Hotfixes are for **unplanned urgent** fixes (production broken). Lightweight is for **planned trivial** work (simple, low-risk changes you can describe in a few sentences).

### When to Use Lightweight

A feature qualifies as lightweight when **ALL** of the following are true:

1. **No new code logic** — docs-only, config-only, or trivial changes (typo fixes, renaming, reordering)
2. **No architectural decisions** — no new files, no new data models, no new interfaces, no dependency changes
3. **Well-understood scope** — the change can be fully described in a few sentences
4. **Low risk** — failure would not break production, corrupt data, or compromise security
5. **Self-contained** — the change does not affect other features in progress

If **any** criterion is not met, use the full lifecycle. When in doubt, use the full lifecycle.

### Lightweight Lifecycle

```
┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
│  CREATE  │─▶│   WORK   │─▶│  VERIFY  │─▶│   SHIP   │
│ lightweight│  │  Execute │  │  Review  │  │  Merge   │
│   .md    │  │  tasks   │  │  & test  │  │ & reflect│
└──────────┘  └──────────┘  └──────────┘  └──────────┘
```

1. **Create** — Create `XX-feature-name/lightweight.md` using the template. Fill in Summary, Scope & Approach, Tasks, and Verification sections. Create feature branch.
2. **Work** — Execute the tasks. Log progress in the Changelog section.
3. **Verify** — Run the verification checks. Confirm everything works.
4. **Ship** — Human-approved merge to `main`. Fill in the Reflection section after merge.

### Lightweight Rules

- Lightweight features **still use feature branches** (`feature/XX-name`) — no direct commits to main
- Lightweight features **still require human approval** for merge — no autonomous merging
- Feature branches are **never deleted** — same as full lifecycle
- If scope grows beyond eligibility, **upgrade to full lifecycle**: the lightweight doc becomes your `discussion.md`, then create the remaining docs as needed
- The lightweight doc stays in the feature folder even after upgrade — it's historical record

---

## 📛 Document Naming Convention

### Feature Folders

Each feature gets its own folder inside `docs/features/`, named with the sequence number and feature name. All docs inside use simple, consistent filenames:

```
docs/features/
├── 01-project-setup/
│   ├── discussion.md
│   ├── architecture.md
│   ├── tasks.md
│   ├── testplan.md
│   ├── changelog.md
│   └── review.md
├── 02-auth-system/
│   ├── discussion.md
│   ├── architecture.md
│   ├── tasks.md
│   ├── testplan.md
│   ├── api.md
│   ├── changelog.md
│   └── review.md
├── 03-update-readme/
│   └── lightweight.md          # Lightweight variant — single combined doc
└── ...
```

### Naming Rules

| Element | Format | Example |
|---|---|---|
| **Folder name** | `XX-feature-name` (2-digit zero-padded + lowercase hyphen-separated) | `01-project-setup`, `02-auth-system` |
| **Doc filenames** | Simple type name inside the folder | `discussion.md`, `architecture.md`, `tasks.md`, `testplan.md`, `api.md`, `changelog.md`, `review.md` |
| **Branch name** | `feature/XX-feature-name` (matches folder name) | `feature/02-auth-system` |

### Why Folders Instead of Flat Files?

- A project with 20 features would have 120+ files in a flat structure — unmanageable
- Folders group related docs together — everything about one feature is in one place
- Filenames stay short and clean — no repetitive prefixes
- Easy to navigate in any file explorer or IDE
- Each folder is self-contained — you can understand a feature by opening its folder

### Sequence Assignment Principle

Features are numbered in **dependency order** — what must exist first comes first. Define the sequence in `project-roadmap.md` based on your project's specific needs.

General ordering logic (adapt to your project type):
1. **Foundation** — project setup, configuration, core infrastructure
2. **Data layer** — database, models, state management, storage
3. **Core logic** — business logic, libraries, services, algorithms
4. **Interface layer** — APIs, CLIs, event handlers, protocol handlers
5. **Presentation** — UI, views, output formatting, reporting
6. **Authentication/Security** — before any protected feature
7. **Protected features** — features requiring auth or elevated access
8. **Integrations** — third-party services, external APIs, plugins
9. **Optimization** — caching, performance, security hardening
10. **Deployment** — CI/CD, monitoring, production readiness

---

## 📝 Document Templates

Below are the templates for every document type. Copy the relevant template when starting a new document.

---

### 1. Project Discussion Document

**Filename**: `project-discussion.md`
**Location**: `docs/project-discussion.md`
**Purpose**: The very first document created for any project. A structured conversation to fully understand the project before formalizing anything. Once complete, its decisions flow into `project-context.md` and `project-roadmap.md`.
**Created**: First thing during project initialization. Marked COMPLETE before any other project doc is created.

````markdown
# 💬 Project Discussion

> **Project**: [Project Name or Working Title]
> **Status**: 🟡 IN PROGRESS | 🟢 COMPLETE
> **Date Started**: YYYY-MM-DD
> **Date Completed**: —

---

## What Are We Building?

<!-- Describe the project in plain language. What does it do? What problem does it solve? Who is it for? -->

## Why Does This Project Exist?

<!-- What's the motivation? What pain point or opportunity drives this? -->
<!-- Why build this instead of using an existing solution? -->

## Target Users / Consumers

<!-- Who will use this? End users? Developers? Internal team? Other systems? -->

| User Type | Description | Primary Need |
|---|---|---|
| [User type] | [Who they are] | [What they need from this project] |

## Core Use Cases

<!-- The essential things this project must do. Not a full feature list — just the core value. -->

- [Use case 1 — what the user does and what happens]
- [Use case 2]
- [Use case 3]

## Tech Stack Discussion

<!-- What technologies should we use? Discuss options and trade-offs. -->

| Layer | Options Considered | Decision | Rationale |
|---|---|---|---|
| **Language** | [Option A, Option B] | [Chosen] | [Why] |
| **Framework** | [Option A, Option B] | [Chosen] | [Why] |
| **Database** | [Option A, Option B, None] | [Chosen] | [Why] |
| **Testing** | [Option A, Option B] | [Chosen] | [Why] |
| **Build/Tooling** | [Option A, Option B] | [Chosen] | [Why] |
| **Deployment** | [Option A, Option B, TBD] | [Chosen] | [Why] |

<!-- Add or remove rows as needed -->

## Architecture Discussion

<!-- High-level architecture thoughts. Not detailed design — just the big picture. -->
<!-- What pattern? Monolith vs microservices? MVC? Event-driven? Serverless? -->

### Proposed Pattern
<!-- e.g., "Monolithic MVC with service layer" or "Serverless event-driven" -->

### Key Architectural Decisions
<!-- Big decisions that shape the entire project -->

| Decision | Choice | Why |
|---|---|---|
| [Decision area] | [What was chosen] | [Rationale] |

## Project Structure Discussion

<!-- How should the codebase be organized? Discuss folder structure, module boundaries. -->

```
project-root/
├── [directory]/          # [Purpose]
├── [directory]/          # [Purpose]
└── docs/                 # Mastery documentation
```

## Scope & Boundaries

### In Scope (v1.0 / MVP)
<!-- What WILL be built in the first milestone -->

- [Feature/capability]
- [Feature/capability]

### Out of Scope (v1.0 / MVP)
<!-- What will NOT be built yet — important to define boundaries early -->

- [Feature/capability] — [why deferred]
- [Feature/capability] — [why deferred]

### Known Constraints
<!-- Technical, business, time, or resource constraints -->

- [Constraint and its impact]

## Feature Brainstorm

<!-- List all features that come to mind. Don't worry about order yet — that's for the roadmap. -->
<!-- Mark priority: 🔴 Must Have, 🟡 Should Have, 🟢 Nice to Have -->

| Feature Idea | Priority | Notes / Dependencies |
|---|---|---|
| [Feature] | 🔴 Must Have | [Notes] |
| [Feature] | 🔴 Must Have | [Notes] |
| [Feature] | 🟡 Should Have | [Notes] |
| [Feature] | 🟢 Nice to Have | [Notes] |

## Conventions & Standards Discussion

<!-- Agree on coding style, naming, git workflow, etc. -->

| Convention | Standard | Notes |
|---|---|---|
| **Code formatting** | [e.g., Prettier, Black] | [Config details] |
| **Linting** | [e.g., ESLint, flake8] | [Config details] |
| **Naming convention** | [e.g., camelCase, snake_case] | [Where applied] |
| **File naming** | [e.g., kebab-case, PascalCase] | [Where applied] |
| **Git workflow** | Mastery branching strategy | See mastery.md |
| **Commit messages** | Mastery convention | See mastery.md |

## Open Questions

<!-- Things we're unsure about — resolve before marking complete -->

- [ ] Question 1?
- [ ] Question 2?

## Decisions Log

<!-- Running log of decisions made during this discussion -->

| Date | Decision | Rationale |
|---|---|---|
| YYYY-MM-DD | [Decision] | [Why] |

## Discussion Complete ✅

<!-- Fill this when the discussion is done -->

**Summary**: [One-paragraph summary of what was agreed about the project]
**Completed**: YYYY-MM-DD
**Next Steps**:
1. Create `project-context.md` — formalize the project identity from this discussion
2. Create `project-roadmap.md` — order the features and assign sequence numbers
3. Start Feature 01 — begin the feature lifecycle
````

---

### 2. Project Context Document

**Filename**: `project-context.md`
**Location**: `docs/project-context.md`
**Purpose**: Define the project's identity, stack, architecture, and conventions. This is the single source of truth for "what is this project?" — formalized from the project discussion.
**Created**: After `project-discussion.md` is marked COMPLETE. Updated rarely and only with human approval.

````markdown
# 🎯 Project Context

> **Project**: [Project Name]
> **Version**: [Current version or "Pre-release"]
> **Last Updated**: YYYY-MM-DD

---

## What Is This Project?

<!-- One to three paragraphs: What does this project do? Who is it for? What problem does it solve? -->

## Project Type

<!-- What kind of software is this? -->

| Property | Value |
|---|---|
| **Type** | Web App / CLI Tool / Library / API Service / Mobile App / Desktop App / Data Pipeline / Other |
| **Platform** | Web / iOS / Android / Cross-platform / Server / Embedded / Other |
| **Distribution** | SaaS / Self-hosted / Package / Binary / Other |

## Tech Stack

<!-- List every technology choice and WHY it was chosen -->

| Layer | Technology | Version | Why |
|---|---|---|---|
| **Language** | [e.g., Python, TypeScript, Rust] | [version] | [reason] |
| **Framework** | [e.g., Django, Next.js, Actix] | [version] | [reason] |
| **Database** | [e.g., PostgreSQL, SQLite, None] | [version] | [reason] |
| **ORM/Data** | [e.g., SQLAlchemy, Prisma, None] | [version] | [reason] |
| **Testing** | [e.g., pytest, Jest, cargo test] | [version] | [reason] |
| **Build** | [e.g., webpack, cargo, make] | [version] | [reason] |
| **Deployment** | [e.g., Docker, Vercel, AWS, None yet] | — | [reason] |

<!-- Add or remove rows as needed for your stack -->

## Architecture Overview

<!-- High-level architecture: patterns, layers, key design decisions -->

### Pattern

<!-- e.g., MVC, Clean Architecture, Microservices, Monolith, Event-Driven, Serverless -->

### Project Structure

```
project-root/
├── [directory]/          # [Purpose]
├── [directory]/          # [Purpose]
├── [file]                # [Purpose]
└── docs/                 # Mastery documentation
```

### Key Architectural Decisions

<!-- List the big decisions that shape the entire project -->

| Decision | Choice | Rationale |
|---|---|---|
| [Decision area] | [What was chosen] | [Why] |

## Conventions & Standards

### Code Style

<!-- Formatting, linting, naming conventions -->

| Convention | Standard |
|---|---|
| **Formatting** | [e.g., Prettier, Black, rustfmt] |
| **Linting** | [e.g., ESLint, flake8, clippy] |
| **Naming** | [e.g., camelCase for JS, snake_case for Python] |
| **File naming** | [e.g., kebab-case, PascalCase for components] |

### Git Conventions

<!-- Branching, commit messages — reference mastery.md -->

- Branching: See `mastery.md` Git Branching Strategy
- Commits: See `mastery.md` Commit Message Convention

### Environment Setup

<!-- How to get this project running from scratch -->

```bash
# Step-by-step commands to set up the project
```

### Environment Variables

<!-- List all env vars the project uses -->

| Variable | Required | Default | Description |
|---|---|---|---|
| `EXAMPLE_VAR` | Yes/No | [default] | [What it does] |

## Scope & Constraints

### In Scope (v1.0)

<!-- What WILL be built -->

- [Feature/capability]
- [Feature/capability]

### Out of Scope (v1.0)

<!-- What will NOT be built yet — important to define boundaries -->

- [Feature/capability] — [why deferred]
- [Feature/capability] — [why deferred]

### Known Constraints

<!-- Technical, business, or resource constraints -->

- [Constraint and its impact]

## Team & Roles

<!-- Who works on this project and how -->

| Role | Who | Responsibilities |
|---|---|---|
| **Lead / Owner** | [Name or "Solo"] | Final decisions, merge approval |
| **AI Agent** | [Agent name or "Any"] | Implementation within Mastery framework |
| **Contributors** | [Names or "None yet"] | Feature work, reviews |
````

---

### 3. Project Roadmap Document

**Filename**: `project-roadmap.md`
**Location**: `docs/project-roadmap.md`
**Purpose**: Track all features, their priority, dependencies, and progress. This is the single source of truth for "what are we building and in what order?"
**Created**: After `project-discussion.md` is marked COMPLETE. Updated continuously as features progress.

````markdown
# 🗺️ Project Roadmap

> **Project**: [Project Name]
> **Current Milestone**: [e.g., v1.0, MVP, Beta]
> **Last Updated**: YYYY-MM-DD

---

## Progress Overview

| Metric | Count |
|---|---|
| Total Features | XX |
| 🟢 Complete | XX |
| 🟡 In Progress | XX |
| 🔴 Not Started | XX |
| ⏸️ On Hold | XX |

**Overall Progress**: ░░░░░░░░░░ X% <!-- Update visually or with percentage -->

---

## Feature List

<!-- Order by sequence number (dependency order) -->

| # | Feature | Status | Depends On | Branch | Notes |
|---|---|---|---|---|---|
| 01 | [Feature Name] | 🟢 Complete | — | `feature/01-name` | [Brief note] |
| 02 | [Feature Name] | 🟡 In Progress | #01 | `feature/02-name` | [Brief note] |
| 03 | [Feature Name] | 🔴 Not Started | #01, #02 | — | [Brief note] |
| 04 | [Feature Name] | 🔴 Not Started | #02 | — | [Brief note] |
| 05 | [Feature Name] | ⏸️ On Hold | #03 | — | [Why on hold] |

---

## Dependency Map

<!-- Visual or textual representation of what depends on what -->

```
01 [Foundation]
 ├── 02 [Feature] ──── 04 [Feature]
 │    └── 03 [Feature] ──── 05 [Feature]
 └── 06 [Feature]
```

---

## Milestones

### [Milestone Name, e.g., MVP / v1.0 / Beta]

**Target**: YYYY-MM-DD (or "When features 01-06 complete")
**Features Included**: #01, #02, #03, #04, #05, #06

| Criterion | Status |
|---|---|
| All included features merged | ⬜ / ✅ |
| All test plans passing | ⬜ / ✅ |
| Documentation complete | ⬜ / ✅ |
| Deployment ready | ⬜ / ✅ |

---

## Backlog

<!-- Features identified but not yet scheduled — no sequence number assigned -->

| Feature Idea | Priority | Notes |
|---|---|---|
| [Feature idea] | High / Medium / Low | [Context] |
| [Feature idea] | High / Medium / Low | [Context] |

---

## Change Log

<!-- Track changes to the roadmap itself -->

| Date | Change | Reason |
|---|---|---|
| YYYY-MM-DD | [What changed in the roadmap] | [Why] |
````

---

### 4. Discussion Document

**Filename**: `discussion.md`
**Location**: `docs/features/XX-feature-name/discussion.md`
**Purpose**: Understand the feature completely through structured conversation.

````markdown
# 💬 Discussion: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Status**: 🟡 IN PROGRESS | 🟢 COMPLETE
> **Branch**: `feature/XX-feature-name`
> **Depends On**: #XX, #XX (list prerequisite feature numbers)
> **Date Started**: YYYY-MM-DD
> **Date Completed**: —

---

## Summary

<!-- One paragraph: What does this feature do and why does it matter? -->

---

## Functional Requirements

<!-- What should this feature do from the user's/consumer's perspective? -->
<!-- Use bullet points, user stories, or acceptance statements -->

- As a [role], I want [action] so that [outcome]
- ...

## Current State / Reference

<!-- How does this work today? Legacy system? Existing code? Starting from scratch? -->
<!-- Include file paths, code patterns, screenshots, or links -->

### What Exists
<!-- Describe current implementation or "Nothing — greenfield feature" -->

### What Works Well
<!-- Patterns to keep or replicate -->

### What Needs Improvement
<!-- What should be redesigned, removed, or rethought? -->

## Proposed Approach

<!-- High-level description of how we'll implement this -->
<!-- NOT detailed architecture — that comes in the architecture doc -->

## Dependencies

<!-- What must exist before this feature can be built? -->

| Dependency | Type | Status |
|---|---|---|
| Feature #XX — [Name] | Feature | ✅ Done / 🔴 Not started |
| [Package/Library] | External | ✅ Available / 🔴 Needs install |
| [Service/API] | Infrastructure | ✅ Ready / 🔴 Needs setup |

## Open Questions

<!-- Things we're unsure about — resolve before marking complete -->

- [ ] Question 1?
- [ ] Question 2?

## Decisions Made

<!-- Running log — add entries as decisions happen -->

| Date | Decision | Rationale |
|---|---|---|
| YYYY-MM-DD | [Decision] | [Why] |

## Discussion Complete ✅

<!-- Fill this when done -->

**Summary**: [One-sentence final summary of what was agreed]
**Completed**: YYYY-MM-DD
**Next**: Create architecture doc → `architecture.md`
````

---

### 5. Architecture Document

**Filename**: `architecture.md`
**Location**: `docs/features/XX-feature-name/architecture.md`
**Purpose**: Technical design — file structure, data flow, interfaces, and trade-offs.

````markdown
# 🏗️ Architecture: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Discussion**: [`discussion.md`](discussion.md)
> **Status**: 🟡 DRAFT | 🟢 FINALIZED
> **Date**: YYYY-MM-DD

---

## Overview

<!-- One paragraph: Technical summary of the approach -->

## File Structure

<!-- Every file to create or modify, with full paths -->

```
path/to/
├── new-file-1.ext          # Purpose
├── new-file-2.ext          # Purpose
└── existing-file.ext       # MODIFY — what changes
```

## Data Model

<!-- Database tables, schemas, state structures, data formats -->
<!-- Adapt to your project: SQL tables, document schemas, state trees, config structures, etc. -->
<!-- If feature has no data model, write "N/A — this feature does not introduce data models" -->

### [Table/Collection/Entity/Structure Name]

| Field | Type | Constraints | Description |
|---|---|---|---|
| id | int/uuid/string | PK, auto | Unique identifier |
| ... | ... | ... | ... |

### Relationships / References
<!-- Foreign keys, references, associations, or "N/A" -->

## Component Design

<!-- Classes, modules, functions, commands — the building blocks -->

### [Component Name]

**Responsibility**: [What this component does]
**Location**: `path/to/file.ext`

```
Key Methods / Functions:
├── methodName(params) → returnType    # What it does
├── methodName(params) → returnType    # What it does
└── methodName(params) → returnType    # What it does
```

## Data Flow

<!-- How data moves through the system for this feature -->

```
[Trigger] → [Entry Point] → [Processing] → [Storage/Output] → [Response/Result]
```

<!-- Describe each step -->

## Configuration

<!-- Environment variables, config files, settings -->
<!-- If none, write "No configuration changes required" -->

| Key | Value/Type | Description |
|---|---|---|
| `CONFIG_KEY` | string/int/bool | What it configures |

## Security Considerations

<!-- Auth, authorization, input validation, encryption, etc. -->
<!-- If not applicable, write "No security implications for this feature" -->

## Trade-offs & Alternatives

<!-- Why this approach? What else was considered? -->

| Approach | Pros | Cons | Verdict |
|---|---|---|---|
| Chosen approach | ... | ... | ✅ Selected |
| Alternative A | ... | ... | ❌ Reason |

## Next

Create tasks doc → `tasks.md`
````

---

### 6. Tasks Document

**Filename**: `tasks.md`
**Location**: `docs/features/XX-feature-name/tasks.md`
**Purpose**: Phased implementation checklist with checkpoints. Phases are customizable per project type.

````markdown
# ✅ Tasks: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Architecture**: [`architecture.md`](architecture.md)
> **Branch**: `feature/XX-feature-name`
> **Status**: 🔴 NOT STARTED | 🟡 IN PROGRESS | 🟢 COMPLETE
> **Progress**: 0/XX tasks complete

---

## Pre-Flight

- [ ] Discussion doc is marked COMPLETE
- [ ] Architecture doc is FINALIZED
- [ ] Feature branch created from main
- [ ] Dependent features are merged to main

---

<!-- 
PHASE GUIDANCE: Organize phases logically for your project type.
See mastery.md "Phase Organization Guidance" for examples.
The phases below are a TEMPLATE — rename, add, remove, or reorder as needed.
Always keep a Testing phase and a Documentation/Cleanup phase at the end.
-->

## Phase A — [Phase Name]

> [One-line description of what this phase covers]

- [ ] **A.1** — [Specific task description]
  - [ ] Sub-step if needed
  - [ ] Sub-step if needed
- [ ] **A.2** — [Specific task description]
- [ ] 📍 **Checkpoint A** — [How to verify this phase is complete]

---

## Phase B — [Phase Name]

> [One-line description]

- [ ] **B.1** — [Specific task description]
- [ ] **B.2** — [Specific task description]
- [ ] 📍 **Checkpoint B** — [Verification criteria]

---

## Phase C — [Phase Name]

> [One-line description]

- [ ] **C.1** — [Specific task description]
- [ ] **C.2** — [Specific task description]
- [ ] 📍 **Checkpoint C** — [Verification criteria]

---

<!-- Add more phases as needed -->

## Phase Y — Testing

> Execute the test plan, verify everything.

- [ ] **Y.1** — Run test plan: happy paths
- [ ] **Y.2** — Run test plan: error cases
- [ ] **Y.3** — Run test plan: edge cases
- [ ] 📍 **Checkpoint Y** — All acceptance criteria met

---

## Phase Z — Documentation & Cleanup

> Code comments, doc updates, self-review.

- [ ] **Z.1** — Inline comments where logic is non-obvious
- [ ] **Z.2** — Update changelog doc with final summary
- [ ] **Z.3** — Update project roadmap progress
- [ ] 📍 **Checkpoint Z** — Self-review all diffs

---

## Ship 🚀

- [ ] All phases complete
- [ ] Final commit with descriptive message
- [ ] Push to feature branch
- [ ] Human approval received
- [ ] Merge to main
- [ ] Push main
- [ ] **Keep the feature branch** — do not delete
- [ ] Create review doc → `review.md`
````

---

### 7. Test Plan Document

**Filename**: `testplan.md`
**Location**: `docs/features/XX-feature-name/testplan.md`
**Purpose**: Define exactly what "working" means — test cases, acceptance criteria, edge cases.

````markdown
# 🧪 Test Plan: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Tasks**: [`tasks.md`](tasks.md)
> **Date**: YYYY-MM-DD

---

## Acceptance Criteria

<!-- The feature is DONE when all of these are true -->

- [ ] [Criterion 1 — specific, measurable]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

---

## Test Cases

### TC-01: [Test Case Name]

| Property | Value |
|---|---|
| **Category** | Happy Path / Error / Edge Case / Security / Performance |
| **Precondition** | [What must be true before this test] |
| **Steps** | 1. [Step] → 2. [Step] → 3. [Step] |
| **Expected Result** | [What should happen] |
| **Status** | ⬜ Not Run / ✅ Pass / ❌ Fail |
| **Notes** | — |

### TC-02: [Test Case Name]

| Property | Value |
|---|---|
| **Category** | ... |
| **Precondition** | ... |
| **Steps** | ... |
| **Expected Result** | ... |
| **Status** | ⬜ Not Run |
| **Notes** | — |

<!-- Add more test cases as needed -->

---

## TC Naming Convention (optional)

<!-- Adopt a naming convention ONLY if you want automated traceability between test cases and test code. This is optional — skip if testing is informal or not applicable. -->

When test cases should be traceable to test code, use a consistent naming pattern:

| Language | Pattern | Example |
|---|---|---|
| Go | `TestTC01_DescribesWhat` | `TestTC01_ReturnsErrorOnInvalidInput` |
| Python | `test_tc01_describes_what` | `test_tc01_returns_error_on_invalid_input` |
| JavaScript | `it("TC-01: describes what")` | `it("TC-01: returns error on invalid input")` |
| Other | `TC-XX` prefix in test name | Adapt to your language's conventions |

To link each test case to its implementation, add a **Test Function** column to the TC table:

| Property | Value |
|---|---|
| **Test Function** | `TestTC01_ReturnsErrorOnInvalidInput` |

---

## Edge Cases

<!-- Unusual inputs, boundary conditions, race conditions -->

| # | Scenario | Expected Behavior |
|---|---|---|
| 1 | [Edge case description] | [How system should handle it] |
| 2 | ... | ... |

## Security Tests

<!-- If not applicable, write "No security-sensitive behavior in this feature" -->

| # | Test | Expected |
|---|---|---|
| 1 | [Unauthorized access attempt] | [Rejected with proper status] |
| 2 | [Malicious input] | [Sanitized / rejected] |

## Performance Considerations

<!-- If not applicable, write "No performance-critical paths in this feature" -->

| Metric | Target | Actual |
|---|---|---|
| [Relevant metric] | [Target value] | — |

---

## Test Summary

<!-- Fill after running all tests -->

| Category | Total | Pass | Fail | Skip |
|---|---|---|---|---|
| Happy Path | — | — | — | — |
| Error Cases | — | — | — | — |
| Edge Cases | — | — | — | — |
| Security | — | — | — | — |
| **Total** | — | — | — | — |

**Result**: ⬜ NOT RUN | ✅ ALL PASS | ❌ HAS FAILURES
````

---

### 8. API Spec Document

**Filename**: `api.md`
**Location**: `docs/features/XX-feature-name/api.md`
**Purpose**: External interface contracts — APIs, CLIs, event schemas, protocol definitions.

> **Create this doc when the feature exposes any external interface**: HTTP/REST endpoints, GraphQL operations, CLI commands, WebSocket events, message queue schemas, gRPC services, or any other contract that consumers depend on.

````markdown
# 🔌 Interface Spec: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Interface Type**: REST API / GraphQL / CLI / WebSocket / gRPC / Event Schema / Other
> **Date**: YYYY-MM-DD

---

<!-- 
Adapt the sections below to your interface type.
The REST API format is shown as a common example.
For other types, replace with appropriate contract definitions:
- GraphQL: queries, mutations, subscriptions, type definitions
- CLI: commands, flags, arguments, exit codes
- WebSocket: event names, payload schemas, connection lifecycle
- gRPC: service definitions, message types
- Events/Messages: event names, payload schemas, routing keys
-->

## Interface Overview

| Method/Command | Path/Name | Auth | Description |
|---|---|---|---|
| `GET` | `/resource` | 🔒 Yes | List resources |
| `POST` | `/resource` | 🔒 Yes | Create resource |

---

## Interface Details

### [Method] [Path/Command]

**Description**: [What this does]
**Auth**: [Required / Optional / None]

**Parameters / Input**:

| Param | Type | Required | Default | Description |
|---|---|---|---|---|
| `param` | type | Yes/No | [default] | [description] |

**Success Response / Output**:

```json
{
  "example": "response"
}
```

**Error Responses / Failure Modes**:

| Status/Code | Response | When |
|---|---|---|
| `400` / Error | `{ "message": "..." }` | [Condition] |
| `401` / Error | `{ "message": "..." }` | [Condition] |

<!-- Repeat for each interface endpoint/command -->
````

---

### 9. Changelog Document

**Filename**: `changelog.md`
**Location**: `docs/features/XX-feature-name/changelog.md`
**Purpose**: Running log of what actually happened during implementation — changes, deviations, decisions, session notes.

````markdown
# 📝 Changelog: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Branch**: `feature/XX-feature-name`
> **Started**: YYYY-MM-DD
> **Completed**: —

---

## Session Notes

<!-- Add session handoff notes here (see AI Agent Protocol in mastery.md) -->

### Session Note — YYYY-MM-DD
- **Who**: [Human / AI Agent Name]
- **Duration**: [Approximate time or "async"]
- **Worked On**: [Brief description]
- **Stopped At**: [Exact task ID]
- **Blockers**: [Any issues, or "None"]
- **Next Steps**: [What to pick up next]

---

## Log

<!-- Add entries as you work. Most recent first. -->

### YYYY-MM-DD

- **[Added/Changed/Fixed/Removed]**: [Description of what happened]
  - Detail or context if needed
  - Related file: `path/to/file`

### YYYY-MM-DD

- **[Added]**: [Description]

---

## Deviations from Plan

<!-- Things that went differently than the architecture/tasks docs planned -->

| What Changed | Original Plan | What Actually Happened | Why |
|---|---|---|---|
| [Component] | [Planned approach] | [Actual approach] | [Reason for change] |

## Key Decisions Made During Build

<!-- Decisions that were NOT in the discussion/architecture docs -->

| Decision | Context | Date |
|---|---|---|
| [Decision] | [Why it came up and what was chosen] | YYYY-MM-DD |
````

---

### 10. Review Document

**Filename**: `review.md`
**Location**: `docs/features/XX-feature-name/review.md`
**Purpose**: Post-implementation retrospective — learn from what just happened.

````markdown
# 🪞 Review: [Feature Name]

> **Feature**: `XX` — [Feature Name]
> **Branch**: `feature/XX-feature-name`
> **Merged**: YYYY-MM-DD
> **Time Spent**: [Estimate — hours or days]

---

## Result

**Status**: ✅ Shipped | ⚠️ Shipped with known issues | ❌ Abandoned

**Summary**: [One paragraph — what was built and delivered]

---

## What Went Well ✅

<!-- Patterns, approaches, or decisions that worked great -->

- [Thing that worked well]
- [Thing that worked well]

## What Went Wrong ❌

<!-- Problems, blockers, time sinks, bugs -->

- [Problem] — [Impact] — [How it was resolved]
- [Problem] — [Impact] — [How it was resolved]

## What Was Learned 📚

<!-- New knowledge, techniques, or insights gained -->

- [Lesson learned]
- [Lesson learned]

## What To Do Differently Next Time 🔄

<!-- Concrete changes to apply to future features -->

- [Change]
- [Change]

## Metrics

| Metric | Value |
|---|---|
| Tasks planned | XX |
| Tasks completed | XX |
| Tests planned | XX |
| Tests passed | XX |
| Deviations from plan | XX |
| Commits on branch | XX |

## Follow-ups

<!-- Anything spawned from this feature that needs future attention -->

- [ ] [Follow-up item]
- [ ] [Follow-up item]
````

### 11. Lightweight Feature Document

Use this template when a feature meets ALL lightweight eligibility criteria (see [Lightweight Feature Variant](#-lightweight-feature-variant)). This single document replaces the six standard feature docs.

````markdown
# Feature #XX — [Feature Name] (Lightweight)

**Status**: 💬 IN PROGRESS | 🟢 COMPLETE
**Type**: Docs-only | Config-only | Trivial change
**Date**: YYYY-MM-DD
**Branch**: `feature/XX-feature-name`

---

## Summary

<!-- WHAT is changing and WHY — 2-3 sentences max -->

## Scope & Approach

<!-- WHAT files change, HOW — keep brief. No multi-paragraph design docs. -->

| File | Change |
|---|---|
| `path/to/file` | Description of change |

## Tasks

- [ ] Task 1
- [ ] Task 2
- [ ] ...

### Verification

<!-- HOW you'll confirm the change works — manual check, visual inspection, test run, etc. -->

- [ ] Verification step 1
- [ ] Verification step 2

## Changelog

<!-- Log entries as work progresses -->

| Date | Entry |
|---|---|
| YYYY-MM-DD | Description of what was done |

## Reflection

<!-- Fill after merge — brief: what went well, anything learned -->

- **Went well**: ...
- **Learned**: ...
- **Follow-ups**: None | [list any]
````

### 12. AGENTS.md (AI Agent Orientation)

Every Mastery project should have an `AGENTS.md` at the **project root**. This is the first file AI agent tools read when entering a project — it provides quick orientation so agents know what the project is, how it's structured, and where to find the full protocol.

**When to create**: During Project Initialization, after `project-context.md` is created (Step 3.5).
**Source of truth**: Derived from `project-context.md` + `mastery.md` conventions. Not independently authored.
**When to update**: Whenever `project-context.md` changes (project structure, conventions, scope).
**Location**: Project root (NOT inside `docs/`) — AI tools scan the root for this file.

````markdown
# AGENTS.md

[One-paragraph project summary: what it is, what it does, what problem it solves.]

## Project Structure

```
[Project tree — copy from project-context.md, annotate key files/folders]
```

## Getting Started (for AI Agents)

Read docs in this exact order (matches the AI Agent Protocol in `docs/mastery.md`):

1. `docs/mastery-compact.md` — Framework rules (compact — all rules, no templates)
2. `docs/project-discussion.md` — Understand WHY the project exists and key decisions
3. `docs/project-context.md` — Understand WHAT the project is (formalized)
4. `docs/project-roadmap.md` — Understand WHERE the project stands
5. `docs/features/` (active) — Understand the current feature state

> Need a document template? Load it from the full `docs/mastery.md` — search for the specific template heading.

To find current work:
1. Check `docs/project-roadmap.md` for features marked 🟡 IN PROGRESS
2. Open that feature's folder: `discussion → architecture → tasks → changelog`
3. In `tasks.md`, find the last checked checkbox — that's where work stopped
4. In `changelog.md`, read the latest Session Note for context

## Key Rules

- **Docs before code** — discuss, design, and plan before building. Never skip stages.
- **Feature branches only** — all work happens on `feature/XX-name` branches, never on `main`.
- **Never delete branches** — kept forever as historical reference.
- **Human approval required** for: merging to main, modifying architecture after finalization, changing `project-context.md`, reordering the roadmap, adding dependencies.
- **AI agents CAN** autonomously: read docs, write code within active tasks, check off tasks, log changelog entries, create commits, push to feature branches.

See the full Autonomy Boundaries table in `docs/mastery.md` → AI Agent Protocol section.

## Conventions

**Branches**: `feature/XX-feature-name` from `main` (e.g., `feature/01-auth`)

**Commits**: `type(scope): short description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `hotfix`
- Scope: feature name or module (e.g., `auth`, `api`, `docs`)

**File naming**: kebab-case for all files (e.g., `project-context.md`, `process-overrides.md`)

**Markdown style**: ATX headings (`#`), fenced code blocks (triple backtick)

## Full Protocol

The complete AI Agent Protocol — including context loading order, autonomy boundaries, session handoff protocol, and communication style rules — is defined in:

**`docs/mastery.md` → Section: 🤖 AI Agent Protocol**
````

### 13. SKILL.md (AI Agent Skill)

SKILL.md packages a project's domain knowledge as a discoverable skill for AI agent tools. While AGENTS.md tells agents *how to work* in a project, SKILL.md tells agents *what expertise this project offers* — domain patterns, specialized workflows, or conventions that agents can invoke.

**When to create**: When the project has domain-specific knowledge worth packaging (specialized workflows, domain rules, coding patterns).
**Location**: Project root (alongside AGENTS.md) — AI tools scan the root for skill files.
**Format**: Markdown with YAML frontmatter for tool discovery.

````markdown
---
name: [skill-name]
description: [One-sentence description of what this skill teaches AI agents]
applyTo: [glob pattern for files this skill applies to, e.g. "**/*.md" or "**"]
---

# [Skill Name]

[2-3 sentence description of the domain knowledge this skill provides. What does it teach? What patterns does it encode?]

## When to Use

- [Scenario 1 where this skill applies]
- [Scenario 2 where this skill applies]
- [Scenario 3 where this skill applies]

## When NOT to Use

- [Scenario where this skill does NOT apply]
- [Scenario where a different approach is better]

## Key Patterns

[Document the domain-specific patterns, conventions, or workflows that define this skill. Be specific and actionable — agents will use this as a reference.]

## References

- [Link to detailed docs, specs, or examples within the project]
````

### 14. llms.txt (Machine-Readable Summary)

llms.txt provides a concise, machine-readable summary of the project for LLMs encountering it via web, API, or file system. It follows the [llms.txt convention](https://llmstxt.org/) — a structured text file that gives LLMs instant context about what a project is and where to find key resources.

**When to create**: When the project is publicly accessible and benefits from machine discoverability (open source projects, public APIs, documentation sites).
**Location**: Project root (or served at `/.well-known/llms.txt` for web projects).
**Format**: Markdown-compatible plain text with structured sections.

````markdown
# [Project Name]

> [One-sentence project description]

[2-3 sentence expanded summary. What does the project do? Who is it for? What problem does it solve?]

## Docs

- [Document Name](path/to/doc.md): [Brief description]
- [Document Name](path/to/doc.md): [Brief description]
- [Document Name](path/to/doc.md): [Brief description]

## Optional

- [Additional Resource](path/or/url): [Brief description]
- [Additional Resource](path/or/url): [Brief description]
````

> **Tip**: Keep llms.txt concise — under 50 lines. For projects with extensive documentation, link to a `llms-full.txt` with expanded content.

---

### 15. Summary Document (Retroactive Feature)

The summary document captures completed work retroactively during mid-project adoption. Instead of creating full lifecycle docs for past features, a single summary preserves what matters.

**When to create**: During [mid-project adoption](#-adopting-mastery-mid-project) only — for features completed before Mastery was adopted.
**Location**: `docs/features/XX-feature-name/summary.md` (only file in the folder)
**Purpose**: Retroactive record of what was built, not a plan for what to build.

````markdown
# 📋 Summary — [Feature Name]

> **Feature**: #XX — [Feature Name]
> **Status**: ✅ Complete (Retroactive)
> **Approximate Date Range**: YYYY-MM – YYYY-MM

## What Was Built

[2-4 sentence synopsis of what this feature delivered. What does it do? What problem did it solve?]

## Key Decisions

- **[Decision 1]**: [What was decided and why — reconstructed from code, commits, or team knowledge]
- **[Decision 2]**: [What was decided and why]
- **[Decision 3]**: [What was decided and why]

## Files & Components Affected

- `path/to/file.ext` — [What this file does / what changed]
- `path/to/directory/` — [What this directory contains]
- `path/to/other.ext` — [What this file does / what changed]

## Dependencies

- **Depends on**: [What this feature required to exist first, or "None"]
- **Enables**: [What subsequent features this unlocked, or "N/A"]

## Notes

[Any additional context worth preserving — known limitations, technical debt, things the team wishes they'd done differently. Optional.]
````

> **Keep it honest**: Summary docs capture what actually happened, not an idealized version. If a decision was made for expediency rather than best practice, say so — future developers benefit from that honesty.

---

### 16. Project Changelog Document

**Filename**: `project-changelog.md`
**Location**: `docs/project-changelog.md`
**Purpose**: High-level record of all shipped features, hotfixes, and significant changes — the project's history at a glance. Unlike per-feature changelogs (which track implementation details), this captures WHAT shipped and WHEN.
**Created**: After the first feature ships. Updated every time a feature is merged or a hotfix is applied.

````markdown
# 📋 Project Changelog

> **Project**: [Project Name]
> **Format**: Based on [Keep a Changelog](https://keepachangelog.com/)
> **Last Updated**: YYYY-MM-DD

---

## [Unreleased]

<!-- Features merged to main but not yet released/deployed -->

### Added
### Changed
### Fixed
### Removed

---

<!-- Copy this block for each version or release -->

## [X.Y.Z] — YYYY-MM-DD

### Added
- **Feature #XX — Feature Name** — Brief description of what was added

### Changed
- **Feature #XX — Feature Name** — Brief description of what changed

### Fixed
- **Hotfix — Description** — What was fixed and why

### Removed
- **Feature #XX — Feature Name** — What was removed and why
````

> **Granularity**: One entry per feature merge or hotfix — not per-commit. Group entries by version when your project uses versioned releases. If your project deploys continuously, group by date or milestone instead.

---

## 🌿 Git Branching Strategy

```
main ─────●────●────●────●────●────●────●──────▶
           \       ↗  \       ↗  \       ↗
            ●─●─●─●    ●─●─●─●    ●─●─●─●
           feature/     feature/    feature/
           01-name      02-name     03-name
           (kept)       (kept)      (kept)

           hotfix/      ← abbreviated lifecycle
           fix-name
           (kept)
```

### Branch Rules

| Rule | Detail |
|---|---|
| **main** | Always deployable. Only receives merges from feature/hotfix branches. |
| **feature/XX-name** | Created from latest `main`. One branch per feature. |
| **hotfix/description** | Created from latest `main`. For critical fixes only. |
| **Never delete** | All branches are kept forever as historical reference. |
| **One feature at a time** | Default recommendation. See "Parallel Features" section for exceptions. |

### Git Commands Cheat Sheet

```bash
# Start a new feature
git checkout main
git pull origin main
git checkout -b feature/XX-feature-name

# Work on feature (repeat as needed)
git add .
git commit -m "feat(scope): description"

# Push branch
git push origin feature/XX-feature-name

# Merge to main (when feature complete & tested — human approved)
git checkout main
git pull origin main
git merge feature/XX-feature-name
git push origin main

# Start a hotfix
git checkout main
git pull origin main
git checkout -b hotfix/brief-description

# Merge hotfix (human approved)
git checkout main
git merge hotfix/brief-description
git push origin main
```

> **Note**: These commands use `origin` as the remote name, which is the Git default. If your project uses a different remote name, substitute accordingly.

---

## ✍️ Commit Message Convention

### Format

```
type(scope): short description

[optional body — explain WHY, not WHAT]
[optional footer — references, breaking changes]
```

### Types

| Type | When |
|---|---|
| `feat` | New feature or functionality |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, whitespace — no logic change |
| `refactor` | Code restructure — no behavior change |
| `test` | Adding or updating tests |
| `chore` | Build, config, tooling, dependencies |
| `perf` | Performance improvement |
| `hotfix` | Critical production fix via hotfix workflow |

### Scope

The scope is the feature name or module affected. Examples: `auth`, `routing`, `user-dashboard`, `api`, `cli`, `core`.

### Examples

```
feat(auth): add login controller with session management
fix(routing): resolve domain filter matching for www subdomain
docs(mastery): add test plan template
refactor(user): extract validation into dedicated service
test(contact): add form submission edge case tests
chore(deps): update framework to latest version
hotfix(payments): fix decimal rounding in invoice calculation
```

---

## 🔀 Parallel Features

The default recommendation is **one feature at a time** — finish and merge before starting the next. This keeps things simple and avoids merge conflicts.

However, real projects sometimes need parallel work. Here's how to handle it safely.

### When Parallel Work Is Safe

- Features touch completely different files and modules
- Features have no shared dependencies
- Both features branch from the same `main` commit
- Team members (human or AI) are assigned to separate features

### When Parallel Work Is Risky

- Features modify the same files
- One feature depends on another that isn't merged yet
- Shared data models or schemas are being changed by both

### Parallel Feature Rules

1. **Always branch from latest `main`** — both features start from the same baseline
2. **Communicate actively** — if you discover overlap, stop and coordinate
3. **Merge the simpler/smaller feature first** — reduces conflict surface
4. **Rebase the second feature after first merge** — `git rebase main` on the remaining branch
5. **Re-run tests after rebase** — conflicts may introduce subtle bugs
6. **Document in changelog** — note that parallel work occurred and how conflicts were resolved

### Conflict Resolution Protocol

If merge conflicts arise:

1. The feature being merged second is responsible for resolving conflicts
2. After resolution, re-run the FULL test plan for that feature
3. Log the conflict and resolution in the changelog
4. If the conflict changes architecture, update the architecture doc

---

## 📚 References Directory

The `docs/references/` directory holds standalone documents that don't belong to a specific feature but are important for the project.

### What Goes Here

| Document Type | Naming Convention | Purpose |
|---|---|---|
| **Architecture Decision Records** | `ADR-NNN-title.md` | Record significant architectural decisions with context and rationale |
| **Style Guide** | `style-guide.md` | Coding conventions, formatting rules, naming patterns |
| **Glossary** | `glossary.md` | Domain-specific terms and their definitions |
| **Hotfix Log** | `hotfix-log.md` | Record of all hotfixes applied outside the normal feature lifecycle |
| **External Specs** | `spec-name.md` | Third-party API docs, protocol specs, or standards being followed |
| **Onboarding Guide** | `onboarding.md` | How to get started as a new contributor (human or AI) |
| **Runbooks** | `runbook-topic.md` | Operational procedures (deployment, rollback, incident response) |
| **Process Overrides** | `process-overrides.md` | Team-specific adjustments to the Mastery framework (never edit mastery.md directly) |

### ADR Format (Quick Reference)

```markdown
# ADR-NNN: [Title]

**Date**: YYYY-MM-DD
**Status**: Proposed | Accepted | Deprecated | Superseded by ADR-NNN

## Context
[What is the issue or decision that needs to be made?]

## Decision
[What was decided?]

## Consequences
[What are the positive and negative outcomes of this decision?]
```

### Rules

- Reference docs are NOT tied to feature numbers
- They can be created at any time, not just during a feature lifecycle
- They should be linked from relevant feature docs when applicable
- Keep them up to date — stale reference docs are worse than no docs

---

## 🔧 Cross-Tool Configuration

Many AI coding tools look for their own configuration files. Rather than maintaining these independently, derive them from your existing Mastery docs — making Mastery the single source of truth for how agents work in your project.

### Source Mapping

| Tool | Config File | Derive From | Key Content to Include |
|---|---|---|---|
| **Cursor** | `.cursorrules` | project-context.md, AGENTS.md | Tech stack, conventions, project rules, coding patterns |
| **Claude Code** | `CLAUDE.md` | AGENTS.md, project-context.md | Project overview, structure, key rules, build/test commands |
| **Windsurf** | `.windsurfrules` | project-context.md, AGENTS.md | Tech stack, conventions, project rules |
| **GitHub Copilot** | `.github/copilot-instructions.md` | project-context.md, process-overrides.md | Coding conventions, project constraints, style rules |
| **Kiro** | `.kiro/steering.md` | project-context.md, AGENTS.md | Project structure, tech stack, development workflow |

### Derivation Principles

1. **Single source of truth** — Mastery docs are the source. Tool configs are derived artifacts, not independently authored.
2. **Regenerate, don’t edit** — When project-context.md or AGENTS.md changes, regenerate tool configs rather than editing them directly.
3. **Include only what the tool needs** — Each tool has different strengths. Cursor needs coding rules; Claude needs project overview; Copilot needs style guidance. Don’t dump everything into every config.
4. **Keep configs in version control** — Commit generated configs alongside the source docs so team members get them automatically.
5. **Document the derivation** — Add a comment at the top of each generated config noting it was derived from Mastery docs and when.

### MCP Alternative

Projects with a Mastery MCP server can expose project context programmatically — AI tools that support MCP can query project state directly instead of reading static config files. See [MCP-Enhanced Workflow](#mcp-enhanced-workflow) for details.

---

## 🔁 Resuming Work

Whether you're a human returning after a break or an AI agent starting a new session, follow this protocol to pick up where things left off.

### For AI Agents

1. Read `docs/mastery-compact.md` — reload framework rules (mandatory every session)
2. Read `docs/project-context.md` — refresh on what this project is
3. Read `docs/project-roadmap.md` — find the feature marked 🟡 IN PROGRESS
4. Open that feature's `changelog.md` — read the latest Session Note
5. Open that feature's `tasks.md` — find the last checked checkbox
6. Read the architecture doc if you need to understand the design
7. Continue from the exact task where work stopped
8. When you start working, add a new Session Note to the changelog

### For Humans

1. Check `project-roadmap.md` for current status
2. Open the active feature's `tasks.md` — see what's done and what's next
3. Check the `changelog.md` for recent session notes and decisions
4. If an AI agent was working, review its commits: `git log --oneline -20`
5. Continue from where things left off

### After a Long Break (> 1 week)

1. `git pull origin main` — sync with any changes
2. Check if the feature branch needs rebasing: `git log main..HEAD --oneline`
3. Re-read the discussion and architecture docs — refresh your mental model
4. Run existing tests to confirm nothing is broken
5. Then resume normal work

---

## ✅ Definition of Done

A feature is considered DONE when ALL of the following are true:

### Feature Level

- [ ] All tasks in the tasks doc are checked off
- [ ] All acceptance criteria in the test plan are met
- [ ] All test cases pass (no ❌ failures)
- [ ] Changelog is up to date with all changes and deviations
- [ ] Code is committed and pushed to the feature branch
- [ ] Human has reviewed and approved the merge
- [ ] Feature is merged to main
- [ ] Review doc is completed (reflection done)
- [ ] Project roadmap is updated (feature marked 🟢 Complete)

### Code Level

- [ ] Code runs without errors
- [ ] No known bugs introduced
- [ ] Code follows project conventions (see `project-context.md`)
- [ ] No hardcoded secrets, credentials, or environment-specific values
- [ ] Error handling is in place for expected failure modes

### Documentation Level

- [ ] All feature docs are complete and accurate
- [ ] Changelog reflects what actually happened (not just what was planned)
- [ ] Any deviations from architecture are documented with rationale
- [ ] Project changelog is updated with shipped feature entry

---

## ⚡ Quick Reference

### Project Initialization (One Time)

```
1.  Create  docs/mastery.md                              (copy full framework)
2.  Create  docs/mastery-compact.md                      (copy compact variant)
3.  Create  docs/project-discussion.md                   (discuss the project)
4.  Discuss until fully understood → mark COMPLETE
5.  Create  docs/project-context.md                      (formalize from discussion)
6.  Create  docs/project-roadmap.md                      (plan the features)
7.  Create  docs/features/                               (empty directory)
8.  Create  docs/references/                             (empty directory)
9.  Start Feature 01                                     (begin the lifecycle)
```

### Mid-Project Adoption (Existing Codebase)

```
1.  Move existing docs to docs/_archive/                 (preserve, don't delete)
2.  Create  docs/mastery.md                              (copy this framework)
3.  Create  docs/project-discussion.md                   (reconstruct from codebase + history)
4.  Mark discussion COMPLETE                             (decisions already made)
5.  Create  docs/project-context.md                      (formalize current state)
6.  Create  AGENTS.md                                    (at project root)
7.  Create  docs/features/XX/summary.md                  (one per completed feature)
8.  Create  docs/project-roadmap.md                      (retroactive ✅ + future 🔴)
9.  Start next feature normally                          (full lifecycle from here)
```

### Starting a New Feature (Step by Step)

```
1.  Check project-roadmap.md → identify next feature number
2.  Create  docs/features/XX-feature-name/               (create feature folder)
3.  Create  docs/features/XX-feature-name/discussion.md   (discuss)
4.  Discuss until fully understood → mark COMPLETE
5.  Create  docs/features/XX-feature-name/architecture.md (design)
6.  Finalize architecture → mark FINALIZED
7.  Create  docs/features/XX-feature-name/tasks.md        (plan)
8.  Create  docs/features/XX-feature-name/testplan.md     (define done)
9.  Create  docs/features/XX-feature-name/api.md          (if has external interfaces)
10. Create  docs/features/XX-feature-name/changelog.md    (empty, ready)
11. Create  git branch: feature/XX-feature-name           (build)
12. Execute tasks, log in changelog                       (build)
13. Run test plan                                         (verify)
14. Human approval → merge to main, keep branch           (ship)
15. Create  docs/features/XX-feature-name/review.md       (reflect)
16. Update  project-roadmap.md progress tracker           (track)
```

> **Lightweight path**: If the feature meets ALL lightweight eligibility criteria, replace steps 3–15 with a single `lightweight.md`. See [Lightweight Feature Variant](#-lightweight-feature-variant).

### Document Quick Reference

| Need to... | Open this doc |
|---|---|
| Understand the process (full + templates) | `docs/mastery.md` (this file) |
| Understand framework rules (compact) | `docs/mastery-compact.md` |
| See the project discussion | `docs/project-discussion.md` |
| See what we're building | `docs/project-context.md` |
| See what's next | `docs/project-roadmap.md` |
| Start a feature | `docs/features/XX-feature-name/discussion.md` |
| Design a feature | `docs/features/XX-feature-name/architecture.md` |
| Plan implementation | `docs/features/XX-feature-name/tasks.md` |
| Define test cases | `docs/features/XX-feature-name/testplan.md` |
| Spec an interface | `docs/features/XX-feature-name/api.md` |
| Log build progress | `docs/features/XX-feature-name/changelog.md` |
| Reflect on delivery | `docs/features/XX-feature-name/review.md` |
| Record a big decision | `docs/references/ADR-NNN-title.md` |
| Log a hotfix | `docs/references/hotfix-log.md` |
| See project history | `docs/project-changelog.md` |

### AI Agent Quick Start

```
1. Read mastery-compact.md (mandatory every session — compact rules, no templates)
2. Read project-discussion.md (if you need WHY context)
3. Read project-context.md
4. Read project-roadmap.md
5. Find the 🟡 IN PROGRESS feature
6. Read its changelog (latest session note)
7. Read its tasks (find where work stopped)
8. Continue from there
9. Log a session note when done
```

---

> *"Think. Design. Plan. Build. Ship. Reflect. Repeat."*

---

*Mastery Framework v3.1*
*Works for any project. Any language. Any stack. Any team. Human or AI.*
