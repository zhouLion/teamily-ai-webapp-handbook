---
path: /auth/github
id: auth-github
name: GitHub OAuth Callback
title: Completing GitHub Sign-In
description: Headless GitHub OAuth handoff page that reads the code and state from the callback URL, exchanges the code for a login session (loginChannel 3), then redirects to the state.from target (or /) on success or to /login with a toast on missing code, error, or failure; renders only a "completing sign-in" message.
relationship:
  upstream: "/login"
  downstream: "/, /login"
cta: {}
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
