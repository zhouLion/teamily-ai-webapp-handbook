---
path: /search
id: search
name: Global Search
title: Search
description: Mobile global-search screen with a sticky header (back/home + query input synced to the q param) and live results across contacts, groups, agents, messages, files, and media; empty query shows recent items, and conversation hits route into /search/conversation while picking a result opens the conversation in /chat.
relationship:
  upstream: "/chat, /"
  downstream: "/, /chat, /search/conversation"
cta:
  "Search header":
    type: nav
    trigger: click
    description: "Sticky top bar holding the back/home control and the query input."
    items:
      "Back":
        type: button
        trigger: click
        description: "Arrow-left button (shown when there is navigation history) that calls router.back()."
      "Home":
        type: link
        trigger: click
        description: "Favicon link to / (shown instead of Back when there is no history)."
      "Search input":
        type: input
        trigger: input
        description: "Autofocused query box synced to the q query param; searches contacts, groups, agents, messages, files, and media live, and shows an X to clear it."
  "Category tabs":
    type: tabs
    trigger: click
    description: "Filter pills selecting which result category to show: All, Contacts, Groups, Agents, Messages, Files, Media (All caps each list to a small preview)."
  "Default recents":
    type: nav
    trigger: click
    description: "Shown when the query is empty: recent contacts, groups, chat history, files, and media as tappable rows."
    items:
      "Open recent contact / group":
        type: button
        trigger: click
        description: "Opens that conversation in /chat."
      "Open recent message / file / media":
        type: button
        trigger: click
        description: "Sets the pending jump message and opens its conversation in /chat scrolled to that item."
  "Result rows":
    type: nav
    trigger: click
    description: "Live query results grouped into Contacts, Groups, Agents, and per-conversation Chat History / Files / Media sections."
    items:
      "Open contact / group / agent":
        type: button
        trigger: click
        description: "Tapping a contact, group, or agent row opens that conversation in /chat."
      "Open conversation matches":
        type: button
        trigger: click
        description: "Tapping a conversation group (or its View all matches) routes to /search/conversation with the conversation, query, and category in the URL params."
      "Jump to matched message":
        type: button
        trigger: click
        description: "Tapping a previewed message/file/media hit sets the pending jump message and opens its conversation in /chat (replace)."
      "View all (category)":
        type: button
        trigger: click
        description: "Section-level View all matches switches the active tab to that category (Contacts/Groups/Agents) to expand the list."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
