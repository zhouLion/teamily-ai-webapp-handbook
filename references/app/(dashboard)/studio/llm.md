---
path: /studio
id: studio
name: Studio
title: Studio
description: Standalone collaborative artifact workspace bound to URL params (artifact_ref, artifact_type, mode, conversation, thread, selection, surface) — renders the same studio surface the chat drawer uses (header + mode toolbar + canvas + adapter composer/context slot) with comments, markup, and edit modes, live presence, and webpage version switching; invalid params render a route-error page.
relationship:
  upstream: "/chat"
  downstream: "/chat"
cta:
  "Studio header":
    type: nav
    trigger: click
    description: "Top bar: artifact type icon, artifact title, live-viewer avatars, version pill, share, and (on the standalone page) a left close button."
    items:
      "Live viewer avatars":
        type: button
        trigger: [click, hover]
        description: "Stack of present collaborators (presence-capable surfaces only); hover shows identity/status/mode, click follows that peer (scrolls to and tints their cursor), click again unfollows; a colored dot shows realtime connection health (live/degraded/connecting)."
      "Version picker":
        type: menu
        trigger: click
        description: "Version pill; for versioned webpage artifacts opens a popover listing every version (newest first) and switches the preview via URL replace on select; static v1 pill for other artifact types."
      "Share":
        type: dialog
        trigger: click
        description: "Opens the share-link popover for the artifact_ref; disabled when no artifact_ref."
      "Close studio":
        type: button
        trigger: click
        description: "Left close button; pops the native WebView (bridge mode) or goes back in browser history, returning toward /chat."
  "Mode toolbar":
    type: nav
    trigger: click
    description: "Toolbar under the header; mode buttons appear only for capabilities the artifact adapter declares (disabled/coming-soon types collapse it entirely)."
    items:
      "Refresh preview":
        type: button
        trigger: click
        description: "Reloads the artifact preview/canvas."
      "Comments mode":
        type: toggle
        trigger: click
        description: "Toggles comments mode (opens the comments panel/dock); a badge shows the open comment count; clicking the active mode returns to mode none."
      "Markup mode":
        type: toggle
        trigger: click
        description: "Toggles free-draw markup mode (brush strokes over the canvas); disables native swipe-to-go-back while active."
      "Edit mode":
        type: toggle
        trigger: click
        description: "Toggles edit mode for editable artifacts; shell forces 100% zoom in edit except for html/webpage (and self-managed-zoom adapters like markdown/slides)."
      "Zoom level":
        type: menu
        trigger: click
        description: "Opens a zoom menu (25-400% presets plus a custom numeric input committed on Enter/blur); hidden in edit mode when the adapter forces 100%."
      "Fullscreen":
        type: toggle
        trigger: click
        description: "Soft-maximize the surface over the page (fixed overlay, browser chrome kept); Escape exits; desktop only."
      "Collapse header":
        type: button
        trigger: click
        description: "Folds the header and toolbar into a thin strip exposing only an expand chevron."
  "Expand header":
    type: button
    trigger: click
    description: "Floating chevron shown when the chrome is collapsed; restores the header and mode toolbar."
  "Artifact canvas":
    type: nav
    trigger: [click, scroll, drag]
    description: "Adapter-rendered main view (html/webpage, slides, markdown, sheet, image, design, url, tree); interactions vary by adapter and active mode — comment pins, markup brush strokes, inline editing, slide navigation, zoom-pan."
  "Adapter composer":
    type: input
    trigger: [click, input]
    description: "Optional bottom composer rendered by the artifact adapter (e.g. add-comment / send-to-agent input); send-to-agent and mentions target the conversation named in the URL and degrade gracefully when it is absent or unresolvable."
  "Context slot":
    type: nav
    trigger: click
    description: "Optional right-side panel rendered by the adapter (e.g. comments list / inspector) on wider layouts; on mobile the mode panel becomes a collapsible bottom sheet instead of a side split."
  "Route error":
    type: link
    trigger: click
    description: "When artifact_ref/artifact_type/mode are missing or invalid the page shows an error with title/detail and a 'Back to chat' link to /chat."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
