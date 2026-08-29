---
description: Refresh the Blitzit cache now
---

Run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" sync` to refresh the local cache (lists, today, counts) from the
server, then briefly report how many lists and today-tasks are cached. If not
logged in, tell the user to run `node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" login`.
