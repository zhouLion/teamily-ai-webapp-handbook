---
path: /settings/creator-center
id: settings-creator-center
name: Creator Center
title: Creator Center
description: Creator earnings hub — an earnings hero with the cash balance plus withdraw entry, a 4-step How-It-Works guide with Start-Creating CTAs, a static engagement rewards ladder (100/1000/10000 engagements → $CASH), recent per-post earnings, and a creator-earnings FAQ accordion.
relationship:
  upstream: "/, /settings, /settings/withdraw, /chat"
  downstream: "/settings/withdraw, /chat, /discover"
cta:
  "Earnings hero":
    type: nav
    trigger: click
    description: "Green balance card showing the current cash balance plus pending / lifetime / card-linked status chips."
    items:
      "Withdraw":
        type: button
        trigger: click
        description: "Routes to /settings/withdraw when the withdraw-entry flag is on; otherwise opens the 'coming soon' dialog (fires a withdraw-blocked event)."
  "How it works":
    type: nav
    trigger: click
    description: "4-step earnings explainer (Start creating → Publish → Engage → Get paid); a vertical timeline on mobile, stepped layout on desktop."
    items:
      "Create with Personal AI":
        type: link
        trigger: click
        description: "Start-creating option that links to /chat."
      "Create with Agent":
        type: button
        trigger: click
        description: "Start-creating option that opens the Create Artifacts modal on the agents tab."
      "Remix your own":
        type: link
        trigger: click
        description: "Start-creating option that links to /discover."
  "Rewards ladder info":
    type: button
    trigger: click
    description: "Info button beside the ladder heading; opens a popover explaining how engagement-based earning works (fires a tier-popover-opened event)."
  "FAQ accordion":
    type: toggle
    trigger: click
    description: "Single-open accordion of six creator-earnings FAQ items; tapping a question expands its answer."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
