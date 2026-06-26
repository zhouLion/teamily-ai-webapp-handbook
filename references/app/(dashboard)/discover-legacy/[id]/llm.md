---
path: /discover-legacy/[id]
id: discover-legacy-id
name: Discover Legacy Agent Detail
title: Agent Details
description: Legacy full-page agent detail (mobile target of a discover card tap) rendering the rating view — agent info, score/category/users, conversation starters, reviews, and a review form.
relationship:
  upstream: "/discover-legacy"
  downstream: "/discover, /chat, /callback/chat, /login"
cta:
  "Back":
    type: button
    trigger: click
    description: "Back arrow that routes to /discover on mobile."
  "Copy Link":
    type: button
    trigger: click
    description: "Copies the agent's share URL (/agent/<name>) to the clipboard."
  "Try Agent":
    type: button
    trigger: click
    description: "Subscribes then opens a chat with the agent (-> /chat); signed-out users are sent to /login?from=/callback/chat."
  "Conversation starter chip":
    type: button
    trigger: click
    description: "Prefilled prompt that launches a chat with the agent using that prompt; signed-out users are sent to /login?from=/callback/chat."
  "Open rating form":
    type: button
    trigger: click
    description: "Edit/comment button that reveals the star + comment form; signed-out users are sent to /login?from=/discover."
  "Star rating":
    type: button
    trigger: click
    description: "Tap a 1-5 star to set the rating (animated)."
  "Comment field":
    type: input
    trigger: input
    description: "Textarea for the review text."
  "Submit review":
    type: button
    trigger: click
    description: "Posts a new comment or updates an existing one (disabled until a rating and comment exist), then refreshes the view."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
