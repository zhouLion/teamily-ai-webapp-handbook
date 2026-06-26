---
path: /discover-legacy
id: discover-legacy
name: Discover Legacy
title: Discover
description: Legacy agent-discovery page — a search bar, category filter tabs, and grids of agent cards; clicking a card opens a rating/subscription drawer on desktop or routes to the detail page on mobile.
relationship:
  upstream: "/chat"
  downstream: "/discover/[id], /chat, /callback/chat, /login"
cta:
  "Search bar":
    type: nav
    trigger: click
    description: "Top search field that debounces (300ms) and queries the agent discover API by name, showing a results dropdown."
    items:
      "Search input":
        type: input
        trigger: input
        description: "Types an agent name; empty input clears results and uses the auth vs anonymous discover endpoint depending on login state."
      "Result row":
        type: button
        trigger: [click, hover]
        description: "Avatar + name + users + description row; click opens the agent (drawer on desktop, /discover/[id] on mobile)."
      "Subscribe toggle (result)":
        type: toggle
        trigger: click
        description: "Per-result subscribe/unsubscribe button (login only); disabled for ChainOpera-x1, Deep Search, Teamily AI-x1."
  "Category tabs":
    type: tabs
    trigger: click
    description: "Filter row synced to the ?category query param: All, Latest, backend categories, and My Agents (login only)."
    items:
      "All":
        type: button
        trigger: click
        description: "Default view showing the Hottest list plus a first-page preview of each category."
      "Latest":
        type: button
        trigger: click
        description: "Shows the newest agents list."
      "Category":
        type: button
        trigger: click
        description: "One button per backend category; selects that category's full paginated list."
      "My Agents":
        type: button
        trigger: click
        description: "Login-only — shows the user's own/subscribed agents."
  "Agent card":
    type: nav
    trigger: click
    description: "Card in the result grid; clicking it opens the rating drawer (desktop) or pushes to /discover/[id] (mobile)."
    items:
      "Open agent":
        type: button
        trigger: click
        description: "Throttled (300ms) card click; desktop opens the side rating drawer, mobile navigates to /discover/[id]."
      "Subscribe toggle (card)":
        type: toggle
        trigger: click
        description: "Subscribe/unsubscribe button (login only) with optimistic update and rollback on failure; disabled when already subscribed for ChainOpera-x1 / Deep Search / Teamily AI-x1."
      "See More":
        type: button
        trigger: click
        description: "On the All view, jumps to that category's full list."
      "Load more":
        type: button
        trigger: [click, scroll]
        description: "On a category's full list, loads the next page (auto-loads on scroll into view)."
  "Agent rating drawer":
    type: dialog
    trigger: click
    description: "Desktop right-side sheet opened from a card; shows agent info, score/category/users, conversation starters, and reviews."
    items:
      "Back / close":
        type: button
        trigger: click
        description: "Closes the drawer (desktop); on mobile the back arrow routes to /discover."
      "Copy Link":
        type: button
        trigger: click
        description: "Copies the agent's share URL (/agent/<name>) to the clipboard."
      "Try Agent":
        type: button
        trigger: click
        description: "Subscribes then opens a chat with the agent (-> /chat); signed-out users are sent to /login?from=/callback/chat."
      "Conversation starter chip":
        type: button
        trigger: click
        description: "Prefilled prompt that launches a chat with the agent using that prompt; signed-out users are sent to /login?from=/callback/chat."
      "Open rating form":
        type: button
        trigger: click
        description: "Edit/comment button that reveals the star + comment form; signed-out users are sent to /login?from=/discover."
      "Star rating":
        type: button
        trigger: click
        description: "Tap a 1-5 star to set the rating (animated)."
      "Comment field":
        type: input
        trigger: input
        description: "Textarea for the review text."
      "Submit review":
        type: button
        trigger: click
        description: "Posts a new comment or updates an existing one (disabled until a rating and comment exist), then refreshes the drawer."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
