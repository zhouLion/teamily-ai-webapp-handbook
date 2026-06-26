---
path: /settings
id: settings
name: Settings Home
title: Settings
description: The settings hub — a usage banner at the top plus grouped, tappable rows that link out to every settings sub-page and legal/support page, ending in social links and a sign-out/sign-in row.
relationship:
  upstream: "/, /agents/config/[agentId]"
  downstream: "/profile/edit, /settings/creator-center, /settings/credits-center, /settings/affiliate, /settings/subscription, /settings/usage, /settings/language, /settings/connectors, /settings/channels, /settings/privacy, /about/help-center, /about/terms-of-service, /about/privacy-policy, /about/refund-policy, /about, /pricing, /login, /"
cta:
  "Usage banner":
    type: nav
    trigger: click
    description: "Top card showing the current plan, remaining-window percent (conic ring), and reset countdown, with a single CTA button."
    items:
      "Try Plus / Manage":
        type: button
        trigger: click
        description: "Free users go to /pricing; paid users re-check the live subscription — Stripe billing opens /settings/subscription, an inactive plan goes to /pricing, and a non-web store shows a 'managed elsewhere' toast."
  "Account profile":
    type: nav
    trigger: click
    description: "Account & Profile section."
    items:
      "Account Profile row":
        type: link
        trigger: click
        description: "Navigates to /profile/edit."
  "Creator rewards":
    type: nav
    trigger: click
    description: "Creator & Rewards section, each row showing an earned/balance amount on the right."
    items:
      "Creator Center row":
        type: link
        trigger: click
        description: "Navigates to /settings/creator-center; right text shows $CASH earned as a creator."
      "Credit Center row":
        type: link
        trigger: click
        description: "Navigates to /settings/credits-center (onboarding tab while first-week tasks remain, otherwise the My Credits tab); right text shows the $CREDIT balance."
      "Incentive Program row":
        type: link
        trigger: click
        description: "Navigates to /settings/affiliate; right text shows $CASH earned in commissions."
  "Plan, billing & usage":
    type: nav
    trigger: click
    description: "Plan, Billing & Usage section."
    items:
      "Plan & Billing row":
        type: link
        trigger: click
        description: "Navigates to /settings/subscription; right text shows the current plan name."
      "Usage row":
        type: link
        trigger: click
        description: "Navigates to /settings/usage; right text shows the remaining-window percent."
  "AI agent":
    type: nav
    trigger: click
    description: "AI Agent section."
    items:
      "Language row":
        type: link
        trigger: click
        description: "Navigates to /settings/language; right text shows the agent's reply-language label."
      "App Connectors row":
        type: link
        trigger: click
        description: "Navigates to /settings/connectors."
      "OpenClaw Management row":
        type: link
        trigger: click
        description: "Navigates to /settings/channels."
  "Preferences & security":
    type: nav
    trigger: click
    description: "Preferences & Security section."
    items:
      "Privacy Settings row":
        type: link
        trigger: click
        description: "Navigates to /settings/privacy."
  "Support & legal":
    type: nav
    trigger: click
    description: "Support & Legal section."
    items:
      "Help Center row":
        type: link
        trigger: click
        description: "Navigates to /about/help-center."
      "Terms of Service row":
        type: link
        trigger: click
        description: "Navigates to /about/terms-of-service."
      "Privacy Policy row":
        type: link
        trigger: click
        description: "Navigates to /about/privacy-policy."
      "Refund Policy row":
        type: link
        trigger: click
        description: "Navigates to /about/refund-policy."
      "About row":
        type: link
        trigger: click
        description: "Navigates to /about."
  "Session":
    type: nav
    trigger: click
    description: "Session section with the sign-out/sign-in control."
    items:
      "Sign Out / Sign In row":
        type: button
        trigger: click
        description: "When signed in, logs out and returns to /; when signed out, shows 'Sign In' and routes to /login (destructive styling)."
  "Social links":
    type: link
    trigger: click
    description: "X, LinkedIn, and Discord icons opening the product's social pages in a new tab."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
