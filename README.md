# The Hotel Financial Coach — "The 5 Numbers Every GM Should Know" Webinar Registration Page

A single, self-contained landing page (`index.html`) built to be pasted into one
GoHighLevel **Custom HTML** element. It's a dedicated registration page for one
free live webinar, with the GoHighLevel opt-in form embedded directly in the hero.

## Files

```
index.html   ← the entire deliverable (HTML + CSS + JS, one file)
```

There is no `assets/` folder — the webinar thumbnail and David Lund's photo are
already hosted on GoHighLevel Media Storage (`assets.cdn.filesafe.space/...`),
so nothing needs to be uploaded to this repo to preview or ship the page.

## Webinar details

- **Title:** The 5 Numbers Every GM Should Know
- **Date:** Wednesday, October 14, 2026
- **Time:** 10:00 AM – 11:00 AM EST
- **Cost:** Free

To reuse this page for a future webinar, update the title/date/time in these
places: the hero (`<h1>`, date/time chips, countdown target date in the
`<script>` block), the sticky top bar, the registration card, the FAQ answers
that mention the date, and the final CTA section.

## Pasting into GoHighLevel

`index.html` is written as a **fragment** (a scoped `<style>` block, a wrapping
`<div>`, then `<script>` blocks) rather than a full `<!DOCTYPE html>` document —
this is the safer pattern for a Custom HTML element, since GHL injects your
snippet into an existing page rather than rendering it as a standalone document.
Copy the entire contents of `index.html` and paste it into the Custom HTML
element as-is.

All CSS is scoped under a `.dlw-` prefix (short for "David Lund Webinar") and
CSS custom properties are namespaced to `--dlw-*` to avoid colliding with other
elements/styles already on your GHL page.

## Registration form

The GoHighLevel form embed (iframe + `form_embed.js`) is used exactly as
provided, once, inside the hero registration card. It is not duplicated
anywhere else on the page — every other call-to-action (sticky bar, final CTA,
mobile sticky bar) smooth-scrolls the visitor back up to this one form instead
of embedding a second copy (duplicate iframe `id`s would be invalid HTML).

A small loading spinner shows behind the iframe until it finishes loading (or
after a 4-second fallback), so visitors never see an empty white box while the
form initializes.

## Typography

"Gotham" is a licensed commercial typeface and isn't available on Google
Fonts. This page uses **Jost** for headlines (a free geometric sans with
Gotham-like proportions) and **Inter** for body copy. If you later license
Gotham (e.g. an Adobe Fonts/Typekit kit), add the kit's `<link>` above the
Google Fonts `<link>` in `index.html` and swap the family names in the
`--dlw-font-head` / `--dlw-font-body` custom properties — nothing else needs
to change.

## Page structure

1. **Sticky top bar** — hidden until the visitor scrolls past the hero, then
   slides down with the webinar name and a "Register Free" button.
2. **Hero** — two-column layout. Left: badge, headline, subheadline, supporting
   copy, date/time, key benefits, and a live countdown timer. Right: the
   registration card (thumbnail → "Register for FREE" → persuasive copy →
   embedded form). The registration card stacks above the "Why" section on
   tablet/mobile so visitors can register without much scrolling.
3. **Why Every GM Needs to Know These Five Numbers** — problem/agitation
   section framing the cost of financial overwhelm, then bridges to the promise
   of the webinar.
4. **What You'll Learn** — a 5-item agenda (framed with curiosity rather than
   naming specific named metrics, since the exact 5 numbers are the webinar's
   payoff).
5. **Meet David Lund** — bio, credentials, and photo.
6. **Benefits of Attending** — an 8-card grid of outcomes.
7. **FAQ** — accordion, covers cost, audience, replay availability, format.
8. **Final CTA** — closing section that scrolls back up to the one registration
   form.
9. **Mobile sticky CTA** — a bottom bar on phones/tablets, shown once the
   visitor scrolls past the hero.

## Editing copy or links later

Every major section is marked with an HTML comment
(`<!-- ====== SECTION N: ... ====== -->` or `<!-- ==== SECTION: ... ==== -->`)
so a future editor can find things fast. Image URLs are marked with
`<!-- IMAGE: ... -->` comments directly above the relevant `<img>` tag.
