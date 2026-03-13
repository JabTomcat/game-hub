# Game Hub — Style Guide

A reference for keeping every page consistent. When starting a new page, always copy `TEMPLATE.html` and link to `style.css`.

-----

## Fonts

|Role                      |Font            |Usage                                  |
|--------------------------|----------------|---------------------------------------|
|Headings, labels, badges  |`Press Start 2P`|Small sizes only (7–12px) — it’s chunky|
|Body, descriptions, tables|`VT323`         |18–22px for comfortable reading        |

Both are loaded via Google Fonts in `style.css` — no extra imports needed.

-----

## Colours

|Variable    |Hex      |Use for                         |
|------------|---------|--------------------------------|
|`--bg`      |`#0a0a0f`|Page background                 |
|`--panel`   |`#12121a`|Cards, stat bars                |
|`--border`  |`#2a2a3a`|All borders                     |
|`--gold`    |`#f0c040`|Titles, highlights, active state|
|`--gold-dim`|`#a07a10`|Shadows, decorative lines       |
|`--red`     |`#e04040`|HP bars, warnings, badges       |
|`--blue`    |`#4080e0`|Section labels                  |
|`--green`   |`#40c060`|Page counts, positive values    |
|`--purple`  |`#9060e0`|Available if needed             |
|`--text`    |`#d0d0e0`|Body text                       |
|`--text-dim`|`#707088`|Secondary / muted text          |

Always use CSS variables — never hardcode hex values in page-level styles.

-----

## Page Structure

Every page follows this order:

```
<header class="site-header">   ← title, subtitle, HP bar
<nav class="breadcrumb">       ← navigation trail (skip on root index)
<div class="divider">          ← decorative section break
<main class="container">       ← all page content goes here
<footer class="site-footer">   ← consistent footer
```

-----

## Breadcrumbs

Show the user where they are. Always link back up the chain.

```
Root index:   (no breadcrumb)
Game index:   HUB ▶ DIABLO II RESURRECTED
Class page:   HUB ▶ DIABLO II RESURRECTED ▶ SORCERESS
```

-----

## Content Patterns

### Content Cards (links to sub-pages)

Use `.content-grid` + `.content-card` for grids of links.

### Reference Tables

Use `.data-table` for skill lists, item stats, build data, etc.

### Plain Text / Guides

Use `<p style="font-size:20px; line-height:1.6; color:var(--text)">` for readable paragraphs.

-----

## Folder Structure

```
game-hub/
├── index.html          ← root hub (all games)
├── style.css           ← shared styles (link from every page)
├── TEMPLATE.html       ← copy this to start any new page
├── STYLE-GUIDE.md      ← this file
│
├── diablo2r/
│   ├── index.html      ← game landing page
│   ├── sorceress.html
│   └── necromancer.html
│
└── new-game/
    ├── index.html
    └── ...
```

### CSS path per level

- Root (`index.html`) → `href="style.css"`
- Game index or class page → `href="../style.css"`

-----

## Adding a New Game

1. Copy `TEMPLATE.html` → create `new-game/index.html`
1. Update the `<link>` path to `../style.css`
1. Fill in the title, breadcrumb, and content cards
1. Add a new `.game-card` to the root `index.html`
1. Update the GAMES and PAGES counts in the root stats bar

## Adding a New Page Inside a Game

1. Copy `TEMPLATE.html` → create `game-name/page-name.html`
1. Link `../style.css`
1. Set breadcrumb: `HUB ▶ GAME NAME ▶ PAGE NAME`
1. Add a link to it in the game’s `index.html`
1. Update the PAGES count in the root stats bar

-----

## Checklist for Every New Page

- [ ] Copied from `TEMPLATE.html`
- [ ] `style.css` path is correct for this folder level
- [ ] `<title>` updated in `<head>`
- [ ] Header title and subtitle filled in
- [ ] Breadcrumb updated with correct links
- [ ] Footer left unchanged
- [ ] Linked from parent index page