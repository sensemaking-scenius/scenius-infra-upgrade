---
title: "Scenius Workshop — Community Platform Integration"
date: 2026-03-04
type: workshop
duration: 55
participants_list:
  - Gabriel Chartier
  - Artem Zhiganov
  - Jon Bo
  - Kristen Pavle
keywords:
  - Knowledge Graph
  - Telegram Integration
  - Portico App
  - Community Dashboard
  - Cross-Community Collaboration
---

The team discussed integrating community tools into a cohesive platform for improving engagement and information flow.

## Key Topics

### Community Platform Integration
Gabriel and Artem are merging experiments — co-presence audio/text chat, knowledge graph builders, and community sense-making tools — into a unified data pipeline accessible via REST APIs.

### Portico: Spatial Community Interaction
Gabriel demonstrated Portico, a spatial audio and text chat app where users move between rooms corresponding to Telegram subgroups. Rooms offer synchronous voice/text chat with proximity-based audio, using Jazz (real-time sync) and LiveKit (audio).

### Dynamic & Emergent Rooms
Rooms shouldn't just mirror Telegram groups — they could emerge dynamically from cross-community topics and conversations, driven by the Knowledge Graph's semantic analysis.

### Cross-Platform Integration
Artem plans to integrate Portico and the Knowledge Graph with his Chrome extension (My Community), allowing AT Proto sign-in with controlled access to private feeds.

### Public vs. Private Content
The website serves as a public gateway — a filter that piques interest without overwhelming visitors. Community conversations and knowledge graph data stay gated for members.

### Infrastructure
Jon overhauled the compute cluster to offer affordable hosting alternatives. Gabriel plans to host the Knowledge Graph on a free cloud server with REST API endpoints.

## Action Items

**Gabriel Chartier**
- Push Portico code to GitHub and send repo link for integration
- Host the Knowledge Graph on a free cloud server and add REST API endpoints

**Artem Zhiganov**
- Explore integrating the Scenius Digest into Portico's interface as a side panel

**Jon Bo**
- Share Telegram KG experiment URL and implementation details
- Provide beta access and documentation for the compute cluster

**Team**
- Continue feedback and next steps in the Scenius Workshop Telegram channel
