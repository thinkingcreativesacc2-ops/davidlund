# The Hotel Financial Coach — Webinar Funnel Landing Page

A single, self-contained landing page (`index.html`) built to be pasted into one
GoHighLevel **Custom HTML** element. It links out to the replay and to each live
webinar's own registration page — this page itself has no opt-in form.

## Files

```
index.html   ← the entire deliverable (HTML + CSS + JS, one file)
```

There is no `assets/` folder — every photo, thumbnail, and the logo are already
wired to hosted GoHighLevel Media Storage URLs (`assets.cdn.filesafe.space/...`),
so nothing needs to be uploaded to this repo to preview or ship the page.

## Image map

| Used for | Image |
|---|---|
| Top promo bar + footer logo | Hotel Financial Coach logo |
| Hero section | David Lund speaking on stage |
| "Meet David Lund" section | David Lund professional headshot |
| Replay card + modal — "Why Hotel Leaders Get Passed Over for Promotion" | replay thumbnail |
| Live webinar — "How to Read Your Hotel P&L in 30 Minutes" | webinar thumbnail |
| Live webinar — "How to Build a Hotel Budget Like a Leader" | webinar thumbnail |
| Live webinar — "The Labor Cost Problem Nobody Talks About" | webinar thumbnail |
| Live webinar — "The 5 Numbers Every GM Should Know" | webinar thumbnail |
| Live webinar — "From Department Head to GM: The Financial Shift" | webinar thumbnail |

To swap any image later: open `index.html`, search for the section by its visible
text (e.g. search "Meet David Lund" or the webinar title), and replace the `src`
value on the nearby `<img>` tag with a new hosted URL. The five live-webinar
thumbnails also live together in the `WEBINARS` config object near the top of the
`<script>` block, so you can update all five `img` values in one place.

There's no Open Graph / social-share image wired into this snippet (that's a
`<head>`-level `<meta>` tag, which belongs to GHL's page/funnel SEO settings, not
this element) — set that separately in the GHL page editor if you want a custom
link-preview image.

## Pasting into GoHighLevel

`index.html` is written as a **fragment** (a scoped `<style>` block, a wrapping
`<div>`, then a `<script>` block) rather than a full `<!DOCTYPE html>` document —
this is the safer pattern for a Custom HTML element, since GHL injects your snippet
into an existing page rather than rendering it as a standalone document. Copy the
entire contents of `index.html` and paste it into the Custom HTML element as-is.

All CSS is scoped under an `.hfc-` prefix and CSS custom properties are namespaced
to `--hfc-*` to avoid colliding with other elements/styles already on your GHL page.

## Page structure

There is no site navigation/header — for a single-page funnel, a nav menu mostly
just gives visitors more ways to leave before registering. In its place is a slim
**top promo bar** advertising the nearest upcoming live webinar (currently July 22,
"How to Read Your Hotel P&L in 30 Minutes") with a direct "Save My Seat" link. If
that webinar has already passed, update the date/title/link in the promo bar markup
near the top of the page body (look for the `<!-- SECTION: TOP PROMO BAR -->` comment)
to point at whichever session is coming up next.

## Editing copy or links later

Every major section is marked with an HTML comment (`<!-- ==== SECTION: ... ==== -->`)
so you or a future editor can find things fast. The five live-webinar registration
links and the replay link are also grouped at the top of the `<script>` block in a
single `WEBINARS` config object — update dates, titles, or URLs there and the page
re-renders the cards automatically, so you never have to hunt through markup to
change a date.

---

# Dr. Bryan K. Williams — 20th Anniversary Celebration Replay Experience

A separate, unrelated single-file deliverable: `bryan-williams-20th-anniversary-replay.html`.
It's a premium, story-driven replay experience for Dr. Bryan K. Williams' 20th
Anniversary Celebration — hero, legacy storytelling, three session cards with a
video modal, a legacy statement banner, and a final CTA — built the same way as
`index.html` above (a self-contained GHL Custom HTML fragment, no `<head>`/`<body>`
wrapper, styles scoped under a unique prefix so it can sit on a page with other
elements).

**Before publishing, replace these placeholders:**

- **Logo** — the hero's focal point is currently a hand-built inline SVG medallion
  (search the file for `HERO EMBLEM`). Swap it for `<img class="dbw-emblem" src="[official logo URL]" ...>` once the real 20th Anniversary logo is uploaded to GHL Media Storage.
- **Session videos** — the `SESSIONS` array near the top of the `<script>` block
  holds each day's title, description, duration, and `video` embed URL. All three
  currently point at a harmless public placeholder video so the modal is fully
  functional to preview; replace each `video` value with the real Day 1/2/3
  recording URL (YouTube/Vimeo embed URL or GHL-hosted video page).
- **Thumbnails** — each session card uses a distinct gold-on-navy gradient
  "poster" instead of a stock photo, so the page ships premium and fast with zero
  external image dependencies. Add a real `<img>` inside `.dbw-card__media` if you
  later want photo thumbnails.
- **Links** — the "Continue Learning With Dr. Bryan" button and the footer social
  icons are marked `PLACEHOLDER LINK` / `PLACEHOLDER LINKS` and default to `#`;
  point them at Dr. Bryan's real site, community, or social profiles.

Everything else (copy, layout, animations, the share button, the scroll-reveal
and count-up effects) works as-is — paste the file's contents into one GHL
Custom HTML element.
