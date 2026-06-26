---
path: /download
id: download
name: Download
title: Download Teamily — Apps for iOS, Android, Mac & Windows
description: Landing-style download page rendering the marketing hero (animated demo chat preview) with platform download buttons for iOS, Android, macOS, and Windows plus a Web pill to try Teamily online.
relationship:
  upstream: "/"
  downstream: "/login"
cta:
  "Download links":
    type: nav
    trigger: click
    description: "Row of platform CTAs shown in the hero (desktop title block and mobile view); desktop entries (macOS/Windows) are hidden on phone browsers via user-agent detection."
    items:
      "Web (try online)":
        type: link
        trigger: click
        description: "Pill linking to {baseUrl}/login to use Teamily in the browser instead of installing."
      "iOS":
        type: link
        trigger: click
        description: "App Store download link; if the configured URL is missing it shows a 'Coming Soon!' alert and stays on page."
      "Android":
        type: link
        trigger: click
        description: "Google Play download link; missing URL shows a 'Coming Soon!' alert."
      "macOS":
        type: menu
        trigger: [click, hover]
        description: "macOS button revealing a dropdown with Apple Silicon and Intel build links (desktop browsers only); missing URL shows a 'Coming Soon!' alert."
        items:
          "Apple Silicon":
            type: link
            trigger: click
            description: "Downloads the Apple Silicon macOS build."
          "Intel":
            type: link
            trigger: click
            description: "Downloads the Intel macOS build."
      "Windows":
        type: link
        trigger: click
        description: "Windows download link (desktop browsers only); missing URL shows a 'Coming Soon!' alert."
  "Demo chat preview":
    type: nav
    trigger: click
    description: "Animated, non-functional hero showcase that auto-plays scripted agent conversations; interactions only drive the demo, not real chat."
    items:
      "Switch demo conversation":
        type: button
        trigger: click
        description: "Desktop or mobile chat-list items switch the previewed scenario (Personal AI, family group, work sync, analysis/finance/research/slides/webpage agents) and replay its scripted message sequence."
      "Device mode toggle":
        type: toggle
        trigger: click
        description: "Desktop-only control switching the preview between desktop and mobile renderings of the panel."
      "Play demo music":
        type: button
        trigger: click
        description: "Music-recommendation demo opens a floating vinyl record player; a close button dismisses it."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
