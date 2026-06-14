---
name: teamily-ai-mobile-app-guide
description: >-
  Usage manual for the Teamily AI mobile app (iOS/Android, Expo Router) — the
  screen map, navigation relationships, CTAs, and feature areas. Use when
  operating, testing, automating, or integrating with the Teamily AI mobile
  app, or when you need to know which screen handles a task and how to reach it.
---

# Teamily AI Mobile App Guide

Teamily AI is a personal and social AI agent OS: an IM-style mobile app where
users chat with friends, groups, and AI agents; discover and remix
community-created content; and manage agents, credits, and subscriptions.

> **Route convention:** every path in this guide (e.g. `/chat`,
> `/settings/language`) is an **in-app Expo Router route**, not a web URL — it
> is what you pass to `router.push()` / `<Link href>` to navigate inside the
> native app. Expo Router **route groups** (parenthesised segments such as
> `(app)`, `(tabs)`, `(rewards)`) are organisational only and do **not** appear
> in the route — e.g. the file `app/(app)/(tabs)/discover/index.tsx` is reached
> at `/discover`. Dynamic segments are shown in brackets (`/profile/[uid]`).

This manual is generated from the per-route `llm.md` (screen) and
`layout.llm.md` (`_layout.tsx`) files under `apps/mobile/app`. Each screen
entry lists:

- **upstream** — screens that navigate into this screen
- **downstream** — screens this screen navigates to
- **CTAs** — the screen's main interactive controls. Each CTA notes its `type` (button, input, tabs, toggle, select, link, dialog, menu, nav), its `trigger` (how it's activated: tap, longpress, input, swipe, …; defaults to tap), and may nest child CTAs under `items`.

Regenerate with `pnpm gen:skill` (or `node generate-skill-md.mjs`) after editing any `llm.md` or `layout.llm.md`.

## How navigation works

