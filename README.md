# The Hotel Financial Coach — Webinar Funnel Landing Page

Two single, self-contained landing pages built to be pasted into GoHighLevel
**Custom HTML** elements.

## Files

```
index.html                                       ← webinar hub/funnel page (no opt-in form; links out to
                                                    the replay and to each live webinar's own registration page)
how-to-build-a-hotel-budget-like-a-leader.html   ← dedicated registration page for the "How to Build a Hotel
                                                    Budget Like a Leader" webinar (Wed, Aug 19, 2026, 10–11 AM
                                                    EST), with the live GHL registration form embedded on-page
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

## `how-to-build-a-hotel-budget-like-a-leader.html`

The dedicated registration page for the "How to Build a Hotel Budget Like a
Leader" webinar (Wed, Aug 19, 2026, 10–11 AM EST). Unlike `index.html`, this
page carries the live GoHighLevel registration form embedded directly in its
"Register FREE Today" section — visitors register on-page, no click-through
to another URL.

It follows the same fragment pattern and `.hfc-`/`--hfc-*` scoping as
`index.html` (safe to paste directly into a GHL Custom HTML element), and
reuses the same brand tokens (burgundy `#8B0000`, gold `#C89B2A`, white),
fonts (Montserrat headlines / Inter body — see the font note in the file's
header comment), and component patterns (buttons, reveal-on-scroll, FAQ
accordion, sticky CTA) as the hub page, so the two stay visually consistent.

**Sections:** top bar → hero (with live countdown + framed webinar thumbnail)
→ quick-facts strip → Why Budgeting Matters → What You'll Learn → Meet David
Lund → Benefits of Attending → Registration (embedded form) → FAQ → final CTA
→ footer. A sticky CTA bar appears once visitors scroll past the hero and
hides again once the registration form scrolls into view.

**Images used:** the same Hotel Financial Coach logo, the "How to Build a
Hotel Budget Like a Leader" webinar thumbnail, and David Lund's professional
headshot — all already hosted on GHL Media Storage, same URLs as in
`index.html`.

**Countdown timer:** targets Aug 19, 2026, 10:00 AM Eastern, hardcoded near
the top of the `<script>` block (`setupCountdown`) as a UTC epoch — update
that one `Date.UTC(...)` call if the date/time ever changes.

**Registration form:** the GHL iframe embed snippet is included byte-for-byte
inside `<!-- ==== SECTION: REGISTRATION ==== -->`, wrapped in a padded white
card so it's visually integrated rather than looking like a bolted-on widget.
