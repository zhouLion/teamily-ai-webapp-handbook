---
path: /settings
id: settings-layout
name: Settings Layout
title: Settings Layout
description: Chrome for settings sub-pages — wraps each sub-page in a max-width column with a sticky header (localized title + Back button) and an enter motion transition; at the /settings root it is a pure pass-through that renders the hub with no header.
relationship:
  upstream: ""
  downstream: "/settings"
cta:
  "Sub-page header":
    type: nav
    trigger: click
    description: "Sticky top header shown on every settings sub-page (not the /settings root), displaying the localized sub-page title."
    items:
      "Back button":
        type: button
        trigger: click
        description: "Arrow-left control; navigates back in in-app history when available, otherwise falls back to the /settings root."
---

<!-- 正文待补充:后续人工补充该布局的详细介绍 -->