- `/` is the app's initial route; it immediately redirects to [`/discover`](#screen-discover) (the Home tab).
- The app shell is a **bottom tab bar** with five tabs: Home ([`/discover`](#screen-discover)), Explore ([`/explore`](#screen-explore)), Chats ([`/conversation`](#screen-conversation)), Contacts ([`/contact`](#screen-contact)), and Me ([`/settings`](#screen-settings)). Each tab hosts its own navigation stack.
- Screens reachable directly from a tab root: _see per-screen upstream below_.
- Signed-out / token-expired users are intercepted by a reauth flow (`ReauthNavProvider`) rather than a login route.
- **Deep-link / external entry screens** (no in-app upstream; reached via shared links, push notifications, or invite URLs): [`/agent-settings/[agentId]`](#screen-agent-settingsagentid), [`/agents/config/[agentId]`](#screen-agentsconfigagentid), [`/apply-invite-code`](#screen-apply-invite-code), [`/chat/create-agent`](#screen-chatcreate-agent), [`/contact`](#screen-contact), [`/contact/invite-friends`](#screen-contactinvite-friends), [`/conversation`](#screen-conversation), [`/discover`](#screen-discover), [`/favorites`](#screen-favorites), [`/i/[code]`](#screen-icode), [`/invite-friends`](#screen-invite-friends), [`/invite/[...slug]`](#screen-inviteslug), [`/message-inbox`](#screen-message-inbox), [`/search`](#screen-search), [`/user-profile`](#screen-user-profile).
- **Hub screens** (most outbound links): [`/settings/system`](#screen-settingssystem) (14), [`/settings`](#screen-settings) (10), [`/settings/legacy`](#screen-settingslegacy) (8), [`/chat`](#screen-chat) (7), [`/credits-center`](#screen-credits-center) (7), [`/contact`](#screen-contact) (6).

## Feature areas

### Home & Discovery

The Home tab: the agent/group discovery feed and its detail and search screens. `/` is the app's initial route and redirects here.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/`](#screen-) | Home Redirect | The app's initial route. Renders nothing — it immediately redirects to /discover (the Home tab), so there is no extra root index screen for the user to see. |
| [`/discover`](#screen-discover) | Discover Feed | Home tab discovery feed with Following/Feeds/Agents/Groups tabs, category sub-tabs, and an infinite recommended-post list with like, bookmark, and share actions. |
| [`/discover-search`](#screen-discover-search) | Discover Search | Keyword search screen for discover posts that shows recent search history and renders matching post cards with like, bookmark, and share actions. |
| [`/discover-vertical`](#screen-discover-vertical) | Discover Vertical Explore | Full-screen vertical (swipe-up) explore feed of recommended posts seeded from the cached explore post, with per-post like, bookmark, comment, and share actions. |
| [`/discover-vertical/[id]`](#screen-discover-verticalid) | Discover Vertical Feed | Full-screen vertical (swipe-up) post feed opened at a specific post id, honoring scope/tag recommendation filters or a profile feed context, with per-post like, bookmark, comment, and share actions. |
| [`/discover/[id]`](#screen-discoverid) | Discover Post Redirect | Legacy compatibility route that redirects an old /discover/:id link to the global post detail stack, or back to the Discover feed when no id is present. |

### Explore, Posts & Profiles

The Explore tab's social feed: posts (showcases), the post composer, reporting, favorites, and user profiles.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/explore`](#screen-explore) | Explore Feed | Full-screen vertical social feed of discover posts that hides the tab bar while focused and routes hardware back to the Discover tab. |
| [`/favorites`](#screen-favorites) | Favorites | Paginated list of the user's favorited completed cards with pull to refresh and per-item unfavorite, opening profiles or conversations from card actions. |
| [`/post-editor/[id]`](#screen-post-editorid) | Post Editor | Editor screen for an existing post that lets the author update the cover language, title, description and prompt with optional AI generation, then save changes. |
| [`/post-use-case`](#screen-post-use-case) | Post Use Case | Composer that turns a chat result draft into a published post, previewing the work and offering AI-generated title, description and prompt before publishing. |
| [`/post/[id]`](#screen-postid) | Post Detail | Detail view for a single discover post showing its media, prompt and comments, with like, bookmark, comment, share, remix and an actions menu for edit/delete/report. |
| [`/post/edit/[id]`](#screen-posteditid) | Post Edit | Modal editor for an existing post that lets the author update the cover language, title, description and prompt with optional AI generation, then save changes. |
| [`/profile-follow-list`](#screen-profile-follow-list) | Profile Follow List | Followers and following list for a profile with tabbed switching, search filtering, per-row follow toggling and tapping a row to open that user's profile. |
| [`/profile/[uid]`](#screen-profileuid) | Profile Detail | Collapsible profile screen for a user or agent showing header stats and tabbed posts/saves, with follow, message, share, edit and social-list actions. |
| [`/report-post/[postId]`](#screen-report-postpostid) | Report Post | Form that lets a user pick one standard reason from a radio list and submit a report for the given post, returning back on success. |
| [`/user-profile`](#screen-user-profile) | User Profile | OpenIM contact profile showing a user's avatar, name and (for friends) email and remark, with actions to message, add contact, edit remark or copy email. |

### Chat & Messaging

The Chats tab and the conversation workspace: the conversation list, an open chat with friends/groups/agents, chat-scoped settings and tools, message search, and the notification inbox.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/chat`](#screen-chat) | Chat | Open conversation workspace rendering the message list, header bar, floating actions, and composer for a single or group chat. |
| [`/chat/agent-skills`](#screen-chatagent-skills) | Agent Skills | Skill library editor for a custom agent with Browse, Upload, and Create tabs to add, import, upload, or generate skills. |
| [`/chat/create-agent`](#screen-chatcreate-agent) | Create Agent | Route wrapper presenting the CreateAgentDialog; on success it replaces the route with the chat workspace, otherwise it pops back. |
| [`/chat/create-group`](#screen-chatcreate-group) | Create Group | Group creation screen for naming a group, selecting agent/friend members, and choosing a payment mode before creating. |
| [`/chat/group-settings`](#screen-chatgroup-settings) | Group Settings | Group conversation settings for managing the name, invite link, members, payment mode, mute, translation, and ownership actions. |
| [`/chat/history-search`](#screen-chathistory-search) | In-Chat History Search | Searches the current conversation by keyword across messages, media, files, and voice tabs, tapping a hit jumps back to that message in chat. |
| [`/chat/invite-friends`](#screen-chatinvite-friends) | Add Contact | Adds contacts via QR code, a shareable invite link, or email lookup, then chats with friends or sends an email invitation. |
| [`/chat/language-settings`](#screen-chatlanguage-settings) | Language Settings | Sets the app's system display language and the chat auto-translate target language, with a toggle to enable or disable auto-translation. |
| [`/chat/merge-history`](#screen-chatmerge-history) | Merged Chat History | Displays the nested messages contained in a forwarded merged-message bubble as a scrollable, read-only transcript. |
| [`/chat/read-receipt`](#screen-chatread-receipt) | Read Receipt | Lists which group members have read or not yet read a specific message, split across Read and Unread tabs. |
| [`/chat/user-settings`](#screen-chatuser-settings) | Chat Settings | Single-conversation settings for a friend or agent, covering profile, remark, mute, pin, block, translation, skills, and history actions. |
| [`/conversation`](#screen-conversation) | Chats | Chats tab listing all conversations with a pinned super-agent row, pull-to-refresh, search, and per-row swipe/long-press actions. |
| [`/message-inbox`](#screen-message-inbox) | Activity Inbox | Shows the social activity / notification feed with pull-to-refresh and pagination, auto-marking notifications read as they are viewed. |
| [`/search`](#screen-search) | Global Search | Global keyword search across contacts, agents, groups, and chat messages/files/media, with category filter tabs and per-section view-all links. |
| [`/search-category`](#screen-search-category) | Search Category Results | Shows all matches for one search category (messages, files, or media) across every conversation, grouped by conversation and paginated. |
| [`/search-messages-detail`](#screen-search-messages-detail) | Conversation Match Detail | Lists all message matches for a single conversation and the active search category, tapping a match jumps to it in chat. |

### Contacts & Invitations

The Contacts tab plus friend/agent management, invite flows, deep-linked invitations, and invite-code redemption.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/add-contact`](#screen-add-contact) | Add Contact | Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact. |
| [`/apply-invite-code`](#screen-apply-invite-code) | Apply Invite Code | Invite/promo code entry screen that verifies a code for a $5 welcome credit, with a skip option and onboarding hint. |
| [`/contact`](#screen-contact) | Contacts | Contacts tab home listing all contacts with search, an alphabet index, category nav rows, and a phone-contacts sync banner. |
| [`/contact/invite-friends`](#screen-contactinvite-friends) | Invite Friends | Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact. |
| [`/contact/my-agents`](#screen-contactmy-agents) | My Agents | Searchable list of the user's agent contacts with an alphabet index and a phone-contacts sync banner. |
| [`/contact/my-friends`](#screen-contactmy-friends) | My Friends | Searchable list of the user's friend contacts with an alphabet index and a phone-contacts sync banner. |
| [`/contact/phone-contacts`](#screen-contactphone-contacts) | Phone Contacts | Matches device phone contacts against Teamily, grouping them into on-Teamily and invitable sections with add, chat, and invite actions. |
| [`/i/[code]`](#screen-icode) | Invite Landing | Universal-link landing for https://teamily.ai/i/{code}. Lives at the root (sibling of (app)) so unauthenticated viewers still see the inviter card — an avatar→Teamily hero, the inviter's tagline, follower/post/like stats and top post (personal codes only), and a welcome-credit reward banner. The connect CTA either opens an in-place login modal (signed-out) or runs verifyInviteCode, builds the IM friendship, and drops the user into the inviter chat. Channel codes show a welcome-bonus variant. Invalid codes render a friendly empty state. |
| [`/invite-friend/[imUid]`](#screen-invite-friendimuid) | Invite Friend | Friend invitation acceptance card that resolves the inviter's profile and connects the two users into a direct chat. |
| [`/invite-friends`](#screen-invite-friends) | Invite Friends | Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact. |
| [`/invite-group/[groupId]`](#screen-invite-groupgroupid) | Invite Group | Group invitation acceptance card that resolves the group's name and joins the user into the group chat. |
| [`/invite/[...slug]`](#screen-inviteslug) | Invite Redirect | Deep-link router for teamily.ai invite links that redirects to the group, friend, or home route based on the URL segments. |

### AI Agents

Configuring custom and swarm AI agents.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/agent-settings/[agentId]`](#screen-agent-settingsagentid) | Agent Settings | Edit screen for a custom agent's avatar, nickname, and description, with save and (gated) delete actions. |
| [`/agents/config/[agentId]`](#screen-agentsconfigagentid) | Agent Config | Edit screen for a custom agent's avatar, nickname, and description (re-export of Agent Settings), with save and gated delete actions. |

### Rewards, Credits & Subscription

Root-level overlays for the credits center, credit usage history, and subscription/paywall — reachable from any tab.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/credit-usage`](#screen-credit-usage) | Usage | Read-only usage overview showing the 5-hour window, weekly cap, and on-demand usage with progress bars. |
| [`/credits-center`](#screen-credits-center) | Credits Center | Three-tab rewards hub for onboarding tasks, friend invites, and the user's credit balance and activity. |
| [`/subscription`](#screen-subscription) | Subscription | Subscription settings screen showing the current plan, manage/upgrade actions, restore purchases, and a help center link. |

### Settings & Account

The Me tab's settings hub and its sub-pages: account, security, privacy, language, connectors, creator earnings, storage, help, and the about/legal pages.

| Screen | Name | What it does |
| --- | --- | --- |
| [`/settings`](#screen-settings) | Me Profile Hub | The Me tab profile screen showing the current user's profile with posts feed; a menu opens a settings drawer linking to all settings entries. |
| [`/settings/account`](#screen-settingsaccount) | Edit Profile | Edit the user's avatar, public info, handle, details, and view private contact info; save persists handle and profile changes. |
| [`/settings/affiliate`](#screen-settingsaffiliate) | Affiliate Program | Shows affiliate earnings, the 25% commission rule, per-invitee payouts, and a share-invite block. |
| [`/settings/connectors`](#screen-settingsconnectors) | App Connectors | Lists third-party app connectors with search, and lets the user connect via OAuth or disconnect them. |
| [`/settings/creator-center`](#screen-settingscreator-center) | Creator Center | Shows creator earnings, a how-it-works guide with create options, a rewards ladder, recent earnings, and an FAQ. |
| [`/settings/delete-account`](#screen-settingsdelete-account) | Delete Account | Two-step confirmation to permanently deactivate the account by typing the username/email and the phrase "delete my account". |
| [`/settings/help`](#screen-settingshelp) | Help And Support | Lists help resources, opening the Help Center in a webview and offering an email contact option. |
| [`/settings/help/stack-webview`](#screen-settingshelpstack-webview) | Help Webview | Hosts an in-app webview for help and support URLs passed as route params, with title synced to the header. |
| [`/settings/invite-friends`](#screen-settingsinvite-friends) | Invite Friends | Legacy redirect route that replaces itself with the Credits Center invite tab on mount. |
| [`/settings/language`](#screen-settingslanguage) | Language Settings | Lets the user pick the app system language and chat translation language and toggle auto-translate. |
| [`/settings/legacy`](#screen-settingslegacy) | Settings | Top-level settings list with profile header, invite, favorites, billing and support rows, social links, and logout. |
| [`/settings/openclaw-management`](#screen-settingsopenclaw-management) | OpenClaw Management | Shows the Teamily API key and a quick-connect script with copy and key-visibility controls. |
| [`/settings/privacy`](#screen-settingsprivacy) | Privacy | Manage phone contacts sync and toggle the visibility of liked and saved posts, then save activity-visibility changes. |
| [`/settings/security`](#screen-settingssecurity) | Security | Shows bound email and phone contact information with entries to change or bind each. |
| [`/settings/security/change-email`](#screen-settingssecuritychange-email) | Change Email | Two-step flow to change the account email: enter a new address, then verify a 6-digit code sent to it. |
| [`/settings/security/change-phone`](#screen-settingssecuritychange-phone) | Change Phone | Two-step flow to change the account phone number: enter country code and number, then verify a 6-digit code sent via SMS. |
| [`/settings/storage`](#screen-settingsstorage) | Storage | Shows on-device cache sizes for task cards, previews, temp media, and photos with per-item clear actions; unsupported on web. |
| [`/settings/system`](#screen-settingssystem) | System Settings | Full settings list grouped by account, creator, plan, AI, preferences, and support; includes a usage card, social links, and sign out. |

## Screen reference

One entry per screen, grouped by feature area. Upstream/downstream paths link
to their entries.

### Home & Discovery — details

#### Screen /

**Home Redirect** — The app's initial route. Renders nothing — it immediately redirects to /discover (the Home tab), so there is no extra root index screen for the user to see.

- File: `app/(app)/(tabs)/index.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/discover`](#screen-discover)
- CTAs: _none_

#### Screen /discover

**Discover Feed** — Home tab discovery feed with Following/Feeds/Agents/Groups tabs, category sub-tabs, and an infinite recommended-post list with like, bookmark, and share actions.

- File: `app/(app)/(tabs)/discover/index.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/discover-vertical/[id]`](#screen-discover-verticalid), [`/post/[id]`](#screen-postid), [`/discover-search`](#screen-discover-search)
- CTAs:
  - **Feed Tabs** (`tabs`, tap) — Switches between Following, Feeds, Agents, and Groups views.
  - **Personal AI Chat** (`button`, tap) — Opens a chat with the user's Super Agent.
  - **Search** (`button`, tap) — Navigates to /discover-search.
  - **Category Sub-Tabs** (`select`, tap) — Revealed by pull, filters the feed by content category; an expand toggle shows the full category grid.
  - **Post Card** (`button`, tap) — Opens the post in the vertical detail feed /discover-vertical/[id].
    - **Author Avatar** (`button`, tap) — Opens the post author's profile.
    - **Like** (`toggle`, tap) — Likes or unlikes the post.
    - **Bookmark** (`toggle`, tap) — Bookmarks or unbookmarks the post.
    - **Share** (`button`, tap) — Opens the share sheet to forward the post to chats or external channels.
  - **Agent Chat** (`button`, tap) — On the Agents tab, opens a chat with the listed discover agent.
  - **Group Join** (`button`, tap) — On the Groups tab, joins the trending group via its invite URL.
  - **Pull To Refresh** (`button`, swipe) — Pull-to-refresh reloads the active feed or reveals the category sub-tabs.

#### Screen /discover-search

**Discover Search** — Keyword search screen for discover posts that shows recent search history and renders matching post cards with like, bookmark, and share actions.

- File: `app/(app)/discover-search.tsx`
- Upstream: [`/discover`](#screen-discover)
- Downstream: _none_
- CTAs:
  - **Search Input** (`input`, input) — Enters a keyword; submitting runs the search and saves it to history.
  - **Search Button** (`button`, tap) — Runs the search for the current keyword.
  - **Clear Keyword** (`button`, tap) — Clears the search input and results.
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **History Chip** (`button`, tap) — Re-runs a previous search from the history list.
  - **Clear History** (`button`, tap) — Prompts to confirm, then clears all saved search history.
  - **Result Card** (`button`, tap) — A matched post card.
    - **Like** (`toggle`, tap) — Likes or unlikes the post.
    - **Bookmark** (`toggle`, tap) — Bookmarks or unbookmarks the post.
    - **Share** (`button`, tap) — Opens the share sheet to forward the post to chats or external channels.

#### Screen /discover-vertical

**Discover Vertical Explore** — Full-screen vertical (swipe-up) explore feed of recommended posts seeded from the cached explore post, with per-post like, bookmark, comment, and share actions.

- File: `app/(app)/discover-vertical/index.tsx`
- Upstream: [`/discover`](#screen-discover)
- Downstream: _none_
- CTAs:
  - **Swipe Feed** (`nav`, swipe) — Vertical swipe pages through recommended posts.
  - **Back** (`button`, tap) — Returns to the previous screen or configured back path.
  - **Author** (`button`, tap) — Opens the post author's profile.
  - **Like** (`toggle`, tap) — Likes or unlikes the current post.
  - **Bookmark** (`toggle`, tap) — Bookmarks or unbookmarks the current post.
  - **Comment** (`button`, tap) — Opens the comments modal for the current post.
  - **Share** (`button`, tap) — Opens the share sheet to forward the post.
  - **Post Actions** (`menu`, tap) — Opens the post actions sheet (e.g. report, more options).

#### Screen /discover-vertical/[id]

**Discover Vertical Feed** — Full-screen vertical (swipe-up) post feed opened at a specific post id, honoring scope/tag recommendation filters or a profile feed context, with per-post like, bookmark, comment, and share actions.

- File: `app/(app)/discover-vertical/[id].tsx`
- Upstream: [`/discover`](#screen-discover), [`/discover-vertical`](#screen-discover-vertical)
- Downstream: _none_
- CTAs:
  - **Swipe Feed** (`nav`, swipe) — Vertical swipe pages through the post feed.
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Author** (`button`, tap) — Opens the post author's profile.
  - **Next Post** (`button`, tap) — Advances to the next post in the feed.
  - **Like** (`toggle`, tap) — Likes or unlikes the current post.
  - **Bookmark** (`toggle`, tap) — Bookmarks or unbookmarks the current post.
  - **Comment** (`button`, tap) — Opens the comments modal for the current post.
  - **Share** (`button`, tap) — Opens the share sheet to forward the post.
  - **Post Actions** (`menu`, tap) — Opens the post actions sheet.
  - **More** (`menu`, tap) — Opens the more/details modal for the current post.

#### Screen /discover/[id]

**Discover Post Redirect** — Legacy compatibility route that redirects an old /discover/:id link to the global post detail stack, or back to the Discover feed when no id is present.

- File: `app/(app)/(tabs)/discover/[id].tsx`
- Upstream: [`/discover`](#screen-discover)
- Downstream: [`/post/[id]`](#screen-postid), [`/discover`](#screen-discover)
- CTAs: _none_

### Explore, Posts & Profiles — details

#### Screen /explore

**Explore Feed** — Full-screen vertical social feed of discover posts that hides the tab bar while focused and routes hardware back to the Discover tab.

- File: `app/(app)/(tabs)/explore/index.tsx`
- Upstream: [`/discover`](#screen-discover)
- Downstream: [`/discover`](#screen-discover), [`/post/[id]`](#screen-postid), [`/profile/[uid]`](#screen-profileuid)
- CTAs: _none_

#### Screen /favorites

**Favorites** — Paginated list of the user's favorited completed cards with pull to refresh and per-item unfavorite, opening profiles or conversations from card actions.

- File: `app/(app)/favorites.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Back** (`button`, tap) — Navigates back from the favorites list.
  - **Unfavorite** (`button`, tap) — Removes a card from saves with optimistic update and undo on error.
  - **Pull To Refresh** (`button`, swipe) — Pull-down gesture that refetches the favorites list.
  - **Retry** (`button`, tap) — Refetches the list after a load error.

#### Screen /post-editor/[id]

**Post Editor** — Editor screen for an existing post that lets the author update the cover language, title, description and prompt with optional AI generation, then save changes.

- File: `app/(app)/post-editor/[id].tsx`
- Upstream: [`/post/[id]`](#screen-postid)
- Downstream: _none_
- CTAs:
  - **Language** (`select`, tap) — Opens the post language selector that controls the AI generation language.
  - **Generate Field** (`button`, tap) — Per-field AI sparkle button that regenerates the title, description or prompt text.
  - **Save** (`button`, tap) — Saves the edited post fields and navigates back on success.
  - **Close** (`button`, tap) — Dismisses the editor and navigates back.

#### Screen /post-use-case

**Post Use Case** — Composer that turns a chat result draft into a published post, previewing the work and offering AI-generated title, description and prompt before publishing.

- File: `app/(app)/post-use-case.tsx`
- Upstream: [`/post/[id]`](#screen-postid)
- Downstream: [`/settings`](#screen-settings), [`/post/[id]`](#screen-postid)
- CTAs:
  - **Post** (`button`, tap) — Validates the fields and publishes the post, then dismisses to the user's own profile posts tab.
  - **Language** (`select`, tap) — Opens the post language selector controlling the AI metadata language.
  - **Generate Field** (`button`, tap) — Per-field AI sparkle button that regenerates the title, description or prompt text.
  - **Back** (`button`, tap) — Dismisses the composer and navigates back.
  - **View Post** (`button`, tap) — Shown when the work was already published; opens the existing post detail.

#### Screen /post/[id]

**Post Detail** — Detail view for a single discover post showing its media, prompt and comments, with like, bookmark, comment, share, remix and an actions menu for edit/delete/report.

- File: `app/(app)/post/[id].tsx`
- Upstream: [`/explore`](#screen-explore), [`/discover`](#screen-discover), [`/profile/[uid]`](#screen-profileuid), [`/favorites`](#screen-favorites)
- Downstream: [`/post-editor/[id]`](#screen-post-editorid), [`/post-use-case`](#screen-post-use-case), [`/report-post/[postId]`](#screen-report-postpostid), [`/conversation`](#screen-conversation)
- CTAs:
  - **Like** (`button`, tap) — Toggles the like state on the post and updates the like count.
  - **Bookmark** (`button`, tap) — Toggles whether the post is saved to the viewer's bookmarks.
  - **Comment** (`button`, tap) — Opens the comment composer modal to add a comment or reply.
  - **Share** (`button`, tap) — Opens the share sheet to forward the post to conversations.
  - **Create My Own** (`button`, tap) — Opens the remix composer; on send, navigates to the chat conversation seeded with the remix prompt.
  - **Post Actions** (`menu`, tap) — Opens the post actions sheet with edit, delete and report options.
    - **Edit** (`button`, tap) — Navigates to the post editor at /post-editor/[id] (author only).
    - **Delete** (`button`, tap) — Confirms and deletes the post, then navigates back (author only).
    - **Report** (`button`, tap) — Navigates to the report screen at /report-post/[postId].

#### Screen /post/edit/[id]

**Post Edit** — Modal editor for an existing post that lets the author update the cover language, title, description and prompt with optional AI generation, then save changes.

- File: `app/(app)/post/edit/[id].tsx`
- Upstream: [`/post/[id]`](#screen-postid)
- Downstream: _none_
- CTAs:
  - **Language** (`select`, tap) — Opens the post language selector that controls the AI generation language.
  - **Generate Field** (`button`, tap) — Per-field AI sparkle button that regenerates the title, description or prompt text.
  - **Save** (`button`, tap) — Saves the edited post fields and navigates back on success.
  - **Close** (`button`, tap) — Dismisses the editor and navigates back.

#### Screen /profile-follow-list

**Profile Follow List** — Followers and following list for a profile with tabbed switching, search filtering, per-row follow toggling and tapping a row to open that user's profile.

- File: `app/(app)/profile-follow-list.tsx`
- Upstream: [`/profile/[uid]`](#screen-profileuid)
- Downstream: [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Following / Followers Tabs** (`tabs`, tap) — Switches between the following and followers lists.
  - **Search** (`input`, input) — Filters the visible follow list by name.
  - **Open User** (`nav`, tap) — Taps a row to open that user's profile at /profile/[uid].
  - **Follow** (`toggle`, tap) — Toggles following the listed user.
  - **Load More** (`button`, tap) — Fetches the next page of follow entries.
  - **Try Again** (`button`, tap) — Refetches the list after a load error.
  - **Back** (`button`, tap) — Navigates back from the follow list.

#### Screen /profile/[uid]

**Profile Detail** — Collapsible profile screen for a user or agent showing header stats and tabbed posts/saves, with follow, message, share, edit and social-list actions.

- File: `app/(app)/profile/[uid].tsx`
- Upstream: [`/explore`](#screen-explore), [`/post/[id]`](#screen-postid), [`/favorites`](#screen-favorites), [`/profile-follow-list`](#screen-profile-follow-list)
- Downstream: [`/post/[id]`](#screen-postid), [`/profile-follow-list`](#screen-profile-follow-list), [`/message-inbox`](#screen-message-inbox), [`/agents/config/[agentId]`](#screen-agentsconfigagentid), [`/settings/account`](#screen-settingsaccount)
- CTAs:
  - **Follow** (`toggle`, tap) — Toggles following the viewed user or agent.
  - **Message** (`button`, tap) — Opens a direct conversation with the viewed user.
  - **Share** (`button`, tap) — Opens the share sheet to share the profile link.
  - **Social List** (`button`, tap) — Opens the followers/following list at /profile-follow-list.
  - **Messages Inbox** (`button`, tap) — Opens the message inbox at /message-inbox (own profile only).
  - **Edit Profile** (`button`, tap) — Opens the account settings page to edit the own profile.
  - **Edit Agent** (`button`, tap) — Opens the agent config editor at /agents/config/[agentId].
  - **Menu** (`menu`, tap) — Opens the settings drawer (own profile only).
  - **Tabs** (`tabs`, tap) — Switches between the profile posts and saves tabs.
  - **Post Item** (`nav`, tap) — Opens a post from the feed tab at /post/[id].

#### Screen /report-post/[postId]

**Report Post** — Form that lets a user pick one standard reason from a radio list and submit a report for the given post, returning back on success.

- File: `app/(app)/report-post/[postId].tsx`
- Upstream: [`/post/[id]`](#screen-postid)
- Downstream: _none_
- CTAs:
  - **Reason Option** (`select`, tap) — Selects a single report reason from the radio list of standard options.
  - **Submit** (`button`, tap) — Submits the chosen report reason for the post and navigates back on success.
  - **Back** (`button`, tap) — Navigates back without submitting.

#### Screen /user-profile

**User Profile** — OpenIM contact profile showing a user's avatar, name and (for friends) email and remark, with actions to message, add contact, edit remark or copy email.

- File: `app/(app)/user-profile.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/conversation`](#screen-conversation)
- CTAs:
  - **Send Message** (`button`, tap) — Opens a direct conversation with the contact (friends only).
  - **Add Contact** (`button`, tap) — Sends a friend request to the user; disabled for private claw identities.
  - **Set Remark** (`dialog`, tap) — Opens a modal to edit the friend's remark name.
    - **Confirm** (`button`, tap) — Saves the new remark and closes the modal.
    - **Cancel** (`button`, tap) — Closes the remark modal without saving.
  - **Copy Email** (`button`, tap) — Copies the friend's email to the clipboard.
  - **Back** (`button`, tap) — Navigates back from the profile.

### Chat & Messaging — details

#### Screen /chat

**Chat** — Open conversation workspace rendering the message list, header bar, floating actions, and composer for a single or group chat.

- File: `app/(app)/chat/index.tsx`
- Upstream: [`/conversation`](#screen-conversation), [`/search`](#screen-search)
- Downstream: [`/chat/group-settings`](#screen-chatgroup-settings), [`/chat/user-settings`](#screen-chatuser-settings), [`/chat/history-search`](#screen-chathistory-search), [`/chat/read-receipt`](#screen-chatread-receipt), [`/profile/[uid]`](#screen-profileuid), [`/user-profile`](#screen-user-profile), [`/conversation`](#screen-conversation)
- CTAs:
  - **Header Bar** (`nav`, tap) — Top bar showing avatar, name, and connection status with navigation and tool controls.
    - **Back Button** (`nav`, tap) — Returns to the conversation list (/conversation); shown when a stack back is available.
    - **Avatar / Title** (`nav`, tap) — Group chat opens /chat/group-settings; single chat opens the peer profile (/profile/[uid]) or falls back to /chat/user-settings or a profile bottom sheet.
    - **Tasks / Skills Button** (`button`, tap) — Settings2 icon (agent chats only) opens the tasks-history bottom sheet for the agent.
    - **Search Button** (`nav`, tap) — Opens the in-conversation history search screen (/chat/history-search).
    - **More (Ellipsis) Button** (`nav`, tap) — Opens /chat/group-settings for groups or /chat/user-settings for single chats.
  - **Message List** (`nav`, tap/longpress/scroll) — FlashList of messages; scroll paginates history, long-press opens per-message action sheet, tapping links/avatars navigates to profiles or read receipts.
  - **Floating Actions** (`button`, tap) — Bottom-right FABs for navigating the message list.
    - **Jump to Mention** (`button`, tap) — Jumps to the next message that @-mentions the user (shown when at-me count > 0).
    - **Scroll to Bottom** (`button`, tap) — Scrolls to the latest message; badge shows new incoming count and fetches the latest window if needed.
  - **Composer** (`input`, input) — Bottom message composer with text input, mentions, attachments, emoji, voice, and send.
    - **Text Input** (`input`, input) — Multiline message field supporting @-mentions (groups), URL highlighting, and pasted images/media.
    - **Expand Button** (`button`, tap) — Maximize2 icon opens the expanded full-screen input modal when content is tall.
    - **Emoji / Keyboard Toggle** (`toggle`, tap) — Toggles the emoji/sticker panel; switches between Smile and Keyboard icons.
    - **Attachment Button** (`toggle`, tap) — Paperclip icon toggles the attachment panel for picking images, video, files, and media.
    - **Send / Mic Button** (`button`, tap) — Sends the message when there is content; otherwise starts voice recording.
    - **Quote Preview** (`button`, tap) — Shows the quoted message being replied to with a dismiss (X) control.
    - **Pending Attachment Chip** (`button`, tap) — Preview chip per staged attachment with a remove (X) control.
  - **Selection Toolbar** (`button`, tap) — Replaces the composer in multi-select mode for batch message operations.
    - **Cancel Selection** (`button`, tap) — Exits multi-select mode.
    - **Forward (Step)** (`button`, tap) — Forwards the selected messages individually via the forward modal.
    - **Forward (Merge)** (`button`, tap) — Forwards the selected messages as one merged message.
    - **Delete Selected** (`button`, tap) — Deletes the selected messages after confirmation.
  - **Not Found Fallback** (`nav`, tap) — Shown when no current conversation exists; Back to Conversations returns to /conversation.

#### Screen /chat/agent-skills

**Agent Skills** — Skill library editor for a custom agent with Browse, Upload, and Create tabs to add, import, upload, or generate skills.

- File: `app/(app)/chat/agent-skills.tsx`
- Upstream: [`/chat/user-settings`](#screen-chatuser-settings)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Back Button** (`nav`, tap) — Returns to the previous screen (router.back).
  - **Tabs** (`tabs`, tap) — Switches between Browse, Upload, and Create skill sections.
  - **Browse Tab** (`nav`, tap) — Searchable, tag-filterable list of library skills.
    - **Search Input** (`input`, input) — Debounced text search over the skill library.
    - **Tag Filter** (`button`, tap) — Horizontal chips filtering skills by tag (All by default).
    - **Add / Added Toggle** (`toggle`, tap) — Adds or removes a skill from the agent and syncs enabled skills to the server.
    - **Load More** (`button`, tap) — Fetches the next page of library skills.
    - **Retry** (`button`, tap) — Refetches the skill list after a load error.
  - **Upload Tab** (`nav`, tap) — Uploads a packaged skill or imports one from GitHub.
    - **Tap to Upload** (`button`, tap) — Opens the document picker to upload a .skill/.zip package and adds it to the agent.
    - **GitHub URL Input** (`input`, input) — Field for a GitHub repository URL to import a skill from.
    - **Import Button** (`button`, tap) — Imports the skill from the entered GitHub URL and adds it to the agent.
  - **Create Tab** (`nav`, tap) — Describes a new skill to generate, with template presets.
    - **Describe Input** (`input`, input) — Multiline prompt describing the skill to create.
    - **Send Prompt** (`button`, tap) — Sends the description as a message to the agent conversation and returns to the chat.
    - **Template Preset** (`button`, tap) — Fills the describe input with a prefilled prompt for the chosen template.

#### Screen /chat/create-agent

**Create Agent** — Route wrapper presenting the CreateAgentDialog; on success it replaces the route with the chat workspace, otherwise it pops back.

- File: `app/(app)/chat/create-agent.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Create Agent Dialog** (`dialog`, tap) — Agent-creation sheet; closing without creating returns to the previous screen, and successful creation replaces this route with /chat.

#### Screen /chat/create-group

**Create Group** — Group creation screen for naming a group, selecting agent/friend members, and choosing a payment mode before creating.

- File: `app/(app)/chat/create-group.tsx`
- Upstream: [`/chat/user-settings`](#screen-chatuser-settings)
- Downstream: [`/chat`](#screen-chat), [`/conversation`](#screen-conversation)
- CTAs:
  - **Back Button** (`nav`, tap) — Returns to the previous screen (router.back).
  - **Create Button** (`button`, tap) — Creates the group with the selected members and payment mode, then opens the new group chat (/chat).
  - **Group Name Input** (`input`, input) — Optional group name field; falls back to an auto-generated name from member names.
  - **Search Contacts** (`input`, input) — Filters the contact list by remark, nickname, or user ID.
  - **Member Type Tabs** (`tabs`, tap) — Switches the selectable list between Agents and Friends.
  - **Contact Row** (`toggle`, tap) — Toggles selection of a contact for the group (preselected members are locked).
  - **Payment Mode** (`select`, tap) — Chooses who pays for agent usage in the group; switching opens a confirmation dialog.
    - **Members Pay** (`button`, tap) — Selects the members-pay billing mode.
    - **Owner Pays** (`button`, tap) — Selects the owner-pays billing mode (uses a daily budget cap).
  - **Payment Mode Confirm Dialog** (`dialog`, tap) — Confirms or cancels the pending payment-mode change.

#### Screen /chat/group-settings

**Group Settings** — Group conversation settings for managing the name, invite link, members, payment mode, mute, translation, and ownership actions.

- File: `app/(app)/chat/group-settings.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: [`/conversation`](#screen-conversation)
- CTAs:
  - **Back Button** (`nav`, tap) — Returns to the previous screen (router.back).
  - **Rename Button** (`dialog`, tap) — Opens the rename dialog to change the group name (permitted roles only).
  - **Copy Invite Link** (`button`, tap) — Copies the group invite link to the clipboard.
  - **Invite via Link or Email** (`dialog`, tap) — Opens the share sheet to send the group invite link or email.
  - **Quick Actions** (`button`, tap) — Row of quick action buttons under the group header.
    - **Add Agent** (`dialog`, tap) — Opens the invite dialog to add agent members.
    - **Add Friend** (`dialog`, tap) — Opens the invite dialog to add friend members.
    - **Mute / Unmute** (`toggle`, tap) — Toggles muting of group notifications.
    - **Quit** (`dialog`, tap) — Opens the leave-group confirmation dialog.
  - **Translation Section** (`toggle`, tap) — Conversation auto-translation settings for the group.
  - **Payment Mode** (`select`, tap) — Owner-only toggle between Members Pay and Owner Pays, confirmed via dialog.
  - **Member Tabs** (`tabs`, tap) — Switches the member list between Agents and Friends.
  - **Member Row** (`nav`, tap/longpress) — Tap opens the member profile sheet; long-press (context menu) exposes management actions.
    - **Set / Remove Admin** (`button`, tap) — Owner action to grant or revoke admin for a human member.
    - **Transfer Owner** (`dialog`, tap) — Owner action to transfer group ownership to a member (confirmed via dialog).
    - **Kick Member** (`dialog`, tap) — Removes a member from the group after confirmation.
  - **Dismiss Group** (`dialog`, tap) — Owner-only action to dissolve the group after confirmation, then returns to /conversation.

#### Screen /chat/history-search

**In-Chat History Search** — Searches the current conversation by keyword across messages, media, files, and voice tabs, tapping a hit jumps back to that message in chat.

- File: `app/(app)/chat/history-search.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Back** (`button`, tap) — Returns to the chat conversation.
  - **Search Input** (`input`, input) — Auto-focused keyword field (max 64 chars) that debounces and runs the in-conversation search for the active tab.
  - **Category Tabs** (`tabs`, tap) — Switches between Messages (keyword required), Media, Files, and Voice; media/file/voice browse by type without a keyword.
  - **Result Item** (`button`, tap) — Stages a pending jump to the selected message, dismisses the keyboard, and pops back to chat scrolled to it.

#### Screen /chat/invite-friends

**Add Contact** — Adds contacts via QR code, a shareable invite link, or email lookup, then chats with friends or sends an email invitation.

- File: `app/(app)/chat/invite-friends.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Download QR Code** (`button`, tap) — Fetches the personal invite QR image and opens the native share sheet to save or send it.
  - **Copy Link** (`button`, tap) — Copies the personal invite link to the clipboard.
  - **Email Input** (`input`, input) — Debounced email field that validates format and looks up the user by email; submit also triggers the search.
  - **Result Action** (`button`, tap) — Context action on the lookup result.
    - **Chat** (`button`, tap) — Opens a direct conversation with an existing friend.
    - **Invite** (`button`, tap) — Sends a friend invitation email to the looked-up user.

#### Screen /chat/language-settings

**Language Settings** — Sets the app's system display language and the chat auto-translate target language, with a toggle to enable or disable auto-translation.

- File: `app/(app)/chat/language-settings.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **System Language** (`select`, tap) — Opens a bottom sheet to pick the app display language or follow the device system language.
  - **Chat Language** (`select`, tap) — Opens a bottom sheet to pick the target language messages are translated into.
  - **Auto Translate** (`toggle`, tap) — Enables or disables automatic chat message translation.

#### Screen /chat/merge-history

**Merged Chat History** — Displays the nested messages contained in a forwarded merged-message bubble as a scrollable, read-only transcript.

- File: `app/(app)/chat/merge-history.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the chat conversation.

#### Screen /chat/read-receipt

**Read Receipt** — Lists which group members have read or not yet read a specific message, split across Read and Unread tabs.

- File: `app/(app)/chat/read-receipt.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: [`/user-profile`](#screen-user-profile)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Read/Unread Tabs** (`tabs`, tap) — Switches between the list of members who have read and those who have not read the message.
  - **Member Row** (`button`, tap) — Opens the selected member's user profile.

#### Screen /chat/user-settings

**Chat Settings** — Single-conversation settings for a friend or agent, covering profile, remark, mute, pin, block, translation, skills, and history actions.

- File: `app/(app)/chat/user-settings.tsx`
- Upstream: [`/chat`](#screen-chat)
- Downstream: [`/chat/create-group`](#screen-chatcreate-group), [`/chat/agent-skills`](#screen-chatagent-skills), [`/settings/connectors`](#screen-settingsconnectors), [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Back Button** (`nav`, tap) — Returns to the previous screen (router.back).
  - **View Full Profile** (`nav`, tap) — Opens the peer's full profile via the IM user ID.
  - **Copy Email** (`button`, tap) — Copies the friend's email address to the clipboard (when present).
  - **Create New Group** (`nav`, tap) — Opens /chat/create-group prefilled with this user as an initial member.
  - **Translation Section** (`toggle`, tap) — Conversation auto-translation settings.
  - **Set Remark** (`dialog`, tap) — Opens a modal to set or edit the friend's remark name (friends only).
  - **Mute Notifications** (`toggle`, tap) — Toggles muting of conversation notifications.
  - **Pin to Top** (`toggle`, tap) — Toggles pinning the conversation to the top of the list.
  - **Block User** (`toggle`, tap) — Toggles the user's blacklist status.
  - **Clear Chat History** (`dialog`, tap) — Confirms and clears all messages in the conversation.
  - **Delete Friend** (`dialog`, tap) — Confirms removal of the friend, then returns to the previous screen.
  - **Add Contact** (`button`, tap) — Sends a friend request to a non-friend, non-agent user.
  - **Agent Info Section** (`nav`, tap) — For agent conversations, shows agent profile, skills, and connector controls.
    - **Open Agent Profile** (`nav`, tap) — Navigates to the agent's profile when available.
    - **Open Skill Editor** (`nav`, tap) — Opens /chat/agent-skills for a custom agent with the resolved agent ID and title.
    - **Connect App / Connectors** (`nav`, tap) — Opens the connectors settings page (/settings/connectors).
    - **Enable / Disable Connector** (`toggle`, tap) — Enables or disables an MCP connector slug for the custom agent.

#### Screen /conversation

**Chats** — Chats tab listing all conversations with a pinned super-agent row, pull-to-refresh, search, and per-row swipe/long-press actions.

- File: `app/(app)/(tabs)/conversation/index.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#screen-chat), [`/search`](#screen-search), [`/discover`](#screen-discover)
- CTAs:
  - **Search Bar** (`button`, tap) — Opens the global search screen (/search).
  - **New Menu** (`menu`, tap) — Top-right header menu (NewMenu) for starting new chats/groups; dismisses open row swipes before opening.
  - **Super Agent Row** (`nav`, tap) — Pinned personal-AI conversation row; opens its chat workspace (/chat).
  - **Conversation Row** (`nav`, tap/longpress) — Tap opens the conversation in /chat; long-press / swipe reveals row actions.
    - **Pin / Unpin** (`button`, tap) — Toggles pinned state for the conversation via the IM SDK.
    - **Mark as Read** (`button`, tap) — Clears the unread count and at-mention flag for the conversation.
    - **Delete** (`dialog`, tap) — Confirms then deletes the conversation and all its messages.
  - **Discover Agents** (`nav`, tap) — Empty-state button that navigates to /discover to find agents.
  - **Pull to Refresh** (`button`, swipe) — Pull-down gesture re-fetches the conversation list (re-runs auth queries if the SDK is not connected).

#### Screen /message-inbox

**Activity Inbox** — Shows the social activity / notification feed with pull-to-refresh and pagination, auto-marking notifications read as they are viewed.

- File: `app/(app)/message-inbox.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Flushes pending read state and returns to the previous screen.
  - **Mark All As Read** (`button`, tap) — Marks every notification as read and clears the unread badge.
  - **Notification Row** (`button`, tap) — Marks the opened notification as read.
  - **Pull To Refresh** (`button`, swipe) — Reloads the latest activity feed from the server.

#### Screen /search

**Global Search** — Global keyword search across contacts, agents, groups, and chat messages/files/media, with category filter tabs and per-section view-all links.

- File: `app/(app)/search.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/search-messages-detail`](#screen-search-messages-detail), [`/search-category`](#screen-search-category)
- CTAs:
  - **Close** (`button`, tap) — Dismisses the search screen and returns to the previous screen.
  - **Search Input** (`input`, input) — Auto-focused keyword field that searches across all categories; includes a clear button.
  - **Category Tabs** (`tabs`, tap) — Filters results to All, Contacts, Agents, Groups, Messages, Files, or Media.
  - **Contact/Agent Result** (`button`, tap) — Opens a direct conversation with the selected contact or agent.
  - **Group Result** (`button`, tap) — Opens the selected group conversation.
  - **Message Result** (`button`, tap) — Jumps to the matched message inside its conversation.
  - **Conversation Group Header** (`button`, tap) — Opens the single-conversation match detail for that conversation and category.
  - **View All / View More** (`button`, tap) — Opens the per-category aggregated results screen, or expands the section to its dedicated tab.

#### Screen /search-category

**Search Category Results** — Shows all matches for one search category (messages, files, or media) across every conversation, grouped by conversation and paginated.

- File: `app/(app)/search-category.tsx`
- Upstream: [`/search`](#screen-search)
- Downstream: [`/search-messages-detail`](#screen-search-messages-detail)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Conversation Group Header** (`button`, tap) — Opens the single-conversation match detail for that conversation, query, and category.
  - **Message Result** (`button`, tap) — Jumps to the matched message inside its conversation.

#### Screen /search-messages-detail

**Conversation Match Detail** — Lists all message matches for a single conversation and the active search category, tapping a match jumps to it in chat.

- File: `app/(app)/search-messages-detail.tsx`
- Upstream: [`/search`](#screen-search), [`/search-category`](#screen-search-category)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Message Result** (`button`, tap) — Jumps to the matched message inside its conversation.

### Contacts & Invitations — details

#### Screen /add-contact

**Add Contact** — Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact.

- File: `app/(app)/add-contact.tsx`
- Upstream: [`/contact`](#screen-contact)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Download QR Code** (`button`, tap) — Shares the personal invite QR code as a PNG file.
  - **Copy Link** (`button`, tap) — Copies the personal invite link to the clipboard.
  - **Email Lookup** (`input`, input) — Email field that searches for an existing Teamily user after a short debounce or on submit.
  - **Chat** (`button`, tap) — Shown when the looked-up email is an existing friend; opens the direct conversation.
  - **Invite** (`button`, tap) — Shown for an existing non-friend user or unknown email; sends a friend invitation email.
  - **Back** (`button`, tap) — Chevron in the header that pops the screen.

#### Screen /apply-invite-code

**Apply Invite Code** — Invite/promo code entry screen that verifies a code for a $5 welcome credit, with a skip option and onboarding hint.

- File: `app/(app)/apply-invite-code/index.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Invite Or Promo Code** (`input`, input) — Auto-uppercased text field for the invite or promo code; submitting the keyboard triggers Apply.
  - **Apply** (`button`, tap) — Verifies the entered code, shows a success toast on a recognized code, and returns to the prior screen or a redirect target.
  - **Skip** (`button`, tap) — Skips code entry, going back or replacing to the redirect target.
  - **Back** (`button`, tap) — App bar back button that pops the screen.

#### Screen /contact

**Contacts** — Contacts tab home listing all contacts with search, an alphabet index, category nav rows, and a phone-contacts sync banner.

- File: `app/(app)/(tabs)/contact/index.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/add-contact`](#screen-add-contact), [`/contact/my-agents`](#screen-contactmy-agents), [`/contact/my-friends`](#screen-contactmy-friends), [`/contact/phone-contacts`](#screen-contactphone-contacts), [`/user-profile`](#screen-user-profile), [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Add Contact** (`button`, tap) — Plus button in the app bar that opens the Add Contact screen.
  - **Search Contacts** (`input`, input) — Search bar that filters the contact list by name; hides the category nav and alphabet index while active.
  - **Category Nav Row** (`nav`, tap) — Rows that open a contact category subpage.
    - **My Agents** (`nav`, tap) — Opens the My Agents list.
    - **My Friends** (`nav`, tap) — Opens the My Friends list.
    - **Phone Contacts** (`nav`, tap) — Opens the Phone Contacts matching screen.
  - **Contact Row** (`button`, tap) — Opens the user profile; agents open /user-profile, human friends open /profile/[uid].
  - **Phone Contacts Sync Banner** (`button`, tap) — Banner (shown when sync is off or access is limited) that opens the Phone Contacts screen; can be dismissed.

#### Screen /contact/invite-friends

**Invite Friends** — Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact.

- File: `app/(app)/(tabs)/contact/invite-friends.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Download QR Code** (`button`, tap) — Shares the personal invite QR code as a PNG file.
  - **Copy Link** (`button`, tap) — Copies the personal invite link to the clipboard.
  - **Email Lookup** (`input`, input) — Email field that searches for an existing Teamily user after a short debounce or on submit.
  - **Chat** (`button`, tap) — Shown when the looked-up email is an existing friend; opens the direct conversation.
  - **Invite** (`button`, tap) — Shown for an existing non-friend user or unknown email; sends a friend invitation email.
  - **Back** (`button`, tap) — Chevron in the header that pops the screen.

#### Screen /contact/my-agents

**My Agents** — Searchable list of the user's agent contacts with an alphabet index and a phone-contacts sync banner.

- File: `app/(app)/(tabs)/contact/my-agents.tsx`
- Upstream: [`/contact`](#screen-contact)
- Downstream: [`/user-profile`](#screen-user-profile), [`/profile/[uid]`](#screen-profileuid), [`/contact/phone-contacts`](#screen-contactphone-contacts)
- CTAs:
  - **Search Agents** (`input`, input) — Search bar that filters the agent list by name.
  - **Agent Row** (`button`, tap) — Opens the contact's profile; agents open /user-profile, others open /profile/[uid].
  - **Phone Contacts Sync Banner** (`button`, tap) — Banner (shown when sync is off or access is limited) that opens the Phone Contacts screen; can be dismissed.

#### Screen /contact/my-friends

**My Friends** — Searchable list of the user's friend contacts with an alphabet index and a phone-contacts sync banner.

- File: `app/(app)/(tabs)/contact/my-friends.tsx`
- Upstream: [`/contact`](#screen-contact)
- Downstream: [`/user-profile`](#screen-user-profile), [`/profile/[uid]`](#screen-profileuid), [`/contact/phone-contacts`](#screen-contactphone-contacts)
- CTAs:
  - **Search Friends** (`input`, input) — Search bar that filters the friend list by name.
  - **Friend Row** (`button`, tap) — Opens the contact's profile; agents open /user-profile, others open /profile/[uid].
  - **Phone Contacts Sync Banner** (`button`, tap) — Banner (shown when sync is off or access is limited) that opens the Phone Contacts screen; can be dismissed.

#### Screen /contact/phone-contacts

**Phone Contacts** — Matches device phone contacts against Teamily, grouping them into on-Teamily and invitable sections with add, chat, and invite actions.

- File: `app/(app)/(tabs)/contact/phone-contacts.tsx`
- Upstream: [`/contact`](#screen-contact)
- Downstream: [`/user-profile`](#screen-user-profile), [`/settings/privacy`](#screen-settingsprivacy)
- CTAs:
  - **Allow Access** (`button`, tap) — Opens the permission prompt sheet to request phone-contacts access; opens system Settings when access can't be re-requested.
  - **Open Settings** (`button`, tap) — Shown when sync is disabled or permission is permanently denied; opens privacy settings or the system settings.
  - **Allow Full Access** (`link`, tap) — Inline link in the limited-access banner that opens system settings to grant full contacts access.
  - **Refresh** (`button`, tap) — Top refresh button that re-runs the full contact scan and match.
  - **Pull To Refresh** (`button`, swipe) — Pull-down gesture that re-evaluates permission or re-runs the full contact scan.
  - **Contact Row** (`button`, tap) — Opens a friend's chat, or a matched non-friend user's profile.
  - **Add** (`button`, tap) — Sends a friend request to a matched Teamily user who is not yet a friend.
  - **Invite** (`button`, tap) — Opens the invite channel sheet (SMS, WhatsApp, or system share) for an unmatched contact.

#### Screen /i/[code]

**Invite Landing** — Universal-link landing for https://teamily.ai/i/{code}. Lives at the root (sibling of (app)) so unauthenticated viewers still see the inviter card — an avatar→Teamily hero, the inviter's tagline, follower/post/like stats and top post (personal codes only), and a welcome-credit reward banner. The connect CTA either opens an in-place login modal (signed-out) or runs verifyInviteCode, builds the IM friendship, and drops the user into the inviter chat. Channel codes show a welcome-bonus variant. Invalid codes render a friendly empty state.

- File: `app/i/[code].tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#screen-chat), [`/discover`](#screen-discover)
- CTAs:
  - **Connect / claim bonus** (`button`, tap) — Primary CTA. Signed out → opens the in-place login modal, then consumes the code (verifyInviteCode) and opens the inviter chat. Signed in → applies the code (or claims the channel welcome bonus) and navigates into the chat; self-links and already-applied codes short-circuit to a toast and open the existing chat.
  - **Login modal** (`dialog`, tap) — In-place sign-in/register sheet shown for signed-out viewers; on success the invite code is consumed here (not at login) so consumption, error handling, and addFriend stay on this screen.
  - **Top post** (`button`, tap) — Preview card of the inviter's top post (personal codes only) showing title, likes, and bookmarks.
  - **Terms / Privacy links** (`link`, tap) — Open the Terms of Service and Privacy Policy in the in-app browser.
  - **Close** (`button`, tap) — X button — pops back if possible, otherwise replaces to the tabs home.

#### Screen /invite-friend/[imUid]

**Invite Friend** — Friend invitation acceptance card that resolves the inviter's profile and connects the two users into a direct chat.

- File: `app/(app)/invite-friend/[imUid].tsx`
- Upstream: [`/invite/[...slug]`](#screen-inviteslug)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Accept Invitation** (`button`, tap) — Accepts the friend invite, refreshes the contact list, and opens the direct chat; prompts sign-in first if logged out.
  - **Close** (`button`, tap) — X button that dismisses the screen, going back or replacing to the home route.
  - **Terms Of Service** (`link`, tap) — Opens the Terms of Service in an in-app webview.
  - **Privacy Policy** (`link`, tap) — Opens the Privacy Policy in an in-app webview.

#### Screen /invite-friends

**Invite Friends** — Add-contact screen with a personal QR code, shareable invite link, and email lookup to chat with or invite a contact.

- File: `app/(app)/invite-friends.tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Download QR Code** (`button`, tap) — Shares the personal invite QR code as a PNG file.
  - **Copy Link** (`button`, tap) — Copies the personal invite link to the clipboard.
  - **Email Lookup** (`input`, input) — Email field that searches for an existing Teamily user after a short debounce or on submit.
  - **Chat** (`button`, tap) — Shown when the looked-up email is an existing friend; opens the direct conversation.
  - **Invite** (`button`, tap) — Shown for an existing non-friend user or unknown email; sends a friend invitation email.
  - **Back** (`button`, tap) — Chevron in the header that pops the screen.

#### Screen /invite-group/[groupId]

**Invite Group** — Group invitation acceptance card that resolves the group's name and joins the user into the group chat.

- File: `app/(app)/invite-group/[groupId].tsx`
- Upstream: [`/invite/[...slug]`](#screen-inviteslug)
- Downstream: [`/chat`](#screen-chat)
- CTAs:
  - **Join Group** (`button`, tap) — Joins the group via invite, refreshes the group list, and opens the group chat; prompts sign-in first if logged out.
  - **Close** (`button`, tap) — X button that dismisses the screen, going back or replacing to the home route.
  - **Terms Of Service** (`link`, tap) — Opens the Terms of Service in an in-app webview.
  - **Privacy Policy** (`link`, tap) — Opens the Privacy Policy in an in-app webview.

#### Screen /invite/[...slug]

**Invite Redirect** — Deep-link router for teamily.ai invite links that redirects to the group, friend, or home route based on the URL segments.

- File: `app/(app)/invite/[...slug].tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/invite-group/[groupId]`](#screen-invite-groupgroupid), [`/invite-friend/[imUid]`](#screen-invite-friendimuid), `/(tabs)`
- CTAs: _none_

### AI Agents — details

#### Screen /agent-settings/[agentId]

**Agent Settings** — Edit screen for a custom agent's avatar, nickname, and description, with save and (gated) delete actions.

- File: `app/(app)/agent-settings/[agentId].tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Save** (`button`, tap) — App bar action that saves changed agent fields; disabled until the draft differs from the saved state.
  - **Change Photo** (`button`, tap) — Picks and uploads a new agent avatar image.
  - **Nickname** (`input`, input) — Text field for the agent's display name.
  - **Description** (`input`, input) — Multiline field for the agent's description.
  - **Delete** (`button`, tap) — Danger-zone button (currently gated off) that confirms via alert and permanently deletes the agent, then returns to the user's profile.
  - **Retry** (`button`, tap) — Shown on load failure; refetches the agent detail.
  - **Back** (`button`, tap) — App bar back button that pops the screen.

#### Screen /agents/config/[agentId]

**Agent Config** — Edit screen for a custom agent's avatar, nickname, and description (re-export of Agent Settings), with save and gated delete actions.

- File: `app/(app)/agents/config/[agentId].tsx`
- Upstream: _none (direct/external entry)_
- Downstream: [`/profile/[uid]`](#screen-profileuid)
- CTAs:
  - **Save** (`button`, tap) — App bar action that saves changed agent fields; disabled until the draft differs from the saved state.
  - **Change Photo** (`button`, tap) — Picks and uploads a new agent avatar image.
  - **Nickname** (`input`, input) — Text field for the agent's display name.
  - **Description** (`input`, input) — Multiline field for the agent's description.
  - **Delete** (`button`, tap) — Danger-zone button (currently gated off) that confirms via alert and permanently deletes the agent, then returns to the user's profile.
  - **Retry** (`button`, tap) — Shown on load failure; refetches the agent detail.
  - **Back** (`button`, tap) — App bar back button that pops the screen.

### Rewards, Credits & Subscription — details

#### Screen /credit-usage

**Usage** — Read-only usage overview showing the 5-hour window, weekly cap, and on-demand usage with progress bars.

- File: `app/(app)/(rewards)/credit-usage/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /credits-center

**Credits Center** — Three-tab rewards hub for onboarding tasks, friend invites, and the user's credit balance and activity.

- File: `app/(app)/(rewards)/credits-center/index.tsx`
- Upstream: [`/settings`](#screen-settings), [`/discover`](#screen-discover), [`/chat`](#screen-chat)
- Downstream: [`/credit-usage`](#screen-credit-usage), [`/discover`](#screen-discover), [`/conversation`](#screen-conversation), [`/chat`](#screen-chat), [`/chat/create-agent`](#screen-chatcreate-agent), [`/chat/create-group`](#screen-chatcreate-group), [`/settings/account`](#screen-settingsaccount)
- CTAs:
  - **Tab Segmented Control** (`tabs`, tap) — Switches between Onboarding, Invite, and My Credits tabs by updating the tab query param. Order and default depend on login-streak visibility.
  - **Onboarding Task Row** (`button`, tap) — Navigates to the in-app destination for the task (discover, Personal AI chat, create-agent, create-group, or settings account). Disabled when the task is completed.
  - **Apply Credits (Onboarding)** (`button`, tap) — Switches to the My Credits tab.
  - **First 7 Days Info** (`button`, tap) — Opens an info popover explaining the first-7-days bonus.
  - **Login Streak Info** (`button`, tap) — Opens an info popover explaining the login streak rewards.
  - **Apply Credits (Invite)** (`button`, tap) — Switches to the My Credits tab.
  - **Accept An Invite Code** (`input`, input) — Enters an invite code; the Apply pill verifies and redeems it. Hidden once a code has been redeemed for the account.
  - **Apply Invite Code** (`button`, tap) — Verifies and applies the entered invite code, showing a success or error result.
  - **Send An Invite** (`button`, tap) — Shared invite block for sharing the user's own invite code/link.
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /subscription

**Subscription** — Subscription settings screen showing the current plan, manage/upgrade actions, restore purchases, and a help center link.

- File: `app/(app)/(rewards)/subscription/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Help Center** (`link`, tap) — Opens the Teamily help center in an in-app webview.
  - **Restore Purchases** (`button`, tap) — Prompts to restore prior purchases via RevenueCat and shows a success/none toast.
  - **Upgrade / View Plans** (`button`, tap) — Presents the RevenueCat paywall for free or expired users to subscribe.
  - **Open Manager** (`link`, tap) — Opens the RevenueCat Customer Center for paid users to cancel or manage billing.
  - **Manage Elsewhere** (`button`, tap) — For cross-platform subscriptions, opens the Teamily web settings or Google Play subscriptions page in the browser.
  - **Back** (`button`, tap) — Returns to the previous screen.

### Settings & Account — details

#### Screen /settings

**Me Profile Hub** — The Me tab profile screen showing the current user's profile with posts feed; a menu opens a settings drawer linking to all settings entries.

- File: `app/(app)/(tabs)/settings/index.tsx`
- Upstream: [`/conversation`](#screen-conversation)
- Downstream: [`/settings/account`](#screen-settingsaccount), [`/settings/creator-center`](#screen-settingscreator-center), `/settings/credits-center`, [`/settings/affiliate`](#screen-settingsaffiliate), [`/subscription`](#screen-subscription), [`/credit-usage`](#screen-credit-usage), [`/settings/openclaw-management`](#screen-settingsopenclaw-management), [`/settings/connectors`](#screen-settingsconnectors), [`/settings/help`](#screen-settingshelp), [`/settings/system`](#screen-settingssystem)
- CTAs:
  - **Settings Menu** (`menu`, tap) — Opens the settings drawer with all account and settings entries.
    - **Account & Profile** (`nav`, tap) — Navigates to /settings/account to edit profile.
    - **Creator Center** (`nav`, tap) — Navigates to /settings/creator-center.
    - **Credit Center** (`nav`, tap) — Navigates to the credits center overlay.
    - **Incentive Program** (`nav`, tap) — Navigates to /settings/affiliate.
    - **Plan & Billing** (`nav`, tap) — Navigates to the subscription screen.
    - **Usage** (`nav`, tap) — Navigates to the credit usage screen.
    - **OpenClaw Management** (`nav`, tap) — Navigates to /settings/openclaw-management.
    - **App Connector** (`nav`, tap) — Navigates to /settings/connectors.
    - **Help** (`nav`, tap) — Navigates to /settings/help.
    - **All Settings** (`nav`, tap) — Navigates to /settings/system (the full system settings list).
    - **Sign Out / Sign In** (`button`, tap) — Logs out with confirmation when signed in, or opens the reauth modal when signed out.
  - **Share Profile** (`button`, tap) — Opens the share sheet to share the profile link.

#### Screen /settings/account

**Edit Profile** — Edit the user's avatar, public info, handle, details, and view private contact info; save persists handle and profile changes.

- File: `app/(app)/(tabs)/settings/account/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/settings/delete-account`](#screen-settingsdelete-account), [`/subscription`](#screen-subscription)
- CTAs:
  - **Save** (`button`, tap) — Saves all profile and handle edits; disabled while busy, when there are no changes, or on handle errors.
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Edit Profile Picture** (`button`, tap) — Picks and uploads a new avatar image.
  - **Public Info** (`input`, input) — Edits display name, handle, bio and other public profile fields.
  - **Details** (`input`, input) — Edits gender, location, and website.
  - **Delete Account** (`button`, tap) — Navigates to /settings/delete-account; blocked with a warning toast when an active subscription exists.
  - **Cancel Subscription Link** (`link`, tap) — Navigates to /subscription to cancel an active subscription before deleting (shown only when subscribed).
  - **Sign In** (`button`, tap) — Opens the reauth modal when the user is not signed in.

#### Screen /settings/affiliate

**Affiliate Program** — Shows affiliate earnings, the 25% commission rule, per-invitee payouts, and a share-invite block.

- File: `app/(app)/(tabs)/settings/affiliate/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Copy Link** (`button`, tap) — Copies the invite link to the clipboard.
  - **QR Code** (`button`, tap) — Opens a bottom sheet showing the invite QR code.
  - **Copy Code** (`button`, tap) — Copies the invite code to the clipboard.
  - **Email** (`button`, tap) — Opens a bottom sheet to send the invite by email.
  - **Social Share** (`button`, tap) — Shares the invite link via Twitter, Facebook, LinkedIn, or the native share sheet.

#### Screen /settings/connectors

**App Connectors** — Lists third-party app connectors with search, and lets the user connect via OAuth or disconnect them.

- File: `app/(app)/(tabs)/settings/connectors/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Search** (`input`, input) — Filters the connector list by name.
  - **Connect** (`button`, tap) — Creates a connection profile and opens the OAuth authorization URL in the browser, then polls for completion.
  - **Disconnect** (`button`, tap) — Removes the connection profile(s) for the connector.

#### Screen /settings/creator-center

**Creator Center** — Shows creator earnings, a how-it-works guide with create options, a rewards ladder, recent earnings, and an FAQ.

- File: `app/(app)/(tabs)/settings/creator-center/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/conversation`](#screen-conversation), [`/chat`](#screen-chat), [`/discover`](#screen-discover)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Create With Personal AI** (`button`, tap) — Opens a direct conversation with the Personal AI, falling back to the conversation tab.
  - **Create With Agent** (`button`, tap) — Opens the in-app Create Agent dialog.
  - **Remix Your Own** (`button`, tap) — Navigates to the Discover tab.
  - **How Earning Works Info** (`button`, tap) — Opens an info popover explaining how earning works.
  - **FAQ Item** (`button`, tap) — Expands or collapses a frequently-asked-question entry.

#### Screen /settings/delete-account

**Delete Account** — Two-step confirmation to permanently deactivate the account by typing the username/email and the phrase "delete my account".

- File: `app/(app)/(tabs)/settings/delete-account/index.tsx`
- Upstream: [`/settings/account`](#screen-settingsaccount)
- Downstream: [`/subscription`](#screen-subscription)
- CTAs:
  - **Username Or Email** (`input`, input) — Types the account username or email to confirm identity.
  - **Confirmation Phrase** (`input`, input) — Types the exact phrase "delete my account" to confirm intent.
  - **Delete Your Account** (`button`, tap) — Deactivates the account and resets app state; enabled only when both inputs match and no active subscription exists.
  - **Manage Subscription** (`button`, tap) — Navigates to /subscription to cancel an active subscription before deletion (shown only when subscribed).
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /settings/help

**Help And Support** — Lists help resources, opening the Help Center in a webview and offering an email contact option.

- File: `app/(app)/(tabs)/settings/help/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/settings/help/stack-webview`](#screen-settingshelpstack-webview)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Help Center** (`button`, tap) — Opens the Help Center page in the in-app webview.
  - **Contact Us** (`button`, tap) — Shows an alert offering to open the email client to the support address.

#### Screen /settings/help/stack-webview

**Help Webview** — Hosts an in-app webview for help and support URLs passed as route params, with title synced to the header.

- File: `app/(app)/(tabs)/settings/help/stack-webview.tsx`
- Upstream: [`/settings/help`](#screen-settingshelp), [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /settings/invite-friends

**Invite Friends** — Legacy redirect route that replaces itself with the Credits Center invite tab on mount.

- File: `app/(app)/(tabs)/settings/invite-friends/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/credits-center`](#screen-credits-center)
- CTAs: _none_

#### Screen /settings/language

**Language Settings** — Lets the user pick the app system language and chat translation language and toggle auto-translate.

- File: `app/(app)/(tabs)/settings/language/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **System Language** (`select`, tap) — Opens a bottom-sheet picker to choose the app language or follow the system language.
  - **Chat Language** (`select`, tap) — Opens a bottom-sheet picker to choose the chat translation target language.
  - **Auto Translate** (`toggle`, tap) — Toggles automatic chat message translation on or off.

#### Screen /settings/legacy

**Settings** — Top-level settings list with profile header, invite, favorites, billing and support rows, social links, and logout.

- File: `app/(app)/(tabs)/settings/legacy/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/settings/account`](#screen-settingsaccount), [`/settings/openclaw-management`](#screen-settingsopenclaw-management), [`/settings/connectors`](#screen-settingsconnectors), [`/settings/help`](#screen-settingshelp), [`/settings/help/stack-webview`](#screen-settingshelpstack-webview), [`/settings/storage`](#screen-settingsstorage), [`/credits-center`](#screen-credits-center), [`/favorites`](#screen-favorites)
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Profile Row** (`button`, tap) — Opens the account screen when signed in, otherwise opens the reauth modal.
  - **Copy Email** (`button`, tap) — Copies the account email to the clipboard.
  - **Invite Friends** (`button`, tap) — Navigates to the Credits Center invite tab.
  - **My Favorites** (`button`, tap) — Navigates to the favorites screen.
  - **OpenClaw Management** (`button`, tap) — Navigates to the OpenClaw Management screen.
  - **App Connectors** (`button`, tap) — Navigates to the App Connectors screen.
  - **About** (`button`, tap) — Opens the Teamily about page in the in-app webview.
  - **Support** (`button`, tap) — Navigates to the Help and Support screen.
  - **Restore Purchases** (`button`, tap) — Shows an alert to restore previous in-app purchases.
  - **Storage** (`button`, tap) — Navigates to the storage screen.
  - **Log Out / Sign In** (`button`, tap) — Logs out with a confirmation alert when signed in, otherwise opens the reauth flow.
  - **Social Links** (`button`, tap) — Opens the Teamily X, LinkedIn, or Discord page in the browser.

#### Screen /settings/openclaw-management

**OpenClaw Management** — Shows the Teamily API key and a quick-connect script with copy and key-visibility controls.

- File: `app/(app)/(tabs)/settings/openclaw-management/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Back** (`button`, tap) — Returns to the previous screen.
  - **Toggle API Key Visibility** (`toggle`, tap) — Shows or hides the masked API key.
  - **Copy API Key** (`button`, tap) — Copies the API key to the clipboard.
  - **Copy Script** (`button`, tap) — Copies the quick-connect script to the clipboard.

#### Screen /settings/privacy

**Privacy** — Manage phone contacts sync and toggle the visibility of liked and saved posts, then save activity-visibility changes.

- File: `app/(app)/(tabs)/settings/privacy/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Sync Phone Contacts** (`toggle`, tap) — Enables contacts permission and syncs device contacts when on; confirms via dialog and clears saved contacts when turned off.
  - **Allow Full Access** (`button`, tap) — Opens system settings to grant full contacts access when access is limited.
  - **Resync Now** (`button`, tap) — Forces an immediate re-sync of device phone contacts.
  - **Liked Posts** (`toggle`, tap) — Toggles whether liked posts are visible to others (draft, applied on Save).
  - **Saved Posts** (`toggle`, tap) — Toggles whether saved posts are visible to others (draft, applied on Save).
  - **Save** (`button`, tap) — Persists activity-visibility changes; disabled when there are no changes or while busy.
  - **Retry** (`button`, tap) — Refetches activity-visibility settings after a load error.
  - **Sign In** (`button`, tap) — Opens the reauth modal when the user is not signed in.
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /settings/security

**Security** — Shows bound email and phone contact information with entries to change or bind each.

- File: `app/(app)/(tabs)/settings/security/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/settings/security/change-email`](#screen-settingssecuritychange-email), [`/settings/security/change-phone`](#screen-settingssecuritychange-phone)
- CTAs:
  - **Email** (`nav`, tap) — Navigates to /settings/security/change-email to change or bind the email address.
  - **Phone Number** (`nav`, tap) — Navigates to /settings/security/change-phone to change or bind the phone number.
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /settings/security/change-email

**Change Email** — Two-step flow to change the account email: enter a new address, then verify a 6-digit code sent to it.

- File: `app/(app)/(tabs)/settings/security/change-email.tsx`
- Upstream: [`/settings/security`](#screen-settingssecurity)
- Downstream: _none_
- CTAs:
  - **New Email Address** (`input`, input) — Enters the new email address to bind.
  - **Send Code** (`button`, tap) — Sends a verification code to the entered email and advances to the verify step; disabled until the email is valid.
  - **Verification Code** (`input`, input) — Enters the 6-digit OTP; auto-submits and updates the email when complete.
  - **Resend** (`button`, tap) — Resends the verification code after the 60-second cooldown.
  - **Back** (`button`, tap) — Returns to the input step from verify, or to the previous screen from input.

#### Screen /settings/security/change-phone

**Change Phone** — Two-step flow to change the account phone number: enter country code and number, then verify a 6-digit code sent via SMS.

- File: `app/(app)/(tabs)/settings/security/change-phone.tsx`
- Upstream: [`/settings/security`](#screen-settingssecurity)
- Downstream: _none_
- CTAs:
  - **New Phone Number** (`input`, input) — Selects the country dial code and enters the new phone number.
  - **Send Code** (`button`, tap) — Sends a verification code to the entered phone and advances to the verify step; disabled until the number is valid.
  - **Verification Code** (`input`, input) — Enters the 6-digit OTP; auto-submits and updates the phone when complete.
  - **Resend** (`button`, tap) — Resends the verification code after the 60-second cooldown.
  - **Back** (`button`, tap) — Returns to the input step from verify, or to the previous screen from input.

#### Screen /settings/storage

**Storage** — Shows on-device cache sizes for task cards, previews, temp media, and photos with per-item clear actions; unsupported on web.

- File: `app/(app)/(tabs)/settings/storage/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: _none_
- CTAs:
  - **Clear Task Cards Cache** (`button`, tap) — Clears swarm snapshot caches after a confirmation dialog; disabled when zero bytes.
  - **Clear Previews Cache** (`button`, tap) — Clears attachment preview caches after a confirmation dialog; disabled when zero bytes.
  - **Clear Temp Media Cache** (`button`, tap) — Clears save-media prefetch caches after a confirmation dialog; disabled when zero bytes.
  - **Clear Photos Cache** (`button`, tap) — Clears the Expo image cache after a confirmation dialog.
  - **Pull To Refresh** (`button`, swipe) — Reloads the storage cache size summary.
  - **Back** (`button`, tap) — Returns to the previous screen.

#### Screen /settings/system

**System Settings** — Full settings list grouped by account, creator, plan, AI, preferences, and support; includes a usage card, social links, and sign out.

- File: `app/(app)/(tabs)/settings/system/index.tsx`
- Upstream: [`/settings`](#screen-settings)
- Downstream: [`/settings/account`](#screen-settingsaccount), [`/settings/creator-center`](#screen-settingscreator-center), `/settings/credits-center`, [`/settings/affiliate`](#screen-settingsaffiliate), [`/subscription`](#screen-subscription), [`/credit-usage`](#screen-credit-usage), [`/settings/connectors`](#screen-settingsconnectors), [`/settings/openclaw-management`](#screen-settingsopenclaw-management), [`/settings/language`](#screen-settingslanguage), [`/settings/privacy`](#screen-settingsprivacy), [`/settings/security`](#screen-settingssecurity), [`/settings/help`](#screen-settingshelp), [`/settings/help/stack-webview`](#screen-settingshelpstack-webview), [`/conversation`](#screen-conversation)
- CTAs:
  - **Usage Card CTA** (`button`, tap) — Presents the upgrade paywall when on a free plan, or navigates to /subscription to manage a paid plan.
  - **Account & Profile** (`nav`, tap) — Navigates to /settings/account.
  - **Creator Center** (`nav`, tap) — Navigates to /settings/creator-center, showing earned $CASH.
  - **Credit Center** (`nav`, tap) — Navigates to the credits center, showing $CREDITs balance.
  - **Incentive Program** (`nav`, tap) — Navigates to /settings/affiliate, showing earned $CASH.
  - **Plan & Billing** (`nav`, tap) — Navigates to /subscription, showing the current plan name.
  - **Usage** (`nav`, tap) — Navigates to /credit-usage, showing percent remaining.
  - **App Connector** (`nav`, tap) — Navigates to /settings/connectors.
  - **OpenClaw Management** (`nav`, tap) — Navigates to /settings/openclaw-management.
  - **Language** (`nav`, tap) — Navigates to /settings/language, showing the current language.
  - **Privacy Settings** (`nav`, tap) — Navigates to /settings/privacy.
  - **Security** (`nav`, tap) — Navigates to /settings/security.
  - **Help Center** (`nav`, tap) — Navigates to /settings/help.
  - **Terms Of Service** (`nav`, tap) — Opens the Terms of Service in an in-app webview.
  - **Privacy Policy** (`nav`, tap) — Opens the Privacy Policy in an in-app webview.
  - **Refund Policy** (`nav`, tap) — Opens the Refund Policy in an in-app webview.
  - **About** (`nav`, tap) — Opens the About page in an in-app webview, showing the app version.
  - **Community** (`link`, tap) — Navigates to the conversation tab and opens the community group webview.
  - **X** (`link`, tap) — Opens the Teamily AI X profile in an in-app webview.
  - **LinkedIn** (`link`, tap) — Opens the Teamily AI LinkedIn page in an in-app webview.
  - **Discord** (`link`, tap) — Opens the Teamily AI Discord invite in an in-app webview.
  - **Sign Out / Sign In** (`button`, tap) — Logs out with confirmation when signed in, or opens the reauth modal when signed out.
  - **Back** (`button`, tap) — Returns to the previous screen.

## Shared layouts & chrome

`_layout.tsx` files wrap one or more route segments and render the persistent
chrome — stack headers, the tab bar, modals, and providers — shared by the
screens beneath them. Their CTAs are the app-wide navigation controls.

### Layout: Rewards Overlay Layout (`/`)

A root-level Stack (the (rewards) route group, which adds no URL segment) that hosts the Credits Center, Subscription, and Credit Usage overlays. Living outside the Me tab lets these pages overlay any tab and lets back return to the origin tab, leaving the Me tab's own stack untouched. Screens are registered singular to guard against double-push on rapid taps; all slide in from the right with the swipe-back gesture enabled.

- File: `app/(app)/(rewards)/_layout.tsx`
- Wraps: `app/(app)/(rewards)/`
- Downstream: [`/credits-center`](#screen-credits-center), [`/subscription`](#screen-subscription), [`/credit-usage`](#screen-credit-usage)
- CTAs:
  - **Swipe back** (`button`, swipe) — Right-edge swipe gesture pops the overlay back to the tab it was opened from.

### Layout: Tab Bar Layout (`/`)

The bottom tab bar (custom AppTabBar) and its five tabs, each with its own navigation stack — Home (/discover), Explore (/explore), Chats (/conversation), Contacts (/contact), and Me (/settings). A hidden index tab (href null) redirects to Home. The Me tab pops its inner stack to the profile root when it loses focus (popToTopOnBlur).

- File: `app/(app)/(tabs)/_layout.tsx`
- Wraps: `app/(app)/(tabs)/`
- Downstream: [`/discover`](#screen-discover), [`/explore`](#screen-explore), [`/conversation`](#screen-conversation), [`/contact`](#screen-contact), [`/settings`](#screen-settings)
- CTAs:
  - **Home tab** (`button`, tap) — Opens the Home tab — the agent/group discovery feed (/discover).
  - **Explore tab** (`button`, tap) — Opens the Explore tab — the social posts feed (/explore).
  - **Chats tab** (`button`, tap) — Opens the Chats tab — the conversation list (/conversation).
  - **Contacts tab** (`button`, tap) — Opens the Contacts tab — friends, agents, and contact management (/contact).
  - **Me tab** (`button`, tap) — Opens the Me tab — the settings/profile hub (/settings).

### Layout: App Shell Layout (`/`)

The signed-in app shell — a native Stack that hosts the (tabs) tab bar plus every full-screen overlay pushed on top of a tab (chat, profiles, search, invites, posts, agent settings, message inbox, favorites, …) and the (rewards) overlay group. Hydrates the auth token behind a splash, wires reauth (token-empty → in-place reauth modal via ReauthNavProvider rather than a login route), and syncs RevenueCat identity, app badge, location/timezone, phone contacts, social-notification unread count, and cold-start push-notification taps.

- File: `app/(app)/_layout.tsx`
- Wraps: `app/(app)/`
- Downstream: [`/discover`](#screen-discover), [`/explore`](#screen-explore), [`/conversation`](#screen-conversation), [`/contact`](#screen-contact), [`/settings`](#screen-settings), [`/credits-center`](#screen-credits-center), [`/subscription`](#screen-subscription), [`/credit-usage`](#screen-credit-usage), [`/chat`](#screen-chat), [`/add-contact`](#screen-add-contact), [`/discover-vertical`](#screen-discover-vertical), [`/user-profile`](#screen-user-profile), [`/profile/[uid]`](#screen-profileuid), [`/profile-follow-list`](#screen-profile-follow-list), [`/agent-settings/[agentId]`](#screen-agent-settingsagentid), [`/agents/config/[agentId]`](#screen-agentsconfigagentid), [`/search`](#screen-search), [`/discover-search`](#screen-discover-search), [`/report-post/[postId]`](#screen-report-postpostid), [`/search-messages-detail`](#screen-search-messages-detail), [`/search-category`](#screen-search-category), [`/message-inbox`](#screen-message-inbox), [`/invite-friends`](#screen-invite-friends), [`/favorites`](#screen-favorites), [`/post-use-case`](#screen-post-use-case), [`/post-editor/[id]`](#screen-post-editorid), [`/post/[id]`](#screen-postid), [`/invite-group/[groupId]`](#screen-invite-groupgroupid), [`/invite-friend/[imUid]`](#screen-invite-friendimuid), [`/invite/[...slug]`](#screen-inviteslug), [`/apply-invite-code`](#screen-apply-invite-code)
- CTAs:
  - **Stack header back** (`button`, tap/swipe) — Native stack back control (minimal chevron) on pushed overlay screens; the edge-swipe gesture pops the screen back to the originating tab.
  - **Reauth modal** (`dialog`, tap) — Surfaced by ReauthNavProvider when the auth token becomes empty; prompts re-login in place instead of routing to a login screen, preserving the current tab/stack.

### Layout: Root Layout (`/`)

The app's root Stack. Boots i18n, the safe-area / keyboard / gesture / bottom-sheet / portal providers and analytics, paints the splash art until ready, then hosts the top-level route groups — (app) (the signed-in shell, the initial route), the (modal) transparent-modal group, the i/[code] universal-invite landing, and the +not-found fallback. Tracks the device system locale and re-hides the Android splash on foreground.

- File: `app/_layout.tsx`
- Wraps: `app/`
- Downstream: [`/discover`](#screen-discover), [`/i/[code]`](#screen-icode)
- CTAs: _none_

### Layout: About Layout (`/about`)

Stack layout for the about section with hidden headers, hosting the webview screen as a singular route.

- File: `app/(app)/about/_layout.tsx`
- Wraps: `app/(app)/about/`
- Downstream: `/about/webview`
- CTAs: _none_

### Layout: Chat Layout (`/chat`)

Expo Router Stack layout for the chat feature; registers the chat workspace and its sub-screens (search, settings, create, skills, receipts) inside a bottom-sheet provider.

- File: `app/(app)/chat/_layout.tsx`
- Wraps: `app/(app)/chat/`
- Downstream: [`/chat`](#screen-chat), [`/chat/history-search`](#screen-chathistory-search), [`/chat/group-settings`](#screen-chatgroup-settings), [`/chat/user-settings`](#screen-chatuser-settings), [`/chat/create-group`](#screen-chatcreate-group), [`/chat/invite-friends`](#screen-chatinvite-friends), [`/chat/create-agent`](#screen-chatcreate-agent), [`/chat/agent-skills`](#screen-chatagent-skills), [`/chat/read-receipt`](#screen-chatread-receipt), [`/chat/merge-history`](#screen-chatmerge-history), [`/chat/language-settings`](#screen-chatlanguage-settings)
- CTAs: _none_

### Layout: Contacts Layout (`/contact`)

Stack navigator for the Contacts tab; wraps subpages with a shared CommonAppBar back header and slide-from-right animation.

- File: `app/(app)/(tabs)/contact/_layout.tsx`
- Wraps: `app/(app)/(tabs)/contact/`
- Downstream: [`/contact`](#screen-contact), [`/contact/my-agents`](#screen-contactmy-agents), [`/contact/my-friends`](#screen-contactmy-friends), [`/contact/phone-contacts`](#screen-contactphone-contacts), [`/contact/invite-friends`](#screen-contactinvite-friends)
- CTAs:
  - **Back** (`button`, tap) — Header back button (CommonAppBar) that pops the current Contacts subpage; hidden on the index and invite-friends screens.

### Layout: Conversation Layout (`/conversation`)

Expo Router Stack layout for the Chats tab; hosts the single conversation-list index screen with headers hidden.

- File: `app/(app)/(tabs)/conversation/_layout.tsx`
- Wraps: `app/(app)/(tabs)/conversation/`
- Downstream: [`/conversation`](#screen-conversation)
- CTAs: _none_

### Layout: Discover Layout (`/discover`)

Expo Router stack layout for the Discover tab; renders the headerless feed list at index and a custom-header detail route at [id].

- File: `app/(app)/(tabs)/discover/_layout.tsx`
- Wraps: `app/(app)/(tabs)/discover/`
- Downstream: [`/discover`](#screen-discover), [`/discover/[id]`](#screen-discoverid)
- CTAs: _none_

### Layout: Post Layout (`/post`)

Stack navigator for post detail screens; renders a custom detail header and presents the edit screen as a modal sliding up from the bottom.

- File: `app/(app)/post/_layout.tsx`
- Wraps: `app/(app)/post/`
- Downstream: [`/post/[id]`](#screen-postid), [`/post/edit/[id]`](#screen-posteditid)
- CTAs: _none_

### Layout: Settings Layout (`/settings`)

Stack navigator for the Settings section; hosts the profile hub and all settings sub-pages with slide-from-right transitions.

- File: `app/(app)/(tabs)/settings/_layout.tsx`
- Wraps: `app/(app)/(tabs)/settings/`
- Downstream: [`/settings/account`](#screen-settingsaccount), [`/settings/security`](#screen-settingssecurity), [`/settings/privacy`](#screen-settingsprivacy), [`/settings/delete-account`](#screen-settingsdelete-account), [`/settings/storage`](#screen-settingsstorage), [`/settings/system`](#screen-settingssystem), [`/settings/connectors`](#screen-settingsconnectors), [`/settings/language`](#screen-settingslanguage), [`/settings/help`](#screen-settingshelp)
- CTAs: _none_
