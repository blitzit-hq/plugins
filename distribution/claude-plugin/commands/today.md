---
description: Show today's Blitzit tasks
---

Run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" today --cached` when a recent explicit sync has populated the local
cache; otherwise run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" today`. If it errors with "Not logged in", tell the
user to run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" login`.

Show the returned tasks as a compact checklist (title, and board if not "today").
Do not add commentary unless the user asks.
