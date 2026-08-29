# OneCue Agent Skill

**You forgot this. OneCue didn't.**

OneCue is a local-first Agent Skill for preserving the working context that is actually worth keeping: decisions, discoveries, insights, references, and open loops.

It uses the open Agent Skills format rather than coupling M1 to one model or one coding agent.

## Install

From your project:

```bash
npx skills add akashp1712/onecue-skill
```

The Skills CLI can install skills into supported agents such as Claude Code, Cursor, Codex, GitHub Copilot, Windsurf, Gemini, Cline and others. Check your agent's current Agent Skills support.

## Try it

Tell your agent:

```text
Remember that we decided not to turn the product into a CRM until customer demand proves it.
The reason is to protect the narrow after-hours booking wedge.
```

Later, while doing related work:

```text
What did we previously decide that is relevant to the job-management code I'm changing?
```

A strong match can return one concise cue. A weak match should return nothing.

## What gets remembered

- decisions and why they were made
- discoveries that may matter later
- non-obvious insights
- unresolved/open loops
- references whose future use is understood

Routine chatter stays disposable.

## Where M1 memory lives

When the agent has filesystem access, OneCue writes Markdown files to:

```text
.onecue/memories/
```

That makes M1 local-first, inspectable, portable across compatible agents, and useful without a OneCue account.

Review memory files before committing them if they contain sensitive project context.

## What M1 does not do

M1 does not yet provide cloud sync, browser capture, cross-device memory, background monitoring, team sharing, or ambient cues.

Those come only if the first behavior proves useful: preserve something valuable now and recover it when later work makes it relevant.

## Philosophy

> Your work creates the context. OneCue creates the relevance.

> Silence is a feature.

> Preserve the reason, not just the conclusion.

## Optional runtime adapters

Agent Skills is the canonical distribution format. Runtime-specific adapters may be added separately when they improve installation or UX without changing the core skill behavior.

## License

MIT

---

[onecue.app](https://onecue.app)
