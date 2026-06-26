---
path: /post/[showcaseId]
id: post-showcaseId
name: Showcase Post
title: Showcase · Teamily
description: Full-page detail view of one AI-generated showcase post — renders the deliverable artifact preview alongside title, author, prompt, and a comment thread, with remix, share, like, save, follow, and report actions; emits Article JSON-LD and SEO metadata.
relationship:
  upstream: "/discover, /discover-legacy, /discover-legacy/[id], /explore, /explore/[postId], /profile/[uid], /chat, /search"
  downstream: "/profile/[uid], /me, /agent/[agent_name], /chat, /discover, /login"
cta:
  "Back":
    type: button
    trigger: click
    description: "Header chevron that goes to the previous page if there is history, otherwise replaces to /discover; also the Back button on the post-unavailable (404) state."
  "Artifact preview":
    type: button
    trigger: click
    description: "Deliverable file/media preview at the top (mobile) or left pane (desktop); tapping opens the full file viewer in post_detail context."
  "Author":
    type: nav
    trigger: click
    description: "Avatar, display name, and @handle in the header; tapping any opens the author's profile (/me when it's the current user, else /profile/[uid])."
    items:
      "Follow author":
        type: toggle
        trigger: click
        description: "Follow/unfollow button next to the name (hidden when the post is your own); requires login."
  "Created by agent":
    type: button
    trigger: click
    description: "\"Created by <owner>'s <agent>\" link under the title; opens the source agent (custom-agent page /agent/[agent_name] or its chat); disabled while resolving or when no agent is attached."
  "Remix (Create my own)":
    type: dialog
    trigger: click
    description: "Sparkles button that opens the remix dialog (also auto-opened by a pending remix intent); requires login."
    items:
      "Prompt editor":
        type: input
        trigger: [input, paste]
        description: "Textarea prefilled with the post's prompt (empty when building on the deliverable); auto-focused on open."
      "Copy prompt":
        type: button
        trigger: click
        description: "Copies the current prompt text to the clipboard (toggles to a check on success)."
      "Build on this deliverable":
        type: toggle
        trigger: click
        description: "Checkbox (shown when the post has attachments) to attach the deliverable to the remix; toggling clears or restores the prompt; an X on the attachment chip removes it."
      "Send prompt":
        type: button
        trigger: click
        description: "Arrow-up button (disabled until non-empty) that sends the prompt to the post's agent or Personal AI, optionally with the deliverable card, then opens that conversation (→ /chat)."
      "Close dialog":
        type: button
        trigger: click
        description: "X button that closes the remix dialog."
  "Share":
    type: dialog
    trigger: click
    description: "Share button (icon for others' posts, in the action row) that opens the share sheet seeded with the post snapshot and its public /post URL; requires login."
  "Post options menu":
    type: menu
    trigger: click
    description: "Kebab (⋯) menu in the header; contents depend on ownership."
    items:
      "Edit post":
        type: dialog
        trigger: click
        description: "Owner only — opens the post use-case modal to edit title, description, prompt, and preview."
      "Delete post":
        type: dialog
        trigger: click
        description: "Owner only — opens a confirmation; on confirm deletes the post and redirects to the author's profile (/me → /discover)."
      "Report post":
        type: dialog
        trigger: click
        description: "Non-owner — opens a report dialog with a radio list of reasons; Submit reports the post (requires login)."
  "Comment thread":
    type: nav
    trigger: click
    description: "Comment list (right pane on desktop, below the body on mobile) with root comments and nested replies."
    items:
      "Like comment":
        type: toggle
        trigger: click
        description: "Heart on each comment/reply that likes or unlikes it (optimistic); requires login."
      "Reply to comment":
        type: button
        trigger: click
        description: "Reply link that sets the comment as the composer's reply target and focuses the input; requires login."
      "Expand / collapse replies":
        type: toggle
        trigger: click
        description: "\"View/Hide N replies\" toggle on root comments with replies."
      "Load more comments":
        type: button
        trigger: click
        description: "Bottom button that fetches the next page of comments when a cursor exists."
      "Retry loading":
        type: button
        trigger: click
        description: "Shown on comment load error to refetch the thread."
  "Engagement footer":
    type: nav
    trigger: click
    description: "Sticky bottom bar with the comment composer plus like/save shortcuts."
    items:
      "Comment composer":
        type: input
        trigger: [input, paste]
        description: "Rounded input to write a comment or reply; focusing requires login and expands the Send/Cancel row; submitting posts the comment and clears any reply target."
      "Emoji picker":
        type: menu
        trigger: click
        description: "Emoji button (stickers disabled) that appends the chosen emoji to the comment draft."
      "Send comment":
        type: button
        trigger: click
        description: "Posts the composed comment/reply (disabled when the draft is empty)."
      "Cancel comment":
        type: button
        trigger: click
        description: "Clears the draft and reply target and collapses the composer."
      "Like post":
        type: toggle
        trigger: click
        description: "Heart shortcut (shown when the composer is collapsed) that likes/unlikes the post with synced counts; requires login."
      "Save post":
        type: toggle
        trigger: click
        description: "Bookmark shortcut (shown when the composer is collapsed) that bookmarks/unbookmarks the post; requires login."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
