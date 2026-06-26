---
path: /i/[invite_code]
id: i-invite_code
name: Invite Landing
title: Invite Landing - Teamily AI
description: An invite/referral landing page that validates the URL invite code and renders a hero plus an inviter profile card (avatar, stats, top post, reward banner) with a single Connect/Claim-Welcome CTA; logged-out visitors are routed to /login, otherwise the code is verified, the inviter added as an IM friend, and the user sent into /chat. Invalid or expired codes show a fallback state.
relationship:
  upstream: ""
  downstream: "/login, /chat, /about/terms-of-service, /about/privacy-policy, /"
cta:
  "Connect / Claim welcome CTA":
    type: button
    trigger: click
    description: "Primary card button — label is 'Claim welcome' for CHANNEL codes or 'Connect with <name>' for personal invites; routes signed-out users to /login?from=/i/<code>, otherwise verifies the code, adds the inviter as an IM friend, and pushes to /chat?imUid=<inviterId> (or /chat). Disabled and shows 'Connecting…' while pending; recovers to /chat when the code was already used."
  "Terms & privacy (card)":
    type: link
    trigger: click
    description: "Inline links under the CTA pointing to /about/terms-of-service and /about/privacy-policy."
  "Footer Terms / Privacy":
    type: link
    trigger: click
    description: "Footer links to /about/terms-of-service and /about/privacy-policy (alongside a copyright label)."
  "Go home (invalid state)":
    type: link
    trigger: click
    description: "Shown only on the invalid/expired-invite fallback screen; links back to /."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
