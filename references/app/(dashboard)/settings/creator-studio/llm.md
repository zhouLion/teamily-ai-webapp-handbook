---
path: /settings/creator-studio
id: settings-creator-studio
name: Creator Studio
title: Creator Studio
description: Creator studio page that currently just renders the account-level Connectors settings (Composio toolkit list) as a placeholder until the agents-management module lands.
relationship:
  upstream: "/, /settings"
  downstream: ""
cta:
  "Search connectors":
    type: input
    trigger: input
    description: "Filters the Composio toolkit list by search term (connected toolkits are sorted first)."
  "Connect":
    type: button
    trigger: click
    description: "Per-toolkit; opens a popup window and creates a Composio credential profile to start the OAuth connect flow."
  "Disconnect":
    type: button
    trigger: click
    description: "Per connected toolkit; deletes all credential profiles for that toolkit (bulk if multiple) and refreshes the list, with a success/partial/error toast."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
