---
path: /settings/privacy
id: settings-privacy
name: Privacy
title: Privacy
description: Privacy settings page that loads the current profile privacy view-model and lets the owner toggle whether their liked posts and bookmarked/saved posts are publicly visible, then save the changes (saving is enabled only when a toggle differs from the loaded state).
relationship:
  upstream: "/settings"
  downstream: ""
cta:
  "Likes visible toggle":
    type: toggle
    trigger: click
    description: "Switch controlling whether your liked posts are publicly visible on your profile; disabled while loading or saving."
  "Bookmarks visible toggle":
    type: toggle
    trigger: click
    description: "Switch controlling whether your saved/bookmarked posts are publicly visible on your profile; disabled while loading or saving."
  "Save changes":
    type: button
    trigger: click
    description: "Persists the changed toggles via the privacy API and syncs the profile-header cache; disabled until a toggle changes, shows a spinner while saving, and toasts success/failure."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
