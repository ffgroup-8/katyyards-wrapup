# Forefathers Project Wrap-Up: Master Template

A neutral, black-and-white version of the McNellie's Group wrap-up (ffgroup-8/mg-wrapup). Every project gets its own branding from its own master library. Used by the `ff-project-wrapup` skill.

## Files

```
index.html                 the whole page: styles, markup and scripts in one file
assets/logos/              client logo SVGs (copied in per project)
assets/fonts/              client headline webfont, if licensed for web
assets/shots/              screenshots as WebP; placeholder.svg stands in until replaced
```

## 1. Apply the client's brand (the only styling you change)

Edit the `:root` block at the top of `<style>`:

| Slot | Role | McNellie's example |
|---|---|---|
| `--ink` / `--ink-rgb` | Primary dark: hero, dark bands, headings | Glen #003A0F |
| `--deep` / `--deep-rgb` | Body text, brand-section band | Stout #40200D |
| `--accent` | Highlight: "up.", arrows, #1 pills, Added pills | Ignite #F17112 |
| `--accent-2` | Section numbers, small labels | Clover #1C9D3A |
| `--paper` / `--paper-rgb` | Page background, text on dark | Irish Cream #FFF8EA |
| `--paper-2` | Alternate light bands | #f4ecdb |
| `--line` | Hairlines, card borders | #e8dcc4 |
| `--muted` | Secondary text on light | #6b5446 |
| `--on-dark-accent` | Labels on dark bands | #9fdcae |
| `--on-dark-muted` | Secondary text on dark bands | #cfd8c9 |
| `--chip` | Delivered and rank-2 pills | #dcefd9 |
| `--display` | Headline font | MD Nichrome |
| `--body` | Body font | Figtree |

Rules:
- Use the client's shipped palette from their master library, never earlier explorations.
- Derive the tints (`--paper-2`, `--line`, `--on-dark-*`, `--chip`) from the brand colors so neutrals lean toward the brand.
- Check contrast: `--accent` must read on both `--ink` and `--paper`. If it doesn't, give the hero `.up` its own color.
- Fonts: see the slot comment in `<head>`. A webfont in a public repo can be downloaded, so confirm the web license.

## 2. Logos

Replace each `.logo-slot` placeholder SVG (top bar, brand card, footer) and the `.mk` mark tiles with the client's SVGs:
- Remove `<?xml ?>`, `<defs><style>`, and every `id` and `data-name`.
- Change `class="cls-1"` (or the fill) to `fill="currentColor"`, so each logo takes the color of its container.
- Top bar: horizontal or primary lockup at about 34px tall. Brand card: primary lockup. Footer: stacked logotype.

## 3. Content

- Fill every `[[PLACEHOLDER]]`. Before publishing, search for `[[`; none may remain.
- Each section sits between `<!-- SECTION:name START -->` and `END` markers, with optional `BLOCK:` parts inside. Delete anything without real material, then renumber the `.num` labels (01, 02 ...).
- Repeat rows and cards as needed: `.c` portfolio cards, `.row` scorecard rows, `tr` AI test rows, `.rollout` periods (up to six).
- Screenshots: convert to WebP (max 2000px wide). Give each img its real `width` and `height`, and keep `data-zoom` pointing at the same file.
- Writing: plain language, no em dashes, every number traceable to a source.

## 4. Built in (don't remove)

- Lightbox for every `.zoom` button: Esc, the × button or a backdrop click closes it.
- Scroll reveal for content below the fold, skipped when reduced motion is on.
- Responsive rules: AI table becomes cards under 860px, grids use `minmax(0,1fr)`, and `overflow-x:clip` guards the page.
- `noindex` meta, so wrap-ups stay out of Google.

## 5. Adding a new section to the master

When a project needs a section the template doesn't have:
1. Build it in that project's repo using only the token variables, never raw hex.
2. Once it works, copy it into this template between new `SECTION:name` markers, using placeholder content.
3. Add any new CSS to the template's `<style>`, plus the selector to the reveal script's `single` or `groups` list if it should animate.
4. Run the overflow check at all twelve widths, then commit to the template repo and note the change below.

## Changelog

- 2026-11: v1, extracted from the McNellie's Group wrap-up.
