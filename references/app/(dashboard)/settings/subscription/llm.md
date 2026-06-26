---
path: /settings/subscription
id: settings-subscription
name: Subscription
title: Subscription
description: Subscription settings page stacking three cards — the current-plan summary (plan name, trial/canceled badge, renewal/expiry date, plan actions), a manage-billing card (Stripe customer portal or store-managed deep link, or an upgrade promo for free users), and a quick-links/resources card with social follow icons.
relationship:
  upstream: "/, /settings"
  downstream: "/pricing, /about/help-center, /about/refund-policy"
cta:
  "Current plan card":
    type: nav
    trigger: click
    description: "Top card showing the plan name with status badge (trial / canceled / via-store), the renewal or access-until date, and the contextual plan action buttons."
    items:
      "Upgrade":
        type: button
        trigger: click
        description: "Closes settings and navigates to /pricing; shown for non-Pro active plans, trialing users, and canceled non-Pro users."
      "Change Plan":
        type: button
        trigger: click
        description: "Outline button (active paid subscribers) that closes settings and navigates to /pricing to switch plans."
      "Resume Plan":
        type: button
        trigger: click
        description: "Canceled subscriptions only — opens the Stripe customer portal in a new tab to resume the subscription."
  "Manage billing card":
    type: nav
    trigger: click
    description: "Shown for paid plans; routes billing management to Stripe or the originating app store."
    items:
      "Manage Billing":
        type: button
        trigger: click
        description: "Stripe-managed plans — opens the Stripe customer portal in a new tab (payment method, invoices, cancellation); shows a loading toast and error toast on failure."
      "Manage on Device":
        type: button
        trigger: click
        description: "Store-managed plans — opens the App Store or Google Play subscription page in a new tab depending on the originating store."
  "Upgrade promo card":
    type: nav
    trigger: click
    description: "Free-plan-only card listing Plus benefits (more credits, more tasks, all agents, early access) with a single CTA."
    items:
      "View Plans":
        type: button
        trigger: click
        description: "Closes settings and navigates to /pricing."
  "Resources / quick links":
    type: nav
    trigger: click
    description: "Resource link rows plus a Follow Us social row."
    items:
      "View All Plans":
        type: link
        trigger: click
        description: "Closes settings and navigates to /pricing."
      "Help Center":
        type: link
        trigger: click
        description: "Closes settings and navigates to /about/help-center."
      "Refund Policy":
        type: link
        trigger: click
        description: "Closes settings and navigates to /about/refund-policy."
      "Social links":
        type: link
        trigger: click
        description: "X, LinkedIn, and Discord icons opening the respective social pages in a new tab."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
