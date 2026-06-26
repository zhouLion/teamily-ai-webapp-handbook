---
path: /callback/chat
id: callback-chat
name: Chat Callback
title: Chat Callback
description: Server-side post-login redirect handler — decodes the base64 q param (model, agentName, prompt, adp_agentId, attachmentsBase64), verifies the auth-token cookie and account, fetches the agent detail, auto-subscribes if not already subscribed, then redirects to /chat with action=startChatAfterLogin; redirects to / when q is missing or any step fails.
relationship:
  upstream: "/login, /chat"
  downstream: "/chat, /"
cta: {}
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
