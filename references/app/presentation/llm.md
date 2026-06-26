---
path: /presentation
id: presentation
name: Presentation Viewer
title: Presentation Viewer
description: Standalone full-screen deck viewer driven by name/sandboxUrl/slide query params; loads slide metadata (with retry/backoff) and renders 16:9 slides in a sandboxed iframe with navigation, keyboard control, export, and a collapsible toolbar (share link disabled on this route).
relationship:
  upstream: "/chat"
  downstream: ""
cta:
  "Toolbar header":
    type: nav
    trigger: click
    description: "Top bar showing logo, deck title, and current 'Slide X of Y'; hidden while the toolbar is collapsed."
    items:
      "Export deck":
        type: menu
        trigger: click
        description: "Download dropdown (disabled while exporting) to render and download the deck; shows 'Exporting (~1 min)' during export."
        items:
          "Export as PDF":
            type: button
            trigger: click
            description: "Renders all slides and downloads the deck as a PDF (~1 minute)."
          "Export as PPTX":
            type: button
            trigger: click
            description: "Exports an editable PPTX (~1 minute); complex slides may fall back to images."
      "Download folder":
        type: button
        trigger: click
        description: "Fetches every slide HTML file, zips them client-side (JSZip), and downloads '<deck>-slides.zip'; shown once slides have loaded."
      "Close full screen":
        type: button
        trigger: click
        description: "X button that calls onClose → router.back() to leave the viewer."
  "Slide stage":
    type: nav
    trigger: click
    description: "Center area rendering the current slide scaled to fit 16:9 inside a sandboxed iframe; shows Loading / Retrying / unavailable states."
    items:
      "Keyboard navigation":
        type: button
        trigger: click
        description: "ArrowLeft/Up = previous slide, ArrowRight/Down/Space = next, Home = first, End = last, Escape = close."
  "Slide controls":
    type: nav
    trigger: click
    description: "Bottom control row for moving through the deck."
    items:
      "First slide":
        type: button
        trigger: click
        description: "SkipBack — jumps to slide 1 (disabled on the first slide)."
      "Previous slide":
        type: button
        trigger: click
        description: "ChevronLeft — goes to the previous slide (disabled on the first slide)."
      "Slide indicators":
        type: button
        trigger: click
        description: "Row of dots; tap a dot to jump directly to that slide (active dot highlighted)."
      "Next slide":
        type: button
        trigger: click
        description: "ChevronRight — goes to the next slide (disabled on the last slide)."
      "Last slide":
        type: button
        trigger: click
        description: "SkipForward — jumps to the final slide (disabled on the last slide)."
  "Toolbar collapse toggle":
    type: toggle
    trigger: click
    description: "Top-right Maximize2/Minimize2 button that hides or shows the header toolbar for an immersive view; while collapsed an extra X (close full screen) is also offered."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
