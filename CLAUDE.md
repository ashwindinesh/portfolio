# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file static portfolio website for Ashwin Dinesh, a Product Design Architect. Everything — HTML structure, CSS styles, and JavaScript — lives in `index.html`.

## Development

No build system or tooling. View by opening `index.html` directly in a browser, or serve locally:

```sh
python3 -m http.server
```

## Architecture

`index.html` is self-contained with three parts:

- **`<style>`** — all CSS using CSS custom properties (`--bg`, `--fg`, `--fg-muted`, `--border`, `--font`, `--max-w`) defined on `:root`. Responsive breakpoints at 1024px (tablet) and 640px (mobile).
- **HTML body** — fixed `<nav>`, a `<main>` with four sections (`hero`, `#work`, `#experience`, `#education`), and a `<footer>`.
- **`<script>`** — scroll listener that highlights the active nav link by comparing `scrollY` against each `section[id]`'s `offsetTop`.

Work portfolio images are loaded from Dribbble CDN with `loading="lazy"`.

## CSS Conventions

- Use existing CSS custom properties for all color/spacing — never hardcode values that could use a variable.
- The `--border` color (`#e5e7eb`) is also used for decorative elements (e.g., bullet dashes in `.exp-desc li::before`), not just borders.
- Mobile nav hides nav items 3+ (Experience, Education) via `li:nth-child(n+3) { display: none }` — keep nav item order stable.

## JS Behavior

- The scroll listener uses a `-80px` offset (`offsetTop - 80`) to account for the fixed nav height (56px) with margin.
- The "About" link (`href="#"`) never activates via scroll; only `#work`, `#experience`, `#education` do.
