---
description: Show your Blitzit lists
---

Run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" lists --cached` (falls back to `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" lists` if the cache is cold).
If it errors with "Not logged in", tell the user to run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" login`.

Show each list with its name, task count, and id (the id is needed to create tasks
in that list). Keep it compact.
