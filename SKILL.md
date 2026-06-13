---
name: teamily-ai-app-guide
description: >-
  Usage manual for the Teamily AI web app (teamily.ai) — the page map,
  navigation relationships, CTAs, and feature areas. Use when operating,
  testing, automating, or integrating with the Teamily AI web app, or when
  you need to know which page handles a task and how to reach it.
---

# Teamily AI Web App Guide

Teamily AI is a personal and social AI agent OS: an IM-style workspace where
users chat with friends, groups, and AI agents; discover and remix
community-created content; and manage agents, credits, and subscriptions.

This manual is generated from the per-route `llm.md` (page) and
`layout.llm.md` (shared layout) files in `apps/chat-to/app`. Each page entry
lists:

- **upstream** — pages that navigate into this page
- **downstream** — pages this page navigates to
- **CTAs** — the page's main interactive controls. Each CTA notes its `type` (button, input, tabs, toggle, select, link, dialog), its `trigger` (how it's activated: click, hover, input, …; defaults to click), and may nest child CTAs under `items`.

Regenerate with `pnpm gen:skill` (or `node generate-skill-md.mjs`) after editing any `llm.md` or `layout.llm.md`.

## How navigation works

- `/` is the landing page and dashboard shell. Its global navigation (header, sidebar, tab bar) reaches: [`/about`](#page-about), [`/about/help-center`](#page-abouthelp-center), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/refund-policy`](#page-aboutrefund-policy), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/chat`](#page-chat), [`/contact`](#page-contact), [`/discover`](#page-discover), [`/download`](#page-download), [`/explore`](#page-explore), [`/login`](#page-login), [`/me`](#page-me), [`/pricing`](#page-pricing), [`/profile/[uid]`](#page-profileuid), [`/profile/edit`](#page-profileedit), [`/settings`](#page-settings), [`/settings/affiliate`](#page-settingsaffiliate), [`/settings/channels`](#page-settingschannels), [`/settings/connectors`](#page-settingsconnectors), [`/settings/creator-center`](#page-settingscreator-center), [`/settings/credits-center`](#page-settingscredits-center), [`/settings/language`](#page-settingslanguage), [`/settings/subscription`](#page-settingssubscription), [`/settings/usage`](#page-settingsusage).
- Signed-out users are redirected to [`/login`](#page-login) by most product pages; after login they land back in the app.
- **Deep-link entry pages** (no in-app upstream; reached via external/shared URLs): [`/add-contact`](#page-add-contact), [`/agent/[agent_name]`](#page-agentagent_name), [`/apply/invite-code`](#page-applyinvite-code), [`/auth/github`](#page-authgithub), [`/callback/auto-login`](#page-callbackauto-login), [`/callback/chat`](#page-callbackchat), [`/callback/stripe/cancel`](#page-callbackstripecancel), [`/callback/stripe/success`](#page-callbackstripesuccess), [`/checkout`](#page-checkout), [`/credits`](#page-credits), [`/dev/group-message-cases`](#page-devgroup-message-cases), [`/discover-legacy`](#page-discover-legacy), [`/embed/tool-view`](#page-embedtool-view), [`/get-started`](#page-get-started), [`/i/[invite_code]`](#page-iinvite_code), [`/invite/[imUid]`](#page-inviteimuid), [`/invite/friend/[imUid]`](#page-invitefriendimuid), [`/link/[code]`](#page-linkcode), [`/modal`](#page-modal), [`/playbook`](#page-playbook), [`/presentation`](#page-presentation), [`/profile/settings/connectors`](#page-profilesettingsconnectors), [`/region-restricted`](#page-region-restricted), [`/search`](#page-search), [`/settings/creator-studio`](#page-settingscreator-studio), [`/settings/credit-usage`](#page-settingscredit-usage), [`/settings/help`](#page-settingshelp), [`/settings/invite-history`](#page-settingsinvite-history), [`/settings/knowledge-base`](#page-settingsknowledge-base), [`/settings/security`](#page-settingssecurity), [`/settings/translation`](#page-settingstranslation), [`/share/[id]`](#page-shareid), [`/support`](#page-support), [`/test-native`](#page-test-native), [`/ui`](#page-ui), [`/ui/openclaw-test`](#page-uiopenclaw-test), [`/ui/video-test`](#page-uivideo-test), [`/ui/wip`](#page-uiwip), [`/web`](#page-web).
- **Hub pages** (most outbound links): [`/settings`](#page-settings) (18), [`/`](#page-) (10), [`/discover`](#page-discover) (7), [`/i/[invite_code]`](#page-iinvite_code) (5), [`/post/[showcaseId]`](#page-postshowcaseid) (5), [`/pricing`](#page-pricing) (5).

## Feature areas

### Landing & Public Pages

Marketing and informational pages reachable without an account.

| Page | Name | What it does |
| --- | --- | --- |
| [`/`](#page-) | Home | The Teamily AI landing/home page introducing the personal and social AI agent OS for productivity and creativity. |
| [`/about`](#page-about) | About | An in-depth about page covering Teamily AI's vision for human-AI group intelligence, use cases, technical architecture, and co-founders. |
| [`/about/help-center`](#page-abouthelp-center) | Help Center | A localized help center answering common questions about billing, subscriptions, credits, and account usage on Teamily AI. |
| [`/about/privacy-policy`](#page-aboutprivacy-policy) | Privacy Policy | Teamily AI's privacy policy explaining how personal information is collected, used, protected, and retained, plus user privacy rights. |
| [`/about/refund-policy`](#page-aboutrefund-policy) | Refund Policy | Teamily AI's refund policy for subscriptions and services, covering billing and refund terms. |
| [`/about/terms-of-service`](#page-aboutterms-of-service) | Terms of Service | Teamily AI's terms of service outlining the rules and guidelines for using the platform, including subscriptions, billing, credits, and user responsibilities. |
| [`/download`](#page-download) | Download | Download landing page guiding users to get the Teamily apps for iOS, Android, Mac, and Windows. |
| [`/presentation`](#page-presentation) | Presentation Viewer | Opens a full-screen presentation viewer driven by name, sandboxUrl, and slide query parameters. |
| [`/region-restricted`](#page-region-restricted) | Region Restricted | Informs the user that the service is unavailable in their region due to compliance and regulatory restrictions. |
| [`/support`](#page-support) | Support | A support hub linking to the refund policy, terms of service, privacy policy, help center, and contact options. |

### Authentication & Onboarding

Sign-in, OAuth callbacks, invite-code redemption, and first-run onboarding. Most product pages redirect here when the user is signed out.

| Page | Name | What it does |
| --- | --- | --- |
| [`/apply/invite-code`](#page-applyinvite-code) | Apply Invite Code | Lets a user enter and verify an invite or promo code to claim a welcome credit, or skip to onboarding. |
| [`/auth/github`](#page-authgithub) | GitHub OAuth Callback | Handles the GitHub OAuth callback by exchanging the code for a login session and redirecting on success or failure. |
| [`/callback/auto-login`](#page-callbackauto-login) | Auto Login Callback | Redirect handler that completes passwordless login by verifying the email code from the URL, connecting the IM service, and redirecting the user back to their original destination. |
| [`/get-started`](#page-get-started) | Get Started | Redirects users to the credits center onboarding tab. |
| [`/i/[invite_code]`](#page-iinvite_code) | Invite Landing | An invite/referral landing page that validates an invite code, shows the inviter's profile and reward, and lets visitors connect or claim a welcome offer. |
| [`/login`](#page-login) | Login | The login page where users authenticate to access Teamily AI, with support for a legacy web2 login variant. |

### Chat & Messaging

The core IM workspace: conversations with friends, groups, and AI agents, plus message search and notifications.

| Page | Name | What it does |
| --- | --- | --- |
| [`/callback/chat`](#page-callbackchat) | Chat Callback | Post-login redirect handler that decodes the pending chat request, auto-subscribes the user to the selected agent, and forwards them to the chat page to start the conversation. |
| [`/chat`](#page-chat) | Chat | The main chat workspace that opens conversations from URL params and renders the active conversation's chat content. |
| [`/message-inbox`](#page-message-inbox) | Message Inbox | Displays the user's social notifications inbox. |
| [`/modal`](#page-modal) | Modal Route | Empty placeholder route used by the modal context router to render dialogs without a 404. |
| [`/search`](#page-search) | Global Search | Mobile-oriented global search screen with a query input and live search results. |
| [`/search/conversation`](#page-searchconversation) | Conversation Search | Shows search matches (messages, files, media, voice) within a specific conversation and opens the conversation at the selected message. |
| [`/web`](#page-web) | Visitor Chat | Visitor chat experience with a conversation sidebar and chat content; redirects logged-in users from root to /chat. |

### Contacts & Social Graph

Friend management, invitations, and user profiles.

| Page | Name | What it does |
| --- | --- | --- |
| [`/add-contact`](#page-add-contact) | Add Contact | A full-page form for adding a new contact, with a back button header wrapping the AddContactContent component. |
| [`/contact`](#page-contact) | Contacts | Contacts landing page that shows the alphabetized contact list with an index on mobile and defaults to the My Agents list on desktop. |
| [`/contact/my-agents`](#page-contactmy-agents) | My Agents | Lists the user's saved AI agents using the shared MyFriends contact view. |
| [`/contact/my-friends`](#page-contactmy-friends) | My Friends | Lists the user's friends using the shared MyFriends contact view. |
| [`/contact/phone-contacts`](#page-contactphone-contacts) | Phone Contacts | Renders the PhoneContacts view for importing and browsing contacts from the user's phone. |
| [`/invite/[imUid]`](#page-inviteimuid) | Accept Invitation | Lets a user accept an invitation identified by the inviter's IM user ID. |
| [`/invite/friend/[imUid]`](#page-invitefriendimuid) | Accept Friend Invitation | Lets a user accept a friend invitation identified by the inviter's IM user ID. |
| [`/invite/group/[groupId]`](#page-invitegroupgroupid) | Accept Group Invitation | Lets a user accept an invitation to join a group identified by its group ID. |
| [`/me`](#page-me) | My Profile Redirect | Redirects the signed-in user to their own profile page, or to profile edit if not logged in. |
| [`/profile/[uid]`](#page-profileuid) | User Profile | Displays a Teamily user's public profile by uid, including their AI showcases, posts, and saves, with SEO metadata and Person JSON-LD. |
| [`/profile/edit`](#page-profileedit) | Edit Profile | Lets the signed-in user edit their own Teamily profile details. |
| [`/profile/settings/connectors`](#page-profilesettingsconnectors) | Connectors Settings | Settings page for managing the user's third-party connectors and integrations. |

### AI Agents

Discovering, configuring, and reviewing AI agents.

| Page | Name | What it does |
| --- | --- | --- |
| [`/agent/[agent_name]`](#page-agentagent_name) | Agent Detail | Displays an agent's detail page (fetched by name) with an invite-code prompt, redirecting home if the agent is not found. |
| [`/agents/config/[agentId]`](#page-agentsconfigagentid) | Agent Settings | Renders the agent settings page for configuring a specific agent identified by agentId. |
| [`/discover-legacy`](#page-discover-legacy) | Discover Legacy | Legacy agent discovery page with search, category tabs, agent cards, and a rating/subscription drawer for browsing and subscribing to agents. |
| [`/discover-legacy/[id]`](#page-discover-legacyid) | Discover Legacy Agent Detail | Legacy per-agent detail view (used on mobile) showing the agent's information, ratings, and comments with the ability to submit a review. |
| [`/playbook`](#page-playbook) | Playbook | Showcases playbooks and guides for getting the most out of Teamily AI agents and team collaboration. |

### Social Discovery & Sharing

The public content feed: posts (showcases), groups, remixing, and shared conversation replays.

| Page | Name | What it does |
| --- | --- | --- |
| [`/discover`](#page-discover) | Discover | Discover feed home that surfaces onboarding, trending groups, recommended agents, and featured playbooks for users to explore the Teamily community. |
| [`/discover/groups`](#page-discovergroups) | Explore Groups | Full listing of trending community groups with category filters and join links that invite users into Teamily group chats. |
| [`/explore`](#page-explore) | Explore | Explore feed showcasing AI-generated creations, agents, and showcases from the Teamily community. |
| [`/explore/[postId]`](#page-explorepostid) | Explore Showcase Detail | Explore feed opened directly to a specific showcase post, with dynamic per-post metadata generated from the showcase's title and prompt. |
| [`/link/[code]`](#page-linkcode) | Share Link Viewer | Resolves a shared content code and renders it as an image, presentation, or framed page based on the detected content type. |
| [`/post/[showcaseId]`](#page-postshowcaseid) | Showcase Post | Detail page for an AI-generated showcase post, rendering the deliverable showcase with SEO metadata and JSON-LD. |
| [`/share/[id]`](#page-shareid) | Shared Thread | Renders a shared, read-only conversation thread by id, redirecting home if the thread is not found. |

### Billing, Credits & Subscription

Plans, checkout flows, credit rewards, and payment callbacks.

| Page | Name | What it does |
| --- | --- | --- |
| [`/callback/stripe/cancel`](#page-callbackstripecancel) | Stripe Cancel Callback | Stripe checkout cancellation redirect handler that releases the reserved payment session, shows a canceled dialog, and deep-links back to the desktop app when launched from there. |
| [`/callback/stripe/success`](#page-callbackstripesuccess) | Stripe Success Callback | Stripe checkout success redirect handler that tracks the purchase conversion, refreshes the subscription, celebrates with confetti, and deep-links back to the desktop app when applicable. |
| [`/checkout`](#page-checkout) | Checkout | A Paddle-powered checkout page showing an order summary and payment form for a selected price plan. |
| [`/checkout/success`](#page-checkoutsuccess) | Checkout Success | A payment-success confirmation page that fires confetti, refetches the subscription, and links back to the dashboard or pricing. |
| [`/credits`](#page-credits) | Credits | A redirect-only page that forwards users to the credits center settings tab. |
| [`/pricing`](#page-pricing) | Pricing | Compare Teamily AI plans and pricing, choose a plan, and manage subscriptions across supported payment providers. |

### Settings & Account

The settings hub and its subpages: profile, language, privacy, connectors, creator earnings, and usage.

| Page | Name | What it does |
| --- | --- | --- |
| [`/settings`](#page-settings) | Settings Home | The settings hub that lists grouped entries for account profile, creator rewards, plan/billing/usage, AI agent connectors, preferences, support, and sign-out, with a usage banner at the top. |
| [`/settings/affiliate`](#page-settingsaffiliate) | Affiliate Program | The affiliate incentive page showing commission earnings, withdrawable and pending balances, per-invitee breakdowns, and invite-sharing tools. |
| [`/settings/channels`](#page-settingschannels) | Channels | The OpenClaw channel management page where users connect and manage messaging channels for their AI agent. |
| [`/settings/connectors`](#page-settingsconnectors) | App Connectors | The account-level app connectors page where users connect and disconnect third-party integrations (Composio toolkits) for their AI agent. |
| [`/settings/creator-center`](#page-settingscreator-center) | Creator Center | The creator earnings page showing the cash balance, how-it-works steps, the engagement rewards ladder, recent earnings, and FAQs. |
| [`/settings/creator-studio`](#page-settingscreator-studio) | Creator Studio | The creator studio page, currently reusing the app connectors settings until the agents management module lands. |
| [`/settings/credit-usage`](#page-settingscredit-usage) | Credit Usage | The usage overview page that displays the user's credit consumption and plan usage data. |
| [`/settings/credits-center`](#page-settingscredits-center) | Credits Center | The credits center with tabbed views for onboarding-task rewards, inviting friends, and the user's credit balance and activity history. |
| [`/settings/help`](#page-settingshelp) | Help | Help settings page linking to the help center and opening a contact-us dialog with the support email. |
| [`/settings/invite-history`](#page-settingsinvite-history) | Invite History | Redirects to the credits center invite tab to show the user's invitation history. |
| [`/settings/knowledge-base`](#page-settingsknowledge-base) | Knowledge Base | Knowledge base management settings page, currently showing a coming-soon placeholder. |
| [`/settings/language`](#page-settingslanguage) | Language | Language settings page that lets the user choose the interface language. |
| [`/settings/privacy`](#page-settingsprivacy) | Privacy | Privacy settings page where the user manages their privacy preferences. |
| [`/settings/security`](#page-settingssecurity) | Security | Security settings page for managing account security, currently showing a coming-soon placeholder. |
| [`/settings/subscription`](#page-settingssubscription) | Subscription | Subscription settings page where the user views and manages their plan. |
| [`/settings/translation`](#page-settingstranslation) | Translation | Translation settings page that reuses the language settings component to configure language preferences. |
| [`/settings/usage`](#page-settingsusage) | Usage | Usage settings page showing the user's credit usage details. |
| [`/settings/withdraw`](#page-settingswithdraw) | Withdraw | Withdraw settings page showing withdrawable creator and affiliate earnings, withdrawal history, and a withdraw action gated by a feature flag. |

### Developer & Test Pages

Internal playgrounds and embeds; not part of normal user flows.

| Page | Name | What it does |
| --- | --- | --- |
| [`/dev/group-message-cases`](#page-devgroup-message-cases) | Group Message Cases | A developer page for previewing group-message render and streaming card layouts across selectable mock cases. |
| [`/embed/tool-view`](#page-embedtool-view) | Embedded Tool View | Renders a single agent tool-call view from a base64-encoded JSON payload passed via the data query parameter, intended for embedding. |
| [`/test-native`](#page-test-native) | Native WebView Test | Developer test harness that embeds the native-webview iframe and posts messages to it for debugging. |
| [`/ui`](#page-ui) | UI Design Reference | Internal design reference page showing the primary color palette (copyable) and wallet connection status. |
| [`/ui/openclaw-test`](#page-uiopenclaw-test) | OpenClaw Test | Internal test page to deploy, list, inspect, and destroy OpenClaw instances and connect to them via terminal. |
| [`/ui/video-test`](#page-uivideo-test) | Video Test | Internal test page for previewing videos and tracing their redirect chains, HTTP statuses, and video element lifecycle events. |
| [`/ui/wip`](#page-uiwip) | WIP Playbooks | Internal work-in-progress workbench for previewing UI playbooks such as usage overview, model routing, VM warnings, uploads, and audio preview. |

## Page reference

One entry per page, grouped by feature area. Upstream/downstream paths link to
their entries.

### Landing & Public Pages — details

#### Page /

**Home** — The Teamily AI landing/home page introducing the personal and social AI agent OS for productivity and creativity.

- Upstream: [`/agent/[agent_name]`](#page-agentagent_name), [`/apply/invite-code`](#page-applyinvite-code), [`/auth/github`](#page-authgithub), [`/callback/auto-login`](#page-callbackauto-login), [`/callback/chat`](#page-callbackchat), [`/callback/stripe/cancel`](#page-callbackstripecancel), [`/callback/stripe/success`](#page-callbackstripesuccess), [`/checkout/success`](#page-checkoutsuccess), [`/i/[invite_code]`](#page-iinvite_code), [`/link/[code]`](#page-linkcode), [`/search`](#page-search), [`/settings`](#page-settings), [`/settings/withdraw`](#page-settingswithdraw), [`/share/[id]`](#page-shareid)
- Downstream: [`/chat`](#page-chat), [`/discover`](#page-discover), [`/explore`](#page-explore), [`/login`](#page-login), [`/download`](#page-download), [`/pricing`](#page-pricing), [`/about`](#page-about), [`/about/help-center`](#page-abouthelp-center), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/terms-of-service`](#page-aboutterms-of-service)
- CTAs:
  - **Header nav tabs** (`tabs`, click) — Top navigation; each click fires a landing analytics event.
    - **Agents tab** (`link`, click) — Links to /discover?tab=agents.
    - **Discover tab** (`link`, click) — Links to /discover.
    - **Explore tab** (`link`, click) — Links to /explore.
    - **Blog tab** (`link`, click) — External link to the blog.
  - **Login** (`button`, click) — Primary header button that navigates to /login.
  - **Try on web** (`link`, click) — 'Web' pill in the hero that links to /login to use Teamily in the browser.
  - **Download app** (`link`, click) — Hero download pills for the native installers.
    - **iOS** (`link`, click) — Download the iOS app.
    - **Android** (`link`, click) — Download the Android app.
    - **macOS** (`link`, click) — Download the macOS app (Apple Silicon / Intel).
    - **Windows** (`link`, click) — Download the Windows installer.
  - **Mobile download dialog** (`dialog`, click) — Auto-opens on phone browsers prompting to download the mobile app.
    - **OK** (`button`, click) — Confirms and proceeds to download the mobile app.
    - **Ignore** (`button`, click) — Dismisses the dialog.

#### Page /about

**About** — An in-depth about page covering Teamily AI's vision for human-AI group intelligence, use cases, technical architecture, and co-founders.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: _none_
- CTAs: _none_

#### Page /about/help-center

**Help Center** — A localized help center answering common questions about billing, subscriptions, credits, and account usage on Teamily AI.

- Upstream: [`/`](#page-), [`/settings`](#page-settings), [`/settings/help`](#page-settingshelp), [`/settings/subscription`](#page-settingssubscription), [`/support`](#page-support)
- Downstream: _none_
- CTAs: _none_

#### Page /about/privacy-policy

**Privacy Policy** — Teamily AI's privacy policy explaining how personal information is collected, used, protected, and retained, plus user privacy rights.

- Upstream: [`/`](#page-), [`/i/[invite_code]`](#page-iinvite_code), [`/login`](#page-login), [`/pricing`](#page-pricing), [`/region-restricted`](#page-region-restricted), [`/settings`](#page-settings), [`/support`](#page-support)
- Downstream: _none_
- CTAs: _none_

#### Page /about/refund-policy

**Refund Policy** — Teamily AI's refund policy for subscriptions and services, covering billing and refund terms.

- Upstream: [`/`](#page-), [`/pricing`](#page-pricing), [`/settings`](#page-settings), [`/settings/subscription`](#page-settingssubscription), [`/support`](#page-support)
- Downstream: _none_
- CTAs: _none_

#### Page /about/terms-of-service

**Terms of Service** — Teamily AI's terms of service outlining the rules and guidelines for using the platform, including subscriptions, billing, credits, and user responsibilities.

- Upstream: [`/`](#page-), [`/i/[invite_code]`](#page-iinvite_code), [`/login`](#page-login), [`/pricing`](#page-pricing), [`/region-restricted`](#page-region-restricted), [`/settings`](#page-settings), [`/support`](#page-support)
- Downstream: _none_
- CTAs: _none_

#### Page /download

**Download** — Download landing page guiding users to get the Teamily apps for iOS, Android, Mac, and Windows.

- Upstream: [`/`](#page-)
- Downstream: [`/login`](#page-login)
- CTAs:
  - **Try on web** (`link`, click) — 'Web' pill linking to /login to try Teamily online instead of installing.
  - **Download links** (`link`, click) — Platform download links for iOS / Android / macOS (Apple Silicon / Intel dropdown) / Windows; desktop links hidden on phone browsers.

#### Page /presentation

**Presentation Viewer** — Opens a full-screen presentation viewer driven by name, sandboxUrl, and slide query parameters.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /region-restricted

**Region Restricted** — Informs the user that the service is unavailable in their region due to compliance and regulatory restrictions.

- Upstream: _none (direct/external entry)_
- Downstream: [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy)
- CTAs: _none_

#### Page /support

**Support** — A support hub linking to the refund policy, terms of service, privacy policy, help center, and contact options.

- Upstream: _none (direct/external entry)_
- Downstream: [`/about/refund-policy`](#page-aboutrefund-policy), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/help-center`](#page-abouthelp-center)
- CTAs:
  - **Refund Policy** (`link`, click) — Card linking to /about/refund-policy.
  - **Terms of Service** (`link`, click) — Card linking to /about/terms-of-service.
  - **Privacy Policy** (`link`, click) — Card linking to /about/privacy-policy.
  - **Help Center** (`link`, click) — Card linking to /about/help-center.
  - **Contact Us** (`link`, click) — Card opening mailto:contact@teamily.ai to reach the support team.

### Authentication & Onboarding — details

#### Page /apply/invite-code

**Apply Invite Code** — Lets a user enter and verify an invite or promo code to claim a welcome credit, or skip to onboarding.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](#page-settingscredits-center), [`/`](#page-)
- CTAs:
  - **Invite code input** (`input`, input) — Text field for entering an invite or promo code; Enter key submits.
  - **Apply button** (`button`, click) — Verifies the entered invite code and claims the welcome credit, then redirects to credits center (logged in) or home.
  - **Skip button** (`button`, click) — Skips invite code entry, clears any pending code, and continues to onboarding tasks (logged in) or home.

#### Page /auth/github

**GitHub OAuth Callback** — Handles the GitHub OAuth callback by exchanging the code for a login session and redirecting on success or failure.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-), [`/login`](#page-login)
- CTAs: _none_

#### Page /callback/auto-login

**Auto Login Callback** — Redirect handler that completes passwordless login by verifying the email code from the URL, connecting the IM service, and redirecting the user back to their original destination.

- Upstream: _none (direct/external entry)_
- Downstream: [`/login`](#page-login), [`/`](#page-)
- CTAs:
  - **Go to Login** (`button`, click) — Shown when auto-login fails; navigates back to the /login page to sign in manually.

#### Page /get-started

**Get Started** — Redirects users to the credits center onboarding tab.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](#page-settingscredits-center)
- CTAs: _none_

#### Page /i/[invite_code]

**Invite Landing** — An invite/referral landing page that validates an invite code, shows the inviter's profile and reward, and lets visitors connect or claim a welcome offer.

- Upstream: _none (direct/external entry)_
- Downstream: [`/login`](#page-login), [`/chat`](#page-chat), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/`](#page-)
- CTAs:
  - **Connect / Claim Welcome** (`button`, click) — Main invite CTA: redirects to /login if logged out, otherwise verifies the invite code, adds the inviter as IM friend and routes to /chat.
  - **Terms / Privacy links** (`link`, click) — Links to /about/terms-of-service and /about/privacy-policy below the CTA and in the footer.
  - **Go Home** (`link`, click) — Shown on the invalid-invite state; links back to /.

#### Page /login

**Login** — The login page where users authenticate to access Teamily AI, with support for a legacy web2 login variant.

- Upstream: [`/`](#page-), [`/agent/[agent_name]`](#page-agentagent_name), [`/auth/github`](#page-authgithub), [`/callback/auto-login`](#page-callbackauto-login), [`/checkout`](#page-checkout), [`/discover`](#page-discover), [`/discover-legacy`](#page-discover-legacy), [`/discover-legacy/[id]`](#page-discover-legacyid), [`/download`](#page-download), [`/explore`](#page-explore), [`/explore/[postId]`](#page-explorepostid), [`/i/[invite_code]`](#page-iinvite_code), [`/invite/[imUid]`](#page-inviteimuid), [`/invite/friend/[imUid]`](#page-invitefriendimuid), [`/invite/group/[groupId]`](#page-invitegroupgroupid), [`/playbook`](#page-playbook), [`/post/[showcaseId]`](#page-postshowcaseid), [`/pricing`](#page-pricing), [`/settings`](#page-settings)
- Downstream: [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy)
- CTAs:
  - **Continue with Google** (`button`, click) — Google Identity Services button; on success the credential is exchanged for a session.
  - **Auth method tabs** (`tabs`, click) — Switch between sign-in methods.
    - **Email tab** (`button`, click) — Selects the email sign-in flow.
    - **Phone tab** (`button`, click) — Selects the phone (SMS) sign-in flow.
  - **Email input** (`input`, input) — Email address field for the email auth flow.
  - **Continue with Email** (`button`, click) — Submits the email; checks the account and advances to the password / verification-code panel (sign-in or sign-up).
  - **Phone input** (`input`, input) — Country picker plus phone number field with per-country validation.
  - **Continue with Phone** (`button`, click) — Sends an SMS verification code and advances to the phone verify panel.
  - **Terms / Privacy links** (`link`, click) — 'By continuing' footer links to terms of service and privacy policy.

### Chat & Messaging — details

#### Page /callback/chat

**Chat Callback** — Post-login redirect handler that decodes the pending chat request, auto-subscribes the user to the selected agent, and forwards them to the chat page to start the conversation.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-), [`/chat`](#page-chat)
- CTAs: _none_

#### Page /chat

**Chat** — The main chat workspace that opens conversations from URL params and renders the active conversation's chat content.

- Upstream: [`/`](#page-), [`/callback/chat`](#page-callbackchat), [`/discover`](#page-discover), [`/discover-legacy`](#page-discover-legacy), [`/discover-legacy/[id]`](#page-discover-legacyid), [`/explore`](#page-explore), [`/explore/[postId]`](#page-explorepostid), [`/i/[invite_code]`](#page-iinvite_code), [`/playbook`](#page-playbook), [`/post/[showcaseId]`](#page-postshowcaseid), [`/search`](#page-search), [`/search/conversation`](#page-searchconversation), [`/settings/creator-center`](#page-settingscreator-center), [`/settings/credits-center`](#page-settingscredits-center), [`/web`](#page-web)
- Downstream: _none_
- CTAs:
  - **Send message** (`button`, click) — Sends the composed message (text/attachments) in the currently open conversation.

#### Page /message-inbox

**Message Inbox** — Displays the user's social notifications inbox.

- Upstream: [`/profile/[uid]`](#page-profileuid)
- Downstream: [`/profile/[uid]`](#page-profileuid), [`/post/[showcaseId]`](#page-postshowcaseid)
- CTAs:
  - **Open notification** (`button`, click) — Opens a notification row, marks it read, and for moderation-rejected posts opens the post editor modal.
  - **Refresh** (`button`, click) — Refetches the notifications feed and unread count.
  - **Try again** (`button`, click) — Retries loading the notifications feed when it failed to load.
  - **Edit rejected post** (`dialog`, click) — Post editor modal for a moderation-rejected post; lets the user revise and resave or delete the post.

#### Page /modal

**Modal Route** — Empty placeholder route used by the modal context router to render dialogs without a 404.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /search

**Global Search** — Mobile-oriented global search screen with a query input and live search results.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-), [`/search/conversation`](#page-searchconversation), [`/chat`](#page-chat)
- CTAs:
  - **Search input** (`input`, input) — Global search box (synced to the q query param) that searches contacts, groups, agents, messages, files, and media.
  - **Tabs** (`tabs`, click) — Filters results by category: All, Contacts, Groups, Agents, Messages, Files, Media.
  - **View all matches** (`button`, click) — Expands a result section to show all matches for that category or conversation.

#### Page /search/conversation

**Conversation Search** — Shows search matches (messages, files, media, voice) within a specific conversation and opens the conversation at the selected message.

- Upstream: [`/search`](#page-search)
- Downstream: [`/chat`](#page-chat)
- CTAs:
  - **Open matched message** (`button`, click) — Clicking a search hit opens the conversation scrolled to that message.

#### Page /web

**Visitor Chat** — Visitor chat experience with a conversation sidebar and chat content; redirects logged-in users from root to /chat.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#page-chat)
- CTAs: _none_

### Contacts & Social Graph — details

#### Page /add-contact

**Add Contact** — A full-page form for adding a new contact, with a back button header wrapping the AddContactContent component.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Download QR Code button** (`button`, click) — Downloads the personal invite-link QR code as a PNG image.
  - **Copy Link button** (`button`, click) — Copies the personal friend-invite link to the clipboard.
  - **Email search** (`input`, input) — Email input plus Search submit button; looks up whether a Teamily account exists for that email.
  - **Chat button** (`button`, click) — Shown when the found user is already a friend; opens an IM conversation with them.
  - **Invite button** (`button`, click) — Shown when the user exists but isn't a friend; sends a friend invitation email.

#### Page /contact

**Contacts** — Contacts landing page that shows the alphabetized contact list with an index on mobile and defaults to the My Agents list on desktop.

- Upstream: [`/`](#page-), [`/contact/my-agents`](#page-contactmy-agents), [`/contact/my-friends`](#page-contactmy-friends)
- Downstream: [`/contact/my-agents`](#page-contactmy-agents), [`/contact/my-friends`](#page-contactmy-friends), [`/contact/phone-contacts`](#page-contactphone-contacts)
- CTAs:
  - **Tabs** (`tabs`, click) — Sidebar/list nav switching between My Agents, My Friends, and Phone Contacts (desktop defaults to My Agents).
  - **Add Contact button** (`button`, click) — Plus icon in the header; opens the Add Contact modal on desktop or navigates to /add-contact on mobile.
  - **Contact item** (`dialog`, click) — Tapping a contact row (mobile list) opens the user info dialog for that friend.

#### Page /contact/my-agents

**My Agents** — Lists the user's saved AI agents using the shared MyFriends contact view.

- Upstream: [`/contact`](#page-contact)
- Downstream: [`/contact`](#page-contact)
- CTAs: _none_

#### Page /contact/my-friends

**My Friends** — Lists the user's friends using the shared MyFriends contact view.

- Upstream: [`/contact`](#page-contact)
- Downstream: [`/contact`](#page-contact)
- CTAs: _none_

#### Page /contact/phone-contacts

**Phone Contacts** — Renders the PhoneContacts view for importing and browsing contacts from the user's phone.

- Upstream: [`/contact`](#page-contact)
- Downstream: _none_
- CTAs:
  - **Invite button** (`button`, click) — On unregistered contacts; shares/SMS/copies an invite message with a personal invite link to join Teamily.
  - **Contact row** (`button`, click) — Tapping a registered contact opens an IM conversation; tapping their avatar opens the user info dialog.
  - **Download app links** (`link`, click) — Empty state shows iOS / Android buttons linking to the mobile app stores (contacts sync requires the app).

#### Page /invite/[imUid]

**Accept Invitation** — Lets a user accept an invitation identified by the inviter's IM user ID.

- Upstream: _none (direct/external entry)_
- Downstream: [`/login`](#page-login)
- CTAs:
  - **Accept Invitation button** (`button`, click) — Accepts the friend invitation (sends friend request) and opens a chat with the inviter; prompts login first if not signed in.
  - **Sign In button** (`button`, click) — Header button shown when not logged in that redirects to the login flow.

#### Page /invite/friend/[imUid]

**Accept Friend Invitation** — Lets a user accept a friend invitation identified by the inviter's IM user ID.

- Upstream: _none (direct/external entry)_
- Downstream: [`/login`](#page-login)
- CTAs:
  - **Accept Invitation button** (`button`, click) — Accepts the friend invitation (sends friend request) and opens a chat with the inviter; prompts login first if not signed in.
  - **Sign In button** (`button`, click) — Header button shown when not logged in that redirects to the login flow.

#### Page /invite/group/[groupId]

**Accept Group Invitation** — Lets a user accept an invitation to join a group identified by its group ID.

- Upstream: [`/discover`](#page-discover), [`/discover/groups`](#page-discovergroups)
- Downstream: [`/login`](#page-login)
- CTAs:
  - **Join Group button** (`button`, click) — Joins the invited group via the joinGroup API and then opens the group conversation; prompts login first if not signed in.
  - **Sign In button** (`button`, click) — Header button shown when not logged in that redirects to the login flow.

#### Page /me

**My Profile Redirect** — Redirects the signed-in user to their own profile page, or to profile edit if not logged in.

- Upstream: [`/`](#page-), [`/profile/[uid]`](#page-profileuid)
- Downstream: [`/profile/edit`](#page-profileedit), [`/profile/[uid]`](#page-profileuid)
- CTAs: _none_

#### Page /profile/[uid]

**User Profile** — Displays a Teamily user's public profile by uid, including their AI showcases, posts, and saves, with SEO metadata and Person JSON-LD.

- Upstream: [`/`](#page-), [`/agents/config/[agentId]`](#page-agentsconfigagentid), [`/discover`](#page-discover), [`/explore`](#page-explore), [`/explore/[postId]`](#page-explorepostid), [`/me`](#page-me), [`/message-inbox`](#page-message-inbox), [`/post/[showcaseId]`](#page-postshowcaseid)
- Downstream: [`/agents/config/[agentId]`](#page-agentsconfigagentid), [`/message-inbox`](#page-message-inbox), [`/me`](#page-me)
- CTAs:
  - **Follow button** (`button`, click) — Follows/unfollows the profile owner; label toggles between Follow and Following (hidden on agent profiles).
  - **Share profile button** (`button`, click) — Opens the share flow for this profile (also auto-triggered via ?share=1 query param).
  - **Message button** (`button`, click) — Starts a chat with the user or agent (adds friend if needed, then opens the IM conversation).
  - **Edit Profile button** (`button`, click) — Shown to the owner; navigates to /profile/edit (or agent settings for owned agent profiles).
  - **Tabs** (`tabs`, click) — Switches the feed between Posts / Saves / Likes; self view of Saves adds Public Posts / Chat History sub-tabs.
  - **Stats bar** (`dialog`, click) — Following/Followers counts open the follow list panel (dialog on desktop, full page on mobile).
  - **Notifications button** (`button`, click) — Owner-only bell that opens social notifications (dialog on desktop, /message-inbox on mobile).

#### Page /profile/edit

**Edit Profile** — Lets the signed-in user edit their own Teamily profile details.

- Upstream: [`/`](#page-), [`/me`](#page-me), [`/settings`](#page-settings), [`/settings/credits-center`](#page-settingscredits-center)
- Downstream: _none_
- CTAs:
  - **Change photo button** (`button`, click) — Opens a file picker, then an avatar crop dialog, and uploads the new profile photo.
  - **Save button** (`button`, click) — Saves all edited profile fields and navigates back; disabled until the draft is dirty.
  - **Name input** (`input`, input) — Edits display name with character counter.
  - **Username input** (`input`, input) — Edits @handle with local validation and change-quota limits.
  - **Bio input** (`input`, input) — Multi-line textarea for the profile bio.
  - **Tags input** (`input`, input) — Adds/removes profile tags via Enter, comma, or the plus button.
  - **Gender select** (`select`, click) — Popover selector for gender (Not set / Male / Female / Other).

#### Page /profile/settings/connectors

**Connectors Settings** — Settings page for managing the user's third-party connectors and integrations.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Search input** (`input`, input) — Filters the Composio connector toolkit list by keyword.
  - **Connect button** (`button`, click) — Creates a credential profile for the app and opens an OAuth popup to authorize the connection.
  - **Disconnect button** (`button`, click) — Deletes the app's credential profile(s) to disconnect the account-level connector.

### AI Agents — details

#### Page /agent/[agent_name]

**Agent Detail** — Displays an agent's detail page (fetched by name) with an invite-code prompt, redirecting home if the agent is not found.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-), [`/login`](#page-login)
- CTAs:
  - **Try Agent button** (`button`, click) — Sticky bottom button that opens a chat with this agent (optionally seeded with a prompt).
  - **Conversation starters** (`button`, click) — Clickable suggested prompts that start a chat with the agent using that prompt.
  - **Rate stars** (`button`, click) — Tap-to-rate 1-5 star control in the comment view (redirects to login if signed out).
  - **Submit comment button** (`button`, click) — Submits the star rating and comment text to the agent's review API.
  - **Write comment button** (`button`, click) — Pencil icon (or empty-comments card) that toggles into the rate-and-comment view.

#### Page /agents/config/[agentId]

**Agent Settings** — Renders the agent settings page for configuring a specific agent identified by agentId.

- Upstream: [`/profile/[uid]`](#page-profileuid)
- Downstream: [`/settings`](#page-settings), [`/profile/[uid]`](#page-profileuid)
- CTAs:
  - **Save button** (`button`, click) — Header button that saves changed agent name/description/avatar; disabled until dirty.
  - **Change Photo button** (`button`, click) — Opens a file picker and crop dialog to upload a new agent avatar.
  - **Delete button** (`dialog`, click) — Danger-zone button that opens a confirm dialog, then permanently deletes the agent and redirects to the owner's profile.
  - **Nickname input** (`input`, input) — Edits the agent's display name (required).
  - **Description input** (`input`, input) — Textarea editing the agent's description.

#### Page /discover-legacy

**Discover Legacy** — Legacy agent discovery page with search, category tabs, agent cards, and a rating/subscription drawer for browsing and subscribing to agents.

- Upstream: _none (direct/external entry)_
- Downstream: [`/discover-legacy/[id]`](#page-discover-legacyid), [`/discover`](#page-discover), [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Search agents** (`input`, input) — Debounced search bar that queries the agent discover API by name.
  - **Category tabs** (`tabs`, click) — Category filter: All / Latest / backend categories / My Agents (when logged in), synced to the ?category query param.
  - **Subscribe toggle** (`toggle`, click) — Subscribe/unsubscribe button on each agent card with optimistic update and rollback on failure.
  - **Open agent detail** (`dialog`, click) — Clicking an agent card opens the agent rating drawer (desktop) or navigates to the detail page (mobile).
  - **Try Agent** (`button`, click) — Button in the agent detail drawer that starts a chat with the agent.
  - **Submit rating & comment** (`button`, click) — Star rating plus comment textarea in the drawer; Submit posts or updates the user's review.
  - **Copy share link** (`button`, click) — Copies the agent's share URL to the clipboard.
  - **Example prompt chips** (`button`, click) — Conversation-starter chips that launch a chat with the agent using that prompt.

#### Page /discover-legacy/[id]

**Discover Legacy Agent Detail** — Legacy per-agent detail view (used on mobile) showing the agent's information, ratings, and comments with the ability to submit a review.

- Upstream: [`/discover-legacy`](#page-discover-legacy)
- Downstream: [`/discover`](#page-discover), [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Try Agent** (`button`, click) — Starts a chat with this agent.
  - **Submit rating & comment** (`button`, click) — Star rating plus comment textarea; Submit creates or updates the user's review for the agent.
  - **Copy share link** (`button`, click) — Copies the agent's share URL to the clipboard.
  - **Example prompt chips** (`button`, click) — Conversation-starter chips that launch a chat with the agent using the selected prompt.

#### Page /playbook

**Playbook** — Showcases playbooks and guides for getting the most out of Teamily AI agents and team collaboration.

- Upstream: _none (direct/external entry)_
- Downstream: [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Category filter** (`tabs`, click) — Sticky category pills (All + fetched categories) that filter the playbook masonry grid.
  - **Try** (`button`, click) — On-card hover button that opens an agent chat preloaded with the playbook's agent, prompt and attachments.
  - **Replay** (`link`, click) — On-card button that opens the playbook's replay_url in a new tab to watch the recorded run.

### Social Discovery & Sharing — details

#### Page /discover

**Discover** — Discover feed home that surfaces onboarding, trending groups, recommended agents, and featured playbooks for users to explore the Teamily community.

- Upstream: [`/`](#page-), [`/discover-legacy`](#page-discover-legacy), [`/discover-legacy/[id]`](#page-discover-legacyid), [`/discover/groups`](#page-discovergroups), [`/post/[showcaseId]`](#page-postshowcaseid), [`/settings/creator-center`](#page-settingscreator-center), [`/settings/credits-center`](#page-settingscredits-center)
- Downstream: [`/post/[showcaseId]`](#page-postshowcaseid), [`/profile/[uid]`](#page-profileuid), [`/chat`](#page-chat), [`/login`](#page-login), [`/settings/credits-center`](#page-settingscredits-center), [`/discover/groups`](#page-discovergroups), [`/invite/group/[groupId]`](#page-invitegroupgroupid)
- CTAs:
  - **Tabs** (`tabs`, click) — Switch the discover feed between sections.
    - **Following tab** (`button`, click) — Shows posts from accounts the user follows.
    - **Feeds tab** (`button`, click) — Shows the general discover feed.
    - **Agents tab** (`button`, click) — Shows recommended agents.
    - **Groups tab** (`button`, click) — Shows trending groups.
  - **Search posts** (`input`, input) — Filters the discover feed posts by keyword (shown on Following/Feeds tabs).
  - **Category pills** (`select`, click) — Horizontal category pill filter for feed posts; tapping the active pill again refreshes the feed.
  - **Post actions** (`button`, click) — Like, comment, share, remix, and bookmark buttons on each feed post card; clicking the card opens the post detail.
  - **Chat with agent** (`button`, click) — Chat button on each agent card (Agents tab) that starts a conversation with that agent.
  - **Join group** (`link`, click) — Group card with a Join badge (Groups tab) that opens the group's invite URL.
  - **Onboarding rewards banner** (`button`, click) — Dismissible banner showing first-week task progress; clicking navigates to the rewards page.

#### Page /discover/groups

**Explore Groups** — Full listing of trending community groups with category filters and join links that invite users into Teamily group chats.

- Upstream: [`/discover`](#page-discover)
- Downstream: [`/discover`](#page-discover), [`/invite/group/[groupId]`](#page-invitegroupgroupid)
- CTAs:
  - **Category pills** (`select`, click) — Filter the group list by category: All / Daily / Share / Explore / Find / Community / Investment / Events / Other.
  - **Join group** (`link`, click) — Group card with a Join badge that opens the group's invite URL in a new tab.

#### Page /explore

**Explore** — Explore feed showcasing AI-generated creations, agents, and showcases from the Teamily community.

- Upstream: [`/`](#page-)
- Downstream: [`/explore/[postId]`](#page-explorepostid), [`/profile/[uid]`](#page-profileuid), [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Like** (`button`, click) — Like/unlike the current post with optimistic count update (requires login).
  - **Save** (`button`, click) — Bookmark/unbookmark the current post (requires login).
  - **Comments** (`dialog`, click) — Open the comments drawer for the post and submit new comments.
  - **Share** (`dialog`, click) — Open the share sheet with the post's snapshot and public /post URL.
  - **Remix** (`dialog`, click) — Open the Remix dialog to recreate the showcase from its original prompt.
  - **Follow author** (`toggle`, click) — Follow/unfollow the post's author.
  - **Prev/next navigation** (`button`, click) — Navigate to the previous or next post in the vertical snap-scroll explore feed.
  - **Author profile** (`button`, click) — Clicking the author's name/avatar opens their profile.

#### Page /explore/[postId]

**Explore Showcase Detail** — Explore feed opened directly to a specific showcase post, with dynamic per-post metadata generated from the showcase's title and prompt.

- Upstream: [`/explore`](#page-explore)
- Downstream: [`/explore/[postId]`](#page-explorepostid), [`/profile/[uid]`](#page-profileuid), [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Like** (`button`, click) — Like/unlike the current post with optimistic count update (requires login).
  - **Save** (`button`, click) — Bookmark/unbookmark the current post (requires login).
  - **Comments** (`dialog`, click) — Open the comments drawer for the post and submit new comments.
  - **Share** (`dialog`, click) — Open the share sheet with the post's snapshot and public /post URL.
  - **Remix** (`dialog`, click) — Open the Remix dialog to recreate the showcase from its original prompt (auto-opens from a pending remix intent).
  - **Follow author** (`toggle`, click) — Follow/unfollow the post's author.
  - **Prev/next navigation** (`button`, click) — Navigate to the previous or next post in the vertical snap-scroll explore feed.
  - **Author profile** (`button`, click) — Clicking the author's name/avatar opens their profile.

#### Page /link/[code]

**Share Link Viewer** — Resolves a shared content code and renders it as an image, presentation, or framed page based on the detected content type.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-)
- CTAs:
  - **Copy Share Link button** (`button`, click) — Copies the short share URL (/link/{code}) to the clipboard with a success toast.
  - **Open button** (`link`, click) — Opens the Teamily AI home page in a new tab (Made with Teamily CTA).
  - **Toggle top bar** (`toggle`, click) — Collapses or restores the share viewer top bar for a fullscreen-like view of the shared content.

#### Page /post/[showcaseId]

**Showcase Post** — Detail page for an AI-generated showcase post, rendering the deliverable showcase with SEO metadata and JSON-LD.

- Upstream: [`/discover`](#page-discover), [`/message-inbox`](#page-message-inbox)
- Downstream: [`/discover`](#page-discover), [`/profile/[uid]`](#page-profileuid), [`/post/[showcaseId]`](#page-postshowcaseid), [`/chat`](#page-chat), [`/login`](#page-login)
- CTAs:
  - **Remix** (`dialog`, click) — Open the Remix dialog to recreate the showcase from its prompt (also triggered by a pending remix intent).
  - **Like** (`button`, click) — Like/unlike the showcase post with synced engagement counts.
  - **Save** (`button`, click) — Bookmark/unbookmark the showcase post.
  - **Share** (`dialog`, click) — Open the share sheet with the showcase snapshot and its public URL.
  - **Submit comment** (`input`, input) — Comment composer that posts a new comment or reply; comments can be liked/unliked.
  - **Follow author** (`toggle`, click) — Follow/unfollow the showcase author.
  - **Copy prompt** (`button`, click) — Copy the showcase's original prompt to the clipboard.

#### Page /share/[id]

**Shared Thread** — Renders a shared, read-only conversation thread by id, redirecting home if the thread is not found.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-)
- CTAs:
  - **Playback controls** (`button`, click) — Floating replay controls for the shared read-only conversation: play/pause, previous/next message, skip to end, and playback speed.

### Billing, Credits & Subscription — details

#### Page /callback/stripe/cancel

**Stripe Cancel Callback** — Stripe checkout cancellation redirect handler that releases the reserved payment session, shows a canceled dialog, and deep-links back to the desktop app when launched from there.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-)
- CTAs:
  - **OK** (`button`, click) — Closes the payment-canceled dialog, refetches subscription state, and redirects to the home page.

#### Page /callback/stripe/success

**Stripe Success Callback** — Stripe checkout success redirect handler that tracks the purchase conversion, refreshes the subscription, celebrates with confetti, and deep-links back to the desktop app when applicable.

- Upstream: _none (direct/external entry)_
- Downstream: [`/`](#page-)
- CTAs:
  - **OK** (`button`, click) — Closes the payment-succeeded dialog, refetches subscription state, and redirects to the home page.

#### Page /checkout

**Checkout** — A Paddle-powered checkout page showing an order summary and payment form for a selected price plan.

- Upstream: _none (direct/external entry)_
- Downstream: [`/pricing`](#page-pricing), [`/checkout/success`](#page-checkoutsuccess), [`/login`](#page-login)
- CTAs:
  - **Back to Pricing** (`link`, click) — Returns to the /pricing page from the embedded Paddle checkout.

#### Page /checkout/success

**Checkout Success** — A payment-success confirmation page that fires confetti, refetches the subscription, and links back to the dashboard or pricing.

- Upstream: [`/checkout`](#page-checkout)
- Downstream: [`/`](#page-), [`/pricing`](#page-pricing)
- CTAs:
  - **Go to Dashboard** (`link`, click) — Navigates to the home dashboard after a successful subscription payment.
  - **View Plans** (`link`, click) — Navigates to the /pricing page to review subscription plans.

#### Page /credits

**Credits** — A redirect-only page that forwards users to the credits center settings tab.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](#page-settingscredits-center)
- CTAs: _none_

#### Page /pricing

**Pricing** — Compare Teamily AI plans and pricing, choose a plan, and manage subscriptions across supported payment providers.

- Upstream: [`/`](#page-), [`/checkout`](#page-checkout), [`/checkout/success`](#page-checkoutsuccess), [`/settings`](#page-settings), [`/settings/channels`](#page-settingschannels), [`/settings/credits-center`](#page-settingscredits-center), [`/settings/subscription`](#page-settingssubscription)
- Downstream: [`/login`](#page-login), [`/settings/credits-center`](#page-settingscredits-center), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/refund-policy`](#page-aboutrefund-policy)
- CTAs:
  - **Billing cycle tabs** (`tabs`, click) — Billing-cycle toggle synced to the ?billingCycle query param.
    - **Monthly** (`button`, click) — Switches plans to monthly pricing.
    - **Annual** (`button`, click) — Switches plans to annual pricing (shows 'save 20%').
  - **Choose Plan** (`button`, click) — Per-plan CTA whose label varies by state (Start Free Trial, Upgrade, Your Current Plan, etc.); starts a Stripe Checkout session for eligible users.
  - **Discount toggle** (`toggle`, click) — Per-card option to apply reward credits or the Creator 90%-off perk to the first checkout (monthly plans only).
  - **Manage Subscription** (`button`, click) — For logged-in paid subscribers: opens the Stripe customer portal to manage, invoice, or cancel the plan.
  - **Help Center tabs** (`tabs`, click) — FAQ category tabs; each shows an accordion of questions.
    - **Billing tab** (`button`, click) — Billing-related FAQ accordion.
    - **Usage tab** (`button`, click) — Usage-related FAQ accordion.
    - **Support tab** (`button`, click) — Support FAQ accordion (includes the policy links).
  - **Policy links** (`link`, click) — Legal links inside the Support FAQ: terms of service, privacy policy, refund policy.

### Settings & Account — details

#### Page /settings

**Settings Home** — The settings hub that lists grouped entries for account profile, creator rewards, plan/billing/usage, AI agent connectors, preferences, support, and sign-out, with a usage banner at the top.

- Upstream: [`/`](#page-), [`/agents/config/[agentId]`](#page-agentsconfigagentid)
- Downstream: [`/profile/edit`](#page-profileedit), [`/settings/creator-center`](#page-settingscreator-center), [`/settings/credits-center`](#page-settingscredits-center), [`/settings/affiliate`](#page-settingsaffiliate), [`/settings/subscription`](#page-settingssubscription), [`/settings/usage`](#page-settingsusage), [`/settings/language`](#page-settingslanguage), [`/settings/connectors`](#page-settingsconnectors), [`/settings/channels`](#page-settingschannels), [`/settings/privacy`](#page-settingsprivacy), [`/about/help-center`](#page-abouthelp-center), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/refund-policy`](#page-aboutrefund-policy), [`/about`](#page-about), [`/pricing`](#page-pricing), [`/login`](#page-login), [`/`](#page-)
- CTAs:
  - **Try Plus / Manage button** (`button`, click) — Usage banner CTA: routes free users to /pricing to upgrade, or paid Stripe users to /settings/subscription to manage their plan.
  - **Settings rows** (`link`, click) — Tappable rows navigating to settings subpages: Account Profile, Creator Center, Credit Center, Incentive Program, Plan & Billing, Usage, Language, App Connectors, OpenClaw Management, Privacy, Help Center, legal pages, and About.
  - **Sign Out button** (`button`, click) — Logs the user out and returns to home (shows Sign In and routes to /login when logged out).
  - **Social links** (`link`, click) — X, LinkedIn, and Discord icons opening the product's social pages in a new tab.

#### Page /settings/affiliate

**Affiliate Program** — The affiliate incentive page showing commission earnings, withdrawable and pending balances, per-invitee breakdowns, and invite-sharing tools.

- Upstream: [`/`](#page-), [`/settings`](#page-settings), [`/settings/withdraw`](#page-settingswithdraw)
- Downstream: [`/settings/withdraw`](#page-settingswithdraw)
- CTAs:
  - **Withdraw button** (`button`, click) — On the earnings hero; routes to /settings/withdraw, or opens a 'coming soon' dialog when the withdraw feature flag is off.
  - **Copy invite link button** (`button`, click) — Copies the personal invite link to the clipboard and fires an invite-link-copied analytics event.
  - **QR code button** (`dialog`, click) — Opens a dialog showing a QR code for the invite link/code.
  - **Email invite button** (`dialog`, click) — Opens a dialog to send the invite by email.
  - **Social share buttons** (`link`, click) — Share the invite link via X, Facebook, LinkedIn, or SMS.

#### Page /settings/channels

**Channels** — The OpenClaw channel management page where users connect and manage messaging channels for their AI agent.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: [`/pricing`](#page-pricing)
- CTAs:
  - **Show/Hide API key button** (`button`, click) — Toggles the Teamily API key between masked and plain text.
  - **Copy API key button** (`button`, click) — Copies the Teamily API key to the clipboard with a success/error toast.
  - **Copy connect script button** (`button`, click) — Copies the OpenClaw quick-connect shell script shown in the code block.
  - **Manage Subscription / Renew Now button** (`button`, click) — Shown in the platform-VM warning card when the subscription is canceled/expired; closes settings and routes to /pricing.
  - **Export Data button** (`button`, click) — Secondary action in the platform-VM warning card to export VM data before deletion.

#### Page /settings/connectors

**App Connectors** — The account-level app connectors page where users connect and disconnect third-party integrations (Composio toolkits) for their AI agent.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: _none_
- CTAs:
  - **Search connectors input** (`input`, input) — Filters the Composio toolkit list by search term.
  - **Connect button** (`button`, click) — Per-toolkit; creates a Composio credential profile and opens the OAuth flow in a popup window.
  - **Disconnect button** (`button`, click) — Per connected toolkit; deletes all credential profiles for that toolkit and refreshes the list.

#### Page /settings/creator-center

**Creator Center** — The creator earnings page showing the cash balance, how-it-works steps, the engagement rewards ladder, recent earnings, and FAQs.

- Upstream: [`/`](#page-), [`/settings`](#page-settings), [`/settings/withdraw`](#page-settingswithdraw)
- Downstream: [`/settings/withdraw`](#page-settingswithdraw), [`/chat`](#page-chat), [`/discover`](#page-discover)
- CTAs:
  - **Withdraw button** (`button`, click) — On the earnings hero; routes to /settings/withdraw, or opens a 'coming soon' dialog when the withdraw feature flag is off.
  - **Start creating buttons** (`button`, click) — Three CTAs: Create with Personal AI (links to /chat), Create with Agent (opens the Create Agent modal), and Remix Your Own (links to /discover).
  - **FAQ accordion** (`button`, click) — Expandable FAQ items about creator earnings.

#### Page /settings/creator-studio

**Creator Studio** — The creator studio page, currently reusing the app connectors settings until the agents management module lands.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Search connectors input** (`input`, input) — Filters the Composio toolkit list by search term (page reuses the Connectors settings component).
  - **Connect button** (`button`, click) — Per-toolkit; creates a Composio credential profile and opens the OAuth flow in a popup window.
  - **Disconnect button** (`button`, click) — Per connected toolkit; deletes all credential profiles for that toolkit and refreshes the list.

#### Page /settings/credit-usage

**Credit Usage** — The usage overview page that displays the user's credit consumption and plan usage data.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **On-demand toggle** (`toggle`, click) — Enables/disables on-demand usage billing; turning it on first opens a confirmation dialog, turning it off disables immediately.
  - **Enable confirmation dialog** (`dialog`, click) — Confirms enabling on-demand billing (Enable / Cancel) and applies the previous or default $100 monthly limit.
  - **Monthly limit input** (`input`, input) — Number input for the on-demand monthly spend limit; clamped to $10-$9999 and saved on blur.
  - **Retry Payment button** (`button`, click) — Shown when on-demand payment is suspended; retries charging the unpaid balance.

#### Page /settings/credits-center

**Credits Center** — The credits center with tabbed views for onboarding-task rewards, inviting friends, and the user's credit balance and activity history.

- Upstream: [`/`](#page-), [`/apply/invite-code`](#page-applyinvite-code), [`/credits`](#page-credits), [`/discover`](#page-discover), [`/get-started`](#page-get-started), [`/pricing`](#page-pricing), [`/settings`](#page-settings), [`/settings/invite-history`](#page-settingsinvite-history)
- Downstream: [`/pricing`](#page-pricing), [`/discover`](#page-discover), [`/chat`](#page-chat), [`/profile/edit`](#page-profileedit)
- CTAs:
  - **Tabs** (`tabs`, click) — Switches between views, synced to the ?tab= query param.
    - **Onboarding Tasks tab** (`button`, click) — Shows first-week onboarding tasks that earn credits.
    - **Invite Friends tab** (`button`, click) — Shows the invite link, code redemption, and share options.
    - **My Credits tab** (`button`, click) — Shows the credit balance and activity history.
  - **Buy Plus button** (`button`, click) — In the first-7-days card on the Onboarding tab; routes to the pricing page to buy Plus using earned credits.
  - **Apply Credits button** (`button`, click) — Routes to the pricing page to apply credit balance at checkout.
  - **Task cards** (`button`, click) — Onboarding task rows; clicking an incomplete task dispatches its action (e.g. chat, create agent, publish post) to earn credits.
  - **Apply invite code input** (`input`, input) — Input plus Apply button to redeem a friend's invite code; verifies the code and shows success/error toasts.
  - **Copy invite link button** (`button`, click) — Copies the personal invite link to the clipboard (Invite tab).
  - **Share invite buttons** (`button`, click) — QR code and Email dialogs plus X/Facebook/LinkedIn/SMS share links for the invite link.

#### Page /settings/help

**Help** — Help settings page linking to the help center and opening a contact-us dialog with the support email.

- Upstream: _none (direct/external entry)_
- Downstream: [`/about/help-center`](#page-abouthelp-center)
- CTAs:
  - **Help Center** (`link`, click) — Settings item linking to the /about/help-center page.
  - **Contact Us** (`dialog`, click) — Opens a contact dialog showing the direct support email (mailto:contact@teamily.ai).

#### Page /settings/invite-history

**Invite History** — Redirects to the credits center invite tab to show the user's invitation history.

- Upstream: _none (direct/external entry)_
- Downstream: [`/settings/credits-center`](#page-settingscredits-center)
- CTAs: _none_

#### Page /settings/knowledge-base

**Knowledge Base** — Knowledge base management settings page, currently showing a coming-soon placeholder.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /settings/language

**Language** — Language settings page that lets the user choose the interface language.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: _none_
- CTAs:
  - **System Language** (`select`, click) — Selects the app UI locale, persisted via the locale context.
  - **Chat Language** (`select`, click) — Selects the target language for chat message auto-translation, saved to the translation service.
  - **Auto Translate** (`toggle`, click) — Enables or disables automatic translation of incoming chat messages.

#### Page /settings/privacy

**Privacy** — Privacy settings page where the user manages their privacy preferences.

- Upstream: [`/settings`](#page-settings)
- Downstream: _none_
- CTAs:
  - **Likes Visible** (`toggle`, click) — Controls whether your liked posts are publicly visible on your profile.
  - **Bookmarks Visible** (`toggle`, click) — Controls whether your saved/bookmarked posts are publicly visible on your profile.
  - **Save Changes** (`button`, click) — Saves the changed privacy toggles via the privacy API; disabled until there are unsaved changes.

#### Page /settings/security

**Security** — Security settings page for managing account security, currently showing a coming-soon placeholder.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /settings/subscription

**Subscription** — Subscription settings page where the user views and manages their plan.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: [`/pricing`](#page-pricing), [`/about/help-center`](#page-abouthelp-center), [`/about/refund-policy`](#page-aboutrefund-policy)
- CTAs:
  - **Upgrade** (`button`, click) — Navigates to /pricing to upgrade the current plan (shown for non-Pro, trialing, or canceled users).
  - **Change Plan** (`button`, click) — Navigates to /pricing to switch plans (shown for active paid subscribers).
  - **Resume Plan** (`button`, click) — Opens the Stripe customer portal in a new tab to resume a canceled subscription.
  - **Manage Billing** (`button`, click) — Opens the Stripe customer portal to manage payment method, invoices, and cancellation.
  - **Manage on Device** (`button`, click) — Opens App Store or Google Play subscription management for store-managed subscriptions.
  - **View Plans** (`button`, click) — Navigates to /pricing from the free-plan promo card.
  - **Help links** (`link`, click) — Quick links to /pricing (View All Plans), /about/help-center, and /about/refund-policy.

#### Page /settings/translation

**Translation** — Translation settings page that reuses the language settings component to configure language preferences.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **System Language** (`select`, click) — Selects the app UI locale, persisted via the locale context.
  - **Chat Language** (`select`, click) — Selects the target language for chat message auto-translation, saved to the translation service.
  - **Auto Translate** (`toggle`, click) — Enables or disables automatic translation of incoming chat messages.

#### Page /settings/usage

**Usage** — Usage settings page showing the user's credit usage details.

- Upstream: [`/`](#page-), [`/settings`](#page-settings)
- Downstream: _none_
- CTAs:
  - **Enable On-Demand** (`toggle`, click) — Turns on-demand (pay-as-you-go) usage on; enabling opens a confirmation dialog, disabling takes effect immediately.
  - **Enable Confirmation** (`dialog`, click) — Confirmation dialog with Cancel/Enable actions that activates on-demand billing with the previous or default monthly limit.
  - **Monthly Limit** (`input`, input) — Number input ($10-$9999) that sets the on-demand monthly spend limit on blur.
  - **Retry Payment** (`button`, click) — Retries the failed on-demand charge when payment is suspended due to an unpaid balance.

#### Page /settings/withdraw

**Withdraw** — Withdraw settings page showing withdrawable creator and affiliate earnings, withdrawal history, and a withdraw action gated by a feature flag.

- Upstream: [`/settings/affiliate`](#page-settingsaffiliate), [`/settings/creator-center`](#page-settingscreator-center)
- Downstream: [`/settings/creator-center`](#page-settingscreator-center), [`/settings/affiliate`](#page-settingsaffiliate), [`/`](#page-)
- CTAs:
  - **Withdraw All** (`button`, click) — Opens the withdraw dialog to cash out the total withdrawable balance; labeled 'Link Card and Withdraw' when no Stripe payout account is connected.
  - **Withdraw Dialog** (`dialog`, click) — Three-step modal: connect a Stripe payout account, enter the withdrawal amount, then a success screen.
  - **Earnings source rows** (`link`, click) — Rows linking to /settings/creator-center and /settings/affiliate.

### Developer & Test Pages — details

#### Page /dev/group-message-cases

**Group Message Cases** — A developer page for previewing group-message render and streaming card layouts across selectable mock cases.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Case select** (`select`, click) — Dropdown of mock case IDs (loading, completed, running/streaming, failed, etc.) that switches the rendered GroupMessage mock state.

#### Page /embed/tool-view

**Embedded Tool View** — Renders a single agent tool-call view from a base64-encoded JSON payload passed via the data query parameter, intended for embedding.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /test-native

**Native WebView Test** — Developer test harness that embeds the native-webview iframe and posts messages to it for debugging.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Send Message** (`button`, click) — Opens a browser prompt for text and postMessage()s it to the embedded /native-webview iframe.

#### Page /ui

**UI Design Reference** — Internal design reference page showing the primary color palette (copyable) and wallet connection status.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs: _none_

#### Page /ui/openclaw-test

**OpenClaw Test** — Internal test page to deploy, list, inspect, and destroy OpenClaw instances and connect to them via terminal.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Deployment name input** (`input`, input) — Text field for naming the new OpenClaw deployment.
  - **Template select** (`select`, click) — Dropdown to choose an OpenClaw template for the new deployment.
  - **Deploy button** (`button`, click) — Creates a new OpenClaw deployment on GCP and polls until it reaches running status.
  - **Select deployment** (`button`, click) — Clicking a deployment in the list makes it active, showing its details, status, and terminal/settings panel.
  - **Destroy deployment** (`dialog`, click) — Opens a confirmation dialog; confirming permanently deletes the GCP VM and its data.
  - **Refresh deployments** (`button`, click) — Refetches the deployment list from the OpenClaw API.

#### Page /ui/video-test

**Video Test** — Internal test page for previewing videos and tracing their redirect chains, HTTP statuses, and video element lifecycle events.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Mode tabs** (`tabs`, click) — Switches between test modes: PhotoSlider and Native Video.
  - **Preview buttons** (`button`, click) — Open the PhotoSlider video preview overlay in normal or gesture-isolated mode.
  - **Video URL input** (`input`, input) — Textarea for the video URL to test; preset buttons fill in sample URLs and Enter triggers Load.
  - **Load button** (`button`, click) — Sets the video element src to the entered URL and traces native loading lifecycle events into the log.
  - **Probe button** (`button`, click) — Runs a server-side fetch that follows the URL's redirect chain and logs each hop's status and headers.
  - **Clear Log button** (`button`, click) — Clears all entries from the event log panel.
  - **Download Log button** (`button`, click) — Downloads the event log as a plain-text file.

#### Page /ui/wip

**WIP Playbooks** — Internal work-in-progress workbench for previewing UI playbooks such as usage overview, model routing, VM warnings, uploads, and audio preview.

- Upstream: _none (direct/external entry)_
- Downstream: _none_
- CTAs:
  - **Playbook nav** (`tabs`, click) — Sidebar list that switches the active test playbook: Usage Overview, Model Routing Table, Platform VM Warning, Bunny Storage Upload, Audio Preview.
  - **Toggle controls** (`toggle`, click) — Shows or hides the active playbook's right-hand controls panel.
  - **Toggle sidebar** (`toggle`, click) — Collapses or expands the playbook navigation sidebar.

## Shared layouts & chrome

Layout components (`layout.tsx`) wrap one or more route segments and render
the persistent chrome — headers, sidebars, tab bars, and providers — shared by
the pages beneath them. Their CTAs are the app-wide navigation controls.

### Layout / — Root Layout

**Root Layout** — The top-level App Router layout wrapping every route — sets up fonts, global providers, analytics, JSON-LD structured data, viewport/theme-color, and the base HTML document. Renders no visible chrome of its own.

- Wraps: `app`
- Downstream: _none_
- CTAs: _none_

### Layout /(dashboard) — Dashboard Layout (App Shell)

**Dashboard Layout (App Shell)** — The signed-in app shell wrapping every dashboard route. On desktop it renders the left Sidebar (primary nav + footer utilities + info menu); on mobile it renders the bottom Tab bar on primary pages. It also hosts the modal slot, the mobile download-app dialog, and the web first-run tour.

- Wraps: `app/(dashboard)`
- Downstream: [`/chat`](#page-chat), [`/discover`](#page-discover), [`/explore`](#page-explore), [`/contact`](#page-contact), [`/me`](#page-me), [`/download`](#page-download), [`/settings`](#page-settings), [`/settings/language`](#page-settingslanguage), [`/credits`](#page-credits), [`/get-started`](#page-get-started), [`/pricing`](#page-pricing), [`/about`](#page-about), [`/about/terms-of-service`](#page-aboutterms-of-service), [`/about/privacy-policy`](#page-aboutprivacy-policy), [`/about/help-center`](#page-abouthelp-center)
- CTAs:
  - **Sidebar** (`nav`, click) — Desktop left navigation rail with the primary destinations, footer utilities, and the user/info menu.
    - **Chat nav** (`link`, click) — Opens /chat (or /login when signed out); shows an unread-message badge.
    - **Discover nav** (`link`, click) — Opens /discover (agent + content discovery).
    - **Explore nav** (`link`, click) — Opens /explore (the social feed).
    - **Contacts nav** (`link`, click) — Opens /contact; shows a badge for pending friend applications.
    - **Create Agent** (`button`, click) — Entry point to create a new agent (opens the create flow).
    - **Me nav** (`link`, click) — Opens /me, which redirects to the signed-in user's own profile.
    - **Download** (`link`, click) — Footer link to /download (native apps).
    - **Language** (`link`, click) — Footer link to /settings/language.
    - **Credits** (`link`, click) — Footer credits control; links to /get-started while onboarding tasks remain, otherwise /credits.
    - **Usage** (`link`, click) — Footer link to the usage page.
    - **Info menu** (`dialog`, click) — Overflow menu with account and informational links.
      - **Settings** (`link`, click) — Opens /settings.
      - **Pricing** (`link`, click) — Opens /pricing.
      - **Terms of Service** (`link`, click) — Opens /about/terms-of-service.
      - **Privacy Policy** (`link`, click) — Opens /about/privacy-policy.
      - **Help Center** (`link`, click) — Opens /about/help-center.
      - **Contact us** (`link`, click) — mailto link to contact@teamily.ai.
      - **Social links** (`link`, click) — External links to X, LinkedIn, and Discord.
  - **Mobile tab bar** (`tabs`, click) — Bottom navigation shown on mobile primary pages (and when the glueview/thread view is visible).
    - **Chat tab** (`link`, click) — Navigates to /chat (or /login when signed out); shows an unread-message badge.
    - **Discover tab** (`link`, click) — Navigates to /discover.
    - **Explore tab** (`link`, click) — Navigates to /explore (resets the explore feed session).
    - **Contacts tab** (`link`, click) — Navigates to /contact; shows a pending-friend-application badge.
  - **Mobile download app dialog** (`dialog`, click) — Prompt encouraging mobile-web users to install the native app.
  - **Web first-run tour** (`dialog`, click) — Onboarding walkthrough highlighting key chrome (e.g. the discover nav) on a user's first web session.

### Layout /(public) — Public Layout

**Public Layout** — Chrome for signed-out / public routes (login, support, invite landing, etc.) — a sticky top nav bar with optional back button, home logo, and (when signed in) an avatar shortcut into the app. The whole bar is hidden when the route is embedded.

- Wraps: `app/(public)`
- Downstream: [`/`](#page-), [`/chat`](#page-chat)
- CTAs:
  - **Top nav bar** (`nav`, click) — Sticky top navigation bar; hidden entirely on embedded views (data-hide-on-embed).
    - **Back button** (`button`, click) — Shown only when in-app history exists; navigates back one step via router.back().
    - **Home logo** (`link`, click) — Favicon + home icon linking to / (the landing/home page).
    - **Avatar shortcut** (`link`, click) — Shown only when signed in; the user avatar links to /chat to jump into the app.

### Layout /chat — Chat Layout

**Chat Layout** — Two-pane chrome for the messaging workspace — a resizable left sidebar (the aside panel with conversation search and the user's conversation list) beside the active conversation. On mobile the open conversation is presented in a full-screen sheet whose back button clears the selection.

- Wraps: `app/(dashboard)/chat`
- Downstream: _none_
- CTAs:
  - **Conversation sidebar** (`nav`, click) — Resizable aside panel listing the user's conversations; width persists under the chat-sidebar-width key.
    - **Conversation search** (`input`, input) — Search box that filters the conversation list as you type.
    - **Conversation list item** (`button`, click) — Selects a conversation to open it in the main pane (or the mobile sheet).
  - **Mobile conversation sheet** (`dialog`, click) — Full-screen right-side sheet that shows the open conversation on mobile; the system/back gesture closes it and clears the current conversation.
  - **Sidebar resize handle** (`button`, hover/click) — Drag handle on the resizable sidebar edge; persists the chosen width. (Desktop only.)

### Layout /contact — Contact Layout

**Contact Layout** — Two-pane chrome for the Contacts area — a resizable left sidebar (title, add-contact button, and the contact nav) beside the routed contact content. On mobile the root shows the nav plus list with a header add-contact button; sub-pages go full screen.

- Wraps: `app/(dashboard)/contact`
- Downstream: [`/contact/my-agents`](#page-contactmy-agents), [`/contact/my-friends`](#page-contactmy-friends), [`/contact/phone-contacts`](#page-contactphone-contacts), [`/add-contact`](#page-add-contact)
- CTAs:
  - **Add contact button** (`button`, click) — Plus icon in the sidebar/header; opens the Add Contact modal on desktop, or navigates to /add-contact on mobile.
  - **Contact nav** (`tabs`, click) — Sidebar navigation between the contact sub-views.
    - **My Agents tab** (`link`, click) — Navigates to /contact/my-agents (also the active tab for the /contact root on desktop).
    - **My Friends tab** (`link`, click) — Navigates to /contact/my-friends.
    - **Phone Contacts tab** (`link`, click) — Navigates to /contact/phone-contacts.
  - **Sidebar resize handle** (`button`, hover/click) — Drag handle on the resizable sidebar edge; persists the chosen width under the contact-sidebar-width key. (Desktop only.)

### Layout /embed — Embed Layout

**Embed Layout** — Pass-through layout for embeddable (iframe) routes — renders its children with no app chrome so views can be hosted inside other apps.

- Wraps: `app/embed`
- Downstream: _none_
- CTAs: _none_

### Layout /embed/tool-view — Embed Tool View Layout

**Embed Tool View Layout** — Pass-through layout for the embeddable tool-view route; sets the "Tool view" title and marks the route noindex/nofollow so it stays out of search.

- Wraps: `app/embed/tool-view`
- Downstream: _none_
- CTAs: _none_

### Layout /explore — Explore Layout

**Explore Layout** — Pass-through layout for the Explore feed and its sub-routes; renders children unchanged and defers all chrome to the dashboard shell.

- Wraps: `app/(dashboard)/explore`
- Downstream: _none_
- CTAs: _none_

### Layout /i/[invite_code] — Invite Landing Layout

**Invite Landing Layout** — Server layout that fetches invite-landing data to build per-invite OG/Twitter title and description (falling back to generic invite copy), so shared invite links preview the inviter; the og:image still comes from opengraph-image.tsx.

- Wraps: `app/(public)/i/[invite_code]`
- Downstream: _none_
- CTAs: _none_

### Layout /link/[code] — Share Link Layout

**Share Link Layout** — Server layout for shared-artifact deep links; emits crawler-readable OG/Twitter title, description, and canonical URL for the /link/[code] route, then renders its children.

- Wraps: `app/link/[code]`
- Downstream: _none_
- CTAs: _none_

### Layout /login — Login Layout

**Login Layout** — Server layout for the client-rendered /login page; its sole job is to mark the auth route noindex/nofollow so sign-in pages stay out of search results.

- Wraps: `app/(public)/login`
- Downstream: _none_
- CTAs: _none_

### Layout /settings — Settings Layout

**Settings Layout** — Wraps the settings sub-pages (subscription, credits center, affiliate, connectors, privacy, language, etc.) in a centered max-width column with a sticky header. The settings root renders children bare; sub-pages get a localized title and a back control with an animated page transition.

- Wraps: `app/(dashboard)/settings`
- Downstream: [`/settings`](#page-settings)
- CTAs:
  - **Sub-page header** (`nav`, click) — Sticky top header shown on settings sub-pages (not the /settings root), displaying the localized sub-page title.
    - **Back button** (`button`, click) — Arrow-left control; goes back in history if available, otherwise jumps to the /settings root.

### Layout /share/[id] — Shared Conversation Layout

**Shared Conversation Layout** — Server layout for shared agent-conversation replays; loads the thread/project to build OG/Twitter title, description, and canonical URL (with a generic fallback on error), then renders its children.

- Wraps: `app/(dashboard)/share/[id]`
- Downstream: _none_
- CTAs: _none_

### Layout /support — Support Layout

**Support Layout** — Server layout that supplies SEO/OG metadata (title, description, canonical, Twitter card) for the client-rendered /support page, then renders its children.

- Wraps: `app/(public)/support`
- Downstream: _none_
- CTAs: _none_
