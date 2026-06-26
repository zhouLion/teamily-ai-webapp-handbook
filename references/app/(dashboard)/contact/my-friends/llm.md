---
path: /contact/my-friends
id: contact-my-friends
name: My Friends
title: My Friends
description: Lists the user's friends in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog.
relationship:
  upstream: "/contact"
  downstream: "/chat, /contact"
cta:
  "Back to contacts":
    type: button
    trigger: click
    description: "Mobile-only back arrow in the header; navigates (replace) to /contact."
  "Friend list item":
    type: button
    trigger: click
    description: "Tapping a friend row opens the user-info dialog for that friend."
  "Alphabet index":
    type: nav
    trigger: [click, drag, longpress]
    description: "A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter."
  "User info dialog":
    type: dialog
    trigger: click
    description: "Opened from a friend row; shows avatar/name/badge with a primary action."
    items:
      "Send message":
        type: button
        trigger: click
        description: "Opens (or creates) the IM conversation with this friend and navigates to /chat."
      "Add friend":
        type: button
        trigger: click
        description: "Shown if the local friendship is stale; sends a friend request and adds the user to ADP."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
