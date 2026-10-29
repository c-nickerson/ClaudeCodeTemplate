---
name: wrap-up
description: End-of-session wrap-up. Updates .claude/memory/PROJECT.md with progress, decisions and next steps. Use when the user runs /wrap-up or says "wrap up".
---

# Wrap up the session

Update `.claude/memory/PROJECT.md` so the next session can pick up straight away.

## 1. See what happened
- Look back over this conversation.
- Run `git status` and `git log --oneline -15` to see what changed.

## 2. Update `.claude/memory/PROJECT.md`
- **Plan:** set statuses — ✅ done, 🔄 in progress, ⬜ not started. Add new tasks
  or phases that came up.
- **Decisions / Requirements / Commands / Tech stack:** add anything new; fix
  anything that's now wrong.
- **Open questions:** add new ones, remove answered ones.
- **Current focus / Next up:** rewrite it for the *next* session.
- **Last updated:** today's date (YYYY-MM-DD).

Keep it a snapshot of *now*: replace outdated info, don't append a diary.
Fill in `TODO`s only with facts you actually know — leave the rest as `TODO`.

## 3. Report
Reply with a short summary:
- ✅ Done this session
- ➡️ Next up
- ❓ Open questions (if any)

Don't commit unless the user asks.
