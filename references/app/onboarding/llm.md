---
path: /onboarding
id: onboarding
name: Onboarding
title: Onboarding
description: Post-signup first-run wizard that floats as a modal (desktop) or full screen (mobile); collects identity/interests/usage answers, provisions starter agents, teams, content, and a knowledge base, then prompts new users for an invite code before handing off to /chat.
relationship:
  upstream: "/login, /signup, /callback/chat, /i/[invite_code]"
  downstream: "/chat, /login"
cta:
  "Welcome step":
    type: nav
    trigger: click
    description: "Opening slide with a typewriter title, brand badge, time-estimate hint, and confetti on mount."
    items:
      "Get started":
        type: button
        trigger: click
        description: "Advances to the first question (identity)."
      "Skip":
        type: button
        trigger: click
        description: "Skips the whole wizard; new users (isFirst) then see the invite prompt, others go straight to /chat."
  "Identity question":
    type: nav
    trigger: click
    description: "Question 1 of the wizard — multi-select chips for 'who you are' (capped at MAX_IDENTITY_SELECTIONS)."
    items:
      "Identity option chip":
        type: toggle
        trigger: click
        description: "Toggles an identity option; disabled once the selection cap is reached (unless already selected)."
      "Other (identity)":
        type: input
        trigger: [click, input]
        description: "Free-text 'Other' chip; selecting it reveals an input to type a custom identity."
      "Back":
        type: button
        trigger: click
        description: "Returns to the previous step."
      "Continue":
        type: button
        trigger: click
        description: "Advances to the interests question; disabled until at least one selection is made."
      "Skip":
        type: button
        trigger: click
        description: "Skips the wizard (same exit flow as the welcome Skip)."
  "Interests question":
    type: nav
    trigger: click
    description: "Question 2 — multi-select interest chips (capped at MAX_INTEREST_SELECTIONS) plus an Other free-text chip."
    items:
      "Interest option chip":
        type: toggle
        trigger: click
        description: "Toggles an interest; disabled once the selection cap is reached (unless already selected)."
      "Other (interests)":
        type: input
        trigger: [click, input]
        description: "Free-text 'Other' chip with an input for a custom interest."
      "Back":
        type: button
        trigger: click
        description: "Returns to the identity question."
      "Continue":
        type: button
        trigger: click
        description: "Advances to the usage question; disabled until a selection is made."
      "Skip":
        type: button
        trigger: click
        description: "Skips the wizard."
  "Usage question":
    type: nav
    trigger: click
    description: "Question 3 — multi-select chips for how you'll use the product, plus an Other free-text chip; the final question before provisioning."
    items:
      "Usage option chip":
        type: toggle
        trigger: click
        description: "Toggles a usage option."
      "Other (usage)":
        type: input
        trigger: [click, input]
        description: "Free-text 'Other' chip with an input for a custom usage."
      "Back":
        type: button
        trigger: click
        description: "Returns to the interests question."
      "Start building":
        type: button
        trigger: click
        description: "Submits all answers, kicks off provisioning (agents, team, content, knowledge base), and advances to the settlement step; shows a spinner while submitting."
      "Skip":
        type: button
        trigger: click
        description: "Skips the wizard."
  "Settlement step":
    type: nav
    trigger: click
    description: "Provisioning summary showing four result rows (agents created, team created, content loaded, knowledge base initialized), each with a live count-up badge and spinner until it resolves; fires confetti when all rows are ready."
    items:
      "Done / Preparing":
        type: button
        trigger: click
        description: "Disabled and labeled 'Preparing' (cursor-wait) until every slot resolves; then becomes 'Done' — new users (isFirst) see the invite prompt next, others go to /chat."
  "Post-onboarding invite prompt":
    type: dialog
    trigger: click
    description: "Shown to new users after finishing/skipping the wizard, before entering the product; replaces the wizard rather than layering over it. Either confirms a known inviter's credit or asks for a code."
    items:
      "Invited-by confirm (invite-link arrivals)":
        type: dialog
        trigger: click
        description: "Shown when a pending invite code exists (user arrived via /i/{code}); displays the inviter and the welcome credit."
        items:
          "Apply":
            type: button
            trigger: click
            description: "Verifies the code (establishes the friend relationship and applies the credit), then proceeds to /chat; idempotent on the backend."
          "Skip":
            type: button
            trigger: click
            description: "Clears the pending code and proceeds to /chat."
      "Invite-code entry (natural sign-up)":
        type: dialog
        trigger: click
        description: "Shown when no inviter context exists; prompts for an invite/promo code with a no-code reward hint."
        items:
          "Invite code field":
            type: input
            trigger: [input, paste]
            description: "Uppercase mono code input; normalizes input and shows inline validation errors; Enter submits when non-empty."
          "Apply":
            type: button
            trigger: click
            description: "Verifies the entered code; on success applies the credit and proceeds to /chat, otherwise shows an error; disabled while empty or pending."
          "Skip":
            type: button
            trigger: click
            description: "Clears any pending code and proceeds to /chat without applying a code."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
