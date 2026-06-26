---
path: /discover
id: discover
name: Discover
title: Discover
description: The discover home — a sticky-header, tabbed feed shell that surfaces two surfaces driven by URL params: a content feed (Following / Feeds masonry) by default, or an Agents rail (Agents / Agent Teams) when ?tab= or ?section=agents|groups is set, each with search, source sub-tabs, and category filters.
relationship:
  upstream: "/, /discover-legacy, /discover-legacy/[id], /discover/groups, /post/[showcaseId], /settings/creator-center, /settings/credits-center"
  downstream: "/chat, /login, /post/[showcaseId], /profile/[uid], /settings/credits-center, /discover/groups"
cta:
  "Tabs":
    type: tabs
    trigger: click
    description: "Top tab strip; the visible set depends on the surface — Following | Feeds on the default content surface, Agents | Agent Teams on the agents surface (entered via ?tab= or ?section=agents|groups). Switching off the agents rail resets to the Feeds default."
    items:
      "Following tab":
        type: button
        trigger: click
        description: "Content surface — masonry of posts scoped to accounts the user follows."
      "Feeds tab":
        type: button
        trigger: click
        description: "Content surface — the general discover feed masonry (default landing tab)."
      "Agents tab":
        type: button
        trigger: click
        description: "Agents surface — list of agent templates as row cards (default landing tab when ?tab=agents)."
      "Agent Teams tab":
        type: button
        trigger: click
        description: "Agents surface — curated agent-team cards; labelled Groups internally (?tab=groups)."
  "Search":
    type: input
    trigger: input
    description: "Rounded search box (top-left on desktop, above pills on mobile) with a per-tab placeholder; filters feed posts, agent templates (server-side, debounced 300ms), or agent teams (local filter on name/scene/description/tags)."
  "Create Own Agent":
    type: button
    trigger: click
    description: "Plus button beside search on the Agents tab; opens the create-artifacts modal on the agents tab (in-page dialog)."
  "Create Own Agent Team":
    type: button
    trigger: click
    description: "Plus button beside search on the Agent Teams tab; opens the New Group creation modal (in-page dialog)."
  "Source sub-tabs":
    type: tabs
    trigger: click
    description: "On Agents / Agent Teams surfaces — toggle between By Teamily (official library) and Created by Me (the signed-in user's own templates/teams); category pills are hidden under Created by Me."
  "Category pills":
    type: select
    trigger: click
    description: "Horizontal pill filter. On Following/Feeds it filters feed posts (re-tapping the active pill refreshes, with a spinner). On the Agents official tab it filters templates by team category; on the Agent Teams official tab it filters by team category."
  "Feed post card":
    type: button
    trigger: click
    description: "Masonry card on Following/Feeds; opens the post detail and carries the feed's like/comment/share/remix/bookmark actions."
  "Chat with agent":
    type: button
    trigger: click
    description: "Chat button on each agent row card (Agents tab); when signed out redirects to /login, otherwise creates an agent from the template and opens its conversation in /chat (shows an inline spinner while creating)."
  "Agent team members popover":
    type: menu
    trigger: click
    description: "Member-count badge on an agent-team cover (Agent Teams tab) opening a popover that lists each member's avatar, name, role, and description."
  "Create agent team":
    type: button
    trigger: click
    description: "Create button on an agent-team card; spins up a group chat from the curated team (shows a spinner on that card while creating)."
  "Load more":
    type: nav
    trigger: scroll
    description: "Infinite-scroll sentinels auto-fetch the next page near the viewport edge for the feed masonry, the Agents template list, and the Created by Me agent-teams list."
  "Onboarding rewards banner":
    type: button
    trigger: click
    description: "Dismissible first-week-tasks banner shown above the feed (content surface only) with a progress bar; clicking it navigates to /settings/credits-center?tab=onboarding, and the X stores a per-account dismissal."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
