---
path: /settings/credits-center
id: settings-credits-center
name: Credits Center
title: Credits Center
description: Tabbed credits/rewards hub synced to the ?tab= query param (onboarding, invite, leaderboard, credits) — first-week onboarding tasks and login-streak rewards, an invite-friends panel (referral rewards, share link, code redemption, invite history, FAQ), a personal token-usage leaderboard, and a credit balance with activity history. All tabs route the Apply Credits / Buy Plus CTAs to /pricing.
relationship:
  upstream: "/, /apply/invite-code, /credits, /discover, /get-started, /pricing, /settings, /settings/invite-history"
  downstream: "/pricing, /discover, /chat, /profile/edit"
cta:
  "Tab nav":
    type: tabs
    trigger: click
    description: "Horizontally scrollable row of tab pills synced to ?tab=; the Leaderboard tab is hidden when the leaderboard feature gate is off, and the streak-dependent tab order varies by whether the login-streak feature is visible."
    items:
      "Onboarding Tasks tab":
        type: button
        trigger: click
        description: "?tab=onboarding — first-week bonus card, login-streak rewards, and the task list."
      "Invite Friends tab":
        type: button
        trigger: click
        description: "?tab=invite — referral rewards, share/redeem invite codes, invite history, and FAQ."
      "Leaderboard tab":
        type: button
        trigger: click
        description: "?tab=leaderboard — personal token-usage league (hidden when the feature gate is off)."
      "My Credits tab":
        type: button
        trigger: click
        description: "?tab=credits — credit balance hero and activity history."
  "Onboarding tab":
    type: nav
    trigger: click
    description: "First-week rewards view shown on ?tab=onboarding."
    items:
      "First-7-days info popover":
        type: menu
        trigger: click
        description: "Info icon in the first-7-days / login-streak section labels opening an explanatory popover."
      "Buy Plus":
        type: button
        trigger: click
        description: "In the first-7-days progress card — routes to /pricing to buy Plus with earned credits."
      "Task card":
        type: button
        trigger: click
        description: "A first-week task row; tapping an incomplete task dispatches its action (e.g. open chat, create agent, publish post, set up profile); completed tasks are disabled and show a check."
      "Apply Credits":
        type: button
        trigger: click
        description: "Footer CTA routing to /pricing to apply earned credits at checkout."
  "Invite tab":
    type: nav
    trigger: click
    description: "Referral panel shown on ?tab=invite."
    items:
      "Apply Credits (referral)":
        type: button
        trigger: click
        description: "On the referral-rewards card — routes to /pricing to spend earned referral credits."
      "Copy invite link":
        type: button
        trigger: click
        description: "Copies the personal invite link to the clipboard (button shows a check when copied)."
      "Show QR code":
        type: button
        trigger: click
        description: "Opens the invite QR-code dialog."
      "Share via email":
        type: button
        trigger: click
        description: "Opens the invite email dialog."
      "Social share links":
        type: link
        trigger: click
        description: "X, Facebook, LinkedIn, and SMS share links opening prefilled share intents in a new tab."
      "Apply invite code":
        type: input
        trigger: [input, click]
        description: "Text field plus Apply button to redeem a friend's invite code (min 3 chars); verifies via API and shows success/error toasts, then hides the section once applied."
      "Invite history":
        type: nav
        trigger: click
        description: "Sent/accepted/pending summary rows over a paginated list of invitees."
        items:
          "History pagination":
            type: button
            trigger: click
            description: "Page controls for the invite history list (10 per page)."
      "Invite FAQ":
        type: button
        trigger: click
        description: "Single-open accordion of six referral FAQ entries."
  "Leaderboard tab":
    type: nav
    trigger: click
    description: "Personal token-usage league shown on ?tab=leaderboard."
    items:
      "Period toggle":
        type: toggle
        trigger: click
        description: "Today / This Week toggle switching the leaderboard period."
  "My Credits tab":
    type: nav
    trigger: click
    description: "Credit balance and activity view shown on ?tab=credits."
    items:
      "Apply Credits (balance)":
        type: button
        trigger: click
        description: "On the green balance hero — routes to /pricing to apply the credit balance at checkout."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
