---
path: /memory
id: memory
name: Memory
title: Memory
description: The Memory (Wiki) workspace — a two-pane knowledge base with a left index (search, All/Updates/Tags filters, reserved-view entries, and a grouped page list) beside a main area that switches between the knowledge-graph Overview, an editable wiki page detail (title/summary/tags/markdown body, files, source chats, version history, conflict review, Dream re-organize), the read-only Profile and To-dos memory views, and the agent-generated Artifacts gallery; the `page` URL param selects what the main area shows.
relationship:
  upstream: ""
  downstream: "/chat"
cta:
  "Index panel":
    type: nav
    trigger: click
    description: "Fixed left sidebar (360px): search box, filter row + tag cloud, reserved-view entries, and the grouped page list."
    items:
      "Search pages":
        type: input
        trigger: input
        description: "Debounced search over page title/summary (server ILIKE); merges with any active tag filter into one /pages query. An X clears it."
      "All filter":
        type: button
        trigger: click
        description: "Shows all loaded pages (with a count badge); default filter."
      "Updates filter":
        type: button
        trigger: click
        description: "Shows recently-changed/conflict/new pages from the /updates feed (count badge); an active search overrides it back to /pages results."
      "Tags toggle":
        type: toggle
        trigger: click
        description: "Expands/collapses the tag cloud below the filter row."
      "Tag chip":
        type: toggle
        trigger: click
        description: "Toggles a tag into the tag filter; multiple tags AND into the page query."
      "+ New page":
        type: button
        trigger: click
        description: "Creates an 'Untitled page' and opens it (not in edit mode); disabled while a create is pending to avoid double-creation."
      "Reserved-view entry":
        type: button
        trigger: click
        description: "Four pinned entries (Overview, Profile, To-dos, Artifacts) that switch the main area; selecting one sets the page param to its sentinel id."
      "Page list item":
        type: button
        trigger: click
        description: "Opens that wiki page in the detail view; shows conflict/new chips, summary, updated time, and up to two tags."
      "Group header":
        type: toggle
        trigger: click
        description: "Collapses/expands a category group within the (virtualized) page list."
      "Load more":
        type: button
        trigger: click
        description: "Fetches the next page of results (shown when the list has more, not in Updates mode)."
      "Empty-state actions":
        type: button
        trigger: click
        description: "On the empty list: Write a page (→ + New), Open Personal AI (opens the Super Agent chat → /chat), or Clear tags when the empty state is caused by tag filters."
  "Overview map":
    type: nav
    trigger: [click, hover]
    description: "Default main view: a force-directed knowledge graph of pages (nodes sized by ref_count, colored by category, conflict nodes dashed) with degraded/truncated notices."
    items:
      "Graph node":
        type: button
        trigger: [click, hover, focus]
        description: "Click opens that page in the detail view; hover/focus highlights the node and its connected edges/neighbors."
      "Create first page":
        type: button
        trigger: click
        description: "Shown in the empty graph state (fewer than 2 nodes); creates and opens a new page."
  "Page detail":
    type: nav
    trigger: click
    description: "Main view for a selected wiki page: editable header, tags, optional conflict card, markdown body, files, and source chats; the whole panel is an image drop zone when editing."
    items:
      "Edit title":
        type: input
        trigger: [click, input]
        description: "Click the title to edit; debounced autosave via optimistic-lock PATCH, Enter/Escape/blur commits, empty reverts (owner/editable pages only)."
      "Edit summary":
        type: input
        trigger: input
        description: "Always-on auto-growing textarea for the one-line summary; debounced autosave, Enter or Escape blurs to commit (editable pages only)."
      "Tag editor":
        type: input
        trigger: input
        description: "Type a tag + Enter to add (whole-array replace PATCH); each existing tag chip has an X to remove it (editable pages only)."
      "Markdown body editor":
        type: input
        trigger: [input, paste, drag]
        description: "Single expandable ProseMirror/markdown editor for the whole body (`##` sections inline); debounced autosave, image drop/paste upload; read-only pages render static markdown."
      "Dream button":
        type: button
        trigger: click
        description: "Emerald Sparkles button that kicks off the background Dream re-organize for this page; locks the editor read-only while running (polling/result handled at the page level)."
      "Share page":
        type: button
        trigger: click
        description: "Packs title + summary + body into a .md and opens the chat share sheet to send it to a conversation; empty pages get a toast instead."
      "Version history":
        type: menu
        trigger: click
        description: "History popover listing revisions (lazy-loaded); selecting an older entry previews its snapshot in the main area, selecting the latest exits preview, and a per-row Restore (when allowed) restores that revision."
      "Download page":
        type: button
        trigger: click
        description: "Exports the page (authenticated blob fetch → file download); toast on failure."
      "Delete page":
        type: dialog
        trigger: click
        description: "Opens a confirm dialog; deleting soft-deletes to trash (30 days) and returns to Overview."
      "Conflict review card":
        type: nav
        trigger: click
        description: "On conflict pages: shows the agent-suggested merge with existing vs. new content side by side, plus Accept (merge) / Deny (dismiss) actions."
      "Files list":
        type: button
        trigger: click
        description: "Attachment links parsed from the body; tapping a file opens it in the in-app viewer (videos → media lightbox, others → file viewer modal)."
      "Body file link":
        type: link
        trigger: click
        description: "Inline body links that point at page files are intercepted to open the in-app viewer instead of navigating out."
      "Source chat":
        type: button
        trigger: click
        description: "Lists chats the memory was extracted from; tapping one opens that group/Personal-AI conversation (→ /chat)."
      "Preview banner":
        type: nav
        trigger: click
        description: "Shown while previewing a historical version: Exit preview, or Restore this version (when restorable)."
      "Version conflict dialog":
        type: dialog
        trigger: click
        description: "On a 409 save conflict: Overwrite (re-saves using the server's current version) or Discard (refetches the latest)."
  "Profile view":
    type: nav
    trigger: click
    description: "Read-only 'My profile' memory view: markdown body with a refresh (Dream) button and a share button; renders backend-localized placeholder when empty."
    items:
      "Refresh profile":
        type: button
        trigger: click
        description: "Dream button that bypasses cache to regenerate the profile; toasts refreshed / empty / error."
      "Share profile":
        type: button
        trigger: click
        description: "Opens the chat share sheet to send the profile markdown as a .md (hidden when empty)."
      "Retry":
        type: button
        trigger: click
        description: "Shown on non-503 errors; reruns the query."
  "To-dos view":
    type: nav
    trigger: click
    description: "Read-only To-dos memory view (same shell as Profile, with a freshness/updated-at label): markdown body plus refresh and share."
    items:
      "Refresh to-dos":
        type: button
        trigger: click
        description: "Dream button that bypasses cache to regenerate the to-dos; toasts refreshed / empty / error."
      "Share to-dos":
        type: button
        trigger: click
        description: "Opens the chat share sheet to send the to-dos markdown as a .md (hidden when empty)."
      "Retry":
        type: button
        trigger: click
        description: "Shown on non-503 errors; reruns the query."
  "Artifacts gallery":
    type: nav
    trigger: click
    description: "Agent-generated artifacts (lazy-loaded): search, scope segmented control, group picker, type filters, and an infinite grid of artifact cards."
    items:
      "Search artifacts":
        type: input
        trigger: input
        description: "Debounced (1s) search over artifacts; resets to a clean query."
      "Scope segments":
        type: tabs
        trigger: click
        description: "All / Private / Group segmented control; switching scope clears any selected group and type narrowing."
      "Group picker":
        type: menu
        trigger: click
        description: "Group-scope dropdown to pick a specific group (entering Group scope); a context chip with X returns to all groups."
      "Type filters":
        type: button
        trigger: click
        description: "Type chips (All + each artifact type) that toggle the type filter."
      "Artifact card":
        type: button
        trigger: click
        description: "Opens the artifact: code → new tab, docx → Office viewer, presentation → slides viewer, others → in-app file viewer."
      "Clear filters / search / view all":
        type: button
        trigger: click
        description: "Empty-state actions to clear active filters, clear the search, or reset everything (view all)."
  "Maintenance banner":
    type: nav
    trigger: click
    description: "Full-view fallback shown when a wiki/memory request returns 503 (kill switch)."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
