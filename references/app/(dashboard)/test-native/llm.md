---
path: /test-native
id: test-native
name: Native WebView Test
title: Native WebView Test
description: Developer test harness that embeds the /native-webview page in a sandboxed iframe, auto-posts a greeting to it on mount, and lets you postMessage arbitrary text into it for native-bridge debugging.
relationship:
  upstream: ""
  downstream: ""
cta:
  "Native-webview iframe":
    type: nav
    trigger: click
    description: "Sandboxed iframe (allow-scripts/same-origin/popups/forms) loading /native-webview; on mount the parent posts 'Hello from parent' to its contentWindow via postMessage."
  "Send Message":
    type: button
    trigger: click
    description: "Opens a browser prompt for text and postMessage()s the entered value to the embedded /native-webview iframe (no-op if the prompt is left empty)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
