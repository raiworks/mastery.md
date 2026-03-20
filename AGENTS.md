# AGENTS.md

This repository contains **MASTERY.md** — a universal, tech-agnostic development process framework distributed as a single Markdown file. It defines a complete software lifecycle: Discuss → Design → Plan → Approve → Build → Ship → Reflect.

**This is NOT a code project.** The product is `mastery.md` — a single file that other projects copy into their `docs/` folder and follow.

## Project Structure

```
MASTERY.md/
├── mastery.md          # THE PRODUCT — the full framework file (editable here, read-only in consuming projects)
├── mastery-compact.md  # COMPACT VARIANT — AI-optimized (rules only, no templates)
├── AGENTS.md           # This file — AI agent orientation
├── README.md           # Human-oriented landing page
├── LICENSE             # MIT
├── CHANGELOG.md        # Framework version history (semver)
├── .gitignore          # Ignores docs/ and temp/
└── docs/               # GITIGNORED — internal dev docs (exists locally only)
    ├── mastery.md              # Copy of framework for self-reference
    ├── project-discussion.md   # WHY — project-level decisions
    ├── project-context.md      # WHAT — formalized project identity
    ├── project-roadmap.md      # WHERE — feature ordering and progress
    ├── features/               # Per-feature lifecycle docs
    │   └── XX-feature-name/    # discussion, architecture, tasks, testplan, changelog
    ├── references/             # Process overrides, specs
    └── research/               # Landscape research (16 tools/protocols analyzed)
```

> **Important**: The `docs/` folder is gitignored — it contains internal development docs used to build the framework itself. These files exist locally but are NOT in git history. If you're on a fresh clone, only the root-level files are present.

## Getting Started (for AI Agents)

Read docs in this exact order (matches the AI Agent Protocol in `mastery.md`):

1. `mastery-compact.md` — Framework rules (compact — all rules, no templates; ~5k tokens vs ~25k)
2. `docs/project-discussion.md` — Understand WHY the project exists and key decisions
3. `docs/project-context.md` — Understand WHAT the project is (formalized)
4. `docs/project-roadmap.md` — Understand WHERE the project stands
5. `docs/features/` (active) — Understand the current feature state

> **Note**: In this repo, the framework lives at root (`mastery.md` / `mastery-compact.md`) rather than `docs/` because it IS the product. Load the compact variant for rules; load the full file only when you need a specific template.
> **Need a template?** Load it from `mastery.md` — search for the heading (e.g., "### 4. Discussion Document").

To find current work:
1. Check `docs/project-roadmap.md` for features marked 🟡 IN PROGRESS
2. Open that feature's folder: `discussion → architecture → tasks → changelog`
3. In `tasks.md`, find the last checked checkbox — that's where work stopped
4. In `changelog.md`, read the latest Session Note for context

## Key Rules

- **`mastery.md` is the product** — this repo develops it. In consuming projects, the copy at `docs/mastery.md` is read-only.
- **Docs before code** — discuss, design, and plan before building. Never skip stages.
- **Feature branches only** — all work happens on `feature/XX-name` branches, never on `main`.
- **Never delete branches** — kept forever as historical reference.
- **Human approval required** for: merging to main, modifying architecture after finalization, changing `project-context.md`, reordering the roadmap, adding dependencies.
- **AI agents CAN** autonomously: read docs, write code within active tasks, check off tasks, log changelog entries, create commits, push to feature branches.

See the full Autonomy Boundaries table in `mastery.md` → AI Agent Protocol section.

## Conventions

**Branches**: `feature/XX-feature-name` from `main` (e.g., `feature/02-agents-md`)

**Commits**: `type(scope): short description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `hotfix`
- Scope: feature name or module (e.g., `auth`, `framework`, `mastery`, `readme`)

**File naming**: kebab-case for all files (e.g., `project-context.md`, `process-overrides.md`)

**Markdown style**: ATX headings (`#`), fenced code blocks (triple backtick)

## Important Notes

- This project uses its own framework to develop itself (Mastery develops Mastery)
- The framework is **v3.3.0** — actively being improved
- The `docs/` folder follows the full Mastery lifecycle process internally
- Process customizations go in `docs/references/process-overrides.md`, not in `mastery.md`
- When resuming work, always read `mastery-compact.md` first (AI Agent Protocol)

## Full Protocol

The complete AI Agent Protocol — including context loading order, autonomy boundaries, session handoff protocol, and communication style rules — is defined in:

**`mastery.md` → Section: 🤖 AI Agent Protocol**
