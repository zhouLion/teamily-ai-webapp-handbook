---
path: /pricing
id: pricing
name: Pricing
title: Pricing - Teamily AI
description: ISR-rendered plans-and-pricing page — a billing-cycle-toggled 5-tier plan table (Free / Go / Plus / Premium / Pro) with state-aware per-plan CTAs that start a Stripe Checkout session or open the customer portal, an optional reward-credits / Creator-90%-off discount layer, a manage-subscription entry, a tabbed Help Center FAQ, and the shared Teamily footer.
relationship:
  upstream: "/, /chat, /checkout, /checkout/success, /settings, /settings/credits-center, /settings/subscription"
  downstream: "/login, /settings/credits-center, /about, /about/terms-of-service, /about/privacy-policy, /about/refund-policy"
cta:
  "Billing cycle controls":
    type: nav
    trigger: click
    description: "Row above the plan cards: the billing-cycle tabs and (when the user has reward credits and no active paid plan) the global credits toggle."
    items:
      "Billing cycle tabs":
        type: tabs
        trigger: click
        description: "Monthly / Annual toggle synced to the ?billingCycle query param; Annual shows a 'save 20%' note. Auto-set to Annual when the current plan is an annual plan."
      "Global credits toggle":
        type: toggle
        trigger: click
        description: "Shown when reward-credit balance > 0 and no active paid subscription; applies the credit balance to all eligible direct-checkout plans (off by default when ?apply=none)."
  "Plan table":
    type: nav
    trigger: click
    description: "Grid of plan cards (Free / Go / Plus / Premium / Pro); each shows price, features, an optional discount option, and a state-aware action button. A plan_code x billing_cycle view event fires on scroll-into-view."
    items:
      "Choose Plan button":
        type: button
        trigger: click
        description: "Per-plan CTA whose label varies by state — Your Current Plan / Included in Your Plan (disabled), Start 7-day Free Trial (new user → monthly Plus), Currently on Trial, or Upgrade; signed-out clicks go to /login?from=/pricing, eligible upgrades open a Stripe Checkout session, current-plan clicks open the Stripe customer portal, and downgrades show a toast and are blocked."
      "Creator perk checkbox":
        type: toggle
        trigger: click
        description: "Per-card option on perk-eligible plans (Plus/Pro, monthly, direct-checkout only) applying the Creator 90%-off first-charge coupon; mutually exclusive with credits."
      "View credits link":
        type: link
        trigger: click
        description: "Shown when credits are applied to a card; links to /settings/credits-center."
  "Manage subscription":
    type: button
    trigger: click
    description: "Below the table for signed-in paid subscribers (hidden for free plans and store-managed subscriptions); opens the Stripe customer portal to manage, invoice, or cancel. On the Paddle provider this is a link to the Paddle portal; with no payment provider it is replaced by an auto-renewal notice banner."
  "Help Center":
    type: nav
    trigger: click
    description: "FAQ section with category tabs and per-category accordions; expanding a question fires a one-time analytics event."
    items:
      "FAQ category tabs":
        type: tabs
        trigger: click
        description: "Billing / Usage / Support tabs, each switching to that category's FAQ accordion."
      "FAQ accordion item":
        type: toggle
        trigger: click
        description: "Expands/collapses a question to reveal its answer (first item open by default)."
      "Policy links":
        type: link
        trigger: click
        description: "Inside the Support tab's legal accordion: Terms of Service (/about/terms-of-service), Privacy Policy (/about/privacy-policy), Refund Policy (/about/refund-policy)."
  "Teamily footer":
    type: nav
    trigger: click
    description: "Shared site footer (hidden on embedded views); product/company/legal link columns to /, /pricing, /about, the help center, /about/privacy-policy, and /about/terms-of-service."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
