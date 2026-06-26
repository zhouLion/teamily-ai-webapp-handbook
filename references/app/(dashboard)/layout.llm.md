---
path: /(dashboard)
id: dashboard-layout
name: Dashboard Layout (App Shell)
title: Dashboard Layout (App Shell)
description: The app shell wrapping every dashboard route — desktop renders the left icon rail (primary nav + footer utility rail + account/info menu) and mobile renders a bottom tab bar on primary pages; it also hosts the parallel modal slot and the mobile download-app dialog, while embedded (RN WebView / iframe) requests skip all chrome.
relationship:
  upstream: ""
  downstream: "/chat, /login, /discover, /automations, /explore, /memory, /me, /contact, /download, /settings, /settings/language, /settings/usage, /settings/subscription, /settings/creator-center, /settings/affiliate, /settings/channels, /settings/connectors, /profile/edit, /credits, /get-started, /pricing, /about, /about/refund-policy, /about/terms-of-service, /about/privacy-policy, /about/help-center"
cta:
  "Sidebar rail":
    type: nav
    trigger: click
    description: "Desktop-only left icon rail (md+): logo, primary nav, footer utility rail, and the account/info menu; hidden on mobile and on embed."
    items:
      "Logo":
        type: link
        trigger: click
        description: "Teamily logo; links to the signed-in user's own profile (/me) when logged in, otherwise /."
      "Chat nav":
        type: button
        trigger: [click, hover]
        description: "Opens /chat (or /login when signed out); shows an unread-message badge. On a chat route while signed in, clicking toggles the conversation-list panel open/closed (icon swaps to a panel-collapse/expand glyph on hover) instead of navigating."
      "Agents nav":
        type: link
        trigger: click
        description: "Navigates to /discover?tab=agents (Discover's Agents tab); active only when that tab is selected."
      "Automations nav":
        type: link
        trigger: click
        description: "Navigates to /automations (signed-in only)."
      "Discover nav":
        type: link
        trigger: click
        description: "Navigates to /discover (agent + content discovery)."
      "Explore nav":
        type: link
        trigger: click
        description: "Navigates to /explore (social feed); resets the explore feed session on click."
      "Memory nav":
        type: link
        trigger: click
        description: "Navigates to /memory (the wiki/memory space, signed-in only); shows a wiki-updates count badge."
      "Me nav":
        type: link
        trigger: click
        description: "Navigates to the signed-in user's own profile (/me → /profile/<imUid>); shows a social-notifications unread badge (signed-in only)."
      "Download (footer)":
        type: link
        trigger: [click, hover]
        description: "Footer rail icon linking to /download (native apps); tooltip on hover."
      "Language (footer)":
        type: link
        trigger: [click, hover]
        description: "Footer rail icon linking to /settings/language; tooltip on hover."
      "Usage (footer)":
        type: menu
        trigger: click
        description: "Footer plan-name pill (signed-in only) opening a mini usage-overview popover."
        items:
          "Upgrade":
            type: button
            trigger: click
            description: "Navigates to /pricing."
          "View details":
            type: button
            trigger: click
            description: "Navigates to /settings/usage."
      "Credits / Get-started (footer)":
        type: link
        trigger: [click, hover]
        description: "Footer gift icon (signed-in only); links to /get-started while onboarding tasks remain (pulsing badge with remaining count), otherwise to the credits center (/credits)."
      "Account menu":
        type: menu
        trigger: click
        description: "Signed-in only — avatar/menu button opening a rich account dropdown."
        items:
          "View my profile":
            type: link
            trigger: click
            description: "User card (avatar, name, email) linking to the user's own profile (/profile/<imUid>)."
          "Account & profile":
            type: button
            trigger: click
            description: "Navigates to /profile/edit."
          "Creator center":
            type: button
            trigger: click
            description: "Navigates to /settings/creator-center; shows the creator $CASH balance."
          "Credit center":
            type: button
            trigger: click
            description: "Navigates to the credit-center route; shows the $CREDITs balance."
          "Incentive program":
            type: button
            trigger: click
            description: "Navigates to /settings/affiliate; shows the commission $CASH balance."
          "Plan & billing":
            type: button
            trigger: click
            description: "Navigates to /settings/subscription; shows the current plan name."
          "Usage":
            type: button
            trigger: click
            description: "Navigates to /settings/usage; shows the usage percent."
          "OpenClaw management":
            type: button
            trigger: click
            description: "Navigates to /settings/channels."
          "App connectors":
            type: button
            trigger: click
            description: "Navigates to /settings/connectors."
          "Help":
            type: menu
            trigger: click
            description: "Submenu of help/legal links."
            items:
              "Help center":
                type: link
                trigger: click
                description: "Opens /about/help-center."
              "Download apps":
                type: link
                trigger: click
                description: "Opens /download."
              "Terms of service":
                type: link
                trigger: click
                description: "Opens /about/terms-of-service."
              "Privacy policy":
                type: link
                trigger: click
                description: "Opens /about/privacy-policy."
              "Report a bug":
                type: link
                trigger: click
                description: "mailto bug report to contact@teamily.ai."
          "All settings":
            type: button
            trigger: click
            description: "Navigates to /settings."
          "Social links":
            type: link
            trigger: click
            description: "External links to X, LinkedIn, and Discord (new tab)."
          "Sign out":
            type: button
            trigger: click
            description: "Logs out and redirects to /."
      "Sign in (footer)":
        type: button
        trigger: click
        description: "Signed-out only — replaces the account menu; navigates to /login."
      "Info menu":
        type: menu
        trigger: click
        description: "Signed-out only — gear button opening an info/legal dropdown."
        items:
          "Settings":
            type: link
            trigger: click
            description: "Opens /settings."
          "About":
            type: link
            trigger: click
            description: "Opens /about."
          "Pricing":
            type: link
            trigger: click
            description: "Opens /pricing."
          "Refund policy":
            type: link
            trigger: click
            description: "Opens /about/refund-policy."
          "Terms of service":
            type: link
            trigger: click
            description: "Opens /about/terms-of-service."
          "Privacy policy":
            type: link
            trigger: click
            description: "Opens /about/privacy-policy."
          "Help center":
            type: link
            trigger: click
            description: "Opens /about/help-center."
          "Contact us":
            type: dialog
            trigger: click
            description: "Opens a contact dialog showing the contact@teamily.ai email."
          "Social links":
            type: link
            trigger: click
            description: "External links to X, LinkedIn, and Discord (new tab)."
  "Mobile tab bar":
    type: tabs
    trigger: click
    description: "Bottom navigation shown on mobile primary pages (and when the glueview/thread view is visible); hidden on desktop and on embed."
    items:
      "Chat tab":
        type: link
        trigger: [click, doubleclick]
        description: "Navigates to /chat (or /login when signed out); shows an unread-message badge. Double-tapping while already on Chat scrolls the conversation list to the top."
      "Discover tab":
        type: link
        trigger: click
        description: "Navigates to /discover."
      "Explore tab":
        type: link
        trigger: click
        description: "Navigates to /explore; resets the explore feed session."
      "Contacts tab":
        type: link
        trigger: click
        description: "Navigates to /contact; shows a pending-friend-application badge."
      "Me / Settings tab":
        type: link
        trigger: click
        description: "Signed-in shows the user avatar and navigates to /me (own profile); signed-out shows a gear icon and navigates to /me (Settings)."
  "Modal slot":
    type: dialog
    trigger: click
    description: "Parallel-route @modal slot rendered alongside children for intercepted route modals."
  "Mobile download-app dialog":
    type: dialog
    trigger: click
    description: "Prompt encouraging mobile-web users to install the native app."
---

<!-- 正文待补充:后续人工补充该布局的详细介绍 -->
