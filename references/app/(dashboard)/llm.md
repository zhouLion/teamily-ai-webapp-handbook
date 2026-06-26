---
path: /
id: home
name: Home
title: Teamily AI - The Personal and Social AI Agent OS to Create, Share, and Explore Anything for Productivity and Creativity
description: The Teamily AI marketing landing/home page (the `tmly-landing` package) — hero with an animated chat demo, founder video, product/architecture/community sections, and a Ghost-backed blog; signed-in visitors are redirected to /chat.
relationship:
  upstream: "/agent/[agent_name], /apply/invite-code, /auth/github, /callback/auto-login, /callback/chat, /callback/stripe/cancel, /callback/stripe/success, /checkout/success, /i/[invite_code], /link/[code], /search, /settings, /settings/withdraw, /share/[id]"
  downstream: "/chat, /discover, /explore, /login, /pricing, /about, /about/help-center, /about/privacy-policy, /about/terms-of-service, /download"
cta:
  "Header nav":
    type: nav
    trigger: click
    description: "Sticky top bar; clicking the logo smooth-scrolls to top, and each entry link fires a landing analytics event via onNavClick."
    items:
      "Agents":
        type: link
        trigger: click
        description: "Links to /discover?tab=agents (deep-links the Discover agents tab)."
      "Discover":
        type: link
        trigger: click
        description: "Links to /discover."
      "Explore":
        type: link
        trigger: click
        description: "Links to /explore."
      "Blog":
        type: link
        trigger: click
        description: "External link to https://blog.teamily.ai/ (opens in a new tab)."
      "Login":
        type: link
        trigger: click
        description: "Primary-styled pill at the end of the nav row that links to /login."
  "Hero download / try-online bar":
    type: nav
    trigger: click
    description: "Row of pills under the hero title (desktop) and in the mobile hero view for getting into the product."
    items:
      "Web":
        type: link
        trigger: click
        description: "Green pill that links to /login to use Teamily in the browser; fires the landing.clicked_try_online event."
      "iOS":
        type: link
        trigger: click
        description: "Links to the configured iOS download URL; alerts 'Coming Soon!' if no URL is set."
      "Android":
        type: link
        trigger: click
        description: "Links to the configured Android download URL; alerts 'Coming Soon!' if no URL is set."
      "macOS":
        type: menu
        trigger: [hover, click]
        description: "Desktop-only dropdown (hidden on phone browsers) offering Apple Silicon and Intel macOS installers."
        items:
          "Apple Silicon":
            type: link
            trigger: click
            description: "Links to the Apple Silicon macOS download URL ('Coming Soon!' alert if unset)."
          "Intel":
            type: link
            trigger: click
            description: "Links to the Intel macOS download URL ('Coming Soon!' alert if unset)."
      "Windows":
        type: link
        trigger: click
        description: "Desktop-only pill (hidden on phone browsers) linking to the Windows installer URL ('Coming Soon!' alert if unset)."
  "Hero chat demo":
    type: nav
    trigger: click
    description: "Interactive (non-functional) mock chat that auto-plays agent task sequences; visitors can switch conversations and the device preview."
    items:
      "Switch conversation":
        type: button
        trigger: click
        description: "Demo sidebar/list entries (Personal AI, Music, My Family, Work Sync, analysis/finance/etc. agents); selecting one resets and replays that conversation's scripted sequence."
      "Device preview toggle":
        type: toggle
        trigger: click
        description: "Desktop-only Desktop/Mobile buttons that swap the mock between a laptop and a phone frame."
      "Back to list":
        type: button
        trigger: click
        description: "In the phone-frame mock, returns from the open chat to the conversation list."
      "Music vinyl player":
        type: dialog
        trigger: click
        description: "Playing a music recommendation opens a spinning vinyl-record overlay; a close button dismisses it."
      "Mobile list teamily.ai links":
        type: link
        trigger: click
        description: "Mobile demo-list rows that open https://teamily.ai in a new tab."
  "Mobile download dialog":
    type: dialog
    trigger: click
    description: "Auto-opens once on phone browsers (suppressed for 30 days after dismissal, and skipped in embedded/native-webview/download-route contexts) prompting to get the mobile app."
    items:
      "OK":
        type: button
        trigger: click
        description: "Opens the platform store URL (iOS/Android) if known, otherwise routes to /download."
      "Ignore":
        type: button
        trigger: click
        description: "Dismisses the dialog and records the dismissal."
  "Founder video section":
    type: nav
    trigger: click
    description: "Embedded YouTube product-introduction video (auto-plays/unmutes when scrolled into view) with a follow-up CTA."
    items:
      "More Use Cases":
        type: link
        trigger: click
        description: "Pill button linking to /discover."
  "Blog section":
    type: nav
    trigger: click
    description: "Ghost-powered blog grid; hidden entirely if the blog feed errors or has no tags."
    items:
      "Show More":
        type: link
        trigger: click
        description: "Header link to the blog home (https://blog.teamily.ai/), opens in a new tab."
      "Tag filter":
        type: tabs
        trigger: click
        description: "Tag pills (desktop) / accordion rows (mobile) that switch the displayed posts to the selected tag."
      "Blog post card":
        type: link
        trigger: click
        description: "Each card links to that post's URL, opening in a new tab."
  "Community social links":
    type: nav
    trigger: click
    description: "Social icon buttons in the Super Community section, each opening in a new tab when configured."
    items:
      "X (Twitter)":
        type: link
        trigger: click
        description: "Opens the configured X/Twitter profile."
      "LinkedIn":
        type: link
        trigger: click
        description: "Opens the configured LinkedIn page."
      "Discord":
        type: link
        trigger: click
        description: "Opens the configured Discord invite."
  "Footer":
    type: nav
    trigger: click
    description: "Site footer with the logo and grouped link columns (Product / Company / Legal)."
    items:
      "Logo / Teamily.ai":
        type: link
        trigger: click
        description: "Logo and 'Teamily.ai' link both navigate to / (home)."
      "Pricing":
        type: link
        trigger: click
        description: "Links to /pricing."
      "About":
        type: link
        trigger: click
        description: "Links to /about."
      "Help Center":
        type: link
        trigger: click
        description: "Links to /about/help-center."
      "Privacy Policy":
        type: link
        trigger: click
        description: "Links to /about/privacy-policy."
      "Terms of Service":
        type: link
        trigger: click
        description: "Links to /about/terms-of-service."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
