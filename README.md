# TAP FAQs

This repository stores the static markup used to build the TAP FAQ pages. No
runtime generation or CSV processing is performed here—everything is written as
HTML snippets that can be dropped directly into the production site. The FAQ
interface uses a simple search bar and accordion sections; earlier tile-based
navigation has been removed.

See [ARCHITECTUREOVERVIEW.md](ARCHITECTUREOVERVIEW.md) for details on the
overall HTML structure and guidance on integrating the snippets.

## CSV references

The CSV files in the `resources/` directory exist only as human-friendly
reference material that captures the original FAQ copy and organization. They
are **not** imported into any code, compiled into the build, or used at runtime.

## Project deliverable

The output of this project is a set of hard‑coded HTML blocks—one for each FAQ
question and answer. These blocks are ready for copy‑and‑paste into the live
TAP site without additional tooling.

