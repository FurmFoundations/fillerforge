# Filler Forge

**Domain:** [fillerforge.online](https://fillerforge.online)  
**Tagline:** Layout-accurate placeholder text generator

## Product Overview

**Problem:** Lorem Ipsum doesn't preserve the structure, word length, or semantic patterns of real content. Designers paste it in and their layouts shift when real copy arrives.

**Solution:** Filler Forge generates placeholder text that matches the exact word count, sentence structure, punctuation patterns, and content types (dates, names, currencies, bullets) of your original text — so layouts stay pixel-perfect.

## Core Features (v1 — Shipped)

### 1. Three Generation Modes
- **Basic:** Fast word-by-word replacement matching length
- **Structure:** Preserves capitalization patterns, punctuation placement, proper noun shapes
- **Semantic (AI-powered):** Uses Gemini API to understand content types and generate contextually accurate filler
  - Detects: Date+Event pairs, Name+Title, bullets, numbered lists, currency, phone numbers, emails, URLs, body copy, headlines, legal text, ALL CAPS labels
  - Preserves tone (legal stays formal, marketing stays punchy)

### 2. Multilingual Support (9 languages)
- English, Spanish, Portuguese, French, German, Arabic (with RTL layout), Korean, Japanese, Chinese
- Two styles per language:
  - **Authentic:** Real words from that language
  - **Phonetic:** Invented text that looks/sounds like the language

### 3. Advanced Options
- **Proper Noun Preservation:** Keeps names the same character length for pixel-perfect columns
- **Tone Preservation:** AI matches the register of original text (Semantic mode only)

### 4. Output Tools
- Copy as plain text
- Copy as rich text (preserves formatting for InDesign/Word)
- Download as .txt
- Per-paragraph regeneration (hover any paragraph to re-roll just that section)

### 5. Quality-of-Life Features
- PII detection (warns if real emails, phones, SSNs, credit cards detected)
- History (last 5 generations, click to restore)
- Light/Dark mode toggle
- Stats (live word/char count in/out)
- Pattern detection bar (shows what Semantic mode recognized)

## Technical Architecture

### Frontend
- Single-page HTML/CSS/JS app (no build step, no dependencies)
- Vanilla JavaScript for all logic
- localStorage for: API key, theme preference, generation history
- Responsive bento-box grid layout

### API Integration
- Google Gemini 2.0 Flash (via free tier)
- User provides their own API key (stored locally in browser)
- Fallback to local pattern-matching semantic mode if no key

### Hosting
- GitHub Pages (free, auto-deploys on push to main)
- Custom domain: fillerforge.online (DNS via Namecheap)
- SSL via GitHub Pages (automatic)

---
*Tool is 100% free forever. Support the project at [ko-fi.com/furmfoundry](https://ko-fi.com/furmfoundry)*
