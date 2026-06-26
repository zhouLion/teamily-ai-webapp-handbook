---
path: /contact/phone-contacts
id: contact-phone-contacts
name: Phone Contacts
title: Phone Contacts
description: Browses contacts synced from the user's phone, split into "On Teamily" (registered, openable in chat) and "Invite to Teamily" (unregistered) sections; shows an empty state with app-download links when nothing is synced.
relationship:
  upstream: "/contact"
  downstream: "/chat"
cta:
  "Back to contacts":
    type: button
    trigger: click
    description: "Mobile-only back arrow in the header; navigates (replace) to /contact."
  "Registered contact row":
    type: button
    trigger: click
    description: "On an On-Teamily contact; opens (or creates) the IM conversation with them and navigates to /chat."
  "Contact avatar":
    type: button
    trigger: click
    description: "On a registered contact; opens the user-info dialog instead of jumping to chat."
  "Invite button":
    type: button
    trigger: click
    description: "On an unregistered contact; shares via Web Share, falls back to an SMS draft on mobile, else copies a personalized invite link to join Teamily; shows a spinner while pending."
  "Match-unavailable retry":
    type: button
    trigger: click
    description: "Inline banner shown when Teamily matches can't be resolved; retries the contacts lookup."
  "Error retry":
    type: button
    trigger: click
    description: "Shown when the contacts list fails to load; retries the fetch."
  "Download app links":
    type: link
    trigger: click
    description: "Empty-state iOS / Android buttons opening the app-store download links in a new tab (contacts sync requires the mobile app)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
