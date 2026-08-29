---
description: Refresh the Blitzit cache now
---

Run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" sync` to refresh the local cache (lists, today, counts) from the
server, then briefly report how many lists and today-tasks are cached. If not
logged in, tell the user to run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" login`.
