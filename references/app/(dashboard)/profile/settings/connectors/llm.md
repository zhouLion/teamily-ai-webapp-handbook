---
path: /profile/settings/connectors
id: profile-settings-connectors
name: Connectors Settings
title: Connectors
description: Account-level connectors page — a searchable, single-column list of Composio third-party app toolkits (connected ones sorted first, a hardcoded set of slugs hidden) where each card can Connect (creates a credential profile and opens an OAuth popup) or Disconnect (deletes the toolkit's credential profile(s)). Has a sticky header with a Back button and the page title.
relationship:
  upstream: "/profile/[uid], /settings"
  downstream: ""
cta:
  "Back":
    type: button
    trigger: click
    description: "Sticky-header arrow that returns to the previous page."
  "Search connectors":
    type: input
    trigger: input
    description: "Filters the Composio toolkit list by keyword."
  "Connect":
    type: button
    trigger: click
    description: "Opens a blank OAuth popup then creates a credential profile for the app and redirects the popup to authorize; refreshes profiles on success, closes the popup on error."
  "Disconnect":
    type: button
    trigger: click
    description: "Connected apps only — deletes all of the toolkit's credential profile(s) (single or bulk) and refreshes the list."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
