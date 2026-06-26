---
path: /region-restricted
id: region-restricted
name: Region Restricted
title: Region Restricted - Teamily AI
description: Blocking notice (noindex) shown when the service is unavailable in the user's region due to regulatory requirements; displays the Teamily logo, a shield-alert message, and legal links, with a mobile pull-to-refresh that re-checks the 'is-restricted' status.
relationship:
  upstream: ""
  downstream: "/about/terms-of-service, /about/privacy-policy"
cta:
  "Pull to refresh":
    type: button
    trigger: drag
    description: "Mobile-only pull-down gesture; releasing past the threshold invalidates the 'is-restricted' query to re-check region access (spinner indicator while refreshing)."
  "Terms of Service link":
    type: link
    trigger: click
    description: "Opens /about/terms-of-service."
  "Privacy Policy link":
    type: link
    trigger: click
    description: "Opens /about/privacy-policy."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
