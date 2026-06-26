---
name: teamily-ai-app-guide
description: >-
  Usage manual for the Teamily AI web app (teamily.ai) — the page map,
  navigation relationships, CTAs, and feature areas. Use when operating,
  testing, automating, or integrating with the Teamily AI web app, or when
  you need to know which page handles a task and how to reach it.
version: 1.5.0
---

# Teamily AI Web App Guide

Teamily AI is a personal and social AI agent OS: an IM-style workspace where
users chat with friends, groups, and AI agents; discover and remix
community-created content; and manage agents, credits, and subscriptions.

> **Link convention:** every relative path in this guide (e.g. `/chat`,
> `/settings/language`) is relative to the `https://teamily.ai` domain. When
> you are asked for a full/shareable link to a page, you MUST return the
> absolute URL by prefixing the path with `https://teamily.ai` — for example,
> `/settings/language` → `https://teamily.ai/settings/language`.

> **Reference files:** this SKILL.md is the curated overview. The complete
> per-route documentation lives under `references/app/<route>/`, mirroring the
> app's directory layout — `llm.md` for a page, `layout.llm.md` for a layout.
> Each page below links to its reference file; **open it for the full nested
> CTA tree** (SKILL.md lists only top-level controls).

This guide is generated from the per-route `llm.md` (page) and
`layout.llm.md` (shared layout) files in `apps/chat-to/app`. Each page entry
lists:

- **upstream** — pages that navigate into this page
- **downstream** — pages this page navigates to
- **CTAs** — the page's main interactive controls. Each CTA notes its `type` (button, input, tabs, toggle, select, link, nav, menu, dialog), its `trigger` (how it's activated: click, hover, input, …; defaults to click), and may nest child CTAs (shown in the reference file).
- **reference** — the path to the full per-route doc.

Regenerate with `pnpm gen:skill` (or `node generate-skill-md.mjs`) after editing any `llm.md` or `layout.llm.md`.

## How navigation works

- `/` is the landing page and dashboard shell. Its global navigation (header, sidebar, tab bar) reaches: [`/about`](<references/app/(public)/about/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/apply/invite-code`](<references/app/apply/invite-code/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/contact`](<references/app/(dashboard)/contact/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/download`](<references/app/(dashboard)/download/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/settings/channels`](<references/app/(dashboard)/settings/channels/llm.md>), [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/creator-studio`](<references/app/(dashboard)/settings/creator-studio/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/settings/invite-history`](<references/app/(dashboard)/settings/invite-history/llm.md>), [`/settings/knowledge-base`](<references/app/(dashboard)/settings/knowledge-base/llm.md>), [`/settings/language`](<references/app/(dashboard)/settings/language/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/settings/translation`](<references/app/(dashboard)/settings/translation/llm.md>), [`/settings/usage`](<references/app/(dashboard)/settings/usage/llm.md>).
- Signed-out users are redirected to [`/login`](<references/app/(public)/login/llm.md>) by most product pages; after login they land back in the app.
- **Deep-link entry pages** (no in-app upstream; reached via external/shared URLs): [`/credits`](<references/app/(dashboard)/credits/llm.md>), [`/dev/group-message-cases`](<references/app/(dashboard)/dev/group-message-cases/llm.md>), [`/embed/tool-view`](<references/app/embed/tool-view/llm.md>), [`/get-started`](<references/app/(dashboard)/get-started/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/invite/[imUid]`](<references/app/invite/[imUid]/llm.md>), [`/invite/friend/[imUid]`](<references/app/invite/friend/[imUid]/llm.md>), [`/link/[code]`](<references/app/link/[code]/llm.md>), [`/memory`](<references/app/(dashboard)/memory/llm.md>), [`/modal`](<references/app/(dashboard)/modal/llm.md>), [`/playbook`](<references/app/(dashboard)/playbook/llm.md>), [`/region-restricted`](<references/app/region-restricted/llm.md>), [`/settings/credit-usage`](<references/app/(dashboard)/settings/credit-usage/llm.md>), [`/share/[id]`](<references/app/(dashboard)/share/[id]/llm.md>), [`/support`](<references/app/(public)/support/llm.md>), [`/web`](<references/app/(dashboard)/web/llm.md>).
- **Hub pages** (most outbound links): [`/settings`](<references/app/(dashboard)/settings/llm.md>) (18), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>) (16), [`/`](<references/app/(dashboard)/llm.md>) (10), [`/chat`](<references/app/(dashboard)/chat/llm.md>) (7), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>) (6), [`/discover`](<references/app/(dashboard)/discover/llm.md>) (6).

## Feature areas

### Landing & Public Pages

Marketing and informational pages reachable without an account.

| Page | Name | What it does |
| --- | --- | --- |
| [`/`](<references/app/(dashboard)/llm.md>) | Home | The Teamily AI marketing landing/home page (the `tmly-landing` package) — hero with an animated chat demo, founder video, product/architecture/community sections, and a Ghost-backed blog; signed-in visitors are redirected to /chat. |
| [`/about`](<references/app/(public)/about/llm.md>) | About | A long-form editorial about page on Teamily AI's human-AI group-intelligence vision — hero video, use cases (friends/communities/families/co-workers), feature highlights, the three-layer technical architecture, co-founder bios, and the company/team section, closed by the shared site footer. |
| [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>) | Help Center | A locale-aware help center rendering the help-center markdown (billing, subscriptions, credits, account usage) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer. |
| [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>) | Privacy Policy | Renders the privacy-policy markdown (data collection, use, protection, retention, and user privacy rights) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer. |
| [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>) | Refund Policy | Renders the refund-policy markdown (refund terms for subscriptions and services, billing) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer. |
| [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>) | Terms of Service | Renders the terms-of-service markdown (platform rules and guidelines covering subscriptions, billing, credits, and user responsibilities) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer. |
| [`/download`](<references/app/(dashboard)/download/llm.md>) | Download | Landing-style download page rendering the marketing hero (animated demo chat preview) with platform download buttons for iOS, Android, macOS, and Windows plus a Web pill to try Teamily online. |
| [`/presentation`](<references/app/presentation/llm.md>) | Presentation Viewer | Standalone full-screen deck viewer driven by name/sandboxUrl/slide query params; loads slide metadata (with retry/backoff) and renders 16:9 slides in a sandboxed iframe with navigation, keyboard control, export, and a collapsible toolbar (share link disabled on this route). |
| [`/region-restricted`](<references/app/region-restricted/llm.md>) | Region Restricted | Blocking notice (noindex) shown when the service is unavailable in the user's region due to regulatory requirements; displays the Teamily logo, a shield-alert message, and legal links, with a mobile pull-to-refresh that re-checks the 'is-restricted' status. |
| [`/support`](<references/app/(public)/support/llm.md>) | Support | A support hub presenting a responsive grid of cards linking to the refund policy, terms of service, privacy policy, help center, and a mailto contact entry (the Feedback card is commented out in source). |

### Authentication & Onboarding

Sign-in, OAuth callbacks, invite-code redemption, and first-run onboarding. Most product pages redirect here when the user is signed out.

| Page | Name | What it does |
| --- | --- | --- |
| [`/apply/invite-code`](<references/app/apply/invite-code/llm.md>) | Apply Invite Code | Standalone post-signup page to enter and verify an invite/promo code (normalized to uppercase) for a $5 welcome credit, or skip straight to onboarding; prefills from the ?code= param or a pending stored code and tracks rewards analytics events. |
| [`/get-started`](<references/app/(dashboard)/get-started/llm.md>) | Get Started | Server-side redirect-only route that immediately forwards to the credits center onboarding tab; renders no UI of its own. |
| [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>) | Invite Landing | An invite/referral landing page that validates the URL invite code and renders a hero plus an inviter profile card (avatar, stats, top post, reward banner) with a single Connect/Claim-Welcome CTA; logged-out visitors are routed to /login, otherwise the code is verified, the inviter added as an IM friend, and the user sent into /chat. Invalid or expired codes show a fallback state. |
| [`/login`](<references/app/(public)/login/llm.md>) | Login | The authentication page where users sign in or create a Teamily AI account via Google, email (password / one-time code), or phone SMS code through a multi-step panel flow; a legacy username/password web2 variant is shown only on chat-test/localhost with ?v=0. |
| [`/onboarding`](<references/app/onboarding/llm.md>) | Onboarding | Post-signup first-run wizard that floats as a modal (desktop) or full screen (mobile); collects identity/interests/usage answers, provisions starter agents, teams, content, and a knowledge base, then prompts new users for an invite code before handing off to /chat. |

### Chat & Messaging

The core IM workspace: conversations with friends, groups, and AI agents, plus message search and notifications.

| Page | Name | What it does |
| --- | --- | --- |
| [`/chat`](<references/app/(dashboard)/chat/llm.md>) | Chat | The core IM chat workspace — opens conversations from URL params and renders the active conversation (messages, composer, header, side drawers). The home of message sending plus a deep tree of feature entries, dialogs, drawers, and per-message actions. |
| [`/message-inbox`](<references/app/(dashboard)/message-inbox/llm.md>) | Message Inbox | The social notifications inbox — a paginated, infinite-scroll feed of activity (follows, likes, comments, bookmarks, shared posts, leaderboard rewards, and moderation-rejected posts) that auto-marks rows read as they scroll into view and routes each row to its target. |
| [`/modal`](<references/app/(dashboard)/modal/llm.md>) | Modal Route | A no-op route that renders null; it exists so the modal context's router.push has a valid destination (avoiding a 404), while the actual dialog content is rendered by RootLayoutClient based on the open modal set. |
| [`/search`](<references/app/(dashboard)/search/llm.md>) | Global Search | Mobile global-search screen with a sticky header (back/home + query input synced to the q param) and live results across contacts, groups, agents, messages, files, and media; empty query shows recent items, and conversation hits route into /search/conversation while picking a result opens the conversation in /chat. |
| [`/search/conversation`](<references/app/(dashboard)/search/conversation/llm.md>) | Conversation Search | Mobile screen listing search matches within a single conversation (read from id/title/avatar/isGroup/q/category URL params) for the chosen category (messages, files, media, or voice), with infinite-scroll paging and a match count; tapping a hit opens the conversation in /chat scrolled to that message. |
| [`/web`](<references/app/(dashboard)/web/llm.md>) | Visitor Chat | The logged-out / root chat surface — a conversation sidebar listing recommended agents (super agent + normal) over a chat content pane; opens an agent via ?agentId=, and redirects signed-in users at / to /chat. |

### Contacts & Social Graph

Friend management, invitations, and user profiles.

