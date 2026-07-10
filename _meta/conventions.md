---
tags: [meta, conventions]
status: active
updated: 2026-07-03
---

# Vault conventions — navigation contract

This file is the entry point for humans and agents. Read it before writing.

## Purpose
Living notes: personal, project, and **non-sensitive** work notes. Governance/config
docs (identity, policies, infra) live in their git repos — **not here**.

## Agent-readable, later agent-writable
This vault is readable by agents now and will become agent-writable. **Nothing goes in
`work/` that could not survive being read or written by an agent.** Sensitive work
material is excluded by the author, at authoring time.

## Frontmatter
Every note carries: `tags`, `status`, `updated`.
Agent-authored notes additionally carry: `author`, `created`, `source`.

## Linking
Notes link to related notes with `[[wiki-links]]` when a real connection exists — the graph indexes links, not folders. New notes should link to at least one existing note where it makes sense. Applies to humans and agents alike.

## Agent write rules (forward-looking — not yet enabled)
- MAY create new notes with attribution frontmatter (`author`/`created`/`source`).
- MAY append dated entries to log-style notes; never rewrite history above.
- MUST NOT rewrite human-authored prose in place — add a dated addendum or a
  `> [!suggestion]` callout instead.
- Working files go in `agents/<name>/scratch/`, not in topic folders.

## Folder map
- `inbox/` — unsorted captures; triage into a topic folder.
- `travel/` — one note per trip.
- `projects/` — one note or subfolder per active project.
- `home/` — house, maintenance, purchases, logistics.
- `wine/` — cellar inventory and tasting notes.
- `food/` — recipes, cooking notes, meal ideas.
- `work/` — non-sensitive work notes only.
- `agents/` — per-agent scratch space; not human notes.
- `_meta/` — this contract and vault-level docs.
