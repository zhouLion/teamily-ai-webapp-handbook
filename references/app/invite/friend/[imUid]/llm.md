---
path: /invite/friend/[imUid]
id: invite-friend-imUid
name: Accept Friend Invitation
title: Accept Friend Invitation
description: Friend-invitation acceptance page keyed by the inviter's IM user ID (same flow as /invite/[imUid], with friend-specific OpenGraph metadata); shows the inviter and signed-in user as connecting avatars and an Accept button that sends a friend request then auto-opens the chat — already-friend or self links redirect straight to the conversation, and signed-out visitors are routed to login.
relationship:
  upstream: ""
  downstream: "/chat, /login, /about/terms-of-service, /about/privacy-policy, /"
cta:
  "Accept Invitation button":
    type: button
    trigger: click
    description: "Primary card button — sends the friend request (inviteFriend) for the inviter's IM uid then auto-opens the chat after success; if signed out it redirects to /login, blocks a self-link, and toasts on invalid/lookup errors."
  "Terms of Service link":
    type: link
    trigger: click
    description: "Fine-print link under the button opening /about/terms-of-service."
  "Privacy Policy link":
    type: link
    trigger: click
    description: "Fine-print link under the button opening /about/privacy-policy."
  "Header":
    type: nav
    trigger: click
    description: "Sticky top bar with the Teamily.ai brand and account controls."
    items:
      "Brand logo":
        type: link
        trigger: click
        description: "Teamily.ai logo/name linking back to the home page (/)."
      "Sign In button":
        type: button
        trigger: click
        description: "Shown when signed out; redirects to /login with the current path as the return URL."
      "User avatar":
        type: button
        trigger: click
        description: "Shown when signed in; displays the current user's avatar pill."
      "Close button":
        type: link
        trigger: click
        description: "X icon linking back to the home page (/)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
