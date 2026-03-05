# Scenius Infra Upgrade

Dashboard and archive for the Sensemaking Scenius community — tracking sessions, workshops, and emerging consensus around shared infrastructure.

**Live:** https://sensemaking-scenius.github.io/scenius-infra-upgrade/

## About

Sensemaking Scenius is a community of practice exploring collective intelligence, relational technology, and tools for a more intentional internet. Members are building complementary tools — spatial community platforms, knowledge graphs, community dashboards, synchronized listening rooms — and figuring out how they fit together.

This repo is our shared workspace: a living record of what we've discussed, what we've agreed on, and what we're building next. It combines async [Harmonica](https://harmonica.chat) deliberation sessions with summaries from live workshops.

**Community:** https://scenius.space

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
