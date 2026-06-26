---
path: /settings/language
id: settings-language
name: Language
title: Language
description: Language settings page with two independent knobs — the System (UI) locale and the Chat auto-translation target language — plus an auto-translate master toggle; the two pickers draw from different supported-language sets (see body).
relationship:
  upstream: "/, /settings"
  downstream: ""
cta:
  "System Language":
    type: select
    trigger: click
    description: "Picks the app UI locale; applied immediately via the locale context and persisted locally. 17 supported locales from LOCALES/LOCALE_LABELS — see the body."
  "Chat Language":
    type: select
    trigger: click
    description: "Picks the target language for chat message auto-translation; saved to the translation service (toasts on save failure). 17 supported languages from TRANSLATION_LANGUAGES — see the body; this set differs from the UI locales."
  "Auto Translate":
    type: toggle
    trigger: click
    description: "Checkbox master switch enabling/disabling automatic translation of incoming chat messages (stored on the IM self user; defaults ON when never set; toasts on save failure)."
---

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
