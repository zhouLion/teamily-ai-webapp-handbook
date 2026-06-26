---
path: /apply/invite-code
id: apply-invite-code
name: Apply Invite Code
title: Invite code
description: Standalone post-signup page to enter and verify an invite/promo code (normalized to uppercase) for a $5 welcome credit, or skip straight to onboarding; prefills from the ?code= param or a pending stored code and tracks rewards analytics events.
relationship:
  upstream: "/login, /"
  downstream: "/settings/credits-center, /"
cta:
  "Back":
    type: button
    trigger: click
    description: "Round arrow button in the header that calls router.back() to return to the previous page."
  "Invite or promo code input":
    type: input
    trigger: [input, paste]
    description: "Monospace uppercase code field, autofocused and prefilled from ?code= or the pending stored code; clears the inline error on change and submits via Apply when Enter is pressed (unless a verify is already pending)."
  "Apply":
    type: button
    trigger: click
    description: "Verifies the normalized code; on success clears the pending code, toasts the $5 welcome credit, and redirects to /settings/credits-center?tab=my-credits (logged in) or / (signed out); on failure shows an inline error. Disabled while pending or when the field is empty."
  "Skip":
    type: button
    trigger: click
    description: "Skips code entry, clears any pending code, tracks the skip event, and continues to /settings/credits-center?tab=onboarding (logged in) or / (signed out). Disabled while a verify is pending."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
