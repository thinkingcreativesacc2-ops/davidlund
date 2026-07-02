# The Hotel Financial Coach — Webinar Funnel Landing Page

A single, self-contained landing page (`index.html`) built to be pasted into one
GoHighLevel **Custom HTML** element. It links out to the replay and to each live
webinar's own registration page — this page itself has no opt-in form.

## Files

```
index.html                  ← the entire deliverable (HTML + CSS + JS, one file)
assets/images/*.svg         ← branded placeholder graphics (see below)
```

## Before you go live: swap the images

GoHighLevel renders your pasted snippet on **its own domain**, not on GitHub. That
means relative paths like `assets/images/david-headshot.svg` will not resolve once
this is pasted into GHL — and linking directly to raw GitHub files isn't reliable
for production either. The placeholders in this repo exist so the page previews
correctly (nothing looks "broken") while you build; before launch you need to:

1. Open `assets/images/`.
2. Upload each file's **real** replacement to GoHighLevel → **Sites → Media Storage**
   (or any public image host / CDN you control).
3. Copy the generated URL GHL gives you.
4. In `index.html`, search for the matching filename (e.g. `david-headshot.svg`) —
   every `<img>` tag has an HTML comment directly above it telling you exactly what
   the image should be and its recommended dimensions — and replace the `src` value
   with the hosted URL.

| Placeholder file | Used for | Recommended size |
|---|---|---|
| `david-headshot.svg` | "Meet David Lund" section portrait | 800×1000 (portrait) |
| `david-hero.svg` | Hero section speaking photo | 1200×1500 (portrait) |
| `webinar-replay.svg` | Replay card — "Why Hotel Leaders Get Passed Over for Promotion" | 1280×720 |
| `webinar-pl-30-min.svg` | Live webinar — "How to Read Your Hotel P&L in 30 Minutes" | 1280×720 |
| `webinar-budget-leader.svg` | Live webinar — "How to Build a Hotel Budget Like a Leader" | 1280×720 |
| `webinar-labor-cost.svg` | Live webinar — "The Labor Cost Problem Nobody Talks About" | 1280×720 |
| `webinar-5-numbers.svg` | Live webinar — "The 5 Numbers Every GM Should Know" | 1280×720 |
| `webinar-dept-head-gm.svg` | Live webinar — "From Department Head to GM: The Financial Shift" | 1280×720 |
| `og-share-image.svg` | Social share preview (Open Graph / Twitter card) | 1200×630 |

The logo in the header/footer is **not** an image file — it's built from live CSS/SVG
text so it stays crisp at any size with zero extra image requests. If you'd rather
use your actual logo mark, replace the `.hfc-logo` markup near the top of the body
with an `<img>` tag pointing at your hosted logo file.

## Pasting into GoHighLevel

`index.html` is written as a **fragment** (a scoped `<style>` block, a wrapping
`<div>`, then a `<script>` block) rather than a full `<!DOCTYPE html>` document —
this is the safer pattern for a Custom HTML element, since GHL injects your snippet
into an existing page rather than rendering it as a standalone document. Copy the
entire contents of `index.html` and paste it into the Custom HTML element as-is.

All CSS is scoped under an `.hfc-` prefix and CSS custom properties are namespaced
to `--hfc-*` to avoid colliding with other elements/styles already on your GHL page.

## Editing copy or links later

Every major section is marked with an HTML comment (`<!-- ==== SECTION: ... ==== -->`)
so you or a future editor can find things fast. The five live-webinar registration
links and the replay link are also grouped at the top of the `<script>` block in a
single `WEBINARS` config object — update dates, titles, or URLs there and the page
re-renders the cards automatically, so you never have to hunt through markup to
change a date.
