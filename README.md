# The Hotel Financial Coach — Webinar Funnel Landing Page

A single, self-contained landing page (`index.html`) built to be pasted into one
GoHighLevel **Custom HTML** element. It links out to the replay and to each live
webinar's own registration page — this page itself has no opt-in form.

## Files

```
index.html      ← webinar registration landing page (HTML + CSS + JS, one file)
thank-you.html  ← post-registration Thank You + Skool community upsell page (one file)
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

## `thank-you.html` — post-registration Thank You + upsell page

Shown immediately after someone registers for a webinar. Confirms the signup,
walks visitors through "What Happens Next," and upsells David Lund's Skool
community (**not** a hard sell — positioned as a natural next step while they
wait for the live event). Same one-file, GHL-Custom-HTML-element pattern as
`index.html`, but scoped under `.hfty-` / `--hfty-*` instead of `.hfc-` so the
two snippets can never collide if they ever end up on the same page.

Notable choices, all confirmed with the client:
- **No contact merge fields** — the greeting is generic so the page works
  whether or not contact data is present.
- **No countdown timer / hardcoded date** — copy points people to their inbox
  for the exact date & time, so one page can be reused for any webinar without
  edits.
- **Montserrat (headlines) + Inter (body)** via Google Fonts — same typography
  approach as `index.html`, since "Gotham" isn't a free web font.
- **Both supplied David Lund photos are used** — the on-stage/speaking photo in
  the hero (energy/excitement), the professional headshot in "Meet David Lund"
  (credibility/trust).

Both "Join the Community" buttons link to
`https://www.skool.com/the-hotel-financial-coach-6836/about` — search the file
for `skool.com` if that URL ever needs to change.
