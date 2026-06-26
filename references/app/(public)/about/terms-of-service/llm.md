---
path: /about/terms-of-service
id: about-terms-of-service
name: Terms of Service
title: Terms of Service - Teamily AI
description: Renders the terms-of-service markdown (platform rules and guidelines covering subscriptions, billing, credits, and user responsibilities) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer.
relationship:
  upstream: "/, /i/[invite_code], /login, /pricing, /region-restricted, /settings, /support"
  downstream: "/, /pricing, /about, /about/help-center, /about/privacy-policy"
cta:
  "Table of contents":
    type: nav
    trigger: click
    description: "Sticky right-side TOC of the article headings (desktop lg+ only); click an entry to smooth-scroll to that section and highlight it as active."
  "Copy heading link":
    type: button
    trigger: click
    description: "Clicking any H1-H3 heading in the content copies its anchor URL to the clipboard and updates the page hash."
  "Site footer":
    type: nav
    trigger: click
    description: "Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal."
    items:
      "Logo / Teamily.ai":
        type: link
        trigger: click
        description: "Logo and the Teamily.ai link both navigate to the home page (/)."
      "Pricing":
        type: link
        trigger: click
        description: "Navigates to /pricing."
      "About":
        type: link
        trigger: click
        description: "Navigates to /about."
      "Help Center":
        type: link
        trigger: click
        description: "Navigates to /about/help-center."
      "Privacy Policy":
        type: link
        trigger: click
        description: "Navigates to /about/privacy-policy."
      "Terms of Service":
        type: link
        trigger: click
        description: "Navigates to /about/terms-of-service (this page)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