| Page | Name | What it does |
| --- | --- | --- |
| [`/add-contact`](<references/app/(dashboard)/add-contact/llm.md>) | Add Contact | Full-page contact-adding workspace with a back-button header wrapping AddContactContent — share your personal invite QR/link, or look up a person by email to chat, add as friend, or invite them by email. |
| [`/contact`](<references/app/(dashboard)/contact/llm.md>) | Contacts | Contacts landing page — on mobile it renders the alphabetized contact list with a draggable A–Z index jump bar and a user-info dialog; on desktop it defaults to the My Agents list using the shared MyFriends view. |
| [`/contact/my-agents`](<references/app/(dashboard)/contact/my-agents/llm.md>) | My Agents | Lists the user's saved AI agents in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog. |
| [`/contact/my-friends`](<references/app/(dashboard)/contact/my-friends/llm.md>) | My Friends | Lists the user's friends in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog. |
| [`/contact/phone-contacts`](<references/app/(dashboard)/contact/phone-contacts/llm.md>) | Phone Contacts | Browses contacts synced from the user's phone, split into "On Teamily" (registered, openable in chat) and "Invite to Teamily" (unregistered) sections; shows an empty state with app-download links when nothing is synced. |
| [`/invite/[imUid]`](<references/app/invite/[imUid]/llm.md>) | Accept Invitation | Friend-invitation acceptance page keyed by the inviter's IM user ID; shows the inviter and signed-in user as connecting avatars and an Accept button that sends a friend request, then auto-opens the chat — already-friend or self links redirect straight to the conversation, and signed-out visitors are routed to login. |
| [`/invite/friend/[imUid]`](<references/app/invite/friend/[imUid]/llm.md>) | Accept Friend Invitation | Friend-invitation acceptance page keyed by the inviter's IM user ID (same flow as /invite/[imUid], with friend-specific OpenGraph metadata); shows the inviter and signed-in user as connecting avatars and an Accept button that sends a friend request then auto-opens the chat — already-friend or self links redirect straight to the conversation, and signed-out visitors are routed to login. |
| [`/invite/group/[groupId]`](<references/app/invite/group/[groupId]/llm.md>) | Accept Group Invitation | Group-invitation acceptance page keyed by group ID; resolves the group name and shows a Join button that calls joinGroup then auto-opens the group conversation — existing members redirect straight in, invalid/unknown groups redirect home, and signed-out visitors are routed to login. |
| [`/me`](<references/app/(dashboard)/me/llm.md>) | My Profile Redirect | Redirect-only page that sends the signed-in user to their own profile (/profile/{imUid}?source=me, preserving share=1), or to /profile/edit when signed out; renders only a background/loading placeholder while resolving. |
| [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>) | User Profile | A Teamily user's (or agent's) public profile by uid — header (avatar, name, bio, tags, plan/gender badges, social stats), a Posts/Saves/Likes feed with pull-to-refresh and infinite scroll, and (non-agent) a right-rail of the user's agents; emits SEO metadata and Person JSON-LD. Self view exposes owner actions (edit, notifications, contacts, settings menu); other users see Follow/Message; owned-agent profiles expose agent settings and Message. |
| [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>) | Edit Profile | Single-column form for the signed-in user to edit their own Teamily profile — avatar (pick + crop upload), public info (display name, @handle with validation and change-quota, bio, tags), details (gender, location, website), and a read-only private-info block (email). A sticky header carries Back and a Save action that persists the dirty draft and returns. |
| [`/profile/settings/connectors`](<references/app/(dashboard)/profile/settings/connectors/llm.md>) | Connectors Settings | Account-level connectors page — a searchable, single-column list of Composio third-party app toolkits (connected ones sorted first, a hardcoded set of slugs hidden) where each card can Connect (creates a credential profile and opens an OAuth popup) or Disconnect (deletes the toolkit's credential profile(s)). Has a sticky header with a Back button and the page title. |

### AI Agents

Discovering, configuring, and reviewing AI agents.

| Page | Name | What it does |
| --- | --- | --- |
| [`/agent/[agent_name]`](<references/app/(dashboard)/agent/[agent_name]/llm.md>) | Agent Detail | Public agent profile page fetched by name (ISR-cached) showing avatar, creator, score/category/users stats, description, conversation starters, and user reviews; redirects home if the agent is not found, and "Try Agent" subscribes then opens a chat with the agent. |
| [`/agents/config/[agentId]`](<references/app/(dashboard)/agents/config/[agentId]/llm.md>) | Agent Settings | Single-screen editor for one of your agents (loaded by agentId) — edit its avatar, name, and description, save the changes, or delete the agent from a danger zone; a sticky header carries Back and Save. |
| [`/automations`](<references/app/(dashboard)/automations/llm.md>) | Automations | A gallery of automation templates that, once picked, opens an inline task builder where the user composes a structured prompt (intent, schedule, team, scope) and generates it into a prefilled Personal-AI or new-group conversation. |
| [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>) | Discover Legacy | Legacy agent-discovery page — a search bar, category filter tabs, and grids of agent cards; clicking a card opens a rating/subscription drawer on desktop or routes to the detail page on mobile. |
| [`/discover-legacy/[id]`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>) | Discover Legacy Agent Detail | Legacy full-page agent detail (mobile target of a discover card tap) rendering the rating view — agent info, score/category/users, conversation starters, reviews, and a review form. |
| [`/memory`](<references/app/(dashboard)/memory/llm.md>) | Memory | The Memory (Wiki) workspace — a two-pane knowledge base with a left index (search, All/Updates/Tags filters, reserved-view entries, and a grouped page list) beside a main area that switches between the knowledge-graph Overview, an editable wiki page detail (title/summary/tags/markdown body, files, source chats, version history, conflict review, Dream re-organize), the read-only Profile and To-dos memory views, and the agent-generated Artifacts gallery; the `page` URL param selects what the main area shows. |
| [`/playbook`](<references/app/(dashboard)/playbook/llm.md>) | Playbook | Discover-style gallery of agent playbooks rendered as an infinite-scroll masonry grid, with a sticky category filter and per-card Try (open the agent chat preloaded with the playbook prompt) and Replay (watch the recorded run) actions. |
| [`/studio`](<references/app/(dashboard)/studio/llm.md>) | Studio | Standalone collaborative artifact workspace bound to URL params (artifact_ref, artifact_type, mode, conversation, thread, selection, surface) — renders the same studio surface the chat drawer uses (header + mode toolbar + canvas + adapter composer/context slot) with comments, markup, and edit modes, live presence, and webpage version switching; invalid params render a route-error page. |

### Social Discovery & Sharing

The public content feed: posts (showcases), groups, remixing, and shared conversation replays.

| Page | Name | What it does |
| --- | --- | --- |
| [`/discover`](<references/app/(dashboard)/discover/llm.md>) | Discover | The discover home — a sticky-header, tabbed feed shell that surfaces two surfaces driven by URL params: a content feed (Following / Feeds masonry) by default, or an Agents rail (Agents / Agent Teams) when ?tab= or ?section=agents|groups is set, each with search, source sub-tabs, and category filters. |
| [`/discover/groups`](<references/app/(dashboard)/discover/groups/llm.md>) | Explore Groups | A standalone full listing of 25 curated community groups in a responsive card grid, with category-pill filtering and Join cards that open each group's external teamily.ai invite link in a new tab. |
| [`/explore`](<references/app/(dashboard)/explore/llm.md>) | Explore | Full-screen vertical snap-scroll feed of AI-generated showcase posts; each page shows a media preview with author/title/summary and a like/save/comment/share/remix action rail, virtualized with infinite recommendation paging and arrow-key/button navigation, syncing the URL to /explore/[postId] as you scroll. |
| [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>) | Explore Showcase Detail | The Explore snap-scroll feed deep-linked to a specific showcase, seeding that post as the feed entry/active item with per-post SEO metadata from its title and prompt; identical feed UI to /explore and can auto-open the Remix dialog from a pending remix intent. |
| [`/link/[code]`](<references/app/link/[code]/llm.md>) | Share Link Viewer | Public viewer for a shared content code — the server probes the backend /s/{code} target's content type and renders it as a full-screen image, a multi-slide presentation deck, or a sandboxed iframe ("frame"), all under a top bar with copy-link and open-app actions. |
| [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>) | Showcase Post | Full-page detail view of one AI-generated showcase post — renders the deliverable artifact preview alongside title, author, prompt, and a comment thread, with remix, share, like, save, follow, and report actions; emits Article JSON-LD and SEO metadata. |
| [`/share/[id]`](<references/app/(dashboard)/share/[id]/llm.md>) | Shared Thread | Public, read-only replay of an agent conversation identified by thread id — renders the messages, tool calls, and workspace artifacts with floating playback controls; the composer, agent/model selection, history, and new-task actions are all hidden, and an unknown/removed thread toasts "conversation not found" before redirecting home. |

### Billing, Credits & Subscription

Plans, checkout flows, credit rewards, and payment callbacks.

| Page | Name | What it does |
| --- | --- | --- |
| [`/checkout`](<references/app/(dashboard)/checkout/llm.md>) | Checkout | Paddle-powered checkout that reads a priceId from the URL, shows a live order summary (per-item price, billing cycle, subtotal/tax/total) beside an embedded Paddle payment form; on completion fires confetti and redirects to /checkout/success, and redirects signed-out users to /login. |
| [`/checkout/success`](<references/app/(dashboard)/checkout/success/llm.md>) | Checkout Success | Payment-success confirmation page that fires confetti on load, refetches the subscription after a short delay, and offers links to the dashboard or the pricing page. |
| [`/credits`](<references/app/(dashboard)/credits/llm.md>) | Credits | A redirect-only page that immediately forwards to the credits center settings page on its My Credits tab; renders no UI of its own. |
| [`/pricing`](<references/app/(public)/pricing/llm.md>) | Pricing | ISR-rendered plans-and-pricing page — a billing-cycle-toggled 5-tier plan table (Free / Go / Plus / Premium / Pro) with state-aware per-plan CTAs that start a Stripe Checkout session or open the customer portal, an optional reward-credits / Creator-90%-off discount layer, a manage-subscription entry, a tabbed Help Center FAQ, and the shared Teamily footer. |

### Settings & Account

The settings hub and its subpages: profile, language, privacy, connectors, creator earnings, and usage.

| Page | Name | What it does |
| --- | --- | --- |
| [`/settings`](<references/app/(dashboard)/settings/llm.md>) | Settings Home | The settings hub — a usage banner at the top plus grouped, tappable rows that link out to every settings sub-page and legal/support page, ending in social links and a sign-out/sign-in row. |
| [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>) | Affiliate Program | Affiliate program hub — an earnings hero with commission balance plus withdraw entry and withdrawable/pending and invitees/spend chips, a 25% commission explainer with per-user cap, a per-invitee earnings breakdown list, and an invite-sharing toolbar (copy link, QR, email, social). |
| [`/settings/channels`](<references/app/(dashboard)/settings/channels/llm.md>) | Channels | OpenClaw channel management — shows the user's Teamily API key and a one-line quick-connect shell script for linking a self-hosted OpenClaw (2026.3.8+); polls connected deployments every 10s and, when there is a platform-hosted claw and the subscription is not Active, surfaces a VM-suspension warning card. |
| [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>) | Connectors | Account-level connectors directory — a single-column, searchable list of Composio toolkits (third-party apps) the user can Connect (OAuth popup creates a credential profile) or Disconnect (deletes the credential profile); connected apps sort to the top and a hardcoded slug set is hidden. |
| [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>) | Creator Center | Creator earnings hub — an earnings hero with the cash balance plus withdraw entry, a 4-step How-It-Works guide with Start-Creating CTAs, a static engagement rewards ladder (100/1000/10000 engagements → $CASH), recent per-post earnings, and a creator-earnings FAQ accordion. |
| [`/settings/creator-studio`](<references/app/(dashboard)/settings/creator-studio/llm.md>) | Creator Studio | Creator studio page that currently just renders the account-level Connectors settings (Composio toolkit list) as a placeholder until the agents-management module lands. |
| [`/settings/credit-usage`](<references/app/(dashboard)/settings/credit-usage/llm.md>) | Credit Usage | Usage overview page rendering the shared CreditUsageSettings — read-only progress cards for the 5-hour window, weekly cap, and (Plus/Pro only) advanced-model monthly quota, an on-demand pay-as-you-go billing card (eligible Plus/Pro only) with toggle, spend/limit details and suspended/limit-reached banners, plus a token-usage summary card (lifetime/month/week/day). |
| [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>) | Credits Center | Tabbed credits/rewards hub synced to the ?tab= query param (onboarding, invite, leaderboard, credits) — first-week onboarding tasks and login-streak rewards, an invite-friends panel (referral rewards, share link, code redemption, invite history, FAQ), a personal token-usage leaderboard, and a credit balance with activity history. All tabs route the Apply Credits / Buy Plus CTAs to /pricing. |
| [`/settings/help`](<references/app/(dashboard)/settings/help/llm.md>) | Help | Help settings page listing a Help Center link and a Contact Us entry that opens a dialog with the support email; on mobile it shows a sticky header with a back button. |
| [`/settings/invite-history`](<references/app/(dashboard)/settings/invite-history/llm.md>) | Invite History | Server redirect-only route that immediately forwards to /settings/credits-center?tab=invite to show the user's invitation history; renders no UI of its own. |
| [`/settings/knowledge-base`](<references/app/(dashboard)/settings/knowledge-base/llm.md>) | Knowledge Base | Knowledge Base settings page — currently a static placeholder rendering a title, a one-line description, and a "Coming soon" notice; no interactive controls or data yet. |
| [`/settings/language`](<references/app/(dashboard)/settings/language/llm.md>) | Language | Language settings page with two independent knobs — the System (UI) locale and the Chat auto-translation target language — plus an auto-translate master toggle; the two pickers draw from different supported-language sets (see body). |
| [`/settings/privacy`](<references/app/(dashboard)/settings/privacy/llm.md>) | Privacy | Privacy settings page that loads the current profile privacy view-model and lets the owner toggle whether their liked posts and bookmarked/saved posts are publicly visible, then save the changes (saving is enabled only when a toggle differs from the loaded state). |
| [`/settings/security`](<references/app/(dashboard)/settings/security/llm.md>) | Security | Account security settings page; currently a static placeholder showing the security heading, a manage-security subtitle, and a "coming soon" message with no interactive controls. |
| [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>) | Subscription | Subscription settings page stacking three cards — the current-plan summary (plan name, trial/canceled badge, renewal/expiry date, plan actions), a manage-billing card (Stripe customer portal or store-managed deep link, or an upgrade promo for free users), and a quick-links/resources card with social follow icons. |
| [`/settings/translation`](<references/app/(dashboard)/settings/translation/llm.md>) | Translation | Translation settings page that reuses the LanguageSettings component — two independent language pickers (the System/UI locale and the Chat auto-translation target language, drawn from different supported-language sets) plus an auto-translate master toggle. |
| [`/settings/usage`](<references/app/(dashboard)/settings/usage/llm.md>) | Usage | Usage settings page rendering the shared CreditUsageSettings without its title — read-only progress cards for the 5-hour window, weekly cap, and (Plus/Pro only) advanced-model monthly quota, an on-demand pay-as-you-go billing card (eligible Plus/Pro only) with toggle, spend/limit details and suspended/limit-reached banners, plus a token-usage summary card (lifetime/month/week/day). |
| [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>) | Withdraw | Unified cash-out page — total withdrawable balance (creator + affiliate) with a Withdraw All action, source rows linking to the creator and affiliate pages, and a withdrawal-history list; whole page is gated and redirects home via a 'coming soon' dialog when the withdraw-entry flag is off. |

### Developer & Test Pages

Internal playgrounds and embeds; not part of normal user flows.

| Page | Name | What it does |
| --- | --- | --- |
| [`/dev/group-message-cases`](<references/app/(dashboard)/dev/group-message-cases/llm.md>) | Group Message Cases | Developer-only preview page that renders the group-message custom message components against selectable mock fixtures, to verify GroupMessageStartRender, the before-cutoff card, and the streaming-card layouts; no real data or navigation. |
| [`/embed/tool-view`](<references/app/embed/tool-view/llm.md>) | Embed Tool View | Standalone iframe-embeddable renderer that decodes a base64-encoded JSON `data` query param (toolCall + optional toolResult + threadId) and renders the matching read-only ToolView from the tool-view registry; shows a Loading state during Suspense and an error notice when the payload is missing or invalid. |

## Page reference

One entry per page, grouped by feature area. Upstream/downstream paths and the
reference link point to each page's full doc.

### Landing & Public Pages — details

#### Page /

**Home** — The Teamily AI marketing landing/home page (the `tmly-landing` package) — hero with an animated chat demo, founder video, product/architecture/community sections, and a Ghost-backed blog; signed-in visitors are redirected to /chat.

- Upstream: [`/agent/[agent_name]`](<references/app/(dashboard)/agent/[agent_name]/llm.md>), [`/apply/invite-code`](<references/app/apply/invite-code/llm.md>), `/auth/github`, `/callback/auto-login`, `/callback/chat`, `/callback/stripe/cancel`, `/callback/stripe/success`, [`/checkout/success`](<references/app/(dashboard)/checkout/success/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/link/[code]`](<references/app/link/[code]/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>), [`/share/[id]`](<references/app/(dashboard)/share/[id]/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/download`](<references/app/(dashboard)/download/llm.md>)
- Reference: [`references/app/(dashboard)/llm.md`](<references/app/(dashboard)/llm.md>)
- CTAs:
  - **Header nav** (`nav`, click) — Sticky top bar; clicking the logo smooth-scrolls to top, and each entry link fires a landing analytics event via onNavClick. _(+5 nested — see reference)_
  - **Hero download / try-online bar** (`nav`, click) — Row of pills under the hero title (desktop) and in the mobile hero view for getting into the product. _(+5 nested — see reference)_
  - **Hero chat demo** (`nav`, click) — Interactive (non-functional) mock chat that auto-plays agent task sequences; visitors can switch conversations and the device preview. _(+5 nested — see reference)_
  - **Mobile download dialog** (`dialog`, click) — Auto-opens once on phone browsers (suppressed for 30 days after dismissal, and skipped in embedded/native-webview/download-route contexts) prompting to get the mobile app. _(+2 nested — see reference)_
  - **Founder video section** (`nav`, click) — Embedded YouTube product-introduction video (auto-plays/unmutes when scrolled into view) with a follow-up CTA. _(+1 nested — see reference)_
  - **Blog section** (`nav`, click) — Ghost-powered blog grid; hidden entirely if the blog feed errors or has no tags. _(+3 nested — see reference)_
  - **Community social links** (`nav`, click) — Social icon buttons in the Super Community section, each opening in a new tab when configured. _(+3 nested — see reference)_
  - **Footer** (`nav`, click) — Site footer with the logo and grouped link columns (Product / Company / Legal). _(+6 nested — see reference)_

#### Page /about

**About** — A long-form editorial about page on Teamily AI's human-AI group-intelligence vision — hero video, use cases (friends/communities/families/co-workers), feature highlights, the three-layer technical architecture, co-founder bios, and the company/team section, closed by the shared site footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>)
- Reference: [`references/app/(public)/about/llm.md`](<references/app/(public)/about/llm.md>)
- CTAs:
  - **Hero video** (`button`, click) — Embedded YouTube player in the hero (autoplay, muted) introducing Teamily AI; standard play/pause/fullscreen controls.
  - **Use-case demo tweet** (`button`, click) — Embedded X/Twitter post (react-tweet) demonstrating the use cases; play/expand opens the post on X.
  - **Site footer** (`nav`, click) — Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal. _(+6 nested — see reference)_

#### Page /about/help-center

**Help Center** — A locale-aware help center rendering the help-center markdown (billing, subscriptions, credits, account usage) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/help`](<references/app/(dashboard)/settings/help/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/support`](<references/app/(public)/support/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>)
- Reference: [`references/app/(public)/about/help-center/llm.md`](<references/app/(public)/about/help-center/llm.md>)
- CTAs:
  - **Table of contents** (`nav`, click) — Sticky right-side TOC of the article headings (desktop lg+ only); click an entry to smooth-scroll to that section and highlight it as active.
  - **Copy heading link** (`button`, click) — Clicking any H1-H3 heading in the content copies its anchor URL to the clipboard and updates the page hash.
  - **Site footer** (`nav`, click) — Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal. _(+6 nested — see reference)_

#### Page /about/privacy-policy

**Privacy Policy** — Renders the privacy-policy markdown (data collection, use, protection, retention, and user privacy rights) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/region-restricted`](<references/app/region-restricted/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/support`](<references/app/(public)/support/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>)
- Reference: [`references/app/(public)/about/privacy-policy/llm.md`](<references/app/(public)/about/privacy-policy/llm.md>)
- CTAs:
  - **Table of contents** (`nav`, click) — Sticky right-side TOC of the article headings (desktop lg+ only); click an entry to smooth-scroll to that section and highlight it as active.
  - **Copy heading link** (`button`, click) — Clicking any H1-H3 heading in the content copies its anchor URL to the clipboard and updates the page hash.
  - **Site footer** (`nav`, click) — Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal. _(+6 nested — see reference)_

