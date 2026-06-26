---
path: /settings/channels
id: settings-channels
name: Channels
title: Channels
description: OpenClaw channel management — shows the user's Teamily API key and a one-line quick-connect shell script for linking a self-hosted OpenClaw (2026.3.8+); polls connected deployments every 10s and, when there is a platform-hosted claw and the subscription is not Active, surfaces a VM-suspension warning card.
relationship:
  upstream: "/, /settings"
  downstream: "/pricing"
cta:
  "Toggle API key visibility":
    type: toggle
    trigger: click
    description: "Eye / eye-off button that reveals or masks the Teamily API key; disabled until a key is available."
  "Copy API key":
    type: button
    trigger: click
    description: "Copies the Teamily API key to the clipboard (toasts success, or error if unavailable/copy fails); shows a check icon briefly after copying. Disabled when no key."
  "Copy connect script":
    type: button
    trigger: click
    description: "Copy control on the quick-connect code block; copies the full OpenClaw connect shell command to the clipboard."
  "Platform-VM warning card":
    type: nav
    trigger: click
    description: "Shown when the subscription is Canceled/Expired and a platform-hosted claw exists; warns that platform VMs will be suspended and data deleted after 14 days."
    items:
      "Renew Now / Manage Subscription":
        type: button
        trigger: click
        description: "Primary action (label depends on expired vs canceled) — closes the settings panel and navigates to /pricing."
      "Export Data":
        type: button
        trigger: click
        description: "Secondary action to export platform-VM data before deletion."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
