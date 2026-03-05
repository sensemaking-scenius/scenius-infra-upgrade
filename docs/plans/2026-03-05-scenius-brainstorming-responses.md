# Sensemaking Scenius Brainstorming — Session Responses

Session: `hst_206730127f33`
Date: 2026-03-05
Participant: Artem

---

## Step 1: Community Pain Points

The biggest frustration is **fragmentation**. Conversations happen across Telegram, calls, shared docs, and individual projects — but there's no single place where the community's knowledge accumulates. You have to "be there" to know what happened. If you miss a week, you're lost.

Specific pain points:

- **Discovery is broken.** Interesting links, ideas, and references get shared in Telegram and disappear into scroll. There's no way to search or browse what the community has collectively surfaced.
- **Projects are invisible to each other.** Gabriel is building Portico, I'm building My Community and Navidrome Jam — but we only learned about overlaps through live calls. There's no ambient awareness of what others are working on or where they need help.
- **Participation has a high floor.** To contribute meaningfully you need to attend sync calls or read long Telegram threads. There's no lightweight async way to participate — something between "lurking" and "showing up to every call."
- **No shared memory.** The community generates insights, makes informal decisions, surfaces patterns — but none of it is captured in a way that's browsable or buildable-upon. Every conversation starts from scratch.

What members wish existed: a low-effort way to stay in the loop, see what others are thinking and building, and contribute without needing to be online at the same time.

### Follow-up: Who does the curation work? Technical vs social problem?

Both, but the technical problem enables the social one. People don't curate because there's no place to curate *into*. If you had a shared surface that passively accumulated community activity, the social norm of "tagging what matters" could emerge. Without the surface, curation feels like unpaid labor with no audience.

On who does the work — layered approach:

1. **Automated baseline.** Extract links, topics, and activity from existing channels (Telegram, calls) without anyone lifting a finger. Gabriel's Knowledge Graph Builder does this for conversation structure. My Community's digest API does it for links. Neither is sufficient alone but together they cover a lot.
2. **Lightweight member input.** Not full curation — more like reactions. Upvote a link, flag something as important, tag a project. The kind of thing you can do in 5 seconds from a phone.
3. **AI-assisted synthesis.** Periodic summaries of what the community discussed, decided, or disagreed on. This is where Harmonica-style structured conversations could feed back — session outputs become part of the shared memory automatically.

The key insight: curation shouldn't be a role or a task. It should be a byproduct of normal participation.

The shared memory problem is primarily technical. The social will exists. People reference past conversations all the time ("remember when we discussed X?"). They just can't *find* them.

### Follow-up: Signal vs noise filtering

**Social filtering with algorithmic support**, not pure automation:

- **For links and content:** Member signals — if 3 people react to a link, it's signal. If nobody engages, it fades. Human attention as the primary filter, with recency decay.
- **For AI synthesis:** Harmonica sessions produce structured outputs *with participant validation*. The risk of misrepresenting consensus drops when the source material is already structured. For unstructured conversations (Telegram, calls), don't auto-extract decisions — surface *that a conversation happened* and *what topics it touched*, then let members decide if it's worth a structured follow-up.

**Filtering stack:**
- Automated: topic extraction, link deduplication, activity detection (what happened)
- Social: member reactions, engagement signals (what matters)
- Structured: Harmonica sessions for things that need actual synthesis (what we think)

The shared memory should be confident about *what happened* (facts, links, activity) and cautious about *what it means* (synthesis, decisions).

### Follow-up: Uneven engagement / participation burden

For a community of ~15-20 active members, you don't need representative sampling — any signal above zero is a massive improvement. And "tap a thumbs up while scrolling" is categorically different from "attend a 90-minute call."

The real risk isn't uneven engagement — it's **cold start**. Solution: launch with the automated layer already populated (digest links, recent topics, project activity) so the feed is useful on day one even with zero member input.