#### Page /about/refund-policy

**Refund Policy** — Renders the refund-policy markdown (refund terms for subscriptions and services, billing) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/support`](<references/app/(public)/support/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>)
- Reference: [`references/app/(public)/about/refund-policy/llm.md`](<references/app/(public)/about/refund-policy/llm.md>)
- CTAs:
  - **Table of contents** (`nav`, click) — Sticky right-side TOC of the article headings (desktop lg+ only); click an entry to smooth-scroll to that section and highlight it as active.
  - **Copy heading link** (`button`, click) — Clicking any H1-H3 heading in the content copies its anchor URL to the clipboard and updates the page hash.
  - **Site footer** (`nav`, click) — Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal. _(+6 nested — see reference)_

#### Page /about/terms-of-service

**Terms of Service** — Renders the terms-of-service markdown (platform rules and guidelines covering subscriptions, billing, credits, and user responsibilities) with a desktop table-of-contents sidebar, copy-link headings, and the shared site footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/region-restricted`](<references/app/region-restricted/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/support`](<references/app/(public)/support/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>)
- Reference: [`references/app/(public)/about/terms-of-service/llm.md`](<references/app/(public)/about/terms-of-service/llm.md>)
- CTAs:
  - **Table of contents** (`nav`, click) — Sticky right-side TOC of the article headings (desktop lg+ only); click an entry to smooth-scroll to that section and highlight it as active.
  - **Copy heading link** (`button`, click) — Clicking any H1-H3 heading in the content copies its anchor URL to the clipboard and updates the page hash.
  - **Site footer** (`nav`, click) — Shared Teamily footer at the bottom (hidden when embedded); links grouped under Product / Company / Legal. _(+6 nested — see reference)_

#### Page /download

**Download** — Landing-style download page rendering the marketing hero (animated demo chat preview) with platform download buttons for iOS, Android, macOS, and Windows plus a Web pill to try Teamily online.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>)
- Downstream: [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/download/llm.md`](<references/app/(dashboard)/download/llm.md>)
- CTAs:
  - **Download links** (`nav`, click) — Row of platform CTAs shown in the hero (desktop title block and mobile view); desktop entries (macOS/Windows) are hidden on phone browsers via user-agent detection. _(+5 nested — see reference)_
  - **Demo chat preview** (`nav`, click) — Animated, non-functional hero showcase that auto-plays scripted agent conversations; interactions only drive the demo, not real chat. _(+3 nested — see reference)_

#### Page /presentation

**Presentation Viewer** — Standalone full-screen deck viewer driven by name/sandboxUrl/slide query params; loads slide metadata (with retry/backoff) and renders 16:9 slides in a sandboxed iframe with navigation, keyboard control, export, and a collapsible toolbar (share link disabled on this route).

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: _none_
- Reference: [`references/app/presentation/llm.md`](<references/app/presentation/llm.md>)
- CTAs:
  - **Toolbar header** (`nav`, click) — Top bar showing logo, deck title, and current 'Slide X of Y'; hidden while the toolbar is collapsed. _(+3 nested — see reference)_
  - **Slide stage** (`nav`, click) — Center area rendering the current slide scaled to fit 16:9 inside a sandboxed iframe; shows Loading / Retrying / unavailable states. _(+1 nested — see reference)_
  - **Slide controls** (`nav`, click) — Bottom control row for moving through the deck. _(+5 nested — see reference)_
  - **Toolbar collapse toggle** (`toggle`, click) — Top-right Maximize2/Minimize2 button that hides or shows the header toolbar for an immersive view; while collapsed an extra X (close full screen) is also offered.

#### Page /region-restricted

**Region Restricted** — Blocking notice (noindex) shown when the service is unavailable in the user's region due to regulatory requirements; displays the Teamily logo, a shield-alert message, and legal links, with a mobile pull-to-refresh that re-checks the 'is-restricted' status.

- Upstream: _none (direct/external entry)_
- Downstream: [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>)
- Reference: [`references/app/region-restricted/llm.md`](<references/app/region-restricted/llm.md>)
- CTAs:
  - **Pull to refresh** (`button`, drag) — Mobile-only pull-down gesture; releasing past the threshold invalidates the 'is-restricted' query to re-check region access (spinner indicator while refreshing).
  - **Terms of Service link** (`link`, click) — Opens /about/terms-of-service.
  - **Privacy Policy link** (`link`, click) — Opens /about/privacy-policy.

#### Page /support

**Support** — A support hub presenting a responsive grid of cards linking to the refund policy, terms of service, privacy policy, help center, and a mailto contact entry (the Feedback card is commented out in source).

- Upstream: _none (direct/external entry)_
- Downstream: [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>)
- Reference: [`references/app/(public)/support/llm.md`](<references/app/(public)/support/llm.md>)
- CTAs:
  - **Refund Policy** (`link`, click) — Card linking to /about/refund-policy.
  - **Terms of Service** (`link`, click) — Card linking to /about/terms-of-service.
  - **Privacy Policy** (`link`, click) — Card linking to /about/privacy-policy.
  - **Help Center** (`link`, click) — Card linking to /about/help-center.
  - **Contact Us** (`link`, click) — Card opening mailto:contact@teamily.ai in a new tab to reach the support team.

### Authentication & Onboarding — details

#### Page /apply/invite-code

**Apply Invite Code** — Standalone post-signup page to enter and verify an invite/promo code (normalized to uppercase) for a $5 welcome credit, or skip straight to onboarding; prefills from the ?code= param or a pending stored code and tracks rewards analytics events.

- Upstream: [`/login`](<references/app/(public)/login/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Downstream: [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/apply/invite-code/llm.md`](<references/app/apply/invite-code/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Round arrow button in the header that calls router.back() to return to the previous page.
  - **Invite or promo code input** (`input`, input/paste) — Monospace uppercase code field, autofocused and prefilled from ?code= or the pending stored code; clears the inline error on change and submits via Apply when Enter is pressed (unless a verify is already pending).
  - **Apply** (`button`, click) — Verifies the normalized code; on success clears the pending code, toasts the $5 welcome credit, and redirects to /settings/credits-center?tab=my-credits (logged in) or / (signed out); on failure shows an inline error. Disabled while pending or when the field is empty.
  - **Skip** (`button`, click) — Skips code entry, clears any pending code, tracks the skip event, and continues to /settings/credits-center?tab=onboarding (logged in) or / (signed out). Disabled while a verify is pending.

#### Page /get-started

**Get Started** — Server-side redirect-only route that immediately forwards to the credits center onboarding tab; renders no UI of its own.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- Reference: [`references/app/(dashboard)/get-started/llm.md`](<references/app/(dashboard)/get-started/llm.md>)
- CTAs: _none_

#### Page /i/[invite_code]

**Invite Landing** — An invite/referral landing page that validates the URL invite code and renders a hero plus an inviter profile card (avatar, stats, top post, reward banner) with a single Connect/Claim-Welcome CTA; logged-out visitors are routed to /login, otherwise the code is verified, the inviter added as an IM friend, and the user sent into /chat. Invalid or expired codes show a fallback state.

- Upstream: _none (direct/external entry)_
- Downstream: [`/login`](<references/app/(public)/login/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/(public)/i/[invite_code]/llm.md`](<references/app/(public)/i/[invite_code]/llm.md>)
- CTAs:
  - **Connect / Claim welcome CTA** (`button`, click) — Primary card button — label is 'Claim welcome' for CHANNEL codes or 'Connect with <name>' for personal invites; routes signed-out users to /login?from=/i/<code>, otherwise verifies the code, adds the inviter as an IM friend, and pushes to /chat?imUid=<inviterId> (or /chat). Disabled and shows 'Connecting…' while pending; recovers to /chat when the code was already used.
  - **Terms & privacy (card)** (`link`, click) — Inline links under the CTA pointing to /about/terms-of-service and /about/privacy-policy.
  - **Footer Terms / Privacy** (`link`, click) — Footer links to /about/terms-of-service and /about/privacy-policy (alongside a copyright label).
  - **Go home (invalid state)** (`link`, click) — Shown only on the invalid/expired-invite fallback screen; links back to /.

#### Page /login

**Login** — The authentication page where users sign in or create a Teamily AI account via Google, email (password / one-time code), or phone SMS code through a multi-step panel flow; a legacy username/password web2 variant is shown only on chat-test/localhost with ?v=0.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/agent/[agent_name]`](<references/app/(dashboard)/agent/[agent_name]/llm.md>), `/auth/github`, `/callback/auto-login`, [`/checkout`](<references/app/(dashboard)/checkout/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>), [`/discover-legacy/[id]`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>), [`/download`](<references/app/(dashboard)/download/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/invite/[imUid]`](<references/app/invite/[imUid]/llm.md>), [`/invite/friend/[imUid]`](<references/app/invite/friend/[imUid]/llm.md>), [`/invite/group/[groupId]`](<references/app/invite/group/[groupId]/llm.md>), [`/playbook`](<references/app/(dashboard)/playbook/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/onboarding`](<references/app/onboarding/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(public)/login/llm.md`](<references/app/(public)/login/llm.md>)
- CTAs:
  - **Continue with Google** (`button`, click) — Google Identity Services button (continue_with, popup mode); on success the credential is exchanged for a session, then redirects to /onboarding (new users), the sanitized from-param, or /.
  - **Auth method tabs** (`tabs`, click) — Email / Phone segmented control above the form on the initial login panel; defaults to Phone. _(+2 nested — see reference)_
  - **Email input** (`input`, input) — Email address field on the login panel's email tab (autofocus, required).
  - **Continue with Email** (`button`, click) — Submits the email; validates format then checks if the account exists — existing users advance to the password panel, new users to the create-password (register) panel.
  - **Phone input row** (`nav`, click) — Country dial-code picker plus phone number field on the login panel's phone tab, with per-country validation. _(+2 nested — see reference)_
  - **Continue with Phone** (`button`, click) — Enabled once the number is complete/valid; sends an SMS verification code and advances to the phone-verify panel.
  - **Password panel** (`nav`, click) — Shown after Continue with Email for an existing account: sign in with the account password (or switch to a one-time code). _(+4 nested — see reference)_
  - **Create-password (register) panel** (`nav`, click) — Shown after Continue with Email for a new account: set a password to create the account. _(+4 nested — see reference)_
  - **Email verify panel** (`nav`, click) — Shown after requesting an email code: enter the 6-digit code sent to the address. _(+4 nested — see reference)_
  - **Phone verify panel** (`nav`, click) — Shown after Continue with Phone: enter the 6-digit SMS code (auto-submits when 6 digits are filled). _(+3 nested — see reference)_
  - **Terms / Privacy links** (`link`, click) — 'By continuing' footer links opening Terms of Service (/about/terms-of-service) and Privacy Policy (/about/privacy-policy) in a new tab.
  - **Legacy web2 login (?v=0)** (`nav`, click) — Alternate form rendered only on chat-test.teamily.ai or localhost:3000 with ?v=0: Google sign-in, a username/password form, a Create An Account toggle to an inline register form, a back arrow (router.back), and terms/privacy links.

#### Page /onboarding

**Onboarding** — Post-signup first-run wizard that floats as a modal (desktop) or full screen (mobile); collects identity/interests/usage answers, provisions starter agents, teams, content, and a knowledge base, then prompts new users for an invite code before handing off to /chat.

- Upstream: [`/login`](<references/app/(public)/login/llm.md>), `/signup`, `/callback/chat`, [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/onboarding/llm.md`](<references/app/onboarding/llm.md>)
- CTAs:
  - **Welcome step** (`nav`, click) — Opening slide with a typewriter title, brand badge, time-estimate hint, and confetti on mount. _(+2 nested — see reference)_
  - **Identity question** (`nav`, click) — Question 1 of the wizard — multi-select chips for 'who you are' (capped at MAX_IDENTITY_SELECTIONS). _(+5 nested — see reference)_
  - **Interests question** (`nav`, click) — Question 2 — multi-select interest chips (capped at MAX_INTEREST_SELECTIONS) plus an Other free-text chip. _(+5 nested — see reference)_
  - **Usage question** (`nav`, click) — Question 3 — multi-select chips for how you'll use the product, plus an Other free-text chip; the final question before provisioning. _(+5 nested — see reference)_
  - **Settlement step** (`nav`, click) — Provisioning summary showing four result rows (agents created, team created, content loaded, knowledge base initialized), each with a live count-up badge and spinner until it resolves; fires confetti when all rows are ready. _(+1 nested — see reference)_
  - **Post-onboarding invite prompt** (`dialog`, click) — Shown to new users after finishing/skipping the wizard, before entering the product; replaces the wizard rather than layering over it. Either confirms a known inviter's credit or asks for a code. _(+2 nested — see reference)_

### Chat & Messaging — details

#### Page /chat

**Chat** — The core IM chat workspace — opens conversations from URL params and renders the active conversation (messages, composer, header, side drawers). The home of message sending plus a deep tree of feature entries, dialogs, drawers, and per-message actions.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), `/callback/chat`, [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>), [`/discover-legacy/[id]`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/i/[invite_code]`](<references/app/(public)/i/[invite_code]/llm.md>), [`/playbook`](<references/app/(dashboard)/playbook/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>), [`/search/conversation`](<references/app/(dashboard)/search/conversation/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/web`](<references/app/(dashboard)/web/llm.md>)
- Downstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/agent/[agent_name]`](<references/app/(dashboard)/agent/[agent_name]/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/add-contact`](<references/app/(dashboard)/add-contact/llm.md>), [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>), [`/search/conversation`](<references/app/(dashboard)/search/conversation/llm.md>)
- Reference: [`references/app/(dashboard)/chat/llm.md`](<references/app/(dashboard)/chat/llm.md>)
- CTAs:
  - **Message composer** (`nav`, click) — Bottom input bar for composing and sending messages; resizable on desktop via a bottom drag handle. _(+11 nested — see reference)_
  - **Conversation header** (`nav`, click) — Top bar of the open conversation: title, avatar, and the row of action entries. _(+5 nested — see reference)_
  - **Conversation info panel** (`dialog`, click) — Side sheet opened from the header (avatar / title / ⋯). Contents vary by conversation type (direct, agent, group). _(+16 nested — see reference)_
  - **Message actions** (`menu`, hover/rightclick/longpress) — Per-message action menu (hover overlay on desktop, long-press sheet on mobile). _(+11 nested — see reference)_
  - **Message reactions** (`button`, click) — Reaction pills shown under a message; tap to open a popover of who reacted. _(+2 nested — see reference)_
  - **Quote jump** (`button`, click) — Tapping a quoted-message preview scrolls to and highlights the original message.
  - **Multi-select action bar** (`nav`, click) — Bottom bar shown while messages are selected. _(+4 nested — see reference)_
  - **Media & file viewers** (`dialog`, click) — Full-screen image/media lightbox opened by tapping an image, video, or media result. _(+6 nested — see reference)_
  - **Side panels & drawers** (`nav`, click) — Right-side drawers and overlays opened from agent/group messages and long content. _(+3 nested — see reference)_
  - **Inline status banners** (`nav`, click) — Contextual notices that appear above the message list or composer. _(+3 nested — see reference)_
  - **Floating jump buttons** (`button`, click) — Circular buttons on the message list's right edge. _(+2 nested — see reference)_

#### Page /message-inbox

**Message Inbox** — The social notifications inbox — a paginated, infinite-scroll feed of activity (follows, likes, comments, bookmarks, shared posts, leaderboard rewards, and moderation-rejected posts) that auto-marks rows read as they scroll into view and routes each row to its target.

- Upstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- Reference: [`references/app/(dashboard)/message-inbox/llm.md`](<references/app/(dashboard)/message-inbox/llm.md>)
- CTAs:
  - **Header bar** (`nav`, click) — Sticky top bar with the localized Notifications title and back/refresh controls. _(+2 nested — see reference)_
  - **Notification row** (`button`, click) — A feed entry that auto-marks itself read once 60% visible; click marks it read and navigates by type (post, leaderboard, moderation-rejected, or sender profile). _(+2 nested — see reference)_
  - **Edit rejected post dialog** (`dialog`, click) — PostUseCaseModal in edit mode opened from a moderation-rejected row; loads the post by id and prefills title/description/prompt/attachments plus the moderation reason for revise-and-resave or delete. _(+2 nested — see reference)_
  - **Try again** (`button`, click) — Shown in the error state; refetches the notifications feed after a load failure.
  - **Load more sentinel** (`nav`, scroll) — Intersection-observed footer that fetches the next page when scrolled into view; shows a spinner while loading.

#### Page /modal

**Modal Route** — A no-op route that renders null; it exists so the modal context's router.push has a valid destination (avoiding a 404), while the actual dialog content is rendered by RootLayoutClient based on the open modal set.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- Reference: [`references/app/(dashboard)/modal/llm.md`](<references/app/(dashboard)/modal/llm.md>)
- CTAs: _none_

#### Page /search

**Global Search** — Mobile global-search screen with a sticky header (back/home + query input synced to the q param) and live results across contacts, groups, agents, messages, files, and media; empty query shows recent items, and conversation hits route into /search/conversation while picking a result opens the conversation in /chat.

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/search/conversation`](<references/app/(dashboard)/search/conversation/llm.md>)
- Reference: [`references/app/(dashboard)/search/llm.md`](<references/app/(dashboard)/search/llm.md>)
- CTAs:
  - **Search header** (`nav`, click) — Sticky top bar holding the back/home control and the query input. _(+3 nested — see reference)_
  - **Category tabs** (`tabs`, click) — Filter pills selecting which result category to show: All, Contacts, Groups, Agents, Messages, Files, Media (All caps each list to a small preview).
  - **Default recents** (`nav`, click) — Shown when the query is empty: recent contacts, groups, chat history, files, and media as tappable rows. _(+2 nested — see reference)_
  - **Result rows** (`nav`, click) — Live query results grouped into Contacts, Groups, Agents, and per-conversation Chat History / Files / Media sections. _(+4 nested — see reference)_

