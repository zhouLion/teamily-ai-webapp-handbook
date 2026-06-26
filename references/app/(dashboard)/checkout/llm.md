---
path: /checkout
id: checkout
name: Checkout
title: Checkout
description: Paddle-powered checkout that reads a priceId from the URL, shows a live order summary (per-item price, billing cycle, subtotal/tax/total) beside an embedded Paddle payment form; on completion fires confetti and redirects to /checkout/success, and redirects signed-out users to /login.
relationship:
  upstream: "/pricing"
  downstream: "/pricing, /checkout/success, /login"
cta:
  "Back to pricing":
    type: link
    trigger: click
    description: "Ghost button with a back arrow returning to /pricing."
  "Paddle payment form":
    type: nav
    trigger: input
    description: "Embedded Paddle checkout container (card/payment fields) that mounts for the URL priceId once Paddle is ready and the user is signed in; completing payment shows a processing spinner, fires confetti, toasts success, then redirects to /checkout/success, while a payment error toasts a retry message."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
