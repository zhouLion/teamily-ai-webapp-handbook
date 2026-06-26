---
path: /dev/group-message-cases
id: dev-group-message-cases
name: Group Message Cases
title: Group message cases (mock)
description: Developer-only preview page that renders the group-message custom message components against selectable mock fixtures, to verify GroupMessageStartRender, the before-cutoff card, and the streaming-card layouts; no real data or navigation.
relationship:
  upstream: ""
  downstream: ""
cta:
  "Case select":
    type: select
    trigger: click
    description: "Dropdown of ~18 mock case IDs (loading, completed variants with 0/1/2/3+ files & follow-ups, text-only, running with/without steps, streaming overlay/media-scroll/text-collapsible/waiting, failed, stopped, pending); switching it rebuilds the mock snapshot/stream state and re-renders the before-cutoff card plus the media-vs-text start-render preview below."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