#### Page /search/conversation

**Conversation Search** — Mobile screen listing search matches within a single conversation (read from id/title/avatar/isGroup/q/category URL params) for the chosen category (messages, files, media, or voice), with infinite-scroll paging and a match count; tapping a hit opens the conversation in /chat scrolled to that message.

- Upstream: [`/search`](<references/app/(dashboard)/search/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(dashboard)/search/conversation/llm.md`](<references/app/(dashboard)/search/conversation/llm.md>)
- CTAs:
  - **Conversation header** (`nav`, click) — Top bar showing the back button, conversation avatar/title, and a live match count (or Searching... while loading). _(+1 nested — see reference)_
  - **Match list** (`nav`, click/scroll) — Scrollable list of matching messages for the active category; infinite-scrolls to fetch more pages, and shows Type keywords to search or No messages found when empty. _(+1 nested — see reference)_

#### Page /web

**Visitor Chat** — The logged-out / root chat surface — a conversation sidebar listing recommended agents (super agent + normal) over a chat content pane; opens an agent via ?agentId=, and redirects signed-in users at / to /chat.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>), [`/add-contact`](<references/app/(dashboard)/add-contact/llm.md>)
- Reference: [`references/app/(dashboard)/web/llm.md`](<references/app/(dashboard)/web/llm.md>)
- CTAs:
  - **Conversation sidebar** (`nav`, click) — Left resizable sidebar (collapsed on mobile once a conversation is open) holding search, the new-content menu, and the recommended-agent conversation list. _(+5 nested — see reference)_
  - **Chat content pane** (`nav`, click) — Right-hand chat surface rendered once a conversation is active (?agentId= on mobile, or the super agent by default on desktop); shows the selected agent's messages, composer, header, and drawers (same surface as /chat).

### Contacts & Social Graph — details

#### Page /add-contact

**Add Contact** — Full-page contact-adding workspace with a back-button header wrapping AddContactContent — share your personal invite QR/link, or look up a person by email to chat, add as friend, or invite them by email.

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(dashboard)/add-contact/llm.md`](<references/app/(dashboard)/add-contact/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Ghost chevron button in the header that calls router.back().
  - **Invite QR code** (`nav`, click) — Card showing a QR code encoding your personal friend-invite link (/invite/friend/{imUid}); shows a sign-in-required placeholder when signed out. _(+1 nested — see reference)_
  - **Share your link** (`nav`, click) — Read-only display of your personal friend-invite link. _(+1 nested — see reference)_
  - **Add by email** (`nav`, click) — Email lookup form that checks whether a Teamily account exists for the entered address (debounced 500ms after typing, plus on submit). _(+6 nested — see reference)_

#### Page /contact

**Contacts** — Contacts landing page — on mobile it renders the alphabetized contact list with a draggable A–Z index jump bar and a user-info dialog; on desktop it defaults to the My Agents list using the shared MyFriends view.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/contact/my-agents`](<references/app/(dashboard)/contact/my-agents/llm.md>), [`/contact/my-friends`](<references/app/(dashboard)/contact/my-friends/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/contact/my-agents`](<references/app/(dashboard)/contact/my-agents/llm.md>), [`/contact/my-friends`](<references/app/(dashboard)/contact/my-friends/llm.md>), [`/contact/phone-contacts`](<references/app/(dashboard)/contact/phone-contacts/llm.md>)
- Reference: [`references/app/(dashboard)/contact/llm.md`](<references/app/(dashboard)/contact/llm.md>)
- CTAs:
  - **Contact list item** (`button`, click) — Tapping a contact row opens the user-info dialog for that person (avatar, name, plan badge, creator).
  - **Alphabet index** (`nav`, click/drag/longpress) — Mobile-only A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter.
  - **User info dialog** (`dialog`, click) — Opened from a contact row; shows avatar/name/badge with a primary action. _(+2 nested — see reference)_

#### Page /contact/my-agents

**My Agents** — Lists the user's saved AI agents in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog.

- Upstream: [`/contact`](<references/app/(dashboard)/contact/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/contact`](<references/app/(dashboard)/contact/llm.md>)
- Reference: [`references/app/(dashboard)/contact/my-agents/llm.md`](<references/app/(dashboard)/contact/my-agents/llm.md>)
- CTAs:
  - **Back to contacts** (`button`, click) — Mobile-only back arrow in the header; navigates (replace) to /contact.
  - **Agent list item** (`button`, click) — Tapping an agent row opens the user-info dialog for that agent.
  - **Alphabet index** (`nav`, click/drag/longpress) — A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter.
  - **User info dialog** (`dialog`, click) — Opened from an agent row; shows avatar/name/badge with a primary action. _(+2 nested — see reference)_

#### Page /contact/my-friends

**My Friends** — Lists the user's friends in the shared MyFriends view — an alphabetized, A–Z-indexed contact list whose rows open a user-info dialog.

- Upstream: [`/contact`](<references/app/(dashboard)/contact/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/contact`](<references/app/(dashboard)/contact/llm.md>)
- Reference: [`references/app/(dashboard)/contact/my-friends/llm.md`](<references/app/(dashboard)/contact/my-friends/llm.md>)
- CTAs:
  - **Back to contacts** (`button`, click) — Mobile-only back arrow in the header; navigates (replace) to /contact.
  - **Friend list item** (`button`, click) — Tapping a friend row opens the user-info dialog for that friend.
  - **Alphabet index** (`nav`, click/drag/longpress) — A–Z jump bar on the right edge; tap or slide a letter to scroll the list to that group, highlighting the current letter.
  - **User info dialog** (`dialog`, click) — Opened from a friend row; shows avatar/name/badge with a primary action. _(+2 nested — see reference)_

#### Page /contact/phone-contacts

**Phone Contacts** — Browses contacts synced from the user's phone, split into "On Teamily" (registered, openable in chat) and "Invite to Teamily" (unregistered) sections; shows an empty state with app-download links when nothing is synced.

- Upstream: [`/contact`](<references/app/(dashboard)/contact/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(dashboard)/contact/phone-contacts/llm.md`](<references/app/(dashboard)/contact/phone-contacts/llm.md>)
- CTAs:
  - **Back to contacts** (`button`, click) — Mobile-only back arrow in the header; navigates (replace) to /contact.
  - **Registered contact row** (`button`, click) — On an On-Teamily contact; opens (or creates) the IM conversation with them and navigates to /chat.
  - **Contact avatar** (`button`, click) — On a registered contact; opens the user-info dialog instead of jumping to chat.
  - **Invite button** (`button`, click) — On an unregistered contact; shares via Web Share, falls back to an SMS draft on mobile, else copies a personalized invite link to join Teamily; shows a spinner while pending.
  - **Match-unavailable retry** (`button`, click) — Inline banner shown when Teamily matches can't be resolved; retries the contacts lookup.
  - **Error retry** (`button`, click) — Shown when the contacts list fails to load; retries the fetch.
  - **Download app links** (`link`, click) — Empty-state iOS / Android buttons opening the app-store download links in a new tab (contacts sync requires the mobile app).

#### Page /invite/[imUid]

**Accept Invitation** — Friend-invitation acceptance page keyed by the inviter's IM user ID; shows the inviter and signed-in user as connecting avatars and an Accept button that sends a friend request, then auto-opens the chat — already-friend or self links redirect straight to the conversation, and signed-out visitors are routed to login.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/invite/[imUid]/llm.md`](<references/app/invite/[imUid]/llm.md>)
- CTAs:
  - **Accept Invitation button** (`button`, click) — Primary card button — sends the friend request (inviteFriend) for the inviter's IM uid then auto-opens the chat after success; if signed out it redirects to /login, blocks a self-link, and toasts on invalid/lookup errors.
  - **Terms of Service link** (`link`, click) — Fine-print link under the button opening /about/terms-of-service.
  - **Privacy Policy link** (`link`, click) — Fine-print link under the button opening /about/privacy-policy.
  - **Header** (`nav`, click) — Sticky top bar with the Teamily.ai brand and account controls. _(+4 nested — see reference)_

#### Page /invite/friend/[imUid]

**Accept Friend Invitation** — Friend-invitation acceptance page keyed by the inviter's IM user ID (same flow as /invite/[imUid], with friend-specific OpenGraph metadata); shows the inviter and signed-in user as connecting avatars and an Accept button that sends a friend request then auto-opens the chat — already-friend or self links redirect straight to the conversation, and signed-out visitors are routed to login.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/invite/friend/[imUid]/llm.md`](<references/app/invite/friend/[imUid]/llm.md>)
- CTAs:
  - **Accept Invitation button** (`button`, click) — Primary card button — sends the friend request (inviteFriend) for the inviter's IM uid then auto-opens the chat after success; if signed out it redirects to /login, blocks a self-link, and toasts on invalid/lookup errors.
  - **Terms of Service link** (`link`, click) — Fine-print link under the button opening /about/terms-of-service.
  - **Privacy Policy link** (`link`, click) — Fine-print link under the button opening /about/privacy-policy.
  - **Header** (`nav`, click) — Sticky top bar with the Teamily.ai brand and account controls. _(+4 nested — see reference)_

#### Page /invite/group/[groupId]

**Accept Group Invitation** — Group-invitation acceptance page keyed by group ID; resolves the group name and shows a Join button that calls joinGroup then auto-opens the group conversation — existing members redirect straight in, invalid/unknown groups redirect home, and signed-out visitors are routed to login.

- Upstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/discover/groups`](<references/app/(dashboard)/discover/groups/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/invite/group/[groupId]/llm.md`](<references/app/invite/group/[groupId]/llm.md>)
- CTAs:
  - **Join Group button** (`button`, click) — Primary card button — joins the group (joinGroup) by its ID then auto-opens the group conversation after success; if signed out it redirects to /login and toasts on invalid/join errors.
  - **Terms of Service link** (`link`, click) — Fine-print link under the button opening /about/terms-of-service.
  - **Privacy Policy link** (`link`, click) — Fine-print link under the button opening /about/privacy-policy.
  - **Header** (`nav`, click) — Sticky top bar with the Teamily.ai brand and account controls. _(+4 nested — see reference)_

#### Page /me

**My Profile Redirect** — Redirect-only page that sends the signed-in user to their own profile (/profile/{imUid}?source=me, preserving share=1), or to /profile/edit when signed out; renders only a background/loading placeholder while resolving.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>)
- Downstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>)
- Reference: [`references/app/(dashboard)/me/llm.md`](<references/app/(dashboard)/me/llm.md>)
- CTAs: _none_

#### Page /profile/[uid]

**User Profile** — A Teamily user's (or agent's) public profile by uid — header (avatar, name, bio, tags, plan/gender badges, social stats), a Posts/Saves/Likes feed with pull-to-refresh and infinite scroll, and (non-agent) a right-rail of the user's agents; emits SEO metadata and Person JSON-LD. Self view exposes owner actions (edit, notifications, contacts, settings menu); other users see Follow/Message; owned-agent profiles expose agent settings and Message.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/agents/config/[agentId]`](<references/app/(dashboard)/agents/config/[agentId]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/message-inbox`](<references/app/(dashboard)/message-inbox/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>)
- Downstream: [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>), [`/agents/config/[agentId]`](<references/app/(dashboard)/agents/config/[agentId]/llm.md>), [`/message-inbox`](<references/app/(dashboard)/message-inbox/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/settings/usage`](<references/app/(dashboard)/settings/usage/llm.md>), [`/settings/channels`](<references/app/(dashboard)/settings/channels/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/download`](<references/app/(dashboard)/download/llm.md>)
- Reference: [`references/app/(dashboard)/profile/[uid]/llm.md`](<references/app/(dashboard)/profile/[uid]/llm.md>)
- CTAs:
  - **Profile header** (`nav`, click) — Top section: avatar (AI badge on agent profiles), name with plan/gender badges, @handle, bio, tags, social stats, and the context-dependent action row. _(+8 nested — see reference)_
  - **Social stats** (`button`, click) — Following / Followers / Likes & Saves counts (formatted K/M/B/T). _(+1 nested — see reference)_
  - **Back** (`button`, click) — Returns to the previous page; shown on desktop (except self view entered via ?source=me) and on mobile when viewing another user.
  - **Feed tabs** (`tabs`, click) — Switches the feed between Posts / Saves / Likes; private/agent tabs show a lock icon and a private/only-visible-to-you placeholder. _(+1 nested — see reference)_
  - **Feed grid** (`nav`, click/scroll/drag) — Showcase/post card grid; cards open their detail. Infinite-scrolls more items near the bottom; pull down from the top to refresh. _(+1 nested — see reference)_
  - **Agents rail** (`nav`, click) — Desktop right rail (non-agent profiles) listing the user's agents. _(+2 nested — see reference)_

#### Page /profile/edit

