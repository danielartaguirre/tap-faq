# TAP FAQ Project Business Rules

A consolidated set of rules and guidelines for building the new TAP FAQs page. Use these as the source of truth for UI, UX, HTML, JavaScript, and CSS development.

---

## 1. Project Overview
- **Goal:** Merge and optimize two existing FAQ pages (`TAPFAQ` and `TAPAppFAQs`) into one unified, categorized FAQ.
- **Source Content:**
  - `/resources/TAP FAQs page.html`
  - `/resources/TAP App FAQs page.html`
  - `/resources/TAP-FAQ-existing-structure.csv`
- **Deliverable:** Responsive HTML/CSS/JS that can be deployed as a standalone FAQ webpage or integrated into taptogo.net.

## 2. FAQ Content
- **FAQ Structure:** Merge and optimize two existing FAQ pages (`TAPFAQ` and `TAPAppFAQs`) into one unified, categorized FAQ.
- **Source Content:**
  - `/resources/TAP FAQs page.html`
  - `/resources/TAP App FAQs page.html`
  - `/resources/TAP-FAQ-existing-structure.csv`
  - make the accordions as the sections from csv, and have sub sections within the accordion for the questions as organized in the csv
  

### 2.1 Accordion sections:
1. About TAP
2. Using Your TAP Card
3. Managing Fare on Your TAP Card
4. TAP card Features
5. Employer TAP Cards
6. Reduced Fare TAP cards
7. Programs
8. iPhone - TAP App
9. Android - TAP App
10. App Overview

---

## 3. TAP FAQ — Single-Source UX & UI Rules

### 3.1 Color Tokens
```css
--tap-blue       : #0096D6;   /* Primary */
--tap-light-blue : #6FC4E9;   /* Selected tile / hover */
--tap-orange     : #DB7D07;   /* Highlights / warnings */
--tap-grey-bg    : #F2F6F9;   /* Light backgrounds */
--tap-white      : #FFFFFF;
--tap-text-dark  : #333333;
```

### 3.2 Typography
- Heading (Museo Sans 700 / 24–32 px)
- Body (Museo Slab 400 / 14–18 px)
- Label (Museo Sans 600 / 14 px, uppercase allowed on buttons)
- Line-height: 1.4 desktop, 1.5 mobile.

### 3.3 Spacing & Layout
| Token         | Value                                             |
|-------------- |---------------------------------------------------|
| Base unit     | 8 px grid                                         |
| Desktop grid  | 12 columns, 80 px gutter                          |
| Mobile grid   | 4 columns, 16 px gutter                           |
| Corner radius | 8 px (tiles / accordions), 15 px (search bar)     |
| Shadow        | 0 2 4 0 rgba(0,0,0,0.08) on hover / active panels |

### 3.4 Components
**Search Bar**

- Height 60 px, full-width.
- BG `var(--tap-grey-bg)` with 1 px border `#D0D0D0`.
- Placeholder style 18 px / `var(--tap-text-dark)`.

**Category Tile**

- Size 170 × 130 px desktop, 160 × 140 px mobile.
- BG `var(--tap-blue)`; selected → `var(--tap-light-blue)` + 2 px outline `var(--tap-blue)`.
- Icon circle 60 px, white abbreviation label 20 px bold.

**Accordion Header**

- Height 52 px.
- Collapsed BG `var(--tap-blue)` → expanded `var(--tap-light-blue)`.
- Chevron rotates 90° on open (0.2 s ease).

**Accordion Body**

- Min-height 120 px, BG `var(--tap-grey-bg)`.
- Text 14 px / `var(--tap-text-dark)`.

**Highlight**

- Wrap matched word with `<span class="highlight">`; CSS:

```css
.highlight { background: rgba(219,125,7,0.3); }
```

### 3.5 Behaviour & States
- Tiles multi-select: Users can toggle any combination; state drives accordion open/close.
- **Search:**
  - Case-insensitive substring match across questions and answers.
  - On input: expand categories with hits, collapse others, highlight matches.
  - Empty query → restore pre-search selection.
  - No-results state: Centered illustration + “No FAQs matched your search” in `var(--tap-orange)`.

### 3.6 Accessibility
- All interactive elements are real `<button>` or `<a>` with `aria-expanded` where applicable.
- Keyboard ↔ : Tab focuses tile, Enter toggles; arrow keys navigate tiles in row / grid.
- Colour contrast ≥ 4.5:1 for all text.
- Focus ring 2 px outline `var(--tap-orange)` (WCAG AA visible).

### 3.7 Motion
- Tiles hover: 0.15 s background fade.
- Accordion: 0.2 s ease-in-out height animation; chevron syncs.

---

## 4. HTML Structure Guidelines

- **Semantic Markup:**
  - Use modern HTML5 elements: `<header>`, `<nav>`, `<section>`, etc.
  - Include `<form role="search">` for the search box.
  - Use `<section>` per FAQ category with an `id` matching its name (e.g. `<section id="using-tap">`).
- **Header & Footer:**
  - Embed the standard header and footer from [taptogo.net](http://taptogo.net/) so the page can be previewed via GitHub Pages and match the main site’s chrome.

---

## 5. Structured Data

- **FAQ Schema:** Implement [schema.org](https://schema.org) `FAQPage` markup to help search engines understand the content.
  - Each question should use the `Question` type with `name` and `acceptedAnswer`.
  - Answers should use the `Answer` type inside `acceptedAnswer`.
  - Use microdata inline html
