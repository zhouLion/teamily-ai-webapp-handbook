---
path: /ui/video-test
id: ui-video-test
name: Video Test
title: Video Load Inspector
description: Internal dev/test page with two tabs — a react-photo-view PhotoSlider video preview (normal vs. gesture-optimized autoplay) and a Native Video load inspector that plays a URL while logging video lifecycle events and probing the redirect chain (HTTP status + headers per hop) via a server action.
relationship:
  upstream: ""
  downstream: ""
cta:
  "Mode tabs":
    type: tabs
    trigger: click
    description: "Switches between the PhotoSlider preview tab and the Native Video inspector tab."
  "PhotoSlider preview":
    type: nav
    trigger: click
    description: "PhotoSlider tab controls that open the full-screen video lightbox over the preset sample videos."
    items:
      "Click to preview":
        type: button
        trigger: click
        description: "Opens the PhotoSlider lightbox in normal (non-optimized) autoplay mode."
      "Click to preview (no gesture)":
        type: button
        trigger: click
        description: "Opens the lightbox in gesture-optimized mode where only the active slide plays and others pause."
      "Lightbox slider":
        type: dialog
        trigger: [click, drag]
        description: "Looping full-screen video viewer with banner, mask-close, and pull-to-close; swiping changes the active index."
  "Native Video inspector":
    type: nav
    trigger: click
    description: "Native Video tab: a video player plus an event log, with controls to load a URL, probe its redirects, and manage the log."
    items:
      "Preset URL":
        type: button
        trigger: click
        description: "Preset 1/2/3 buttons that fill the URL textarea with a sample video URL."
      "URL textarea":
        type: input
        trigger: [input, paste]
        description: "Editable video URL; Enter loads the video into the player."
      "Load":
        type: button
        trigger: click
        description: "Sets the video src to the entered URL and triggers native browser loading (forces reload if the URL is unchanged)."
      "Probe":
        type: button
        trigger: click
        description: "Server-side fetch (probeVideoUrl action) that follows redirects and logs each hop's status, statusText, and key headers; disabled while probing."
      "Clear log":
        type: button
        trigger: click
        description: "Trash button that empties the event log."
      "Download log":
        type: button
        trigger: click
        description: "Download-icon button that exports the event log to a .txt file (disabled when empty)."
      "Video player":
        type: button
        trigger: [click, drag]
        description: "Native HTML5 video with controls; play/pause/seek emit lifecycle events into the log."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
