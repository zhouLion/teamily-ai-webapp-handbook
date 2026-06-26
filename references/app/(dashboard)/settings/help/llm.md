---
path: /settings/help
id: settings-help
name: Help
title: Help
description: Help settings page listing a Help Center link and a Contact Us entry that opens a dialog with the support email; on mobile it shows a sticky header with a back button.
relationship:
  upstream: "/settings"
  downstream: "/about/help-center"
cta:
  "Mobile back button":
    type: button
    trigger: click
    description: "Mobile-only sticky-header arrow that navigates back to the previous page."
  "Help Center":
    type: link
    trigger: click
    description: "Settings row linking to /about/help-center."
  "Contact Us":
    type: button
    trigger: click
    description: "Settings row that opens the contact dialog."
    items:
      "Contact dialog":
        type: dialog
        trigger: click
        description: "Shows the direct support email as a mailto link (contact@teamily.ai)."
        items:
          "Email link":
            type: link
            trigger: click
            description: "mailto:contact@teamily.ai — opens the OS mail composer."
          "Close":
            type: button
            trigger: click
            description: "Closes the contact dialog."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
