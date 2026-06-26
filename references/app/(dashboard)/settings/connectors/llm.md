---
path: /settings/connectors
id: settings-connectors
name: Connectors
title: Connectors
description: Account-level connectors directory — a single-column, searchable list of Composio toolkits (third-party apps) the user can Connect (OAuth popup creates a credential profile) or Disconnect (deletes the credential profile); connected apps sort to the top and a hardcoded slug set is hidden.
relationship:
  upstream: "/, /settings, /chat"
  downstream: ""
cta:
  "Search apps":
    type: input
    trigger: input
    description: "Filters the toolkit list by name (sent as the server-side search query); empty shows all visible toolkits."
  "Connect app":
    type: button
    trigger: click
    description: "Shown on a disconnected app — opens a blank popup, POSTs a new Composio credential profile, and redirects the popup to the returned OAuth URL; refreshes profiles on success, closes the popup on error. Shows a spinner while pending."
  "Disconnect app":
    type: button
    trigger: click
    description: "Shown on a connected app — deletes all credential profiles for that toolkit slug (single or bulk delete), toasts success/partial/failure, and refreshes the list. Shows a spinner while pending."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
