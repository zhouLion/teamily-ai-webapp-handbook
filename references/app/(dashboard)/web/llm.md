---
path: /web
id: web
name: Visitor Chat
title: Chat
description: The logged-out / root chat surface — a conversation sidebar listing recommended agents (super agent + normal) over a chat content pane; opens an agent via ?agentId=, and redirects signed-in users at / to /chat.
relationship:
  upstream: ""
  downstream: "/, /chat, /discover, /login, /search, /add-contact"
cta:
  "Conversation sidebar":
    type: nav
    trigger: click
    description: "Left resizable sidebar (collapsed on mobile once a conversation is open) holding search, the new-content menu, and the recommended-agent conversation list."
    items:
      "Search box":
        type: input
        trigger: [input, click]
        description: "Search field; on desktop focusing it opens an inline global-search overlay over the list, on mobile focusing it navigates to /search (with ?q= when text is present). An arrow-back button clears/exits search."
      "New content menu (+)":
        type: menu
        trigger: click
        description: "Plus button (mobile header / desktop next to search) opening a dropdown of create actions; while signed out every item except Create agent redirects to /login."
        items:
          "New group":
            type: button
            trigger: click
            description: "Opens the create-group modal (-> /login when signed out)."
          "Add contact":
            type: button
            trigger: click
            description: "Opens the add-contact modal, or navigates to /add-contact on mobile (-> /login when signed out)."
          "Create artifacts":
            type: button
            trigger: click
            description: "Opens the create-artifacts modal (-> /login when signed out)."
          "Create task":
            type: button
            trigger: click
            description: "Navigates to /automations (-> /login when signed out)."
          "Create agent":
            type: button
            trigger: click
            description: "Opens the create-artifacts modal on the agents tab (available even when signed out)."
      "Super agent entry":
        type: button
        trigger: click
        description: "Pinned card at the top of the list for the Super Agent; tapping it opens that agent via /?agentId=<id>."
      "Recommended conversation":
        type: button
        trigger: click
        description: "A recommended-agent row (avatar, name, preview, time); tapping it opens that agent via /?agentId=<id>. Visitor-mode items have no right-click/long-press context menu."
      "Discover agents (empty state)":
        type: link
        trigger: click
        description: "Shown when the list is empty — a Discover Agents button linking to /discover."
  "Chat content pane":
    type: nav
    trigger: click
    description: "Right-hand chat surface rendered once a conversation is active (?agentId= on mobile, or the super agent by default on desktop); shows the selected agent's messages, composer, header, and drawers (same surface as /chat)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
