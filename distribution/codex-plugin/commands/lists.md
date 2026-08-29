---
description: Show your Blitzit lists
---

Run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" lists --cached` (falls back to `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" lists` if the cache is cold).
If it errors with "Not logged in", tell the user to run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" login`.

Show each list with its name, task count, and id (the id is needed to create tasks
in that list). Keep it compact.
