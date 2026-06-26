---
path: /link/[code]
id: link-code
name: Share Link Viewer
title: Share Link Viewer
description: Public viewer for a shared content code — the server probes the backend /s/{code} target's content type and renders it as a full-screen image, a multi-slide presentation deck, or a sandboxed iframe ("frame"), all under a top bar with copy-link and open-app actions.
relationship:
  upstream: ""
  downstream: "/"
cta:
  "Share viewer top bar":
    type: nav
    trigger: click
    description: "Header above the image/frame content (and reused as the presentation deck's header); hidden when the top bar is collapsed."
    items:
      "Teamily AI logo / Made with":
        type: link
        trigger: click
        description: "Favicon plus a 'Made with Teamily' label (label desktop-only); opens the home page (/) in a new tab."
      "Copy share link":
        type: button
        trigger: click
        description: "Copies the short share URL (origin/link/{code}) to the clipboard, swaps to a check icon for ~1.5s, and shows a success (or failure) toast."
      "Open app":
        type: link
        trigger: click
        description: "Opens the Teamily AI home page (/) in a new tab; full label on desktop, short label on mobile."
  "Image / frame content":
    type: nav
    trigger: click
    description: "Main content area: an image (object-contain) when the target is an image, otherwise a sandboxed iframe of the shared page; an image that fails to load falls back to the iframe."
  "Toggle top bar":
    type: toggle
    trigger: click
    description: "Maximize/minimize button overlaid at the top-right of the content; collapses the top bar for a full-screen view or restores it (image/frame modes only)."
  "Presentation deck viewer":
    type: dialog
    trigger: click
    description: "When the target is a presentation folder, a full-screen slide-deck viewer (lazy-loaded) renders the deck with the shared top bar; its built-in close returns to the previous page (router.back)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
