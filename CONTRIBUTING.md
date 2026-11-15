# Contributing to WSP Bench

Thanks for helping. This project is meant to be a living, community-built benchmark for weight-space programming
(AI agents reading, debugging and editing neural-network weights directly). There's plenty to do, and much of it
needs no deep machine-learning background.

## Ways to help

| You have… | You could… |
|---|---|
| 10 minutes | Play a replay in the [Arena](https://encore488.github.io/weight-space-manipulator/arena.html) and open an issue for anything confusing |
| An hour and an API key | Run a model on the bench and [submit it to the leaderboard](https://encore488.github.io/weight-space-manipulator/submit.html) |
| An afternoon | Pick a [good first issue](https://github.com/encore488/weight-space-manipulator/labels/good%20first%20issue) |
| An idea for a task | Open a **Challenge idea** issue. A challenge-authoring kit and a contest are coming ([roadmap](ROADMAP.md)) |
| A bug | Open a **Bug report** with the command you ran and its output |

Questions and show-and-tell go in [Discussions](https://github.com/encore488/weight-space-manipulator/discussions).

## Development setup

You need Python 3.11+. Everything runs on CPU.

```bash
git clone https://github.com/encore488/weight-space-manipulator && cd weight-space-manipulator
python -m venv .venv && source .venv/bin/activate
pip install torch --index-url https://download.pytorch.org/whl/cpu   # Linux without a GPU: avoids a multi-GB download
pip install -e ".[dev,hf,pdf,agent]"
```

Check that everything works:

```bash
ruff check wsp_toolkit tests
pytest                     # ~90 tests, about 4 minutes, no network
```

Try it out:

```bash
wsp challenge prepare      # builds the small models once
wsp ui                     # http://127.0.0.1:8765
```

To keep your experiments out of your real data directory, set `WSP_DATA_DIR=/some/scratch/dir` first.

## Where things live

| Path | What |
|---|---|
| `wsp_toolkit/core/service.py` | `Toolkit`: every tool, with logging, access levels, budgets and size caps (`@tool` registers one) |
| `wsp_toolkit/core/extras.py` | Tool groups registered later: zoo, challenges, features, diff, `narrate` |
| `wsp_toolkit/challenge_defs.py`, `core/challenges.py` | Challenge definitions (pure data), plus instance building and scoring |
| `wsp_toolkit/core/leaderboard.py`, `site/` | Leaderboard export and verification; the static website |
| `wsp_toolkit/core/arena.py`, `ui/static/arena.js` | Arena timelines and the canvas renderer |
| `wsp_toolkit/api/`, `ui/` | The local web UI (FastAPI + Jinja2) |
| `wsp_toolkit/mcp_server/` | The MCP server; tool schemas come from the `Toolkit` method signatures |
| `wsp_toolkit/agents/` | CLIs, the Anthropic API runner, scripted baselines |
| `tests/` | pytest; `conftest.py` trains the fixture models once per session |
| `DECISIONS.md` | Why things are the way they are. Read the relevant section before changing behaviour |

## Pull requests

- **Keep each PR small and about one thing.** Open an issue first for anything that changes scoring, the leaderboard
  format or tool behaviour.
- **Add or update tests.** CI runs `ruff` and `pytest` on every PR.
- **Note user-visible changes** under a `## Unreleased` heading at the top of [CHANGELOG.md](CHANGELOG.md).
- **For UI changes**, include before/after screenshots (dark and light).
- **If you add a tool**, regenerate its docs page with `python scripts/gen_tool_docs.py` and commit only the new or
  changed pages.
- **AI-assisted contributions are welcome** (this project is built with Claude Code). Review the code yourself and
  mention the assistance in the PR description.
- **Scores must stay comparable.** A change that alters how an existing challenge is generated or scored means a new
  bench version (`BENCH_VERSION` in `wsp_toolkit/challenge_defs.py`). Discuss it in an issue first.

## Fair play

The leaderboard is only useful if it's honest. Don't submit edited result files, and don't let an agent read
instance files from disk or regenerate instances from the code. The [submission page](https://encore488.github.io/weight-space-manipulator/submit.html)
has the full rules.

## Be kind

Assume good faith, explain rather than dismiss, and remember that many contributors are new to interpretability. The
maintainer may remove comments or contributions that are harassing or demeaning.

## License

By contributing, you agree that your contributions are licensed under the project's
[Apache-2.0 license](LICENSE).
