---
path: /ui/wip
id: ui-wip
name: WIP Playbooks
title: WIP Playbooks
description: Internal work-in-progress workbench with a collapsible left nav that switches between UI playbooks (Usage Overview, Model Routing Table, Platform VM Warning, Bunny Storage Upload, Audio Preview, Onboarding Message V2), each rendering a live component preview alongside a collapsible right-side mini-controls panel.
relationship:
  upstream: ""
  downstream: ""
cta:
  "Playbook nav":
    type: nav
    trigger: click
    description: "Collapsible left sidebar listing the playbooks; tap an item to make it the active preview."
    items:
      "Select playbook":
        type: button
        trigger: click
        description: "Switches the active playbook to Usage Overview, Model Routing Table, Platform VM Warning, Bunny Storage Upload, Audio Preview, or Onboarding Message V2."
      "Collapse sidebar":
        type: toggle
        trigger: click
        description: "Chevron button that collapses/expands the left nav (icon-only when collapsed)."
  "Toggle controls":
    type: toggle
    trigger: click
    description: "Top-bar panel button that shows/hides the active playbook's right-side mini-controls panel."
  "Playbook controls":
    type: nav
    trigger: click
    description: "Per-playbook mini-controls panel (visible when controls are shown): preset buttons plus mini select/range/text inputs that mutate the previewed component's state."
    items:
      "Apply preset":
        type: button
        trigger: click
        description: "Preset buttons that load a predefined state for the active playbook (Usage Overview, Platform VM Warning, Audio Preview)."
      "Tweak field":
        type: select
        trigger: [click, input]
        description: "Mini select/range/text controls that adjust the previewed component's props (e.g. credits state, VM status, audio source)."
      "Upload file":
        type: button
        trigger: click
        description: "Bunny Storage Upload playbook — file picker / drop zone that uploads a selected file to Bunny storage."
      "Remount preview":
        type: button
        trigger: click
        description: "Re-renders the previewed component (Audio Preview player remount, Onboarding Message V2 nonce bump)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
