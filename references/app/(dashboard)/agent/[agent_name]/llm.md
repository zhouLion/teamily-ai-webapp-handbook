---
path: /agent/[agent_name]
id: agent-agent_name
name: Agent Detail
title: Agent Detail
description: Public agent profile page fetched by name (ISR-cached) showing avatar, creator, score/category/users stats, description, conversation starters, and user reviews; redirects home if the agent is not found, and "Try Agent" subscribes then opens a chat with the agent.
relationship:
  upstream: "/discover, /discover-legacy, /explore, /chat, /search"
  downstream: "/chat, /login"
cta:
  "Try Agent button":
    type: button
    trigger: click
    description: "Sticky bottom button (disabled until the agent loads); signed in it subscribes to the agent and opens its chat (→ /chat), signed out it redirects to /login?from=/callback/chat with the agent encoded for post-login open."
  "Conversation starters":
    type: button
    trigger: click
    description: "Suggested prompt chips (shown when present); tapping one runs Try Agent seeded with that prompt — opens the agent chat signed in, else redirects to /login."
  "Rate / comment toggle":
    type: button
    trigger: click
    description: "Pencil-icon button (or the empty 'No comments yet' card) that switches the page into the rate-and-comment view; redirects to /login?from=/discover when signed out."
  "Back to detail":
    type: button
    trigger: click
    description: "Floating ArrowLeft button shown in the rate-and-comment view; returns to the agent detail view."
  "Rate stars":
    type: button
    trigger: [click, hover]
    description: "1-5 tap-to-rate star control in the rate-and-comment view, with a per-star fill animation on selection."
  "Comment textarea":
    type: input
    trigger: input
    description: "Free-text field to write the review comment (placeholder 'Please share your thoughts here.')."
  "Submit comment button":
    type: button
    trigger: click
    description: "Sticky bottom Submit button (disabled while empty or pending) that posts the score + comment to the agent review API, then returns to the detail view."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
