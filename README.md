# Blitzit plugins

Marketplace distribution for the [Blitzit](https://blitzit.app) coding-agent
integration. Blitzit turns every agent conversation into a task and records how
long it took, and keeps a live checklist on that task so the plan survives
compaction.

**This repository is generated.** It is published from the Blitzit CLI release
pipeline; open issues and pull requests at
[blitzit-hq/cli](https://github.com/blitzit-hq/cli/issues).

Current release: `v1.1.0`

## Install

Neither host needs a global `blitzit` executable — each plugin bundles its own
runtime. Node 20+ must be on the machine.

### Claude Code

```bash
claude plugin marketplace add blitzit-hq/plugins@v1.1.0
claude plugin install blitzit@blitzit
```

Run `/reload-plugins` if Claude reports that activation is pending.

### Codex

```bash
codex plugin marketplace add blitzit-hq/plugins --ref v1.1.0
codex plugin add blitzit@blitzit
```

### Or let the CLI do it

```bash
npm install --global blitzit
blitzit setup --claude --codex
```

## Log in

Installing the plugin does not sign you in. Authenticate once:

```bash
blitzit login --browser
```

## Uninstall

```bash
blitzit setup --claude --codex --uninstall
```

Or remove the plugin through each host's own `plugin uninstall` / `plugin remove`
command. Removing Blitzit leaves configuration it does not manage untouched.

## Troubleshooting

`blitzit doctor` reports the installed plugin version, which hook manifests each
host can see, and the API origin. Its output is redacted and safe to paste into
an issue.

## Layout

| Path | Purpose |
| --- | --- |
| `.claude-plugin/marketplace.json` | Claude Code catalogue |
| `.agents/plugins/marketplace.json` | Codex catalogue |
| `distribution/claude-plugin/` | Claude artifact — manifest, `hooks/hooks.json`, launcher, runtime |
| `distribution/codex-plugin/` | Codex artifact — manifest, `hooks.json`, runtime |

Each plugin root contains exactly one hook manifest, in its own host's schema.
Codex discovers hook files recursively, so a Claude manifest under the Codex root
would be evaluated as a Codex hook and fail; the release gate asserts the two
schemas never share a root.

## License

MIT — see [LICENSE](./LICENSE).
