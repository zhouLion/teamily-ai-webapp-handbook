---
path: /contact
id: contact
name: Contacts
title: Contacts
description: Contacts landing page — on mobile it renders the alphabetized contact list with a draggable A–Z index jump bar and a user-info dialog; on desktop it defaults to the My Agents list using the shared MyFriends view.
relationship:
  upstream: "/, /contact/my-agents, /contact/my-friends"
  downstream: "/chat, /contact/my-agents, /contact/my-friends, /contact/phone-contacts"
cta:
  "Contact list item":
    type: button
    trigger: click
    description: "Tapping a contact row opens the user-info dialog for that person (avatar, name, plan badge, creator)."
  "Alphabet index":
    type: nav
    trigger: [click, drag, longpress]
    description: "Mobile-only A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter."
  "User info dialog":
    type: dialog
    trigger: click
    description: "Opened from a contact row; shows avatar/name/badge with a primary action."
    items:
      "Send message":
        type: button
        trigger: click
        description: "Shown when the person is already a friend; opens (or creates) the IM conversation and navigates to /chat."
      "Add friend":
        type: button
        trigger: click
        description: "Shown when not yet a friend; sends a friend request and adds the agent to ADP (disabled / shows Private for Claw agents)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
