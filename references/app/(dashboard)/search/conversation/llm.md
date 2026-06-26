---
path: /search/conversation
id: search-conversation
name: Conversation Search
title: Search in Conversation
description: Mobile screen listing search matches within a single conversation (read from id/title/avatar/isGroup/q/category URL params) for the chosen category (messages, files, media, or voice), with infinite-scroll paging and a match count; tapping a hit opens the conversation in /chat scrolled to that message.
relationship:
  upstream: "/search"
  downstream: "/chat"
cta:
  "Conversation header":
    type: nav
    trigger: click
    description: "Top bar showing the back button, conversation avatar/title, and a live match count (or Searching... while loading)."
    items:
      "Back":
        type: button
        trigger: click
        description: "Arrow-left button that calls router.back() to return to /search."
  "Match list":
    type: nav
    trigger: [click, scroll]
    description: "Scrollable list of matching messages for the active category; infinite-scrolls to fetch more pages, and shows Type keywords to search or No messages found when empty."
    items:
      "Open matched message":
        type: button
        trigger: click
        description: "Tapping a hit sets the pending jump message and opens the conversation in /chat (replace) scrolled to that message."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
