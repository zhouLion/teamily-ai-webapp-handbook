---
path: /(public)
id: public-layout
name: Public Layout
title: Public Layout
description: Chrome for public / signed-out routes (pricing, about, support, login, invite landing, features) — a sticky top nav with an optional history back button, a home logo, and either an avatar shortcut into the app (signed in) or a Login button (signed out). The whole bar is hidden on embedded views.
relationship:
  upstream: ""
  downstream: "/, /chat, /login"
cta:
  "Top nav bar":
    type: nav
    trigger: click
    description: "Sticky, blur-backed top navigation bar; hidden entirely on embedded views (data-hide-on-embed / useIsEmbedded)."
    items:
      "Back button":
        type: button
        trigger: click
        description: "Shown only when in-app history exists (useCanGoBack); navigates back one step via router.back()."
      "Home logo":
        type: link
        trigger: click
        description: "Favicon image plus a home icon (home icon shown sm+) linking to / (landing/home)."
      "Avatar shortcut":
        type: link
        trigger: click
        description: "Signed-in only — the user's avatar (or initials fallback) links to /chat to jump into the app."
      "Login button":
        type: link
        trigger: click
        description: "Shown when signed out (and not already on /login) — links to /login."
---

<!-- 正文待补充:后续人工补充该布局的详细介绍 -->
