---
path: /add-contact
id: add-contact
name: Add Contact
title: Add Contact
description: Full-page contact-adding workspace with a back-button header wrapping AddContactContent — share your personal invite QR/link, or look up a person by email to chat, add as friend, or invite them by email.
relationship:
  upstream: "/chat"
  downstream: "/chat"
cta:
  "Back":
    type: button
    trigger: click
    description: "Ghost chevron button in the header that calls router.back()."
  "Invite QR code":
    type: nav
    trigger: click
    description: "Card showing a QR code encoding your personal friend-invite link (/invite/friend/{imUid}); shows a sign-in-required placeholder when signed out."
    items:
      "Download QR code":
        type: button
        trigger: click
        description: "Downloads the invite QR as teamily-contact-qr.png; disabled when no invite link (signed out)."
  "Share your link":
    type: nav
    trigger: click
    description: "Read-only display of your personal friend-invite link."
    items:
      "Copy link":
        type: button
        trigger: click
        description: "Copies the invite link to the clipboard (toast on success/failure); disabled when no invite link."
  "Add by email":
    type: nav
    trigger: click
    description: "Email lookup form that checks whether a Teamily account exists for the entered address (debounced 500ms after typing, plus on submit)."
    items:
      "Email input":
        type: input
        trigger: input
        description: "Email field; validates format and shows an inline error for invalid addresses."
      "Search":
        type: button
        trigger: [click, input]
        description: "Submits the form to run the email lookup; shows a spinner and 'Searching' label while checking; disabled when empty or checking."
      "Open chat":
        type: button
        trigger: click
        description: "Result action shown when the found user is already a friend; opens an IM conversation with them (navigates to /chat) and closes the page."
      "Add friend":
        type: button
        trigger: click
        description: "Result action shown when the user exists but isn't yet a friend; sends a friend request by email and marks them as friend on success."
      "Invite by email":
        type: button
        trigger: click
        description: "Result action shown when no account exists for the email; sends a friend-type invitation email."
      "Yourself (disabled)":
        type: button
        trigger: click
        description: "Disabled result label shown when the looked-up email is your own account."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
