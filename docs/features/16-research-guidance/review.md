# 🪞 Review: Research Guidance

> **Feature**: `16` — Research Guidance
> **Branch**: `feature/16-research-guidance`
> **Merged**: 2026-03-21
> **Time Spent**: ~1 session

---

## Result

**Status**: ✅ Shipped

**Summary**: Added structured research guidance to the Mastery framework via a hybrid approach — a "Research & Prior Art" section in both Discussion templates (always available) plus a conditional `research.md` template (#17) for deep multi-topic research. Updated all ecosystem tables, Quick Reference, Naming Rules, mastery-compact.md, and bumped version to v3.4.0.

---

## What Went Well ✅

- Hybrid approach (Option C) was the right call — keeps framework lean while providing structure when needed
- Cross-check before build caught 2 gaps (task count, Naming Rules table) that would have been missed
- Clean fast-forward merge — no conflicts
- All 13 touch points across mastery.md updated consistently in one pass

## What Went Wrong ❌

- Quick Reference step renumbering introduced a duplicate step 11 — caught and fixed during cross-check
- Initial task count was wrong (17 vs actual 15) — header math didn't account for checkpoints not being tasks
- Architecture doc initially missed 2 change locations (Naming Rules table, version bump) — caught during cross-check

## What Was Learned 📚

- Cross-checks before build are valuable even for docs-only features — they catch structural gaps
- When adding a new conditional doc type, there are ~13 locations to update across mastery.md + compact — worth having a checklist
- Template numbering at the end (after #16) avoids any renumbering risk

## What To Do Differently Next Time 🔄

- Include version bump planning in the architecture doc from the start — it was a gap caught in cross-check
- Count tasks more carefully when writing the header — exclude checkpoints from the count

## Metrics

| Metric | Value |
|---|---|
| Tasks planned | 21 |
| Tasks completed | 21 |
| Tests planned | 9 TC + 4 edge |
| Tests passed | All (manual verification) |
| Deviations from plan | 2 (added Naming Rules + version bump tasks after cross-check) |
| Commits on branch | 2 |

## Follow-ups

- [ ] Consider adding `research.md` to the docs copy in this repo's own `docs/mastery.md`
