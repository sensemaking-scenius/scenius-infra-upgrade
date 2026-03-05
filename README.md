# Scenius Infra Upgrade

Dashboard and archive for the Sensemaking Scenius community — tracking sessions, workshops, and emerging consensus around shared infrastructure.

**Live:** https://sensemaking-scenius.github.io/scenius-infra-upgrade/

## About

Sensemaking Scenius is a community of practice exploring collective intelligence, relational technology, and tools for a more intentional internet. Members are building complementary tools — spatial community platforms, knowledge graphs, community dashboards, synchronized listening rooms — and figuring out how they fit together.

This repo is our shared workspace: a living record of what we've discussed, what we've agreed on, and what we're building next. It combines async [Harmonica](https://harmonica.chat) deliberation sessions with summaries from live workshops.

**Community:** https://scenius.space

## How it works

Built with Jekyll (GitHub Pages native). Two collections:

- `_sessions/` — auto-synced from [Harmonica](https://harmonica.chat) every 6 hours via GitHub Actions. When someone participates in a session, the dashboard updates automatically with new responses, participant counts, and summaries.
- `_workshops/` — manually added markdown summaries from live calls.

The **consensus block** and **stats** on the main page need manual updates as the project evolves.

## Sync sessions manually

The GitHub Action handles this automatically, but you can also sync locally or trigger manually from the Actions tab.

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
