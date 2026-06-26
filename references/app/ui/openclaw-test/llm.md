---
path: /ui/openclaw-test
id: ui-openclaw-test
name: OpenClaw Test
title: OpenClaw Test
description: Internal dev/test page to deploy a new OpenClaw GCP instance, list/select existing deployments, inspect a deployment's details, and manage it (terminal, auto-repair, restart, token, destroy) via the embedded ClawSetting panel.
relationship:
  upstream: ""
  downstream: ""
cta:
  "My Deployments list":
    type: nav
    trigger: click
    description: "Left-column card listing the user's deployments; each row shows name, status badge, and short id."
    items:
      "Refresh list":
        type: button
        trigger: click
        description: "Reloads the deployments list (spins while loading)."
      "Select deployment":
        type: button
        trigger: click
        description: "Tapping a row makes that deployment active in the right-column detail panel."
      "Destroy deployment":
        type: dialog
        trigger: click
        description: "Per-row trash button (shown on hover) that opens a confirm dialog; confirming permanently deletes the GCP VM and removes it from the list."
  "New Deployment form":
    type: nav
    trigger: click
    description: "Left-column card for creating a new OpenClaw instance on GCP."
    items:
      "Name input":
        type: input
        trigger: input
        description: "Text field for the deployment name (disabled while deploying/polling)."
      "Template select":
        type: select
        trigger: click
        description: "Dropdown to choose a template (loaded from listTemplates; hidden when none available)."
      "Deploy":
        type: button
        trigger: click
        description: "Creates the deployment and polls every 5s up to 10 min until running; logs progress and disables while in flight (requires a name)."
      "Reset":
        type: button
        trigger: click
        description: "Refresh-icon button (shown after ready/error) that clears the active deployment, log, and error and returns to idle."
  "Deployment detail":
    type: nav
    trigger: click
    description: "Right-column card shown when a deployment is active: status icon, name, and a details grid (id, status, region, machine, storage, model, gateway URL)."
    items:
      "ClawSetting panel":
        type: nav
        trigger: click
        description: "Collapsible OpenClaw Settings section (expand via header) with platform-managed instance actions."
        items:
          "Open Terminal":
            type: button
            trigger: click
            description: "Connects to the instance shell and opens the web-terminal dialog (requires running status)."
          "Auto-Repair":
            type: dialog
            trigger: click
            description: "Opens the ClawRepairDialog to diagnose and fix common issues."
          "Restart":
            type: dialog
            trigger: click
            description: "Opens a confirm dialog to restart the instance (requires running status)."
          "Token Management":
            type: dialog
            trigger: click
            description: "Opens the refresh-token dialog to view and regenerate the instance token."
          "Destroy":
            type: dialog
            trigger: click
            description: "Opens a confirm dialog to permanently delete the instance and all data."
          "Web terminal dialog":
            type: dialog
            trigger: click
            description: "Full xterm shell over WebSocket; Escape is blocked and it closes via its own close control."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
