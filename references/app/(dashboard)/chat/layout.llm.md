---
path: /chat
id: chat-layout
name: Chat Layout
title: Chat Layout
description: Two-pane chrome for the messaging workspace — a resizable left sidebar (the aside panel with conversation search, the new/contact menu, and the conversation list with per-item context menus) beside the active conversation. On mobile the open conversation is presented in a full-screen sheet whose back button clears the selection.
relationship:
  upstream: ""
  downstream: "/discover, /add-contact, /search/conversation"
cta:
  "Conversation sidebar":
    type: nav
    trigger: click
    description: "Resizable aside panel: header (search + new menu), the conversation list, and (when searching) the global-search screen."
    items:
      "Conversation search box":
        type: input
        trigger: [input, click]
        description: "Filters/searches conversations; focusing it opens the search screen (navigates to /search?q= on mobile). A back arrow exits search."
      "New / contact menu":
        type: menu
        trigger: click
        description: "Plus button (desktop sidebar / mobile header) opening a create menu."
        items:
          "Create new group":
            type: button
            trigger: click
            description: "Opens the create-group modal (or /login when signed out)."
          "Add contact":
            type: button
            trigger: click
            description: "Opens the add-contact modal on desktop, or navigates to /add-contact on mobile."
          "Create agent":
            type: button
            trigger: click
            description: "Opens the create-agent modal."
      "Personal AI item":
        type: button
        trigger: click
        description: "Pinned super-agent conversation at the top of the list; opens the user's Personal AI."
      "Conversation list item":
        type: button
        trigger: [click, rightclick, longpress]
        description: "Tap to open the conversation; shows unread / mention / pinned / mute / official indicators. Right-click (desktop) or long-press (mobile) opens its context menu."
        items:
          "Pin / unpin to top":
            type: button
            trigger: click
            description: "Toggles whether the conversation is pinned to the top of the list."
          "Mark as read":
            type: button
            trigger: click
            description: "Clears unread count and @mention markers (shown when unread)."
          "Delete conversation":
            type: button
            trigger: click
            description: "Deletes the conversation and its messages (opens a confirmation dialog)."
      "Empty-state Discover Agents":
        type: button
        trigger: click
        description: "Shown when the list is empty; navigates to /discover."
      "Jump to first unread (mobile)":
        type: button
        trigger: doubleclick
        description: "Double-tapping the Chat tab scrolls the list to the first unread conversation (or top)."
      "Search screen":
        type: nav
        trigger: [input, click]
        description: "Replaces the list while searching; category tabs over result rows that open conversations or jump to messages."
        items:
          "Category tabs":
            type: tabs
            trigger: click
            description: "All / Contacts / Groups / Agents / Messages / Files / Media — filters the results."
          "Contact / group / agent result":
            type: button
            trigger: click
            description: "Opens the conversation with that contact, group, or agent (query highlighted)."
          "Message / file / media result":
            type: button
            trigger: click
            description: "Jumps to that message (or file/media) in its conversation."
          "Default suggestions":
            type: button
            trigger: click
            description: "When the query is empty: recent contacts/groups/messages/files/media rows that open or jump to them."
          "View all matches":
            type: button
            trigger: click
            description: "Opens the category-search dialog (desktop) or /search/conversation (mobile) for the full result list."
          "Category-search dialog":
            type: dialog
            trigger: click
            description: "Full, infinite-scrolling results for one category; rows open a conversation or its matches dialog, or jump to a message; close to return."
          "Conversation-matches dialog":
            type: dialog
            trigger: click
            description: "All message/file/media hits within one conversation; tap a row to jump to that message; close to return."
  "Mobile conversation sheet":
    type: dialog
    trigger: click
    description: "Full-screen right-side sheet that shows the open conversation on mobile; the system/back gesture closes it and clears the current conversation."
  "Sidebar resize handle":
    type: button
    trigger: [hover, drag]
    description: "Drag handle on the resizable sidebar edge; persists the chosen width (300–500px) under the chat-sidebar-width key. (Desktop only.)"
---

<!-- 正文待补充:后续人工补充该布局的详细介绍 -->
