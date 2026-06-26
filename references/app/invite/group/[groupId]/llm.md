---
path: /invite/group/[groupId]
id: invite-group-groupId
name: Accept Group Invitation
title: Accept Group Invitation
description: Group-invitation acceptance page keyed by group ID; resolves the group name and shows a Join button that calls joinGroup then auto-opens the group conversation — existing members redirect straight in, invalid/unknown groups redirect home, and signed-out visitors are routed to login.
relationship:
  upstream: "/discover, /discover/groups"
  downstream: "/chat, /login, /about/terms-of-service, /about/privacy-policy, /"
cta:
  "Join Group button":
    type: button
    trigger: click
    description: "Primary card button — joins the group (joinGroup) by its ID then auto-opens the group conversation after success; if signed out it redirects to /login and toasts on invalid/join errors."
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
