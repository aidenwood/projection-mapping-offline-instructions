# Projection Offline Instructions — Project Rules

Context: offline field-manual set for **Boog Visuals** projection-mapping gigs (Magnetic Fields stage and any future shows). Read at the venue on a laptop or phone with no internet. Print-ready in a pinch.

## Hard rules for this folder

### Offline-safe or it doesn't ship
- **Single self-contained HTML file per manual.** No external `<link>`, no external `<script src>`, no CDN fonts, no remote images.
- Styles inline in `<style>` inside the document. Scripts inline in `<script>` inside the document.
- Fonts must be system fallbacks only — the existing `--mono` and `--serif` stacks. Never add a `@font-face` that points to a URL.
- Diagrams are ASCII inside `<pre>`, not SVG references and not raster images. If something genuinely must be a picture, inline it as a base64 `data:` URI and warn me first because file size matters.
- USB-portable. Drop the folder on a stick → opens on any browser, anywhere, with Wi-Fi disabled.

### Match the existing visual language
- Palette tokens already defined in every manual's `:root`: `--bg`, `--surface`, `--surface-2`, `--border`, `--text`, `--muted`, `--accent` (#ffb547), `--accent-dim`, `--warn`, `--ok`, `--info`. Do not invent new tokens.
- Typography: monospace headers and labels (`--mono`), serif body (`--serif`). Don't introduce sans-serif.
- Layout shell for full manuals: sticky left TOC + main column, mobile collapses to stacked. Don't redesign it.
- Reuse the existing components: `.masthead`, `.callout` (with `.warn`/`.ok`/`.info`), `.diagram`, `.ts` (troubleshooting collapse), `.checklist`, `.glossary`, `ol.steps`. Copy them from a sibling manual rather than reinventing.
- Search box behaviour (cloned-node DOM filter at the bottom of each manual) is the standard — keep it.
- Footer line is always `END OF FIELD MANUAL · OFFLINE-SAFE · SINGLE FILE · NO EXTERNAL DEPENDENCIES`.

### Voice and structure
- Stage-technician's tone: terse, opinionated, practical. Short paragraphs. No marketing-speak. No emoji.
- Every manual opens with `Volume N` kicker, plain-language title, one-line lede.
- Every manual ends with a Troubleshooting section, a Show-day checklist, and a Glossary.
- Cross-link to other volumes by relative href (`./ndi_mac_windows_field_manual.html` etc) — never absolute URLs.
- Use real product names and version-agnostic instructions. If a setting moves between versions, name the menu path AND the search term, e.g. `Preferences → MIDI` *(or search settings for "MIDI")*.

### Content rules
- Always assume **no internet at the venue**. Anything that needs to be downloaded, name-and-shame it under "Pre-cache before the gig."
- Always assume **the network is just the switch.** No router, no DHCP, no cloud login.
- Always include a baked-fallback line where a live system could fail (BT drops → wired USB; NDI drops → MP4 clip; etc).
- Honest about latency, battery, and quirks. If Bluetooth is ~20 ms, say so. Don't oversell.
- If a step changes between Windows and macOS, split it cleanly — never paper over the difference.

### When updating an existing manual
- Re-read the file before editing. Match indentation and the surrounding HTML pattern exactly.
- After adding a section, also add the matching `<li>` to the in-page TOC.
- After adding a new manual file, also update `manuals_index.html` with a `.card` entry and update the lede if the count changes.

## Pre-cache list — keep in mind when writing setup steps
Things that need to be on the laptop or USB stick before leaving home:
- Resolume Arena installer + licence file.
- TouchDesigner (non-commercial or licensed) installer.
- NDI Tools installer (Windows + Mac).
- loopMIDI installer (Windows, virtual MIDI cable).
- Art-Net node discovery utility for whichever node we're using.
- Bridge utilities for any controller-as-MIDI work (see Volume V).
- All MP4 fallback renders of each live composition.

## Do not
- Do not minify the HTML. Humans read these files at 2am with a torch.
- Do not move shared CSS into a separate file "for cleanliness" — it breaks the offline rule.
- Do not add analytics, telemetry, or anything that fires a network request.
- Do not assume the latest OS — these manuals get read on whatever laptop is on the truck.
