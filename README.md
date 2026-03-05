# Scenius Infra Upgrade

Dashboard and archive for the Sensemaking Scenius community — tracking sessions, workshops, and emerging consensus around shared infrastructure.

**Live:** https://sensemaking-scenius.github.io/scenius-infra-upgrade/

## What's here

- **Harmonica sessions** — async structured deliberations, synced automatically via [harmonica-sync](https://github.com/harmonicabot/harmonica-sync)
- **Workshop summaries** — notes from live calls, added manually as markdown files
- **Dashboard** — stats, contributor list, emerging consensus, and a combined activity feed

## How it works

Built with Jekyll (GitHub Pages native). Two collections:

- `_sessions/` — synced every 6h by a GitHub Action running `harmonica-sync`
- `_workshops/` — manually authored markdown with YAML frontmatter

## Sync sessions

```bash
export HARMONICA_API_KEY=hm_live_...
npx harmonica-sync
```

## Add a workshop

Create a file in `_workshops/` with this frontmatter:

```yaml
---
title: "Workshop Title"
date: 2026-03-04
type: workshop
duration: 55
participants_list:
  - Name One
  - Name Two
keywords:
  - Topic A
  - Topic B
---

Workshop content in markdown...
```
