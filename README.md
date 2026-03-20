# MASTERY.md

**Current**: v3.4.0 · [Changelog](CHANGELOG.md) · [Website](https://masterymd.com)

> A universal, tech-agnostic development process framework — one Markdown file that defines how software projects should be structured, discussed, designed, planned, built, shipped, and reflected upon.

## What Is This?

**MASTERY.md** is a single Markdown file (`mastery.md`) that codifies the entire development lifecycle for any software project. Copy it into your project's `docs/` folder and follow its process — whether you're a solo developer, a small team, or an AI coding agent.

It comes in **two variants**:

| Variant | File | Tokens | Best For |
|---|---|---|---|
| **Full** | `mastery.md` | ~25k | Complete reference with all 17 document templates, hotfix workflows, and advanced guidance |
| **Compact** | `mastery-compact.md` | ~5k | AI agent context loading — all rules and lifecycle stages, no templates |

Both files are the same framework. The compact variant drops templates and rarely-needed reference sections to save ~80% of tokens. AI agents load the compact file every session and pull specific templates from the full file only when creating new documents.

It provides:

- **7-stage lifecycle**: Discuss → Design → Plan → Approve → Build → Ship → Reflect
- **Document templates**: Project discussion, context, roadmap, feature specs, task lists, and more
- **AI Agent Protocol**: Rules for how AI assistants should read context, make decisions, and ask for help
- **Git conventions**: Branching strategy, commit message format, and merge workflow
- **Session continuity**: Structured docs that let any human or AI pick up where work left off

## Why?

AI coding agents are powerful but directionless without process. They'll start coding without understanding the project, repeat mistakes, and lose context between sessions. Human developers face similar problems at smaller scale.

Mastery solves this by giving every project the same structured process — documented in a single file that both humans and AI agents can read and follow.

**Zero dependencies.** Pure Markdown. No tooling, no runtime, no packages — works with any language, any stack, any editor.

## With Mastery vs Without

| Aspect | Without Mastery | With Mastery |
|---|---|---|
| **Project start** | Jump straight into code; goals live in someone's head | Structured discussion doc captures the why, what, and constraints before a line is written |
| **Context between sessions** | AI agents (and humans) lose track — repeat questions, duplicate work | Docs act as persistent memory; anyone picks up exactly where work stopped |
| **Feature planning** | Ad-hoc tickets or mental checklists | Each feature gets a lifecycle folder: discussion → architecture → tasks → test plan → changelog |
| **AI agent behavior** | Agents guess at conventions, hallucinate structure, skip steps | Agent Protocol defines what to read, what to decide, and when to ask for help |
| **Git workflow** | Inconsistent branch names, vague commits | Defined branching strategy and commit format baked into the process |
| **Design decisions** | Lost in chat threads or never recorded | Architecture docs with explicit rationale — searchable, reviewable, permanent |
| **Onboarding** | "Read the code" or a stale wiki | New contributors read the docs folder and understand the full project state in minutes |
| **Session handoff** | "Where were we?" every time | Changelog session notes and task checkboxes show exactly what happened and what's next |
| **Process consistency** | Every project reinvents its workflow | One file, same lifecycle, any tech stack |
| **Tooling required** | CI configs, project management apps, custom templates | Pure Markdown — zero dependencies, works everywhere |

## Quick Start

1. **Copy** `mastery.md` and `mastery-compact.md` into your project's `docs/` directory
2. **Read** the compact file to understand rules and lifecycle (or full file for templates)
3. **Create** `docs/project-discussion.md` using the embedded template
4. **Follow** the lifecycle: Discuss → Design → Plan → Approve → Build → Ship → Reflect

```
your-project/
├── docs/
│   ├── mastery.md              # Full framework (read-only — never edit this)
│   ├── mastery-compact.md      # Compact variant for AI agents (read-only)
│   ├── project-discussion.md   # First: discuss what you're building
│   ├── project-context.md      # Then: formalize the project identity
│   ├── project-roadmap.md      # Then: plan the feature order
│   └── features/               # Per-feature lifecycle docs
│       └── 01-feature-name/
├── src/                        # Your code
└── ...
```

## Key Principles

- **Read-only framework**: Never edit `mastery.md` in your project. Customizations go in `docs/references/process-overrides.md`.
- **Docs before code**: Discuss, design, and plan before building. This saves time, not costs it.
- **One source of truth**: Each document has a clear purpose. No duplicated or conflicting information.
- **AI-native**: Every document is designed to be loaded by AI agents as context for productive work.

## Adopting Mastery

| Step | Action |
|---|---|
| 1 | Copy `mastery.md` and `mastery-compact.md` to `docs/` in your project |
| 2 | Create `.gitignore` rules if you want docs private |
| 3 | Follow the Project Initialization flow in the framework |
| 4 | When Mastery updates, replace both copies with the new versions |

## Versioning

This framework uses [semantic versioning](https://semver.org/):

- **Major** (v2 → v3): Breaking changes to process, templates, or structure
- **Minor** (v3.0 → v3.1): New features, templates, or guidance added
- **Patch** (v3.0.0 → v3.0.1): Fixes, clarifications, typo corrections

See [CHANGELOG.md](CHANGELOG.md) for version history.

## License

[MIT](LICENSE) — use freely in any project, commercial or open source.

## Mastery MCP Server

An optional companion tool that gives AI agents native access to Mastery docs through the [Model Context Protocol](https://modelcontextprotocol.io/).

**14 tools** for reading project context, roadmaps, features, tasks, test plans, reviews, and more.
**11 resources** for direct document access via `mastery://` URIs — including `mastery://mastery-compact` for the compact variant.

The server watches your `docs/` folder and serves structured, parsed content — so AI agents can query your project state without reading raw files.

- **Repository**: [github.com/raiworks/mastery-mcp-server](https://github.com/raiworks/mastery-mcp-server)
- **Details**: [masterymd.com/mcp-server](https://masterymd.com/mcp-server)

Works with VS Code (GitHub Copilot), Claude Desktop, Cursor, and any MCP-compatible client.

## Contributing

Contributions are welcome. Please open an issue to discuss proposed changes before submitting a pull request.
