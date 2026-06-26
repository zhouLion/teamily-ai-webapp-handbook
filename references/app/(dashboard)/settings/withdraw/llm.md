---
path: /settings/withdraw
id: settings-withdraw
name: Withdraw
title: Withdraw
description: Unified cash-out page — total withdrawable balance (creator + affiliate) with a Withdraw All action, source rows linking to the creator and affiliate pages, and a withdrawal-history list; whole page is gated and redirects home via a 'coming soon' dialog when the withdraw-entry flag is off.
relationship:
  upstream: "/settings/affiliate, /settings/creator-center"
  downstream: "/settings/creator-center, /settings/affiliate, /"
cta:
  "Withdraw All":
    type: button
    trigger: click
    description: "Opens the withdraw dialog; disabled when nothing is withdrawable, and labeled 'Link Card and Withdraw' when no Stripe payout account is connected."
  "Withdraw dialog":
    type: dialog
    trigger: click
    description: "3-step modal (Connect Stripe → Amount → Done). Connect starts Stripe Connect onboarding in a popup; Amount confirms the full withdrawable amount; Done shows a confetti success that auto-closes after 3s."
    items:
      "Connect Stripe":
        type: button
        trigger: click
        description: "Step 1 — starts (or updates) the Stripe Connect payout-account onboarding; safe to re-run for already-linked users."
      "Withdraw all (amount step)":
        type: button
        trigger: click
        description: "Step 2 — submits a withdrawal for the full withdrawable balance to the linked payout card."
      "Back to connect":
        type: button
        trigger: click
        description: "Step 2 — returns to the Connect step to re-link or update the payout account."
      "Close dialog":
        type: button
        trigger: click
        description: "X button closing the dialog; blocked while a withdrawal is submitting."
  "Earnings source rows":
    type: link
    trigger: click
    description: "Two rows — Creator (→ /settings/creator-center) and Affiliate (→ /settings/affiliate) — each showing its withdrawable amount and summary."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
