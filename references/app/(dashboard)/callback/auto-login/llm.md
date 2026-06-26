---
path: /callback/auto-login
id: callback-auto-login
name: Auto Login Callback
title: Auto Login
description: Passwordless-login completion handler — reads the 6-digit code from the URL, looks up the email/password stashed in cookies, calls the email-code login API, connects the IM service, then redirects to the sanitized from URL (default /); auto-redirects to / if already signed in or to /login if the code is missing.
relationship:
  upstream: "/login"
  downstream: "/, /login"
cta:
  "Verification code display":
    type: input
    trigger: click
    description: "Read-only 6-slot OTP field pre-filled with the code from the URL; slots animate to red on error or green on success. Disabled (not user-editable)."
  "Please wait":
    type: button
    trigger: click
    description: "Disabled spinner button shown during the loading state while credentials are verified and the IM service connects; no action."
  "Go to Login":
    type: button
    trigger: click
    description: "Shown only in the error state (expired session, invalid code, or login failure); navigates back to /login to sign in manually."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
