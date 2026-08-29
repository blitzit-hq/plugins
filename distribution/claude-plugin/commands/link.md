---
description: Link this conversation to a Blitzit task and start tracking its time
---

Link the current conversation to a Blitzit task. From then on, the time spent in
this conversation is recorded against that task and shows up in Blitzit reports
alongside desktop Blitz time.

A conversation belongs to **exactly one** task — linking again moves it.

Steps:

1. Identify the target task from: "$ARGUMENTS". If it is a 24-hex task id, use it
   directly. Otherwise find it: `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" tasks --search "<words>" --json` (or
   `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" today --cached`), and pick the best match — ask only if genuinely
   ambiguous.
2. Run `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" link <taskId>`. The current conversation is auto-detected (the
   SessionStart hook stashes it), so no id is needed.
3. Confirm with the linked task's title. If it reports "No conversation to link",
   the SessionStart hook hasn't run — tell the user to reload plugins (or pass
   `--conversation <id>` explicitly).

Timing, so you can answer questions about it accurately:

- The clock starts on the **first prompt** after linking, not when the terminal
  opened.
- A turn that is still running counts in full, however long it takes.
- Once the reply lands, at most 5 more minutes count — so a terminal left open
  overnight adds five minutes, not nine hours.
- Closing the terminal, quitting VS Code, or a crash all end the session at the
  last real activity; nothing is lost and nothing is invented.

To stop tracking: `node "${CLAUDE_PLUGIN_ROOT}/runtime/blitzit.mjs" unlink` (banks the time so far, then detaches).
