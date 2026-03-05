# Scenius Infra Upgrade

Dashboard and archive for the Sensemaking Scenius community — tracking sessions, workshops, and emerging consensus around shared infrastructure.

**Live:** https://sensemaking-scenius.github.io/scenius-infra-upgrade/

## About

Sensemaking Scenius is a community of practice exploring collective intelligence, relational technology, and tools for a more intentional internet. Members are building complementary tools — spatial community platforms, knowledge graphs, community dashboards, synchronized listening rooms — and figuring out how they fit together.

This repo is our shared workspace: a living record of what we've discussed, what we've agreed on, and what we're building next. It combines async deliberation sessions with workshop summaries and community artifacts (proposals, specs, etc.).

**Community:** https://scenius.space

### Current content

- **[Community Application Brainstorming](https://sensemaking-scenius.github.io/scenius-infra-upgrade/sessions/2026-02-27-sensemaking-scenius-community-application-brainstorming.html)** — async Harmonica session on what to build and how tools fit together
- **[Telegram Group Restructuring Proposal](https://sensemaking-scenius.github.io/scenius-infra-upgrade/artifacts/2026-02-24-telegram-restructuring-proposal.html)** — main group + opt-in subgroups + Drip synthesis channel ([Notion source](https://m4co.notion.site/Telegram-Group-Restructuring-Proposal-31496ae9065580a69dcddf02cd483a45))
- **[Community Platform Integration Workshop](https://sensemaking-scenius.github.io/scenius-infra-upgrade/workshops/2026-03-04-scenius-workshop.html)** — Portico, Knowledge Graph, cross-platform integration, public vs private content

## How it works

Built with Jekyll (GitHub Pages native). Three collections:

- `_sessions/` — auto-synced every 6 hours via GitHub Actions using [harmonica-sync](https://github.com/harmonicabot/harmonica-sync). When someone participates in a session, the dashboard updates automatically with new responses, participant counts, and summaries.
- `_workshops/` — manually added markdown summaries from live calls.
- `_artifacts/` — proposals, specs, and other community documents.

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

## Add an artifact

Create a file in `_artifacts/` with this frontmatter:

```yaml
---
title: "Artifact Title"
date: 2026-02-24
type: artifact
artifact_type: proposal
source_url: "https://example.com/original"
authors:
  - Name One
  - Name Two
keywords:
  - Topic A
  - Topic B
---

Artifact content in markdown...
```
