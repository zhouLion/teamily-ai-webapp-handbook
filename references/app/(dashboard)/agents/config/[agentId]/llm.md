---
path: /agents/config/[agentId]
id: agents-config-agentId
name: Agent Settings
title: Agent Settings
description: Single-screen editor for one of your agents (loaded by agentId) — edit its avatar, name, and description, save the changes, or delete the agent from a danger zone; a sticky header carries Back and Save.
relationship:
  upstream: "/profile/[uid], /chat, /me, /settings"
  downstream: "/settings, /me, /profile/[uid]"
cta:
  "Header bar":
    type: nav
    trigger: click
    description: "Sticky top bar with the page title, a Back control, and the Save action."
    items:
      "Back":
        type: button
        trigger: click
        description: "Left arrow that calls the onBack handler if provided, otherwise navigates back in history (router.back())."
      "Save":
        type: button
        trigger: click
        description: "Persists changed name/description/avatar via updateAgent (only changed fields sent); disabled until the draft is dirty and while loading/saving/uploading; shows a spinner while saving."
  "Avatar editor":
    type: nav
    trigger: click
    description: "Top avatar block showing the current agent icon with edit affordances."
    items:
      "Change avatar (camera)":
        type: button
        trigger: click
        description: "Camera button over the avatar that opens the OS image file picker (image/* only); shows a spinner while uploading."
      "Change Photo":
        type: button
        trigger: click
        description: "Text button below the avatar that opens the same image file picker."
      "Avatar crop dialog":
        type: dialog
        trigger: click
        description: "Opens after picking a non-GIF image to crop it to a 1:1 square before upload; GIFs skip cropping and upload directly."
        items:
          "Zoom slider":
            type: input
            trigger: [input, drag]
            description: "Range slider (100%–300%) that zooms the crop region; the cropper is also pannable by drag."
          "Cancel crop":
            type: button
            trigger: click
            description: "Discards the crop and closes the dialog without uploading."
          "Save crop":
            type: button
            trigger: click
            description: "Renders the cropped square, uploads it, and sets it as the draft avatar (shows a processing state)."
  "Nickname input":
    type: input
    trigger: input
    description: "Text field editing the agent's display name; required (Save errors if blank)."
  "Description input":
    type: input
    trigger: input
    description: "Textarea editing the agent's description."
  "Delete agent":
    type: button
    trigger: click
    description: "Danger-zone button that opens a confirmation dialog; on confirm, permanently deletes the agent."
    items:
      "Delete confirmation dialog":
        type: dialog
        trigger: click
        description: "Confirm dialog naming the agent; Cancel dismisses it, Delete calls deleteAgent and on success redirects to the owner's profile (/settings on mobile, profile/me page on desktop)."
        items:
          "Cancel":
            type: button
            trigger: click
            description: "Closes the dialog without deleting."
          "Delete (confirm)":
            type: button
            trigger: click
            description: "Permanently deletes the agent, removes it from cached agent lists, then redirects to the owner's profile."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
