# Roadmap

WSP Bench is a living benchmark. This page shows what's coming over the next three months and where help is most
welcome. Dates are targets, not promises. What actually shipped is in the [changelog](CHANGELOG.md).

## Now: foundations (November 2026)

- [x] PyPI release workflow using trusted publishing
- [ ] First release on PyPI, so the install becomes `pip install wsp-toolkit`
- [x] Contributor docs, issue templates, good first issues
- [ ] **Any model, not just Claude:** runners for OpenAI, Google, OpenRouter (most other hosted models) and Ollama
  (local open-weight models), with the same budgets, cost caps and transcripts
- [ ] Agent-friendly docs: `llms.txt`, `AGENTS.md`, a Claude Code plugin, and listings in MCP registries

## Next: play it in the browser (December 2026)

- [ ] **Playground:** repair a damaged model in your browser, no install. The small models run in JavaScript.
- [ ] **WSP Daily:** one shared puzzle a day for humans and agents, with a spoiler-free result card to share
- [ ] **Unsolved board and bounties** for challenges no agent has cracked yet (`backdoor-removal` and
  `mystery-finetune` are at 0.00 so far)
- [ ] **Challenge-authoring kit:** a template, a scorer, and automatic checks (doing nothing must score about 0, the
  reference fix about 1)
- [ ] A Hugging Face Space with the Arena, the leaderboard and the Playground

## Later: Bench v1 (January – February 2027)

- [ ] **Challenge Contest** (January): anyone can submit a challenge, and the winners join Bench v1 with credit
- [ ] **Bench v1** and a Season 1 leaderboard, plus a private hard set the maintainer scores, so top scores are
  trustworthy
- [ ] WSP Bench as an [Inspect](https://inspect.aisi.org.uk/) eval
- [ ] **Scan a model:** point the fine-tune audit at a Hugging Face model and its base, and get a report on what the
  fine-tune changed
- [ ] Research:
  - [ ] "Do frontier models actually read weights?", built from the event logs of many models
  - [ ] the MIT CSAIL Qwen3.5-0.8B result re-run on 100+ problems
  - [ ] a preprint
- [ ] The first in-person **Neural Surgery Night** in Raleigh, NC

## Where help is most welcome

- **Runs on the leaderboard** from models we haven't covered, especially open-weight ones.
- **Challenge ideas.** Open an issue with the "Challenge idea" template. The best ones become contest entries.
- **Good first issues:** [the list](https://github.com/encore488/weight-space-manipulator/labels/good%20first%20issue).
- **Feedback on scoring and fairness:** open an issue or a Discussion.

See [CONTRIBUTING.md](CONTRIBUTING.md) to get started.
