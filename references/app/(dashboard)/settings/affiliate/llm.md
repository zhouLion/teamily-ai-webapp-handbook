---
path: /settings/affiliate
id: settings-affiliate
name: Affiliate Program
title: Affiliate
description: Affiliate program hub — an earnings hero with commission balance plus withdraw entry and withdrawable/pending and invitees/spend chips, a 25% commission explainer with per-user cap, a per-invitee earnings breakdown list, and an invite-sharing toolbar (copy link, QR, email, social).
relationship:
  upstream: "/, /settings, /settings/withdraw"
  downstream: "/settings/withdraw"
cta:
  "Earnings hero":
    type: nav
    trigger: click
    description: "Green card showing the affiliate commission balance with withdrawable/pending and invitees/lifetime-spend status chips."
    items:
      "Withdraw":
        type: button
        trigger: click
        description: "Routes to /settings/withdraw when the withdraw-entry flag is on; otherwise opens the 'coming soon' dialog (fires a withdraw-blocked event)."
  "Send an invite":
    type: nav
    trigger: click
    description: "Invite-sharing toolbar showing the personal invite link plus copy and share controls."
    items:
      "Copy link":
        type: button
        trigger: click
        description: "Copies the invite link to the clipboard (button shows a check on success) and fires an invite-link-copied event."
      "QR code":
        type: dialog
        trigger: click
        description: "Opens the QR dialog rendering a scannable QR for the invite link, with a Download QR button."
      "Email invite":
        type: dialog
        trigger: click
        description: "Opens the email-invite dialog to enter a recipient address and send the invite by email."
      "Share on X / Facebook / LinkedIn / SMS":
        type: link
        trigger: click
        description: "Opens the respective share intent (X, Facebook, LinkedIn in a new tab; SMS via sms: link), each firing an invite-share-clicked event."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
