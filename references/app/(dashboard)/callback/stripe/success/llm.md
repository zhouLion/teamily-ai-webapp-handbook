---
path: /callback/stripe/success
id: callback-stripe-success
name: Stripe Success Callback
title: Payment Succeeded
description: Stripe Checkout success-return handler that fires the Google Ads payment conversion and a PURCHASE growth event (once), then either deep-links back to the desktop app (source=desktop) or shows a confetti-backed success dialog before refreshing the subscription and routing home.
relationship:
  upstream: "/pricing"
  downstream: "/"
cta:
  "Payment-succeeded dialog":
    type: dialog
    trigger: click
    description: "Modal shown on web returns (not desktop deep-link) with a success title and body; closing it (OK or backdrop) refetches the subscription and redirects to /."
    items:
      "OK":
        type: button
        trigger: click
        description: "Closes the dialog, refetches subscription state, and redirects to the home page (/)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
