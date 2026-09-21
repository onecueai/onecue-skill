<h1 align="center">OneCue</h1>

<p align="center">
  <strong>The decision layer for coding agents.</strong><br>
  Stop your agent re-deciding what you already decided.
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License: MIT"></a>
  <a href="skills/onecue/SKILL.md"><img src="https://img.shields.io/badge/version-0.4.0-green.svg" alt="Version 0.4.0"></a>
  <img src="https://img.shields.io/badge/runtime-local%20files-black.svg" alt="Local files only">
  <a href="https://skills.sh/onecueai/onecue-skill"><img src="https://skills.sh/b/onecueai/onecue-skill" alt="Installs on skills.sh"></a>
</p>

<p align="center">
  <a href="#install">Install</a> ·
  <a href="#how-it-works">How it works</a> ·
  <a href="#what-gets-remembered">What gets remembered</a> ·
  <a href="#ecosystem">Ecosystem</a> ·
  <a href="#roadmap">Roadmap</a>
</p>

---

**Stop re-teaching Claude your project.**

Every new session, your agent starts from zero. The decision you made on Tuesday, the incident you debugged on Thursday — gone. OneCue gives Claude Code durable project memory: decisions, rejected approaches, and debugging discoveries that survive the session and surface exactly when they're relevant.

Not a notes app. Not a transcript archive. Not another memory layer that dumps everything into context.

**One cue. Or silence.**

## Install

One command inside your repo — installs the `onecue` CLI, this skill, recall hooks, and the local store:

```bash
curl -fsSL https://onecue.sh/install.sh | sh
```

Works with Claude Code and Devin today. Local files only — no account, no cloud, no dashboard.

**Skill only** (no CLI, no hooks — the agent still captures and recalls on request):

```bash
npx skills add onecueai/onecue-skill
```

**Or npm**: `npm i -g onecue-cli`, then `onecue install` inside your repo.

## How it works

**Remember** — capture learning as it happens:

```text
Remember that the queue uses Postgres SKIP LOCKED instead of Redis.
Redis reconnect duplicated jobs.
```

OneCue writes one readable Markdown file per learning. With the CLI (preferred), that file lands in the git-visible decisions store; without it, the skill writes a fallback file:

```text
.onecue/decisions/2026-09-13T09-15-00-000Z-decision-a1b2c3d4.md
.onecue/memories/2026-09-13-0915-decision-queue-storage.md
```

**Recall** — the next session, ask for anything relevant:

```text
Make the queue faster.
```

OneCue returns **one** sourced cue — the decision, its reason, and the file it came from. The agent applies it or ignores it. With the CLI on PATH, run `onecue recall "<task>"` rather than searching files by hand.

**Silence** — fix a README typo, and nothing surfaces. A memory is useful only when it changes the next action. Silence is a successful result.

## What gets remembered

| Capture | Never capture |
| --- | --- |
| Decisions **with the reason** | Routine chatter |
| Approaches tried and rejected | Credentials, tokens, keys |
| Debugging discoveries and root causes | Facts the repo already states |
| Architectural constraints | Raw transcripts |
| User corrections | Personal or cross-AI notes |
| Open loops worth resuming | A conclusion without a reason |

**Bad:** `Use Postgres.`
**Good:** `The queue uses Postgres SKIP LOCKED rather than Redis because Redis reconnect duplicated jobs.`

With the CLI, `onecue remember` dedupes and writes to `.onecue/decisions/`. Without it, search `.onecue/memories/` for a near-duplicate and update it instead of cloning.

## Status

Ask Claude: `OneCue status`

With the CLI: run `onecue status` (or `onecue doctor`). Without it, the skill reports whether `.onecue/memories/` exists and how many files it holds.

## Ecosystem

- **[onecue-doctor](https://github.com/onecueai/onecue-doctor)** — diagnoses your setup: store, hooks, runtime. Run it when a decision doesn't surface.
- **`onecue` CLI 0.4.0** — deterministic capture and recall via agent hooks: `init`, `remember`, `recall`, `list`, `forget`, `doctor`, `status`, `statusline`, `bench`. `npm i -g onecue-cli`
- **Docs** — every command: [onecue.sh/docs](https://onecue.sh/docs)
- **OneCue Cloud** — shared decisions across sessions and tools via skills + MCP. [Join the waitlist](https://onecue.sh).

## Roadmap

- [x] Local Markdown store — the M1 source of truth
- [x] Recall with relevance gating and silence
- [x] `onecue` CLI with hooks (auto-recall on every prompt)
- [x] Git-visible `.onecue/decisions/` store (CLI 0.4.0)
- [x] `onecue doctor` diagnostics
- [ ] MCP server — the same decisions across every agent
- [ ] OneCue Cloud — team-shared context, spend analysis

## Principles

- **Readable files, not a black box.** `.onecue/decisions/` is Markdown you can diff, grep, and commit. The skill-only fallback is `.onecue/memories/`.
- **One cue, or silence.** Relevance is gated; noise is the failure mode.
- **Honest over helpful.** If OneCue can't persist, it says so — it never pretends a decision was saved.

## License

[MIT](LICENSE)
