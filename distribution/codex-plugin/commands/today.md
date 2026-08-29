---
description: Show today's Blitzit tasks
---

Run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" today --cached` when a recent explicit sync has populated the local
cache; otherwise run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" today`. If it errors with "Not logged in", tell the
user to run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" login`.

Show the returned tasks as a compact checklist (title, and board if not "today").
Do not add commentary unless the user asks.
