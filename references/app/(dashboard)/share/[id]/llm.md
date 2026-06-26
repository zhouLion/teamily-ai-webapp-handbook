---
path: /share/[id]
id: share-id
name: Shared Thread
title: Shared Conversation
description: Public, read-only replay of an agent conversation identified by thread id — renders the messages, tool calls, and workspace artifacts with floating playback controls; the composer, agent/model selection, history, and new-task actions are all hidden, and an unknown/removed thread toasts "conversation not found" before redirecting home.
relationship:
  upstream: ""
  downstream: "/"
cta:
  "Playback controls":
    type: nav
    trigger: click
    description: "Floating pill of replay controls anchored at the bottom (re-centers when the workspace panel is open), driving step-by-step playback of the recorded conversation."
    items:
      "Play / pause replay":
        type: toggle
        trigger: click
        description: "Toggles automatic playback of messages at the chosen speed; disabled once the replay reaches the end."
      "Previous message":
        type: button
        trigger: click
        description: "Steps back one message; disabled at the start of the conversation."
      "Next message":
        type: button
        trigger: click
        description: "Steps forward one message; disabled at the end of the conversation."
      "Playback speed":
        type: select
        trigger: click
        description: "Chooses auto-playback speed: 1x, 1.5x, 2x, 3x, or 4x."
      "Skip to end":
        type: button
        trigger: click
        description: "Jumps to the final message, revealing the full conversation."
  "Shared header":
    type: nav
    trigger: click
    description: "Top bar showing the project name with a 'Shared' badge; rename, history, new-task, and stop-agent actions are suppressed in shared mode."
    items:
      "Toggle workspace preview":
        type: toggle
        trigger: click
        description: "Laptop icon (also CMD+I) that opens/closes the right-side workspace preview panel showing the agent's tool calls and artifacts."
  "Workspace preview panel":
    type: dialog
    trigger: click
    description: "Right-side resizable panel (full-screen overlay on mobile) syncing to the current playback step; shows the tool call / artifact for the active message with navigation across tool calls."
    items:
      "Navigate tool calls":
        type: button
        trigger: click
        description: "Previous/next controls to step through the recorded tool calls; the active tool stays in sync with the message being replayed."
      "Open file in viewer":
        type: button
        trigger: click
        description: "Opens a file referenced by a tool call in the full file viewer modal."
      "Close panel":
        type: button
        trigger: click
        description: "Dismisses the workspace preview panel."
  "File viewer":
    type: dialog
    trigger: click
    description: "Full file viewer modal for workspace artifacts produced during the conversation (read-only)."
    items:
      "Navigate files":
        type: button
        trigger: click
        description: "Previous/next controls to move between files in the workspace."
      "Download file":
        type: button
        trigger: click
        description: "Downloads the currently selected file."
      "Download all":
        type: button
        trigger: click
        description: "Zips and downloads all workspace files, with progress feedback."
  "Presentation viewer":
    type: dialog
    trigger: click
    description: "Lazily-loaded full-screen presentation/slides viewer opened when a presentation artifact in the conversation is launched."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
