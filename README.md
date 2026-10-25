# Yonis Diriye

AI automation developer in Toronto. I build AI products for small businesses, and the agent workflow I use to ship them, with tests that prove they're safe to put in front of real customers.

[diriye.ca](https://diriye.ca) · [LinkedIn](https://www.linkedin.com/in/yonisdiriye/) · [Book a call](https://cal.com/yonis-diriye)

## Now

- **Lintel** (private): an AI front desk for GTA repair shops. It answers missed calls, quotes from the shop's own price list, books drop-offs and texts the owner. Piloting with two shops; a public case study follows once there are real numbers.
- **Barakah Rewards**: co-founder of a halal loyalty platform for Muslim-owned GTA merchants, live on iOS and Android. I'm building the owner dashboard.
- **Canada Revenue Agency**: AI automation developer through the Federal Student Work Experience Program.

## Public work

| Project | What it does | Status |
| --- | --- | --- |
| [Workflow Friction Mapper](https://github.com/Yasuui/workflow-friction-mapper) | A chat agent that reads a workflow you share and returns a grounded brief: friction, bottlenecks and one first move. | [Live](https://workflow-friction-mapper.vercel.app), open source |
| [HarnessGrade](https://github.com/Yasuui/harness-grade) | Scores the instruction files around a coding agent (AGENTS.md, Cursor rules, skills) on a deterministic rubric. | Scoring library; CLI and per-rule ablation in progress |
| [Hermes Community Skills](https://github.com/Yasuui/hermes-community-skills) | A provenance-aware registry for finding and checking community agent skills. | [Live](https://hermes-community-skills.vercel.app) |
| [Hermes Mobile](https://github.com/Yasuui/hermes-mobile) | The bridge from my retired multi-agent setup. | Retired; [why I stopped](lab/notes/2026-10-25-retiring-my-agent-crew.md) |

## How I build with agents

Codex and Claude Code write most of my code. These rules are what make that shippable:

- **Cross-model review.** Codex reviews Claude's pull requests and Claude reviews Codex's. Nothing merges without passing CI and an independent review.
- **Hooks, not hope.** Agents can't push to `main`, force-push or write env files; the hooks block it and the rules are unit tested.
- **Code owns the money.** A model never sets a price or computes tax. Every model output is schema-validated before use, and customer text is treated as untrusted input.
- **Tenant isolation in the database.** Row-level security on every table, tested with two tenants.
- **Every model call is metered.** Tokens, cost, latency and model id go to a ledger.
- **Plan, then build.** One plan per slice, small PRs, and a `NOW.md` that separates what's proven from what isn't.

## Lab

Experiments and build notes, kept separate from finished work: [the lab](lab/README.md).
