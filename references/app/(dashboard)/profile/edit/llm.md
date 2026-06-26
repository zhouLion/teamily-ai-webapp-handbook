---
path: /profile/edit
id: profile-edit
name: Edit Profile
title: Edit Profile
description: Single-column form for the signed-in user to edit their own Teamily profile — avatar (pick + crop upload), public info (display name, @handle with validation and change-quota, bio, tags), details (gender, location, website), and a read-only private-info block (email). A sticky header carries Back and a Save action that persists the dirty draft and returns.
relationship:
  upstream: "/, /me, /profile/[uid], /settings"
  downstream: ""
cta:
  "Back":
    type: button
    trigger: click
    description: "Sticky-header arrow that returns to the previous page without saving."
  "Save":
    type: button
    trigger: click
    description: "Saves all edited fields, toasts success, and navigates back; disabled until the draft is dirty (and while saving, uploading, or when a handle change is quota-blocked)."
  "Avatar / Change photo":
    type: button
    trigger: click
    description: "Camera button or Change photo link opens the OS image picker; non-GIFs go through the crop dialog, then upload and update the avatar."
    items:
      "Crop avatar":
        type: dialog
        trigger: click
        description: "Avatar crop dialog (skipped for GIFs); confirming uploads the cropped image."
  "Name":
    type: input
    trigger: input
    description: "Display-name field with a character counter against the max length."
  "Username (@handle)":
    type: input
    trigger: input
    description: "Edits the @handle (normalized on input) with local validation errors and a change-quota label; disabled once the quota is exhausted for an existing handle."
  "Bio":
    type: input
    trigger: input
    description: "Multi-line bio textarea with a character counter."
  "Tags":
    type: input
    trigger: [input, click]
    description: "Adds a tag on Enter, comma, or the plus button (deduped, capped by tag count/length); each tag chip has an X to remove it."
  "Gender":
    type: select
    trigger: click
    description: "Popover selector for Not set / Male / Female / Other."
  "Location":
    type: input
    trigger: input
    description: "Free-text location field."
  "Website":
    type: input
    trigger: input
    description: "Free-text website field."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
