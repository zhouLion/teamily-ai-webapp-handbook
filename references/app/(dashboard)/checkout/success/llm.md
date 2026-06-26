---
path: /checkout/success
id: checkout-success
name: Checkout Success
title: Checkout Success
description: Payment-success confirmation page that fires confetti on load, refetches the subscription after a short delay, and offers links to the dashboard or the pricing page.
relationship:
  upstream: "/checkout"
  downstream: "/, /pricing"
cta:
  "Go to dashboard":
    type: link
    trigger: click
    description: "Primary button linking to the home dashboard (/)."
  "View plans":
    type: link
    trigger: click
    description: "Outline button linking to /pricing to review subscription plans."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
