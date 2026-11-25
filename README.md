# Bowl & Bloom

A minimal, premium, single-page website for a health-focused cafe serving high-protein bowls, yogurt bowls, oat bowls, toasts and drinks. Every menu item lists its calories, protein and fat next to the price.

Built with plain HTML, CSS and vanilla JavaScript. No frameworks, no build step, no dependencies to install.

## Features

- **Scroll-driven hero:** a hand-drawn SVG coconut-shell bowl starts half off-screen on the left and sweeps along a circular arc to the right as you scroll. The three headline stats (protein, fat, sugar) pop in one at a time as the bowl passes each point.
- **Philosophy section:** an infinite right-to-left marquee of ingredients (Olive Oil, Egg, Vegan, Nuts, Seeds, Whole Foods, High Protein), each with a matching line icon. It pauses on hover. Below it, a three-part facts block: Fat Sources, Clean Preparation and Made Fresh.
- **Tabbed menu:** five centered categories (Yogurt Bowls, Drinks, Toasts, Protein Bowls, Oat Bowls). A soft matcha-green pill slides smoothly behind the active tab, and menu items fade in with a stagger when you switch.
- **Build Your Bowl form:** a special-requests section with quick-pick chips (high protein boost, nut-free, vegan, etc.) and a free-text field.
- **Dropdown navigation:** a spoon, knife and butter-knife icon on the right opens an anchored dropdown menu.
- **Responsive:** works on desktop and mobile. On small screens the menu tabs scroll horizontally and the active tab scrolls into view.
- **Accessible motion:** all animations respect `prefers-reduced-motion`.

## Getting started

No installation needed.

```bash
git clone https://github.com/<your-username>/bowl-and-bloom.git
cd bowl-and-bloom
```

Then open `bowl-and-bloom.html` in any modern browser.

To serve it locally instead:

```bash
python3 -m http.server 8000
# visit http://localhost:8000/bowl-and-bloom.html
```

## Deploy with GitHub Pages

1. Rename `bowl-and-bloom.html` to `index.html` so it loads at the site root.
2. Push to GitHub.
3. Go to **Settings → Pages**, choose your branch and the `/ (root)` folder, and save.
4. Your site will be live at `https://<your-username>.github.io/bowl-and-bloom/`.

## Project structure

```
bowl-and-bloom/
├── bowl-and-bloom.html   # The entire site: markup, styles and scripts
└── README.md
```

Everything lives in one file on purpose, which keeps it portable and easy to host anywhere.

## Customizing

### Colors

The palette is defined as CSS variables at the top of the stylesheet:

| Variable | Role |
| --- | --- |
| `--cream` | Page background (warm cream) |
| `--cocoa` / `--cocoa-deep` | Coconut-shell brown, dark sections and headings |
| `--matcha` / `--matcha-deep` / `--matcha-soft` | Primary green accent and the menu pill |
| `--lavender` / `--lavender-deep` | Secondary accent |

### Fonts

Loaded from Google Fonts: **Fraunces** (headings), **Jost** (body) and **JetBrains Mono** (labels, prices and macros).

### Menu items

Each item follows the same structure. Copy one inside the relevant `menu-grid` and edit the text:

```html
<div class="menu-item">
  <div>
    <div class="m-name">Item Name<span class="tag">Veg</span></div>
    <div class="m-desc">Short description of ingredients</div>
    <div class="m-macro mono">320 kcal · 24g protein · 8g fat</div>
  </div>
  <div class="m-right"><div class="m-price">₹250</div></div>
</div>
```

To add a new category, add a `<button class="tab" data-panel="name">` in the `.tabs` block and a matching `<div class="menu-panel" id="panel-name">`. The sliding pill picks it up automatically.

### Hero scroll speed

The hero height (`.hero-scroll`, currently `230vh`) controls how long the bowl takes to travel across. Make it taller for a slower sweep, shorter for a faster one. The stat pop-in points are set in the `swipeThresholds` object in the script.

## Placeholder content to replace

All content is sample data for a fictional cafe. Before going live, update:

- Cafe address, opening hours, phone number and email in the footer
- Menu items, prices and nutrition values (calories, protein, fat)
- The facts and copy in the Philosophy section

## Known limitations

- **The request form is front-end only.** Submitting it shows a confirmation message but does not send the data anywhere. To make it functional, connect it to a form service (Formspree, Netlify Forms, Google Forms) or your own backend.
- Fonts are loaded from Google Fonts, so first load needs an internet connection.
- The bowl graphic is an original SVG illustration, so there are no image assets to license.

## Tech stack

- HTML5
- CSS3 (custom properties, grid, flexbox, `position: sticky`, CSS masks)
- Vanilla JavaScript (IntersectionObserver, scroll-linked animation)
