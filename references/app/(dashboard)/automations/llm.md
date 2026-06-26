---
path: /automations
id: automations
name: Automations
title: Automations
description: A gallery of automation templates that, once picked, opens an inline task builder where the user composes a structured prompt (intent, schedule, team, scope) and generates it into a prefilled Personal-AI or new-group conversation.
relationship:
  upstream: "/chat"
  downstream: "/chat, /login"
cta:
  "Template search":
    type: input
    trigger: input
    description: "Rounded search box in the sticky header that filters the template grid by title/description (case-insensitive); always visible, even while the builder is open."
  "Category pills":
    type: tabs
    trigger: click
    description: "Horizontal config-driven category filter under the header; selecting a pill shows only that category's templates. Hidden while a template's builder is open."
  "Template card":
    type: button
    trigger: click
    description: "Grid card (emoji + title + 2-line description) that opens the inline task builder seeded with the template's preset intent/schedule/scope/team/topic."
  "Task builder":
    type: nav
    trigger: click
    description: "Inline panel replacing the grid after a template is picked; edits chips to live-rewrite a compiled prompt, then generates it into a conversation."
    items:
      "Back":
        type: button
        trigger: click
        description: "Arrow button — from an open sub-editor returns to the main builder; from the main builder returns to the template grid."
      "Compiled prompt editor":
        type: input
        trigger: input
        description: "Editable textarea showing the task body; below a dashed divider an auto-composed appendix (schedule + team + delivery + scope) updates as chips change."
      "Edit intent":
        type: button
        trigger: click
        description: "Amber chip opening the intent editor — a radio list of verbs (what the task does); choosing one swaps the body's leading verb and closes the editor."
      "Edit schedule":
        type: button
        trigger: click
        description: "Blue chip opening the schedule editor — radio list of when/how-often, with conditional date/time/weekday/condition inputs and a live preview, confirmed via Apply."
      "Team pickers":
        type: nav
        trigger: click
        description: "Who section (humans + agents) listing selected member chips; each chip's X removes it. Always present here (showTeamPickers on) — defaults to the user's Personal AI."
        items:
          "Add Agents":
            type: dialog
            trigger: click
            description: "Opens a member picker of friend-list agents (checkbox rows, already-added disabled); Add agents (N) commits the selection."
          "Add People":
            type: dialog
            trigger: click
            description: "Opens a member picker of friend-list people (checkbox rows, already-added disabled); Add people (N) commits the selection."
          "Remove member":
            type: button
            trigger: click
            description: "X on a member chip removes that agent/person from the team."
      "Edit scope":
        type: button
        trigger: click
        description: "Gray chip opening the scope editor — radio list choosing a one-time delivery vs. a lasting goal, confirmed via Apply."
      "Generate Prompt":
        type: button
        trigger: click
        description: "Footer button — assembles the prompt; signed out redirects to /login. With only Personal AI it prefills Personal AI, otherwise it creates a new group with the chosen members; either way navigates to /chat with the composer prefilled."
---

<!-- 正文待补充:后续人工补充该页面的详细介绍 -->
