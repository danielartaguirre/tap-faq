# Architecture Overview

This project produces static HTML fragments representing each Frequently Asked
Question. The markup is organized into sections and uses simple accordion
components for expanding and collapsing answers.

## FAQ HTML structure

- **Section headers** – Each FAQ category begins with an `<h2>` that labels the
  section.
- **Accordion list** – Questions and answers live inside a definition list with
  the class `accordion`:
  - `<dt>` elements contain the question text and act as the clickable headers.
  - `<dd>` elements hold the answer content that is shown or hidden.
- **Styling** – The snippets rely on the host site's existing CSS for fonts and
  accordion behavior. Ensure the class names above are available where the FAQ
  is embedded.

## CSV as reference only

`resources/TAP-FAQ-existing-structure.csv` and any other CSV files in this
repository are *strictly* human‑readable references while authoring the HTML.
They must not be parsed, imported, or included in any build process.

## Example FAQ item

```html
<section>
  <h2>Using the TAP App</h2>
  <dl class="accordion">
    <dt>How do I reset my password?</dt>
    <dd>
      <p>Open the TAP app and select "Forgot Password" on the sign‑in screen...</p>
    </dd>
  </dl>
</section>
```

## Integrating into the site

Developers should paste the generated HTML snippets into the FAQ container of
the TAP site (for example, inside the element that currently holds other FAQ
entries). No additional JavaScript or CSV processing is required—copy the
snippets directly into the page and rely on the site's existing styles and
scripts for accordion functionality.

