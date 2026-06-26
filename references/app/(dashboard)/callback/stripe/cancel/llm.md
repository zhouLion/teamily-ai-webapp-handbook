---
path: /callback/stripe/cancel
id: callback-stripe-cancel
name: Stripe Cancel Callback
title: Payment Canceled
description: Stripe Checkout cancel-return handler that, on web returns, proactively expires the open Checkout Session to release the reserved deduction (then refreshes the rewards balance) and shows a canceled dialog; on desktop returns (source=desktop) it instead deep-links back to the desktop app.
relationship:
  upstream: "/pricing"
  downstream: "/"
cta:
  "Payment-canceled dialog":
    type: dialog
    trigger: click
    description: "Modal shown on web returns (not desktop deep-link) with a canceled title and a resubscribe-anytime body; closing it (OK or backdrop) refetches the subscription and redirects to /."
    items:
      "OK":
        type: button
        trigger: click
        description: "Closes the dialog, refetches subscription state, and redirects to the home page (/)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
