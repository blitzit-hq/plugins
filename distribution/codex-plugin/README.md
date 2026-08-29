# Blitzit plugin

Blitzit turns coding conversations into task-backed work sessions and gives your
agent a safe interface for managing Blitzit lists and tasks. Install it from a
Claude Code or Codex marketplace. The installed plugin contains its own runtime;
you do **not** need `npm install -g blitzit`.

## First use

Sign in once from the installed plugin runtime:

```bash
node "${CODEX_HOME:-$HOME/.codex}/plugins/cache/blitzit/blitzit/1.1.0/runtime/blitzit.mjs" login
```

That opens browser sign-in (or accepts `--token blitzit_api_*`). Credentials stay
in the normal user-local Blitzit configuration directory with owner-only file
permissions.

## What runs automatically

The plugin intentionally has four hooks with separate responsibilities:

| Hook               | Purpose                                                                                                                                              |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `SessionStart`     | Stashes the conversation identity, handles `/resume`, and reaps abandoned sessions. It does not start time.                                          |
| `UserPromptSubmit` | Receives the only reliable prompt text; the first prompt creates/titles the task and starts tracking. It also returns the compact checklist context. |
| `PostToolUse`      | Throttled activity heartbeat during a long tool-driven turn, so live work is visible before the response ends.                                       |
| `SessionEnd`       | Ends the session at the transcript's last activity. A crash is recovered by the next session's reaper.                                               |

The hooks are silent and failure-tolerant so they never block the host agent.
There is deliberately no cache-sync hook: a startup network request merely for a
cache convenience was unnecessary noise. Use the `/blitzit:sync` command when a
fresh offline cache is useful.

## Commands and skills

- `/blitzit:today`, `/blitzit:lists`, `/blitzit:new`, `/blitzit:link`, and
  `/blitzit:sync` provide explicit task actions.
- The `blitzit-manager` skill manages an arbitrary named list or task, while
  requiring confirmation for destructive changes.
- The `blitzit-tasks` skill keeps the current conversation's meaningful
  milestones compact and honest; it does not use tasks as an activity log.

## Uninstall

Use your host's plugin command:

```bash
claude plugin uninstall blitzit@blitzit
codex plugin remove blitzit@blitzit
```

If this plugin was installed by a legacy global CLI setup, run its setup
uninstall command as well. That removes only Blitzit's old standalone hook and
instruction entries; it does not remove other plugins or personal settings.
