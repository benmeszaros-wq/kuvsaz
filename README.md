[README.md](https://github.com/user-attachments/files/28932645/README.md)
# Kuvasz Design System

A small, dependency-free design system for a Kuvasz breeder website. Plain CSS
custom properties plus a set of components — drop it into any stack (static
HTML, Webflow custom code, React, Astro, WordPress) without a build step.

> **Open `styleguide.html` in a browser** to see every token and component live.

---

## Why it looks the way it does

The design is grounded in the breed, not a generic "heritage" template.

- **White coat over dark pigment.** The Kuvasz's defining look isn't simply
  "white dog" — the standard rewards a lustrous white coat over heavily
  pigmented dark skin, a black nose, and dark-brown eyes. The system mirrors
  that: a clean coat-white canvas with a warm **slate** ramp for ink and
  structure, and an optional `data-theme="pigment"` dark mode for hero and
  footer bands.
- **Pasture green** is the single accent — the pastoral, steppe-guardian role
  the breed was bred for. It deliberately avoids the terracotta-and-cream look
  that has become the default for anything "old world."
- **Brass** appears rarely, for genuine heritage moments (champion lines,
  awards) — a nod to the breed's Renaissance status under King Matthias.
- **Type** pairs *Fraunces* (a characterful old-style serif, fitting for an
  ancient landrace) with *Hanken Grotesk* (calm, modern UI) and *IBM Plex Mono*
  for pedigree-style data: measurements, dates, and registration numbers.

---

## File structure

```
kuvasz-design-system/
├── README.md
├── LICENSE
├── package.json            # optional — lets you publish/version the tokens
├── styleguide.html         # living style guide (open this first)
├── tokens/
│   ├── tokens.css          # all design tokens as CSS custom properties (source of truth)
│   └── tokens.json         # same tokens in DTCG JSON (Style Dictionary / Tokens Studio)
└── styles/
    ├── reset.css           # minimal modern reset
    ├── base.css            # element defaults: type scale, links, layout primitives
    ├── components.css      # buttons, badges, cards, records, tables, forms, nav, footer
    └── utilities.css       # spacing, grid, text, and a11y helpers
```

---

## Usage

Load the stylesheets in order. Tokens first, then reset, base, components, and
utilities last.

```html
<!-- Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400..600&family=Hanken+Grotesk:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">

<!-- Design system -->
<link rel="stylesheet" href="tokens/tokens.css">
<link rel="stylesheet" href="styles/reset.css">
<link rel="stylesheet" href="styles/base.css">
<link rel="stylesheet" href="styles/components.css">
<link rel="stylesheet" href="styles/utilities.css">
```

Then build with the classes:

```html
<a class="btn btn--primary">Join the waitlist</a>
<span class="badge badge--available">Available</span>
```

### Dark sections

Any element with `data-theme="pigment"` flips the semantic colors to the
breed's dark side. Components inside keep working unchanged.

```html
<section class="hero" data-theme="pigment"> ... </section>
```

### Using just the tokens

If you only want the variables (e.g. in your own component library), load
`tokens/tokens.css` and reference them:

```css
.my-thing { color: var(--color-text); background: var(--color-accent-tint); }
```

---

## Token reference

| Group | Examples |
| --- | --- |
| Color (semantic) | `--color-bg` `--color-text` `--color-accent` `--color-border` `--color-success` |
| Color (primitive) | `--slate-50…900` `--pasture-50…800` `--brass-500` |
| Type | `--font-display` `--font-body` `--font-mono` `--text-xs…5xl` `--weight-*` |
| Space | `--space-1…10` (4px base) |
| Radius | `--radius-sm/md/lg/xl/pill` |
| Shadow | `--shadow-sm/md/lg/focus` |
| Motion | `--ease-out` `--duration-fast/base/slow` |

Full values live in `tokens/tokens.css`. The JSON mirror in `tokens/tokens.json`
is ready for [Style Dictionary](https://amzn.github.io/style-dictionary/) or
Tokens Studio for Figma.

---

## Components

Buttons (`.btn` + `--primary/secondary/ghost/heritage`, `--sm/lg/block`),
status badges (`.badge--available/reserved/upcoming/placed/heritage`), health
clearance chips, puppy/litter cards, the signature pedigree **record** block,
data tables, form fields, nav, hero, breed-fact stats, callouts, and footer.

All components meet a baseline of: responsive to mobile, visible keyboard
focus, and `prefers-reduced-motion` respected.

---

## Notes

- No JavaScript and no build step required. Add your own where you need it.
- Content in `styleguide.html` (kennel name, dog names, numbers) is placeholder
  demo content — swap in the real breeder's details.
- Fonts load from Google Fonts. Self-host them for production if you prefer.

## License

MIT — see `LICENSE`.
