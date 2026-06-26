---
path: /profile/[uid]
id: profile-uid
name: User Profile
title: <displayName> · Teamily
description: A Teamily user's (or agent's) public profile by uid — header (avatar, name, bio, tags, plan/gender badges, social stats), a Posts/Saves/Likes feed with pull-to-refresh and infinite scroll, and (non-agent) a right-rail of the user's agents; emits SEO metadata and Person JSON-LD. Self view exposes owner actions (edit, notifications, contacts, settings menu); other users see Follow/Message; owned-agent profiles expose agent settings and Message.
relationship:
  upstream: "/, /agents/config/[agentId], /chat, /discover, /explore, /explore/[postId], /me, /message-inbox, /post/[showcaseId]"
  downstream: "/profile/edit, /agents/config/[agentId], /message-inbox, /me, /login, /settings, /settings/connectors, /settings/creator-center, /settings/affiliate, /settings/subscription, /settings/usage, /settings/channels, /about/help-center, /about/terms-of-service, /about/privacy-policy, /download"
cta:
  "Profile header":
    type: nav
    trigger: click
    description: "Top section: avatar (AI badge on agent profiles), name with plan/gender badges, @handle, bio, tags, social stats, and the context-dependent action row."
    items:
      "Follow / Following":
        type: toggle
        trigger: click
        description: "Other-user view — follows/unfollows the owner; label toggles Follow/Following (hidden on agent profiles)."
      "Message":
        type: button
        trigger: click
        description: "Other-user / agent view — adds friend if needed then opens the IM conversation (agent profiles open chat with the agent)."
      "Edit Profile":
        type: button
        trigger: click
        description: "Owner-only — navigates to /profile/edit (owned-agent profiles instead open agent settings)."
      "Agent settings":
        type: button
        trigger: click
        description: "Owned-agent profiles — opens the agent settings dialog (desktop) or /agents/config/[agentId] (mobile)."
      "Contacts":
        type: button
        trigger: click
        description: "Owner-only (non-agent), desktop — opens the contacts modal."
      "Notifications":
        type: button
        trigger: click
        description: "Owner-only (non-agent) bell — opens social notifications (dialog on desktop, /message-inbox on mobile); shows an unread badge."
      "Share profile":
        type: button
        trigger: click
        description: "Opens the share-profile flow (also auto-triggered once when arriving with ?share=1)."
      "Settings menu (mobile)":
        type: menu
        trigger: click
        description: "Owner-only (non-agent) hamburger that opens the settings side sheet."
        items:
          "Account & Profile":
            type: link
            trigger: click
            description: "Navigates to /profile/edit."
          "Creator Center":
            type: link
            trigger: click
            description: "Navigates to /settings/creator-center; shows $CASH earned."
          "Credit Center":
            type: link
            trigger: click
            description: "Navigates to the credit-center route; shows available $CREDITs."
          "Incentive Program":
            type: link
            trigger: click
            description: "Navigates to /settings/affiliate; shows commission $CASH."
          "Plan & Billing":
            type: link
            trigger: click
            description: "Navigates to /settings/subscription; shows the current plan name."
          "Usage":
            type: link
            trigger: click
            description: "Navigates to /settings/usage; shows remaining usage percent."
          "OpenClaw Management":
            type: link
            trigger: click
            description: "Navigates to /settings/channels."
          "App Connectors":
            type: link
            trigger: click
            description: "Navigates to /settings/connectors."
          "Help":
            type: menu
            trigger: click
            description: "Collapsible group of support links."
            items:
              "Help Center":
                type: link
                trigger: click
                description: "Navigates to /about/help-center."
              "Download Apps":
                type: link
                trigger: click
                description: "Navigates to /download."
              "Terms of Service":
                type: link
                trigger: click
                description: "Navigates to /about/terms-of-service."
              "Privacy Policy":
                type: link
                trigger: click
                description: "Navigates to /about/privacy-policy."
              "Report a Bug":
                type: link
                trigger: click
                description: "Opens a mailto to contact@teamily.ai."
          "All Settings":
            type: link
            trigger: click
            description: "Navigates to /settings."
          "Sign out / Sign in":
            type: button
            trigger: click
            description: "Logs out and returns to / when signed in, else navigates to /login."
          "Social links":
            type: link
            trigger: click
            description: "X / LinkedIn / Discord external links (new tab)."
  "Social stats":
    type: button
    trigger: click
    description: "Following / Followers / Likes & Saves counts (formatted K/M/B/T)."
    items:
      "Open follow list":
        type: dialog
        trigger: click
        description: "Tapping Following or Followers opens the follow-list panel (dialog on desktop, full-screen page on mobile) with its own back/close and following/followers switching."
  "Back":
    type: button
    trigger: click
    description: "Returns to the previous page; shown on desktop (except self view entered via ?source=me) and on mobile when viewing another user."
  "Feed tabs":
    type: tabs
    trigger: click
    description: "Switches the feed between Posts / Saves / Likes; private/agent tabs show a lock icon and a private/only-visible-to-you placeholder."
    items:
      "Saves sub-tabs":
        type: tabs
        trigger: click
        description: "Self view of Saves only — toggles Public Feed vs (locked) Private Chat history."
  "Feed grid":
    type: nav
    trigger: [click, scroll, drag]
    description: "Showcase/post card grid; cards open their detail. Infinite-scrolls more items near the bottom; pull down from the top to refresh."
    items:
      "Card follow slot":
        type: toggle
        trigger: click
        description: "Other-user view — inline follow/unfollow prompt rendered within the feed."
  "Agents rail":
    type: nav
    trigger: click
    description: "Desktop right rail (non-agent profiles) listing the user's agents."
    items:
      "Open agent":
        type: button
        trigger: click
        description: "Opens that agent (chat or agent profile); shows a connecting spinner."
      "Show all":
        type: dialog
        trigger: click
        description: "Shown when more than five agents exist; opens the agent-browser dialog for the full list."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