**Edit Profile** — Single-column form for the signed-in user to edit their own Teamily profile — avatar (pick + crop upload), public info (display name, @handle with validation and change-quota, bio, tags), details (gender, location, website), and a read-only private-info block (email). A sticky header carries Back and a Save action that persists the dirty draft and returns.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/profile/edit/llm.md`](<references/app/(dashboard)/profile/edit/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Sticky-header arrow that returns to the previous page without saving.
  - **Save** (`button`, click) — Saves all edited fields, toasts success, and navigates back; disabled until the draft is dirty (and while saving, uploading, or when a handle change is quota-blocked).
  - **Avatar / Change photo** (`button`, click) — Camera button or Change photo link opens the OS image picker; non-GIFs go through the crop dialog, then upload and update the avatar. _(+1 nested — see reference)_
  - **Name** (`input`, input) — Display-name field with a character counter against the max length.
  - **Username (@handle)** (`input`, input) — Edits the @handle (normalized on input) with local validation errors and a change-quota label; disabled once the quota is exhausted for an existing handle.
  - **Bio** (`input`, input) — Multi-line bio textarea with a character counter.
  - **Tags** (`input`, input/click) — Adds a tag on Enter, comma, or the plus button (deduped, capped by tag count/length); each tag chip has an X to remove it.
  - **Gender** (`select`, click) — Popover selector for Not set / Male / Female / Other.
  - **Location** (`input`, input) — Free-text location field.
  - **Website** (`input`, input) — Free-text website field.

#### Page /profile/settings/connectors

**Connectors Settings** — Account-level connectors page — a searchable, single-column list of Composio third-party app toolkits (connected ones sorted first, a hardcoded set of slugs hidden) where each card can Connect (creates a credential profile and opens an OAuth popup) or Disconnect (deletes the toolkit's credential profile(s)). Has a sticky header with a Back button and the page title.

- Upstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/profile/settings/connectors/llm.md`](<references/app/(dashboard)/profile/settings/connectors/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Sticky-header arrow that returns to the previous page.
  - **Search connectors** (`input`, input) — Filters the Composio toolkit list by keyword.
  - **Connect** (`button`, click) — Opens a blank OAuth popup then creates a credential profile for the app and redirects the popup to authorize; refreshes profiles on success, closes the popup on error.
  - **Disconnect** (`button`, click) — Connected apps only — deletes all of the toolkit's credential profile(s) (single or bulk) and refreshes the list.

### AI Agents — details

#### Page /agent/[agent_name]

**Agent Detail** — Public agent profile page fetched by name (ISR-cached) showing avatar, creator, score/category/users stats, description, conversation starters, and user reviews; redirects home if the agent is not found, and "Try Agent" subscribes then opens a chat with the agent.

- Upstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/agent/[agent_name]/llm.md`](<references/app/(dashboard)/agent/[agent_name]/llm.md>)
- CTAs:
  - **Try Agent button** (`button`, click) — Sticky bottom button (disabled until the agent loads); signed in it subscribes to the agent and opens its chat (→ /chat), signed out it redirects to /login?from=/callback/chat with the agent encoded for post-login open.
  - **Conversation starters** (`button`, click) — Suggested prompt chips (shown when present); tapping one runs Try Agent seeded with that prompt — opens the agent chat signed in, else redirects to /login.
  - **Rate / comment toggle** (`button`, click) — Pencil-icon button (or the empty 'No comments yet' card) that switches the page into the rate-and-comment view; redirects to /login?from=/discover when signed out.
  - **Back to detail** (`button`, click) — Floating ArrowLeft button shown in the rate-and-comment view; returns to the agent detail view.
  - **Rate stars** (`button`, click/hover) — 1-5 tap-to-rate star control in the rate-and-comment view, with a per-star fill animation on selection.
  - **Comment textarea** (`input`, input) — Free-text field to write the review comment (placeholder 'Please share your thoughts here.').
  - **Submit comment button** (`button`, click) — Sticky bottom Submit button (disabled while empty or pending) that posts the score + comment to the agent review API, then returns to the detail view.

#### Page /agents/config/[agentId]

**Agent Settings** — Single-screen editor for one of your agents (loaded by agentId) — edit its avatar, name, and description, save the changes, or delete the agent from a danger zone; a sticky header carries Back and Save.

- Upstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>)
- Reference: [`references/app/(dashboard)/agents/config/[agentId]/llm.md`](<references/app/(dashboard)/agents/config/[agentId]/llm.md>)
- CTAs:
  - **Header bar** (`nav`, click) — Sticky top bar with the page title, a Back control, and the Save action. _(+2 nested — see reference)_
  - **Avatar editor** (`nav`, click) — Top avatar block showing the current agent icon with edit affordances. _(+3 nested — see reference)_
  - **Nickname input** (`input`, input) — Text field editing the agent's display name; required (Save errors if blank).
  - **Description input** (`input`, input) — Textarea editing the agent's description.
  - **Delete agent** (`button`, click) — Danger-zone button that opens a confirmation dialog; on confirm, permanently deletes the agent. _(+1 nested — see reference)_

#### Page /automations

**Automations** — A gallery of automation templates that, once picked, opens an inline task builder where the user composes a structured prompt (intent, schedule, team, scope) and generates it into a prefilled Personal-AI or new-group conversation.

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/automations/llm.md`](<references/app/(dashboard)/automations/llm.md>)
- CTAs:
  - **Template search** (`input`, input) — Rounded search box in the sticky header that filters the template grid by title/description (case-insensitive); always visible, even while the builder is open.
  - **Category pills** (`tabs`, click) — Horizontal config-driven category filter under the header; selecting a pill shows only that category's templates. Hidden while a template's builder is open.
  - **Template card** (`button`, click) — Grid card (emoji + title + 2-line description) that opens the inline task builder seeded with the template's preset intent/schedule/scope/team/topic.
  - **Task builder** (`nav`, click) — Inline panel replacing the grid after a template is picked; edits chips to live-rewrite a compiled prompt, then generates it into a conversation. _(+7 nested — see reference)_

#### Page /discover-legacy

**Discover Legacy** — Legacy agent-discovery page — a search bar, category filter tabs, and grids of agent cards; clicking a card opens a rating/subscription drawer on desktop or routes to the detail page on mobile.

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: `/discover/[id]`, [`/chat`](<references/app/(dashboard)/chat/llm.md>), `/callback/chat`, [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/discover-legacy/llm.md`](<references/app/(dashboard)/discover-legacy/llm.md>)
- CTAs:
  - **Search bar** (`nav`, click) — Top search field that debounces (300ms) and queries the agent discover API by name, showing a results dropdown. _(+3 nested — see reference)_
  - **Category tabs** (`tabs`, click) — Filter row synced to the ?category query param: All, Latest, backend categories, and My Agents (login only). _(+4 nested — see reference)_
  - **Agent card** (`nav`, click) — Card in the result grid; clicking it opens the rating drawer (desktop) or pushes to /discover/[id] (mobile). _(+4 nested — see reference)_
  - **Agent rating drawer** (`dialog`, click) — Desktop right-side sheet opened from a card; shows agent info, score/category/users, conversation starters, and reviews. _(+8 nested — see reference)_

#### Page /discover-legacy/[id]

**Discover Legacy Agent Detail** — Legacy full-page agent detail (mobile target of a discover card tap) rendering the rating view — agent info, score/category/users, conversation starters, reviews, and a review form.

- Upstream: [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>)
- Downstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), `/callback/chat`, [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/discover-legacy/[id]/llm.md`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Back arrow that routes to /discover on mobile.
  - **Copy Link** (`button`, click) — Copies the agent's share URL (/agent/<name>) to the clipboard.
  - **Try Agent** (`button`, click) — Subscribes then opens a chat with the agent (-> /chat); signed-out users are sent to /login?from=/callback/chat.
  - **Conversation starter chip** (`button`, click) — Prefilled prompt that launches a chat with the agent using that prompt; signed-out users are sent to /login?from=/callback/chat.
  - **Open rating form** (`button`, click) — Edit/comment button that reveals the star + comment form; signed-out users are sent to /login?from=/discover.
  - **Star rating** (`button`, click) — Tap a 1-5 star to set the rating (animated).
  - **Comment field** (`input`, input) — Textarea for the review text.
  - **Submit review** (`button`, click) — Posts a new comment or updates an existing one (disabled until a rating and comment exist), then refreshes the view.

#### Page /memory

**Memory** — The Memory (Wiki) workspace — a two-pane knowledge base with a left index (search, All/Updates/Tags filters, reserved-view entries, and a grouped page list) beside a main area that switches between the knowledge-graph Overview, an editable wiki page detail (title/summary/tags/markdown body, files, source chats, version history, conflict review, Dream re-organize), the read-only Profile and To-dos memory views, and the agent-generated Artifacts gallery; the `page` URL param selects what the main area shows.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(dashboard)/memory/llm.md`](<references/app/(dashboard)/memory/llm.md>)
- CTAs:
  - **Index panel** (`nav`, click) — Fixed left sidebar (360px): search box, filter row + tag cloud, reserved-view entries, and the grouped page list. _(+11 nested — see reference)_
  - **Overview map** (`nav`, click/hover) — Default main view: a force-directed knowledge graph of pages (nodes sized by ref_count, colored by category, conflict nodes dashed) with degraded/truncated notices. _(+2 nested — see reference)_
  - **Page detail** (`nav`, click) — Main view for a selected wiki page: editable header, tags, optional conflict card, markdown body, files, and source chats; the whole panel is an image drop zone when editing. _(+15 nested — see reference)_
  - **Profile view** (`nav`, click) — Read-only 'My profile' memory view: markdown body with a refresh (Dream) button and a share button; renders backend-localized placeholder when empty. _(+3 nested — see reference)_
  - **To-dos view** (`nav`, click) — Read-only To-dos memory view (same shell as Profile, with a freshness/updated-at label): markdown body plus refresh and share. _(+3 nested — see reference)_
  - **Artifacts gallery** (`nav`, click) — Agent-generated artifacts (lazy-loaded): search, scope segmented control, group picker, type filters, and an infinite grid of artifact cards. _(+6 nested — see reference)_
  - **Maintenance banner** (`nav`, click) — Full-view fallback shown when a wiki/memory request returns 503 (kill switch).

#### Page /playbook

**Playbook** — Discover-style gallery of agent playbooks rendered as an infinite-scroll masonry grid, with a sticky category filter and per-card Try (open the agent chat preloaded with the playbook prompt) and Replay (watch the recorded run) actions.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/playbook/llm.md`](<references/app/(dashboard)/playbook/llm.md>)
- CTAs:
  - **Category filter** (`tabs`, click) — Sticky pill row (All + fetched categories, each with icon) that filters the playbook masonry grid by category; hidden when showCategory is false (e.g. embedded).
  - **Playbook card** (`nav`, hover/click) — Masonry card showing the cover image, category badge, agent name, optional New badge, and title; hovering (desktop) or tapping reveals the Try / Replay action overlay. _(+2 nested — see reference)_
  - **Load more** (`nav`, scroll) — Sentinel at the grid's bottom that auto-fetches the next page (12 per page) via IntersectionObserver when scrolled into view.

#### Page /studio

**Studio** — Standalone collaborative artifact workspace bound to URL params (artifact_ref, artifact_type, mode, conversation, thread, selection, surface) — renders the same studio surface the chat drawer uses (header + mode toolbar + canvas + adapter composer/context slot) with comments, markup, and edit modes, live presence, and webpage version switching; invalid params render a route-error page.

- Upstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Reference: [`references/app/(dashboard)/studio/llm.md`](<references/app/(dashboard)/studio/llm.md>)
- CTAs:
  - **Studio header** (`nav`, click) — Top bar: artifact type icon, artifact title, live-viewer avatars, version pill, share, and (on the standalone page) a left close button. _(+4 nested — see reference)_
  - **Mode toolbar** (`nav`, click) — Toolbar under the header; mode buttons appear only for capabilities the artifact adapter declares (disabled/coming-soon types collapse it entirely). _(+7 nested — see reference)_
  - **Expand header** (`button`, click) — Floating chevron shown when the chrome is collapsed; restores the header and mode toolbar.
  - **Artifact canvas** (`nav`, click/scroll/drag) — Adapter-rendered main view (html/webpage, slides, markdown, sheet, image, design, url, tree); interactions vary by adapter and active mode — comment pins, markup brush strokes, inline editing, slide navigation, zoom-pan.
  - **Adapter composer** (`input`, click/input) — Optional bottom composer rendered by the artifact adapter (e.g. add-comment / send-to-agent input); send-to-agent and mentions target the conversation named in the URL and degrade gracefully when it is absent or unresolvable.
  - **Context slot** (`nav`, click) — Optional right-side panel rendered by the adapter (e.g. comments list / inspector) on wider layouts; on mobile the mode panel becomes a collapsible bottom sheet instead of a side split.
  - **Route error** (`link`, click) — When artifact_ref/artifact_type/mode are missing or invalid the page shows an error with title/detail and a 'Back to chat' link to /chat.

### Social Discovery & Sharing — details

#### Page /discover

**Discover** — The discover home — a sticky-header, tabbed feed shell that surfaces two surfaces driven by URL params: a content feed (Following / Feeds masonry) by default, or an Agents rail (Agents / Agent Teams) when ?tab= or ?section=agents|groups is set, each with search, source sub-tabs, and category filters.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>), [`/discover-legacy/[id]`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>), [`/discover/groups`](<references/app/(dashboard)/discover/groups/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/discover/groups`](<references/app/(dashboard)/discover/groups/llm.md>)
- Reference: [`references/app/(dashboard)/discover/llm.md`](<references/app/(dashboard)/discover/llm.md>)
- CTAs:
  - **Tabs** (`tabs`, click) — Top tab strip; the visible set depends on the surface — Following | Feeds on the default content surface, Agents | Agent Teams on the agents surface (entered via ?tab= or ?section=agents|groups). Switching off the agents rail resets to the Feeds default. _(+4 nested — see reference)_
  - **Search** (`input`, input) — Rounded search box (top-left on desktop, above pills on mobile) with a per-tab placeholder; filters feed posts, agent templates (server-side, debounced 300ms), or agent teams (local filter on name/scene/description/tags).
  - **Create Own Agent** (`button`, click) — Plus button beside search on the Agents tab; opens the create-artifacts modal on the agents tab (in-page dialog).
  - **Create Own Agent Team** (`button`, click) — Plus button beside search on the Agent Teams tab; opens the New Group creation modal (in-page dialog).
  - **Source sub-tabs** (`tabs`, click) — On Agents / Agent Teams surfaces — toggle between By Teamily (official library) and Created by Me (the signed-in user's own templates/teams); category pills are hidden under Created by Me.
  - **Category pills** (`select`, click) — Horizontal pill filter. On Following/Feeds it filters feed posts (re-tapping the active pill refreshes, with a spinner). On the Agents official tab it filters templates by team category; on the Agent Teams official tab it filters by team category.
  - **Feed post card** (`button`, click) — Masonry card on Following/Feeds; opens the post detail and carries the feed's like/comment/share/remix/bookmark actions.
  - **Chat with agent** (`button`, click) — Chat button on each agent row card (Agents tab); when signed out redirects to /login, otherwise creates an agent from the template and opens its conversation in /chat (shows an inline spinner while creating).
  - **Agent team members popover** (`menu`, click) — Member-count badge on an agent-team cover (Agent Teams tab) opening a popover that lists each member's avatar, name, role, and description.
  - **Create agent team** (`button`, click) — Create button on an agent-team card; spins up a group chat from the curated team (shows a spinner on that card while creating).
  - **Load more** (`nav`, scroll) — Infinite-scroll sentinels auto-fetch the next page near the viewport edge for the feed masonry, the Agents template list, and the Created by Me agent-teams list.
  - **Onboarding rewards banner** (`button`, click) — Dismissible first-week-tasks banner shown above the feed (content surface only) with a progress bar; clicking it navigates to /settings/credits-center?tab=onboarding, and the X stores a per-account dismissal.

#### Page /discover/groups

**Explore Groups** — A standalone full listing of 25 curated community groups in a responsive card grid, with category-pill filtering and Join cards that open each group's external teamily.ai invite link in a new tab.

- Upstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>)
- Downstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>)
- Reference: [`references/app/(dashboard)/discover/groups/llm.md`](<references/app/(dashboard)/discover/groups/llm.md>)
- CTAs:
  - **Back to Discover** (`link`, click) — Chevron-left button in the sticky header that navigates back to /discover.
  - **Category pills** (`select`, click) — Filters the group grid by derived category: All / Daily / Share / Explore / Find / Community / Investment / Events / Other (category inferred from each group's name).
  - **Join group card** (`link`, click) — Each group card (cover image, name, Join badge, description) is an anchor that opens the group's external https://teamily.ai/invite/group/<id> invite URL in a new tab.

#### Page /explore

**Explore** — Full-screen vertical snap-scroll feed of AI-generated showcase posts; each page shows a media preview with author/title/summary and a like/save/comment/share/remix action rail, virtualized with infinite recommendation paging and arrow-key/button navigation, syncing the URL to /explore/[postId] as you scroll.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/explore/llm.md`](<references/app/(dashboard)/explore/llm.md>)
- CTAs:
  - **Post navigation** (`nav`, click/scroll) — Moves between posts in the vertical snap feed; the active post's id is written into the URL (/explore/[postId]) and recommendations prefetch as you near the end. _(+4 nested — see reference)_
  - **Author** (`nav`, click) — Author identity block above the post (desktop) or in the header / details sheet (mobile). _(+3 nested — see reference)_
  - **Title & summary panel** (`button`, click) — Desktop title/summary block that expands/collapses the clamped description on tap; mobile opens the details sheet instead.
  - **Action rail** (`nav`, click) — Vertical action column (desktop, right of preview) or horizontal action row (mobile) of post engagement controls. _(+5 nested — see reference)_
  - **Post details sheet (mobile)** (`dialog`, click) — Bottom sheet opened via the header ⋯ / title / more on mobile; shows the full author block (with follow), title, and summary; X or backdrop closes it.