On session frequency: event-driven, not scheduled. 2-3 per month. The three layers have different cadences: automated runs continuously, social signals accumulate passively, structured sessions happen when needed.

---

## Step 2: Tool Intersections

(Informed by March 4 Scenius Workshop transcript)

The most promising intersection: **Knowledge Graph Builder as the shared data backbone, with REST API endpoints that any tool can query.**

Gabriel's plan is to host the KG on a cloud server and expose REST endpoints backed by SPARQL queries. Instead of tightly coupling tools, we build a shared data layer that Portico, My Community, Harmonica, or even Telegram bots can all query independently.

**Portico rooms mapped to Telegram subgroups** is the most concrete integration. Gabriel proposed that each Portico room corresponds to a Telegram group, with a sidebar showing recent activity. You don't need to be in the Telegram group to see a summary. Messages sync back to Telegram via Telethon (Jon has a working implementation for auth).

**Emergent rooms idea:** Beyond mirroring the fixed Telegram structure, rooms could emerge dynamically based on what the community is actually talking about. The Knowledge Graph surfaces recurring cross-community themes. Gabriel proposed a hybrid: fixed rooms for existing structure, plus anyone can spin up a room around an emerging topic.

**My Community as the authenticated entry point.** AT Proto handle sign-in, Scenius whitelist for access. Digest data flows into Portico as a side panel.

**Trade-offs:**
- Gabriel is SvelteKit + Jazz CRDTs. I'm Preact + Vite. Forcing a single app means one stack wins. The REST API approach keeps tools independent but sharing data.
- SIOC ontology makes cross-community interoperability possible (Open Civics, Metagov) without merging codebases.
- Cold start risk on hosting — Gabriel using a free cloud server, Jon offered compute cluster.

**Navidrome Jam** — didn't come up much in the workshop. Its role is ambient social glue. My Community already surfaces live jam rooms.

**Agreed action items from the call:**
1. Gabriel pushes Portico to GitHub and sends repo link
2. Gabriel hosts KG and adds REST API endpoints
3. I explore integrating Scenius Digest into Portico's sidebar
4. Jon shares Telegram auth implementation for the bridge

### Follow-up: KG as single point of failure? Emergent room thresholds?

The KG doesn't need to be the backbone for the MVP. It's the intelligence layer, not the plumbing. The fallback is already built: My Community's digest API works today without the KG. Portico can display room activity directly via Telethon.

MVP works with direct Telegram integration. KG adds quality upgrade — topic clustering, semantic connections — but basic tools function without it. Build direct integrations first, layer KG when stable.

On emergent room thresholds: automated thresholds premature at 15-20 members. KG surfaces suggestions, room creation stays manual. Don't over-engineer the social layer.

### Follow-up: Does direct Telegram integration actually solve fragmentation?

Honest answer: no. Direct Telegram integration alone just moves the scroll problem to a nicer interface.

Minimum viable intelligence needed:
1. **Links grouped by conversation context** (not just chronologically)
2. **Activity summaries per room/channel** — "this week in the workshop channel: 12 messages from 4 people, main topics were X and Y"
3. **Session artifacts as anchors** — Harmonica session summaries visible in the dashboard

The minimum viable intelligence is "basic NLP topic extraction" not "full semantic knowledge graph." The KG is the long-term vision; the MVP needs something in between.

---

## Step 3: Vision

You open your browser and your new tab shows you Sensemaking Scenius — not as a chat app or a feed, but as a living map of what the community is thinking about right now. There are a few active rooms where people are talking, a digest of the most interesting links and ideas from the past week surfaced by member engagement, and a quiet music stream you can join if you want to feel connected while you work. You click into a room — you can see a summary of what's been discussed, browse the relevant links, and either drop into voice or leave an async message. You don't need to have been in every Telegram thread to know what's happening. The community's knowledge is accumulating visibly, and your participation — even just a thumbs up on a link — makes it richer. You come back because every time you open that tab, there's something new to learn, someone to connect with, or a conversation you can meaningfully join without needing a 30-minute catch-up.

