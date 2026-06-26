---
path: /contact
id: contact-layout
name: Contact Layout
title: Contact Layout
description: Two-pane chrome for the Contacts area — a resizable left sidebar with the Contacts title, an add-contact button, and the contact nav (My Agents / My Friends / Phone Contacts) beside the routed contact content. On mobile the /contact root renders a header (title + add-contact) over the nav and contact list in one scroll area, while sub-pages render full-screen.
relationship:
  upstream: ""
  downstream: "/contact/my-agents, /contact/my-friends, /contact/phone-contacts, /add-contact"
cta:
  "Add contact button":
    type: button
    trigger: click
    description: "Plus icon in the sidebar (desktop) / root header (mobile); opens the Add Contact modal on desktop, or navigates to /add-contact on mobile."
  "Contact nav":
    type: nav
    trigger: click
    description: "Sidebar (desktop) / root list (mobile) navigation between the three contact sub-views; the active tab is highlighted."
    items:
      "My Agents tab":
        type: button
        trigger: click
        description: "Navigates to /contact/my-agents (also highlighted as active for the /contact root on desktop)."
      "My Friends tab":
        type: button
        trigger: click
        description: "Navigates to /contact/my-friends."
      "Phone Contacts tab":
        type: button
        trigger: click
        description: "Navigates to /contact/phone-contacts."
  "Sidebar resize handle":
    type: button
    trigger: [hover, drag]
    description: "Drag handle on the resizable sidebar edge; persists the chosen width under the contact-sidebar-width key. (Desktop only.)"
---

<!-- 正文待补充:后续人工补充该布局的详细介绍 -->
