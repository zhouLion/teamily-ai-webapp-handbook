---
path: /settings/credit-usage
id: settings-credit-usage
name: Credit Usage
title: Credit Usage
description: Usage overview page rendering the shared CreditUsageSettings — read-only progress cards for the 5-hour window, weekly cap, and (Plus/Pro only) advanced-model monthly quota, an on-demand pay-as-you-go billing card (eligible Plus/Pro only) with toggle, spend/limit details and suspended/limit-reached banners, plus a token-usage summary card (lifetime/month/week/day).
relationship:
  upstream: ""
  downstream: ""
cta:
  "On-demand toggle":
    type: toggle
    trigger: click
    description: "Switch on the on-demand usage card; turning it on opens the enable confirmation dialog, turning it off disables billing immediately. Disabled when not eligible, while updating, or when payment is suspended."
  "Enable confirmation dialog":
    type: dialog
    trigger: click
    description: "Opened by turning the toggle on — Cancel or Enable; Enable activates on-demand billing with the previous monthly limit or the $100 default."
  "Monthly limit input":
    type: input
    trigger: input
    description: "Number field for the on-demand monthly spend limit (shown when active); clamped to $10–$9999, falling back to $100, and saved on blur."
  "Retry Payment":
    type: button
    trigger: click
    description: "Shown in the payment-suspended banner; retries charging the unpaid balance."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
