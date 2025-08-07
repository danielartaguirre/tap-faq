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

---

## 3. UI Guidelines

### 3.1 Layout & Components
- **Category Navigation:**
  - Display as a horizontal nav bar on desktop; a collapsible “hamburger” menu or select dropdown on mobile.
  - Active category clearly highlighted (e.g. underlined or background tint).
- **Accordions:**
  - Within each category, questions appear in an accordion list.
  - Only one question may be open at a time _per category_ (close previously open when opening a new one).
- **Search Box:**
  - Always visible at top of page.
  - Filters questions in real time as user types.

### 3.2 Colors & Typography
- **Primary Color:** `#0096D6` — use for headings, active nav, icons.
- **Accent Color:** `#DB7D07` — use sparingly for highlights, call-to-action links.
- **Background Tint:** `#6fc4e9` at 10–20% opacity for answer panels.
- **Fonts:**
  - Headings: Sans-serif, bold; sizes (desktop): H1 2rem, H2 1.5rem, H3 1.25rem.
  - Body text: Sans-serif, 1rem, line-height 1.6.
- **Spacing:**
  - Section padding: 2rem top/bottom.
  - Accordion question margin-bottom: 1rem.
  - Answer padding: 1rem.

---

## 4. UX Guidelines

- **Accessibility:**
  - All interactive elements keyboard-focusable; use `aria-expanded`, `aria-controls` on accordion triggers.
  - Sufficient color contrast (≥ 4.5:1) on text.
  - Logical tab order: nav → search → categories → questions.
- **Mobile Responsiveness:**
  - Single-column layout on narrow viewports.
  - Touch targets ≥ 44×44 px.
  - Collapse non-active categories for quick navigation.
- **Performance:**
  - Lazy-load answer content only when panels open.
  - Minimize DOM size by initially loading only the active category’s questions; load others via AJAX when selected.

---

## 5. HTML Structure Guidelines

- **Semantic Markup:**
  - Use modern HTML5 elements: `<header>`, `<nav>`, `<main>`, `<section>`, and `<footer>`.
  - Include `<form role="search">` for the search box.
  - Use `<section>` per FAQ category with an `id` matching its name (e.g. `<section id="using-tap">`).
- **Header & Footer:**
  - Embed the standard header and footer from [taptogo.net](http://taptogo.net/) so the page can be previewed via GitHub Pages and match the main site’s chrome.
- **Accordion Markup Example:**
  ```html
  <dl class="faq-accordion" aria-labelledby="using-tap-heading">
    <dt id="q1" aria-controls="a1">
      <button aria-expanded="false">How do I use TAP?</button>
    </dt>
    <dd id="a1" aria-labelledby="q1" hidden>
      <p>Simply tap your card on the TAP …</p>
    </dd>
    <!-- more items… -->
  </dl>
  ```

---

## 6. Structured Data

- **FAQ Schema:** Implement [schema.org](https://schema.org) `FAQPage` markup to help search engines understand the content.
  - Each question should use the `Question` type with `name` and `acceptedAnswer`.
  - Answers should use the `Answer` type inside `acceptedAnswer`.
  - Use JSON-LD in a `<script type="application/ld+json">` block in the page `<head>`.

