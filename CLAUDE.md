# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static single-page portfolio website template (originally by Colorlib, CC BY 3.0). No build system or package manager — all assets are pre-compiled and served statically. The site is a single `index.html` file with vanilla JavaScript (jQuery-based) and SCSS source files compiled via **Prepros**.

## Development

**Serving locally:** Open `index.html` directly in a browser, or use Prepros (configured on port 8003 with live-reload enabled).

**Styling workflow:** The source of truth for styles is `scss/style.scss`. Prepros compiles it to `css/style.css` automatically on save. Do not edit `css/style.css` directly — edit the SCSS source.

- Main custom SCSS: [scss/style.scss](scss/style.scss)
- Bootstrap SCSS source: [scss/bootstrap/](scss/bootstrap/) (vendored, avoid modifying)

There are no lint, test, or build commands — this is a pure static site.

## Architecture

Everything lives in `index.html` as a single-page layout with anchor-link navigation (`#home-section`, `#about-section`, `#resume-section`, `#project-section`, `#contact-section`).

**JS libraries (all in [js/](js/), loaded at bottom of `index.html`):**
- jQuery + jQuery Migrate — base DOM/event handling
- Bootstrap 4 + Popper — navbar, collapse
- Owl Carousel — hero slider (`.home-slider`)
- AOS (Animate On Scroll) — scroll-triggered fade-ins (`.ftco-animate` elements)
- Stellar.js — parallax backgrounds
- Scrollax — parallax text on hero
- Waypoints + animateNumber — counter animation (`data-number` attribute drives the count-up)
- Magnific Popup — lightbox for images/iframes

**Custom JS:** [js/main.js](js/main.js) wires up all the above libraries and handles: navbar scroll behavior (adds `.scrolled`/`.awake`/`.sleep` classes), burger menu toggle, smooth one-page scroll, counter animation trigger, and staggered `ftco-animate` entrance effects.

**Inline styles:** Some component-specific styles (About section, skill progress bars, typing animation, zoom hover effect) are written directly in a `<style>` block inside `index.html` rather than in the SCSS.

**Typing animation:** Implemented inline in `index.html` via a small vanilla JS script targeting `#typing-animation`. Edit the `typingTexts` array there to change the rotating role titles.
