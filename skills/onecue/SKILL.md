---
name: onecue
description: Preserve and recover durable working context. Use when a user asks an agent to remember something, makes an explicit durable project decision, identifies a non-obvious discovery or insight, leaves an open loop, saves a reference for later, resumes work that may depend on prior reasoning, or asks what was previously decided. Do not use for routine chatter, transient implementation details, or generic transcript storage.
---

# OneCue

OneCue is not a notes app and not a transcript archive. Preserve only context that could change, accelerate, protect, or clarify future work.

## Portable storage contract

When the agent has filesystem write access, store OneCue memories inside the current project:

`.onecue/memories/`

Use one Markdown file per durable memory. Create the directory when needed.

Filename:

`YYYY-MM-DD-HHMM-<kind>-<short-slug>.md`

Use this shape:

```md
---
kind: decision | discovery | insight | open_loop | reference
project: <project or unknown>
captured_at: <ISO timestamp when available>
source: <agent or surface when known>
tags: [optional, concise, tags]
---

# <short descriptive title>

<one self-contained paragraph describing what should be remembered>

## Why it mattered

<the reason, trade-off, evidence, or future condition that makes this useful later>

## Revisit when

<a concrete future trigger if one is known; otherwise "Unknown">
```

Do not invent missing metadata.

If the current agent cannot write files, do not pretend the memory was persisted. Explain that durable M1 memory requires a persistent project filesystem or another configured storage adapter.

## Remember

Capture:
- decisions **with the reason**
- discoveries that could matter later
- non-obvious insights
- unresolved/open loops
- references with an understood future use

Do not capture:
- routine chatter
- every intermediate thought
- obvious facts already represented in the project
- credentials, tokens, passwords, or private keys
- large transcripts when a concise self-contained memory is sufficient

Before writing, use the agent's available project search/read tools to check `.onecue/memories/` for a near-duplicate. Update an existing memory only when new information materially changes the decision, reason, status, or revisit condition.

After capture, respond briefly:

`Remembered — <short description>.`

## Recall

When the user asks what was previously decided, or when current work strongly suggests prior context may matter:

1. Use available project search/read tools to search OneCue memories using the current task, project, entities, and meaningful terms.
2. Prefer decisions and open loops over generic references when relevance is comparable.
3. Prefer memories whose "Revisit when" condition matches the current work.
4. For unsolicited/contextual resurfacing, return at most one cue.
5. If no candidate is strong enough to change, accelerate, protect, or clarify the current work, stay silent about OneCue.

Cue format:

```text
OneCue · <time/project>

<relevant prior context>

Why now: <one sentence connecting it to current work>
```

If the user explicitly asks for history or multiple memories, multiple results are allowed. The one-cue limit applies to unsolicited resurfacing, not explicit search.

## Status

If asked for OneCue status, report only factual local information:
- whether `.onecue/memories/` exists
- memory count
- counts by kind when easy to determine

Do not claim cloud sync, cross-device memory, background monitoring, automatic browser capture, or team sharing.

## Invariants

- Silence is a valid result.
- Preserve the reason, not just the conclusion.
- The user should not need to remember the exact wording of a memory to recover it.
- Never fabricate a memory.
- Never present weak semantic overlap as meaningful relevance.
- Local project files are the source of truth for M1.
