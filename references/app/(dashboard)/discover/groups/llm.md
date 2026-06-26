---
path: /discover/groups
id: discover-groups
name: Explore Groups
title: Explore Groups
description: A standalone full listing of 25 curated community groups in a responsive card grid, with category-pill filtering and Join cards that open each group's external teamily.ai invite link in a new tab.
relationship:
  upstream: "/discover"
  downstream: "/discover"
cta:
  "Back to Discover":
    type: link
    trigger: click
    description: "Chevron-left button in the sticky header that navigates back to /discover."
  "Category pills":
    type: select
    trigger: click
    description: "Filters the group grid by derived category: All / Daily / Share / Explore / Find / Community / Investment / Events / Other (category inferred from each group's name)."
  "Join group card":
    type: link
    trigger: click
    description: "Each group card (cover image, name, Join badge, description) is an anchor that opens the group's external https://teamily.ai/invite/group/<id> invite URL in a new tab."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
