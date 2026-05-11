# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static single-page CV website for Chaima Zidi Saad. No build step, no package manager, no framework — three files total.

## Running locally

Open `index.html` directly in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Architecture

```
index.html        # All content and structure (French)
css/style.css     # All styles, including layout, animations, responsive, print
js/main.js        # Tab switching + animation re-trigger only
```

### Layout

Two-column CSS grid (`.cv-wrapper`): a fixed-width sidebar (230px) and a flexible main area. Collapses to single column at ≤700px via media query. Print mode hides tabs and forces all panels visible.

### Sidebar

Static content: avatar, name/role, contact info, skill tags, skill bars, language dots, certifications. No interactivity.

### Main area — tabs

Three tab panels (`#parcours`, `#projets`, `#publis`) toggled by `showTab()` in `main.js`. Only one panel has `class="active"` at a time.

### Timeline items (`#parcours`)

Each `.tl-item` carries `data-type="experience"` or `data-type="formation"`. This attribute drives marker color (purple vs. teal) and badge style via CSS attribute selectors — no JS involved.

### Animation system

Timeline items, project cards, and publication items use a CSS `fadeUp` keyframe with staggered `animation-delay` applied via `:nth-child` selectors. `showTab()` resets animations on tab switch by toggling `animation: none`, forcing a reflow (`offsetHeight`), then clearing the override.

### Design tokens

All colors are CSS custom properties on `:root` (purple, teal, gray scales). Fonts are DM Serif Display (headings/serifs) and DM Sans (body), loaded from Google Fonts.
