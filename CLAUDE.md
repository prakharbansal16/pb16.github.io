# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static personal academic website for Prakhar Bansal (Physics PhD, University of Michigan), built on the **Hyperspace** template by HTML5 UP. It is deployed via GitHub Pages at `pb16.github.io`. There is no build step — files are served as-is.

To preview locally, open `index.html` directly in a browser or use any static file server:
```
python3 -m http.server 8000
```

## Structure

- `index.html` — single-page site with anchor-linked sections: `#intro`, `#one` (About Me), `#two` (Research), `#four` (CV & Publications), `#five` (Talks), `#three` (Contact)
- `research/` — individual sub-pages per research topic (e.g. `cosmological-tensions.html`, `full-shape.html`), loaded via nav links from the research tiles
- `presentations/` — PDF slides linked from the Talks section
- `images/` — photos and figures used across the site
- `CV_Prakhar.pdf` — CV linked from the Academic Resources section
- `assets/css/main.css` — primary stylesheet; custom styles for this site are appended after the Hyperspace base styles (starting around line 4040)
- `assets/css/noscript.css`, `assets/js/` — Hyperspace template JS (jQuery, Scrollex, browser detection, etc.); do not modify these

## Key Conventions

**CSS**: Custom styles (`.intro-container`, `.research-tile`, `.talk-list`, `.resource-buttons`, etc.) live at the bottom of `assets/css/main.css`. The Hyperspace base styles occupy the bulk of the file; append new styles rather than modifying the base.

**Research sub-pages** (`research/*.html`): Use `../assets/css/main.css` for the stylesheet path (one level up). Script paths currently use `assets/js/...` (missing `../`) — this is a known bug. The header nav links in these pages still point to `index.html` / `generic.html` (leftover template placeholders) and should be updated to point back to `../index.html`.

**Research tiles** in `index.html`: Several tiles link to `cosmological-tensions.html` even when their content belongs elsewhere (e.g. Full Shape, Modified Gravity, CMB Compression tiles all share the same wrong href). Each tile should eventually link to its own dedicated sub-page.

**Contact form**: The form `action="#"` is a placeholder — it does not submit anywhere. It needs a backend or a form service (e.g. Formspree) to actually work.

**Social icons**: The social links in the Contact section (`#three`) all use `href="#"` — they are placeholders and need real URLs.

**MathJax**: Loaded via CDN on `index.html` and `cosmological-tensions.html` for LaTeX rendering in research descriptions. Add the same `<script>` block to any new research pages that contain math.
