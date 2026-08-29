---
description: Create a Blitzit task
---

Create a Blitzit task from: "$ARGUMENTS".

Steps:
1. If the user did not name a target list, run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" lists --cached` and pick the
   most relevant list (ask only if it is genuinely ambiguous).
2. Create it with `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" new "<title>" --list <listId>`, adding `--board today`
   if the user implied it is for today, and `--notes` / `--schedule` / `--estimate`
   if they gave those details.
3. Confirm with the created task's title. If not logged in, tell the user to run
   `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" login`.
