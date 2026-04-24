<div align="center">

# ⚒️ Filler Forge

**Layout-accurate placeholder text generator**

[![Website Live](https://img.shields.io/badge/Live-fillerforge.online-2d6a4f?style=for-the-badge)](https://fillerforge.online)
[![License: Free](https://img.shields.io/badge/License-Free-50c8f0?style=for-the-badge)](https://fillerforge.online)

*Lorem Ipsum breaks your mockups. Filler Forge fixes them.*

</div>

---

## 🛑 The Problem
Lorem Ipsum is random Latin with no connection to real content structure. Designers paste it in, and their beautiful layouts shift and break when the real copy finally arrives.

## ✨ The Solution
**Filler Forge** generates placeholder text that matches the exact **word count, sentence structure, punctuation patterns, and content types** (dates, names, currencies, bullets) of your original text — so your layouts stay pixel-perfect from wireframe to final copy.

---

## 🚀 Core Features

### ✦ Three Generation Modes
* **🟢 Basic:** Fast, word-by-word replacement matching exact length.
* **🔵 Structure:** Preserves capitalization patterns, punctuation placement, and proper noun shapes.
* **🟣 Semantic (AI-powered):** Uses the Gemini API to understand content types and generate contextually accurate filler.
  > *Detects: Date+Event pairs, Name+Title, bullets, numbered lists, currency, phone numbers, emails, URLs, body copy, headlines, legal text, ALL CAPS labels.*

### 🌍 Multilingual Support (9 Languages)
English, Spanish, Portuguese, French, German, Arabic *(with RTL layout)*, Korean, Japanese, and Chinese.

Choose between two unique styles:
* **Authentic:** Real words from that language.
* **Phonetic:** Invented text that looks/sounds like the language but isn't real.

### 🛠 Quality-of-Life Tools
* **Preserve Proper Nouns:** Keeps names the exact same character length for pixel-perfect columns.
* **PII Detection:** Automatically warns you if real emails, phones, SSNs, or credit cards are detected before generating.
* **Hover to Regenerate:** Re-roll individual paragraphs with a single click.
* **Light / Dark Mode:** Toggle between beautifully crafted UI themes.
* **Export Options:** Copy as Plain Text, Rich Text (preserves formatting for InDesign/Word), or Download as `.txt`.

---

## 🗺️ Roadmap

**v1.0 (Shipped — Current)**
- ✅ Basic, Structure, and Semantic modes
- ✅ 9 languages with authentic & phonetic variants
- ✅ Gemini API integration
- ✅ PII detection & warning system
- ✅ Session history & per-paragraph regeneration
- ✅ Responsive bento-box UI with light/dark mode

**v1.1 (Next 2 Weeks)**
- ⏳ Privacy-first analytics (Plausible)
- ⏳ SEO meta tags & Open Graph for social sharing
- ⏳ Keyboard shortcuts (e.g., `Cmd+Enter` to generate)
- ⏳ "Copy as HTML" for immediate web workflows

**v1.2 (Next Month)**
- ⏳ Preset templates (Conference programs, annual reports, e-commerce)
- ⏳ Export to `.docx` styled documents
- ⏳ Browser Extension (right-click to "Forge Filler" in any field)

**v2.0 (3-6 Months)**
- ⏳ Native InDesign Plugin
- ⏳ Figma Plugin Beta
- ⏳ Claude API option (Semantic mode alternative)
- ⏳ Batch processing (Upload CSV/JSON → receive filler)

---

## 💻 Technical Architecture

Filler Forge is built for speed and privacy.

* **Frontend:** 100% Vanilla HTML/CSS/JS single-page app. Zero build steps, zero dependencies.
* **API Integration:** Google Gemini 2.0 Flash.
* **Privacy First:** Users provide their own free API key. It is stored *only* in your browser's `localStorage` and never sent anywhere except directly to Google.
* **Offline Fallback:** If you don't have an API key, Basic and Structure modes run entirely locally in your browser without an internet connection.

---

## ☕ Support the Project

Filler Forge is 100% free forever. No ads, no paywalls, no account required. 
If it saves you time on your design mockups, consider supporting the development!

<a href="https://ko-fi.com/furmfoundry" target="_blank"><img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="Support on Ko-fi" /></a>
