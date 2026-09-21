# Changelog

## 0.4.0 — 2026-09-21

Decision-layer positioning. When `onecue` is on PATH, the CLI owns the canonical git-visible store at `.onecue/decisions/`. Skill-only fallback remains `.onecue/memories/`.

- README one-liner: *Stop your agent re-deciding what you already decided.*
- SKILL.md delegates remember/recall to `onecue` whenever the binary is available
- Tombstone-on-forget stays a CLI concern; the skill-only path still marks or deletes the fallback file

## 0.2.0 — 2026-09-06

M1 polish. Searchable like the rest of [akashp1712/skills](https://github.com/akashp1712/skills). Install experience matched to [Memorable](https://memorable.sh): one command, then normal Claude work.

- description rewritten for Claude auto-discovery and `npx skills` search (third person, trigger phrases)
- `user_invocable: true` so `/onecue` works
- SKIP LOCKED fixture in `references/examples.md`
- memory template and `AGENTS.md` snippet
- unsolicited recall still one cue or silence
- Claude Code is the product surface; store remains `.onecue/memories/`

## 0.1.0 — 2026-08-29

Initial public M1.

- local-first project memory
- durable decision/discovery/insight/open-loop/reference capture
- reason and revisit-condition preservation
- conservative recall
- one unsolicited cue or silence