#### Page /explore/[postId]

**Explore Showcase Detail** — The Explore snap-scroll feed deep-linked to a specific showcase, seeding that post as the feed entry/active item with per-post SEO metadata from its title and prompt; identical feed UI to /explore and can auto-open the Remix dialog from a pending remix intent.

- Upstream: [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>)
- Downstream: [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/post/[showcaseId]`](<references/app/(dashboard)/post/[showcaseId]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/explore/[postId]/llm.md`](<references/app/(dashboard)/explore/[postId]/llm.md>)
- CTAs:
  - **Post navigation** (`nav`, click/scroll) — Moves between posts in the vertical snap feed starting from this post; the active post's id is written into the URL (/explore/[postId]) and recommendations prefetch as you near the end. _(+4 nested — see reference)_
  - **Author** (`nav`, click) — Author identity block above the post (desktop) or in the header / details sheet (mobile). _(+3 nested — see reference)_
  - **Title & summary panel** (`button`, click) — Desktop title/summary block that expands/collapses the clamped description on tap; mobile opens the details sheet instead.
  - **Action rail** (`nav`, click) — Vertical action column (desktop, right of preview) or horizontal action row (mobile) of post engagement controls. _(+5 nested — see reference)_
  - **Post details sheet (mobile)** (`dialog`, click) — Bottom sheet opened via the header ⋯ / title / more on mobile; shows the full author block (with follow), title, and summary; X or backdrop closes it.

#### Page /link/[code]

**Share Link Viewer** — Public viewer for a shared content code — the server probes the backend /s/{code} target's content type and renders it as a full-screen image, a multi-slide presentation deck, or a sandboxed iframe ("frame"), all under a top bar with copy-link and open-app actions.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/link/[code]/llm.md`](<references/app/link/[code]/llm.md>)
- CTAs:
  - **Share viewer top bar** (`nav`, click) — Header above the image/frame content (and reused as the presentation deck's header); hidden when the top bar is collapsed. _(+3 nested — see reference)_
  - **Image / frame content** (`nav`, click) — Main content area: an image (object-contain) when the target is an image, otherwise a sandboxed iframe of the shared page; an image that fails to load falls back to the iframe.
  - **Toggle top bar** (`toggle`, click) — Maximize/minimize button overlaid at the top-right of the content; collapses the top bar for a full-screen view or restores it (image/frame modes only).
  - **Presentation deck viewer** (`dialog`, click) — When the target is a presentation folder, a full-screen slide-deck viewer (lazy-loaded) renders the deck with the shared top bar; its built-in close returns to the previous page (router.back).

#### Page /post/[showcaseId]

**Showcase Post** — Full-page detail view of one AI-generated showcase post — renders the deliverable artifact preview alongside title, author, prompt, and a comment thread, with remix, share, like, save, follow, and report actions; emits Article JSON-LD and SEO metadata.

- Upstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/discover-legacy`](<references/app/(dashboard)/discover-legacy/llm.md>), [`/discover-legacy/[id]`](<references/app/(dashboard)/discover-legacy/[id]/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/explore/[postId]`](<references/app/(dashboard)/explore/[postId]/llm.md>), [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/search`](<references/app/(dashboard)/search/llm.md>)
- Downstream: [`/profile/[uid]`](<references/app/(dashboard)/profile/[uid]/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/agent/[agent_name]`](<references/app/(dashboard)/agent/[agent_name]/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/post/[showcaseId]/llm.md`](<references/app/(dashboard)/post/[showcaseId]/llm.md>)
- CTAs:
  - **Back** (`button`, click) — Header chevron that goes to the previous page if there is history, otherwise replaces to /discover; also the Back button on the post-unavailable (404) state.
  - **Artifact preview** (`button`, click) — Deliverable file/media preview at the top (mobile) or left pane (desktop); tapping opens the full file viewer in post_detail context.
  - **Author** (`nav`, click) — Avatar, display name, and @handle in the header; tapping any opens the author's profile (/me when it's the current user, else /profile/[uid]). _(+1 nested — see reference)_
  - **Created by agent** (`button`, click) — "Created by <owner>'s <agent>" link under the title; opens the source agent (custom-agent page /agent/[agent_name] or its chat); disabled while resolving or when no agent is attached.
  - **Remix (Create my own)** (`dialog`, click) — Sparkles button that opens the remix dialog (also auto-opened by a pending remix intent); requires login. _(+5 nested — see reference)_
  - **Share** (`dialog`, click) — Share button (icon for others' posts, in the action row) that opens the share sheet seeded with the post snapshot and its public /post URL; requires login.
  - **Post options menu** (`menu`, click) — Kebab (⋯) menu in the header; contents depend on ownership. _(+3 nested — see reference)_
  - **Comment thread** (`nav`, click) — Comment list (right pane on desktop, below the body on mobile) with root comments and nested replies. _(+5 nested — see reference)_
  - **Engagement footer** (`nav`, click) — Sticky bottom bar with the comment composer plus like/save shortcuts. _(+6 nested — see reference)_

#### Page /share/[id]

**Shared Thread** — Public, read-only replay of an agent conversation identified by thread id — renders the messages, tool calls, and workspace artifacts with floating playback controls; the composer, agent/model selection, history, and new-task actions are all hidden, and an unknown/removed thread toasts "conversation not found" before redirecting home.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/(dashboard)/share/[id]/llm.md`](<references/app/(dashboard)/share/[id]/llm.md>)
- CTAs:
  - **Playback controls** (`nav`, click) — Floating pill of replay controls anchored at the bottom (re-centers when the workspace panel is open), driving step-by-step playback of the recorded conversation. _(+5 nested — see reference)_
  - **Shared header** (`nav`, click) — Top bar showing the project name with a 'Shared' badge; rename, history, new-task, and stop-agent actions are suppressed in shared mode. _(+1 nested — see reference)_
  - **Workspace preview panel** (`dialog`, click) — Right-side resizable panel (full-screen overlay on mobile) syncing to the current playback step; shows the tool call / artifact for the active message with navigation across tool calls. _(+3 nested — see reference)_
  - **File viewer** (`dialog`, click) — Full file viewer modal for workspace artifacts produced during the conversation (read-only). _(+3 nested — see reference)_
  - **Presentation viewer** (`dialog`, click) — Lazily-loaded full-screen presentation/slides viewer opened when a presentation artifact in the conversation is launched.

### Billing, Credits & Subscription — details

#### Page /checkout

**Checkout** — Paddle-powered checkout that reads a priceId from the URL, shows a live order summary (per-item price, billing cycle, subtotal/tax/total) beside an embedded Paddle payment form; on completion fires confetti and redirects to /checkout/success, and redirects signed-out users to /login.

- Upstream: [`/pricing`](<references/app/(public)/pricing/llm.md>)
- Downstream: [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/checkout/success`](<references/app/(dashboard)/checkout/success/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(dashboard)/checkout/llm.md`](<references/app/(dashboard)/checkout/llm.md>)
- CTAs:
  - **Back to pricing** (`link`, click) — Ghost button with a back arrow returning to /pricing.
  - **Paddle payment form** (`nav`, input) — Embedded Paddle checkout container (card/payment fields) that mounts for the URL priceId once Paddle is ready and the user is signed in; completing payment shows a processing spinner, fires confetti, toasts success, then redirects to /checkout/success, while a payment error toasts a retry message.

#### Page /checkout/success

**Checkout Success** — Payment-success confirmation page that fires confetti on load, refetches the subscription after a short delay, and offers links to the dashboard or the pricing page.

- Upstream: [`/checkout`](<references/app/(dashboard)/checkout/llm.md>)
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>)
- Reference: [`references/app/(dashboard)/checkout/success/llm.md`](<references/app/(dashboard)/checkout/success/llm.md>)
- CTAs:
  - **Go to dashboard** (`link`, click) — Primary button linking to the home dashboard (/).
  - **View plans** (`link`, click) — Outline button linking to /pricing to review subscription plans.

#### Page /credits

**Credits** — A redirect-only page that immediately forwards to the credits center settings page on its My Credits tab; renders no UI of its own.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- Reference: [`references/app/(dashboard)/credits/llm.md`](<references/app/(dashboard)/credits/llm.md>)
- CTAs: _none_

#### Page /pricing

**Pricing** — ISR-rendered plans-and-pricing page — a billing-cycle-toggled 5-tier plan table (Free / Go / Plus / Premium / Pro) with state-aware per-plan CTAs that start a Stripe Checkout session or open the customer portal, an optional reward-credits / Creator-90%-off discount layer, a manage-subscription entry, a tabbed Help Center FAQ, and the shared Teamily footer.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/checkout`](<references/app/(dashboard)/checkout/llm.md>), [`/checkout/success`](<references/app/(dashboard)/checkout/success/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>)
- Downstream: [`/login`](<references/app/(public)/login/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>)
- Reference: [`references/app/(public)/pricing/llm.md`](<references/app/(public)/pricing/llm.md>)
- CTAs:
  - **Billing cycle controls** (`nav`, click) — Row above the plan cards: the billing-cycle tabs and (when the user has reward credits and no active paid plan) the global credits toggle. _(+2 nested — see reference)_
  - **Plan table** (`nav`, click) — Grid of plan cards (Free / Go / Plus / Premium / Pro); each shows price, features, an optional discount option, and a state-aware action button. A plan_code x billing_cycle view event fires on scroll-into-view. _(+3 nested — see reference)_
  - **Manage subscription** (`button`, click) — Below the table for signed-in paid subscribers (hidden for free plans and store-managed subscriptions); opens the Stripe customer portal to manage, invoice, or cancel. On the Paddle provider this is a link to the Paddle portal; with no payment provider it is replaced by an auto-renewal notice banner.
  - **Help Center** (`nav`, click) — FAQ section with category tabs and per-category accordions; expanding a question fires a one-time analytics event. _(+3 nested — see reference)_
  - **Teamily footer** (`nav`, click) — Shared site footer (hidden on embedded views); product/company/legal link columns to /, /pricing, /about, the help center, /about/privacy-policy, and /about/terms-of-service.

### Settings & Account — details

#### Page /settings

**Settings Home** — The settings hub — a usage banner at the top plus grouped, tappable rows that link out to every settings sub-page and legal/support page, ending in social links and a sign-out/sign-in row.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/agents/config/[agentId]`](<references/app/(dashboard)/agents/config/[agentId]/llm.md>)
- Downstream: [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>), [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/settings/usage`](<references/app/(dashboard)/settings/usage/llm.md>), [`/settings/language`](<references/app/(dashboard)/settings/language/llm.md>), [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>), [`/settings/channels`](<references/app/(dashboard)/settings/channels/llm.md>), [`/settings/privacy`](<references/app/(dashboard)/settings/privacy/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/(dashboard)/settings/llm.md`](<references/app/(dashboard)/settings/llm.md>)
- CTAs:
  - **Usage banner** (`nav`, click) — Top card showing the current plan, remaining-window percent (conic ring), and reset countdown, with a single CTA button. _(+1 nested — see reference)_
  - **Account profile** (`nav`, click) — Account & Profile section. _(+1 nested — see reference)_
  - **Creator rewards** (`nav`, click) — Creator & Rewards section, each row showing an earned/balance amount on the right. _(+3 nested — see reference)_
  - **Plan, billing & usage** (`nav`, click) — Plan, Billing & Usage section. _(+2 nested — see reference)_
  - **AI agent** (`nav`, click) — AI Agent section. _(+3 nested — see reference)_
  - **Preferences & security** (`nav`, click) — Preferences & Security section. _(+1 nested — see reference)_
  - **Support & legal** (`nav`, click) — Support & Legal section. _(+5 nested — see reference)_
  - **Session** (`nav`, click) — Session section with the sign-out/sign-in control. _(+1 nested — see reference)_
  - **Social links** (`link`, click) — X, LinkedIn, and Discord icons opening the product's social pages in a new tab.

#### Page /settings/affiliate

**Affiliate Program** — Affiliate program hub — an earnings hero with commission balance plus withdraw entry and withdrawable/pending and invitees/spend chips, a 25% commission explainer with per-user cap, a per-invitee earnings breakdown list, and an invite-sharing toolbar (copy link, QR, email, social).

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>)
- Downstream: [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>)
- Reference: [`references/app/(dashboard)/settings/affiliate/llm.md`](<references/app/(dashboard)/settings/affiliate/llm.md>)
- CTAs:
  - **Earnings hero** (`nav`, click) — Green card showing the affiliate commission balance with withdrawable/pending and invitees/lifetime-spend status chips. _(+1 nested — see reference)_
  - **Send an invite** (`nav`, click) — Invite-sharing toolbar showing the personal invite link plus copy and share controls. _(+4 nested — see reference)_

#### Page /settings/channels

**Channels** — OpenClaw channel management — shows the user's Teamily API key and a one-line quick-connect shell script for linking a self-hosted OpenClaw (2026.3.8+); polls connected deployments every 10s and, when there is a platform-hosted claw and the subscription is not Active, surfaces a VM-suspension warning card.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/pricing`](<references/app/(public)/pricing/llm.md>)
- Reference: [`references/app/(dashboard)/settings/channels/llm.md`](<references/app/(dashboard)/settings/channels/llm.md>)
- CTAs:
  - **Toggle API key visibility** (`toggle`, click) — Eye / eye-off button that reveals or masks the Teamily API key; disabled until a key is available.
  - **Copy API key** (`button`, click) — Copies the Teamily API key to the clipboard (toasts success, or error if unavailable/copy fails); shows a check icon briefly after copying. Disabled when no key.
  - **Copy connect script** (`button`, click) — Copy control on the quick-connect code block; copies the full OpenClaw connect shell command to the clipboard.
  - **Platform-VM warning card** (`nav`, click) — Shown when the subscription is Canceled/Expired and a platform-hosted claw exists; warns that platform VMs will be suspended and data deleted after 14 days. _(+2 nested — see reference)_

#### Page /settings/connectors

