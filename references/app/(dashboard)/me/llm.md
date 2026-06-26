---
path: /me
id: me
name: My Profile Redirect
title: My Profile
description: Redirect-only page that sends the signed-in user to their own profile (/profile/{imUid}?source=me, preserving share=1), or to /profile/edit when signed out; renders only a background/loading placeholder while resolving.
relationship:
  upstream: "/, /chat, /profile/[uid]"
  downstream: "/profile/[uid], /profile/edit"
cta: {}
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