### Follow-up: Summary quality bar? Quiet weeks?

Minimum useful summary is a 3-sentence narrative, not keyword extraction. An LLM call on the last N messages can produce this without the full KG. Summaries need to be good enough to orient you (~70% context), not good enough to replace reading the thread.

On quiet weeks:
- Longer time horizons (rolling window that expands during quiet periods)
- Navidrome Jam rooms show ambient presence even when nobody's discussing substantive topics
- Avoid vanity counters — don't show "3 messages this week"
- A quiet dashboard might be honest feedback the community needs

---

## Step 4: MVP Scope

**In the MVP (4-6 weeks):**

1. **Portico with Telegram-linked rooms.** 3-5 rooms mapped to existing Telegram subgroups. Enter a room, see recent messages, join voice or leave text. Bidirectional sync via Telethon.
2. **Daily channel summaries.** LLM-generated narrative summary per active channel, updated daily. 3-5 sentences. Displayed in Portico context panel and My Community dashboard.
3. **My Community integration.** Chrome extension new tab shows: active Portico rooms, weekly link digest, daily summaries. AT Proto auth with Scenius whitelist.
4. **Navidrome Jam presence.** Already integrated, just maintain.

**What can wait:** KG integration, emergent rooms, cross-community SIOC interoperability, member reaction signals, public website, mobile.

**Biggest risk:** Portico-Telegram bidirectional sync (Telethon auth complexity). Fallback: read-only for launch, basic write-back within 2 weeks post-launch.

**Second risk:** Low-quality LLM summaries. Mitigation: good prompt, manual review first week, iterate.

### Follow-up: Read-only value? Timeline with two people?

Read-only Portico isn't "read Telegram somewhere else" — it's spatial presence + voice + context summaries alongside messages. Even without write-back, can post a summary to Telegram when voice conversations happen in a room.

If timeline slips, scope reduction over adding people. Drop LLM summarization and ship rooms + dashboard with raw activity feeds. Summaries become fast follow.

Jon is the exception for targeted Telethon bridge contribution.

---

## Step 5: Next Steps

**Decisions before building (week 0):**
1. API contract: `GET /channels/{id}/summary` returning `{channel_name, period, summary_text, message_count, active_members, topics[]}`
2. Auth model: shared AT Proto layer or accept two logins for MVP
3. Which 3-5 Telegram channels to link as rooms

**Division of labor:**
- Gabriel: Portico rooms, Telethon bridge, push repo to GitHub
- Artem: LLM summarization pipeline, My Community integration, scenius-digest API maintenance
- Shared: API contract in week 1, spike integration in week 2

**Timeline:** Week 1 (API contract) -> Week 2 (spike) -> Weeks 3-4 (parallel build) -> Week 5 (integration + testing with 2-3 members) -> Week 6 (launch to full group)

**People:** Jon (Telethon auth, compute cluster, first tester), Kristen (less technical tester perspective). Don't involve more until something works.

**Resources:** LLM API ~$1-2/month, hosting via existing Vercel + Railway/Jon's cluster, coordination in Scenius Workshop Telegram group.

**Risks:** Telethon auth complexity (fall back to bot for read-only), summary quality (prompt iteration weeks 2-3), scope creep (KG/emergent rooms are out of scope), community expectations (don't go dark, brief async updates every 2 weeks with screenshots).

### Follow-up: Two-person build sustainability? Managing expectations?

Strictly two-person build. Onboarding a third developer in week 3 costs more than it saves. If timeline slips, drop summaries and ship rooms + dashboard with raw feeds.

Community updates: brief async updates in Workshop Telegram group every 2 weeks. Screenshot, short message. Not a launch announcement — showing work in progress. Avoid going dark for 6 weeks then doing a big reveal.
