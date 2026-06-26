---
path: /login
id: login
name: Login
title: Login - Teamily AI
description: The authentication page where users sign in or create a Teamily AI account via Google, email (password / one-time code), or phone SMS code through a multi-step panel flow; a legacy username/password web2 variant is shown only on chat-test/localhost with ?v=0.
relationship:
  upstream: "/, /agent/[agent_name], /auth/github, /callback/auto-login, /checkout, /discover, /discover-legacy, /discover-legacy/[id], /download, /explore, /explore/[postId], /i/[invite_code], /invite/[imUid], /invite/friend/[imUid], /invite/group/[groupId], /playbook, /post/[showcaseId], /pricing, /settings"
  downstream: "/about/terms-of-service, /about/privacy-policy, /onboarding, /chat"
cta:
  "Continue with Google":
    type: button
    trigger: click
    description: "Google Identity Services button (continue_with, popup mode); on success the credential is exchanged for a session, then redirects to /onboarding (new users), the sanitized from-param, or /."
  "Auth method tabs":
    type: tabs
    trigger: click
    description: "Email / Phone segmented control above the form on the initial login panel; defaults to Phone."
    items:
      "Email tab":
        type: button
        trigger: click
        description: "Selects the email sign-in form (email input + Continue)."
      "Phone tab":
        type: button
        trigger: click
        description: "Selects the phone sign-in form (country picker + number + Continue)."
  "Email input":
    type: input
    trigger: input
    description: "Email address field on the login panel's email tab (autofocus, required)."
  "Continue with Email":
    type: button
    trigger: click
    description: "Submits the email; validates format then checks if the account exists — existing users advance to the password panel, new users to the create-password (register) panel."
  "Phone input row":
    type: nav
    trigger: click
    description: "Country dial-code picker plus phone number field on the login panel's phone tab, with per-country validation."
    items:
      "Country picker":
        type: select
        trigger: click
        description: "Dial-code button opening a searchable country list — a popover on desktop, a bottom sheet on mobile; search filters by name, ISO, or dial code."
      "Phone number field":
        type: input
        trigger: input
        description: "Digits-only national phone number input; defaults country to US."
  "Continue with Phone":
    type: button
    trigger: click
    description: "Enabled once the number is complete/valid; sends an SMS verification code and advances to the phone-verify panel."
  "Password panel":
    type: nav
    trigger: click
    description: "Shown after Continue with Email for an existing account: sign in with the account password (or switch to a one-time code)."
    items:
      "Edit email":
        type: button
        trigger: click
        description: "Returns to the login panel to change the entered email."
      "Password input":
        type: input
        trigger: input
        description: "Account password field with a show/hide eye toggle (hidden when the account is one-time-code only)."
      "Continue (password login)":
        type: button
        trigger: click
        description: "Submits email + password to sign in; on success redirects to the sanitized from-param or /."
      "Sign in with one-time code":
        type: button
        trigger: click
        description: "Emails a 6-digit code and advances to the email-verify panel instead of using a password."
  "Create-password (register) panel":
    type: nav
    trigger: click
    description: "Shown after Continue with Email for a new account: set a password to create the account."
    items:
      "Edit email":
        type: button
        trigger: click
        description: "Returns to the login panel to change the entered email."
      "New password input":
        type: input
        trigger: input
        description: "Password field (min 6 chars, needs upper/lower/number) with a show/hide eye toggle and inline validation."
      "Continue (register)":
        type: button
        trigger: click
        description: "Validates the password, then emails a 6-digit verification code and advances to the email-verify panel to finish sign-up."
      "Sign up with one-time code":
        type: button
        trigger: click
        description: "Skips setting a password; emails a code and advances to the email-verify panel."
  "Email verify panel":
    type: nav
    trigger: click
    description: "Shown after requesting an email code: enter the 6-digit code sent to the address."
    items:
      "Back":
        type: button
        trigger: click
        description: "Returns to the login panel and clears the entered code."
      "OTP code input":
        type: input
        trigger: input
        description: "6-slot numeric one-time-code field."
      "Continue (verify email code)":
        type: button
        trigger: click
        description: "Submits the 6-digit code to sign in / finish sign-up; new users redirect to /onboarding, returning users to the from-param or /."
      "Resend code":
        type: button
        trigger: click
        description: "Re-sends the email code; disabled during a 60s cooldown showing the countdown."
  "Phone verify panel":
    type: nav
    trigger: click
    description: "Shown after Continue with Phone: enter the 6-digit SMS code (auto-submits when 6 digits are filled)."
    items:
      "Back":
        type: button
        trigger: click
        description: "Returns to the login panel and clears the entered phone code."
      "OTP code input":
        type: input
        trigger: input
        description: "6-slot numeric SMS-code field; auto-verifies on the 6th digit and shows wrong/locked/expired errors with remaining-attempt counts."
      "Resend code":
        type: button
        trigger: click
        description: "Re-sends the SMS code; disabled during a 60s cooldown showing the countdown."
  "Terms / Privacy links":
    type: link
    trigger: click
    description: "'By continuing' footer links opening Terms of Service (/about/terms-of-service) and Privacy Policy (/about/privacy-policy) in a new tab."
  "Legacy web2 login (?v=0)":
    type: nav
    trigger: click
    description: "Alternate form rendered only on chat-test.teamily.ai or localhost:3000 with ?v=0: Google sign-in, a username/password form, a Create An Account toggle to an inline register form, a back arrow (router.back), and terms/privacy links."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
