# Architecture Overview

This project produces static HTML fragments representing each Frequently Asked
Question. The markup is organized so that each FAQ section itself behaves as an
accordion. Sections can contain optional subsections, and questions live within
those subsections.

## FAQ HTML structure

- **Section accordion** – Each top‑level category is a `<section>` that opens and
  closes like an accordion. The `<h2>` inside the section acts as the clickable
  header.
- **Subsections** – Within the expanded section, group related questions under
  `<h3>` subsection headings. Every subsection contains its own definition list
  (`<dl>`).
- **Question list** – Inside each subsection's `<dl>`, use `<dt>` for the
  question text and `<dd>` for the answer. If a section has no subsections, place
  the `<dl>` directly inside the section instead of using an `<h3>`.
- **Styling** – The snippets rely on the host site's existing CSS for fonts and
  accordion behavior. Ensure the class names above are available where the FAQ is
  embedded.

## CSV as reference only

`resources/TAP-FAQ-existing-structure.csv` and any other CSV files in this
repository are *strictly* human‑readable references while authoring the HTML.
They must not be parsed, imported, or included in any build process.

## Example FAQ structure

```html
<section class="accordion">
  <h2>Using the TAP App</h2>
  <div class="accordion-panel">
    <h3>Managing Your Account</h3>
    <dl>
      <dt>How do I reset my password?</dt>
      <dd>
        <p>Open the TAP app and select "Forgot Password" on the sign‑in screen...</p>
      </dd>
    </dl>
  </div>
</section>

<section class="accordion">
  <h2>Getting a TAP Card</h2>
  <div class="accordion-panel">
    <dl>
      <dt>Where can I buy a TAP card?</dt>
      <dd>
        <p>TAP cards are sold at vendor locations and ticket machines...</p>
      </dd>
    </dl>
  </div>
</section>
```

## Integrating into the site

Developers should paste the generated HTML snippets into the FAQ container of
the TAP site (for example, inside the element that currently holds other FAQ
entries). No additional JavaScript or CSV processing is required—copy the
snippets directly into the page and rely on the site's existing styles and
scripts for accordion functionality.

