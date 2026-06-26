---
path: /message-inbox
id: message-inbox
name: Message Inbox
title: Message Inbox
description: The social notifications inbox — a paginated, infinite-scroll feed of activity (follows, likes, comments, bookmarks, shared posts, leaderboard rewards, and moderation-rejected posts) that auto-marks rows read as they scroll into view and routes each row to its target.
relationship:
  upstream: "/profile/[uid], /chat"
  downstream: "/profile/[uid], /post/[showcaseId], /settings/credits-center"
cta:
  "Header bar":
    type: nav
    trigger: click
    description: "Sticky top bar with the localized Notifications title and back/refresh controls."
    items:
      "Back":
        type: button
        trigger: click
        description: "Arrow-left button that returns to the previous route (router.back) or runs the provided onBack handler."
      "Refresh":
        type: button
        trigger: click
        description: "Flushes pending read marks, refetches the notifications feed, and refreshes the unread count; icon spins and is disabled while refetching."
  "Notification row":
    type: button
    trigger: click
    description: "A feed entry that auto-marks itself read once 60% visible; click marks it read and navigates by type (post, leaderboard, moderation-rejected, or sender profile)."
    items:
      "Open sender profile":
        type: button
        trigger: click
        description: "Tapping the sender avatar opens that user's profile (/profile/[im_uid]); avatar is hidden for leaderboard and moderation-rejected rows."
      "Open target":
        type: button
        trigger: click
        description: "Tapping the row body marks it read and routes by type: post -> /post/[post_id], leaderboard -> /settings/credits-center?tab=credits, moderation-rejected -> opens the edit-post dialog, otherwise the sender profile."
  "Edit rejected post dialog":
    type: dialog
    trigger: click
    description: "PostUseCaseModal in edit mode opened from a moderation-rejected row; loads the post by id and prefills title/description/prompt/attachments plus the moderation reason for revise-and-resave or delete."
    items:
      "Save post":
        type: button
        trigger: click
        description: "Resaves the revised post and invalidates the notifications feed to refresh it."
      "Delete post":
        type: button
        trigger: click
        description: "Deletes the rejected post and invalidates the notifications feed."
  "Try again":
    type: button
    trigger: click
    description: "Shown in the error state; refetches the notifications feed after a load failure."
  "Load more sentinel":
    type: nav
    trigger: scroll
    description: "Intersection-observed footer that fetches the next page when scrolled into view; shows a spinner while loading."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