**Connectors** — Account-level connectors directory — a single-column, searchable list of Composio toolkits (third-party apps) the user can Connect (OAuth popup creates a credential profile) or Disconnect (deletes the credential profile); connected apps sort to the top and a hardcoded slug set is hidden.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/connectors/llm.md`](<references/app/(dashboard)/settings/connectors/llm.md>)
- CTAs:
  - **Search apps** (`input`, input) — Filters the toolkit list by name (sent as the server-side search query); empty shows all visible toolkits.
  - **Connect app** (`button`, click) — Shown on a disconnected app — opens a blank popup, POSTs a new Composio credential profile, and redirects the popup to the returned OAuth URL; refreshes profiles on success, closes the popup on error. Shows a spinner while pending.
  - **Disconnect app** (`button`, click) — Shown on a connected app — deletes all credential profiles for that toolkit slug (single or bulk delete), toasts success/partial/failure, and refreshes the list. Shows a spinner while pending.

#### Page /settings/creator-center

**Creator Center** — Creator earnings hub — an earnings hero with the cash balance plus withdraw entry, a 4-step How-It-Works guide with Start-Creating CTAs, a static engagement rewards ladder (100/1000/10000 engagements → $CASH), recent per-post earnings, and a creator-earnings FAQ accordion.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>)
- Downstream: [`/settings/withdraw`](<references/app/(dashboard)/settings/withdraw/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>)
- Reference: [`references/app/(dashboard)/settings/creator-center/llm.md`](<references/app/(dashboard)/settings/creator-center/llm.md>)
- CTAs:
  - **Earnings hero** (`nav`, click) — Green balance card showing the current cash balance plus pending / lifetime / card-linked status chips. _(+1 nested — see reference)_
  - **How it works** (`nav`, click) — 4-step earnings explainer (Start creating → Publish → Engage → Get paid); a vertical timeline on mobile, stepped layout on desktop. _(+3 nested — see reference)_
  - **Rewards ladder info** (`button`, click) — Info button beside the ladder heading; opens a popover explaining how engagement-based earning works (fires a tier-popover-opened event).
  - **FAQ accordion** (`toggle`, click) — Single-open accordion of six creator-earnings FAQ items; tapping a question expands its answer.

#### Page /settings/creator-studio

**Creator Studio** — Creator studio page that currently just renders the account-level Connectors settings (Composio toolkit list) as a placeholder until the agents-management module lands.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/creator-studio/llm.md`](<references/app/(dashboard)/settings/creator-studio/llm.md>)
- CTAs:
  - **Search connectors** (`input`, input) — Filters the Composio toolkit list by search term (connected toolkits are sorted first).
  - **Connect** (`button`, click) — Per-toolkit; opens a popup window and creates a Composio credential profile to start the OAuth connect flow.
  - **Disconnect** (`button`, click) — Per connected toolkit; deletes all credential profiles for that toolkit (bulk if multiple) and refreshes the list, with a success/partial/error toast.

#### Page /settings/credit-usage

**Credit Usage** — Usage overview page rendering the shared CreditUsageSettings — read-only progress cards for the 5-hour window, weekly cap, and (Plus/Pro only) advanced-model monthly quota, an on-demand pay-as-you-go billing card (eligible Plus/Pro only) with toggle, spend/limit details and suspended/limit-reached banners, plus a token-usage summary card (lifetime/month/week/day).

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/credit-usage/llm.md`](<references/app/(dashboard)/settings/credit-usage/llm.md>)
- CTAs:
  - **On-demand toggle** (`toggle`, click) — Switch on the on-demand usage card; turning it on opens the enable confirmation dialog, turning it off disables billing immediately. Disabled when not eligible, while updating, or when payment is suspended.
  - **Enable confirmation dialog** (`dialog`, click) — Opened by turning the toggle on — Cancel or Enable; Enable activates on-demand billing with the previous monthly limit or the $100 default.
  - **Monthly limit input** (`input`, input) — Number field for the on-demand monthly spend limit (shown when active); clamped to $10–$9999, falling back to $100, and saved on blur.
  - **Retry Payment** (`button`, click) — Shown in the payment-suspended banner; retries charging the unpaid balance.

#### Page /settings/credits-center

**Credits Center** — Tabbed credits/rewards hub synced to the ?tab= query param (onboarding, invite, leaderboard, credits) — first-week onboarding tasks and login-streak rewards, an invite-friends panel (referral rewards, share link, code redemption, invite history, FAQ), a personal token-usage leaderboard, and a credit balance with activity history. All tabs route the Apply Credits / Buy Plus CTAs to /pricing.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/apply/invite-code`](<references/app/apply/invite-code/llm.md>), [`/credits`](<references/app/(dashboard)/credits/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/get-started`](<references/app/(dashboard)/get-started/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/invite-history`](<references/app/(dashboard)/settings/invite-history/llm.md>)
- Downstream: [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>)
- Reference: [`references/app/(dashboard)/settings/credits-center/llm.md`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- CTAs:
  - **Tab nav** (`tabs`, click) — Horizontally scrollable row of tab pills synced to ?tab=; the Leaderboard tab is hidden when the leaderboard feature gate is off, and the streak-dependent tab order varies by whether the login-streak feature is visible. _(+4 nested — see reference)_
  - **Onboarding tab** (`nav`, click) — First-week rewards view shown on ?tab=onboarding. _(+4 nested — see reference)_
  - **Invite tab** (`nav`, click) — Referral panel shown on ?tab=invite. _(+8 nested — see reference)_
  - **Leaderboard tab** (`nav`, click) — Personal token-usage league shown on ?tab=leaderboard. _(+1 nested — see reference)_
  - **My Credits tab** (`nav`, click) — Credit balance and activity view shown on ?tab=credits. _(+1 nested — see reference)_

#### Page /settings/help

**Help** — Help settings page listing a Help Center link and a Contact Us entry that opens a dialog with the support email; on mobile it shows a sticky header with a back button.

- Upstream: [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>)
- Reference: [`references/app/(dashboard)/settings/help/llm.md`](<references/app/(dashboard)/settings/help/llm.md>)
- CTAs:
  - **Mobile back button** (`button`, click) — Mobile-only sticky-header arrow that navigates back to the previous page.
  - **Help Center** (`link`, click) — Settings row linking to /about/help-center.
  - **Contact Us** (`button`, click) — Settings row that opens the contact dialog. _(+1 nested — see reference)_

#### Page /settings/invite-history

**Invite History** — Server redirect-only route that immediately forwards to /settings/credits-center?tab=invite to show the user's invitation history; renders no UI of its own.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/settings/credits-center`](<references/app/(dashboard)/settings/credits-center/llm.md>)
- Reference: [`references/app/(dashboard)/settings/invite-history/llm.md`](<references/app/(dashboard)/settings/invite-history/llm.md>)
- CTAs: _none_

#### Page /settings/knowledge-base

**Knowledge Base** — Knowledge Base settings page — currently a static placeholder rendering a title, a one-line description, and a "Coming soon" notice; no interactive controls or data yet.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/knowledge-base/llm.md`](<references/app/(dashboard)/settings/knowledge-base/llm.md>)
- CTAs: _none_

#### Page /settings/language

**Language** — Language settings page with two independent knobs — the System (UI) locale and the Chat auto-translation target language — plus an auto-translate master toggle; the two pickers draw from different supported-language sets (see body).

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/language/llm.md`](<references/app/(dashboard)/settings/language/llm.md>)
- CTAs:
  - **System Language** (`select`, click) — Picks the app UI locale; applied immediately via the locale context and persisted locally. 17 supported locales from LOCALES/LOCALE_LABELS — see the body.
  - **Chat Language** (`select`, click) — Picks the target language for chat message auto-translation; saved to the translation service (toasts on save failure). 17 supported languages from TRANSLATION_LANGUAGES — see the body; this set differs from the UI locales.
  - **Auto Translate** (`toggle`, click) — Checkbox master switch enabling/disabling automatic translation of incoming chat messages (stored on the IM self user; defaults ON when never set; toasts on save failure).

## Supported languages

This page exposes **two separate language settings backed by two different lists** — keep them distinct. The System (UI) language is applied through the locale context and stored locally; the Chat language and Auto Translate switch control message auto-translation (the language is persisted on the translation service, the switch on the IM self user).

### System (UI) language — 17 locales

The interface locale, from `LOCALES` / `LOCALE_LABELS` in `lib/i18n/index.ts` (default locale: `en`):

| Code | Label |
| --- | --- |
| `en` | English |
| `fa` | فارسی (Persian) |
| `fr` | Français (French) |
| `de` | Deutsch (German) |
| `es` | Español (Spanish) |
| `it` | Italiano (Italian) |
| `ru` | Русский (Russian) |
| `id` | Bahasa Indonesia |
| `ms` | Bahasa Melayu (Malay) |
| `hi` | हिन्दी (Hindi) |
| `bn` | বাংলা (Bengali) |
| `th` | ภาษาไทย (Thai) |
| `ja` | 日本語 (Japanese) |
| `ko` | 한국어 (Korean) |
| `zh-HK` | 繁體中文(香港) (Traditional Chinese — Hong Kong) |
| `zh-TW` | 繁體中文(台灣) (Traditional Chinese — Taiwan) |
| `zh` | 简体中文 (Simplified Chinese) |

### Chat auto-translation language — 17 languages

The target language for message auto-translation, from `TRANSLATION_LANGUAGES` in `lib/im/translation.ts`. When the user has not set one, the value falls back to `detectSystemTargetLanguage()` (the browser language mapped to a supported code):

| Code | Label |
| --- | --- |
| `en` | English |
| `fa` | فارسی |
| `fr` | Français |
| `de` | Deutsch |
| `es` | Español |
| `pt` | Português |
| `it` | Italiano |
| `ru` | Русский |
| `id` | Bahasa Indonesia |
| `vi` | Tiếng Việt |
| `bn` | বাংলা |
| `th` | ไทย |
| `ar` | العربية |
| `ja` | 日本語 |
| `ko` | 한국어 |
| `zh-TW` | 繁體中文 |
| `zh-CN` | 简体中文 |

### The two sets are NOT identical

- **Only in the UI locale set:** Bahasa Melayu (`ms`), हिन्दी (`hi`), and a Hong Kong Traditional Chinese variant (`zh-HK`).
- **Only in the chat-translation set:** Português (`pt`), Tiếng Việt (`vi`), العربية (`ar`).
- **Chinese codes differ:** the UI uses `zh` / `zh-TW` / `zh-HK`; chat translation uses `zh-CN` / `zh-TW`.

#### Page /settings/privacy

**Privacy** — Privacy settings page that loads the current profile privacy view-model and lets the owner toggle whether their liked posts and bookmarked/saved posts are publicly visible, then save the changes (saving is enabled only when a toggle differs from the loaded state).

- Upstream: [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/privacy/llm.md`](<references/app/(dashboard)/settings/privacy/llm.md>)
- CTAs:
  - **Likes visible toggle** (`toggle`, click) — Switch controlling whether your liked posts are publicly visible on your profile; disabled while loading or saving.
  - **Bookmarks visible toggle** (`toggle`, click) — Switch controlling whether your saved/bookmarked posts are publicly visible on your profile; disabled while loading or saving.
  - **Save changes** (`button`, click) — Persists the changed toggles via the privacy API and syncs the profile-header cache; disabled until a toggle changes, shows a spinner while saving, and toasts success/failure.

#### Page /settings/security

**Security** — Account security settings page; currently a static placeholder showing the security heading, a manage-security subtitle, and a "coming soon" message with no interactive controls.

- Upstream: [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/security/llm.md`](<references/app/(dashboard)/settings/security/llm.md>)
- CTAs: _none_

#### Page /settings/subscription

**Subscription** — Subscription settings page stacking three cards — the current-plan summary (plan name, trial/canceled badge, renewal/expiry date, plan actions), a manage-billing card (Stripe customer portal or store-managed deep link, or an upgrade promo for free users), and a quick-links/resources card with social follow icons.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>)
- Reference: [`references/app/(dashboard)/settings/subscription/llm.md`](<references/app/(dashboard)/settings/subscription/llm.md>)
- CTAs:
  - **Current plan card** (`nav`, click) — Top card showing the plan name with status badge (trial / canceled / via-store), the renewal or access-until date, and the contextual plan action buttons. _(+3 nested — see reference)_
  - **Manage billing card** (`nav`, click) — Shown for paid plans; routes billing management to Stripe or the originating app store. _(+2 nested — see reference)_
  - **Upgrade promo card** (`nav`, click) — Free-plan-only card listing Plus benefits (more credits, more tasks, all agents, early access) with a single CTA. _(+1 nested — see reference)_
  - **Resources / quick links** (`nav`, click) — Resource link rows plus a Follow Us social row. _(+4 nested — see reference)_

#### Page /settings/translation

**Translation** — Translation settings page that reuses the LanguageSettings component — two independent language pickers (the System/UI locale and the Chat auto-translation target language, drawn from different supported-language sets) plus an auto-translate master toggle.

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/translation/llm.md`](<references/app/(dashboard)/settings/translation/llm.md>)
- CTAs:
  - **System Language** (`select`, click) — Picks the app UI locale; applied immediately via the locale context and persisted locally. 17 supported locales from LOCALES/LOCALE_LABELS — see the body.
  - **Chat Language** (`select`, click) — Picks the target language for chat message auto-translation; saved to the translation service (toasts on save failure). 17 supported languages from TRANSLATION_LANGUAGES — see the body; this set differs from the UI locales.
  - **Auto Translate** (`toggle`, click) — Checkbox master switch enabling/disabling automatic translation of incoming chat messages (stored on the IM self user; defaults ON when never set; toasts on save failure).

## Supported languages

This page exposes **two separate language settings backed by two different lists** — keep them distinct. The System (UI) language is applied through the locale context and stored locally; the Chat language and Auto Translate switch control message auto-translation (the language is persisted on the translation service, the switch on the IM self user).

### System (UI) language — 17 locales

The interface locale, from `LOCALES` / `LOCALE_LABELS` in `lib/i18n/index.ts` (default locale: `en`):

| Code | Label |
| --- | --- |
| `en` | English |
| `fa` | فارسی (Persian) |
| `fr` | Français (French) |
| `de` | Deutsch (German) |
| `es` | Español (Spanish) |
| `it` | Italiano (Italian) |
| `ru` | Русский (Russian) |
| `id` | Bahasa Indonesia |
| `ms` | Bahasa Melayu (Malay) |
| `hi` | हिन्दी (Hindi) |
| `bn` | বাংলা (Bengali) |
| `th` | ภาษาไทย (Thai) |
| `ja` | 日本語 (Japanese) |
| `ko` | 한국어 (Korean) |
| `zh-HK` | 繁體中文(香港) (Traditional Chinese — Hong Kong) |
| `zh-TW` | 繁體中文(台灣) (Traditional Chinese — Taiwan) |
| `zh` | 简体中文 (Simplified Chinese) |

### Chat auto-translation language — 17 languages

The target language for message auto-translation, from `TRANSLATION_LANGUAGES` in `lib/im/translation.ts`. When the user has not set one, the value falls back to `detectSystemTargetLanguage()` (the browser language mapped to a supported code):

| Code | Label |
| --- | --- |
| `en` | English |
| `fa` | فارسی |
| `fr` | Français |
| `de` | Deutsch |
| `es` | Español |
| `pt` | Português |
| `it` | Italiano |
| `ru` | Русский |
| `id` | Bahasa Indonesia |
| `vi` | Tiếng Việt |
| `bn` | বাংলা |
| `th` | ไทย |
| `ar` | العربية |
| `ja` | 日本語 |
| `ko` | 한국어 |
| `zh-TW` | 繁體中文 |
| `zh-CN` | 简体中文 |

### The two sets are NOT identical

- **Only in the UI locale set:** Bahasa Melayu (`ms`), हिन्दी (`hi`), and a Hong Kong Traditional Chinese variant (`zh-HK`).
- **Only in the chat-translation set:** Português (`pt`), Tiếng Việt (`vi`), العربية (`ar`).
- **Chinese codes differ:** the UI uses `zh` / `zh-TW` / `zh-HK`; chat translation uses `zh-CN` / `zh-TW`.

#### Page /settings/usage

**Usage** — Usage settings page rendering the shared CreditUsageSettings without its title — read-only progress cards for the 5-hour window, weekly cap, and (Plus/Pro only) advanced-model monthly quota, an on-demand pay-as-you-go billing card (eligible Plus/Pro only) with toggle, spend/limit details and suspended/limit-reached banners, plus a token-usage summary card (lifetime/month/week/day).

- Upstream: [`/`](<references/app/(dashboard)/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Downstream: _none_
- Reference: [`references/app/(dashboard)/settings/usage/llm.md`](<references/app/(dashboard)/settings/usage/llm.md>)
- CTAs:
  - **On-demand toggle** (`toggle`, click) — Switch on the on-demand usage card; turning it on opens the enable confirmation dialog, turning it off disables billing immediately. Disabled when not eligible, while updating, or when payment is suspended.
  - **Enable confirmation dialog** (`dialog`, click) — Opened by turning the toggle on — Cancel or Enable; Enable activates on-demand billing with the previous monthly limit or the $100 default.
  - **Monthly limit input** (`input`, input) — Number field for the on-demand monthly spend limit (shown when active); clamped to $10–$9999, falling back to $100, and saved on blur.
  - **Retry Payment** (`button`, click) — Shown in the payment-suspended banner; retries charging the unpaid balance.

#### Page /settings/withdraw

**Withdraw** — Unified cash-out page — total withdrawable balance (creator + affiliate) with a Withdraw All action, source rows linking to the creator and affiliate pages, and a withdrawal-history list; whole page is gated and redirects home via a 'coming soon' dialog when the withdraw-entry flag is off.

- Upstream: [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>)
- Downstream: [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/`](<references/app/(dashboard)/llm.md>)
- Reference: [`references/app/(dashboard)/settings/withdraw/llm.md`](<references/app/(dashboard)/settings/withdraw/llm.md>)
- CTAs:
  - **Withdraw All** (`button`, click) — Opens the withdraw dialog; disabled when nothing is withdrawable, and labeled 'Link Card and Withdraw' when no Stripe payout account is connected.
  - **Withdraw dialog** (`dialog`, click) — 3-step modal (Connect Stripe → Amount → Done). Connect starts Stripe Connect onboarding in a popup; Amount confirms the full withdrawable amount; Done shows a confetti success that auto-closes after 3s. _(+4 nested — see reference)_
  - **Earnings source rows** (`link`, click) — Two rows — Creator (→ /settings/creator-center) and Affiliate (→ /settings/affiliate) — each showing its withdrawable amount and summary.

