# legwork

> **This repository is a generated build artifact.** Its source of truth is
> [`adamentwistle/legwork`](https://github.com/adamentwistle/legwork) — the `core/`
> directory there. Do not edit files here; changes belong in that repo and are
> republished by its `scripts/build_wedge.py`. See [Canonical source](#canonical-source).

legwork is a project queue for Claude Code that survives you walking away. Each
project is one markdown file with a status, an append-only log, and a
ready-to-run next prompt. You end a work session with `/wrap`, which records
what happened and writes the prompt your next session should start from, while
the context is still hot. Days later, `/pickup` briefs you back into the
project in thirty seconds instead of twenty minutes of re-reading. A static
dashboard shows the whole queue at a glance.

## Install

From inside Claude Code, add the marketplace and install the plugin:

```
/plugin marketplace add adamentwistle/legwork-core
/plugin install legwork@legwork
```

That gives you the six slash commands (`/add`, `/wrap`, `/pickup`, `/log`,
`/shelve`, `/vision`) and the legwork-tracker skill in every repo on your
machine, backed by a queue in `~/legwork` (set `LEGWORK_DIR` to move it).

## The loop

The core of legwork is a habit, not a daemon: never end a session without
writing down what the next session should do.

```
/add      create projects/<name>.md: status, description, a real first prompt
 work     any Claude Code session, in any repo
/wrap     log what happened, write the next prompt while context is hot
 away     days pass; the dashboard shows every project and its next step
/pickup   a 30-second re-entry briefing; run the queued prompt or adjust it
```

The plugin's whole surface is the [`core/`](core/) directory: the commands,
the legwork-tracker skill, a standard-library dashboard builder
(`core/build_dashboard.py`), and the session hooks. No server, no
dependencies.

## Canonical source

This repo is the level-1 manual loop, published on its own. The full project —
including the optional level-2 runner and LLM reviewer that fire queued prompts
as unattended sessions — lives at
**[`adamentwistle/legwork`](https://github.com/adamentwistle/legwork)**, which is also
where `core/` is authored. If you found a copy of this loop somewhere else,
that is the original. Install only from `adamentwistle/legwork-core` or the canonical repo.

## License

MIT — see [LICENSE](LICENSE).
