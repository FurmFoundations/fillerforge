# Filler Forge — Architecture & Technical Overview

This document provides a high-level breakdown of how **Filler Forge** works under the hood. It is designed to help developers and contributors understand the codebase, data flow, and design philosophy.

---

## 1. Core Philosophy & Dependencies

Filler Forge is built entirely as a **Zero-Dependency Single Page Application (SPA)**. 

- **Frameworks:** None. Pure Vanilla HTML, CSS, and JavaScript.
- **Build Tools:** None. No Webpack, Vite, or Babel required.
- **Backend/Database:** None. The app runs 100% locally in the user's browser.
- **Dependencies:** The only external dependency is the native browser `fetch` API used to communicate directly with Google's Gemini API endpoints.

**Why this approach?**
By eliminating backends and databases, the application is incredibly fast, costs absolutely nothing to host (GitHub Pages), and ensures maximum user privacy (since text is never routed through an intermediary server).

---

## 2. Component Breakdown (Inside `index.html`)

The entire application logic is self-contained within `index.html`. It is divided into three distinct layers: the **UI/Theme Layer**, the **Data Layer**, and the **Processing Engines**.

### A. UI and Theming Layer (CSS)
The interface is built using standard CSS Grid for the responsive "Bento Box" layout. 
- **Theming:** Dark mode and light mode are handled entirely via CSS Variables (`--bg`, `--accent`, `--card`, etc.) attached to the `[data-theme="light"]` and `[data-theme="dark"]` selectors on the `<html>` tag.
- **Responsiveness:** Simple media queries (`@media(max-width: 860px)`) reflow the Grid from 4 columns down to 1 column for mobile devices.

### B. The Data Layer (JavaScript Word Banks)
At the top of the `<script>` tag, there are massive constant objects that act as the application's "database".
- **`AUTH` Object:** Contains real words for 9 different languages, categorized by length (`s` = small, `m` = medium, `l` = large). 
- **`PHON` Object:** Contains phonetic "nonsense" words that visually match the target languages.
- **Asian Language Arrays:** Instead of lengths, Korean, Japanese, and Chinese use `units` arrays containing contextually appropriate characters.

### C. The Processing Pipeline (JavaScript Logic)
When a user clicks "Generate", the text flows through one of three distinct engines based on the selected mode:

#### 1. Basic & Structure Engine (`replaceWords()` and `fakeProper()`)
This is the core local engine. 
- It uses Regex to tokenize the input text into words while preserving exact punctuation and spaces.
- It calculates the character length of each word and requests a random word of the same length from the `AUTH` or `PHON` word bank (`wfl()` function).
- If "Structure" mode is on, it checks if a word is Title Case or ALL CAPS, and forces the random filler word to match that exact capitalization.
- If "Preserve Proper Nouns" is checked, it detects capitalized names and replaces them with an invented name of the exact same character count.

#### 2. Asian Character Engine (`replaceAsian()`)
Asian languages do not use spaces to separate words. If an Asian language is selected, the standard `replaceWords` engine is bypassed.
- It uses Unicode property escapes (`\p{P}`) to split the string by punctuation, leaving chunks of characters.
- It replaces these chunks with a randomized assembly of characters from the specific Asian language unit bank.

#### 3. Local Semantic Engine (`localSemantic()`)
Before involving AI, the app attempts to recognize structured data locally.
- It scans the input using specific Regex patterns (e.g., matching Phone Numbers `\(?\d{3}\)?[-.\s]...` or Currency `\$[\d,]+`).
- If it finds a phone number, it doesn't just replace it with random letters. It triggers `g.phone()` to generate a realistic fake phone number. It does the same for Dates, Names, Titles, URLs, and Emails.

#### 4. AI Semantic Engine (`callGemini()`)
If the user selects "Semantic" mode and has provided an API key, the text is routed to Google Gemini.
- The app constructs a highly specific prompt instructing the AI to act as a placeholder generator.
- It injects the user's selected language, tone preference, and proper noun settings directly into the prompt.
- The request is sent directly from the browser to `generativelanguage.googleapis.com`.
- **Fallback:** If the API fails, times out, or the key is invalid, the `catch (e)` block elegantly catches the error and instantly falls back to the **Local Semantic Engine**, ensuring the app never breaks.

---

## 3. Security and Privacy

Because Filler Forge processes potentially sensitive layout documents (like internal company agendas or unreleased product pricing), security is baked into the architecture:

1. **PII Checker (`checkPII()`)**: As the user types or pastes text, an offline regex engine scans the input for Personal Identifiable Information (Emails, Phone Numbers, Social Security Numbers, Credit Cards). If detected, it displays a red warning banner *before* the user clicks Generate.
2. **Bring Your Own Key (BYOK)**: By requiring the user to paste their own Gemini API Key, the developer holds zero liability for API abuse or data interception.
3. **Local Storage**: The API key is saved using `localStorage.setItem('ff_key', v)`. It exists *only* on the user's local hard drive and is never transmitted anywhere except directly to Google's servers.
