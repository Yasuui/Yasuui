# Why I retired my multi-agent crew

*October 25, 2026 · Post-mortem*

Hermes was my self-hosted agent setup on a Mac mini, built on the open-source Hermes Agent framework. I retired it this month. Here's what it did, what broke, and why I stopped.

## What it did

An orchestrator agent called Chief ran on Grok and took requests from me over Telegram or the command line. It handed work to named sub-agents, and every line of code went to a coding tool (Claude Code, Codex or OpenCode) rather than being written by hand. A shared wiki vault gave the agents memory between sessions. Model calls were routed by cost: a flat subscription for volume work, and a pay-per-call reserve only for tasks that needed a specific model.

I also planned a native iOS client to watch and steer the agents from my phone, over Tailscale. It got as far as a [starter bridge](https://github.com/Yasuui/hermes-mobile): a Hono server with an API-key check and a placeholder for live streaming. Neither the streaming nor the app was finished.

## What broke

- **Two identities for one person.** Telegram and the command line created separate sessions for the same conversation. The fix was anchoring every session to my Telegram user ID.
- **Agents fighting over one bot.** When several agent profiles shared one Telegram bot token, their gateway processes competed and orchestration failed. Only the orchestrator could listen.
- **Prompts that timed out.** Long prompts passed to Claude Code as shell arguments timed out. Writing the prompt to a file first and passing the path fixed it.
- **Interrupting myself.** Sending a chat message while a command was running killed that command.

Each fix was small. Together they meant I spent a lot of time running the system instead of building with it, which is the trap I wrote about in [my last note](2026-09-27-smaller-agent-systems.md).

## Why I stopped

The tools caught up. Codex now covers most of what I delegated, Claude Code handles coding and research, and a Grok bot takes the agent-specific daily tasks. Together they did Hermes's jobs with far less upkeep, so I stopped maintaining my own orchestrator.

## What I kept

- An issue, branch, pull request flow for every agent, with no direct pushes to main.
- Prompts written to files, never inline.
- One identity per person across every channel.
- A bootstrap skill that sets up new projects the same way each time.

## When I'd come back

Hermes Agent is open source and improving quickly. When I want a workspace I fully own, for a business or a team, a self-hosted orchestrator makes sense again. For now, owning less of the stack lets me ship more.
