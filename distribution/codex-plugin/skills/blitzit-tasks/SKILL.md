---
name: blitzit-tasks
description: Track substantial multi-step work as a compact checklist on this conversation's Blitzit task. Use when durable progress tracking helps, or when the user asks for progress; skip simple answers, one-step edits, and routine commands.
---

# Blitzit task checklist

The lifecycle hooks create a task from this conversation's first prompt and
track its coding time. Keep the task's checklist honest when the work is
substantial enough to benefit from durable progress tracking across long turns,
compaction, or a resumed conversation.

## When to use it

Use a checklist for substantial multi-step work: a feature, investigation,
migration, repair, refactor, or a request whose outcome needs several meaningful
milestones. Skip pure answers, a one-step edit, and routine commands.

This is a user-facing plan, not an agent activity log. Do not create separate
items for reading files, formatting, commits, CI, or ordinary checks.

## Commands

All commands target the current conversation task automatically:

```bash
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" goal "<concise goal>"
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask list
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask add "Investigate the current behavior" "Implement the user-visible fix"
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask replace 2 "Validate and hand off the completed fix"
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask done 2
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask rm 3
```

## Rules

1. Name the goal once the real outcome is clear; the raw first prompt is only a
   placeholder.
2. Plan **1–5** meaningful milestones with checkable user-visible outcomes.
3. Mark a milestone done only when it genuinely landed; never batch-fill a plan
   after the fact.
4. When related work changes shape, use `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" subtask replace <old> "<new>"`.
   It creates the replacement before removing the old item, and the replacement
   write includes its final checked/unchecked state—no third check operation is
   required.
5. Re-read the list after compaction or when unsure. Remove only items that are
   truly obsolete; never erase useful history to make a list look tidy.

Do not create a separate task for this plan. `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" new` is for work the user
explicitly wants tracked separately. If a command says no task is linked, state
that the lifecycle hooks did not run and continue with the user's requested work
without fabricating a session.
