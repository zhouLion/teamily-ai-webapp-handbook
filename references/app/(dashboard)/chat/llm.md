---
path: /chat
id: chat
name: Chat
title: Chat
description: The core IM chat workspace — opens conversations from URL params and renders the active conversation (messages, composer, header, side drawers). The home of message sending plus a deep tree of feature entries, dialogs, drawers, and per-message actions.
relationship:
  upstream: "/, /callback/chat, /discover, /discover-legacy, /discover-legacy/[id], /explore, /explore/[postId], /i/[invite_code], /playbook, /post/[showcaseId], /search, /search/conversation, /settings/creator-center, /settings/credits-center, /web"
  downstream: "/profile/[uid], /agent/[agent_name], /discover, /pricing, /add-contact, /settings/connectors, /search/conversation"
cta:
  "Message composer":
    type: nav
    trigger: click
    description: "Bottom input bar for composing and sending messages; resizable on desktop via a bottom drag handle."
    items:
      "Message editor":
        type: input
        trigger: [input, paste]
        description: "Rich-text (ProseMirror) field supporting text, links, newlines, and @mentions; Enter sends, Shift+Enter inserts a newline on desktop."
      "Send message":
        type: button
        trigger: [click, input]
        description: "Sends the composed text/attachments; shown when the editor has content (Enter on desktop)."
      "@mention popup":
        type: menu
        trigger: input
        description: "Appears when typing @ in a group; pick a member to mention."
        items:
          "Mention everyone":
            type: button
            trigger: click
            description: "@everyone — mentions all group members (first item)."
          "Mention member":
            type: button
            trigger: [click, hover]
            description: "Mentions a specific member (avatar + name); arrow keys navigate the list."
      "Emoji & sticker picker":
        type: menu
        trigger: click
        description: "Smile-icon button opening the emoji/sticker picker (popover on desktop, drawer on mobile)."
        items:
          "Insert emoji":
            type: button
            trigger: click
            description: "Inserts the chosen emoji at the cursor."
          "Send sticker":
            type: button
            trigger: click
            description: "Sends the chosen sticker as a message."
      "Attach file":
        type: button
        trigger: click
        description: "Paperclip button that opens the OS file picker; selected files open the file confirm dialog before sending."
      "Media picker":
        type: menu
        trigger: click
        description: "Camera-icon dropdown for image/video uploads."
        items:
          "Upload image":
            type: button
            trigger: click
            description: "Opens the image picker; selection opens the files-preview dialog."
          "Upload video":
            type: button
            trigger: click
            description: "Opens the video picker; selection opens the video confirm dialog."
      "Voice recorder":
        type: button
        trigger: click
        description: "Mic button (shown when the editor is empty) that starts voice recording and swaps the input for recorder controls."
        items:
          "Cancel recording":
            type: button
            trigger: click
            description: "Trash icon — stops and discards the recording."
          "Pause / resume recording":
            type: toggle
            trigger: click
            description: "Pauses recording; toggles to resume."
          "Send voice":
            type: button
            trigger: click
            description: "Finalizes and sends the voice message."
      "Quote / reply preview":
        type: button
        trigger: click
        description: "Bar above the editor showing the message being replied to; an X clears the quote."
      "Attachment chips":
        type: button
        trigger: click
        description: "Draft attachment thumbnails; each has an X to remove it before sending."
      "Files preview dialog":
        type: dialog
        trigger: click
        description: "Batch preview for queued files before sending."
        items:
          "Add more files":
            type: button
            trigger: click
            description: "Plus button to append more files to the batch."
          "Select / remove file":
            type: button
            trigger: click
            description: "Tap a thumbnail to preview it; its X removes that file from the batch."
          "Send files":
            type: button
            trigger: click
            description: "Sends all files in the batch."
      "Send-media confirm dialogs":
        type: dialog
        trigger: click
        description: "Audio / video / file confirm dialogs shown before upload, each with Cancel and a Send button (with upload progress)."
  "Conversation header":
    type: nav
    trigger: click
    description: "Top bar of the open conversation: title, avatar, and the row of action entries."
    items:
      "Back to list":
        type: button
        trigger: click
        description: "Mobile-only — returns to the conversation list."
      "Conversation title / avatar":
        type: button
        trigger: click
        description: "Tapping the avatar or title opens the conversation info panel (user / agent / group info)."
      "Tasks history":
        type: button
        trigger: click
        description: "Gear icon (agents with tasks) opening the tasks/threads sheet; tapping a task opens the thread drawer."
      "Search in conversation":
        type: button
        trigger: click
        description: "Opens the in-conversation search sheet (filter by message/media/file/voice; tap a result to jump to it)."
      "More / settings (⋯)":
        type: button
        trigger: click
        description: "Kebab menu that opens the conversation info panel."
  "Conversation info panel":
    type: dialog
    trigger: click
    description: "Side sheet opened from the header (avatar / title / ⋯). Contents vary by conversation type (direct, agent, group)."
    items:
      "View full profile":
        type: link
        trigger: click
        description: "Opens the user's or agent's full profile page (non-agents → /profile, custom agents → agent page)."
      "Mute notifications":
        type: toggle
        trigger: click
        description: "Mutes/unmutes this conversation."
      "Pin to top":
        type: toggle
        trigger: click
        description: "Pins/unpins the conversation in the list."
      "Conversation translation":
        type: toggle
        trigger: click
        description: "Enables/disables automatic message translation for this conversation."
      "Create new group":
        type: button
        trigger: click
        description: "Opens the create-group modal pre-seeded with this user/agent."
      "Set remark":
        type: button
        trigger: click
        description: "Direct chats — opens a dialog to set a custom name for the contact."
      "Block / delete friend":
        type: button
        trigger: click
        description: "Direct chats — block the user, or delete the friend (opens confirmation)."
      "Clear chat history":
        type: button
        trigger: click
        description: "Deletes all messages in the conversation (opens confirmation)."
      "Agent skills":
        type: button
        trigger: click
        description: "Agent chats — expandable skills/tools list; tap a skill or Add skill to open the edit-skills dialog."
      "Agent connectors":
        type: button
        trigger: click
        description: "Agent chats — expandable connectors list with per-connector toggles and a Connect app entry (→ /settings/connectors)."
      "Group: edit name":
        type: button
        trigger: click
        description: "Group chats (owner/admin) — inline-edit the group name."
      "Group: copy / share invite":
        type: button
        trigger: click
        description: "Copy the group link, or open the share-group dialog to invite via link/email."
      "Group: add agent / friend":
        type: button
        trigger: click
        description: "Opens the invite-member dialog on the agent or human tab."
      "Group: payment mode":
        type: select
        trigger: click
        description: "Owner-only radio choice of Owner Pays / Members Pay (opens confirmation)."
      "Group: members":
        type: tabs
        trigger: click
        description: "Agent/Human member tabs; tap a member to open their info, with owner/admin actions (set admin, transfer ownership, remove) each behind a confirmation."
      "Group: leave / dismiss":
        type: button
        trigger: click
        description: "Leave the group (optionally delete the local chat) or, owner-only, dismiss the group — both with confirmation."
  "Message actions":
    type: menu
    trigger: [hover, rightclick, longpress]
    description: "Per-message action menu (hover overlay on desktop, long-press sheet on mobile)."
    items:
      "Reply":
        type: button
        trigger: click
        description: "Quotes the message into the composer."
      "Copy":
        type: button
        trigger: click
        description: "Copies message text (or image as PNG / media-text with attachments) to the clipboard."
      "Forward":
        type: button
        trigger: click
        description: "Opens the forward dialog to send the message to another conversation."
      "Translate":
        type: button
        trigger: click
        description: "Translates the message; opens a language-picker dialog to choose the target language."
      "Transcribe":
        type: button
        trigger: click
        description: "Converts a voice message to a text transcript."
      "Save as sticker":
        type: button
        trigger: click
        description: "Saves an image message to the sticker library."
      "Multi-select":
        type: button
        trigger: click
        description: "Enters multi-select mode with this message selected, revealing the bulk action bar."
      "Recall":
        type: button
        trigger: click
        description: "Revokes a sent message (own messages only)."
      "Delete":
        type: button
        trigger: click
        description: "Deletes the message (opens confirmation)."
      "Report":
        type: button
        trigger: click
        description: "Group messages — opens a report dialog with reasons: spam, violence, child abuse, pornography, copyright, illegal drugs, personal details."
      "React":
        type: menu
        trigger: click
        description: "Emoji reaction strip (👍 ❤️ 😂 😮 😢 😡 👌) to add/toggle a reaction."
  "Message reactions":
    type: button
    trigger: click
    description: "Reaction pills shown under a message; tap to open a popover of who reacted."
    items:
      "Reaction tabs":
        type: tabs
        trigger: click
        description: "All / per-emoji tabs filtering the reactor list."
      "Remove own reaction":
        type: button
        trigger: click
        description: "Removes your reaction from your entry in the list."
  "Quote jump":
    type: button
    trigger: click
    description: "Tapping a quoted-message preview scrolls to and highlights the original message."
  "Multi-select action bar":
    type: nav
    trigger: click
    description: "Bottom bar shown while messages are selected."
    items:
      "Forward step-by-step":
        type: button
        trigger: click
        description: "Forwards the selected messages one at a time."
      "Merge forward":
        type: button
        trigger: click
        description: "Forwards the selected messages as a single merged message."
      "Delete selected":
        type: button
        trigger: click
        description: "Deletes all selected messages (opens confirmation)."
      "Cancel selection":
        type: button
        trigger: click
        description: "Exits multi-select mode."
  "Media & file viewers":
    type: dialog
    trigger: click
    description: "Full-screen image/media lightbox opened by tapping an image, video, or media result."
    items:
      "Navigate media":
        type: button
        trigger: click
        description: "Previous/next controls and a thumbnail strip to move through the conversation's media."
      "Zoom / rotate":
        type: button
        trigger: [click, doubleclick, scroll]
        description: "Zoom in/out and rotate the image (double-click and scroll-wheel also zoom on desktop)."
      "Download media":
        type: button
        trigger: click
        description: "Saves the media file to the device."
      "Star / forward / reply (mobile)":
        type: button
        trigger: click
        description: "Mobile image viewer actions to favorite, forward, or reply to the image."
      "Close viewer":
        type: button
        trigger: click
        description: "Dismisses the media viewer."
      "Audio playback":
        type: button
        trigger: [click, drag]
        description: "Voice-message play/pause, seek scrubber, and volume (native audio controls)."
  "Side panels & drawers":
    type: nav
    trigger: click
    description: "Right-side drawers and overlays opened from agent/group messages and long content."
    items:
      "Thread drawer":
        type: dialog
        trigger: click
        description: "Opened by an agent task's 'View my thoughts'; shows the full thread/task with a close button (and a dev debug panel)."
      "Iframe / tool drawer":
        type: dialog
        trigger: click
        description: "Embeds an external tool / business-action page; closes via the header X (iframe is kept mounted for state)."
      "Show-more sheet":
        type: dialog
        trigger: click
        description: "Expands long markdown (fullscreen on mobile, bottom sheet/TOC on desktop) with copy and close controls."
  "Inline status banners":
    type: nav
    trigger: click
    description: "Contextual notices that appear above the message list or composer."
    items:
      "Need-upgrade banner":
        type: button
        trigger: click
        description: "Usage-limit banner with Upgrade (→ /pricing), Enable on-demand usage, Use credit, and Dismiss."
      "Subscription / token notices":
        type: button
        trigger: click
        description: "Floating notices to refresh an expiring agent token, renew/manage an expired subscription, or repair a timed-out self-hosted agent; each dismissible."
      "Group onboarding card":
        type: button
        trigger: click
        description: "Group intro card — expand for rules and tap a suggested prompt to prefill the composer; dismissible."
  "Floating jump buttons":
    type: button
    trigger: click
    description: "Circular buttons on the message list's right edge."
    items:
      "Jump to @mentions":
        type: button
        trigger: click
        description: "Scrolls to the first unread @mention; badge shows the count (when > 0)."
      "Scroll to bottom":
        type: button
        trigger: click
        description: "Scrolls to the latest message or first unread (shown when not at the bottom)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
