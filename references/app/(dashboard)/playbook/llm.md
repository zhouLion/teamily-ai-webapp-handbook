---
path: /playbook
id: playbook
name: Playbook
title: Playbook - Teamily AI
description: Discover-style gallery of agent playbooks rendered as an infinite-scroll masonry grid, with a sticky category filter and per-card Try (open the agent chat preloaded with the playbook prompt) and Replay (watch the recorded run) actions.
relationship:
  upstream: ""
  downstream: "/chat, /login"
cta:
  "Category filter":
    type: tabs
    trigger: click
    description: "Sticky pill row (All + fetched categories, each with icon) that filters the playbook masonry grid by category; hidden when showCategory is false (e.g. embedded)."
  "Playbook card":
    type: nav
    trigger: [hover, click]
    description: "Masonry card showing the cover image, category badge, agent name, optional New badge, and title; hovering (desktop) or tapping reveals the Try / Replay action overlay."
    items:
      "Try":
        type: button
        trigger: click
        description: "Wand button that opens the playbook's agent chat preloaded with the prompt and attachments (→ /chat); signed out, redirects to /login with a callback that resumes the chat."
      "Replay":
        type: link
        trigger: click
        description: "Rewind button that opens the playbook's replay_url in a new tab to watch the recorded run."
  "Load more":
    type: nav
    trigger: scroll
    description: "Sentinel at the grid's bottom that auto-fetches the next page (12 per page) via IntersectionObserver when scrolled into view."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
