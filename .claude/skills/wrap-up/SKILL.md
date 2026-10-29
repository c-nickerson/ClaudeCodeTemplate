---
name: wrap-up
description: End-of-session wrap-up for this repo. Updates .claude/memory/PROJECT.md, checks the learning log, commits and pushes. Use when the user runs /wrap-up or says "wrap up".
---

# Wrap up the session

Make sure the next session can pick up straight away.

## 1. See what happened
- Look back over this conversation.
- Run `git status` and `git log --oneline -15`.

## 2. Check the learning log
Every step done this session must have a `## Step N — ...` entry at the bottom
of `docs/learning-log.md`. Add any that are missing.

## 3. Update `.claude/memory/PROJECT.md`
- **Plan:** set statuses — ✅ done, 🔄 in progress, ⬜ not started.
- **Decisions / Requirements / Commands:** add anything new; fix anything now wrong.
- **Open questions:** add new ones, remove answered ones.
- **Current focus / Next up:** rewrite it for the *next* session.
- **Last updated:** today's date (YYYY-MM-DD).

Keep it a snapshot of *now*: replace outdated info, don't append a diary.

## 4. Commit and push
If anything changed, commit with message `Wrap-up: <short summary>` and push.

## 5. Report (ELI5, short)
- ✅ Done this session
- ➡️ Next up
- ❓ Open questions (if any)
