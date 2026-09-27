# I want smaller, more understandable agent systems

*September 27, 2026 · Working notes, not a benchmark*

I've spent a lot of time tweaking agent setups: instructions, skills, tooling, context, and ways to hand work between agents. That's fun, but it's easy to spend more time maintaining the system than building the product.

Here's what I'm trying next.

## 1. Make the job obvious

Before adding another specialist agent or skill, I want to know what job it owns, what files it may touch, and what **done** looks like. A short, specific instruction should beat a giant manual when the task is narrow.

## 2. Make the work inspectable

An agent saying “done” is not evidence. I want small artifacts: a useful diff, an exact test result, a browser screenshot when it matters, and a short explanation of what still needs a person. For browser use especially, I want failures and unknowns surfaced instead of hidden.

## 3. Spend verification where it matters

I'm experimenting with a lighter workflow: small changes get small checks; integrations, security boundaries, and user-facing actions earn deeper checks. Running every tool and every test for every tiny change isn't the goal.

## 4. Keep experiments disposable

A prototype doesn't need an entire permanent ecosystem. I'll keep the reusable bits, write down what I learned, and archive the rest. If an experiment becomes genuinely useful, it can graduate to its own repository.

## Things I still need to measure

- Does a smaller harness improve completion quality or just feel cleaner?
- Which browser tasks need deterministic checks versus an agent's judgment?
- What's the smallest useful activity and cost view for multiple coding agents?
- Can I reuse skills between Codex, Antigravity, and Hermes without accumulating platform-specific baggage?

I'll update these notes as I have real demonstrations and results, including the experiments that don't work.

[← Lab index](../README.md)
