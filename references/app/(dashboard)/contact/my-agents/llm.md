---
path: /contact/my-agents
id: contact-my-agents
name: My Agents
title: My Agents
description: Lists the user's saved AI agents in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog.
relationship:
  upstream: "/contact"
  downstream: "/chat, /contact"
cta:
  "Back to contacts":
    type: button
    trigger: click
    description: "Mobile-only back arrow in the header; navigates (replace) to /contact."
  "Agent list item":
    type: button
    trigger: click
    description: "Tapping an agent row opens the user-info dialog for that agent."
  "Alphabet index":
    type: nav
    trigger: [click, drag, longpress]
    description: "A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter."
  "User info dialog":
    type: dialog
    trigger: click
    description: "Opened from an agent row; shows avatar/name/badge with a primary action."
    items:
      "Send message":
        type: button
        trigger: click
        description: "Shown for an agent already added as a friend; opens (or creates) the conversation and navigates to /chat."
      "Add friend":
        type: button
        trigger: click
        description: "Shown when the agent is not yet added; sends a friend request and adds the agent to ADP (disabled / shows Private for Claw agents)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