### Developer & Test Pages — details

#### Page /dev/group-message-cases

**Group Message Cases** — Developer-only preview page that renders the group-message custom message components against selectable mock fixtures, to verify GroupMessageStartRender, the before-cutoff card, and the streaming-card layouts; no real data or navigation.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- Reference: [`references/app/(dashboard)/dev/group-message-cases/llm.md`](<references/app/(dashboard)/dev/group-message-cases/llm.md>)
- CTAs:
  - **Case select** (`select`, click) — Dropdown of ~18 mock case IDs (loading, completed variants with 0/1/2/3+ files & follow-ups, text-only, running with/without steps, streaming overlay/media-scroll/text-collapsible/waiting, failed, stopped, pending); switching it rebuilds the mock snapshot/stream state and re-renders the before-cutoff card plus the media-vs-text start-render preview below.

#### Page /embed/tool-view

**Embed Tool View** — Standalone iframe-embeddable renderer that decodes a base64-encoded JSON `data` query param (toolCall + optional toolResult + threadId) and renders the matching read-only ToolView from the tool-view registry; shows a Loading state during Suspense and an error notice when the payload is missing or invalid.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- Reference: [`references/app/embed/tool-view/llm.md`](<references/app/embed/tool-view/llm.md>)
- CTAs: _none_

## Shared layouts & chrome

Layout components (`layout.tsx`) wrap one or more route segments and render
the persistent chrome — headers, sidebars, tab bars, and providers — shared by
the pages beneath them. Their CTAs are the app-wide navigation controls.

### Layout / — Root Layout

**Root Layout** — The top-level App Router layout wrapping every route — builds the base HTML document with fonts, viewport/theme-color, JSON-LD structured data, Google Analytics and Google Identity scripts, and the global provider stack (theme, locale, react-query, app/auth/subscription/IM/push/studio/modal contexts); SSR is embed-aware (trims i18n namespaces and pre-marks `data-embed` when `?embed=1|native`), and the client shell mounts a toaster, splash screen, and globally-triggered modal/notifier portals. Renders no visible navbar/footer chrome of its own.

- Wraps: `app`
- Downstream: _none_
- Reference: [`references/app/layout.llm.md`](<references/app/layout.llm.md>)
- CTAs: _none_

### Layout /(dashboard) — Dashboard Layout (App Shell)

**Dashboard Layout (App Shell)** — The app shell wrapping every dashboard route — desktop renders the left icon rail (primary nav + footer utility rail + account/info menu) and mobile renders a bottom tab bar on primary pages; it also hosts the parallel modal slot and the mobile download-app dialog, while embedded (RN WebView / iframe) requests skip all chrome.

- Wraps: `app/(dashboard)`
- Downstream: [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>), [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/automations`](<references/app/(dashboard)/automations/llm.md>), [`/explore`](<references/app/(dashboard)/explore/llm.md>), [`/memory`](<references/app/(dashboard)/memory/llm.md>), [`/me`](<references/app/(dashboard)/me/llm.md>), [`/contact`](<references/app/(dashboard)/contact/llm.md>), [`/download`](<references/app/(dashboard)/download/llm.md>), [`/settings`](<references/app/(dashboard)/settings/llm.md>), [`/settings/language`](<references/app/(dashboard)/settings/language/llm.md>), [`/settings/usage`](<references/app/(dashboard)/settings/usage/llm.md>), [`/settings/subscription`](<references/app/(dashboard)/settings/subscription/llm.md>), [`/settings/creator-center`](<references/app/(dashboard)/settings/creator-center/llm.md>), [`/settings/affiliate`](<references/app/(dashboard)/settings/affiliate/llm.md>), [`/settings/channels`](<references/app/(dashboard)/settings/channels/llm.md>), [`/settings/connectors`](<references/app/(dashboard)/settings/connectors/llm.md>), [`/profile/edit`](<references/app/(dashboard)/profile/edit/llm.md>), [`/credits`](<references/app/(dashboard)/credits/llm.md>), [`/get-started`](<references/app/(dashboard)/get-started/llm.md>), [`/pricing`](<references/app/(public)/pricing/llm.md>), [`/about`](<references/app/(public)/about/llm.md>), [`/about/refund-policy`](<references/app/(public)/about/refund-policy/llm.md>), [`/about/terms-of-service`](<references/app/(public)/about/terms-of-service/llm.md>), [`/about/privacy-policy`](<references/app/(public)/about/privacy-policy/llm.md>), [`/about/help-center`](<references/app/(public)/about/help-center/llm.md>)
- Reference: [`references/app/(dashboard)/layout.llm.md`](<references/app/(dashboard)/layout.llm.md>)
- CTAs:
  - **Sidebar rail** (`nav`, click) — Desktop-only left icon rail (md+): logo, primary nav, footer utility rail, and the account/info menu; hidden on mobile and on embed. _(+15 nested — see reference)_
  - **Mobile tab bar** (`tabs`, click) — Bottom navigation shown on mobile primary pages (and when the glueview/thread view is visible); hidden on desktop and on embed. _(+5 nested — see reference)_
  - **Modal slot** (`dialog`, click) — Parallel-route @modal slot rendered alongside children for intercepted route modals.
  - **Mobile download-app dialog** (`dialog`, click) — Prompt encouraging mobile-web users to install the native app.

### Layout /(public) — Public Layout

**Public Layout** — Chrome for public / signed-out routes (pricing, about, support, login, invite landing, features) — a sticky top nav with an optional history back button, a home logo, and either an avatar shortcut into the app (signed in) or a Login button (signed out). The whole bar is hidden on embedded views.

- Wraps: `app/(public)`
- Downstream: [`/`](<references/app/(dashboard)/llm.md>), [`/chat`](<references/app/(dashboard)/chat/llm.md>), [`/login`](<references/app/(public)/login/llm.md>)
- Reference: [`references/app/(public)/layout.llm.md`](<references/app/(public)/layout.llm.md>)
- CTAs:
  - **Top nav bar** (`nav`, click) — Sticky, blur-backed top navigation bar; hidden entirely on embedded views (data-hide-on-embed / useIsEmbedded). _(+4 nested — see reference)_

### Layout /chat — Chat Layout

**Chat Layout** — Two-pane chrome for the messaging workspace — a resizable left sidebar (the aside panel with conversation search, the new/contact menu, and the conversation list with per-item context menus) beside the active conversation. On mobile the open conversation is presented in a full-screen sheet whose back button clears the selection.

- Wraps: `app/(dashboard)/chat`
- Downstream: [`/discover`](<references/app/(dashboard)/discover/llm.md>), [`/add-contact`](<references/app/(dashboard)/add-contact/llm.md>), [`/search/conversation`](<references/app/(dashboard)/search/conversation/llm.md>)
- Reference: [`references/app/(dashboard)/chat/layout.llm.md`](<references/app/(dashboard)/chat/layout.llm.md>)
- CTAs:
  - **Conversation sidebar** (`nav`, click) — Resizable aside panel: header (search + new menu), the conversation list, and (when searching) the global-search screen. _(+7 nested — see reference)_
  - **Mobile conversation sheet** (`dialog`, click) — Full-screen right-side sheet that shows the open conversation on mobile; the system/back gesture closes it and clears the current conversation.
  - **Sidebar resize handle** (`button`, hover/drag) — Drag handle on the resizable sidebar edge; persists the chosen width (300–500px) under the chat-sidebar-width key. (Desktop only.)

### Layout /contact — Contact Layout

**Contact Layout** — Two-pane chrome for the Contacts area — a resizable left sidebar with the Contacts title, an add-contact button, and the contact nav (My Agents / My Friends / Phone Contacts) beside the routed contact content. On mobile the /contact root renders a header (title + add-contact) over the nav and contact list in one scroll area, while sub-pages render full-screen.

- Wraps: `app/(dashboard)/contact`
- Downstream: [`/contact/my-agents`](<references/app/(dashboard)/contact/my-agents/llm.md>), [`/contact/my-friends`](<references/app/(dashboard)/contact/my-friends/llm.md>), [`/contact/phone-contacts`](<references/app/(dashboard)/contact/phone-contacts/llm.md>), [`/add-contact`](<references/app/(dashboard)/add-contact/llm.md>)
- Reference: [`references/app/(dashboard)/contact/layout.llm.md`](<references/app/(dashboard)/contact/layout.llm.md>)
- CTAs:
  - **Add contact button** (`button`, click) — Plus icon in the sidebar (desktop) / root header (mobile); opens the Add Contact modal on desktop, or navigates to /add-contact on mobile.
  - **Contact nav** (`nav`, click) — Sidebar (desktop) / root list (mobile) navigation between the three contact sub-views; the active tab is highlighted. _(+3 nested — see reference)_
  - **Sidebar resize handle** (`button`, hover/drag) — Drag handle on the resizable sidebar edge; persists the chosen width under the contact-sidebar-width key. (Desktop only.)

### Layout /embed — Embed Layout

**Embed Layout** — Pass-through layout segment for the /embed area — returns its children directly with no chrome, metadata, or interactive controls; exists only to namespace embeddable views meant to be loaded inside iframes.

- Wraps: `app/embed`
- Downstream: _none_
- Reference: [`references/app/embed/layout.llm.md`](<references/app/embed/layout.llm.md>)
- CTAs: _none_

### Layout /embed/tool-view — Embed Tool View Layout

**Embed Tool View Layout** — Pass-through layout for the embeddable tool-view segment — returns children directly and only sets metadata (title "Tool view", robots noindex/nofollow); has no chrome or interactive controls.

- Wraps: `app/embed/tool-view`
- Downstream: _none_
- Reference: [`references/app/embed/tool-view/layout.llm.md`](<references/app/embed/tool-view/layout.llm.md>)
- CTAs: _none_

### Layout /explore — Explore Layout

**Explore Layout** — Pass-through layout for the Explore feed and its /explore/[postId] sub-route; returns children unchanged and defers all chrome to the parent dashboard shell.

- Wraps: `app/(dashboard)/explore`
- Downstream: _none_
- Reference: [`references/app/(dashboard)/explore/layout.llm.md`](<references/app/(dashboard)/explore/layout.llm.md>)
- CTAs: _none_

### Layout /i/[invite_code] — Invite Landing Layout

**Invite Landing Layout** — Server layout (revalidate 3600) that fetches invite-landing data to build per-invite OG/Twitter title and description from the inviter's name/tagline and code type (CHANNEL vs personal), falling back to generic invite copy on invalid or unreachable codes; the og:image still comes from opengraph-image.tsx and children pass through unchanged.

- Wraps: `app/(public)/i/[invite_code]`
- Downstream: _none_
- Reference: [`references/app/(public)/i/[invite_code]/layout.llm.md`](<references/app/(public)/i/[invite_code]/layout.llm.md>)
- CTAs: _none_

### Layout /link/[code] — Share Link Layout

**Share Link Layout** — Server pass-through layout for shared-artifact deep links; generateMetadata emits crawler-readable OG/Twitter title, description, and a per-code canonical URL for the /link/[code] route, then renders its children unchanged.

- Wraps: `app/link/[code]`
- Downstream: _none_
- Reference: [`references/app/link/[code]/layout.llm.md`](<references/app/link/[code]/layout.llm.md>)
- CTAs: _none_

### Layout /login — Login Layout

**Login Layout** — Server layout for the client-rendered /login page; a pass-through that renders its children and only sets robots noindex/nofollow metadata so the auth route stays out of search results.

- Wraps: `app/(public)/login`
- Downstream: _none_
- Reference: [`references/app/(public)/login/layout.llm.md`](<references/app/(public)/login/layout.llm.md>)
- CTAs: _none_

### Layout /settings — Settings Layout

**Settings Layout** — Chrome for settings sub-pages — wraps each sub-page in a max-width column with a sticky header (localized title + Back button) and an enter motion transition; at the /settings root it is a pure pass-through that renders the hub with no header.

- Wraps: `app/(dashboard)/settings`
- Downstream: [`/settings`](<references/app/(dashboard)/settings/llm.md>)
- Reference: [`references/app/(dashboard)/settings/layout.llm.md`](<references/app/(dashboard)/settings/layout.llm.md>)
- CTAs:
  - **Sub-page header** (`nav`, click) — Sticky top header shown on every settings sub-page (not the /settings root), displaying the localized sub-page title. _(+1 nested — see reference)_

### Layout /share/[id] — Shared Conversation Layout

**Shared Conversation Layout** — Server layout for shared agent-conversation replays; fetches the thread and its project to build SEO/OG/Twitter metadata (title, description, canonical URL, summary_large_image card) — falling back to a generic "Shared Conversation | Teamily AI" on missing data or error — then renders its children as a transparent pass-through.

- Wraps: `app/(dashboard)/share/[id]`
- Downstream: _none_
- Reference: [`references/app/(dashboard)/share/[id]/layout.llm.md`](<references/app/(dashboard)/share/[id]/layout.llm.md>)
- CTAs: _none_

### Layout /support — Support Layout

**Support Layout** — Server layout that supplies static SEO/OG metadata (title, description, canonical, OpenGraph, Twitter summary_large_image card) for the client-rendered /support page, then passes children through unchanged.

- Wraps: `app/(public)/support`
- Downstream: _none_
- Reference: [`references/app/(public)/support/layout.llm.md`](<references/app/(public)/support/layout.llm.md>)
- CTAs: _none_
